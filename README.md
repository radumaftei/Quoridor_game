# Quoridor_game
#include <iostream>
#include <windows.h>
using namespace std;
void setcolor(unsigned short color)
{
HANDLE hcon = GetStdHandle(STD_OUTPUT_HANDLE);
SetConsoleTextAttribute(hcon,color);
}
/// 1-dark blue 2-pale dark green 3-pale dark cyan 4-dark red 5-dark purple-pink 6-dark yellow 7-default white?
/// 8-gray 9-blue 10-green 11-cyan 12-red 13-pink 14-yellow 15-brighter 9
/// the rest influences the backround
struct nod
{
 char id[20];
 char pass[20];
 nod* urm;
};
void menu();
void createNewAccount(nod*& L)
{
char idI[21],passI[21];
int okay=1,nr1=0,nr2=0,abort=0;
while(okay)
    {
    cout<<"Type in 0 for both username and password if you want to abort.";
    cout<<'\n';
    cout<<"Username:";
    cin>>idI;
    cout<<"Password:";
    cin>>passI;
    int i=0;
    while(idI[i])
        nr1++,i++;
    i=0;
    while(passI[i])
        nr2++,i++;
    if( (nr1==1 || nr2==1) && (idI[0]!='0' || passI[0]!='0') ) 
      cout<<"Numarul de caractere pentru username sau parola trebuie sa fie cel putin 2!"<<'\n';
    else 
      if(nr1>=22 || nr2>=22) 
        cout<<"Numarul de caractere pentrul username sau parola trebuie sa fie cel mult 21!"<<'\n';
            else 
              if(nr1>1 && nr1<22 && nr2>1 && nr2<22) okay=0;
                else 
                  if (nr1==1 && nr2==1 && idI[0]=='0' && passI[0]=='0' ) 
                    okay=0,abort=1;
    if(okay==1)
        {
            nr1=0;
            nr2=0;
            for(int i=0;i<=20;i++)
                idI[i]=NULL,passI[i]=NULL;
        }

    }
if(abort==0)
{
    L=NULL;
    nod* p;
    p=new nod;
    for(int i=0;i<=20;i++)
        p->id[i]=idI[i];
    for(int i=0;i<=20;i++)
        p->pass[i]=passI[i];
    p->urm=L;
    L=p;
    cout<<'\n';
    cout<<'\n';
    cout<<"Account created!"<<'\n';
    system("pause");
}
menu();
}
