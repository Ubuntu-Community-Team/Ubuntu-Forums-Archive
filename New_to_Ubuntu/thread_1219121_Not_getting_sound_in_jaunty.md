---
title: "Not getting sound in jaunty"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by vnrbhargav on 2009-07-21
hi friends..
i am using a HP Dv5t laptop..
my configuration is 2GB RAM,250 GB HDD,and core2duo processor..
previously i was using ubuntu 8.04 and windows vista in parallel..
now using jaunty...
i am not able to get sound in my laptop..
the sound works in vista..but in linux i am not able to get even the startup sound also..

 i tried alsamixer also in terminal.
in it sound card is being detected..but not getting sound..
plz help me out..




thanks in advance friens

---

### Post by philcamlin on 2009-07-21
ok lets rule out the silly things first :)

is your speakers turned on 
are they muted 
right click on the music icon in the top right and click propertues and turn all to full volume through the tabs :popcorn:

---

### Post by vnrbhargav on 2009-07-21
speakers are turned on..

---

### Post by philcamlin on 2009-07-21
right click on the music icon in the top right and click propertues and turn all to full volume through the tabs ?

post output 

cat /proc/asound/cards

---

### Post by vnrbhargav on 2009-07-21
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


this is the message i got..

kept max sound also but sound not coming..

---

### Post by vnrbhargav on 2009-07-21
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x9c700000 irq 22




this is the output dude..

---

### Post by Armor Nick on 2009-07-21
have you checked the advanced sound controls? This can also be checked using alsamixer in a terminal. The Master and PCM channels have to be at a 100 percent.

---

### Post by vnrbhargav on 2009-07-22
they are 100%..
no problem at all..

---

### Post by vnrbhargav on 2009-07-22
but the problem is that i am not at all getting sound..
not even the startup sound also..

plz do help..

---

### Post by TheGoktor on 2009-07-31
I think I may be having the same problem as you. When I installed Intrepid, I had no sound (although it was fine with Vista). My local computer shop sorted it out for me whilst doing some other stuff, so I know it does actually work.

Now I have Jaunty installed, I have no sound again, other than when using headphones or hooking it up to my TV. I had a look here;

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

And followed all of the instructions up to a point where I got stuck (more about that in a minute). It doesn't look as though my card isn't recognised - I didn't get a message telling me there was no soundcard found! This is what I did get: [http://farm4.static.flickr.com/3443/3774295643_bb6d1dc13d.jpg](http://farm4.static.flickr.com/3443/3774295643_bb6d1dc13d.jpg)

Next the instruction is to type; " find /lib/modules/'uname -r' | grep snd "

I tried typing it exactly as it is above but got a message saying there was no such file or directory. So I replaced the 'uname -r' bit with my system's uname (I found it by typing " uname -r " into the terminal). 

Next I got a huge list of stuff! From the instructions, it seems that all of the modules are installed...

Typing in " lspci -v | less " resulted in the following; 
[http://farm4.static.flickr.com/3504/3775117282_437eb02373.jpg](http://farm4.static.flickr.com/3504/3775117282_437eb02373.jpg)

Since there's no sign of an audio device, as described and illustrated in the guide, I’m assuming that it’s a built-in one which needs to be enabled in the BIOS. I’m about to do that now – will report back in a short while!

---

### Post by TheGoktor on 2009-07-31
OK, I've been into the BIOS and I can't see anything there relating to audio at all :(

To be honest, if it's working in Vista, surely it must be enabled? And the fact that I get sound through the headphones and the TV must mean that Janunty has it enabled, no? So is the problem therefore, just the speakers? :confused:

---

