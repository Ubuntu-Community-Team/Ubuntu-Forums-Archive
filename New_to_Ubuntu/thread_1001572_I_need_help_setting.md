---
title: "I need help setting"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by brentdavis29 on 2008-12-04
This is my first time trying Linux, and I need help in a big way.

I've been wanting to try Linux for a LONG time, but I've had a hard time leaving XP. Recently, I was was gifted a computer from my brother which I've installed Ubuntu on. But, the catch is that it didn't come with a monitor, mouse, keyboard, etc.

Is there a way for me to connect the computer with Ubuntu to my home network, and then access the Ubuntu desktop through my laptop's monitor/peripherals? Ideally, it would be cool if I could switch back and forth from the XP desktop on my laptop to the Ubuntu desktop kind of like switching between windows using ALT-Tab. 

Additionally, if possible I'd like to use the big hard drive on the Ubuntu machine to hold all of my music, while accessing it from Windows.

This may be a super simple thing for you, but I've literally searched for _hours_, and I can't figure it out. Here are some details that may or may not be helpful:
[LIST]
[*]The Ubuntu machine is plugged into my Linksys WCG200 router
[*]I've tried to experiment with SSH, and can't figure it out. (I can't figure out how to set up the SSH server on the Ubuntu box, and I don't know how to access it from the XP box via Putty, and such. The instructions just don't make sense to such a newbie)
[*]I don't know ANYTHING about commands in the Linux terminal, so please keep that in mind when asking me to do this or that
[/LIST]

---

### Post by nakama85 on 2008-12-04
> **brentdavis29 said:**
> This is my first time trying Linux, and I need help in a big way.

I've been wanting to try Linux for a LONG time, but I've had a hard time leaving XP. Recently, I was was gifted a computer from my brother which I've installed Ubuntu on. But, the catch is that it didn't come with a monitor, mouse, keyboard, etc.

Is there a way for me to connect the computer with Ubuntu to my home network, and then access the Ubuntu desktop through my laptop's monitor/peripherals? Ideally, it would be cool if I could switch back and forth from the XP desktop on my laptop to the Ubuntu desktop kind of like switching between windows using ALT-Tab. 

Additionally, if possible I'd like to use the big hard drive on the Ubuntu machine to hold all of my music, while accessing it from Windows.

This may be a super simple thing for you, but I've literally searched for _hours_, and I can't figure it out. Here are some details that may or may not be helpful:
[LIST]
[*]The Ubuntu machine is plugged into my Linksys WCG200 router
[*]I've tried to experiment with SSH, and can't figure it out. (I can't figure out how to set up the SSH server on the Ubuntu box, and I don't know how to access it from the XP box via Putty, and such. The instructions just don't make sense to such a newbie)
[*]I don't know ANYTHING about commands in the Linux terminal, so please keep that in mind when asking me to do this or that
[/LIST]

um you could use VNC for a remote desktop experience. I recommend TightVNC
But If you just want it as a server use samba. Otherwise I don't fully understand your question. Could you rephrase it in anyway

---

### Post by nakama85 on 2008-12-04
:

---

### Post by Peter09 on 2008-12-04
Use FreeNX,
[http://freenx.berlios.de/](http://freenx.berlios.de/)

this will give you a remote desktop, its easy to install. The nice thing about FreeNx is that you do not need to login to remote machine locally before you can establish a remote desktop. VNC will require an existing session before you can login remotely.

---

### Post by Peter09 on 2008-12-04
To setup an ssh session, install openssh-server on the local machine 

```
sudo apt-get install openssh-server
```

You should then be able to get an ssh session from a remote linux machine

```
ssh -X <user name>@<machine name> xterm
```

I think Putty supports ssh on windows.

---

### Post by mapes12 on 2008-12-04
> Is there a way for me to connect the computer with Ubuntu to my home network, and then access the Ubuntu desktop through my laptop's monitor/peripherals? Ideally, it would be cool if I could switch back and forth from the XP desktop on my laptop to the Ubuntu desktop kind of like switching between windows using ALT-Tab.I use a KVM box to do this. See here: [http://en.wikipedia.org/wiki/KVM_switch](http://en.wikipedia.org/wiki/KVM_switch)

> Additionally, if possible I'd like to use the big hard drive on the Ubuntu machine to hold all of my music, while accessing it from Windows.This HowTo may help: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by PriceChild on 2008-12-04
Not useful right now... but if you manage to scrimp a monitor from somewhere, you'll *love* synergy: [https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

---

### Post by akshay.sulakhe on 2008-12-04
for network sharing try firestarter...Ubuntu has a archive of firestarter...if u have  router than its well and good...and if remote login is all u want...i will prefer ssh...also use command line whenerve possible to reduce load...

---

### Post by billgoldberg on 2008-12-04
> **brentdavis29 said:**
> 
Additionally, if possible I'd like to use the big hard drive on the Ubuntu machine to hold all of my music, while accessing it from Windows.

I have created a non terminal guide for that, it should take 2 minutes to set up:

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

---

