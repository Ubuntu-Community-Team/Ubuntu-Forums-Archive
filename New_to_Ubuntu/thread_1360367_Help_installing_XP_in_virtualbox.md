---
title: "Help installing XP in virtualbox?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by ChubbySauce on 2009-12-20
before I go into this let me say

Ive tried this before hand myself and made a ten gig portion and deleted it through VB and it didnt restore any hard drive space, I selected keep :I

anywho I have a legit CD with windows xp w/ recent 2009 updates.

I was trying to install, the bios showed up and it said my processor isn't compatible.

Now this is a 2009 version I'm feeling like theres some setting on VB thats preventing this install disk from recognizing my AMD turion 64 bit processor as a compatible one.



:3 soo this is my first time with virtual box so Im very newbish behind the ears if someone could aim me at seuxnoose to walk me through it would be greatly appreciated.

thanks for all replies



btw is says its says my computer isnt compatable with the 64bit disk it says use a 32bit.

but my system is 64????

---

### Post by EnGorDiaz on 2009-12-20
> **ChubbySauce said:**
> before I go into this let me say

Ive tried this before hand myself and made a ten gig portion and deleted it through VB and it didnt restore any hard drive space, I selected keep :I

anywho I have a legit CD with windows xp w/ recent 2009 updates.

I was trying to install, the bios showed up and it said my processor isn't compatible.

Now this is a 2009 version I'm feeling like theres some setting on VB thats preventing this install disk from recognizing my AMD turion 64 bit processor as a compatible one.



:3 soo this is my first time with virtual box so Im very newbish behind the ears if someone could aim me at seuxnoose to walk me through it would be greatly appreciated.

;o thanks for all replies



have you got virtualisation turned on in bios

---

### Post by ChubbySauce on 2009-12-20
I deleted the first one I tried its still in the hard disk folder of virtual box do you know how to restore that part to free space?

---

### Post by ChubbySauce on 2009-12-20
oop nvm I got it lemme try that first thing tho

---

### Post by ChubbySauce on 2009-12-20
where do I go to turn on virtualisation I dont see it anywhere?

---

### Post by Merk42 on 2009-12-21
Just because your processor is 64bit and even your host OS (Ubuntu) is 64bit doesn't mean your guest OS (Windows XP) can be 64bit. What specifically is your processor?

You have XP x64, really?

It's pretty straight forward, have you read [the manual](http://download.virtualbox.org/virtualbox/3.1.2/UserManual.pdf)? It spells out these steps in greater detail. 
You should just load up Virtualbox (I'm curious what version you're using)
[list=1][*]Click New
[*]Tell it Windows XP (x64?)
[*]Give it some amount of RAM
[*]Create new Hard Disk
[*]Dynamically Expanding Storage
[*]Once done, go to settings and point Storage to the Windows XP CD you have in your drive[/list]

Anyway when you originally made that 10GB partition, was that through Virtualbox? You do not make a new partition in something like Gparted.  Virtualbox uses files call .vdi which contain the host OS.

---

### Post by steveneddy on 2009-12-21
Not all BIOS are able to enable KVM support even though the host processor is actually a 64 bit processor.

You will have to run the 32 bit version of XP in this case.

---

### Post by ChubbySauce on 2009-12-21
xp sorry merk I didnt realize I had to have it under 64 but yes its on that now I gave it a try and I got this [IMG]http://i237.photobucket.com/albums/ff253/Charliefox98/problem.png[/IMG]

---

### Post by ChubbySauce on 2009-12-21
the VT/-x is enabled I think its just not possible :( 

can you have xp under an amd 64 tuiron processor

---

### Post by t0p on 2009-12-21
if vt/x is enabled in bios and you still get that message, it means you can't run 64-bit xp in virtualbox on your machine.  You'll have to use 32-bit xp.

**EDIT** Are you using the latest version of virtualbox from virtualbox.org?  If not, I'd advise trying it out.  They update VB quite regularly - especially the non-free version.

---

