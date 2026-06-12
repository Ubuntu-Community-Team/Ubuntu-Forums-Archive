---
title: "Network problems AE2500"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by christopher14 on 2014-07-16
Hello- wife and I are tired of windows so we want to install Ubuntu we are new to it 
and we only have two ways to access internet. Via USB wireless adapter AE2500 linksys or via 
USB tether from iPhone 5s
problem is everything I read says it won't work with our USB adapter it might on 32 bit but we have 8GB ram so 64
bit would be better. And linux can't recognize iphone as network unless download some stuff all of which we can't do because we can't use our USB adapter. We share net with neighbor - again once we install Ubuntu we have no access to internet unless we can get it to work with AE2500 linksys USB adapter or somehow with tether from iPhone 

is there a way to use either or get with setup off line? IE download needed files to a flash drive then use after install.
we did a lot of looking around and really want to use Ubuntu but if we can't use USB adapter or tether from iPhone 5s 
then we can't break microsofts hold on us.

and if there is a way is there a not smart persons way/instructions lol all I can do via terminal is sudo apt-get install
thats about the extent of my knowladge

thank you for your time and patients with us any help would be greatly appreciated we are at out wits end with windows

---

### Post by Vladlenin5000 on 2014-07-16
Hi, welcome.

First of all, in order to troubleshoot a WiFi installation, having a wired connection (Ethernet AKA "LAN") is strongly recommended for the obvious reasons you mentioned - additional packages that may have to be downloaded and installed. That said, it isn't mandatory.

I just did a quick search regarding your Linksys AE2500 and it has, apparently, a **Broadcom BCM43236** chipset under the hood. This is what really matters for checking whether or not it works with a native driver and if not, other solutions. Hopefully an expert will give you some useful info.

---

### Post by christopher14 on 2014-07-16
Hi, thank you

i wish I could use LAN ATM just not able to ill google that chipset see if anything pops up. Spent hours trying find a way to get this to work. 

I found this [http://opensuse-guide.org/wlan.php](http://opensuse-guide.org/wlan.php)  which takes me to this site [http://wireless.kernel.org/en/users/Drivers/brcm80211#Get_the_code](http://wireless.kernel.org/en/users/Drivers/brcm80211#Get_the_code)

Yea- lots of stuff i dont understand....  kernel says my chip not supported but open-suse says this specific on on there site linked.....

Been banging my head with this all day and its a little disappointing. Was really looking forward to using Ubuntu but not even being able to support a network adapter is sort-of off putting.. i plugged this into neighbors mac and their PC and works right away(pc after driver search lol) Wireless is more common then Wired these days having support should be a priority. Especially if the community is to grow, and we want to be a part of it

---

