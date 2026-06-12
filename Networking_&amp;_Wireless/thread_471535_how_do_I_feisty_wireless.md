---
title: "how do I feisty wireless"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Greykrrr on 2007-06-12
Hi

Hope someone can help. I've become tired of surfing unanswered threads regarding getting wireless to work on feisty. I use the 64bit version and have a zyxel zyair card which was plug and play on dapper. is there a guide for setting up wireless on feisty, native or ndis?

thanks

---

### Post by Sendervictorius on 2007-06-12
Not sure what chipset you have. type "lspci" on a terminal command line to see. The wireless card line should be obvious.

Check this link to identify any problems. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsZyxel)

If you have the r818x chipset, you will need to install ndiswrapper and load up the windows driver that comes with your hardware CD.

Let us know how you get on.

---

### Post by Greykrrr on 2007-06-13
I have now tried a number of things without success. I am using a zyxel zyair g-302v3 card which uses the r8185 driver.  Here's the output from lspci:

00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
        Subsystem: ZyXEL Communication Corporation Unknown device 340d
        Flags: bus master, medium devsel, latency 64, IRQ 22
        I/O ports at 2800 [size=256]
        Memory at f0000800 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

However I have tried to follow this guide
[http://ubuntuforums.org/showthread.php?t=440116&highlight=rtl8180](http://ubuntuforums.org/showthread.php?t=440116&highlight=rtl8180)

to installing an open version of the 8185 driver which works until the insmod instruction, which fails when trying to insert the driver itself into the kernel (other instructions worked fine) with a message to the effect 'invalid symbol in module'.

After that I did a clean install...again...

If I just comment out the blacklisted r818x driver in /etc/modules.d/blacklist Ubuntu starts fine and the wireless assistent shows a list of all the networks I can connect to. However they all have a signal strength of 0 and I get a timeout when I try to connect to it.

Any ideas?

---

### Post by Greykrrr on 2007-06-13
alright. mostly there now.

I used this guide: [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

First the r818x driver must be blacklisted in /etc/modprobe.d/blacklist. Second the installation of the newest drivers failed for me (as mentioned in my previous post), however the older stable release works.

Unblacklist the r818x driver and reboot.

However I cannot set up a wireless connection manually. Telling the card what essid to use is no good. Instead I need to set it to roaming to access the network and give it the password when asked for it instead. And also the network indicator isn't working properly stating that I have a permanent 0% in the menu and 30% when hold the mouse over the connection.

Last thing is that I can't do make install, so I don't know if this is still working tomorrow. Is there a way to insert modules into the kernel permanently? Or automatically during boot?

Other than the wireless issue, I am loving Feisty! Best Ubuntu release yet!

---

### Post by RocketRanger on 2007-06-17
There is a 64bit driver issue here. I have started a new thread in the x86_64 section.

---

### Post by Quae on 2007-06-19
> **Greykrrr said:**
> However I cannot set up a wireless connection manually. Telling the card what essid to use is no good. Instead I need to set it to roaming to access the network and give it the password when asked for it instead. And also the network indicator isn't working properly stating that I have a permanent 0% in the menu and 30% when hold the mouse over the connection.


I have the same issue- I've only got a 30% signal, and I'm right next to it. I shudder to think how it'll work when I move the computer back upstairs where it belongs.

Did anyone find a fix for this?


Also, I can only access my network through 'Connect to other Wireless Network' and entering the info, but not through taking off the roaming on my wireless and putting the SSID & WEP in there, what can I do to make this 'other wireless network' permanent/load on boot?

---

### Post by RocketRanger on 2007-06-20
> **Quae said:**
> I have the same issue- I've only got a 30% signal, and I'm right next to it.

I'm guessing that you are using the 64bit version of Ubuntu. My problem was that it reported a fixed signal strength of 30% no matter what. Even when I wasn't connected. I have tried to install the i686 version of Ubuntu with ndiswrapper and all these problems went away. Signal strength jumped up to 70%

> **Quae said:**
> 
Also, I can only access my network through 'Connect to other Wireless Network' and entering the info, but not through taking off the roaming on my wireless and putting the SSID & WEP in there, what can I do to make this 'other wireless network' permanent/load on boot?

I have no solution to this. Same problem in the other Ubuntu install.

Btw. If you do use 64bit version what network card do you have and what did you do to get it to work?

---

### Post by RocketRanger on 2007-06-20
I have a found a workaround for these problems. Look at this thread:

[http://ubuntuforums.org/showthread.php?p=2880274#post2880274](http://ubuntuforums.org/showthread.php?p=2880274#post2880274)

---

