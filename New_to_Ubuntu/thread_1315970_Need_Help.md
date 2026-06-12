---
title: "Need Help"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Pilot12 on 2009-11-05
I am new to this forum.  Please accept my regrets if I have posted incorrectly.
I am having difficulty.  

1.  After installing Ubuntu 9.1 my screen blanks randomly.  I installed 9.04 and it did the same.

2.  I cannot enable the proper drivers for a Linksys Wusb11 V2.8 wireless adapter.

Here are the specifics that may help provide me with a solution.

1.  Machine
Sony Vaio Pentium 4 3.0 GHz processor two (2) GB DDR Ram
Visionteck Xtasy ATI Radeon 9250 Display adapter
M$ Wireless Keyboard and Mouse
HP 2009M 20" Wide screen Monitor.  Resolution 1600 X 900 60 refresh
Linksys WUsb11 V2.8 wireless network adapter

I have sorted through many forums and Googled the question.  I must say that I only became more confused.  I purchased a new Belkin Wireless Network Adapter that worked out of the box.  I have no problem with continuing to use it.

The main problem is **screen blanking. ** Let me define:  The OS installs, all menue items work great, I connect to the internet using Firefox 3.5 and the screen goes black about every two minutes or so.  After about thirty (30) minutes I start seeing blurred colored lines running on the left side of the screen.  The monitor is new and works perfectly with Windows XP.

I really like Ubuntu and would like to change from M$.  If I could get the screen blanking problem worked out I would do this.

Thanks in advance for any assistance you folks may be able to provide.

Pilot12

---

### Post by BQAggie2006 on 2009-11-05
As far as the screen blanking, do you have desktop effects enabled?

---

### Post by Pilot12 on 2009-11-05
Thx
When the OS boots the top and bottom panels and all menue items are visable.  However, the "Desktop" is black.  I checked the "Appearence Menue" and desktop effets were enabled.  I selected "none" the standard theme appeared and the blanking problem starts.

Any ideas ???

Pilot12

---

### Post by BQAggie2006 on 2009-11-05
Not really, that was going to be my only suggestion, to disable desktop effect.

As far as the Linksys USB wifi adapter, have you tried using the ndiswrapper to install the Windows driver?

---

### Post by sandyd on 2009-11-05
> **Pilot12 said:**
> I am new to this forum.  Please accept my regrets if I have posted incorrectly.
I am having difficulty.  

1.  After installing Ubuntu 9.1 my screen blanks randomly.  I installed 9.04 and it did the same.

2.  I cannot enable the proper drivers for a Linksys Wusb11 V2.8 wireless adapter.

Here are the specifics that may help provide me with a solution.

1.  Machine
Sony Vaio Pentium 4 3.0 GHz processor two (2) GB DDR Ram
Visionteck Xtasy ATI Radeon 9250 Display adapter
M$ Wireless Keyboard and Mouse
HP 2009M 20" Wide screen Monitor.  Resolution 1600 X 900 60 refresh
Linksys WUsb11 V2.8 wireless network adapter

I have sorted through many forums and Googled the question.  I must say that I only became more confused.  I purchased a new Belkin Wireless Network Adapter that worked out of the box.  I have no problem with continuing to use it.

The main problem is **screen blanking. ** Let me define:  The OS installs, all menue items work great, I connect to the internet using Firefox 3.5 and the screen goes black about every two minutes or so.  After about thirty (30) minutes I start seeing blurred colored lines running on the left side of the screen.  The monitor is new and works perfectly with Windows XP.

I really like Ubuntu and would like to change from M$.  If I could get the screen blanking problem worked out I would do this.

Thanks in advance for any assistance you folks may be able to provide.

Pilot12
press ctrl+alt+f1
then login using your username and password.
type this in (in sequence, one after the other)    

```

sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t

```follow the onscreen instructions to isntall the ati driver
choose restart when it asks you if you want to or not.

---

### Post by Pilot12 on 2009-11-05
Thx

Yes.  I tried Ndiswrapper -- got frustrated because I couldn't install it from terminal and bought a new network adapter.  Worked great.  That part of the problem is solved. 

The problem is the srcreen blanking.  It seems to be related to the ATI Video Drivers.  I attemted to install the new Linux ATI drivers and they crashed my system.  

I really want to move away from M$.

Thanks again.......

---

### Post by Pilot12 on 2009-11-06
Carlee:

Thanks very much.  I followed your instructions and installed the ATI drivers.  The screen started flashing after the next boot; zero graphics.  This necessitated me re-installing the OS.  I have an HD cable from the monitor to the computer and (just an uneducated thought) was wondering if this could be the culprit causing the screen blanking ?
Any suggestions as to how I can proceed ?

Thanks in advance.

Pilot12

---

### Post by sandyd on 2009-11-08
> **Pilot12 said:**
> Carlee:

Thanks very much.  I followed your instructions and installed the ATI drivers.  The screen started flashing after the next boot; zero graphics.  This necessitated me re-installing the OS.  I have an HD cable from the monitor to the computer and (just an uneducated thought) was wondering if this could be the culprit causing the screen blanking ?
Any suggestions as to how I can proceed ?

Thanks in advance.

Pilot12
see if swapping it with a VGA cable works.

---

### Post by Bartender on 2009-11-08
The very first vid card I tried to run with Ubuntu four years ago was a 9250.  it was horrible.  I know ATI drivers have improved since then, but maybe not so much for older cards?

You may find the best solution is to pick up a cheap Nvidia card...

---

### Post by Pilot12 on 2009-11-12
**Thanks.......  SOLVED !!!!**

I bought an Nvidia Card, installed it, and BINGO --- problem solved.  The screen blanking problem disappeared and every aspect of Ubuntu Works Perfectly.  I am very pleased to move away from M$.  The OS is very smooth, easy to use, and provides me with a platform that I really like.  Incidentally, Desktop Effects now work with the new card whereas before they didn't.

Thanks again...........

Pilot12

---

