---
title: "[SOLVED] Am I doing something wrong?"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by Powerman2442 on 2008-02-09
I just got my laptop to dual boot Windows Vista and Ubuntu without a problem. The problem I have run into is that I can't get connected to my wireless network. I'm sorry if you have seen this question before but I searched the forum and didn't really find anything similar to my problem. I have used the help section to try and figure out the problem on my own, but it keeps yielding the same results.

I have a Gateway MT6451 Notebook. The system specifications are as follows. (Let me know if you need to know anything else)

AMD Turion 64 X2 TL-50
DDR2 Dual Channel PC5300 (667 Mhz) 2GB ram
120GB PATA 4200 RPM 2.5" HDD
ATI Radeon Xpress 1150 Graphics

My wireless card is made by Broadcom.
Board: BCM 0465 Rev 3.9
Chipset: BCM4311 / BCM2050
Software Version: 4.102.15.61 Dec 19, 2006
Driver Version: 4.82.28.56 built by: Win DDK Dec 19, 2006

I type in my SSID, my 120-bit WEP key, and I set it to DHCP. In the top right hand corner the little network icon says SSID (0%)

Of coarse the Broadcom works fine with Vista. So I know it is operational. I have seen many people on this forum, so far, that have problems with wireless Broadcom cards. 

I check this link [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) and I don't believe my wireless card appears there.

---

### Post by Powerman2442 on 2008-02-09
Oh yes, I am only using the 32-bit version of Ubuntu Fiesty. If that helps any. Also... my Router is a Linksys WRT54G

---

### Post by Powerman2442 on 2008-02-11
After posting a looked up a bunch more on the forum and found more "fixes" for my problem. None of which worked. Not sure if I am going to continue with Ubuntu or not. It is useless without internet.

---

### Post by erfahren on 2008-02-11
I'm a little confused about the card - input this into the terminal and look for the "Ethernet controller:" lines - post them back here
```

lspci

```

-- there is a good troubleshooting guide [here](http://ubuntuforums.org/showthread.php?t=571188) - it's a little complicated but it has some good information

---

### Post by Powerman2442 on 2008-02-11
The information I got on my card was picked up from when I had to boot up into Windows Vista to post the previous messages. I will however boot into Ubuntu and copy everything down for you. I'll check out the troubleshooting guide as well.

Okay here it is.

02:00.0 Ethernet controller: Marvel Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)

Right below that is...

05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI card (rev 01)

That is exactly how the command listed them.

---

### Post by Powerman2442 on 2008-02-12
Finally! I am posting from Ubuntu right now. It finally works. Now I get to actually play around with the OS. Can anyone tell me how to set this topic and problem solved?

---

### Post by erfahren on 2008-02-13
> **Powerman2442 said:**
> Finally! I am posting from Ubuntu right now. It finally works. Now I get to actually play around with the OS. Can anyone tell me how to set this topic and problem solved?
I'm glad you got it working! Sry I didn't get back to you here - something came up. I saw you got it going yesterday though.

... to mark it as solved just go to the "Thread Tools" above the top post.

again, I apologize. good luck!.

---

### Post by Powerman2442 on 2008-02-13
No problem. I just went around the forums and the web with google and finally got something to work.

---

### Post by roberto08 on 2008-04-28
Powerman2442 , i'm having the same problem and i have exactly the same wireless device. Can you tell me exactly how you got it working? 

I'm actually using a dual boot XP/Mandriva 08, but i assume it will work on Mandriva too.

thanks

---

