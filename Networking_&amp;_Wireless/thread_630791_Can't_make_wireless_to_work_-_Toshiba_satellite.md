---
title: "Can't make wireless to work - Toshiba satellite"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by salvadorveiga on 2007-12-03
Hello people... I've tried a lot in vain to seach for a guide that works...

I have a Toshiba Satellite-L40 and I planned to install Ubuntu in it...my problem is the wireless is not recognized by the way here's my laptop: [http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=137259](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/productPage.do?service=EU&PRODUCT_ID=137259)

Whate are the steps to follow in order to the wireless to function properly ?


Also I have a HSDPA USB MODEM for internet browsing when you have no AP's or anything else...it works through mobile service... the box says it's a HSDPA USB MODEM Model: ZTE MF620

RoHS compliant. I wanted this one to work also...

can anyone try to help me or indicate guides available that work ? than you so much in advance...

I believe it's a Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter (altohugh it says USB there i don't know why...my laptop has internal wireless connection)

---

### Post by salvadorveiga on 2007-12-04
no one ? serious ?

---

### Post by A + on 2007-12-04
No-ones's answering?  I'm almost finished (I hope) getting my wireless working on a Toshiba Equium and I used a guide on an Irish website which was probably taken from here originally.  It has gotten me to the point where I can choose 'wireless connection' from the system>admin>network menu.  the card is Atheros AE5007EG and Realtek ethernet.

How far have you got anyway if anywhere?

---

### Post by salvadorveiga on 2007-12-05
> **A + said:**
> No-ones's answering?  I'm almost finished (I hope) getting my wireless working on a Toshiba Equium and I used a guide on an Irish website which was probably taken from here originally.  It has gotten me to the point where I can choose 'wireless connection' from the system>admin>network menu.  the card is Atheros AE5007EG and Realtek ethernet.

How far have you got anyway if anywhere?

nowhere... i've been reading lots of posts and most say that can't get the wireless to work... my wireless card is a realtek 8187b , which i think it is said to be a pain in the ***...

just trying to make it work for me to drop Vista in this laptop forever...

---

### Post by rustybronco on 2007-12-05
to the original poster.

