---
title: "Linksys USB Wireless unable to connect"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by tomsr on 2008-02-25
I am a newbie to Linux and Ubuntu. I have posted on the beginner forum with my problem but can't find a solution. I'm hoping someone here will be able to assist me.

I have a wireless Linksys WGUSB54Gv.4 USB adapter on my computer running Ubuntu 7.10. By all indications it is recognized but I don't believe there is a driver installed. I can access the Internet via ethernet cable and my Network Monitor shows my wireless network with a strong signal. However, it will not accept my WEP key. I can access other computers on my network (2) but not the Internet. I have tried following some forum directions to install a driver (a windows driver using ndiswrapper and a detailed script which installed an rt73 driver) without success. Find below some information on my wireless adapter:

wlan0 Scan completed :

Cell 01 - Address: 00:18:F3:71:26:7C

ESSID:"stephens"

Mode:Master

Channel:11

Frequency:2.462 GHz

Signal level=-33 dBm 

Encryption keyn

Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s

12 Mb/s; 48 Mb/s

Extra:tsf=00000002f6f64170



wlan0 IEEE 802.11g ESSID:"" 

Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated 

Retry min limit:7 RTS thrff Fragment thr=2346 B 

Encryption keyff

Link Quality:0 Signal level:0 Noise level:0

Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0

Tx excessive retries:0 Invalid misc:0 Missed beacon:0


wlan0 Link encap:Ethernet HWaddr 00:14:BF:7A:A8:B4 

UP BROADCAST MULTICAST MTU:1500 Metric:1

RX packets:0 errors:0 dropped:0 overruns:0 frame:0

TX packets:133 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000 

RX bytes:0 (0.0 b) TX bytes:26898 (26.2 KB)

I am just beginning to learn to use the Terminal and commands. If anyone has any suggestions I would appreciate it. I believe the driver I need is the rt2570. I don't know how to install a driver under Ubuntu--I wish I did!

Thanks much,
Tom

---

### Post by Sam Lars on 2008-02-25
Well it's looking good... how are you configuring the network connection?

---

### Post by tomsr on 2008-02-26
Well, I have tried through Network Manager which always wants my Passphrase or WEP key and I have tried manually setting it up. I must have entered my WEP key a hundred times hoping it'll work. I am sure I have the correct key.

I must say it is driving me crazy. I downloaded a driver (rt2570) from serialmonkey and attempted to install it but just succeded in blocking my wireless entry in Network. Before that, I tried using ndiswrapper as directed in the help files--without success. I ended up reimstalling Ubuntu and downloading the updates so I can start fresh. As of now, my OS has not been tampered with by me. 

My problem must be driver related but I am not sure which driver to try and I don't know how to install the driver if I had it.

I am pretty savy with Windows but a pure rookie on Linux!
Thanks,
Tom

---

### Post by tomsr on 2008-02-26
I just used this command "lsmod | grep usbcore" and obtained these results:

usbcore    138632  4 rt2500usb,rt2x00usb,uhci_hcd

Looks like I have a driver installed?
Tom

---

### Post by Sam Lars on 2008-02-26
You said you reinstalled now... can you still scan and see your router?
Can you set up the router for no encryption?  That will be simpler and if you get it working from there you can add encryption later...

---

### Post by tomsr on 2008-02-26
Okay, I disabled the WEP security. Let's see what happens.
Thanks much for your patience and help.
Tom

---

### Post by tomsr on 2008-02-26
I am still unable to connect even with no encryption. My Vista wireless laptop connects just fine, but not my Linux computer. Any other ideas?

Thanks
Tom

---

### Post by Sam Lars on 2008-02-26
So what do you get if you try to connect to it now?
Can you post the output of iwconfig?

---

### Post by rustybronco on 2008-02-26
> **tomsr said:**
> I have a wireless Linksys **WUSB54Gv.4** USB adapter on my computer running Ubuntu 7.10. By all indications it is recognized but I don't believe there is a driver installed. well at least not the correct one.

> **tomsr said:**
> I am just beginning to learn to use the Terminal and commands. If anyone has any suggestions I would appreciate it. I believe the driver I need is the **rt2570**. I don't know how to install a driver under Ubuntu--I wish I did!

Thanks much,
Tom

> **tomsr said:**
> 
I must say it is driving me crazy. I downloaded a driver (rt2570) from serialmonkey and attempted to install....

**My problem must be driver related** but I am not sure which driver to try and I don't know how to install the driver if I had it.

I am pretty savy with Windows but a pure rookie on Linux!
Thanks,
Tom

> **tomsr said:**
>  Any other ideas?

Thanks
TomYou know for a rookie you sure have got it together! you figured out what driver you needed, you are pretty handy with the terminal, you thought for your self, tried different things and most of all you didn't say **I'm going back to windows... why is this so hard... ect.** Welcome to the community my friend!

oh yeh, I almost forgot about the any other ideas question... [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)
this should do nicely for you, if not give a holler we would be glad to assist.

(you needed the daily rt2570 cvs, yes I have done it with the same usb device)

---

### Post by tomsr on 2008-02-27
> **rustybronco said:**
> well at least not the correct one.
oh yeh, I almost forgot about the any other ideas question... [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)
this should do nicely for you, if not give a holler we would be glad to assist.

(you needed the daily rt2570 cvs, yes I have done it with the same usb device)

Thank you rustybronco for all the good advice-and the welcome. 

I am going to try the instructions offered by AlexMono94. However, he states that I will need the following packages:

build-essential - which you can get from an Ubuntu CD. (Edgy/Feisty/Gutsy etc.) 
linux-headers-'uname -r' - which you can get from a quick search at packages.ubuntu.com 

I searched packages.ubuntu.com for "linux-headers-'uname -r' without success. All I get is a "Invalid Keyword" reply. Can you help me with this? Also, is he saying that I did to install these two packages prior to installing the driver from serialmonkey?

Again, thanks very,very much for all your assistance. This install is a tough one for me. I am a baby in a new world!
Yours,
Tom

---

### Post by rustybronco on 2008-02-27
> **tomsr said:**
> 

linux-headers-'uname -r' - which you can get from a quick search at packages.ubuntu.com 

I searched packages.ubuntu.com for "linux-headers-'uname -r' without success. All I get is a "Invalid Keyword" reply. Can you help me with this? 
Yours,
Tomopen up a terminal and type in **uname -r** replace the output of uname -r with what you get, it should be something like  linux-headers-2.6.22.17-generic when you get done.

Can yiou get online with a wired connection? if so **sudo apt-get install build-essential**
then ** sudo apt-get install linux-headers-**( what you got with uname -r in the terminal)

---

### Post by tomsr on 2008-02-27
Thanks loads rustybronco! I completed the above as you suggested. I'll try installing the driver and get back to you.
Yes, I can get on line via ethernet cable.

Stay tuned and I thank you very much.
Tom

---

### Post by tomsr on 2008-02-29
It's working! The ole WUSB54G is working! Thanks to everyone and especially rustybronco.
Yours,
Tom

---

### Post by rustybronco on 2008-02-29
No, don't thank me, Thank Alex.

***edit*** this method so far only works with wep. if you need wpa you are going to have to use ndiswrapper, plus the drivers from the cd/download for your device.
we can help you with that also if need be.

---

