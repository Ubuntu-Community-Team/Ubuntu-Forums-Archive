---
title: "What am i doing wrong?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by ioabs on 2009-06-19
I am brand new to programming-started today in fact.   I am trying to learn using [http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python)    I am in the process of writing my first code, i think i scrwed up on the if - else but i am not sure what i am doing wrong.  help me!

#This program is my first attempt at a computer program beides hello world
# - don't be hatin'
#I am attempting to write a python program that can serve as a reference 




usrname = raw_input("What is your name: ")

print "This program is designed as a reference for basic python commands"
print "                 written by Ben"
print
print "What are you having trouble remembering:"
print "1.)how do I accept user input"
print "2.)what are the mathematical operators"
print "3.)what is the syntax of the if operator "


numchoice = input("please input the corresponding number: ")

    
 if numchoice == 1:
        print "for strings, use the command variable$=raw_input('askuser:')" 
    print "for numbers  variable=input('askuser:')"
    elif numchoice == 2:
        print "Mathematical operators:"
    print "addition +    subtraction -   exponents **   modulo %  division /"
    elif numchoice == 3:
    print"If variable booleanoperator variable colon  i.e  if num <1:"
    print"indent elif variable booleanoperator variable colon  i.e. elif num>1:"
    print"else colon i.e. else:
    else:
        print "The character(s) you entered are not valid - pick an number 1-3"

#this is not the finished program, unfortunately it already wont run
#i think that i f*&^ed up the if statement

---

### Post by LowSky on 2009-06-19
Creating IF statements even in Excel can be tough so if this is giving you problems you should start easy, first try just re-writing their texts and making sure you can get it to work.

this should be the first thing you try
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Hello,_World](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Hello,_World)

once mastered move onto 
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Who_Goes_There%3F)

then this
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Count_to_10](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Count_to_10)

 then start an if statement.
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Count_to_10](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Count_to_10)


remember you need to crawl before walking and walk before running.

---

### Post by ioabs on 2009-06-19
Turns out it was a few indentation errors.  I have them fixed now.  will repost code on same thread if i need further help

---

### Post by t0p on 2009-06-19
> **ioabs said:**
> Turns out it was a few indentation errors.  I have them fixed now.  will repost code on same thread if i need further help

If you use something like IDLE (Integrated DeveLopment Environment) it will sort out indentation for you.  I prefer IDLE to gedit for python scripting.

---

### Post by raydeen on 2009-06-19
Some languages use indentation for cosmetic purposes (makes it easier to read and debug). Python requires it and it needs to be consistent. The convention is 4 spaces, but you could use anything as long as it's consistent throughout your code.

---

### Post by ioabs on 2009-06-22
Anyone who is interested here is the update program, it runs well now, but any suggestions to make it better are appreciated:


#This program is my first attempt at a computer program beides hello world
# - don't be hatin'
#I am attempting to write a python program that can serve as a reference 



usrname = raw_input("enter username:")

while usrname != "ben":
    usrname = raw_input("try again: ")


print "This program is designed as a reference for basic python commands"
print "                 written by Ben"
print
while 1 < 5:
    print "What are you having trouble remembering:"
    print "1.)how do I accept user input"
    print "2.)what are the mathematical operators"
    print "3.)what is the syntax of the if operator "


    numchoice = input("please input the corresponding number: ")

    
    if numchoice == 1:
            print
            print
            print "for strings, use the command variable$=raw_input('askuser:')"
            print
            print "for numbers  variable=input('askuser:')"
            print
            print
    elif numchoice == 2:
            print
            print
            print "Mathematical operators:"
            print
            print "addition +    subtraction -   exponents **   modulo %  division /"
            print
            print
    elif numchoice == 3:
            print
            print"If variable booleanoperator variable colon  i.e  if num <1:"
            print"elif variable booleanoperator variable colon  i.e. elif num>1:"
            print"else colon i.e. else:"
            print
            print
    else:
            print "The character(s) you entered are not valid - pick an number 1-3"
            print

---

