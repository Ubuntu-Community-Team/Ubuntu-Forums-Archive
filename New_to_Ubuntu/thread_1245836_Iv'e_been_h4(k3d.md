---
title: "Iv'e been h4(k3d"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-08-21
Yes, the use of a poor password and not changing the ssh port was a bad idea, now two mornings I've waken up with my ipod touch (which is jailbroken and has veency installed) reading ```
Remote Access Request

Accept connection from 190.166.8.74? "(and the next day)" 82.215.43.19?

Accept

Reject
``` 

Now I do not have port forwarding to my ipod especially not on port 5900, but I have a small server with ports 80, 22, 21, and a couple more but they cannot be hacked simply, could you give me a few tips to help secure my server and ultimately all of my crap thats connected.

Also I think what they did was use a bruteforce against my ssh port, ssh into my pc, then scan my network for my ipod, then tried to connect to it through vnc, though my server, trough ssh, through the internet!

So heres what I need to know:

How do I beef up my security? (A new password duh! and how do I change my ssh password from my user login password?

How do I change my ssh and ftp ports?

And is ssh really safe?

:confused:

Thanks in advance. (ps, I posted there IP's so you could hack there windoze pc and show them the wrath of UBUNTU! Just kidding, dont get any ideas.)

---

### Post by R_W322 on 2009-08-21
Im not particularly sure how to help you here but I can give you new Ideas for a beefed up password never use a word from the dictionary instead do something this

Io1Rc4m
I own 1 Rusty car 4 me

or 

mFtisGwBW2

my favorite tshirt is Green with Brent Who 2? (packer joke)

---

### Post by theaaronc on 2009-08-21
One thing you may want to consider is using iptables, a firewall installed by default with Ubuntu. Of course it won't help with the password issue but it's a handy way to lock down a lot of things on your system.

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)


As far as passwords go, one thing I'll do for password ideas is watch license plates on vehicles, either in real life or on tv shows/movies. I've found that one is not usually long enough (in the US at least) to make a strong password length. But if you add two or more together you get a fairly random alphanumeric string. You can use that alone or add it to another phrase like R_W322 suggested.

---

### Post by Arla on 2009-08-21
Another possible for passwords is if you have any electronics around that has serial numbers on it that you ALWAYS have around when you need to log in.

When I was in college I always had my calculator on me (Math major) so used the make, model, and serial number (with a few numbers replaced with appropriate letters) as my password, gave me a 20 character password, I've long since lost/misplaced/retired the calculator, but still remember and use that password today.

For example, if you always have your Ipod around, use that (if they have serial numbers that are visible)

---

### Post by Katalog on 2009-08-21
As far as passwords go, I installed Revelation a while back and use it to generate random 12-20 character (depends on how sensitive the thing I'm protecting is as to the length) passwords for all my logins and applications. Only gotcha with that strategy is 1) making sure you have a good master password to unlock the database in the first place and 2) making sure you back up the database regularly, because if you ever lose it you're in for a real fun time getting passwords reset for all your stuff. :P

---

