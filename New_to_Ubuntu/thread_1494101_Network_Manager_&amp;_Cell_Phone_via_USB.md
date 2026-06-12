---
title: "Network Manager &amp; Cell Phone via USB"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-26
Received an email regarding using the phone mode in my Sony Ericsson W760i by having it recognized by Network Manager when I USB connect the phone. It should be recognized as 3GSM device. This does not happen and all I get is the offer from F-Stop to download the photos.

Right clicked on the NM icon, at the top of the page, but did not see USB connection as one of the options.

Anybody know how to get this to work? Would it work better if I just got a USB Bluetooth connection device?

Thanks for any assist.

---

### Post by -humanaut- on 2010-05-26
Check Synaptic for a driver.

---

### Post by flyfishingphil on 2010-05-26
> **-humanaut- said:**
> Check Synaptic for a driver.
What "kind" of driver am I looking for? Related to? Is it for Network Manager, cell phone, usb?

---

### Post by -humanaut- on 2010-05-26
Id try searching for "3G" "3G Modem"

---

### Post by flyfishingphil on 2010-05-26
> **-humanaut- said:**
> Id try searching for "3G" "3G Modem"
I'll check that out. Thanks for the info. Wasn't sure what I needed to look for.

I emailed one of those I found, refering to the W760i, in a different thread to see if he had any ideas. He just answered back with this tip. Makes for a quick connection when I want to use the W760i as a modem. Here's his tip:

 Did you try plugging
it in and selecting "Phone Mode"? It used to show a pop up, but I just
noticed that if you select Phone Mode and left click the network icon in
the upper right by the clock on the computer there will be an option
called "New Mobile Broadband (GSM) Connection..." If you click that you
can configure all the settings and connect.

Yahoo!! Now I'll check out your GSM modem tip and post what I find there.

Thanks again.

---

### Post by flyfishingphil on 2010-05-26
One more step forward. Found 3G Modem, clicked to install but don't see it listed anywhere under Applications. Plugged in phone but saw no response, at least under phone mode.

Did notice, following the tip above and clicking on the NM icon tht it shows a "Wired Network (Sony Ericsson Sony Ericsson W760) Disconnected. This is all grayed out. Any idea on how to get that from "disconnected" to "connected" when using the USB plug in?

EDIT ADD:

Tried this: 

Right click on NM icon > edit connections (shows choices Wired, Wireless, Mobile Broadband, VPN & DSL) under Wired it shows Auto Eth0 & Auto USB0 > click Edit > shows MAC address Click on ADD and it opens new box with title slot and asks for MAC address.

1. Would adding in usb1, with title and MAC address, give me a direct connection to the cell so I can "mount" it?

2. If so, where do I get the MAC address to put in there?

---

### Post by -humanaut- on 2010-05-27
From a terminal type: cat /etc/network/interfaces

and post back please.

---

### Post by flyfishingphil on 2010-05-27
> **-humanaut- said:**
> From a terminal type: cat /etc/network/interfaces

and post back please.
Here's what comes up:

[I]flyfishingphil@ffpC-Rods:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback[/I]

---

### Post by -humanaut- on 2010-05-27
Ok, its not picking up the new interface (oh yeah what driver did you end up downloading) Ok with the phone plugged into the Computer type: ls /dev

and post back. Sorry about this being such a pain Can you give me your full phone info Make Model Brand & Your Service (AT&T,Verizon,etc...) I'm gonna look into it a bit further because I think we might be going in a circles a little bit. Sorry, but well figure it out.

---

### Post by flyfishingphil on 2010-05-27
> **-humanaut- said:**
> Ok, its not picking up the new interface (oh yeah what driver did you end up downloading) Ok with the phone plugged into the Computer type: ls /dev

