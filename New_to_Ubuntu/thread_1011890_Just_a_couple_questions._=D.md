---
title: "Just a couple questions. =D"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Bunx on 2008-12-15
This may sound stupid so please bear with me. I have just changed from XP to Ubuntu and i'm loving every second of it. It's faster, i'm not swinging Katanas at viruses anymore, generally having fun with my computer again. I put in a DVD that had all of my music on it and when I tried to eject it, it came out, but then sucked the loading tray back in again. WHY?? Also, I would appreciate it if someone could give me a link or add me on MSN as to how to install anything on Ubuntu. I tried Google and all the links to the Monkey Blog tutorial send me to an empty domain address. =|

---

### Post by taurus on 2008-12-15
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by PocketDog on 2008-12-15
There's no better place to start than [here](http://ubuntuforums.org/showthread.php?t=801404)! Installing software is a matter of simply opening Synaptic package manager, searching or browsing through it, ticking the software you want and clicking apply.

---

### Post by Michael.Godawski on 2008-12-15
[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)  <--- still working on it :p

Feel free to ask. There are no stupid questions.

---

### Post by Bunx on 2008-12-15
Well that solves my software installing questions, anyone care to tell me why my CD drive is playing peek-a-boo with me?

---

### Post by Michael.Godawski on 2008-12-15
>  			 		   		 		 		Well that solves my software installing questions, anyone care to tell me why my CD drive is playing peek-a-boo with me?


It is a bug:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316)

Go to System > Software Sources > Updates > check proposed.

Then reload.

Then open the terminal: applications > accessories > terminal 
and run
```
sudo apt-get update
sudo apt-get upgrade
```.
Restart perhaps.

Have a look at the package udev 129-9 or newer during the update. This should fix this.

---

### Post by fluxlizard on 2008-12-15
I don't know about the cd peekaboo, but sometimes my cd drive won't give it up when I push the button. If I right click on the icon for the cd on the desktop and select eject from the menu, it works fine. That might help your situation as well.

---

### Post by Bunx on 2008-12-15
> **fluxlizard said:**
> I don't know about the cd peekaboo, but sometimes my cd drive won't give it up when I push the button. If I right click on the icon for the cd on the desktop and select eject from the menu, it works fine. That might help your situation as well.

I tried that once I realised that things weren't right but to no avail. Thank you though. =)

Michael.Godawski, in my taskbar, the red arrow with the exclamation mark says "There are 161 updates available". Should I just install those?

---

### Post by Michael.Godawski on 2008-12-15
> Michael.Godawski, in my taskbar, the red arrow with the exclamation mark says "There are 161 updates available". Should I just install those?

Red means good, red means [COLOR=Red]**important**[/COLOR], yes :p you should install them probably you will have to restart after they are all installed.

Report back when you have done it.

---

### Post by Bunx on 2008-12-15
Haha, i'm too used to Windows. I remember turning off the updates system process in the administration area in Control Panel because all the updates were crap. :p I downloaded and installed them, thanks heaps. :D

Also, while i'm asking questions and getting awesome answers, i'm downloading a torrent on Transmission and it's SOOOOOOO SLOWWWWWWWW. I read something about Ubuntu and how it has no ports open or something like that. Anyone want to point me in the right direction? The torrent has a solid amount of seeders so it's nothing to do with that. It's times like this that I miss uTorrent. :(

---

### Post by trentscott4 on 2008-12-15
> **Bunx said:**
> Haha, i'm too used to Windows. I remember turning off the updates system process in the administration area in Control Panel because all the updates were crap. :p I downloaded and installed them, thanks heaps. :D

Also, while i'm asking questions and getting awesome answers, i'm downloading a torrent on Transmission and it's SOOOOOOO SLOWWWWWWWW. I read something about Ubuntu and how it has no ports open or something like that. Anyone want to point me in the right direction? The torrent has a solid amount of seeders so it's nothing to do with that. It's times like this that I miss uTorrent. :(

To open the port, you probably need to check your router, not Ubuntu. Forward TCP/51413 to your Ubuntu PC.  To find the IP of your Ubuntu machine on your network, run from a terminal:

```
sudo ifconfig
```

Good luck!

Trent

---

### Post by Bunx on 2008-12-15
Yes well how do I do that? As far as networks go, i'm pretty ignorant. I don't even know my router's IP. Would love a tutorial or some step-by-step instructions! :)

---

### Post by Soriano on 2008-12-15
This link should help you out.  You'll need to look on your router and find your make/model number and then you can follow the tutorial on this website:

[http://www.portforward.com/english/routers/port_forwarding/routerindex.htm]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm")

---

### Post by Bunx on 2008-12-15
My router is a Thomson TG585 v7, which I could not find on that list...:-k

---

### Post by Soriano on 2008-12-15
From what I can see your router should be exactly like this one:

[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/Utorrent.htm]("http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch585/Utorrent.htm")

There is one difference though.  Where the tutorial says you enter the TCP or UDP ports under 'ANY' in the drop down box on the menu, you can't select 'ANY', you have to select 'TCP or 'UDP' in the drop down menu.

Also this tutorial is not for Transmission it is for uTorrent.  I am not familiar with Transmisssion interface but the idea is the same in principal.  You'll need to make sure that Transmission is facing an open port which I am guessing you can pick somewhere in one of the menu's.  And then set up the port forwarding for it similar to the way it is done in the tutorial.  If its your first time you may need to fool around a bit and do a bit of research but this should give you an idea.

Also you may want to read this to better understand port forwarding:

[http://www.portforward.com/help/portforwarding.htm]("http://www.portforward.com/help/portforwarding.htm")

---

### Post by Bunx on 2008-12-15
So if I do this, Transmission will give me back my proper download speed? Because 30kb/s is anal...

---

### Post by Soriano on 2008-12-15
It should increase your speed if all is done appropriately.

---

### Post by Bunx on 2008-12-15
Okay thank you heaps. :D

---

