---
title: "Help with a Python 2.7 syntax error"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by PythonMan on 2011-06-14
Hi guys I am trying to make a game with Python programming language for a school homework piece. To impress teacher I am trying to display knowledge that I have researched on Internet and am having trouble with one area of the program.

print " Welcome"
name = raw_input ("Please enter your name.")
print "Hello " + name
print "Do you want to play a game " + name
answer = raw_input (" Please enter either Yes or No including capital."

if answer == [COLOR="Green"]Yes:[/COLOR]
                    print " Ok lets play Too High Too Low."
                    [COLOR="red"]goto a[/COLOR]
else:
                    print "Okay goodbye"
                    [COLOR="blue"]sys.quit()[/COLOR]




[COLOR="black"]a[/COLOR]
print "Welcome to the game Too High Too Low."
raw_input ()

I want to have the program ask the user if they want to play the game and whether they answer Yes or No affects the programs running. If the user says yes i want to it to skip to a later area of the program marking by the lower case a coloured red. If the user says no I want the program to close coloured blue. I cannot check if these portions of the program work as Python does not let me run the program because of a basic syntax error coloured green.
If you guys could help with any of these's three problems i would be very grateful.
Python Man :D:D:D

---

### Post by Nytram on 2011-06-14
You can rearrange the logic to avoid using the **goto** command, and **Yes** needs to be in quotes, this is how I'd do it:

> 
if answer == "No":
 print "Okay goodbye"
 sys.quit()

<rest of program here, when user types yes>
print " Ok lets play Too High Too Low."



HTH

---

### Post by GWBouge on 2011-06-14
1) I see a few errors in there.  As for the one you're asking about, sys doesn't have a quit attribute, you're looking for sys.exit().  I don't see sys imported ... did you?

2) When asking about an error, please provide the error python gives you.

3) Please put code in CODE tags (click the # button) to retain indentation

4) Does python even have a goto command?  If it does, avoid it at all costs.  Read up on Object Oriented Programming.

---

### Post by 3rdalbum on 2011-06-14
Firstly, the number of close brackets must equal the number of open brackets. You're missing a close bracket.

The raw_input function returns a string, not a boolean - in other words, the 'answer' variable will contain the string "Yes", "yes", "y" or something like that, but it will not contain *Yes* (boolean). You should make sure you tell the user to type y or n, and then put:

```
if answer == "y":
```

I don't think Python supports goto. For a simple program I'd put in a function call that contains the game's logic.

Also, sys.exit() is the function you are looking for, and you need to *import sys* before you can use it.

Now, no more homework help.

---

### Post by PythonMan on 2011-06-14
Thanks a lot to all, special mention 3rd album for fully solving my problem.
Python Man :):):):):):):):)

---

### Post by lisati on 2011-06-15
Thread closed. From the [code of conduct]("http://ubuntuforums.org/index.php?page=policy"):
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

