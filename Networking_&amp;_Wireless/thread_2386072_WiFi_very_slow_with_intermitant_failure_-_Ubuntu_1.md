---
title: "WiFi very slow with intermitant failure - Ubuntu 16.04"
date: 2018-02-28
forum: Networking &amp; Wireless
---

### Post by abc-xyz2 on 2018-02-28
I had problems with the WiFi dropping on my desktop machine, which is located in a different room from the router hence the WiFi. I tried various things such as installing Broadcom drivers, installing Wicd and a USB WiFi dongle I haven't gotten anywhere - if anything the WiFi is slower than it was before I started changing things. I've left the drivers (they seem to be the correct ones according to the sticky thread) but removed the Wicd packages (I think, there still seems to be a wicd process running) and don't have the USB dongle plugged in.

Results from the WiFi script are here: [http://paste.ubuntu.com/p/ZGqrDVvMJb/](http://paste.ubuntu.com/p/ZGqrDVvMJb/)

I'd appreciate any help.

---

### Post by abc-xyz2 on 2018-03-01
I've found two additional wicd packages (wicd-daemon and python-wicd) and uninstalled those so I am back to using NetworkManager. It doesn't seem to have made any difference to the speed and dropping connection though. I've updated the WiFi script results.

[http://paste.ubuntu.com/p/JrrhDWRsb3/](http://paste.ubuntu.com/p/JrrhDWRsb3/)

---

### Post by chili555 on 2018-03-01
> don't have the USB dongle plugged in.But the possibly conflicting drivers are still loaded. From your paste:> [COLOR="#FF0000"]rt2800usb  [/COLOR]            28672  0
rt2x00usb              20480  1 rt2800usb
rt2800lib             110592  1 rt2800usb
rt2x00lib              53248  3 rt2800lib,rt2800usb,rt2x00usb
b43                   417792  0
bcma                   53248  1 b43
mac80211              782336  4 rt2800lib,b43,rt2x00lib,rt2x00usb
cfg80211              614400  3 b43,rt2x00lib,mac80211
mxm_wmi                16384  0
ssb                    57344  1 b43
wmi                    24576  1 mxm_wmiPlease unload them:```
sudo modprobe -r rt2800usb
```Check:```
lsmod | grep rt2
```Most concerning is that you have two SSIDs (routers) with the same name:```
SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
home  <MAC 'home' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
home  <MAC 'home' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2      yes     * 

```In your logs, we see the wireless roaming, and thereby disconnecting and re-connecting, among the two looking for a better connection. Reminds me of my old girlfriend!> [138218.036519] wlan0: authenticate with <MAC 'home' [AC2]>
[138218.052188] wlan0: send auth to <MAC 'home' [AC2]> (try 1/3)
[138218.054761] wlan0: authenticated
[138218.055995] wlan0: associate with <MAC 'home' [[COLOR="#FF0000"]AC2[/COLOR]]> (try 1/3)
[138218.260009] wlan0: associate with <MAC 'home' [AC2]> (try 2/3)
[138218.463987] wlan0: associate with <MAC 'home' [AC2]> (try 3/3)
[138218.667988] wlan0: association with <MAC 'home' [AC2]> timed out
[138228.052633] wlan0: authenticate with <MAC 'home' [[COLOR="#FF0000"]AC1[/COLOR]]>
[138228.068436] wlan0: send auth to <MAC 'home' [AC1]> (try 1/3)
[138228.068470] wlan0: aborting authentication with <MAC 'home' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[138229.472844] wlan0: authenticate with <MAC 'home' [AC1]>
[138229.504456] wlan0: send auth to <MAC 'home' [AC1]> (try 1/3)
[138229.507072] wlan0: authenticated

If you have administrative priveleges over these routers, I suggest that you rename them to home1 and home2 or some such. Connect to home1 and I'm confident that all your disconnects will be over.

If you are unable to rename them, then bind Network Manager to the stronger of the two like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Please let us hear back after making these changes. Any improvement?

---

### Post by abc-xyz2 on 2018-03-02
Thanks for that chili555.

I removed the rt2800 driver which was fine.

The routers is weird though. I only have a single router with SSID home. It seems unlikely that any of the neighbours have the same SSID (and password)! I tried renaming the SSID, a few times. The first time the wireless script only showed one SSID (but of course I didn't screenshot that) but the machine didn't connect to the WiFi.
 The following times I see two SSIDs with the same name. For example:

SSID   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  *
home4  <MAC 'home4' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2      no
home4  <MAC 'home4' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2      yes     *


My router says it is using channel 11 so I don't know why Ubuntu would report home4 on channel 1. I also restarted network manager after renaming the SSID as part of the test.

There are two Windows laptops and a Mac laptop all connecting without any problems so it doesn't seem to be an issue with the router.

---

### Post by chili555 on 2018-03-02
>  I only have a single router with SSID home.Does it have a guest network? Can you disable or rename it?


[IMG]https://s19.postimg.org/mmqe7o1dv/Guest_network.png[/IMG]

---

### Post by abc-xyz2 on 2018-03-03
Nope it doesn't have guest network functionality. It does have separate sections for 2.4GHz and 5GHz configuration. I've tried with these synchronised (there's a tickbox for this) so they use the same SSID and also using separate SSIDs but Ubuntu is still seeing two SSIDs in both scenarios with the SSID of the 2.4GHz network.

---

### Post by chili555 on 2018-03-03
> **abc-xyz2 said:**
> Nope it doesn't have guest network functionality. It does have separate sections for 2.4GHz and 5GHz configuration. I've tried with these synchronised (there's a tickbox for this) so they use the same SSID and also using separate SSIDs but Ubuntu is still seeing two SSIDs in both scenarios with the SSID of the 2.4GHz network.Weird.

Can you try renaming the 2.4 gHz segment home2.4 and the 5 gHz home5? 

> SSID BSSID MODE CHAN FREQ RATE SIGNAL BARS SECURITY ACTIVE *
home4 <MAC 'home4' [AN1]> Infra 11 2462 MHz 54 Mbit/s 90 &#9602;&#9604;&#9606;&#9608; WPA2 no
home4 <MAC 'home4' [AN2]> Infra 1 2412 MHz 54 Mbit/s 75 &#9602;&#9604;&#9606;_ WPA2 yes *

This looks like a 2.4 gHz segment and another 2.4 gHz segment. Again, weird.

---

### Post by abc-xyz2 on 2018-03-04
I've tried that too. Immediately after restarting things (Router and then Network Manager) it sees a single SSID like:

SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  *
home  <MAC 'home24' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  95      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;â&#8211;&#710;  WPA2      no

But then within about a minute it again it picks up the second SSID:


SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  *
home24  <MAC 'home24' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  99      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;â&#8211;&#710;  WPA2      no
home24  <MAC 'home24' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  67      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;_  WPA2      yes     *

This time the channel is the same for both, I've tested it a few times and occasionally it's a different channel (channel 1 from what I remember).

---

### Post by abc-xyz2 on 2018-03-04
Really weird - the second SSID now seems to be dropping in and out. 

user@box:~$ nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
home24  <MAC_ADDRESS2>  Infra  11    2462 MHz  54 Mbit/s  80      â–‚â–„â–†_  WPA2      yes     * 
user@box:~$ 
user@box:~$ 
user@box:~$ 
user@box:~$ nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
home24  <MAC_ADDRESS1>  Infra  11    2462 MHz  54 Mbit/s  79      â–‚â–„â–†_  WPA2      no        
home24  <MAC_ADDRESS2>  Infra  11    2462 MHz  54 Mbit/s  77      â–‚â–„â–†_  WPA2      yes     * 


<MAC_ADDRESS1> is the actual address of the router (according to the router web page and the sticker on the bottom on the router).

---

### Post by chili555 on 2018-03-04
Very, very weird! Are the MAC addresses different? 

You might try binding one in Network Manager like this: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Frankly, I suspect a defective router.

---

### Post by abc-xyz2 on 2018-03-06
Yep the MAC addresses are different. One matches what I'd expect from the router (it's printed on the router and is what is shown on the router's configuration webpage) and I don't know where the other is coming from.

I tried binding to one specific MAC address but the speed is still very slow. It didn't drop out but I didn't leave it for very long so I'm not sure it's fixed.

I'm going to give up on this for the moment. I've a new WiFi card due to arrive at the end of the week and I'm swapping internet provider in a month so that will mean a new WiFi router. I'll wait till those arrive and test again with them and see what happens. For the moment I'll turn off the internal WiFi card and use the USB stick WiFi as that seems to be generally better than the internal card. I'll update this thread once I've done some tests with the new card.

Thanks for the help chili555

---

### Post by abc-xyz2 on 2018-03-14
Update for anyone interested:
So I went back to using the USB WiFi dongle and, once I turned of the internal card , the WiFi seems to work fine. If I left the card turned on it kept trying to reconnect to the WiFi (which the USB one doesn't do). So I've come to the conclusion that the issue is related to the internal WiFi card itself, possibly a hardware issue.

The new internal card has arrived, along with the new router, so I'll now I have to get those setup and working.

---

### Post by abc-xyz2 on 2018-03-15
The new wireless card won't work at all for me. Since it's a new card/new problem I'm going to post in a new thread.

---