[http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

read this part (yes the rest will help also)  "Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers"

---

### Post by ante.wessels on 2008-01-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **rustybronco said:**
> to the original poster.

[http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

read this part (yes the rest will help also)  "Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers"

That should work with ubuntu 7.04, but ubuntu 7.10 does not block the r8187 module, it does not have it... I can do 
sudo modprobe rtl8187
and 
sudo modprobe ndiswrapper. 

But then I do not get any further, 
lshw -C network
does not list a wireless.

So my Toshiba L40 15B, with (internal) Realtek rtl8187B wireless USB 2.0  does not yet have wifi with linux. Any ideas?

The workaround is also mentioned at 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78255)
but at the end with ubuntu 7.10 the new problem shows up. 

Thanks!

---

### Post by AceRimmer on 2008-01-04
I'm looking at the same issue.  I've got a 8187B in my Toshiba Satellite that I want to take Vista off of but if the wireless won't work I can't.

---

### Post by bigspottycat on 2008-01-05
I was having the same problems setting up wireless on my Toshiba Satellite L40 until I found this thread:

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

You must follow the instructions exactly (make sure you download the 32bit driver!). My wireless now works perfectly!

HTH

---

### Post by ante.wessels on 2008-01-06
> **bigspottycat said:**
> I was having the same problems setting up wireless on my Toshiba Satellite L40 until I found this thread:

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

You must follow the instructions exactly (make sure you download the 32bit driver!). My wireless now works perfectly!

HTH

Good to hear! Unfortunately, some Toshiba's (like mine) have the Realtek RTL8187B chipset, not the atheros one.

---

### Post by ante.wessels on 2008-01-07
> **AceRimmer said:**
> I'm looking at the same issue.  I've got a 8187B in my Toshiba Satellite that I want to take Vista off of but if the wireless won't work I can't.

I'm not at home at the moment, so I can't check the solution given here:
[http://www.linuxquestions.org/questions/ubuntu-63/wireless-driver-611481/](http://www.linuxquestions.org/questions/ubuntu-63/wireless-driver-611481/)

"Boot on windows.
Go to the device manager and get into "properties" for your network card.
In the "Advanced Options" tab select:

Wake-on-lan after shutdown | enable

Or the card will not be seen by the next boot to linux."

Since the card is indeed not seen (on my notebook), this may help.

---

### Post by kevdog on 2008-01-07
Could this problem be in any way related to the info posted here:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by bigspottycat on 2008-01-08
> **ante.wessels said:**
> Good to hear! Unfortunately, some Toshiba's (like mine) have the Realtek RTL8187B chipset, not the atheros one.

According to my devices manager, I actually have the Realtek RTL-8139/8139C/8139C+ chipset (I believe I even downloaded the Realktek RTL8187 driver at some point during the guide) so the guide below still worked for me. Are you sure it doesn't work for you?

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

All the best.

---

### Post by ante.wessels on 2008-01-09
> **bigspottycat said:**
> According to my devices manager, I actually have the Realtek RTL-8139/8139C/8139C+ chipset (I believe I even downloaded the Realktek RTL8187 driver at some point during the guide) so the guide below still worked for me. Are you sure it doesn't work for you?

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

All the best.

How can an atheros driver work for a realtek chipset? I have both the Realtek RTL8139/810 (=wired) and the Realtek RTL8187B (=wireless). Couldn't the 8139 you mention be a wired nic and you also have an atheros wireless, so that the guide worked? The wireless do not always show up everywhere.

---

### Post by ante.wessels on 2008-01-09
> **kevdog said:**
> Could this problem be in any way related to the info posted here:

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

In the info you link to, the wired ethernet card is not seen. That is not the problem, the wired one is seen, the wireless one is not. It could still be the same problem, just for the wireless one. 

sudo lshw -C network
only shows the wired one.

In windows vista, the wired ethernet card has 3 "wake on" options. The wireless does not have a "wake on" option. I'm not sure I would like my notebook to be waken up by someone driving by - there may be a good reason the option is not available. 

The Vista power saving tab has two options:
Allow the computer to turn of this device to save power.
Allow the device to wake the computer

I turned off the first one, the second one is greyed out. No result.

In the BIOS  I activated wake on lan. Didn't work, but probably the wired ethernet card is activated, not the wireless one. 

I unplugged the machine, removed the battery for some time. The idea is that no energy restores the defaults. Did not help. 

If it is true that Windows deactivates the wireless, I didn't find a way to turn it on again under linux. Should activation be built into linux?

I noticed one strange thing. 

$ lsusb 
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.  
Bus 006 Device 001: ID 0000:0000   
Bus 007 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   
Bus 005 Device 001: ID 0000:0000   
Bus 004 Device 001: ID 0000:0000   
Bus 003 Device 001: ID 0000:0000   
Bus 002 Device 001: ID 0000:0000  

Bus 006 shows up twice. I do not have external usb devices plugged in, so the Realtek one has to be an internal one, I would say the wireless, which is a usb one (and Realtek). But the number 8197 is different than 8187. Could it be it is not recognized correctly? It's only one number off (8->9). Typo?

KInfoCenter | USB Devices has
EHCI Host Controller (6) - RTL8187B_WLAN_Adapter
How does KInfoCenter collect its data, that it has the correct info, while no command on the prompt can find the wireless? Does KInfoCenter probe the hardware, while the commands use the information known by the operating system? The probing by the OS fails?

The fact KInfoCenter can see the device shows it isn't turned off by windows, at least not so that it can not be seen at all. 

Thanks for all the feedback, everyone, more ideas?

---

### Post by befana on 2008-01-09
I have the same problem on my Toshiba Satellite L40 14F with rtl8187b. I've bought the notebook few days ago, and it was without any OS. As at work I need Windows, I've installed Vista. It was a problem with  rtl8187b and Vista, but right after I pluged the internet cable in, Microsoft told me there were problems with the driver, and after Windows updated rtl8187b has started  to work.
I tried Ubuntu 7.10 Live CD and it did not recognize my rtl8187b. And what to do now with a notebook without wireless? Please, help!

---

### Post by ante.wessels on 2008-01-14
[http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+realtek&page=5](http://ubuntuforums.org/showthread.php?t=571046&highlight=toshiba+realtek&page=5)

Xcuervo has a solution that works for me, in combination with Kevdog's manual commands:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) 

iwlist scan gave me the essid of the open acces point I use to write this. If it does not work for you, some other solutions are offered by others (first link, see the rest of the thread).

Thanks!

---

