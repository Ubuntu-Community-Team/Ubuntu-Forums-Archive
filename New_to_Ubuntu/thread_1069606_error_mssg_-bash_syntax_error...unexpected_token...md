---
title: "error mssg: -bash: syntax error...unexpected token.."
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Gelateria Punk on 2009-02-14
(SOLVED)
Got an error message
full line:
-bash: syntax error near unexpected token 'newline'


what can be done?  what does it mean?  why is it there?



Noob

---

### Post by x33a on 2009-02-14
what are you trying to do when this errors message is displayed?

paste the full command.

---

### Post by Gelateria Punk on 2009-02-14
I am trying to install a "driver" or something to use my M-audio ozone in Studio.  I found instructions, but I am not familiar with the command line stuff.  At one point in the instructions, I am asked to find an archive file in an application called "madfuload".  Here is the command that causes the error:
sudo tar xvfz <madfuload archive file>

I thought it might be because I didn't have madfuload in the right place.  It might also be because I never did anything like:
sudo get-app install madfuload
Also:  If you could describe EXACTLY the order of a line which should download and install a program, that would be awesome.  I am thinking the second command line I wrote is not correct.

---

### Post by cerealtx on 2009-02-14
its in the repositories, ```
supo apt-get install madfuload
``` should work just fine

---

