---
title: "Is there a better way (view Windows desktop on Ubuntu)?"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-11-23
I have 2 apps that I use regularly that only run on Windows.  So, I have an old laptop that runs those apps, and I am using Remote Desktop Viewer on my Ubuntu box to view/run them.  Works great, I get to run those apps without messing with my Linux environment. (I don't want to try Wine; these are ham radio control apps that don't run well in Wine).

However, it seems like it's wasteful to connect the two machines the way I am doing it... the Windows box connects wirelessly to my router, and my Ubuntu box is hardwired to the router.  So every keyboard/mouse/screen change goes over the air to the router then back up to the Ubuntu box, even though the two machines are 3 feet from each other.  (no I don't want the Windows box to sit on the desk, only have room for 1 laptop).

Is there a way to simply do this connection via a USB cable or somehow direct, so as to avoid going through (and burdening) the router?

Using Ubuntu 10.04LTS.

---

### Post by JustinR on 2010-11-23
You can use a virtualization software like VirtualBox to do that.

---

### Post by Bucky Ball on 2010-11-23
Tried any Linux ham-radio apps? There are quite a number. Nothing suitable? Save some time and electricity.

---

### Post by Newbie2910 on 2010-11-23
None of the available ham radio s/w for Linux approaches Ham Radio Deluxe.  That's not a poke, it's just a fact.

Does Virtualbox support serial port I/O?  Meaning can it read/write serial I/O thru a serial port on the Ubuntu box?

---

### Post by gary0 on 2010-11-23
I agree. I dual boot with win xp just to run HRD, LiveMUF, and LogRES, my log book written in .NET and sitting on MySQL. I did try hrd in a virtual box, but was very sluggish, and my logbook became pretty much unusable despite having a gig of ram assigned to the VB. Best bet is to dual boot.

Gary G7RES

---

### Post by Newbie2910 on 2010-11-23
My only concern with HRD is that it uses Access for the logbook database.  As a software coder for many decades, I know that Access is simply not robust enough for something as critical as a ham log.

What is the logbook you are using that stores data in MySql?  As you no doubt recognize, a real SQL server-quality database is necessary for any mission-critical app.

---

### Post by gary0 on 2010-11-24
I wrote it myself, originally in VB6, and then rewrote in .NET
It can use both Access and MySQL, I use MySQL.

Gary.

---

### Post by QLee on 2010-11-24
[QUOTE=Newbie2910]...
However, it seems like it's wasteful to connect the two machines the way I am doing it... the Windows box connects wirelessly to my router, and my Ubuntu box is hardwired to the router.  So every keyboard/mouse/screen change goes over the air to the router then back up to the Ubuntu box, even though the two machines are 3 feet from each other.  (no I don't want the Windows box to sit on the desk, only have room for 1 laptop).

Is there a way to simply do this connection via a USB cable or somehow direct, so as to avoid going through (and burdening) the router?
...[/QUOTE]

Wasteful in what way, use of a few electrons? Joking aside, this stuff runs as fast as the slowest part of the chain is capable of and you're probably using at least "g" wifi and a fast ethernet interface. If you're only talking about those two systems on your network and not an overburdened multi-seat LAN environment, then it's going to be much faster than you can type anyway. Since you'd still have both systems connected to and talking to the gateway/router for Internet connectivity, to do what you suggest would add, in my opinion, complexity to a system that is already serving you. Yes, we could likely help you use one of those USB, network-crossover "thingys" but except for possibility of learning, I doubt that you would find it satisfying or continue to use it and it would tie up USB ports and use current. Could also add network interfaces to each system and set up for what you want but that would be even more cost and I for one wouldn't want to try and talk you through that here in the ABT forum.

---

### Post by Newbie2910 on 2010-11-24
VNC is usually pretty quick, but in this case from one end to the other it's not quick enough so that I can tune the radio to different frequencies using the program.

Monitoring is fine, and the VU meter lags a little but it is usable.

---

### Post by pricetech on 2010-11-24
Use Terminal Server Client instead of VNC.  It's a lot quicker.  That should make the difference.

---

### Post by Newbie2910 on 2010-11-24
What do I run as the server app on the Windows XP box?

---

### Post by pricetech on 2010-11-25
I hope it's Pro.  In properties, Control Panel - System or right click My Computer and select properties, or Winkey + Pause / Break; Remote tab.  Click the box to allow remote connections.  Administrative users will automatically have remote access and won't have to be added.

If it's Home you won't have that option.  (Sorry, I forgot about that when I first mentioned it)

---

### Post by Newbie2910 on 2010-11-25
Well I got it working but it's no faster than using VNC.

---

### Post by QLee on 2010-11-25
The old laptop might be the bottleneck. Maybe wireless is the bottleneck. If you had gigabit NICs in both systems and a router capable of those speed, you might find some improvement by connecting hardwire from both computers to the router. Wired doesn't have to worry about radio freq. interference in the location. (ie other routers nearby using the same channel or higher power level cordless phones in the band, etc.) You're a ham, you'll get the picture.

---

### Post by pricetech on 2010-11-29
> **Newbie2910 said:**
> Well I got it working but it's no faster than using VNC.

Strange.  Works faster everywhere I've used it.  Can you connect both nodes wired ???

---

### Post by krishnarajagopal on 2010-11-29
> **Newbie2910 said:**
> I have 2 apps that I use regularly that only run on Windows. So, I have an old laptop that runs those apps, and I am using Remote Desktop Viewer on my Ubuntu box to view/run them. Works great, I get to run those apps without messing with my Linux environment. (I don't want to try Wine; these are ham radio control apps that don't run well in Wine).
 
However, it seems like it's wasteful to connect the two machines the way I am doing it... the Windows box connects wirelessly to my router, and my Ubuntu box is hardwired to the router. So every keyboard/mouse/screen change goes over the air to the router then back up to the Ubuntu box, even though the two machines are 3 feet from each other. (no I don't want the Windows box to sit on the desk, only have room for 1 laptop).
 
Is there a way to simply do this connection via a USB cable or somehow direct, so as to avoid going through (and burdening) the router?
 
Using Ubuntu 10.04LTS.
 
Hi Newbie,
Have you tried Oracle's Virtual box you can install windows as a guest machine inside the ubuntu and infact connect the extrenal drive to your laptop and point the .VDI file of the windows to be loaded in the external hardisk.

---

