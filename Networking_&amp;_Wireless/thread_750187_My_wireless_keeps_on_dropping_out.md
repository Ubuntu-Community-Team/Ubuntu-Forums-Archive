---
title: "My wireless keeps on dropping out"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Deanodriver on 2008-04-09
Hey all,

I've just purchased a new laptop (Compaq C731TU), and because Windows Vista is a slug (even with 2.5GB of RAM), I decided to put Ubuntu on it.

However, being new to both wireless and laptops (last laptop was a 486 one), I've had a couple of issues with the wireless on this laptop.

After setting it up (installing madwifi-ng using the EeePC entry in the Wiki because it uses an Atheros chipset (Ubuntu detects my wireless card as an AR5006EG, but Windows Vista detects it as a 5007)), it worked fine for a while, and then it wouldn't recognise any networks, then wouldn't recognise the drivers at all.

Then the next day it started working fine, and suddenly dropped out again.

I've tried installing ndiswrapper (and don't know if it's helped, because I don't know if I activated it), but I have noticed a Linux error message saying that ndiswrapper isn't loading the driver.

lsmod shows these wifi-related entries:
```
wlan_scan_sta          15104  1 
ath_rate_sample        15232  1 
ath_pci               114728  0 
wlan                  211248  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280544  3 ath_rate_sample,ath_pci
ndiswrapper           185240  0
```

iwconfig shows this:

