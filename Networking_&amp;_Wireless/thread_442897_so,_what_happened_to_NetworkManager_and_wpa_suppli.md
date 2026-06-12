---
title: "so, what happened to NetworkManager and wpa_supplicant in feisty?"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by skullmunky on 2007-05-14
they worked great in edgy and are giving me all kind of grief in feisty - from the forum here, looks like i'm not the only one ;)  

does anyone know if they're just broken right now and i should stop banging my head against it 'til fixed?  

here's my situation:  hp pavilion ze2000, broadcom bcm4318.  installed ndiswrapper and broadcom firmware, all good there.   my home network is using WPA2.  in edgy, just doing sudo nm-applet got everything running fine.  now, it's a little weirder:

1. card is only active after waking up from standby.  standby is, in fact, flawless out of the box, wireless and ati drivers running great, really nice and smooth!  but the wifi is ONLY after waking up.  
this hp has a little light-up button to turn the wifi on and off; it doesn't do anything before sleeping and reawakening.  then it works perfectly.  

2. ran sudo NetworkManager --no-daemon to see debugs.
3. sudo nm-applet

i remembered from edgy, it needed to be run sudo to get access to the "default keyring", which frankly didn't make a lot of sense but worked.  now, it never asks about the default keyring anymore... 

4. try to connect. i get the password box - it recognizes my network, knows it's WPA, i enter the password, then a long hang and nothing.  incidentally, this is why i can't use Windows on my home wireless network - no windows laptops of any kind can ever connect.   so this is no worse, anyhow.  

5. back in the NetworkManager output, i see a lot of cycles of group handshakes, connections, successful key negotiations.    not sure what's useful, exactly, but here's some of it (paraphrased)

...
eth1: Device is fully supported using driver 'ndiswrapper'
...
New wireless user key requested for network 'bugcity'
Stage 2 of 5 (Device Configure) complete
New wireless user key for network 'bugcity' received
...
access point 'bugcity' is encrypted, and a key exists.  No new key needed.
SUP: sending command 'INTERFACE_ADD eth1  wext /var/run/wpa_supplicant
SUP: response was 'OK'
after that, a series of otehr commands:
AP_SCAN 1, ADD_NETWORK, and a bunch of SET_NETWORK commands:
proto WPA2
key_mgmt WPA-PSK
psk <key>
ENABLE_NETWORK 0

soon after we just get an infinite cycle of key negotiations, and finally gives up.  actually once in about 50 tries it worked immediately, which was weird too.

i just noticed  a couple things - tell if i'm on to anything

* INTERFACE_ADD eth1 wext - should that be ndiswrapper instead of wext?
* why does it always set the key management to WPA-PSK, when it should be AES?
* if i change my router to use WPA-PSK instead of WPA2, why does nm-applet still identify it as WPA2/AES?  
* if i disable security completely on my router, why does nm-applet still think it's WPA2, and System->Administration->Network doesn't do anything either?   

mysterious.  thanks for any help or pointers or suggestions ... meanwhile i'll go grab a long ethernet cable ...

--skullmunky

---

### Post by wieman01 on 2007-05-14
With regard to your questions:

a. "wext" is the right driver in your case. "ndiswrapper" is "deprecated" and thus obsolete.
b. AES is an algorithm and WPA-PSK refers to your authentication method as opposed to WPA-EAP (= Enterprise Authentication Server). AES is part of the WPA2 wireless security standard, TKIP part of WPA.
c. WPA2 is capable of WPA-PSK as well as WPA-EAP. Read [this]("http://en.wikipedia.org/wiki/IEEE_802.11i") if you have a minute.

---

### Post by epee on 2007-05-14
> **skullmunky said:**
> * why does it always set the key management to WPA-PSK, when it should be AES?AES is the encryption method, WPA-PSK is the Shared Key management method.

BTW - I found that my Windows XP laptop won't work with AES, but WILL work with TKIP.
> **skullmunky said:**
> *  if i change my router to use WPA-PSK instead of WPA2, why does nm-applet still identify it as WPA2/AES?  As before WPA2/AES means WPA2 protocol using AES encryption. WPA-PSK is the key menagement scheme. Confusing these two is probably why you're having trouble with the setup.

I think under Windows WPA-PSK is WPAPersonal (or something like that.)

---

### Post by skullmunky on 2007-06-21
:D:D:D:D

here's one possible answer to my original question:

the bcm43xx driver got better!  

just for kicks i tried following thist howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

to use the native bcm43xx driver with the firmware cutter; and it worked.  at least so far.  i'm away from home so can't try out my wpa2 setup, but it's working fine right now with WEP when ndiswrapper was not.    now nm-applet works correctly, all is happy and joyous, and the guinea pigs are popcorning with glee.

---

