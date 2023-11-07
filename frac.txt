#include <bits/stdc++.h>
using namespace std;
struct Item {
	int profit, weight;
/*	Item(int profit, int weight)
	{   this->profit = profit;
		this->weight = weight;}*/};
static bool cmp(struct Item a, struct Item b)
{   double r1 = (double)a.profit / (double)a.weight;
	double r2 = (double)b.profit / (double)b.weight;
	return r1 > r2;}
double fractionalKnapsack(int W, struct Item arr[], int N)
{   sort(arr, arr + N, cmp);
    double finalvalue = 0.0;
	for (int i = 0; i < N; i++) {
		if (arr[i].weight <= W) {
			W -= arr[i].weight;
			finalvalue += arr[i].profit;
		}
    	else {
			finalvalue+= arr[i].profit* ((double)W / (double)arr[i].weight);
			break;	}	}
return finalvalue;}
int main()
{   int n;
    cout<<"Enter no of items"<<endl;
    cin>>n;
    int W;
    cout<<"Enter capacity"<<endl;
    cin>>W;
    Item arr[n];

  for(int i=0;i<n;i++){
        cout<<"Enter weight of items"<<i+1<<endl;
        cin>>arr[i].weight;
        cout<<"Enter profit of items"<<i+1<<endl;
        cin>>arr[i].profit;
       
        }
    cout << fractionalKnapsack(W, arr, n);
	return 0;
}