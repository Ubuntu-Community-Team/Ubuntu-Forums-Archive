---
title: "Python programing help"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by Vikkhacker on 2010-08-24
i made a program in python, its a simple game it askes you for a number and if you guess it right you can play again, but its the same number. how can i put it that each time i guess the number right,to change the number itself,random each time you get it right.

---

### Post by s.fox on 2010-08-24
Hello and welcome to the Ubuntu Forums :).

You are nearly done :)

Here is a very simple example for you to adapt.  It will generate a random number between 0 and 100.

```
import random
randomnumber = random.randint (0,100)
print randomnumber
```
Hope this helps you

-Silver Fox

---

### Post by Vikkhacker on 2010-08-24
thank you very much

---

### Post by Vikkhacker on 2010-08-24
yes but even if i make the change it will ask you for a number between 0-100 and i type in 20 it says lower i type in 1 it says lower i type in 0 it still says lower????

---

### Post by cgroza on 2010-08-24
I don't get it. The program returns "Its smaller" each time. i tried putting 0 and its the same thing. Something else is not good in there. Here is the code again.

```
import random 
a = random.randint(0,100) 
 
def guess(): 
 while 1: 
    number = raw_input ('Enter a number from 0 to 100: ') 
     
    if number == a:  
        print ("Congratulations You got it right!") 
        break 
        
    if number < a : print 'The number is higher' 
    if number > a : print ' The number is smaller' 
 
 
guess()         
while 2:     
     
   z= raw_input('Do you want to play again?y/n: ')      
   if z == 'y' : guess() 
   if z == 'n': break 
    
raw_input('Press <enter> to quit>')    
```

---

### Post by juancarlospaco on 2010-08-24
Welcome, Fox is correct.
Dont forget the:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```

At the beginning of the file.

#!/usr/bin/env python--->make it run by Python interpreter
# -*- coding: utf-8 -*---->make it UTF-8 só yóú cán úsé &#9416;!&#9436;B0Ls™ Ññ &#3232;_&#3232;

---

### Post by Vikkhacker on 2010-08-24
it still says its lower?

---

### Post by cgroza on 2010-08-24
Its still returning "its smaller'. Here is the exact output!

```

Enter a number from 0 to 100: 0
 The number is smaller
Enter a number from 0 to 100: 0
 The number is smaller
Enter a number from 0 to 100: 50
 The number is smaller
Enter a number from 0 to 100: 100
 The number is smaller
Enter a number from 0 to 100: 


```

---

### Post by s.fox on 2010-08-24
Hello again,

Consider data types.

Hope this helps you all.

-Silver Fox

---

### Post by kroq-gar78 on 2010-08-24
try displaying the number ( in this case "a" ) before each repetition/ guess. It'll help you debug the problem and find where the problem is (number input, random #s, if logic (probably not....)) even though it will defeat the point of the game.

---

### Post by Vaphell on 2010-08-24
type(a) = int, type(number) = str

number = int( raw_input ('Enter a number from 0 to 100: ') )

---

### Post by slooksterpsv on 2010-08-24
> **s.fox said:**
> Hello again,

Consider data types.

Hope this helps you all.

-Silver Fox

Silver fox is right; raw_input reads as string and not int, so you have to typecast it to an integer via:
int(num) or num = int(raw_input("enter number: ") - then you have to figure out how to have it not kill the program if someone "accidentially" enters text instead of a number.

---

### Post by cgroza on 2010-08-25
> **kroq-gar78 said:**
> try displaying the number ( in this case "a" ) before each repetition/ guess. It'll help you debug the problem and find where the problem is (number input, random #s, if logic (probably not....)) even though it will defeat the point of the game.


I did, if  i entered the number it said is wrong! I figured it out. I should've used input instead of raw_input. Thanks to you people my problem is solved. Thanks!

---

### Post by cgroza on 2010-08-25
> **slooksterpsv said:**
> Silver fox is right; raw_input reads as string and not int, so you have to typecast it to an integer via:
int(num) or num = int(raw_input("enter number: ") - then you have to figure out how to have it not kill the program if someone "accidentially" enters text instead of a number.
I am trying to make it display Invalid command and put the question again with an else statement. I saw in a program that some code like:
else:
     return

was doing this. But it didnt worked with me. I will try figuring that out. Any suggestions are still welcomed!

---

### Post by cgroza on 2010-08-25
Now, i have another problem. The program doesnt quits when i answer with q. It quits only the firs 2 times but then it just restarts the function again: Here is the code:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import time
import datetime
import random


today = datetime.date.today()
print "The date is", today 


def guess3():
     
 while 1:
    a = random.randint(0,1000)
    number = input ('Enter a number from 0 to 1000: ')    
    if number == a: 
        print ("Congratulations You got it right!")
        b=raw_input('Enter 1 for Easy, enter 2 for Medium, enter 3 for Hard, or q to exit.1/2/3/q/: ')
        if b == '1' : guess1()
        elif b == '2' : guess2()
        elif b == '3' : guess3()  
        elif b == 'q' : break
        
    if number > a : print 'The number is smaller'
    if number < a : print 'The number is higher'
   
        
    


def guess1():
      
 while 2:
    a = random.randint(0,10)  
    number = input ('Enter a number from 0 to 10: ')   
    if number == a: 
        print ("Congratulations You got it right!")
        b=raw_input('Enter 1 for easy, enter 2 for medium, enter 3 for hard, or q to exit.1/2/3/q/: ')
        if b == '1' : guess1()
        elif b == '2' : guess2()
        elif b == '3' : guess3()  
        elif b == 'q' : break
        
    if number > a : print 'The number is smaller'
    if number < a : print 'The number is higher'
    
    
    


def guess2():
     
 while 3:
    a = random.randint(0,100)   
    number = input ('Enter a number from 0 to 100: ')    
    if number == a: 
        print ("Congratulations You got it right!")
        b=raw_input('Enter 1 for easy, enter 2 for medium, enter 3 for hard, or q to exit.1/2/3/q/: ')
        if b == '1' : guess1()
        elif b == '2' : guess2()
        elif b == '3' : guess3()  
        elif b == 'q' : break
        
    if number > a : print 'The number is smaller'
    if number < a : print 'The number is higher'
    
    


b=raw_input('Enter 1 for easy, enter 2 for medium, enter 3 for hard, or q to exit.1/2/3/q/: ')


if b == '1':
    guess1()

if b == '2':
    guess2()

if b =='3':
    guess3()

if b =='q': quit    

    
   
raw_input('Bye, Bye. Press <enter> to quit> ')

```

