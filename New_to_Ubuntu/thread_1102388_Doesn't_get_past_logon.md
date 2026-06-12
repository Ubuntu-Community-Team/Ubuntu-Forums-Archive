---
title: "Doesn't get past logon"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Robt6 on 2009-03-21
I used wubi-installer to install W/Xp. Install completes (15gb) and reboots, selecting Ubuntu, get logon screen, then a little HD activity, then screen goes blank off white, or black, and HD activity stops.
Once, when I walked away for 20 minutes, Xp was running.
Have uninstalled, and reinstalled at 30gb. same thing.
I have not waited more than ten minutes except for the one 20 minute episode. I have also tried the recovery mode, No resolution there.
Help Really appreciated, Thanks.
 
Including hardware profile just in case it may be hardware problem.
System Model
Compaq Presario 06 DA238A-ABA 6450NX NA910 0n81411RE101XENO3
System Serial Number: MX30919395
Enclosure Type: Desktop

Processor
2.53 gigahertz Intel Pentium 4
8 kilobyte primary memory cache
512 kilobyte secondary memory cache

Main Circuit Board
Board: MICRO-STAR INTERNATIONAL CO., LTD MS-6577 020
Bus Clock: 133 megahertz
BIOS: Phoenix Technologies, LTD 3.14 02/14/2003

Drives
120.02 Gigabytes Usable Hard Drive Capacity
85.34 Gigabytes Hard Drive Free Space

CyberDrv CW088D CD-R/RW [CD-ROM drive]
HL-DT-ST DVD-ROM GDR8161B [CD-ROM drive]
3.5" format removeable media [Floppy drive]

WDC WD1200AB-22CBA1 [Hard drive] (120.03 GB) -- drive 0, s/n WD-WMAA31426647, rev 04.07B04, SMART Status: Healthy 

Memory Modules
1528 Megabytes Installed Memory

Slot 'A0' has 512 MB
Slot 'A1' has 1024 MB

DISPLAY
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller [Display adapter]
COMPAQ 5017 [Monitor] (14.6"vis, s/n CNNGI0B670, February 2003)

---

### Post by yeats on 2009-03-21
Have you been able to run the Live CD with success?

---

### Post by blandman3 on 2009-03-21
i get the same thing, just an orange screen past the login.

---

### Post by Robt6 on 2009-03-21
I haven't tried the liveCD. will download and try that.
Will post here with results. Whoops, I got the iso, will burn and try.

Running it from CD gets to orange screen, drum music, then a blank screen,
CD activity stops and Hd activity stops, except for a very small flicker every 15 secs or so.

---

### Post by Robt6 on 2009-03-21
Running liveCD requires running in safe graphics mode.
I'm on Ubuntu now, :) will see if wubi-install has option to 
install in same mode.

---

### Post by blandman3 on 2009-03-22
if you can't run the LIVE CD successfully, I have found when I press F6 twice, and check off:

acpi=off noapic nolapic

hit esc, and type this into the command line:

hw-detect/start_pcmcia=false netcfg/disable_dhcp=true xforcevesa

then hit enter

(you may not need the xforcevesa, but it worked for me just to run the LIVE CD)

---

### Post by Robt6 on 2009-03-22
LiveCD runs fine if while booting, I hit F4 and select "Safe Graphics Mode" Is there a way of forcing the same with the Wubi installed?

---

### Post by blandman3 on 2009-03-22
do you have it installed already?

if so, someone just told me how to get in past the login screen.

before you sign in and put in your password:

hit ctrl alt F1

you will come to a command prompt that asks for your username and password, you will have to type those in.

then type:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

just give it a few minutes, and then type exit

you should be able to get back to the ubuntu login screen, then just try logging on again, and it should load!  It worked for me, anyway.

---

### Post by Robt6 on 2009-03-22
THANKS! That got it going.:p Now, being the curious type, what did that do?
Now for some hands on  to get used to this. Win user since W98 (skipping Me and  2000) and hopefully never Vista:(, nor anything that comes later.

---

### Post by blandman3 on 2009-03-22
From what i get, it is in conflict with some other hardware, or software.  I don't know really, I just got this thing last week.  These forums have been really nice, with a lot of support!

I am glad that it worked for you, I like it a lot.

---

### Post by Robt6 on 2009-03-22
I think I'm going to like it also.
We can consider this thread closed.):P
Thanks again!

---

### Post by anewguy on 2009-03-22
Compiz is the window "decoration" - it does such things as allowing you to have the desktop cube, see-through screen, and untold number of other things - i.e., it's eyecandy.

Some have found incompatibilities between compiz and the 845 integrated graphics processor you have.  Removing compiz (and it's "core") usually fixes it - you just can't have the fancy eyecandy.

I would suspect it's something either in the driver for the 845, or that the 845 itself is just one of many IGP's (Unichrome S3 is another I'm familiar with having problems with) that just don't support everything that compiz needs to run successfully.

Dave :)

---

### Post by Robt6 on 2009-03-22
Then that's all right then, eyecandy isn't necessary here, just a stable workhorse to say. Now to get the mic working for skype, but that will be later, and in another thread. Thanks to all!

---

