---
title: "Help PLEASE...C++ Decleration..."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-18
I tried for 5 hours in the programing forum with no help so I am going to try here. "I JUST STARTED CODING YESTERDAY" Some one helped me with this earlier and fixed the problems but of course I tinkered with it some more and now am stuck. ALL I WANT IS : to know how I declare the blue highlighted [COLOR="RoyalBlue"]kellyfavoritecolor[/COLOR] please.

```

#include <iostream>

using namespace std;

int main()
{
    string name;
    bool iskelly=false, iskelly_age=false, iskelly_favorite_color=false;
    int kellyage=0;

    while (!iskelly) 
    {
        cout << "Please enter your name: ";
        cin >> name;
        
        if (name == "kelly" || name == "Kelly")
        {
            iskelly = true;
            cout << "You have a beautiful name!" << endl;
        }
        else
        {
            cout << "This is not your first name...Please try again." << endl;
        }
    }
        
    while (!iskelly_age)
    {
        cout << "Please enter your age: " << endl;
        cin >> kellyage;
        
        if (kellyage == 32)
        {
            cout << "Wow, you are beautiful and young..." << endl;
            iskelly_age = true;
        }
        else if (kellyage < 32)
            cout << "Come on add some yrs...;-)  Please enter your true age..." << endl;
        else if (kellyage > 32)
            cout << "You must be younger than this, Please enter your true age..." << endl;
		}
	{

	while (!iskelly_favorite_color)
	{	
		cout << "What is your favorite color? " << endl;
		[COLOR="RoyalBlue"]cin >> kellyfavoritecolor;[/COLOR]
		
		if (kellyfavoritecolor == "Red")
		{
			cout << "Red is a very nice color..." << endl;
			iskelly_favorite_color = true;
			
			
		}
		else 
		{
			cout << " I know you better than this, you know that is not your favorite color. Try again...";
		}
    }
                
        cout << endl;
    }
    
    return 0;
}

```

Thank you to anyone who will help me with this and to all those who have tried to help... Problem is my fault cause I just don't understand what they are telling me...

---

### Post by lone_wolfII on 2009-02-18
See just under int main()?
There's a line that says "string name;"
Directly under that line, type "string kellyfavoritecolor" to declare that string. 

If you're looking for tutorials, check out 
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
if you do them one by one, you should get the knack of it soon enough.

EDIT: Oh and don't forget the ; at the end of the line :)

---

### Post by Leo Dragonheart on 2009-02-18
> **lone_wolfII said:**
> See just under int main()?
There's a line that says "string name;"
Directly under that line, type "string kellyfavoritecolor" to declare that string. 

If you're looking for tutorials, check out 
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
if you do them one by one, you should get the knack of it soon enough.

EDIT: Oh and don't forget the ; at the end of the line :)

Thank you very much that solved my problem Thx...

---

### Post by lone_wolfII on 2009-02-18
Yeah, you just need to remember that you have to declare the type (in this case, string) before you use it, otherwise the program won't know what type it is.

---

### Post by Leo Dragonheart on 2009-02-18
> **lone_wolfII said:**
> Yeah, you just need to remember that you have to declare the type (in this case, string) before you use it, otherwise the program won't know what type it is.

Thanx again... I before I added the kelly_favorite_color there was just the 

 string name;
    bool iskelly=false, iskelly_age=false;
    int kellyage=0;

and it worked fine. How come the iskelly_age=false did not need a seperate string like the kelly favorite color did? 

Thanx again and I will keep that in mind...

---

### Post by ephmanjmm on 2009-02-18
bool iskelly=false, iskelly_age=false;

creates two booleans and sets both to false.  These are not string types and can only be true or false.
You could have done (I believe)
bool iskelly;
bool iskelly_age;
iskelly=false;
iskelly_age=false;

But then again I have not worked in c++ in some time so I could be way off base here.

---

### Post by Leo Dragonheart on 2009-02-18
> **ephmanjmm said:**
> bool iskelly=false, iskelly_age=false;

creates two booleans and sets both to false.  These are not string types and can only be true or false.
You could have done (I believe)
bool iskelly;
bool iskelly_age;
iskelly=false;
iskelly_age=false;

But then again I have not worked in c++ in some time so I could be way off base here.

Thank you for the information....

---

### Post by carml on 2009-02-18
For the future,try to write a sketch of your program in pseudo-code,which it's a list of all the operations your program needs,but written into a very poor english grammar.
Then try to refine your first sketch,until you get that every phrase you've written is equivalent to a command in C++.
This my little suggestion,you can find elsewhere,come from my habit when I coded something for an exam at the university,doing so you'll don't have any headache due to too fast coding. ;)

---

