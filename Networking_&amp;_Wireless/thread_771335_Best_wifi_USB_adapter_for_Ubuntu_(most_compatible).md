---
title: "Best wifi USB adapter for Ubuntu? (most compatible)"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by scrappitydoo on 2008-04-27
I don't need the fastest, latest or greatest, just a decent little plug in USB wifi adapter to get internet on my Ubuntu machine. (a little Koolu box [www.koolu.com](www.koolu.com)). Is there a list of these that have been tested and are least likely to cause a newbie installation headaches?

---

### Post by johnn1949 on 2008-04-27
I haven't tried usb but my d-link wireless card(wna-2330) has worked out of box on every version since dapper drake.

---

### Post by scrappitydoo on 2008-05-08
Thanks johnn1949! But I need a USB. The tiny little Koolu box has no room for a card...

---

### Post by martin15s on 2008-05-14
try Edimax - from the box in 8.04 :)

---

### Post by fmartinez on 2008-05-14
> **scrappitydoo said:**
> I don't need the fastest, latest or greatest, just a decent little plug in USB wifi adapter to get internet on my Ubuntu machine. (a little Koolu box [www.koolu.com](www.koolu.com)). Is there a list of these that have been tested and are least likely to cause a newbie installation headaches?

I've used a belkin usb wireless adapter for wifi. All I did was plug it in and it picked it up right away. I didn't have to configure a driver for it or anything. I worked great! I tested it both on Ubuntu and Fedora with no problems.

---

### Post by JEI305u on 2010-01-18
I also checked belkin and read favorable reviews about it but its expensive. First thing you have to consider is the location of your connection. 
 
I recommend you buy the WIFI-N instead of WIFI-G.

---

### Post by Patrick Beumer on 2010-01-28
I have belkin N adapter f5d8051 v3 DOES NOT WORK with (k)ubuntu, looked up a lot on the web due of chipset not compatible. I am a linux rookie and do not want to compile a new core etc... Myself want to buy a new wifi USB adapter and also have no id what to buy 
 
greetz

---

### Post by jml on 2010-01-28
I am currently using a Belkin 802.11g USB adapter.Model number F5D7050.  It worked perfectly with my System 76 Starling Netbook and Ubuntu NBR 9.04.  Have not yet tested it with 9.10, but it should work.  The advantage of getting a slightly older wireless adapter is that the support in Linux is usually better.  And, they are usually cheaper.  Since 802.11n is still not been officially ratified yet, (getting close though,) there are slightly different implementations of the protocol.  I have read threads on this and other forums where the hardware was recognized, but performance was poor.

Joe

---

### Post by dDaYb on 2010-06-14
still what is the best compatible 80211n usb adapter? I want to use it with hostapd in AP mode. thank you

---

### Post by Arlukin on 2011-01-10
> **dDaYb said:**
> still what is the best compatible 80211n usb adapter? I want to use it with hostapd in AP mode. thank you

Anybody found anything? 

After a weekend of googling I'm starting to wonder if it exists an USB wifi dongle that supports all wifi modes (AP, Mesh, monitor, etc.). Atleast I like something that supports these AP and monitor. Looks like everybody has some problem, or that the dongle just supports AP or monitor, or the posts are from like 2007 and kernel/drivers are outdated and the devices are not sold anymore.

:confused::confused::confused::confused::confused: makes me crazy :P

---

