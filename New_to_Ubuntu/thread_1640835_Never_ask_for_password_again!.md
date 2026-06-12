---
title: "Never ask for password again!"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by thexnightmare on 2010-12-08
Dear all,
How can I make ubuntu not asking me for the password each time I make new change to the system?
Thx

---

### Post by slick666 on 2010-12-08
Does this work for you?

[https://help.ubuntu.com/community/AutoLogin#For%20Ubuntu%2010.04%20%28Lucid%20Lynx%29]("https://help.ubuntu.com/community/AutoLogin#For%20Ubuntu%2010.04%20%28Lucid%20Lynx%29")

---

### Post by sydbat on 2010-12-08
He's asking how to disable the password protocols when installing software, changing system settings, etc. I do not think it is possible (although I have been know to be wrong before). And even if it were, it is like asking how to become root...a taboo topic here.

---

### Post by philinux on 2010-12-08
> **thexnightmare said:**
> Dear all,
How can I make ubuntu not asking me for the password each time I make new change to the system?
Thx

Hi,

That is not a good idea at all. It is like it is because that is ubuntu's security model which makes for a secure system.

Please see this.
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by HermanAB on 2010-12-08
Howdy,

There are many good reasons why Unix systems are paranoid about passwords.  You will eventually get used to it.

---

### Post by thexnightmare on 2010-12-08
sydbat: You are totally right, but why it is a taboo?
So, there is no way to disable it?

---

### Post by matt_symes on 2010-12-08
Hi

> How can I make Ubuntu not asking me for the password each time I make new change to the system?

You _really_ don't want to circumvent that protection. It is there to keep your computer safe. It is one of the fundamental pillars of Linux security. It takes next to no time to enter your password.

You need to move away from that windows mentality.

Kind regards

---

### Post by sydbat on 2010-12-08
> **thexnightmare said:**
> sydbat: You are totally right, but why it is a taboo?
So, there is no way to disable it?Read the link in philinux's post.

---

### Post by thexnightmare on 2010-12-08
mmmmm ok guys, can I just make some software run without asking for passwords?

---

### Post by matt_symes on 2010-12-08
Hi> 

You are totally right, but why it is a taboo?

Alot of new people here have just moved over from windows and have a certain way of doing things. They also expect new operating systems like Ubuntu to work in a similar way.

However this is a misconception because they do not act in a similar way. There  are some fundamental differences in how one should use the different OS's. 

A change of mindset is needed to use Linux as it was designed to be used and not how it is expected to be used after moving from different operating systems.

Linux was designed to be used this way and is pretty secure because of it. 

Kind regards

---

### Post by amsterdamharu on 2010-12-08
What program would you like to run without asking for password?

It is forum policy not to advice on running/logging in as root (Administrator for windows) because that is how malicious software and user mistakes can easily mess up your entire system.

It is however possible to run some programs as root without it asking for password. Like when you want to install or software without it asking you for a password you can:
Open up a terminal and type the following command:
```
sudo visudo
```type your password, at the end of the file you type the following line (copy and paste (paste with clicking the scroll button of your mouse in terminal)):
```
yourUser ALL=NOPASSWD: /usr/sbin/synaptic
```Press control + o 
Press enter
Press control + x
Now when you start Package manager or synaptic package manager it should not ask you for a password.

I would recommend removing that line later when you're not playing around installing programs so much anymore.

---

### Post by thexnightmare on 2010-12-08
Thx all, solved and cleared

---

