---
title: "downloaded Epiphany,no see"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by ub9876 on 2009-10-08
Why does this happen sometimes? I got Epihany from the repos
and its installed ok but it didnt show up on the Internet applications list.
Whats the scoop and how do I get it running and an icon
on the Desktop..???
9.04/Chrome or Fox

---

### Post by x C0MMAND0 x on 2009-10-08
First, check to see if you can run it from terminal to see if you actually have it installed.

Go to Applications > Accessories > Terminal and type "epiphany" without quotes.

If that works, then go to

System > Preferences > Main Menu > Internet 

and see if it is just unchecked.  If not, you can add it there.  Click on "New Item". 

Type - Application
Name - Epiphany
Command - epiphany
Comment - anything you want

That will add the launcher for you.

---

### Post by wojox on 2009-10-08
If all else fails reboot. I've had to do that on occasion with applications as well.

---

### Post by ankspo71 on 2009-10-08
Hi,
Like the others have said, you probably need to reboot in order to see it in the menu.

By any chance, did you install the package "epiphany"? I'm asking because that is a game. I believe epiphany-browser is the package you are looking for in Ubuntu 9.04.  In Karmic it's under something different .... (see below)

>  ( Ubuntu 9.10 karmic )
james@Ubuntu:~$ epiphany-browser
The program 'epiphany-browser' can be found in the following packages:
 * epiphany-gecko
 * epiphany-webkit
Try: sudo apt-get install <selected package>
epiphany-browser: command not found
james@Ubuntu:~$ 
James

---

### Post by mikewhatever on 2009-10-08
I think logging out and in would suffice, as xserver is restated in the process.

---