### Post by Sergius14 on 2011-01-10
I use a USB WiFi adapter for work (almost all os's, on Linux just rulz) which is a Realetk RTL8187 chipset based. It is extremelly compatible, supports packet injection :P (WEP cracking, WPA/WPA2 attacks, etc.) It is B/G, not N.

Pros: 
Extremelly compatible.
Used for auditing/hacking.
500mw (doubles a regular router)
5db antenna (you can reach far more wifis than any other regular usb wifi.

Cons:
B/G only.
Have an external antenna (but not that big).
In general, bigger than standards usb adapters.

I think that is most knwon as Alfa brand, but a I have another brand which it is exactly the same thing (G-Sky).

Repeat: It is etremelly compatible: In 10.04/10.10 you can literally plug and play out of the box.


Regards,

---

### Post by Arlukin on 2011-01-11
But do you get it to work with AP/Master mode? What I have read, the Alfa usb dongle doesn't support that. Atleast the AWUS036H that I have read most about.

---

### Post by Sergius14 on 2011-01-11
I can try it for you if you help me o tell me how.

I can confirm you that out of the box is not working:

```

$ iwconfig

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:XX  
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:XX 
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

~$ sudo iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
~$ sudo iwconfig wlan1 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.

```


Look that also fails for an Atheros onboard card too.


Maybe I need another driver or compile something.

---

### Post by Sergius14 on 2011-01-11
Seams that the Realtek is a mac80211 based.

Following this: mac80211 based driver

I get this:

Supported interface modes:
		 * managed
		 * monitor
	Supported commands:
		 * new_interface


Also according to this [http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers) seams that has monitor support.

---

### Post by Arlukin on 2011-01-12
What I have read you should most of the cases use hostapd instead of iwconfig. But also from what I have read the RTL8187 doesn't support AP/master mode, so hostapd doesn't work on it. 

But last night I found some new information, because the RTL8187 supports packet injection it's possible to use airbase-ng to simulate a software access point. I haven't studied any documentation yet, so I don't know the commands and configurations needed to be done. But I'm confident enough that it will work, so I did put an order last night on this usb dongle
[http://www.dealextreme.com/details.dx/sku.35688](http://www.dealextreme.com/details.dx/sku.35688)

---

### Post by randumnumber on 2011-01-27
List of compatible wifi adapters 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I used a linksys WUSB54G V4 for a while that just crapped out, but it worked in monitor mode, permisc, AP, it also has packet injection capability. And there is an antenna hack out there somewhere for it to get better range.

---

### Post by postino2 on 2011-03-29
@ARLUKIN

You say you spent a weekend trying to find a USB WIFI Modem that works with UBUNTU.  Have you perused the AMAZON listing (item B002VX0GJY) that some fifteen customers claim is PLUG-n-PLAY with UBUNTU?  They give it high marks and claim that it is only necessary to plug it in to get it to work.  No drivers, no compiling, no nada.  And it is relatively inexpensive at US $9 - $12.  

NOTE:  13 of the 15 reviewers posted their reviews within the most recent six months, so this is not "info from 2007" as you referenced.  Also, there is some info on the site of variable results, but most reviewers are UNCOMMONLY positive.

the item "name" is:

802.11g USB WiFi Wireless Lan Adapter w/5dBi Antenna  by Taiwan

the AMAZON listing number is B002VX0GJY


As we UBUNTU users know, WIFI is perhaps one of the more difficult issues with LINUX.  So many things with LINUX "just work" as soon as they are plugged in, but often WIFI adapters are not so simple.

ByTheWay - I did not understand your comments about "(AP, Mesh, monitor, etc.)"  So I apologize if you are not looking simply for a USB WIFI adapter that works "PLUG-n-PLAY with UBUNTU.

Also, I DO NOT have this particular USB WIFI modem nor do I intend to purchase it.   The only WIFI I use with LINUX is with internal WIFI cards inside four different portable computers.  And they all work famously well.  It is just that I came across this AMAZON item trying to discover a workable USB WIFI modem for a Cr-48 CHROME OS notebook whose internal WIFI modem apparently stopped working.  And - as a result of my searching - I also saw your post explaining your extreme frustration.

PS:  I noticed that you are writing from Stockholm.    Warm greetings from Chicago !



> **Arlukin said:**
> Anybody found anything? 

After a weekend of googling I'm starting to wonder if it exists an USB wifi dongle that supports all wifi modes (AP, Mesh, monitor, etc.). Atleast I like something that supports these AP and monitor. Looks like everybody has some problem, or that the dongle just supports AP or monitor, or the posts are from like 2007 and kernel/drivers are outdated and the devices are not sold anymore.

:confused::confused::confused::confused::confused: makes me crazy :P

---

### Post by Arlukin on 2011-04-03
Thanks for your answer and no, I haven't looked in to that particular card. But I will have a look, and do some readings.

> **postino2 said:**
> @ARLUKIN
ByTheWay - I did not understand your comments about "(AP, Mesh, monitor, etc.)"  So I apologize if you are not looking simply for a USB WIFI adapter that works "PLUG-n-PLAY with UBUNTU.
What I mainly was looking for is a card that support AP (Access Point)/master mode. So that I can use a computer as a wifi-access-point. But it looks like it's currently not possible to do in all the ways I like it to work, or rather I didn't like to spend more time to find out how.

But the card I finally ended up with was a Alfa AWUS036H with a RTL8187L chip, which is popular in the "Backtrack-scene". And I succeeded to set up an access point with airbase-ng, but unfortunately it didn't work to connect to it from my macbook pro. Which was the biggest reason I had to setup the access point.

---

### Post by cotcot on 2011-04-10
Ubuntu 10.10 on an ACER 1810 TZ with TP-LINK TL-WN727N works very good out the box. Just plugin the USB wifi.

---

### Post by peterhe on 2011-10-09
Hell all, you can find Wifly-City 300WG 36dBi Radar Directional Antenna USB Wifi Wireless Adapter only $20.99 + free shipping, highly recommend.order it at this site: [http://www.mallextreme.com/wifly-city-300wg-36dbi-radar-directional-antenna-usb-wifi-wireless-adapter_p27255.html](http://www.mallextreme.com/wifly-city-300wg-36dbi-radar-directional-antenna-usb-wifi-wireless-adapter_p27255.html)

---

### Post by Arlukin on 2011-10-09
> **peterhe said:**
> Hell all, you can find Wifly-City 300WG 36dBi Radar Directional Antenna USB Wifi Wireless Adapter only $20.99 + free shipping, highly recommend.order it at this site: [http://www.mallextreme.com/wifly-city-300wg-36dbi-radar-directional-antenna-usb-wifi-wireless-adapter_p27255.html](http://www.mallextreme.com/wifly-city-300wg-36dbi-radar-directional-antenna-usb-wifi-wireless-adapter_p27255.html)

Thanks for the tip. Have you succeeded to get it to work in master/AP mode? 

I tried with airbase-ng and hostap. But it looked like none of them really worked, at least I couldn't connect to the AP with my macbook. This was a couple of month ago (9?) so maybe drivers and stuff are updated.

---