```
dean@medusa:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and whenever I type in iwlist ath0 scan, it comes up with:

```
ath0      No scan results
```

I've added ath_pci to /etc/modules (ndiswrapper is commented out), and the first time this happened, typing in sudo modprobe ath_pci helped get it working again.

Sorry if I'm not being very helpful with the information I'm providing (if you need anymore, please ask), and I'm debating reinstalling Ubuntu afresh (done so much stuffing around trying to get things working it might be easier to start with a clean install). Would Hardy have the madwifi drivers installed? Might be coerced into installing Hardy if I have a higher chance of getting it working :)

Should I just reinstall from a clean install and use ndiswrapper from the start? On that topic, is ndiswrapper catered to a certain Windows version (ie: will it run drivers designed for Windows Vista, or XP drivers only)?

Not too worried about getting the wireless button on this laptop working, but hey, it would be nice. :)

Used to use Ubuntu on my desktop for about two years, and then went back to Windows for a change about a year ago. I'm just getting back into Ubuntu now. Everytime I do get back into Ubuntu one little issue I used to have (couldn't access the shared printer originally, can now) is fixed with a new release.

Thanks a heap in advance. :)

EDIT: The Hardware Manager in Ubuntu detects my card as an AR5006EG, and a Restricted Drivers thing comes up with it when I first install Ubuntu (for Atheros Hardware Access Layer, currently in use).

---

### Post by dstew on 2008-04-09
You should install the restricted driver if it is available. Sometimes, if you disable roaming (uncheck the box in the Network --> Properties window for the wireless interface) it works better. And I hear that 8.04 will work better with wireless.

---

### Post by Deanodriver on 2008-04-09
> **dstew said:**
> You should install the restricted driver if it is available. Sometimes, if you disable roaming (uncheck the box in the Network --> Properties window for the wireless interface) it works better. And I hear that 8.04 will work better with wireless.

Restricted driver? I tried installing the madwifi stuff in Restricted, and I don't recall it working. Unless you mean something else?

I tried unchecking the box, but it didn't work. I might install 8.04 in the hope wireless support is improved.

Actually, believe it or not, the wireless is now working again, but if it's been up and down the last few days, there's something wrong.

---

### Post by dstew on 2008-04-10
> Restricted driver? I tried installing the madwifi stuff in Restricted, and I don't recall it working. Unless you mean something else?If you look in System --> Administration --> Restricted Drivers Manager, do you find a driver for your card?

---

### Post by Deanodriver on 2008-04-10
> **dstew said:**
> If you look in System --> Administration --> Restricted Drivers Manager, do you find a driver for your card?

It says "Atheros Hardware Access Layer", with Enabled and In Use beside it.

However, my wireless isn't working again, although it was working when I got home about three hours ago. Still detects the card, but it doesn't detect any networks. I bet tomorrow it'll work just fine.

I'm half tempted to put the Vista image back on just to see whether the problem lies with Ubuntu or with this laptop.

---

### Post by dstew on 2008-04-10
How is your wireless router set up? What is the SSID, and what kind of encryption have you enabled?

---

### Post by Deanodriver on 2008-04-10
> **dstew said:**
> How is your wireless router set up? What is the SSID, and what kind of encryption have you enabled?

I must admit I'm not good with wireless, but the SSID is linksys (being a WAG54G, I cbf changing it), and I have WPA (pre-shared key, generally works with WPA personal in Ubuntu).

However, when my wireless goes down, it won't detect any networks (which includes the other wireless network in another house I can usually see).

---

### Post by dstew on 2008-04-10
> However, when my wireless goes down, it won't detect any networksApparently the current driver for your card does not support scanning. You can still set the card up though:```
sudo iwconfig ath0 essid linksys
sudo iwconfig ath0 key *<your key goes here>*
```

---

### Post by MZ21 on 2008-04-10
hey Deanodriver, I got the same laptop as yours and also got the same freaking problem 

when I first installed kubuntu and using the ndiswrapper to configure the bloody wifi to work, then it worked for a short period of time after a huge struggling, then dead

then i decided to install  a fresh ubuntu and also using ndiswrapper, but got no luck by the time after i installed them, so I turned off the laptop, and supprised!!! the day after, i turned it on, it worked and only for a short period of time, but seems like longer than before, long enough for me do some updates

ubuntu recognizes the card, but as you said, can not delect any networks, the iwlist scan shows  up "no results" to the screen which brings a hot temper to me!

what im thinking now is the wifi may be off, we need to turn it on, the wifi button always gives the bloody red colour. damn!

---

### Post by Deanodriver on 2008-04-11
> **dstew said:**
> Apparently the current driver for your card does not support scanning. You can still set the card up though:```
sudo iwconfig ath0 essid linksys
sudo iwconfig ath0 key *<your key goes here>*
```

I tried that with the GUI stuff in System-Administration-Networking, to no avail. :(

> **MZ21 said:**
> hey Deanodriver, I got the same laptop as yours and also got the same freaking problem 

when I first installed kubuntu and using the ndiswrapper to configure the bloody wifi to work, then it worked for a short period of time after a huge struggling, then dead

then i decided to install  a fresh ubuntu and also using ndiswrapper, but got no luck by the time after i installed them, so I turned off the laptop, and supprised!!! the day after, i turned it on, it worked and only for a short period of time, but seems like longer than before, long enough for me do some updates

ubuntu recognizes the card, but as you said, can not delect any networks, the iwlist scan shows  up "no results" to the screen which brings a hot temper to me!

what im thinking now is the wifi may be off, we need to turn it on, the wifi button always gives the bloody red colour. damn!

Ah, so it's not the WiFi in my laptop being on the fritz? Good to hear. :)

So it's the same with ndiswrapper? Damn. I was hoping that wasn't the case, means it might be the laptop rather than the drivers.

I don't think the button is overly important, after all, it might just be controlled by the stock standard software in Vista.

I may reinstall Vista if I can't get the WiFi working stably, though. I'd rather not, but I may have no choice.

Anyone else have any suggestions? Would dist-upgrading (or fresh installing) Hardy fix my problems?

---

### Post by dstew on 2008-04-11
> Would dist-upgrading (or fresh installing) Hardy fix my problems?Yes, it might work better.

---

### Post by Deanodriver on 2008-04-11
I'll give it a try then.

Long story short, I dist-upgraded to Hardy and broke something (wouldn't even show my GNOME desktop), so I'm downloading the ISO for Hardy beta (on my parents' Windows machine) and starting from scratch :p

If this doesn't work, I'll be forced to go back to Windows Vista (XP would work better, but I only have a licence for Vista).

Hopefully it works in Hardy :)

---

### Post by Deanodriver on 2008-04-11
> **Deanodriver said:**
> I'll give it a try then.

Long story short, I dist-upgraded to Hardy and broke something (wouldn't even show my GNOME desktop), so I'm downloading the ISO for Hardy beta (on my parents' Windows machine) and starting from scratch :p

If this doesn't work, I'll be forced to go back to Windows Vista (XP would work better, but I only have a licence for Vista).

Hopefully it works in Hardy :)

Update.

Now in Hardy, and it detects it as AR242x, with drivers not installed.

Shall I try and use madwifi again or use ndiswrapper?

---

### Post by dstew on 2008-04-11
> Now in Hardy, and it detects it as AR242x, with drivers not installed.I don't know much about Hardy, but does it tell you there are no drivers, or that you need to install a driver? Is there a Restricted Drivers Manager in System --> Administration you can check? Anyway, madwifi might work. If all that fails its back to ndiswrapper.

---

### Post by Deanodriver on 2008-04-11
There is a restricted drivers thing in Ubuntu (with a different name), which shows the Atheros HAL (like in Gutsy) and 'Support for Atheros 802.11 wireless LAN cards'

I'll try and see if I can find madwifi in the Ubuntu repositories this time :)

---

### Post by Deanodriver on 2008-04-12
I've been reading about MadWifi, and I've noted this in the 0.9.4 release notes:

```
Known issues ¶

    * No AR5007 support in this release; experimental support is available for i386 (32bit) in #1679
