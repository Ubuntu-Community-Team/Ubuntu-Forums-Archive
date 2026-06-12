---
title: "Wireless Adapter F5D6050 problems"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by jdolan on 2007-05-09
Hey,

I have been trying to get my wireless adapter working on Ubuntu Feisty for days now and seem to be getting nowhere. If anyone could help me that would be fantastic as it would be a shame to have to drop Ubuntu just because of a silly little issue like this.

I have a **Belkin F5D6050 Wireless USB Adapter**. The adapter works fine from within Windows. When I look at the settings through network tools (Ubuntu) it says there is the loopback, the eth and the wlan found. The packet readings for the wlan give the impression that data is being sent but not received.
I have read the supported wireless cards wiki and my card is not listed. I then tried to install ndiswrapper but whenever I try to compile it through terminal there were a load of errors and it wouldn't compile.

I don't know what else to do, I can't get ndiswrapper made, I can't connect to my local network yet Ubuntu seems to pick up the eth and wlan. It occasionally also picks up my network ID name.

If anyone has had the same problem or think they may be able to point me in the right direction - please do!
Would it be worth posting the terminal output when I try to install ndiswrapper as I have a feeling that (if I can get ndiswrapper installed) I can get my wireless card working.
In know I can get this working as the Ndiswrapper website states the following about my card:

[I]
[COLOR="Red"]Card: Belkin F5D6050
      Chipset: Atmel at76c503-rfmd
      pciid: 050d:0050
      Driver: Belkin [http://www.belkin.com/support/download/files/F5D6050z.exe](http://www.belkin.com/support/download/files/F5D6050z.exe)
      Other: Download the driver. Extract to a new directory using unzip. Extract the CAB files (DATA1.CAB, DATA1.HDR, DATA2.CAB) using “unshield x” . cd Drivers/WINXP .[/COLOR] edit bkusb.in_ and uncomment the CopyFile.XP.Sys section. Run ndiswrapper -i bkusb.in_ as root followed by ndiswrapper -m . modprobe ndiswrapper. ifdown wlan0. ifup wlan0 and you are there.
[/I]

What do these instructions mean exactly? The red stuff I understand, the rest I don't!

Thank you so much!

Jord

---

### Post by chili555 on 2007-05-09
The module *at76c503* is built in to the kernel. It is evidently loaded, because you have a wlan0 interface that is sending packets, but not receiving. Why do we want to fiddle with ndiswrapper?

I think your interface just wants to be associated with your access point. Network Manager is installed by default in Feisty and it should greatly simplify the process. In order for NM to take control, you will need to go into System -> Administration -> Network and mark wlan0 for Roaming Mode. You should then be able to click the NM icon in the panel, select the network you want to connect to, fill in any encryption details and go!

Post back and let us know.

---

### Post by jdolan on 2007-05-09
Thank you chili555! I am *almost* there now.

I set the connection to roaming, the signal strength bar came up, I clicked it and then clicked my wireless connection ID and it asked me for the WEP key. However, there is one last problem now - I have entered the key correctly ( a number of times ) selected open system ( as that what it is ) and selected the correct key type (WEP 128bit hex). 

I then click OK and the box disappears. However, no connection is being made as the connection information dialog shows that the router has not assigned the computer an IP address - everything is 0.0.0.0 'd out.
About a minute after doing this, the WEP entry box will reappear as if I entered an incorrect wep key.

I think I may have an idea about why this is happening but am not entirely sure how to get around it.
My router does not only have a WEP key but a **key number** 0, 1 , 2 and 3 for extra security. Now under Microsoft Windows, you can specify the key number to which your WEP key is assigned, but I can't find any way of doing this under Ubuntu. Is there a way? Could this be the problem now?

Many thanks for your prompt help - I wasn't expecting such a fast response!

Thanks, 

Jord

---

### Post by chili555 on 2007-05-09
Oddly enough, Linux assumes the keys are 1, 2, 3 or 4. It assumes the key is 1 unless otherwise specified. If you are using key #1 from the router, you have no worries. If you are using key 2, 3 or 4, the manual way is from the manual page of iwconfig:> iwconfig eth0 key restricted [3] 0123456789I don't know if you could put a *[3]* for key #3 in Network Manager preceding your key, or not. It's undoubtedly easier to use key #1.

Also, iwconfig, for which Network manager is a gui front-end, along with some other utilities, seems to like lower case in the WEP key; 096c7f299e....etc. rather than 096C7F299E...etc.

---

### Post by jdolan on 2007-05-09
Thanks for all your help.
I'll give it a try later this evening.

Jord

---

