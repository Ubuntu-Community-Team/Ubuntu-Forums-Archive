---
title: "WEP encryption setting not working on Ubuntu 10.04"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by gchiacch on 2010-09-07
Hello,
I am a new linux user (Ubuntu 10.04 Lucid) , 
I'm looking for help about the WEP encryption set-up on my ubuntu PC to connect to my home wireless router. 
It works if I don't use WEP and I can also connet using WEP encryption key by other Windows PCs. 
I am sure the 26-hex digits (128 bit key)is correctly typed in. 
The iwconfig wlan0 shows that ESSID is setup, the AP MAC is associated, the Encryption key is setup like xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx
When I try to connect I get the pop-up window for 'Wireless Network Authentication Required' after a while and the connection is not established.
I googled around finding several suggestions about the settings of the WEP key on ubuntu by CLI commands like:
iface wlan0 inet dhcp
wireless-key hex-key
wireless-essid ssid
auto wlan0
or even as described by the 'WEP Connection' section of [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
So far I haven't found the right setting to use. Please Help

---

### Post by bredman on 2010-09-07
This is a very common problem, and is probably a fault in the driver for your WiFi device.

When writing the code for the driver, the authors usually concentrate on WPA and give little consideration for WEP, because it is next to useless.

My recommendation is to use WPA instead.

If you really can't use WPA (for example if you have a Nintendo DS in your house) you should use MAC filtering instead of WEP. MAC filtering won't stop a hacker, but WEP is no better.

---

### Post by RetchingRabbit on 2010-09-07
I agree. I use mac filtering and leave my network open. Never had a problem in several years of doing it this way. WEP and mac filtering are both almost useless, but they will keep the honest people honest....

---

### Post by uRock on 2010-09-07
WPA2 & hidden network ftw!

---

### Post by gchiacch on 2010-09-07
Thanks for reply. I will verify first if a driver upgrade is available.
Searching around I also read that others with similar problem solved their issue just using some CLI command. I would prefere to investigate this option a bit more before planning to change security to WPA (I need to change my router first to get the WPA2 option).
 
> **bredman said:**
> This is a very common problem, and is probably a fault in the driver for your WiFi device.
 
When writing the code for the driver, the authors usually concentrate on WPA and give little consideration for WEP, because it is next to useless.
 
My recommendation is to use WPA instead.
 
If you really can't use WPA (for example if you have a Nintendo DS in your house) you should use MAC filtering instead of WEP. MAC filtering won't stop a hacker, but WEP is no better.

---

### Post by gchiacch on 2010-09-07
Thanks for your reply,
I will use your suggestion to use MAC filtring and leave the network open as last chance just in case there is no way to fix it while waiting to get a new router with the WAP2 option. 
 
> **RetchingRabbit said:**
> I agree. I use mac filtering and leave my network open. Never had a problem in several years of doing it this way. WEP and mac filtering are both almost useless, but they will keep the honest people honest....

---

### Post by gchiacch on 2010-09-07
Thaks for your reply, this seems the best option but I need first to change my router.
> **uRock said:**
> WPA2 & hidden network ftw!

---

### Post by gchiacch on 2010-09-13
I finally received the new router with the WAP2 capability. It solved the wireless issue. Thank you to everybody for suggestions. 
Can somebody tell me how to flag this thread in  "Solved" status, please?

---

### Post by Kixtosh on 2010-09-13
> **gchiacch said:**
> I finally received the new router with the WAP2 capability. It solved the wireless issue. Thank you to everybody for suggestions. 
Can somebody tell me how to flag this thread in  "Solved" status, please?Glad that you solved your problem!

To mark the thread as solved, simply open it up (it already is if you're reading this) and click on the "[COLOR="Red"]**Thread Tools**[/COLOR]" on the top right of your screen. You should find an option there to mark the thread as solved.

---

