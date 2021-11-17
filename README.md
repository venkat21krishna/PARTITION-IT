# PARTITION-IT
PLEASE CLICK ON ABOVE README FILE

#include <bits/stdc++.h>
using namespace std;
#define ll  long long int
#define max 100000
#define endl '\n'


int main(){
    vector <ll>mk(100001,1);
    vector <ll>count(100001,1);
    for(int i=2;i<=max;i++) {
        if(count[i]==1)
            count[i]=i;
        for(int j=i+i;j<=max;j+=i){
            mk[j]=0;
            if(count[j]==1)
                count[j]=i;}}
   ll t;
   cin >> t;
   while(t--){
       ll n,total;
       cin>>n>>total;
       ll k=total;
       vector <ll>p1;
       if(total==n-1){
           cout<<"YES\n";
           for(int i=2;i<=n;i++)
               cout<<i<<" ";
           cout<<"\n";}
       else if(n==3){
           cout<<"YES\n";
           if(k==1)
               cout<<3<<"\n";
           else if(k==2)
               cout<<1<<" "<<2<<"\n";}
       else if(n==4){
           cout<<"YES\n";
           if(k==1)
               cout<<3<<"\n";
           else if(k==2)
               cout<<3<<" "<<1<<"\n";}
       else{
           ll y=n/2+1;
           ll count=0;
           set <ll>s;
           s.insert(1);
           for(int i=y;i<=n;i++)
               if(mk[i])
                   ++count,s.insert(i);
               ll p=0;
               for(int i=1;i<=count+1;i++){
                   if(total==i or total==n-i){
                       ++p;
                       cout<<"YES\n";
                       if(total==i){
                           ll j=i;
                           while(j--){
                               cout<<*(s.begin())<<" ";
                               s.erase(s.begin());}
                           cout << endl;
                           break;}
                       else{
                           ll u=0;
                           for(int j=n;j>=1;j--){
                               if(u==i){
                                   cout<<j<<" ";}
                               else{
                                   if(s.find(j)!=s.end()){
                                       s.erase(j);
                                       ++u;}
                                   else{
                                       cout<<j<<" ";
                                   }}}
                           cout << endl;
                           break;
                       }}}
               if(!p){
                   cout<<"NO\n"<<"\n";
               }}}
    return 0;}
