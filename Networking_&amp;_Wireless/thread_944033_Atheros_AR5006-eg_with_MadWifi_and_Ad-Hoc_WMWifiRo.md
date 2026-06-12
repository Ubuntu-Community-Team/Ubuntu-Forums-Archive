---
title: "Atheros AR5006-eg with MadWifi and Ad-Hoc WMWifiRouter"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by PMahoney on 2008-10-10
Hello All-

I've recently installed Ubuntu 8.04 Hardy on an ASUS A8 laptop.  My wireless card is as the title suggests...an Atheros ar5006-eg.  The problem I've been having is nothing new, but with hours of searching the forums, I've been unable to find a working solution.

My sole source of internet is through my Sprint Mogul (PPC-6800) phone, either via an ad-hoc WMWifiRouter network (v0.89) or usb tethering (can't install without an internet connection).  However, without being able to access the internet in Ubuntu, I followed the instructions provided in the following link in order to establish a wireless connection...with what I believe to be a success (I know it's for AR5007, but I've read it should work for the 06 as well). 

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

I can now see my card as well as 'all' available networks, but now have two problems.  I cannot access the ad-hoc WMWifiRouter network and most importantly...there appears to be a substantial reduction in network detection range (even when I boot in Vista).  The latter problem, for example, I can no longer pick up what would normally be 2-3 bar signals at libraries, cafes, etc...even when I boot in Vista.  I have to be sitting within 5ft of the router.  This was NOT a problem prior to installing Ubuntu and have no idea why it would be an issue in both OS'.  Is there a way to manually adjust detection ranges?  Any ideas on possible problems?

For connecting to the ad-hoc network, I've tried the following with NM stopped/started and ath0 up and down.
```

sudo iwconfig ath0 mode ad-hoc
```

...all result in the following...

```
Error for wireless request "Set Mode" (8BO6)
  SET failed on device ath0 ; Operation not permitted.
```

...so tried the following...

```

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode adhoc
```

...and successfully changed ath0 Mode:managed to Mode:Ad-Hoc from the iwconfig output.  However, I can't seem to manually connect (including using code the MAC and ESSID of the ad-hoc network) or by through using NM.

lspci still incorrectly identifies my wireless card as AR242x instead of the correct AR5006-eg...might this still be part of the problem?

Thank you so much in advance.  Once I'm able to work past this networking problem, I can finally fully commit to Ubuntu!

Peter

---

### Post by PMahoney on 2008-10-11
Bump...anybody??

---

### Post by Lord C on 2008-10-24
Similar problem here. I want to tether my cellphone connection.
I've had no luck with this at all. I've tried everything.

Including;
```
        wlanconfig ath0 destroy
        wlanconfig ath create wlandev wifi0 wlanmode adhoc
        iwconfig ath0 essid eee
        iwconfig ath0 rate auto 
        iwconfig ath0 channel 1
        ifconfig aht0 169.254.10.2 up
```
And;
```
wlanconfig ath0 destroy
wlanconfig ath0 create nounit wlandev wifi0 wlanmode adhoc
iwconfig ath0 mode Ad-Hoc essid eee
iwconfig ath0 enc open $KEY
ifconfig ath0 -promisc 196.254.161.2 netmask 255.255.0.0
```
The commands seem to work fine. I always check in ifconfig and iwconfig, but whatever happens, the network is never live.
I cannot connect to it from any other device, and the Network Manager icon still displays the not-connected icon.

---

### Post by robert.cooper on 2008-11-05
did you ever find a resolution? my wireless card ceased to work on upgrade from 8.04 to 8.10, so i'm trying the kubuntu version; i really don't want to fresh install but i know how to preserve many settings, and it's sort of disenheartening to revert from a major upgrade package.. oh well. is there  a way i can get certain programs only from the intrepid repositories?
i was wireless with an ar5007eg. no more :(

---

