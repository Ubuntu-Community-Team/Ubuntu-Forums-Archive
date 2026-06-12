---
title: "Connect to windows network"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by dgel on 2007-11-17
Hi,

I have a pc that's connected to the internet via wireless and to another pc via a rj45 crosscable. On windows, i can simply log in and access the share on the other pc, no problem.
So i set up a static ip for the crosscable in ubuntu 7.10, pings fine. However, when i go to places->network, it asks for a password to connect to the other pc.
Now the other pc has three different accounts, all without passwords. My own pc (dual boot) has a windows with password, but when entering that password, it doesn't accept it.
Any ideas what I have to do to access the shares?

Na-Fiann

---

### Post by dgel on 2007-11-21
BUMP

Anyone?

---

### Post by cmnorton on 2007-11-21
Your Ubuntu system might have to be in the same domain as the Windows system. Basically your 127.0.0.1 entry in /etc/hosts would be 

node-name.domain.name node-name

Your user name for login into Windows probably has to be domain-name\user-name, and then the password for that user-name should work. 

You're going to have to experiment with this to get it to work.

---

### Post by jonandrews on 2007-11-22
I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.

---

### Post by A$h X on 2007-11-22
> **jonandrews said:**
> I've put my simple guide to integrating Ubuntu PC's into a wired Windows home network onto a website:

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)


Let me know if it is helpful.Really good guide jonandrews, very easy to understand.
However there is still a problem with samba and XP/ubuntu dual boot machines. Nothing to do with your guide though, just stating if any other users have any problems.

---

### Post by dgel on 2007-11-24
cmnorton:

Since I have little experience with this, I don't know what node-name etc should be. Also, my pc that dual boots is the only pc that uses a password, so it strikes me as odd that I am asked for one at all.

jonandrews:

Very nice guide, but it seemed to me that it was intended for use with dhcp on a router, whereas I am directly linked to the other pc via a crosscable. Thus, I have set the ip addresses manually.

[edit]
Also, I just read more of your guide, it is about making the ubuntu pc visible on the win boxes. My problem lies in what in your guide works out of the box: when I go to Places > Network, it takes a long time to load, and then asks for my username and password to login to guest@MSHOME, the latter being the name of the network. Thing is, I've never encountered this before on my windows boxes, I wasn't even aware that a guest account existed on MSHOME. And if this guest account has less privileges than normal accounts, I don't even want to login as guest.
ahh well
[/edit]

Na-Fiann

---

### Post by Rubaijat on 2008-01-12
Hi,

i haven't read any of the guides, but i actually didn't do anything to get it to work. I know its not much of a help, but have you tried not assigning the cross cable a static ip? Im connected to the internet through a wireless connection in ubuntu 7.10 and from ubuntu to a XP box through the cross cable. I just pluged it in and went to Places -> Network and the win box pop up.

Regards,
Rubi

---

