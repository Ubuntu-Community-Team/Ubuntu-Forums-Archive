---
title: "Help with hotmail"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by trazan87 on 2009-06-04
Hey! I've been around on countless forums and FAQs, but i've been unable to find a solution to my problem.
I'm trying to get Evolution to deliver my hotmail, and i've tried both gotmail and hotway. The problem is that when i try to install the hotway package in the terminal this is what happens

:~$ sudo apt-get install hotway hotsmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway :(
:~$

I'm running the Ubuntu 9.04 Jaunty Jackalope

Take care!

---

### Post by victorbrca on 2009-06-04
What do you get if you do this?

```
sudo aptitude search hotway
```

---

### Post by Paqman on 2009-06-04
Microsoft have finally started loosening up their restrictions on Hotmail accounts, so you should need to install weird stuff to use it with Evolution any more.

Try these settings:
Receiving email
Server Type = POP
Server = pop3.live.com
Secure Connection = SSL encryption

Sending email
Server Type = SMTP
Server = smtp.live.com
Secure Connection = TLS encryption

I can definitely fetch mail over POP3 from my old Hotmail account, but I haven't tried sending.

---

