---
title: "simple instructions please"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by maxgt1 on 2008-12-23
Install goes great,connect to internet wirelessly great,install updates great.
Then problems i need easy to understand instructions covering nvidia drivers (everytime i install them i get a blank screen),
connecting an xp pc via ethernet to ubuntu pc to share internet connection.
I see posts saying install samba, (how do i configure it )
I am very new to this and have only been trying for two weeks,
any links or help would be greatly appreciated.
Thanks

---

### Post by Thelasko on 2008-12-23
> **maxgt1 said:**
> I see posts saying install samba, (how do i configure it )
I am very new to this and have only been trying for two weeks,
any links or help would be greatly appreciated.
Thanks

I recommend the [system-config-samba]("http://packages.ubuntu.com/intrepid/system-config-samba") package for that.  It provides a simple user interface for configuring samba.

P.S. keep in mind that Samba users are not the same as system users.
P.P.S. Sharing an internet connection is called a "bridge" and shouldn't require samba to my knowledge.
P.P.P.S [Here's documentation on how to setup a bridge.]("https://help.ubuntu.com/community/BridgingNetworkInterfaces")  I've never done it myself, so I can't be much more help.  Sorry

---

### Post by Titan8990 on 2008-12-23
> Then problems i need easy to understand instructions covering nvidia drivers (everytime i install them i get a blank screen),


Have you tried System -> Administration -> Restricted Drivers Manager?


> connecting an xp pc via ethernet to ubuntu pc to share internet connection.


Who is going to bridge the connection, the xp or the linux machine? Does either machine have two NICs? Have you considered just buying a router or switch? Building a computer to function as a gateway to the internet is somewhat of an advanced topic.


> I see posts saying install samba, (how do i configure it )


It is really easy. To install samba copy and paste in to the terminal:


sudo apt-get install samba


Then you can right click on folders and select sharing, exactly like you would in Windows.

---

### Post by bodhi.zazen on 2008-12-23
If you want to install the nvidia drivers you can use Envy :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Samba has a few tricks. You do not need to use the command line, just right click a directory in nautilus and select share. In the next windows install samba. Log out and back in, then re-share the directory.

You need to have rw permission on files you want to share (x on directories). In general this is easy for a directory in your home directory.

DO NOT share your entire home directory.

---

### Post by maxgt1 on 2008-12-23
thank you for your swift replies, i will try your suggestions

---

### Post by Titan8990 on 2008-12-23
Bodhi, I was under the impression that Envy was a dead project and it no longer had support in Ubuntu passed 8.04. Is this incorrect?

---

### Post by bodhi.zazen on 2008-12-23
> **Titan8990 said:**
> Bodhi, I was under the impression that Envy was a dead project and it no longer had support in Ubuntu passed 8.04. Is this incorrect?

I think it is still in development.

It is in the intrepid repos :

[http://packages.ubuntu.com/search?keywords=envy&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=envy&searchon=names&suite=intrepid&section=all)

---

### Post by anewguy on 2008-12-23
I used the envyng package in both 8.04 and 8.10 and it still worked for me - don't know if that helps others.

BTW - Bohdi - I finally have a very simple ubuntu server running so that I share a single hard disk at the server - kind of a poor mans NAS I guess.  Don't know what I'm doing yet - just followed another thread and got it going thanks to the great support here on the forums!!

dave :)

---

### Post by bodhi.zazen on 2008-12-23
> **anewguy said:**
> BTW - Bohdi - I finally have a very simple ubuntu server running so that I share a single hard disk at the server - kind of a poor mans NAS I guess.  Don't know what I'm doing yet - just followed another thread and got it going thanks to the great support here on the forums!!

dave :)

w00t !!!

---

