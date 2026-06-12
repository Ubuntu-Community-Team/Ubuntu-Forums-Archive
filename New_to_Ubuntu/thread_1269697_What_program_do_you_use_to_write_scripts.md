---
title: "What program do you use to write scripts?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-18
Hi all!
I know it sounds a bit of an advanced thing, but actually I'd need just to modify a script adding something here 'n there, deleting something and so on. Best way to do so is to write dowwn a brand new script...but I miss the basics:
How do I do it practically? What program do I use, how do I save it to make it readable as a script and executable.
Text editor? Maybe...but saved as what?
Ty!;)

---

### Post by NoaHall on 2009-09-18
In Linux, extensions don't matter for scripts. Just make sure you have the shell you're going to launch it with linked at the start. Eg -

# ! /bin/bash

I use either Gedit, nano, or vi.

---

### Post by cmay on 2009-09-18
for example you want to write a perl script you write #! /usr/bin/perl. at the start as the very first thing . or a shellscript you could do something like #! /bin/sh 
then you make the file executable with chmod +x or chmod 755. +x is the best idea i reckon. then launch the script in the terminal and the startlinje will tell the shell what is being launched and it knows it is a script.  all the # sybols are comments so everything on that line is a comment that is ignored by the shell in the script. i use geany or gedit for all these things. nano is good also. vim i am about to learn but it takes some getting used to. 
good luck.-

---

### Post by webwiller on 2009-09-18
Ty guys!
I try it out and let you know tomorrow! tx again!

---

### Post by jzacsh on 2009-09-18
> **webwiller said:**
> Ty guys!
I try it out and let you know tomorrow! tx again!

you can also google or youtube even (*i'm a visual learner*) "shell scripting". there's an awesome amounts of resources out there just showing the basics of scripting. eg. the reason putting this on the top of your script will work:
> **NoaHall said:**
> 
# ! /bin/bash


or why **vi** (*after the reasonable learning curve*) is such an awesome, worthy, efficient editor (*for me at least.. i don't want to get anybody riled up*). Enjoy! :)

---

