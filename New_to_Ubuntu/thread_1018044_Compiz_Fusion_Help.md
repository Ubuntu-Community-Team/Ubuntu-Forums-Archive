---
title: "Compiz Fusion Help"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by pappasaa on 2008-12-21
trying to setup compiz but I am having some problems

first
when I try to setup my visual effects to the "Extra" setting it says " desktop effects could not be enabled" 

second
in the terminal when i type in " compiz it says 

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

I know i need to install Xgl but i do not know how

---

### Post by neu2buntu on 2008-12-21
you dont enable compiz like this,by typing compiz in terminal...i think it runs inthe background....

you need to go to synaptic search ```
ccsm
``` and install this.... this is the compiz manager and it installs to >system>preferences......  if you need any help using it i should be able to help

---

### Post by pappasaa on 2008-12-21
> **chrissy.mc.1@hotmail.co.u said:**
> you dont enable compiz like this,by typing compiz in terminal...i think it runs inthe background....

you need to go to synaptic search ```
ccsm
``` and install this.... this is the compiz manager and it installs to >system>preferences......  if you need any help using it i should be able to help


i typed in ccsm and the "compizConfig setting manager" opened.

i can select the effects but I still cant use them..

---

### Post by neu2buntu on 2008-12-21
the effects work with a combination of hotkeys .... for example tick the paint fire on flame ...hotkeys are shift>home(as in beside alt)>leftmouse button > and drag your mouse.....

oh and to clear flames do same combination except for drag mouse, change this to c

---

### Post by LtPitt on 2008-12-21
Maybe the problem is about opengl acceleration...
Is your video card working fine?

Try some opengl screensavers to find it out...
If you have troubles on installing the drivers install a program called Envy: it's really easy and it works great :)

---

### Post by jimmy the saint on 2008-12-21
what is your graphics card?  Did you install the approptiate drivers?  If you do not have a card/driver that that can handle 3d graphics, it could cause this very problem.  Let me know what card you have and we can try to get it working.

---

### Post by Piraja on 2008-12-21
Are you running Ubuntu 8.10 (Intrepid Ibex)? Is your machine equipped with an Intel graphics card of the type i845GM or i945GM? If so, then Compiz does not work at the moment with your setup. This is a bug reported in Launchpad and the developers are working on it both downstream and upstream.

Actually "No whitelisted drivers found" indicates precisely that the intel driver is blacklisted, because enabling Compiz would cause X to freeze.

---

### Post by pappasaa on 2008-12-21
> **chrissy.mc.1@hotmail.co.u said:**
> the effects work with a combination of hotkeys .... for example tick the paint fire on flame ...hotkeys are shift>home(as in beside alt)>leftmouse button > and drag your mouse.....

oh and to clear flames do same combination except for drag mouse, change this to c


i get how to run the effects...not sure how to find out if my system can run it. 

what kind of viedo card is required. or do I need a special driver for my current video card. and how can i see what my current video card is

---

### Post by IamReck on 2008-12-21
Go in terminal, and type "lspci" copy and paste the results here.

---

### Post by pappasaa on 2008-12-21
> **IamReck said:**
> Go in terminal, and type "lspci" copy and paste the results here.


```

00:00.0 Host bridge: VIA Technologies, Inc. VT8371 [KX133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8371 [KX133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:08.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)



```

---

### Post by neu2buntu on 2008-12-21
```
lspci
```    im not really up on what can run it...but some of these guys on here will know

---

### Post by jimmy the saint on 2008-12-21
it appears that you have an Nvidia card

go to system>administration>hardware drivers.  If you see a driver there, choose to use it.  If there are two and one is the 177 driver, install the other one.  Otherwise just install the recommended one.  That will give you the more advanced nvidia driver that can do 3d effects a little better.

---

### Post by pappasaa on 2008-12-21
> **jimmy the saint said:**
> it appears that you have an Nvidia card

go to system>administration>hardware drivers.  If you see a driver there, choose to use it.  If there are two and one is the 177 driver, install the other one.  Otherwise just install the recommended one.  That will give you the more advanced nvidia driver that can do 3d effects a little better.


Went to hardware drivers and at the top it says

no proprietary are in use on this system

---

### Post by IamReck on 2008-12-21
If it doesn't work then, open up a terminal and type "compiz"

Post the output here.

---

### Post by pappasaa on 2008-12-21
> **IamReck said:**
> If it doesn't work then, open up a terminal and type "compiz"

Post the output here.


in the terminal when i type in " compiz it says 

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by jimmy the saint on 2008-12-21
hmm okay.  So it appears that you have an Nvidia NV6, which is not capable of supporting glx (3d acceleration) in Ubuntu 8.10.  The package that holds the appropriate drivers (nvidia-glx-legacy) is not compatible withe the version of Xorg that comes with 8.10.  Unfortunately, it appears that you may not be able to run the advanced compiz features with your current setup as the legacy video card will not support the needed features.

Rererence:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)  (toward bottom)

---

### Post by IamReck on 2008-12-21
Looks like your Graphics card is not supported by Compiz, or the driver it is using is not.  Lets make sure you have access to that proprietary one.

One last thing, to make sure you have the repository for restricted drivers present.

Go to System -> Administration -> Software Sources

Make sure you have "Proprietary drivers for devices (restricted)" checked off.

Then do a reboot, and check the Hardware Drivers again.

If 177 is there, use that one, reboot your computer, and try enabling compiz.

---

### Post by pappasaa on 2008-12-21
> **jimmy the saint said:**
> hmm okay.  So it appears that you have an Nvidia NV6, which is not capable of supporting glx (3d acceleration) in Ubuntu 8.10.  The package that holds the appropriate drivers (nvidia-glx-legacy) is not compatible withe the version of Xorg that comes with 8.10.  Unfortunately, it appears that you may not be able to run the advanced compiz features with your current setup as the legacy video card will not support the needed features.

Rererence:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)  (toward bottom)

i fugured as much...this thing is older then dirt. I guess I will just wait till i get a better computer to use all the cool stuff...thanks for your help

---