and post back. Sorry about this being such a pain Can you give me your full phone info Make Model Brand & Your Service (AT&T,Verizon,etc...) I'm gonna look into it a bit further because I think we might be going in a circles a little bit. Sorry, but well figure it out.
Phone is Sony Ericsson W760i using AT&T (Don't have data plan yet. Haven't gotten the phone connected so no sense in paying for something I can't use.)

RE: 3G Modem. Installed that but don't see it listed under applications. Typed 3G Modem in search and what it shows in Synaptics as installed are:

Package               Installed version
modemmanager   0.0.git.20091014t233208.16f3e00-0ubuntu1 D_Bus service for mamaging modems

xfce4-cellmodem-plugin  0.0.5dsfg-1ubuntu1  cellular modem plugin for Xfce panel

libdevice-modem-perl  1.47.2.1   Perl class to interface generic modems (AT-compliant)

Libdevice-serialport-perl   1.04.2   emulation of Win32::SerialPort for Linux/POSIX

ppp   2.4.5~git20081126t1000229-0ubuntu2  Point-to-Point protocol - daemon

ppp config 2.3.18ubuntu2   A text menu based utility for configuring ppp

ntfs-3g   1:20094.4-1ubuntu4 read-write driver for FUSE

libntfs-3g54   1:2009.4.4-1ubuntu4   ntfs-3g filesystem in userspace (FUSE) library

dhcp3-client   3.1.2-1ubuntu7.1   DHCP client


Here is what I get from the ls /dev in terminal:
(on my screen it was a several different colors)

flyfishingphil@ffpC-Rods:~$ ls /dev

agpgart          loop6               random      tty16  tty46    usbmon1
audio            loop7               rfkill      tty17  tty47    usbmon2
binder           mapper              rtc         tty18  tty48    usbmon3
block            mcelog              rtc0        tty19  tty49    usbmon4
bus              mem                 scd0        tty2   tty5     usbmon5
cdc-wdm0         mixer               sda         tty20  tty50    usbmon6
cdrom            net                 sda1        tty21  tty51    usbmon7
cdrw             network_latency     sda2        tty22  tty52    usbmon8
char             network_throughput  sda5        tty23  tty53    v4l
console          null                sdb         tty24  tty54    vcs
core             oldmem              sequencer   tty25  tty55    vcs1
cpu_dma_latency  pktcdvd             sequencer2  tty26  tty56    vcs2
disk             port                serial      tty27  tty57    vcs3
dri              ppp                 sg0         tty28  tty58    vcs4
dsp              psaux               sg1         tty29  tty59    vcs5
dvd              ptmx                sg2         tty3   tty6     vcs6
dvdrw            pts                 shm         tty30  tty60    vcs7
ecryptfs         ram0                snapshot    tty31  tty61    vcs8
fb0              ram1                snd         tty32  tty62    vcsa
fd               ram10               sndstat     tty33  tty63    vcsa1
full             ram11               sr0         tty34  tty7     vcsa2
fuse             ram12               stderr      tty35  tty8     vcsa3
hidraw0          ram13               stdin       tty36  tty9     vcsa4
hpet             ram14               stdout      tty37  ttyACM0  vcsa5
input            ram15               tty         tty38  ttyACM1  vcsa6
kmsg             ram2                tty0        tty39  ttyS0    vcsa7
log              ram3                tty1        tty4   ttyS1    vcsa8
loop0            ram4                tty10       tty40  ttyS2    video0
loop1            ram5                tty11       tty41  ttyS3    zero
loop2            ram6                tty12       tty42  urandom
loop3            ram7                tty13       tty43  usb
loop4            ram8                tty14       tty44  usblp0

Hope you can read all of this because, to me, it makes about as much sense as listening to a candidates speech on the campaign trail.

---

### Post by -humanaut- on 2010-05-27
Turns out we have been running in circles here's the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789?comments=all) Try downloading the fixes offered there.

---

### Post by flyfishingphil on 2010-05-27
> **-humanaut- said:**
> Turns out we have been running in circles here's the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264789?comments=all) Try downloading the fixes offered there.
Looked thru the reports. Most were dated in 2008/9 and saw nothing favorable listed in those that had tried them. At end said it had been repaired in later issues and it was closing date for that bug problem thread. According to the info there the version I have, 2.6.31-21 is supposed to have been corrected and no repairs for this were listed. (Users of 2.61.31-20 said the problem no longer existed.)

Also noted that these were all relating to external hard drives. I can connect my Seagate Maxtor and everything is fine. My problem is communicating between the cell phone and Network Manager.

I'm not a well versed computer program operator but aren't these 2 different areas in regards to what I am trying to do? I'm not looking for an external "backup/restore" storage space. I'm looking to connect the cell phone as a modem so I can get on the 'net when no other way is avaiable.

---

### Post by -humanaut- on 2010-05-28
The only thing I can think of at this point since we've tried about everything is Ubuntu simply isn't seeing the 3G Modem because it's service isn't turned on that's really the last thing I can think of.

---

### Post by flyfishingphil on 2010-05-28
> **-humanaut- said:**
> The only thing I can think of at this point since we've tried about everything is Ubuntu simply isn't seeing the 3G Modem because it's service isn't turned on that's really the last thing I can think of.
Kind of what I was wondering. Sounds like one of the "Catch 22" problems. You can't have it unless you ask for it and, if you ask for it, it's obvious you don't need it!

Well, it worked when I was using XP so I guess I'll have to wait until that cd comes in and set it up thru VBox.

Thanks for the attempts to find a way to get there from here humanaut. If I do happen to stumble across something I'll send you the info.

Call it Solved.

---

### Post by -humanaut- on 2010-05-28
> **flyfishingphil said:**
> Kind of what I was wondering. Sounds like one of the "Catch 22" problems. You can't have it unless you ask for it and, if you ask for it, it's obvious you don't need it!

Well, it worked when I was using XP so I guess I'll have to wait until that cd comes in and set it up thru VBox.

Thanks for the attempts to find a way to get there from here humanaut. If I do happen to stumble across something I'll send you the info.

Call it Solved.

First no problem glad I could help even though it didn't work 
I'll keep an eye to if I find a solution ill send you a P.M. atleast in Maverick I heard the Kernel has way better support for 3G Modems.

---

