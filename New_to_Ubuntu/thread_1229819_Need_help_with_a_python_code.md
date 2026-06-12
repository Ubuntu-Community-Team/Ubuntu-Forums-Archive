---
title: "Need help with a python code"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by leedrew on 2009-08-02
Hi I'm new to this site and also new to writting code. and am in school at ITT tech and I really need help with how to write a while code and get it running so far I can't get it to run and don't know why. Help!
 
_[COLOR=#0066cc][/COLOR]_ 
_[COLOR=#0066cc]def main():[/COLOR]_
_[COLOR=#0066cc]endOrder = "no"[/COLOR]_
_[COLOR=#0066cc]while endOrder == "no":[/COLOR]_
_[COLOR=#0066cc]totalBurger = 0[/COLOR]_
_[COLOR=#0066cc]totatlFry = 0[/COLOR]_
_[COLOR=#0066cc]totalSoda = 0[/COLOR]_
_[COLOR=#0066cc]endOrder = 'no'[/COLOR]_
 
_[COLOR=#0066cc]while endOrder == 'no':[/COLOR]_
_[COLOR=#0066cc]print 'Enter 1 for Yum burger'[/COLOR]_
_[COLOR=#0066cc]print 'Enter 2 for Yum Fries'[/COLOR]_
_[COLOR=#0066cc]print 'Enter 3 for Yum soda'[/COLOR]_
_[COLOR=#0066cc]item = input ('Enter now -> ')[/COLOR]_
_[COLOR=#0066cc]if item == 1:[/COLOR]_
_[COLOR=#0066cc]totalBurger = getBurger (totalBurger)[/COLOR]_
_[COLOR=#0066cc]elif item == 2:[/COLOR]_
_[COLOR=#0066cc]totalFry = GetFry (totalFry)[/COLOR]_
_[COLOR=#0066cc]elif item == 3:[/COLOR]_
_[COLOR=#0066cc]totalSoda = getSoda (totalSoda)[/COLOR]_
_[COLOR=#0066cc]else:[/COLOR]_
_[COLOR=#0066cc]print 'try again'[/COLOR]_
_[COLOR=#0066cc]endOrder = raw_input ('Are you done with your order? ')[/COLOR]_
_[COLOR=#0066cc]totalBill = calcTotal (totalBurger, totalFry, totalSoda)[/COLOR]_
_[COLOR=#0066cc]print ('Your total bill is')[/COLOR]_
 
_[COLOR=#0066cc]def getBurger(totalBurger):[/COLOR]_
_[COLOR=#0066cc]burgerCount = input ('Enter the amount of Yum burgers You would like')[/COLOR]_
_[COLOR=#0066cc]Enter - 1[/COLOR]_
_[COLOR=#0066cc]print ('Enter the number of burgers you want')[/COLOR]_
_[COLOR=#0066cc]totalBurger = burgerCount + totalBurger * .99[/COLOR]_
_[COLOR=#0066cc]return totalBurger[/COLOR]_
 
_[COLOR=#0066cc]def getFry(totalFry): [/COLOR]_
_[COLOR=#0066cc]fryCount = input ('Enter the total number of fries you would like ')[/COLOR]_
_[COLOR=#0066cc]totalFry = fryCount + totalFry * .79[/COLOR]_
_[COLOR=#0066cc]return totalFry[/COLOR]_
_[COLOR=#0066cc]def getSoda(totalSoda):[/COLOR]_
_[COLOR=#0066cc]sodaCount = input ('Enter the total number of soda you would like ')[/COLOR]_
_[COLOR=#0066cc]totalSoda = sodaCount + totalSoda * 1.09[/COLOR]_
_[COLOR=#0066cc]return totalSoda[/COLOR]_
_[COLOR=#0066cc]def totalBill(totalBurger, totalFry, totalSoda):[/COLOR]_
_[COLOR=#0066cc]calcTotal = totalBurger + totalFry + totalSoda[/COLOR]_
_[COLOR=#0066cc]return totalBill[/COLOR]_
_[COLOR=#0066cc]main()[/COLOR]_

---

### Post by leedrew on 2009-08-02
where are the Quick reply icons I don't see any on the page at all this is so frustrating!

---

### Post by doas777 on 2009-08-02
well first off, confirm that this is the correct indentation:
```

def main():
    endOrder = "no"
    while endOrder == "no":
        totalBurger = 0
        totatlFry = 0
        totalSoda = 0
    
        endOrder = 'no'
        while endOrder == 'no':
            print 'Enter 1 for Yum burger'
            print 'Enter 2 for Yum Fries'
            print 'Enter 3 for Yum soda'
            item = input ('Enter now -> ')
        if item == 1:
            totalBurger = getBurger (totalBurger)
        elif item == 2:
            totalFry = GetFry (totalFry)
        elif item == 3:
            totalSoda = getSoda (totalSoda)
        else:
            print 'try again'
            
        endOrder = raw_input ('Are you done with your order? ')
        
    totalBill = calcTotal (totalBurger, totalFry, totalSoda)
    print ('Your total bill is')

def getBurger(totalBurger):
    burgerCount = input ('Enter the amount of Yum burgers You would like')
    Enter - 1
    print ('Enter the number of burgers you want')
    totalBurger = burgerCount + totalBurger * .99
    return totalBurger

def getFry(totalFry):
    fryCount = input ('Enter the total number of fries you would like ')
    totalFry = fryCount + totalFry * .79
    return totalFry

def getSoda(totalSoda):
    sodaCount = input ('Enter the total number of soda you would like ')
    totalSoda = sodaCount + totalSoda * 1.09
    return totalSoda
    
def totalBill(totalBurger, totalFry, totalSoda):
    calcTotal = totalBurger + totalFry + totalSoda
    return totalBill

main()

```

---

### Post by leedrew on 2009-08-02
UMMM how do I do that? please

---

### Post by doas777 on 2009-08-02
since this is homework, I won't give you any code, but look closely at the error message. what does it say?

---

### Post by leedrew on 2009-08-02
I indented but I get unexpected indent when I go to run it

---

### Post by doas777 on 2009-08-02
> **leedrew said:**
> UMMM how do I do that? please

uhh, look at your code. does that look right?
python uses indents for logic flow, but when you posted the code, you didn't put it in a code block so all the indentation was removed. what did the code look like when it still had indents?

the easiest way would be to copy the code into a "code" block when you are posting it to the forum.

---

### Post by doas777 on 2009-08-02
> **leedrew said:**
> I indented but I get unexpected indent when I go to run it

on what line? look at the line, and try to figure out what the message is complaining about.
I use geany for python code. you can find it in the repositories.

I have to ask, is this your code?

---

### Post by leedrew on 2009-08-02
oh ok Like so ?
 
def main():
            endOrder = "no"
                while endOrder == "no":
                        totalBurger = 0
                        totatlFry = 0
                        totalSoda = 0
                        endOrder = 'no'
            
                while endOrder == 'no':
                    print 'Enter 1 for Yum burger'
                    print 'Enter 2 for Yum Fries'
                    print 'Enter 3 for Yum soda'
                        item = input ('Enter now -> ')
                if item == 1:
                totalBurger = getBurger (totalBurger)
                elif item == 2:
                totalFry = GetFry (totalFry)
                elif item == 3:
                totalSoda = getSoda (totalSoda)
                else:
                    print 'try again'
                    endOrder = raw_input ('Are you done with your order? ')
                    totalBill = calcTotal (totalBurger, totalFry, totalSoda)
                    print ('Your total bill is')
            
def getBurger(totalBurger):
            burgerCount = input ('Enter the amount of Yum burgers You would like')
            Enter - 1
            print ('Enter the number of burgers you want')
            totalBurger = burgerCount + totalBurger * .99
            return totalBurger
              
def getFry(totalFry):              
            fryCount = input ('Enter the total number of fries you would like ')
            totalFry = fryCount + totalFry * .79
            return totalFry
def getSoda(totalSoda):
              sodaCount = input ('Enter the total number of soda you would like ')
              totalSoda = sodaCount + totalSoda * 1.09
              return totalSoda
def totalBill(totalBurger, totalFry, totalSoda):
              calcTotal = totalBurger + totalFry + totalSoda
              return totalBill
main()"

Oh this is after doing some indenting but still get the unexpected indent message

---

### Post by benj1 on 2009-08-02
first off when posting code put it in code tags (the # symbol) makes it easier to read, and doesnt mess up python either (preserves white space)

second you dont need 2 'while endOrder == 'no':' loops

---

### Post by leedrew on 2009-08-02
This is what the teacher had us do in class so I'm going by what He had done to the code 
Ps don't understand the white space thing.

---

### Post by leedrew on 2009-08-02
This is the code the teacher had and I don't know if He was able to get it to run
P.S. not sure what the white space thing is about please explain TY.

---

### Post by doas777 on 2009-08-02
> **benj1 said:**
> first off when posting code put it in code tags (the # symbol) makes it easier to read, and doesnt mess up python either (preserves white space)

second you dont need 2 'while endOrder == 'no':' loops

it looks like a nested loop. prompt for type of food, then prompt for number of items repeatedly.

OP: 
please reply, and click the '#' icon on the message window. then between the code tags, paste the code. it will look like my initial reply, if you preview it, with the code in a white box.

---

### Post by doas777 on 2009-08-02
[http://www.clarejohn.com/python1/python1.html](http://www.clarejohn.com/python1/python1.html)
check out chapter for for flow control and whitespace.

---

### Post by benj1 on 2009-08-02
> **leedrew said:**
> This is the code the teacher had and I don't know if He was able to get it to run
P.S. not sure what the white space thing is about please explain TY.

whitespace is important in python

```
def foo (bar):
print bar
```
wont do the same as
```

def foo(bar):
    print bar

```
its basically like brackets in c.
without whitespace your program wont work, thats your problem.

@doas777
the first loop just sets all the variables to 0, and that loop will finish at the same time as the second loop, its not wrong just a bit redundant.

---

### Post by benj1 on 2009-08-02
> **doas777 said:**
> [http://www.clarejohn.com/python1/python1.html](http://www.clarejohn.com/python1/python1.html)
check out chapter for for flow control and whitespace.

your link is broken


[http://www.greenteapress.com/thinkpython/thinkpython.html]("http://www.greenteapress.com/thinkpython/thinkpython.html")

this is quite a good intro too

---

### Post by leedrew on 2009-08-02
that link is broken also I tried them both

---

### Post by doas777 on 2009-08-02
interesting. they both work fine for me. weird.

anyway, just google 'python tutorial flow control' and whitespace will be explained on whatever tutorial you land on. if it isn't, then it's a poor tutorial.

---

### Post by leedrew on 2009-08-02
This is the third time I've tried to reply back Am hoping it goes thru this time Thanks for the help Am looking intoo the thinkpython again thanks.
I'm really green when it comes to code writting as you can tell.

---

