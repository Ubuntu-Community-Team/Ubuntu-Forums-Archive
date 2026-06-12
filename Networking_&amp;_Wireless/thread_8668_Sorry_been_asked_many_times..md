---
title: "Sorry been asked many times."
date: 2004-12-19
forum: Networking &amp; Wireless
---

### Post by MiseryQ on 2004-12-19
First I'll have to admit that I usually try a few Linux distros about once a year then abondon the idea of using them. Well the time has come again and I've tried over the last few days, Xandros, Mandrake 10.1, Lycoris and now Ubuntu since I read good things about it.

I'm lost on networikning and don't know where to start. It's a Toshiba 4600 with a MPCI ORiNOCO and a Intel Pro/100 ve.

The Intel is reconized and shows in device manager while the ORiNOCO does'nt.
In the Network-Admin neither was there. I added the Intel 1st (eth0) and tried to activate it. It will not stay activated. I tried the same thing with the ORiNOCO and got  the same results, it will not stay activated.

I've searched the forum but am still a total n00b after all.
I got the Intel working in Madrake but nothing in the others, Lycoris would'nt even install, "hardware not supported at this time" :).

Thanks
Q..

---

### Post by Averatec5400 on 2004-12-20
[QUOTE=MiseryQ]First I'll have to admit that I usually try a few Linux distros about once a year then abondon the idea of using them. Well the time has come again and I've tried over the last few days, Xandros, Mandrake 10.1, Lycoris and now Ubuntu since I read good things about it.

I'm lost on networikning and don't know where to start. It's a Toshiba 4600 with a MPCI ORiNOCO and a Intel Pro/100 ve.

The Intel is reconized and shows in device manager while the ORiNOCO does'nt.
In the Network-Admin neither was there. I added the Intel 1st (eth0) and tried to activate it. It will not stay activated. I tried the same thing with the ORiNOCO and got  the same results, it will not stay activated.

I've searched the forum but am still a total n00b after all.
I got the Intel working in Madrake but nothing in the others, Lycoris would'nt even install, "hardware not supported at this time" :).

Thanks
Q..[/QUOTE]
 open a terminal and type:
sudo ifup eht0


see if it stays up then, and also the output from it. If it doesnt stay up go to /var/log and check the dmesg and kern.log s to see if you can find out why it didn't stay up.

As far as wireless, it is the same/similar, from terminal:
sudo ifup wlan0

for wlan0 to work you might have to first turn off the th0(I did) by:
sudo ifdown eth0

---

### Post by MiseryQ on 2004-12-20
**sudo ifup eth0:**
*interface eth0 already configured*

**sudo ifup wlan0:**
*Ignoring unknown interface wlan0=wlan0*
That is after bringing down etho.

Looked at dmesg and kern.log but did'nt I really do'nt know what I'm looking for. There are some ACPI errors.

---

### Post by mistic on 2004-12-25
afaik the orinoco-cards need a patched driver to work correctly, haven't had the chance to test it out yet though since i don't have the luxury of an orinoco-wifi-card...

---

### Post by charleyramm on 2004-12-27
Orinoco card would work perfectly i should think. Unless it is one of those crappy new ones.  'Client 11b gold card' or something.

---

### Post by torque2k on 2004-12-29
Hi, all. I'm going to piggyback on this problem, if you don't mind. I've got a Compaq Evo N610c which also has an Intel Pro/100 Vx (Ubuntu sees it as 82801CAM [ICH3] PRO/100 VM [KM]). The chipset for the board is an i845 running a P4M 1.6GHz.

Ubuntu picked up my PCCard-based D-Link DWL-650 wireless 11b card with NO problem (plugged it in as eth1 automatically). This suggests that Ubuntu WANTS to set eth0 aside for something, but doesn't know what.

I'm getting a bit frustrated here, as I'm trying like mad to give this a shot. I dumped XP for SuSE 9.1 Pro a few weeks ago, but was having issues with the wireless under SuSE, and was never able to get the Winmodem (Lucent) under control. Ubuntu showed more promise (wifi is perfect) but why the heck can't it pick up the (very standard) Intel PRO/100 series? SuSE and FC2 had no problems with it at all, neither did Knoppix or SLAX live CDs...

In dmesg, I see this line by grepping for "Intel":
```
e100: eth0: e100_probe: addr 0x40100000, irq 10, MAC addr 00:02:A5:BE:xx:xx
``` (I added the xx:xx in the MAC for this post only) kern.log lists nothing of interest as far as eepro100 or e100 or eth0. No errors, no good news either.

Adding an ethernet interface via the "Network" panel yields a non-working eth2, with the same problems as the person above. Same modules loaded, too.

I'll try booting up the live CD and see if it picks up eth0 correctly. If not, I've gotta say this is a bug, as like I've said, other distros have had NO problems picking this up.

---

### Post by torque2k on 2005-01-04
Just an update. I'm wondering if the Live CD and the official install CD (from the same package sent to me) are running the same software versions for hardware detection?

Live CD picked up the Intel PRO/100 Vx in my Compaq tonight, reserved a DHCP lease, and worked on the internet for browsing. 

BUT, under the Live CD I no longer have full use of my Synaptics touchpad! No tapping, no scroll region on the right side, just standard PS/2 mouse functions. 

So I'm going to have to play with the Live CD setup a bit further to see what's being called differently between it and the full install. If I find anything useful, I'll post it here. This could be a few days to a week, though, because I needed that notebook running again on a network, badly, so I imaged the Ubuntu installation, and reapplied my Windows image. I'll switch back hopefully tomorrow to start testing.

Meanwhile, can anyone shed some light on why the full install won't see the PRO/100 but the Live CD will?

EDIT: Also, can a mod change the topic name to something more "searchable", such as "Ubuntu not picking up Intel PRO/100 NIC..." ?  :)

---

### Post by linux noooob on 2007-06-03
try mad wifi it might work i dont know i have heard good things about it. even though after i was done nothing happend so good luck to you*also if anybody wants to help woth my problem go ahead* hope this helps:) 

ps. sorry about my crappy spelling

---

