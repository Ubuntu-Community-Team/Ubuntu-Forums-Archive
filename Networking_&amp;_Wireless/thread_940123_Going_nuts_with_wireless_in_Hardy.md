---
title: "Going nuts with wireless in Hardy"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by thomasboleyn on 2008-10-06
Hi there, for the past few days since finally managing to get Hardy to run on my vaio pcg-k215z notebook (all it needed was 'acpci=off'!) I've been trying to get my wireless card to work to absolutely no avail.

 lspci -nn brings up the following:

00:09.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)

I've tried various versions of ndiswrapper using synaptic and also by compiling it, and it seemed to accept the .INI file in the windows driver folder from the vaio website, and the ndiswrapper GUI that allows you to add and delete windows drivers states that the hardware 'is present', but there's still no sign of any wireless networks showing up or any menus re wireless anywhere.

I've also tried to use madwifi but it seemed quite complex, and when it started talking about making changes to the kernal config file in the intro of the guide I decided to give up as I have NO idea how to do that.

The card worked perfectly in feisty and gutsy if that is any help.

I have a wired connection at the moment but am moving soon and will have to rely solely on wireless in the new place (or a really long ethernet cable!).

Any help would be really appreciated, thanks.

---

### Post by thomasboleyn on 2008-10-07
frustration bump!:confused:

---

### Post by BitCrusher on 2008-10-07
[I] have the same card and my computer is giving me a similar problem, although my computer is a desktop. I hope you get your answer and that it can help me too.:)

BitCrusher

---

### Post by thomasboleyn on 2008-10-08
I just can't think of anything else to try, it just does *not* want to know about it!

---

### Post by willca on 2008-10-08
Hello

I dont have an atheros nic but if madwifi did not work for you and ndiswrapper then likely there might be overlapping drivers installed already.

I would try madwifi-tools.

sudo apt-get install madwifi-tools

---

### Post by thomasboleyn on 2008-10-08
Hi, I installed this but I'm not exactly sure how to use it.

---

### Post by murphykieran on 2008-10-08
I have a laptop with a similar Atheros wireless chip that I couldn't get working, and ndiswrapper wouldn't work for me.

The solution that worked for me was to install the latest version of Madwifi (it's really not that hard) because the version that shipped with Ubuntu 8.04 didn't support my Atheros wireless chipset.  I then rebooted the PC, went to System>Administration>Hardware Drivers and enabled the Atheros drivers, rebooted again and wireless was working perfectly, it detected my wireless network and when I put in my WEP key, it was fine and it's been working perfectly since.  You may also need to uninstall and remove any traces of ndiswrapper to prevent it trying to take control of the wireless chip.  

I'm no expert, so hopefully someone else can provide instructions or you can search the forums here.

---

### Post by thomasboleyn on 2008-10-08
Thanks for the responses. I installed madwifi before, but after reboting the pc was still using the 'HAL' driver that hardy comes with, there was no alternative option, the only thing I can change is whether this single driver option is disabled or not.

---

### Post by thomasboleyn on 2008-10-09
This is incredibly frustrating..I've tried so many different things now, including blacklisting the exisiting HAL drivers and trying ndiswrapper again..still no luck. 

When I follow the madwifi readme instructions and it says after installing to run "modprobe ath_pci", nothing seems to happen.

I then follow the next instruction of "iwconfig", and only get the following:

"lo        no wireless extensions.

eth0      no wireless extensions."

rather than the expected:

"lo      no wireless extensions.
    
    wifi0   no wireless extensions.
    
    ath0    IEEE 802.11b  ESSID:""
            Mode:Managed  Channel:0  Access Point: Not-Associated
	    Bit Rate:0 kb/s   Tx-Power:50 dBm   Sensitivity=0/3
	    Retry:off   RTS thr:off   Fragment thr:off
	    Power Management:off
	    Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
	    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
	    Tx excessive retries:0  Invalid misc:0   Missed beacon:0"

It just seems as if it's virtually denying this card's existence! It is incredibly annoying. I can't find a great many success stories in forums regarding this chipset to be honest..so frustrating. 

I did notice in the 'requirements' on the madwifi wiki 'howto' a mention of needing to enable certain kernel config options, but I have no idea how to do this and from what I gather it would involve compiling a new kernel :confused:

---

### Post by thomasboleyn on 2008-10-10
I've upgraded to Intrepid beta, still no luck with wireless though..

---

### Post by UgniusS on 2008-10-30
Hi,

Sorry for digging up 2 weeks old thread. I had the same problem installing any recent linux distribution on Sony Vaio PCG-K215Z. Do not know if it's a kernel or/and video driver problem. Anyway installing & running with acpi=off works, but then it is impossible to make wireless card work (and could not start usb 3G modem also). Recently I stumbled upon this [https://bugs.launchpad.net/ubuntu/+bug/221329]("https://bugs.launchpad.net/ubuntu/+bug/221329") bug report. Someone there mentioned that using **nohz=off** and **highres=off** (do not use *acpi=off*) kernel parameters worked for him. I was able to boot Ubuntu Hardy 8.04.1 Live CD with these parameters, and connect to my wireless network (Atheros wireless card worked out of the box). Haven't tried full install though, but it should work.
I've also tried Ubuntu Intrepid RC Live CD with these parameters, but when X should show up, screen just goes blank, no response to keyboard (Ctrl+Alt+F1 does not work). Do not know what causes the problem, so even in Hardy, kernel or xorg update might break things.

I hope this helps at least a little.
Would be very nice to hear success story with Ubuntu Intrepid though.

Good Luck

---

