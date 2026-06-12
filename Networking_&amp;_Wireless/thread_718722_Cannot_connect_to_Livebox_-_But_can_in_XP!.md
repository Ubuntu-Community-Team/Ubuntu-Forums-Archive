---
title: "Cannot connect to Livebox - But can in XP!"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by bunny_basher on 2008-03-08
I have finally installed Ubuntu 7.10 but i am having problems connecting to my Orange LiveBox.
I put the WPA key in the box and about 5 seconds later it asks for it again!
Can somebody please tell me how to connect, am i missing something?

Cheers
Bunny_Basher

---

### Post by ssj3strife on 2008-03-08
I assume this LiveBox is some sort of wireless access point? If you know the specific settings, try bringing up the NetworkManager applet's menu and selecting "Connect to other network," or similar option, and entering the appropriate options manually. I know I couldn't connect to my university's wireless network until I did that, maybe you're having the same sort of issue.

---

### Post by bunny_basher on 2008-03-08
Nah, still can't get it to work?!?!:confused:

---

### Post by ssj3strife on 2008-03-08
Do you know what type of wireless card you have, and what sort of chipset it has? If you don't know, could you run lspci and post the output here?

---

### Post by bunny_basher on 2008-03-08
I dont acually know what card I have - the one that came with the pc! lol- but I will do that lspci thing now mate if you tell me how?? (I'm newer than new to Ubuntu! lol)

Thanks
Bunny Basher

---

### Post by bunny_basher on 2008-03-08
Found out how to do lspci and here are the results...

marcus@Bunny-Basher-Linux:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:01.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
03:01.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
03:01.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
03:01.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
03:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04)
marcus@Bunny-Basher-Linux:~$ 

Hope that will help with the problem!
Bunny Basher

---

### Post by bunny_basher on 2008-03-09
BUMPED - I really want to use Ubuntu!

Thanks
Bunny Basher

---

### Post by bunny_basher on 2008-03-09
Anyone??

Bunny Basher

---

### Post by Neilisgreat on 2008-03-10
I have been trying for months to get ubuntu to work using 3COMUSB adpter to connect to my orange live box IT DOES NOT WORK! 
Its  suposed to work out of the box?? with ubuntu !
UBUNTU AND WIFI SUCKS ,GET IT SORTED !!!!
Iam now having to connect via ethernet cable which does work.

:frown:

---

### Post by ssj3strife on 2008-03-10
It looks like the Atheros driver is pretty well supported in Linux, but I can't say I've ever used one myself. Can you connect to other wireless networks? You might try checking out the madwifi-tools package and seeing if anything in there helps you, it seems to be designed specifically for Atheros cards.

Good luck!

---

### Post by Jay Jay on 2008-03-10
> **Neilisgreat said:**
> I have been trying for months to get ubuntu to work using 3COMUSB adpter to connect to my orange live box IT DOES NOT WORK! 
Its  suposed to work out of the box?? with ubuntu !
UBUNTU AND WIFI SUCKS ,GET IT SORTED !!!!
Iam now having to connect via ethernet cable which does work.

:frown:

I'm forced to agree - I've spent half the day trying to get online and only succeeded after using my Windows dual boot and the Live CD. This is the 2nd time in a few months that I've had this problem where the Ubuntu wireless completely fails but works from the Live CD. Last time only a reinstall cured it and I don't wanna have to go through that again.

I rely upon Ubuntu for the bulk of my serious work. It's so frustrating having to fall back upon Windows during crisis situations and downtime.

The most reliable form of Internet connectivity under Ubuntu seems to be through wired Ethernet.

---

### Post by bunny_basher on 2008-03-11
Ethernet it is then! I better not have the same problems then! 

Bunny Basher

---

### Post by prince sparkle on 2008-03-22
it is impossible to connect to a orange or wannado live box (they are the same anyway lol) unless its wifi is in paring mode. this can be done by accessing the boxes console in some firmware versions however the sure way is to give button "1" a poke on the back of the box. the wireless light should start blinking and you should be able to connect. once youv done it once the box remembers you so you dont need to do it again.

i dont know if anyone knew this but i dont think it was mentioned :confused: but it may well be the answer you were looking for :)

---

### Post by hopkinsjeni on 2008-05-23
If it makes you feel better I have been having the same problem for 3 weeks. I have installed fwcutter which helps find the livebox but i still get asked for my password every 5 seconds. 
If you have thought about calling orange for help, don't bother. The tech support people have never even heard of Linux!
Please let me know if you resolve the problem!
:KS

---

### Post by itsallcrap on 2008-06-11
I am running wireless internet on an Orange Livebox using an atheros wifi card under Ubuntu hardy.   Successfully.

We still don't really know how far you've got with this.  When you click System > Administration > Network, do you see "Wireless connection" listed?  And if you select that can you see a list of nearby routers?

If not, follow these instructions:

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)
[I]
EDIT:  Oh, wait, you're on Gutsy, aren't you?  Anyhoo, it's pretty much the same process.[/I]

If you can see them and you're definitely entering the right kind of key and have the right kind of security selected (and allow DHCP) and it's STILL not working, I suspect you might have the same problem I had.

Namely, your computer has a different hostname in XP than in Ubuntu.  When you run the Orange CD in XP, the Livebox keeps a record of your MAC address filed with your hostname.  Then Ubuntu comes along claiming to have the same MAC address but a different hostname.  Livebox tells it to fsck off.

You can change your Ubuntu hostname in the 'General' tab in System > Administration > Network.  Set it the same as it is under XP and reboot.

---

