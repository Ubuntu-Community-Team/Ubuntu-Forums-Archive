---
title: "Connecting with a Trendnet TEW 421 (redux)"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by akajonesy on 2006-12-23
I'm a total newbie to linux, got attracted to Ubuntu after playing with the working install disc and decided to try Xubuntu on my older "work" laptop (which had been running Win2K).

I'm trying to get a TEW-421 (A) card (texas Instruments) to work with Xubuntu. I understand it may not be possible, since the card is not supported, but I'd rather not have to buy a new card if there's any chance of getting this one to work. So far the links I've read involved different versions of this card (mine is Ver. A) so maybe this is why mine won't work.

What I've done: 
I've followed all the instructions from the above post (here[http://ubuntuforums.org/showthread.php?t=201673]("http://ubuntuforums.org/showthread.php?t=201673")
here [http://www.ubuntuforums.org/showthread.php?t=243566&]("http://www.ubuntuforums.org/showthread.php?t=243566&")
 and here [http://ubuntuguide.org/wiki/Ubuntu:Edgy]("http://ubuntuguide.org/wiki/Ubuntu:Edgy")
plus googled around for a bit. No luck so far. 


Of interest: when I look in the ndiswrapper folder the INF file has a red "x" on it 

I may have done something wrong when installing ndiswrapper since when I enter:


sudo modprobe ndiswrapper  

it gives me: "Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"

if I enter lspci the network controller is listed as:

"05:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface"

IWCONFIG:

lo no wireless extensions
sit0 no wireless extensions

IFCONFIG

nothing happens.

Can I use this card at all?

thx

---

### Post by akajonesy on 2006-12-26
could really use some help with this one. Anyone?

I've tested the set-up with a wired connection and I can get online no worries, but the wireless still eludes.
I would really rather avoid buying a new card if I can.
thanks

---

### Post by FrodoB on 2006-12-26
This device should work find in Ubuntu 6.06 or 6.10 without ndiswrapper.  
 
If you unstalled using the Alternate CD it will not work until you intstall the linux-restricted-modules. 
 
If you boot a Ubuntu CD, 6.0.6 or 6.10 in live CD mode the device should work and you can test it.

---

### Post by akajonesy on 2006-12-27
FrodoB thanks for answering.

I have both the alternate install disc and the regular (both for xubuntu and ubuntu).
I also have a regular (wired) card that I've used to get online.

How do I go about installing these "linux-restricted-modules"?
I have booted from the "live" install disc but wasn't able to connect (in any way), but this was before I played around with network settings.

Thanks again.

---

### Post by akajonesy on 2006-12-28
never mind. Figured it out. Thanks. :D

---

### Post by jaa1180 on 2006-12-30
What did you do?

---

### Post by akajonesy on 2006-12-31
just use synaptic file manager.
Use the search feature for linux-restricted-modules.
When it comes up, you right click and choose to install it.
Then reboot and thats it.

Mind you, Im not sure if this module is available from the "alternate install" disc.
I was able to go online through a wired connection and I was connected when I used synaptic, so don't know if it got the module from the disc or from online.
However I THINK that the "live" cd has it, so you might be able to get it from that.

Right now Im trying to get the soundcard to work. (cs4237b crystal audio).
I've found some files that seem to be the ALSA drivers for it, but can't tell how the heck to tell xubuntu to use them...

---

### Post by akajonesy on 2006-12-31
argh. that should be "use the search feature and search for "linux-restricted-modules""

---

