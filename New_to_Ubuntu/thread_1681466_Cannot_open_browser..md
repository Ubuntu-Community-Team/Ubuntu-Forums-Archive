---
title: "Cannot open browser."
date: 2011-02-04
forum: New to Ubuntu
---

### Post by burned sausage on 2011-02-04
This is my first time with Ubuntu):P and I am struggling to get onto the internet.It says my network connection is O.K. but when I try to open Firefox it says failed to connect.It worked when I first downloaded Ubuntu because I installed a music player.I am running Windows 7.Please be gentle.

---

### Post by dmizer on 2011-02-04
I moved this to the "Absolute Beginner" section. You should find plenty of friendly people to help you here.

---

### Post by wicxity on 2011-02-04
Sounds similar to the problem I was facing, what type of connection are you running?

---

### Post by burned sausage on 2011-02-04
> **wicxity said:**
> Sounds similar to the problem I was facing, what type of connection are you running?

It is a wired connection.I think it may be solved because I was having a problem opening a browser on Windows 7 so I rang my supplier up and they told me to disable then enable my LAN settings and it worked on Windows 7 so I am going onto Ubuntu now to see if that was the problem.Will let you know the outcome.

---

### Post by burned sausage on 2011-02-04
> **burned sausage said:**
> It is a wired connection.I think it may be solved because I was having a problem opening a browser on Windows 7 so I rang my supplier up and they told me to disable then enable my LAN settings and it worked on Windows 7 so I am going onto Ubuntu now to see if that was the problem.Will let you know the outcome.

It has not solved the problem.What amazes me is the fact that it is showing that the wired connection is active and working but when you try to open the browser,nothing.

---

### Post by burned sausage on 2011-02-04
> **dmizer said:**
> I moved this to the "Absolute Beginner" section. You should find plenty of friendly people to help you here.

Thank you.

---

### Post by Tyggna on 2011-02-04
This might help us figure out what's going on:

open up a terminal (it should be somewhere in your applications list) and type in the name of your browser.  Copy what it prints out there and paste it into the forums

So, if you're running firefox do:
accessories->terminal
[username@computername ~]$ firefox<enter>
<stuff we want printed here>

if it's epiphany, then replace firefox with epiphany

---

### Post by Tyggna on 2011-02-04
Also, the way to do the exact same thing you did in Windows in Linux is to open a terminal and type:

sudo dhclient

and then put in your password

---

### Post by burned sausage on 2011-02-05
Problem solved.After searching for ages I found a link to my ethernet cable and clicked that and now it works fine,.I will now download Google earth.Thamks for all you help.

---

