---
title: "WiFi disconecting"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by Mel_Blakey on 2017-08-13
Lenovo-ideapad-100-15IBY
RTL8188EE Wireless Network Adapter

Hello
I installed 16.04 on to this new laptop after wiping Win10 last year.

It has run perfectly for 11 months..... like a dream. Then, 1 month ago I noticed that it was taking quite a long time to shut down, so I searched around and came across this thread [https://ubuntuforums.org/showthread.php?t=2322159 ]("https://ubuntuforums.org/showthread.php?t=2322159") and applied
```
sudo systemctl disable cups-browsed
```
All was back to normal and my machine was shutting down quickly.
(I am telling this as background info)
-------------------------------------------------------------------------------------------------


The WiFi worked flawlessly up until about 5 days ago when it started dropping out at 5-15 minute intervals.

 I know that there are already posts about this problem. But, they are regarding new installs.
My problem has only just started after 12 months.

I have tried an earlier kernel via the start-up menu and that has not made any difference.

Does anyone have a fix? I've attached wireless info

[ATTACH]276385[/ATTACH]

---

### Post by johndough2 on 2017-08-13
Hi

Not really helpful I'm sure, but I don't understand

nameserver 127.0.1.1
searchwww   huaweimobilewifi   com
IP4.DOMAIN[1]:                         www   huaweimobilewifi    com
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000

Are you using a mobile phone for anything?  Are you creating a hotspot?

Also channel 2 is possibly being flooded, perhaps switch to 6 or 11.  My screenshot to show that channels are incline to bleed over.  So the 9 AP's on channel 1 could be a problem.
[ATTACH=CONFIG]276386[/ATTACH]

---

### Post by Mel_Blakey on 2017-08-13
> Are you using a mobile phone for anything?  Are you creating a hotspot?

No, it's a Huawei mobile Wifi. [http://www.expertreviews.co.uk/networks/wireless-routers/1401870/huawei-e5372-review ]("http://www.expertreviews.co.uk/networks/wireless-routers/1401870/huawei-e5372-review")Been using that since last Nov. Again, without issue.

I've changed it to channel 6 and whilst I was in there I noticed that the country setting was wrong. So, I've corrected that aswell.

Thanks for your help!

---

### Post by jeremy31 on 2017-08-13
Can you change the settings on the mobile wifi to disable TKIP encryption and see if there are any WMM/QOS settings.  It might be worth checking to see if there is updated software for the device as there were some errors like
```
AP has invalid WMM params (AIFSN=1 for ACI 0), will use 2
```
That make me think it could be an issue with the device

---

### Post by Mel_Blakey on 2017-08-13
> **jeremy31 said:**
> Can you change the settings on the mobile wifi to disable TKIP encryption and see if there are any WMM/QOS settings.  It might be worth checking to see if there is updated software for the device as there were some errors like
```
AP has invalid WMM params (AIFSN=1 for ACI 0), will use 2
```
That make me think it could be an issue with the device

I have set it to AES only. I don't see any reference to WMM/QOS
The software is up to date.

Before I changed the settings I did a Factory Reset. Now there is only 4 instances of the word invalid in the wireless-info.txt
```
thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx **invalid** nwid:0  Rx **invalid** crypt:0  Rx **invalid** frag:0
          Tx excessive retries:0  **Invalid** misc:0   Missed beacon:0
```
As opposed to 19 before.

The device has stayed connected connected for 1hr 20 min now and that's good enough for me. I'll give it another reboot or 2 and hopefully be marking this thread solved ;)

Thanks both of you for your help!

---