```

[http://madwifi.org/wiki/Releases/0.9.4](http://madwifi.org/wiki/Releases/0.9.4)

This ticket is below:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Even though there are ways around it (and that's what I used for the last install, it seems), I'm going to give up and use ndiswrapper for the time being. Maybe 0.9.5 or later will have full AR5007 support included :)

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489)

Looks like the EeePC uses the same chipset.

EDIT: I can't get ndiswrapper running. I could fix it, but meh, I can't be bothered. I think I'll go back to Windows until the wifi support is fixed and proven to be stable (I might not have a wired network to fall back on in the next house, moving in a week). Can always put Ubuntu back on if madwifi for the AR5007 is stable in Hardy final, or even wait until Intrepid :)

---

### Post by MZ21 on 2008-04-16
I've just got the wifi working for 5 days by luck (*_*), actually since the day I posted my problem, now it stuffs up, dont really get what's going on. I tested the wired network with no problem. 
recall the problem: wifi chipset is recognized as AR5006EG, ndiswrapper -l shows driver installed, hardware presents. iwlist scan gives nothing (no results)
any help plz!!!

---

### Post by MZ21 on 2008-04-16
hey Deanodriver! have a look at this thread
[http://ubuntuforums.org/printthread.php?t=512828&pp=75](http://ubuntuforums.org/printthread.php?t=512828&pp=75)

and find where it says: 
-----------------------------------
Q: Linux seems to see my device now, but it can't see any networks. What can I do now?
A: This frequently happens on built-in devices. There's usually either

    * A switch on your computer somewhere that toggles whether the wireless radio is on or off (BEWARE! Some of these are very unintuitive. The setting that may seem like "on" may be "on" and vice-versa.)
    * A keyboard combination that enables/disables the wireless connection (usually Fn+F2).
    * A setting in the BIOS that needs to be changed. This can be frustrating to track down. The BIOS is the program that loads before your OS. When your computer first boots, there's a key you can press to go into the system setup; look for a wireless setting in there that you can enable.
-----------------------------------

remember when i talked about the bloody LED wifi button, it's not standing there for nothing. you turn the wifi on/off by using that button despite it does not turn to blue (always red), but it still functions. I did several times just to make sure that it's not a dream  *_*

using iwlist scan to test whether its on or off!

---

