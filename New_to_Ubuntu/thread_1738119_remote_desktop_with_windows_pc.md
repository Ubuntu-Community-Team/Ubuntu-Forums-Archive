---
title: "remote desktop with windows pc"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Ross-Gardner on 2011-04-24
I am a new user of ubuntu. I am running ubuntu  on my laptop  and want to setup remote desktop access to my windows PC's some thing like the PC anywhere  concept. I do not have a clue where to start. 

step by step help would be great if possible thank you all!:confused:

---

### Post by elzy89 on 2011-04-24
Top left, Applications, Internet, Terminal Server Client.

Let us know how you get on?

---

### Post by Ross-Gardner on 2011-04-24
> **elzy89 said:**
> Top left, Applications, Internet, Terminal Server Client.

Let us know how you get on?

what do you mean?

---

### Post by Paddy Landau on 2011-04-24
Use [LogMeIn]("http://logmein.com/").

It will allow access via a browser from any computer (including Linux) to a Mac or Windows computer.

It has a free version and a paid-for version. I have used it for a long time to access my father's Windows computer a few thousand miles away, and have never had a problem with XP, Vista or 7.

---

### Post by Ross-Gardner on 2011-04-24
more to the point 
what do I need to do on each pc?
laptop - ubuntu  accessing 
desktops
pc 1 with windows 7 64bit
pc 2 with XP pro 32bit

I want to have full access/ control of my windows PC's from my laptop
what software do I need on each PC to  do this ?
and what do I need to know about to configure each ?

---

### Post by Ross-Gardner on 2011-04-24
[QUOTE=Paddy Landau;10714005]Use [LogMeIn]("http://logmein.com/").

It will allow access via a browser from any computer (including Linux) to a Mac or Windows computer.

It has a free version and a paid-for version. I have used it for a long time to access my father's Windows computer a few thousand miles away, and have never had a problem with XP, Vista or 7.[/QUOTE

thank you I will look into this

---

### Post by elzy89 on 2011-04-24
If they are all on the same network then LMI will be a waste of time and system resources. Use RDP as your protocol for remote access to anything MS based. You will also get your native resolution in full screen, or one of your choosing.

---

### Post by itisbasi on 2011-04-24
Check out TEAMVIEWER, it's free for home use and is available for all platforms windows, linux and mac

---

### Post by HermanAB on 2011-04-24
Choices, choices...

Everybody is talking about a different method.  The nice thing is that they will all work, only some will only work under certain circumstances.

The Microsoft Remote Desktop Protocol (RDP) was purchased from Citrix, who based their work on VNC.  So, it is possible to enable RDP in your Windows machine, then connect to it from Linux using a remote client such as rdesktop.

However, if your Windows machine is behind a NAT router, then you either need to forward port 3389 and make it available to the outside, or you need to use a VNC mirror service such as Teamviewer or GotoMyPC.

Hope that helps!

---

### Post by elzy89 on 2011-04-24
I suppose another important question to ask would be, what edition of Windows 7 is the desktop that you want to RDP to actually running?

---

### Post by Ross-Gardner on 2011-04-24
thanks all I got logmein running it will do for what I need  and seams to be the simplest answer

---

### Post by digitaladvertise.me on 2011-11-17
i have the same basic question.  i use logmein on my windows pc.  im running windows 7 on my main machine.  if i have a remote machine running ubuntu, the only version of logmein i can find on thier website is [https://secure.logmein.com/labs/](https://secure.logmein.com/labs/) but says currently its command line interface only?   im looking for something with more of a GUI, not command line....

---

### Post by Paddy Landau on 2011-11-17
LogMeIn is suitable for accessing Windows and Mac from any other machine (including Linux).

However, it is not suitable for accessing Linux from another machine.

If you want to access Ubuntu remotely, you have few choices.

You can install [xrdp]("apt:xrdp"), which allows Windows to access Ubuntu using Remote Assistance. I have not tried this, but it is free.

Have a look at [Yuuguu]("http://www.yuuguu.com/"), which works on Windows, Mac and Linux. I have tried it and it is quite good (though not as easy as LogMeIn). However, apart from an initial free trial, it does cost.

Also look at [NoMachine]("http://www.nomachine.com/"). This is also cross-platform; its Linux version is free but the others cost.

[Virtual Network Computing (VNC)]("http://en.wikipedia.org/wiki/Virtual_Network_Computing") is free and cross-platform, but you have to be very careful about security. [RealVNC]("http://www.realvnc.com/") is a derivative that supplies encryption, but is not free. [UltraVNC]("http://www.uvnc.com/") provides encryption though an optional plugin; if you use it, be sure to install the plugins and follow the instructions carefully.

If you were to view Ubuntu from another Ubuntu machine, you would have a couple of extra options, including [xnest]("apt:xnest") and [Xephyr X]("http://en.wikipedia.org/wiki/Xephyr") where you can log in as a separate user (Linux allows more than one person to log in at the same time).

Good luck.

---

