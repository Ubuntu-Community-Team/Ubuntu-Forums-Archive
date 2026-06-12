---
title: "CUPS Held for Authentication"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by gallay-charles on 2014-03-02
Hi,

I am trying to print something on a Printer which is configurer using CUPS. I was able to print anything from the GUI interface (the jobs are "Held for Authentication" so I just make a right click on them and select Authenticate which pop me a prompt where I have to put a username and a password), but I would like to know how I could do Using the terminal. I tried to use lp but there is no way to Authenticate me

Does any one have a solution to my problem.

Thanks for your Help

Charles

---

### Post by phidia on 2014-03-04
I'm not sure but it sounds like a permissions issue. You can add your user to lp by > gpasswd -a [user] lp

---

### Post by gallay-charles on 2014-03-07
Unfortunately this doesn't work.

The printer I want to use is in my school network. I am able to print using the GUI because a pop up window ask me to log-in with my school username and password. But I don't know how to print from the terminal. Cause I would like to make a script for printing some files.

Hope you can see what's my problem

thanks anyway for your help

Charles

---

