---
title: "Wirless rt2500pci very slow"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by XiMeNSiOnS on 2008-10-29
Hi, I just installed Ubuntu 8.04 and ran my wireless and noticed its extremely slow. On windows I get 90% signal strength, on Ubuntu I get 48% signal strength. That automatically means something is wrong. I have the rt2500pci drivers on because I did "lsmod" and saw them there, but is there something else I need to do to set them up properly. I need this problem fixed right away for school and business purposes.

---

### Post by lH)4~mK0e on 2008-10-31
Please do

```
 iwconfig 
```

and post the results.

---

### Post by XiMeNSiOnS on 2008-10-31
```
wlan0     IEEE 802.11bg  ESSID:"Wireless"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:00:B2:13   
          Bit Rate=54 Mb/s   Tx-Power=24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by thewolffman on 2008-11-01
My problem with this driver in 8.10 (kernel 2.6.27-7) is that the 
driver get fixed to 1 Mb instead of 54 Mbit.

wlan0     IEEE 802.11bg  ESSID:"AirWolff"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:C6:78:11:13   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=52/100  Signal level:-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


after i do 'iwconfig wlan0 rate 54M' i get this:

wlan0     IEEE 802.11bg  ESSID:"AirWolff"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:C6:78:11:13   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by ComicSubversion on 2008-11-01
I have the same problem (on 8.10 currently, but it was the same on 8.4), so any help would be greatly appreciated.

And here's my info:
wlan0     IEEE 802.11bg  ESSID:"Rings"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:03:2F:48:55:DB   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=40/100  Signal level:-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by XiMeNSiOnS on 2008-11-13
Guess no one wants to help us.

---

### Post by eldragon on 2008-11-13
> **XiMeNSiOnS said:**
> Guess no one wants to help us.

open a terminal and do 
```

$ lsmod |grep rt