---

### Post by snip3r8 on 2010-08-25
Sigh,i know python does stuff other than maths but dammit nobody writes a tutorial on python that doesn't have stupid number games,i want a tutorial that does something useful,not a how to use a calculator guide.

---

### Post by cgroza on 2010-08-25
> **snip3r8 said:**
> Sigh,i know python does stuff other than maths but dammit nobody writes a tutorial on python that doesn't have stupid number games,i want a tutorial that does something useful,not a how to use a calculator guide.
Then go find one. I am a begginer and i  am trying to make a guessing game... now all i need is to make it to quit at the right time...

---

### Post by Vaphell on 2010-08-25
there is some fail buried in your code, sometimes it says that number is higher even if i got it right

python guess.py 
The date is 2010-08-25
Enter 1 for easy, enter 2 for medium, enter 3 for hard, or q to exit.1/2/3/q/: 1
Enter a number from 0 to 10: 4
The number is higher
Enter a number from 0 to 10: 6
The number is smaller
Enter a number from 0 to 10: 5
The number is smaller
Enter a number from 0 to 10: 4
The number is higher
Enter a number from 0 to 10: 5
The number is higher
Enter a number from 0 to 10: 6
The number is higher
Enter a number from 0 to 10: 7
The number is smaller
Enter a number from 0 to 10: 6
The number is higher
Enter a number from 0 to 10: 7
The number is smaller
Enter a number from 0 to 10: 6
The number is smaller
Enter a number from 0 to 10: 7
The number is smaller
Enter a number from 0 to 10: 6
The number is smaller
Enter a number from 0 to 10: 5
The number is higher
Enter a number from 0 to 10: 6
Congratulations You got it right!

WTH? o.O



on a sidenote these 3 guess funtions are virtually identical, write one function instead and take the size of the number range as a parameter. That way any change to the algorithm won't require fixes in 3 different places :)

edit:
try this

```

#!/usr/bin/python

import time
import datetime
import random

def guess(size):
  a = random.randint(0,size)
  number = -1
  while number != a:
    number = input ('Enter a number from 0 to '+`size`+': ')    
    if number < a: 
      print 'The number is higher'
    elif number > a :
      print 'The number is smaller'
    else:
      print 'Congratulations You got it right!'   

today = datetime.date.today()
print 'The date is', today 
b=''
while (b != 'q'):
  b=raw_input('Enter 1 for easy, enter 2 for medium, enter 3 for hard, or q to exit.1/2/3/q/: ')
  if b in ['1','2','3']:
    guess(10**int(b))
    
   
raw_input('Bye, Bye. Press <enter> to quit> ')
```

---

### Post by cgroza on 2010-08-25
Thanks... You really went through the trouble of running the code. I appreciate it.
Edit: I took a careful look on the code. I would never thought at something more genius.

---

### Post by slooksterpsv on 2010-08-25
The number is being generated each time you take a guess so you guess, number changes, you guess number changes. So just put a while look after you generate number.

---

### Post by Vaphell on 2010-08-25
> Edit: I took a careful look on the code. I would never thought at something more genius.

lol :D surely you jest

Programming is all about clean design and code reusability.
When you want to repeat something put that thing in a loop. When you have copy-pasted chunks of code scattered around, always integrate them into 1 function with more abstract approach. And don't produce overly large, monolithic functions. If it doesn't fit on the screen, break it down to functional, easier to grasp pieces. You'll spend much less time debugging.
And start to learn objects, they kick a$s :-)

---

### Post by cgroza on 2010-08-25
> **Vaphell said:**
> lol :D surely you jest

Programming is all about clean design and code reusability.
When you want to repeat something put that thing in a loop. When you have copy-pasted chunks of code scattered around, always integrate them into 1 function with more abstract approach. And don't produce overly large, monolithic functions. If it doesn't fit on the screen, break it down to functional, easier to grasp pieces. You'll spend much less time debugging.
And start to learn objects, they kick a$s :-)
Thanks again. You taught me a lesson I will never forget. Your code amazed me (i'm a begginer).

---

### Post by Vaphell on 2010-08-25
my mediocre skills almost got an ego boost ;-)
anyway if you have any further questions, feel free to ask.

---

### Post by cgroza on 2010-08-27
I'm back. Now I am trying to write the input to a file. What i want to know is how to start a new line when i press enter. Here is the code. :D
```

print('Welcome to my simple text editor.')
a = raw_input('')
fob=open('/home/cgroza/test.txt','w')
fob.write(a)

```

---

### Post by slooksterpsv on 2010-08-27
You would need to continually get input from raw_input for that, but it wouldn't really suffice too much as a text editor. As I was referred to before, check out the curses library.

EDIT: I've made a simple terminal editor that I just did as a fun test project it's pretty neat to me. Here let me upload the py file and you can try it out and see how my code works for what I do.

EDIT 2: Type in =help to see the help menu and =ex to quit

---

