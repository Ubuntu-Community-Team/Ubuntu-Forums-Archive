---
title: "Remote Control Computing - Ubuntu"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Ravenshade on 2011-01-01
Hello there, 

[INDENT]Hello there, first of all, please allow me the freedom of saying, that I'm not exactly sure which prefix I should be using as this topic covers a variety of operating systems and areas, which I hope you guys can help me out with.[/INDENT]

I have three computers, a windows machine (which for some reason can no longer dualboot Ubuntu, I believe it has something to do with me having to forcefully rip Ubuntu out of it before. Grub) which is Windows XP this is generally the computer I work on for a variety of things.

The second computer is a netbook, acerOne, which I put the UNR distribution of Ubuntu onto it. This is the computer I like to use mostly and do most of my word processing, accounts, etcetera etcetera. 

The third computer is as of this moment, Windows XP... I do plan however on turning it into a server. (At least that's the theory) Hopefully using Ubuntu's Server edition. My problem arises from the fact that I have no monitor, keyboard or mouse for it, I do have an ethernet cable, a hub and a power cable. 

Therefore, the solution I need is to be able to remotely access the computer and manipulate it from another device, either Computer#1 or Computer#2 I'm fine with either or both. Is there some software out there for Ubuntu which would enable me to do this? Can anyone provide any insights? 

On a further note. I'm aware that I'm completely new to servers, this is an experimental exercise. 

Thanks for your helps and constructive comments. 
Ravenshade.

---

### Post by pqwoerituytrueiwoq on 2011-01-01
try the terminal server client app under Internet and use the ssh command for some command line work
i think you will need a temp setup for the install (monitor/keyboard)
remembering google is your friend

---

### Post by Ravenshade on 2011-01-01
> **pqwoerituytrueiwoq said:**
> try the terminal server client app under Internet and use the ssh command for some command line work
i think you will need a temp setup for the install 
remembering google is your friend

Fortunately I had googled... which lead me here...but the thread I was looking at was locked and abandoned since 2009. 

Though I will google the Terminal Server Client and see what I can dig up.

---

### Post by Ravenshade on 2011-01-02
After another Google search I come back asking a more refined question. 

1. Will this work for Ubuntu's Server edition (10.04)
2. Can I get something that works from computer to computer over a Lan connection instead of needing to go all the way out to a WAN and then all the way back in again.

---

### Post by Funkey Monkey on 2011-01-02
Hello Ravenshade,

There a a couple of ways to access a ubuntu computer (be it a server or not).

* Applications > Internet > **Remote Desktop Viewer **
* Applications > Internet > **Terminal Server Client**
* **SSH**
* **FTP**
* **SAMBA**
* ect. 

All work over LAN, getting them to work over WAN might needs some extra steps.

1. You first need to decide if you want to Point-and-Click (GUI) or if you are able to use a text only environment.

2. Secondly you need to decided what you want want to do with your "server", as not all the above mentioned software is capable to perform all the possible tasks efficiently

All these options and software have been covered extensively in previous posts.

I think you should start with Ubuntu's built in "Remote Desktop Viewer"

---

### Post by Ravenshade on 2011-01-02
Hi there FM, 

I would like GUI...I'm a little more comfortable with them, not that I'm not comfortable with Command Line, I just don't know all the destinations and syntax to be able to use it as deftly. 

Oh I know full well what I want to do with my server. Web hosting...as tricky as that's going to be but I'm sure I can manage it. 

I'd prefer software that's user friendly, or rather easy to use...neither are being particularly friendly with me. 

As both of my systems are connected to the same router I would have assumed they were on the same network... yet neither are appearing on the other's Remote Desktop. Therefore, I tracked down the IP addresses of the computer. Of course, being from the same network, they give out the same IP address, so I headed off to the terminal and cmdconsole respectively to get my local ip addresses and entered them.  

So far, I can't get Ubuntu to connect to my Windows System....any one want to give a hint? 

by the way...I can get Remote Desktop Viewer to view the same computer that it's running on (what use that is I don't know) but I doesn't pick up the other computer. (Which is connected to the internet by the way; both are).

Results: 
This computer cannot connect to the remote computer - please blah blah blah :-Windows XP

---

### Post by pqwoerituytrueiwoq on 2011-01-02
you have to enable remote assistance on xp it is somewhere in the control panel (that thing is like a maze lol)

---

### Post by Ravenshade on 2011-01-02
Okay, I've had a little luck and I installed realVNC full on my xp comp and a viewer on my netbook. Works like a charm (considering I can't actually find the VNC in the Ubuntu repository...*sigh*). Sudo apt-get vncviewer and I can view and control my computer. 

Unfortunately, no other method has proven quite so...hell they didn't work.

---

### Post by perspectoff on 2011-01-02
See the Remote Access instructions at Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Remote_Access](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Remote_Access)

or Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#Remote_Access](http://kubuntuguide.org/Maverick#Remote_Access)

---

### Post by perspectoff on 2011-01-02
[Duplicate removed]

---

### Post by perspectoff on 2011-01-02
[Duplicate removed]

---

### Post by perspectoff on 2011-01-02
[Duplicate removed]

---

### Post by perspectoff on 2011-01-02
[Duplicate Removed]

---

### Post by perspectoff on 2011-01-02
[Duplicate removed]

---

### Post by pqwoerituytrueiwoq on 2011-01-02
system->preferences->remote desktop to make it work on ubuntu

---

### Post by Ravenshade on 2011-01-02
> **pqwoerituytrueiwoq said:**
> you have to enable remote assistance on xp it is somewhere in the control panel (that thing is like a maze lol)

Already did that. Maybe I'm doing something wrong though since I've never been able to get the remote connection to work, except through VNC (yesterday)

---

### Post by pqwoerituytrueiwoq on 2011-01-03
must be a firewall stopping it

---