```

post output here. i can help you if you got the same chipset.

---

### Post by bgenc on 2008-11-15
$ lsmod |grep rt

agpgart                42184  1 nvidia
rt2500pci              24064  0 
rt2x00pci              15104  1 rt2500pci
rt2x00lib              36224  2 rt2500pci,rt2x00pci
rfkill                 17176  2 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00pci,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
eeprom_93cx6           10240  1 rt2500pci
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc

---

### Post by doug1212 on 2008-11-16
I have just installed Hardy on my old laptop that has a card with the rt2500 chipset and i found that building and installing the latest driver daily build from serial monkey the signal seemed much more stable.

I had to blacklist rt2500pci.

I am using WPA-PSK at home.

I also built and installed the latest Rutilt wireless manager after uninstalling gnome network manager.

Although my experience with wifi is limited to this one card I do find that the wireless range is not as far as under MS XP but it functions ok.

Doug.

---

### Post by deadlydes on 2008-12-15
Hiya
Mine is doing the same. It is running but only connected at 1Mbs. If it helps it used to work ok in Gutsy but didnt work in Hardy and still doesnt work in Ibex.

rt2500pci              24064  0 
rt2x00pci              15104  1 rt2500pci
rt2x00lib              36224  2 rt2500pci,rt2x00pci
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00pci,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
eeprom_93cx6           10240  1 rt2500pci
parport_pc             39204  0 
parport                42604  3 ppdev,parport_pc,lp
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  2 drm,intel_agp

Any ideas?
Thanks
Des

---

### Post by Wally_dog on 2009-01-15
I have this same problem... I can only download at a max speed of about 15kb/s from any website/repository... there is definetly something wrong there. I tried installing SerialMonkey drivers for a guide written for Gutsy, and everything worked except when I put it "ifconfig wlan0 up" it said it couldn't find the interface lol... now I can't get any internet. I'll do a fresh install tomorrow and see if I can find another way to get it to work. And by the way I'm using 64-bit Intrepid Ibex (8.10).

---

### Post by Baldrick_NZ on 2009-01-15
> **doug1212 said:**
> I have just installed Hardy on my old laptop that has a card with the rt2500 chipset and i found that building and installing the latest driver daily build from serial monkey the signal seemed much more stable.

I had to blacklist rt2500pci.

I am using WPA-PSK at home.

I also built and installed the latest Rutilt wireless manager after uninstalling gnome network manager.

Although my experience with wifi is limited to this one card I do find that the wireless range is not as far as under MS XP but it functions ok.

Doug.

Any chance you could write a quick, simple "how to" to the above pls?

I have downloaded the serial monkey files required, but just need to know where to put them.

Cheers.

---

### Post by machina on 2009-03-02
I had same problem, seems setting 'sudo iwconfig wlan0 rate 11M
' instead of 'sudo iwconfig wlan0 rate 54M
' fixes the speed problem, at least for my setup/  (PackardBell mv35 laptop ralink rt73 wireless lan.)

---

### Post by opensourcederry on 2009-03-11
I have the same issue, slow performance on a rt2500pci card, set at 1mb with 8.10, worked fine with pre 8.10

It seems this is an issue with the rt2500 driver and Mepis Linux 8 knows about it and provides a fix.

Anyone know what the equivalent in ubuntu 8.10 is for the fix on this page below?

[http://www.mepis.org/docs/en/index.php/MEPIS_8_Upgrade_FAQ#rt2500_wireless_support](http://www.mepis.org/docs/en/index.php/MEPIS_8_Upgrade_FAQ#rt2500_wireless_support)

---

### Post by RavanH on 2009-07-12
Please check out my fix on [http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785) which involves switching to Wicd plus a small pre-connection script.

Let me know if it works or not :)

---

### Post by Dukius on 2009-11-24
Thanks wolffman!!! Your solution worked great with my problem!!

For those having the same problems (most of you for what I've seen here) If doing an iwconfig your Bit Rate is = 1Mb/s just try to do as wolffman said:

#sudo iwconfig wlan0 rate 54M

I've a Conceptronic 54g Wireless PCI and my bit rate was locked to 1Mb/s and my downloads never been further than 30kb/s, just after switching the bit rate to 54M i got the full connection bandwith!!

The only problem now is that after rebooting it goes back to 1Mb/s....

> **thewolffman said:**
> My problem with this driver in 8.10 (kernel 2.6.27-7) is that the 
driver get fixed to 1 Mb instead of 54 Mbit.

wlan0     IEEE 802.11bg  ESSID:"AirWolff"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:C6:78:11:13   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=52/100  Signal level:-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


after i do 'iwconfig wlan0 rate 54M' i get this:

wlan0     IEEE 802.11bg  ESSID:"AirWolff"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:C6:78:11:13   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by bgenc on 2009-11-24
I have a serious problem with this chipset.
In older versions of Ubuntu, I had this 1mbit rate problem.
Now the default installation in 9.10 assumes a 54mbit connection.
However, now my tx-power is reduced to 20dbi and I cannot increase
it to 27dbi (that is the value in the good old days)

My connection is somehow limited to .5 mbits now. I cannot download
more than 60kb/s. I disabled ipv6 here and there with no help at all.

Please help me because this is really driving me crazy.

---

### Post by RavanH on 2009-11-29
bgenc & Dukius, I have shared my way around the problem on [http://ubuntuforums.org/showthread.php?p=7605785#post7605785](http://ubuntuforums.org/showthread.php?p=7605785#post7605785) (involving Wicd + the "iwconfig wlan0 rate ??M" method) and I am interested to know if it works on Karmic too. So if you want to try it, please let me know the result. I might have to adjust the how-to to fit Karmic?

---

### Post by Dukius on 2009-11-29
Hi RavanH, very nice tutorial you made mate!! Wish I found it before all my troubles with this card.

I'm sorry I can't help you to test your workaround as I'm using Ubuntu 9.04 atm

Anyway, if anyone is interested I solved the booting problem going back to 1MB just adding a script on the /init.d/ folder. I know is not an ellegant solution as you said, but it works...

---

### Post by bgenc on 2010-03-07
> **bgenc said:**
> I have a serious problem with this chipset.
In older versions of Ubuntu, I had this 1mbit rate problem.
Now the default installation in 9.10 assumes a 54mbit connection.
However, now my tx-power is reduced to 20dbi and I cannot increase
it to 27dbi (that is the value in the good old days)

My connection is somehow limited to .5 mbits now. I cannot download
more than 60kb/s. I disabled ipv6 here and there with no help at all.

Please help me because this is really driving me crazy.

I still have this problem and would like to hear if any solutions exist.

---

