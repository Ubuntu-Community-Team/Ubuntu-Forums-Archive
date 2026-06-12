---
title: "Internet problems throug wireless"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by mobdrup on 2006-10-09
Hi

I use Ubuntu 6.06 an a HP DV 1000 with a Intel Pro wireles 3945 ABG card. I am able to use internet through network cable, but I can't get it to work with the wireless. I think it is something regarding the WAP/WEP key. It seems that ubuntu is only able to use WEP - I can't see any possibilities to use WAP. I have changed my router to use both WAP and WEP, but it seems to have no effekt. To me it seems the wireless connects to the router - even I can see in the router, that the laptop is connected, but still I can't load any internet pages.

This is what a iwconfig gives me:

eth1      IEEE 802.11g  ESSID:"obdrup"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:20:02:B6:18
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-22 dBm  Noise level=-23 dBm
          Rx invalid nwid:0  Rx invalid crypt:5  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:465   Missed beacon:0


Any suggestions to what I can do?

Morten

---

### Post by wirelessmonkey on 2006-10-09
In order to use WPA encrypted networks, you'll need to install a wpa supplicant.  You can find wpa_supplicant and xsupplicant via Synaptic.  You'll have to configure the clients, you can search the ubuntuforums or visit the project pages of either application to get information on how to do this.


wpa_supplicant [http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)
xsupplicant  [http://open1x.sourceforge.net/](http://open1x.sourceforge.net/)


Best of Luck

---

### Post by mobdrup on 2006-10-09
Thx for the answer - it seems wpa_supplicant was already installed. 

I do not understand why WPA is not already installed in a system that claims itselfes to be the most secure.

Next time I get a couple of hours of sparetime, I will try to get this to work.

Morten

---

