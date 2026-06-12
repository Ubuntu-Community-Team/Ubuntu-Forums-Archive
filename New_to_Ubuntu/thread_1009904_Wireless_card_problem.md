---
title: "Wireless card problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Joe86 on 2008-12-13
Hi,

I have been trying to get my wireless to work for weeks now.

I have a realtek rtl8187b card on a Toshiba L300 laptop. I have searched the forums and other websites and I still cannot get any wireless, despite trying a whole host of things!. 

When I run modprobe rtl8187b in terminal I get nothing in return, so I assume that this is good.

ifconfig returns:

joe@joe-laptop-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:43:a0:a7  
          inet addr:129.234.178.26  Bcast:129.234.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fe43:a0a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125904 errors:0 dropped:3531201047 overruns:0 frame:0
          TX packets:60469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:142010476 (142.0 MB)  TX bytes:6197281 (6.1 MB)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2004 (2.0 KB)  TX bytes:2004 (2.0 KB)

Therefore, it appears the wireless card is not detected, however, running lsusb returns:

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hu

So the internal usb wireless card is somehow detected.

I have done a fresh install of Ubuntu 8.10, so this wireless card should have the drivers built in according to the recent posts that are around.

Please could you help me to fix this problem?

Thanks. Joe.

---

### Post by stalkingwolf on 2008-12-13
Here is what I do. Ihave a USB wireless adapter and a WIFI card that I use
during initial setup.  The USB is a Netgear wg 111**, the card is a DLink
DWL-G650.  I have yet to find an OS they did not work OOTB with.

If you can You should invest in one or both.  I use the usb around the house,
in fact the landlord has a computer set up for his daughter in his office
that uses one for its primary inet connection.  The card I use when traveling
if I need to.  Less chance of it being smacked around.

I get the USB for about 5.00 and the cards for about 15.00.  I usually keep several of each on hand.

---

### Post by Joe86 on 2008-12-13
Thanks for your reply,
I suppose I could just get a USB external wifi adapter.

The card is connected to the laptop internally, and according to forums and things, 8.10 should now support this card I have. The problem is that when I click on networkmanager, I have no option for wireless networks and when I run ifconfig it appears that I don't have a card attached to the system. I'm a bit perplexed to be honest. Any ideas? 

(Maybe I should have posted this in a more specific area of the forums, but Im relatively new to linux.)

---

### Post by lkraemer on 2008-12-13
Google and Search are your friends..........

A quick search of the forum shows a good looking HOWTO:
[http://ubuntuforums.org/showthread.php?t=792092&highlight=realtek+rtl8187b](http://ubuntuforums.org/showthread.php?t=792092&highlight=realtek+rtl8187b)

You might give it or another posting a try, and cut your week of flailing/testing to a few hours.

Oh, I searched for realtek rtl8187b just as you typed it.

Hope this helps for future searches.

lk

---

### Post by dirac14 on 2008-12-13
Joe86, 

I had the same issue with Realtek RTL8187b wireless card. This is how i ended up with a solution:

First of all, running lsusb returns the following:

```
Bus 001 Device 004: ID 0bda:8198 Realtek Semiconductor Corp. 
```

just as in your case. As you can see, the id of our 8187 card is 8198. RTL8187(id 8197 or 8199) usually works with common drivers existing in 8.10, but you 'll have to do something more as far as the 8198 id is concerned. 

Follow the simple steps described in this link [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b), but just after the step where you run 'sudo patch -p1 <  2.6.24.patch', then edit the r8187_core.c file as in Step 5 in page [http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi-old.html](http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi-old.html). Follow the instructions in these 2 pages and your wifi card should function properly.

---

### Post by Joe86 on 2008-12-13
Dirac14,

Thank you so much for your reply. 
I have mangaged to follow all the steps up to the part where I have to build and install the driver. When I put in the relevant command in the terminal I get this:

> joe@joe-laptop-ubuntu:/wifi$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

So I haven't gone any further becuase this doesn't look right? Did you encounter anything like this when you tried it?

Thanks.

---

### Post by dirac14 on 2008-12-13
Just proceed.I encountered the same issue

---

### Post by Joe86 on 2008-12-14
I've gone through the steps and had no joy. I cannot see an option for wireless in the network manager. When I run modprobe this returns:

> joe@joe-laptop-ubuntu:~$ modprobe rtl8187
WARNING: Error inserting cfg80211 (/lib/modules/2.6.27-9-generic/kernel/net/wireless/cfg80211.ko): Operation not permitted
WARNING: Error inserting eeprom_93cx6 (/lib/modules/2.6.27-9-generic/kernel/drivers/misc/eeprom_93cx6.ko): Operation not permitted
WARNING: Error inserting mac80211 (/lib/modules/2.6.27-9-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
FATAL: Error inserting rtl8187 (/lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/rtl8187.ko): Operation not permitted
joe@joe-laptop-ubuntu:~$ 


I'm not sure what this means. Any suggestions? Thanks for you help so far.


I

---

### Post by Pjotrovitz on 2008-12-14
That just means that you forgot to type sudo first, so the system wo'nt permit you to change those files.

---

### Post by Joe86 on 2008-12-14
Oh yeah! Thanks.

When I use sudo I have no return so I guess thats good.

I've still no wireless though, I must be missing something in one of those steps that dirac14 suggested, but I can't think which, I cut and pasted most of the commands and have gone through them a number of times.

---

### Post by stalkingwolf on 2008-12-15
Is your laptop one of them that has an On/Off button for your WIFI?
Is it on?  I have had this exact thing several times lately.  Get called
to a room because the WIFI isnt working and find the wifi on the guests laptop is off.  Many did not know they had a wifi button or that it needed
to be on to work.

---

### Post by Joe86 on 2008-12-24
Hi,

I do have a wireless card switch on my laptop and it is on. As well as the wireless switch I also have a function key combination that activates the wireless card. However, all the function keys are not detected in Ubuntu. I did wonder whether or not this would mean that the wireless card would be set to off with no function key to enable it, but I don't think this would be the case as when I run lsusb in terminal it tells me that there is the internal wireless card as expected. I'm really puzzled about what to do next, I am sure what I did should have worked as other laptops like mine have apparently worked under Ubuntu with this wireless card. So the problem probably lies within myself not doing something in the intructions pointed out earlier in this thread. Thanks for help so far.

---

