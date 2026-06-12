---
title: "WPC54G - WEP - Not working."
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by gentrybr on 2007-02-02
Hello all,

I am trying to setup a wireless card on my Dell Latitude CPx.  Here is where things stand.  My ubuntu kernel version is** 2.6.17-10-generic**, which i read somewhere on the forums that i did not need to use **ndiswrapper**.  That instead there was native support if i used fwcutter to extract the firmware from my windows .sys file.  I did that from the linksys cd (extracting from the file BCMWL5.sys) and the card came up just fine.

SO.. **iwconfig** shows me that eth1 is my wireless card - here are the details..

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:12:17:7B:06:E7   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:203D-D7EB-FA   Security mode:open
          Link Quality=88/100  Signal level=-43 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:4  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

As you can see, it can also see my access point.  Also, notice that it is giving me back "Rx invalid crypt:4"  This number keeps going up and up (which i assume to mean that there is something not set correctly between my access point and card with regards to the WEP encryption.  I have generated a 10 digit key from the access point and other computers are working with this key just fine. I have also tried other keys that are listed by the access point as valid - to no avail.

** iwlist** give the fillowing...

 Cell 01 - Address: 00:12:17:7B:06:E7
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-30 dBm  
                    Extra: Last beacon: 492ms ago
          Cell 02 - Address: 00:12:17:7B:06:E7
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-49 dBm  
                    Extra: Last beacon: 368ms ago

So a few questions.

1.  Do i need to use ndiswrapper?  If so, do i have to use wlan0 as the interface or will it work with eth1?
2.  Is it true that you can only use the network manager applet with DHCP connections and for devices not listed in /etc/network/interfaces?
3.  What am i doing wrong with getting the access point and card to talk!?

Regards to all,
brian

---

### Post by gentrybr on 2007-02-03
anyone?

<<bump>>

---

### Post by Vox754 on 2007-02-03
Post your version number for WPC54G.
There are many as v.1, v.2, v.3, v.4, v.5, v.6. Each one has a different chipset and different drivers.
Post the specific info of the hardware with "lspci -v".

You have plenty of time so edit your posts to use the "[CODE]" tags.

My advice, uninstall "ndiswrapper", get the new version 1.37, and start over again.

I'm sorry I can't further help you, I have WPC54G v.4 so it's a different matter.

---

### Post by gentrybr on 2007-02-06
v.2 of the WPC54G

so you are saying that i need ndiswrapper?  am i also going to need to use fwcutter to get the firmware or will it work just with ndiswrapper?

regards,

brian

---

### Post by Vox754 on 2007-02-06
> Do i need to use ndiswrapper? If so, do i have to use **wlan0** as the interface or will it work with **eth1**?
It will work with whatever you have, if "iwconfig" says "eth65756756756" then you use that.

> so you are saying that i need ndiswrapper? am i also going to need to use fwcutter to get the firmware or will it work just with ndiswrapper?

I don't know your card, so I can't give you details.
It seems that your card is working strangely, but it is recognized by the driver.
People suggest this: if the native driver doesn't work quite well, you may try "ndiswrapper"; it doesn't hurt trying as you may uninstall it whenever you want.
Look here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

I'm sure I've read successful stories with WPC54G v.2; you should follow those threads, and maybe send private messages to their authors. Just do it politely.

---

### Post by dmizer on 2007-02-07
your card does work with native firmware, but there are problems with it, so i generally stick with ndiswrapper.

i have gotten my v2 card to work with ndiswrapper consistently and i wrote a howto: [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)

be forewarned though ... making ndiswrapper work with this card is no fun.

if you have problems, post in the above thread and i'll do my best to help you out.

---

