---
title: "How can I enable my wireless? (Broadcom 4306)"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by potentia on 2007-10-21
Hi 

On Gutsy I got my Wireless network running:

**IWCONFIG:**
[FONT=Courier New] IEEE 802.11b/g  ESSID:"mynet"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:BF:A4:EC:E2   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level=-53 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:14138  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/FONT]I can switch it on and off using a switch on the laptop, but I always leave in ON. An orange LED shows that it is turned on. Even when it is off I can see the above output.

[B]PROBLEM:
[/B]However, when I turn the computer off for minutes or more, the LED is OFF when I start the computer. No problem, when I boot into Windows XP then it will get enabled after login and the LED is turned on as well. The driver enables the card, it seems.

In Linux the wireless manager doesn't seem to be able to change my network cards settings though. If I boot into Linux the LED stays off and I cannot connect to the network.

I have to reboot into XP first. XP turns the wireless on, then I can reboot and boot into Feisty.

In other words, without XP on this computer, no wireless networking. 
[COLOR=Red][B]
How do I and others fix this?[/B][/COLOR]

---

### Post by crjackson on 2007-10-21
> **potentia said:**
> Hi 

On Gutsy I got my Wireless network running:

**IWCONFIG:**
[FONT=Courier New] IEEE 802.11b/g  ESSID:"mynet"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:BF:A4:EC:E2   
          Bit Rate=24 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level=-53 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:14138  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/FONT]I can switch it on and off using a switch on the laptop, but I always leave in ON. An orange LED shows that it is turned on. Even when it is off I can see the above output.

[B]PROBLEM:
[/B]However, when I turn the computer off for minutes or more, the LED is OFF when I start the computer. No problem, when I boot into Windows XP then it will get enabled after login and the LED is turned on as well. The driver enables the card, it seems.

In Linux the wireless manager doesn't seem to be able to change my network cards settings though. If I boot into Linux the LED stays off and I cannot connect to the network.

I have to reboot into XP first. XP turns the wireless on, then I can reboot and boot into Feisty.

In other words, without XP on this computer, no wireless networking. 
[COLOR=Red][B]
How do I and others fix this?[/B][/COLOR]

I can't even get gutsy to detect mine.  How did you get that far?

---

### Post by potentia on 2007-10-21
It just did detect it, both when dist upgrading and of course installing from scratch from CD. It only worked when I made a clean install from CD though.

In Feisty I got it working via some HOW-TO from this forum, but I don't remember which one. I do remember, however, that it involved blacklisting the fw-cutter something something driver. I hope you can find it.

---

### Post by Ikslewap on 2007-10-22
The answer.

Two comments:

1. If you have broadcom drivers installed via ndiswrapper on your previous Ubuntu version (and this is the same for many others as well) and did an upgrade into Gutsy, you probably have one problem.  The blacklist file must remain the same or have the added line :

blacklist bcm43xx

The file is found in /etc/modprobe.d/

so....

gedit /etc/modprobe.d/blacklist

then add :

blacklist bcm43x

2. If you had altered the blacklist originally after installing windows drivers with Ndiswrapper, the installation will actually ask you if you want to replace it.  I said yes and had this problem, which is why I'm explaining how to fix it.  If you chose not to overwrite the original, you would **probably** be fine though.  So, if you did replace, just add the previously mentioned line in again and it should function properly. 

--

If you are using a fresh Gutsy installation then you want to get on a system with a connection and download the compressed file for ndiswrapper.   Read the documentation or search for it on [www.ubuntuforums.com](www.ubuntuforums.com) or check out this thread :[http://www.linuxquestions.org/questions/linux-hardware-18/how-put-a-work-wlan-card-broadcom-bcm-4311-on-suse-10.1-469467/](http://www.linuxquestions.org/questions/linux-hardware-18/how-put-a-work-wlan-card-broadcom-bcm-4311-on-suse-10.1-469467/) to install ndiswrapper.  Once installed use a flash drive or CD-ROM to import your xp drivers.  For broadcom users, they are available on [www.broadcom.com](www.broadcom.com).  locate the bcmwl5a.inf file and as root on the command line type

ndiswrapper -i bcmwl5a.inf

Make sure you did the blacklist technique described above.
Restart.

Your wireless light should flash on on your notebook.

I hope this saves someone some time.

---

### Post by potentia on 2007-10-22
Thanks for your reply. I am not going to replace drivers now that I have finally wireless and Ubuntu working, but I will fall back on your advice if I have to fiddle with the drivers one day. Unfortunately what you describe sounds exactly like my Feisty configuration.

I was hoping some obscure commands or simple tweaks could have helped me.

---

### Post by crjackson on 2007-10-24
> **Ikslewap said:**
> The answer.

Two comments:

1. If you have broadcom drivers installed via ndiswrapper on your previous Ubuntu version (and this is the same for many others as well) and did an upgrade into Gutsy, you probably have one problem.  The blacklist file must remain the same or have the added line :

blacklist bcm43xx

The file is found in /etc/modprobe.d/

so....

gedit /etc/modprobe.d/blacklist

then add :

blacklist bcm43x

2. If you had altered the blacklist originally after installing windows drivers with Ndiswrapper, the installation will actually ask you if you want to replace it.  I said yes and had this problem, which is why I'm explaining how to fix it.  If you chose not to overwrite the original, you would **probably** be fine though.  So, if you did replace, just add the previously mentioned line in again and it should function properly. 

--

If you are using a fresh Gutsy installation then you want to get on a system with a connection and download the compressed file for ndiswrapper.   Read the documentation or search for it on [www.ubuntuforums.com](www.ubuntuforums.com) or check out this thread :[http://www.linuxquestions.org/questions/linux-hardware-18/how-put-a-work-wlan-card-broadcom-bcm-4311-on-suse-10.1-469467/](http://www.linuxquestions.org/questions/linux-hardware-18/how-put-a-work-wlan-card-broadcom-bcm-4311-on-suse-10.1-469467/) to install ndiswrapper.  Once installed use a flash drive or CD-ROM to import your xp drivers.  For broadcom users, they are available on [www.broadcom.com](www.broadcom.com).  locate the bcmwl5a.inf file and as root on the command line type

ndiswrapper -i bcmwl5a.inf

Make sure you did the blacklist technique described above.
Restart.

Your wireless light should flash on on your notebook.

I hope this saves someone some time.

I can't get the M@**(%&  ^%!##!!! working.  I'm going to do ANOTHER clean install and try again.  I may have to go back to 7.04 to get wireless back.

---

