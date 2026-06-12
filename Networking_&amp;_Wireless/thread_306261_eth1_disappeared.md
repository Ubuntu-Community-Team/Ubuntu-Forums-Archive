---
title: "eth1 disappeared"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by robin_0.8.2 on 2006-11-24
Hi guys

experiencing a nice intriguing issue with edgy on a hp pavilion zd 8112ea laptop with Broadcom wlan card.
eth1 device (previously listed in the GUI network settings list) is now disappeared. All this after following the step by step guide on wiki. if I type ndiswrapper -l i have driver present and device present. but after iwconfig i get this:

root@robin-laptop:/home/robin# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

if i try to ifup eth1 i get this:

root@robin-laptop:/home/robin# ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.

Advices out there? 
Cheers
R_0.8.2

---

### Post by wmatlock on 2006-11-24
I was working with Edgy on my Toshiba Laptop and experienced the same thing. I tried several times including re-loading Edgy. The solution was to download the source for both packages and then build and install them. I have since decided to rest my brain for a while and went back to 6.06 LTS. I am going to keep looking for more info and try again in a month or so. Oh the messages I was reading were from the ndiswrapper forums not Ububtu Forums so you might take a look over there. Matter of fact one of the more thorough responses was using a HP Laptop.

---

### Post by robin_0.8.2 on 2006-11-24
Yeah I guess something needs to be tuned but I really dunno what is wrong here. Worked perfectly on 6.06. Dont really know what to do. Good thing that Ubuntu before Ndiswrapper recognised the card though without being able to make it work, and after the ndis procedure the device disappeared.
I'll keep looking

---

### Post by trubblemaker on 2006-11-24
Couple things, Edgy repositrory for ndiswrapper doesn't work for a bunch of people **if you upgrade**.  Uninstalling *everything* and reinstalling works, that's what building from source usually does (One of the steps is to run 'make uninstall')

the only thing that worries me is you mention both **Broadcom ndiswrapper wlan0 and eth1 **all in the same posting but, you don't seem to mention the bcm43xx driver.

So on edgy there is native support for Broadcom drivers (bcm43xx eth1), this will not work with ndiswrapper (ndiswrapper wlan0), they fight to the death.to correct it look at one of the howto's in my signature.  The "ndiswrapper from source" in my signature is a really easy 10 step program,  It's my favorite right now as it "just works" and doesn't require any outside knowledge.  If you want more info on the other methods check out the first howto in my signature.

Just to make it really clear.

bcm43xx = eth1
ndiswrapper = wlan0

mix of the two = no wireless

---

### Post by robin_0.8.2 on 2006-11-25
thanks trubblemaker

one quick ques: I have blacklisted bcm43xx. Does it make any difference?

---

### Post by trubblemaker on 2006-11-25
for sure it does, you shouldn't see eth1 any more, still think some of the howto's in my signature will help especially the from source, as it's very thorough about removing all instances of ndiswrapper before installing. 

Don't be afraid of the from source, it's a simple 10 step walk through

---

### Post by robin_0.8.2 on 2006-11-25
thanks trubblemaker. I followed your advice and after a coupla of reboots eth1 appeared again. grand. thanks.
the only thing that i cant get to work is this: every time i reboot eth1 goes 'down'. if i type 'ifup eth1' it says that its already up and running. but if i type 'ifdown eth1' and then 'ifup eth1' eth1 goes really up and works great. I have to do this down and up thing every time...

clues?

---

### Post by trubblemaker on 2006-11-25
do you mean that eth1 doesn't automativally come up after a reboot?

If it doesn't you need to add it to your /etc/network/interfaces file. make a duplicate entry to your eth0

---

### Post by robin_0.8.2 on 2006-11-25
well its a bit subtle. as a matter of fact it is up but doesnt work. As soon as I bring it down and then up again it works.
Unclear issue. I go check the interfaces file rite now

---

### Post by robin_0.8.2 on 2006-11-25
i can conferm that eth1 is in the list as 'auto eth1' with all the details about the essd and key number. should be correct so I donnow wheres the missing part...

---

### Post by trubblemaker on 2006-11-25
try adding 
```
 
post-up ifdown eth1
post-up ifup eth1

```
immdiately followig the eth1 entry in the interfaces file and try a reboot?

---

### Post by robin_0.8.2 on 2006-11-25
mmhhhh i tried and now the machine freezes right in the middle of the boot-up. In normal and recovery mode.

Any way to boot without the network support in order to remove the two lines I added? thnks

---

### Post by trubblemaker on 2006-11-25
**** that sucks!  you can always use alt + f2 to look at the output from boot, might even be able to login via commandline.

Failing that you need to use a live cd, like your Ubunutu install disk or something like dsl.  I suggest dsl (damn small linux) as it's really small and takes like a minue to download.  

then once live cd is running is running in a terminal:

```
 
mkdir folder                     #make some directory
mount /dev/hda1 folder           # mount your old file system
cd folder                        # move into your old file system
sudo vim /etc/network/interfaces # edit the interfaces file.

```

I have to say I'm sorry I messed your machine up, post-up run and if they hail then it's over...... oh **** I know what happened it's in a recursive loop.  If we get this fixed I'll show you another way to fix it.

---

### Post by robin_0.8.2 on 2006-11-27
ok trubblemaker I managed to recover the machine don't worry. happens when we want to experiment. its fine. thanks for the latter tip btw, gonna be useful in the future.
The other method you were telling me?

---

### Post by trubblemaker on 2006-11-27
ok so here's a none recursive way to do it.  Write a small script.
```

#/bin/bash
ifdown eth1
ifup eth1

```
make it executable
```
 chmod u+x script_name 
```
using your menu's goto >System>Preferences>Sessions>Startup Programs, and add the script to your session startup programs.

This way the computer runs the commands for you when you login.

---

### Post by trubblemaker on 2006-11-27
Once again sorry for messing up your machine.

---

### Post by robin_0.8.2 on 2006-11-28
really: no big deal. I'll try your tip asap thanx

---

### Post by robin_0.8.2 on 2006-11-28
maybe you can clear me out why after the 'crash' I have removed the two lines but ubuntu still 'hesitates' for some time right in the middle of the boot? if i do ctrl-alt-canc he skips and go ahead....
thnx

---

### Post by trubblemaker on 2006-11-28
I don't know why the new boot system seems to stall on the network but it will if you have anything outside the usual in your 
"/etc/network/interfaces"  check that file for mistakes or a interface that your not booting, both will slow down the boot. _During the boot_ in edgy <crtl>+<alt>+<delete> is the equivalent during the boot <ctrl>+'c' in dapper. Basically it sends killall to that levels' process which seems to be the sign to move to the next stage of boot.

_In short _take another look at you interfaces file, and take auto off anything your not using, (make sure you keep 'auto lo' ) and look out for typo's.

---

