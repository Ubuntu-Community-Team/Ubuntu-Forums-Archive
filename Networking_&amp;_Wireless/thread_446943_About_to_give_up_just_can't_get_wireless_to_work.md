---
title: "About to give up: just can't get wireless to work"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by Pyrogenesis on 2007-05-17
Hi all. I'm a new switcher from Windows - from Vista, to be more precise. That piece of mess finally did to me - I could no longer take it, and I ordered Ubuntu to replace it. Installation went mostly smoothly (had some trouble with widescreen resolution, easily fixed by running the autodetect script again), but I've been trying for two days now to make my wireless connection work, and no luck. So perhaps the good people here can give me some advice. Here's the situation:

I'm trying to get wireless working on my FS Amilo A1630 laptop (meaning it's AMD64) which has a RaLink rt2500 802.11g cardbus/mini-PCI wireless card. Network is protected by WEP 64/128bit hex. Router: Thomson SpeedTouch 780WL. Wired connection works perfectly.

What happens is that when I try to log on, it briefly tries to connect, telling me "Waiting for network key", finally failing - and when I now check connection information, all the lines (from IP address to gateway etc.) except hardware address display 0.0.0.0.

iwconfig shows both the ESSID as well as the access point info.

sudo ifup ra0 results in the message: Ignoring unknown interface ra0=ra0. Perhaps this is the key to the problem? What must I do? Is this a driver problem? I tried looking for the rt2500 drivers but only found the source code.

Setting a static IP also doesn't change anyting. The only noticeable effect I've found is when I manually enter both static IP info and DNS server address - this results in a short timeout period in Firefox before I'm told there is no connection, whereas in other cases this happens immediately. Also, frequently, when I try to check the connection information, I get an error message: "Could not find some required resources (the glade file!)"

Another odd thing is that the connection strength bar is always at zero, even when I'm right next to the router, yet iwconfig currently shows Link Quality 56/100. Don't know if this is relevant.

Let me know what other information I should provide. I'll be avoiding going back to Vista for as long as possible, so please help!

Thanks in advance!

---

### Post by Pyrogenesis on 2007-05-17
I read in another thread to post the log messages as they roll in. So here it is, the sudo tail -f /var/log/messages when trying to connect, in roaming mode. All I get is: 

May 17 21:56:59 silver-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ra0 for sub-path ra0.dbus.get.reason
May 17 21:57:07 silver-laptop kernel: [ 1987.000879] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready

That's it.

---

### Post by blazercist on 2007-05-17
yes I feel your pain i have an rt61.  The rt2x00 drivers are still under heavy development and glitchy, but they are rapidly getting better.  

I got mine working after 2 months of forum scraping and googling all possible combinations of the string "rt61 ubuntu feisty " etc.. etc..   

Anyway try using a script like the one I use

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>
sudo dhclient ra0

obviously you will need to change it to match your settings but it should work, if not you can post here again or PM me I will be glad to help... Its probably an issue with the driver, the rt2x00 driver has problems remembering your WEP key once you've set it AFAIK, theres a patch for it but it can get confusing so ask for help if you need it.

EDIT: Try to disable the WEP on your router and leave it OPEN, see if you can connect this will help narrow down the problem.

---

### Post by Pyrogenesis on 2007-05-17
Thanks for the quick reply!

I tried the script. Its result is that now it shows that the wireless has a signal. However, no connection, and here is the log when I was typing it in. I'm not sure if the pppd PAD0 packets timeouts are relevant - they may be the side-effect of me messing with pppoe.

May 17 22:17:05 silver-laptop pppd[4036]: Timeout waiting for PADO packets
May 17 22:18:10 silver-laptop pppd[4036]: Timeout waiting for PADO packets
May 17 22:18:45 silver-laptop kernel: [  547.619748] 'iwpriv <dev> set NetworkType' is deprecated, please use 'iwconfg <dev> mode' instead
May 17 22:19:15 silver-laptop pppd[4036]: Timeout waiting for PADO packets
May 17 22:20:14 silver-laptop kernel: [  636.476936] 'iwpriv <dev> set DefaultKeyID' is deprecated, please use 'iwconfg <dev> key' instead
May 17 22:20:20 silver-laptop pppd[4036]: Timeout waiting for PADO packets
May 17 22:21:25 silver-laptop pppd[4036]: Timeout waiting for PADO packets
May 17 22:21:25 silver-laptop pppd[4036]: Exit.
May 17 22:22:01 silver-laptop kernel: [  745.278448] 'iwpriv <dev> set Key1' is deprecated, please use 'iwconfg <dev> key [1] ' instead
May 17 22:22:45 silver-laptop kernel: [  788.572871] 'iwpriv <dev> set essid' is deprecated, please use 'iwconfg <dev> essid' instead

Where can I get the patch? I'll try disabling the protection from router tomorrow.

---

### Post by blazercist on 2007-05-17
ok looks like that script is a little outdated ill edit this post wen I find a better one, good news is I think we can get this working.

---

### Post by blazercist on 2007-05-17
actually, before I go any further with the johnny on the spot fixes, do you know how to patch/compile/install a driver from source or am I going to have to walk you through it?

---

### Post by Pyrogenesis on 2007-05-18
Sorry, no idea how to compile and install a driver. I only did something like that in Windows two or three times, and I've been trying to use linux just for three days now.

---

### Post by Hyuuga on 2007-05-18
I got the same problem. I don't quite get the part with rt2x00 drivers beeing under developement since it worked *pefectly* (actually more than perfectly) in ubuntu 5.1 and 6.06

The readme that follows the drivers is also hilareous and explains me nothing, and the FAQ points me to internet which i clearly don't have when i'm trying to install a wireless network driver. I'm dual booting with windows and can't have both up at the same time, so i guess i'll just write down the link, but it's still hilareous. I'm just glad i didn't format the windows partition yet. I finally figured a way to get hardware acceleration on the graphics card on my amilo l7300 then of course wireless cuts out, when i get this fixed i am saying permanently bye bye to windows.

---

### Post by blazercist on 2007-05-21
again, before we go any further i recommend that you disable WEP on your router and see if you can get a connection.  post again with the result.

---

