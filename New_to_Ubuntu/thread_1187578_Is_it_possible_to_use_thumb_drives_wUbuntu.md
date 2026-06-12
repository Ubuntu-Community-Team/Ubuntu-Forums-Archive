---
title: "Is it possible to use thumb drives w/Ubuntu?"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by kileiona on 2009-06-14
New to Ubuntu here!  So far the only hiccup I have encounted is that I cannot use my thumb drive?  Hints?  TY

---

### Post by reboskyz24 on 2009-06-14
What version are you using?  What are you running it on?  Have you connected to the internet and downloaded updates?

---

### Post by Bradtek on 2009-06-14
It should automatically recognise and mount a USB thumb drive

with the thumb drive plugged in, open a terminal 
Applications | Accessories | Terminal 
and type
```
lsusb
```

Then paste what it says here


And of courese more info, like what version of ubuntu, what computer is it, Desktop, laptop etc etc

---

### Post by kileiona on 2009-06-14
I am running on a desktop computer, ubuntu v 9.04, pentium 4 processor

when I did what you told me in the terminal this is what it said

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by kileiona on 2009-06-14
> **reboskyz24 said:**
> What version are you using?  What are you running it on?  Have you connected to the internet and downloaded updates?
Yes, I have installed updates via the web.

---

### Post by Sef on 2009-06-14
1) Do other devices work in your usb ports?

2) Does your thumb drive work in other computers?

3) What version of Ubuntu are you using?

4) Any other problems?

---

### Post by Cowchip7 on 2009-06-14
I haven't met a thumb drive my computer didn't like... as of yet. Do you have another one lying around? Give that a try.

---

### Post by Bradtek on 2009-06-14
> **kileiona said:**
> 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Definately no thumb drive there, does it have a LED on it/ does it come on ?

And as suggested, try another one

---

### Post by kileiona on 2009-06-14
Now that you mention it, my usb mouse wouldn't work in this computer either, I know it's not the port though because I did have windows on this computer (before windows decided to die...) and had no problems using usb objects with it.  The 2 thumb drives I have tried using on this computer work in my other computers without problems (the other computers are windows).  The only other problem that I have encountered is that I can't get DVD movies to play, but that's not major.

edit: is it possible that whatever it was that corrupted my windows on this computer somehow damaged my USB ports?

---

### Post by DGortze380 on 2009-06-14
try another port.
try the drive on another computer.
try another drive on your computer.
try a different usb device on your computer.

I've occasionally had issues with newer thumb drives (2.0) not auto-mounting on a 1.1 Hub.

---

### Post by Bradtek on 2009-06-14
Boot up the live CD and check if it is recognised 

Try downloading another distro, Puppy Linux is a < 100 MB download
and runs from the CD.

---

### Post by theozzlives on 2009-06-14
Is your 2.0 a card? The only thing I can think of is a bad port or bad drive. I have 9.04 with 9.10 Alpha 2 in a VirtualBox and my flash drives work.

EDIT: corse I wouldn't rule out a bad install.

---

### Post by kileiona on 2009-06-14
> **Sef said:**
> 1) Do other devices work in your usb ports?

2) Does your thumb drive work in other computers?

3) What version of Ubuntu are you using?

4) Any other problems?

> **theozzlives said:**
> Is your 2.0 a card? The only thing I can think of is a bad port or bad drive. I have 9.04 with 9.10 Alpha 2 in a VirtualBox and my flash drives work.

EDIT: corse I wouldn't rule out a bad install.

is there a way to check whether or not i have a bad install?

---

