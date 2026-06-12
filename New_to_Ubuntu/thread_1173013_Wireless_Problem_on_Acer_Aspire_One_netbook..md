---
title: "Wireless Problem on Acer Aspire One netbook."
date: 2009-05-29
forum: New to Ubuntu
---

### Post by funkyali on 2009-05-29
Hi

My wireless was working perfectly until a few days ago when I tried to install Sun virtual box and wine say that I could setup internet explorer on a virtual box.

It would not give me the wireless option. I was on 8.10 but last night upgraded to 9.04 thinking that it may sort the problem out. Now I can see the wireless options but I still cannot connect.

Any suggestions?

---

### Post by funkyali on 2009-05-29
forgot to mention that I am dual booting and can connect to my wireless WPA network from XP.

---

### Post by carcar1 on 2009-05-29
Many people are experiencing this problem.I have an acer aspire 5100 with the same card as the aspire one.  The atheros ar5007eg.  This card is very devious.  How did you get it working in 8.10?  If you are familiar with ndiswrapper that solution is easy.  Because you have it working with xp just go to where the driver is located or google around for atheros ar5007eg ubuntu driver.  Install ndiswrapper and and ndisgtk a gtk frontend for ndiswrapper.  And simply fidn your inf file for your card and bam it should come back.

---

### Post by funkyali on 2009-05-29
I've got it working multiple times on 8.10 just by following the easy official tutorial.

how do I  use ndiswrapper? I'm still new to ubuntu/linux.

---

### Post by MockY on 2009-05-29
Why on earth would you willingly use IE when you already have Firefox installed. I am very confused to why you would go through that much trouble to use an inferior browser.
But if that is you choice, then [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") sounds like a much easier option. Unless IE7 is the browser you want to use.

---

### Post by funkyali on 2009-05-29
I need all IE versions as I want to make sure my sites are compatible.

---

### Post by MockY on 2009-05-29
And you are developing these sites on a Acer Aspire One? Sorry, but I find that very odd.

---

### Post by funkyali on 2009-05-29
Sorry since when does it matter what machine you use to develop web pages?

I need help to connect to my wireless network and I think we going off the topic.

---

### Post by MockY on 2009-05-29
Sorry for going off topic, but me personally would be completely frustrated developing webpages on a 8.9" screen. Does not sound at all effective.

On topic: I would install 9.04 from scratch and use VMWare. I have had bad experiences with Virtualbox in the past (though that would probably not be the case anymore) so I'm sticking with VMWare which I know works the way I want it. I just installed 9.04 from scratch on a Aspire One, and it all worked perfectly out of the box.

---

### Post by funkyali on 2009-05-29
I use a kVM switch so dont have to deal with small screen/keyboard only when I'm out and about. :P So now I know were you coming from :P

I think something has been corrupted with the drivers any commands I should try?

---

### Post by nothingspecial on 2009-05-29
Same card, different box, (samsung nc10)

Try editing /etc/modules

```
sudo nano /etc/modules
```

and adding ```
ath5k
``` to the bottom, my card broke after an update, that fixed it.

---

### Post by funkyali on 2009-05-29
when I typed ```
sudo nano /etc/modules
``` I already have > 
lp
ath_pci

should I still add what said?

---

### Post by funkyali on 2009-05-29
ifconfig produces this
> eth0      Link encap:Ethernet  HWaddr 00:1e:68:de:c5:55  
          inet addr:192.168.123.179  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fede:c555/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2901796 (2.9 MB)  TX bytes:557396 (557.3 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:391383 (391.3 KB)  TX bytes:391383 (391.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:3d:43:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-3D-43-13-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by funkyali on 2009-05-29
lsmod |grep ath produces
> ath_pci                99224  0 
wlan                  210288  1 ath_pci
ath_hal               198864  1 ath_pci
ath5k                 107008  0 
mac80211              217208  1 ath5k
led_class              12036  2 ath5k,acer_wmi
cfg80211               38032  2 ath5k,mac80211


---

### Post by nothingspecial on 2009-05-29
Put ath5k underneath what's already there

and comment ath_pci (put a # infront of it)

---

### Post by kingnerd on 2009-05-30
Also, to the original poster, you can use BrowserShots to check your sites in each browser rather than actually using IE...  Might not help to test more advanced functionality, but for basic layout purposes, it does well.

---

### Post by sudharshaw on 2011-01-26
I have an Acer aspire 532h netbook and I have installed ubuntu 10.08 netbook edition. I am having a problem with my wireless card as well. It is very slow and I need to disconnect and connect again time to time to use it. I have the same thing working perfectly on my windows 7 partition. 

However since I love to use the netbook edition of ubuntu I want to fix this problem. Has any one else resolve this issue?

---

