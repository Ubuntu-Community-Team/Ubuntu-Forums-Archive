---
title: "Network Manager don't lists any networks"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by haperw112 on 2011-05-08
Yup, i know that WiFi problems are one of the most common here. Anyway, my google-research didnt help me so i post here ;)
I have *Atheros AR5005G Wireless Network Adapter* and **lspci** command finds it. Also **ifconfig** says that its up as *wlan0*. However, neither *Network Manager* isnt able to find any network nor **iwlist wlan0 scan** (*no results has been found* or similar). I have tried many tutorials on the web (for example [that]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") one and [that]("http://ubuntuforums.org/showthread.php?t=571194") one) but with no luck. Networks exists because on my Win XP wireless connecting works fine. Thanks.

---

### Post by micael3000 on 2011-05-08
Aren't you with your wireless off? I mean, by pressing FN + (Usualy F2) you can turn wireless on / off...

---

### Post by haperw112 on 2011-05-09
Yes, im pretty sure that my wireless is on (diode at the front panel is on - same as on Windows). In Network Managers ticks at "Enable Wireless" are also marked. Still, no networks listed.

---

### Post by jtarin on 2011-05-09
Step-by-step to Enable Wireless Network Connection for Ubuntu 10.10:

    1.Connect an Ethernet cable to your laptop or system to your router, don't use wireless.
    2.Go to the System-Administration Pull-down Menu and find Hardware Drivers.
    3.Activate wireless driver if you see that in the "Additional Drivers" list.
    It looks for proprietary drivers that Ubuntu is not legally allowed to include so you have to do this manually. It should find something like STA Wireless Driver, just select it. If there are more than one, pick the recommended one and enable it. While you are there, if there is a driver for your video card, enable that too while you are at it (then after step 4, go into System-Preference-Appearance and select extra under visual)
    5.Close the dialog after successful installation. Then reboot, restart your computer from the system menu (in the upper, right corner).
    6.Reboot and your wireless network connection should now be working.

When going to the System > Administration > Additional Drivers shows nothing, please make sure you have plugged in an ethernet cable first, or try to use another wired/wireless manager like wicd, if everything else fails, well, the only method is to go back to 10.04.

---

### Post by haperw112 on 2011-05-09
The biggest problem is that i am not able to use wired connection - only WiFi :/ Everything has to be done offline. I has just tried another distro (Slax from USB) and wireless connection works here without problems.

---

### Post by haperw112 on 2011-05-10
Okay, so I hopefully managed to connect wired connection and... WiFi also started to work. Just like that. No additional clicking or so, just plugged a wire and then list of WiFi networks has appeared. After rebooting its still working. Anybody can me explain that? Well, everything seems to work now but explanation could be helpful in future problems.

---

### Post by jtarin on 2011-05-10
> **haperw112 said:**
> Okay, so I hopefully managed to connect wired connection and... WiFi also started to work. Just like that. No additional clicking or so, just plugged a wire and then list of WiFi networks has appeared. After rebooting its still working. Anybody can me explain that? Well, everything seems to work now but explanation could be helpful in future problems.As my directive demonstrates......wired connection.....drivers not provided on install are downloaded and installed....your up and running. I suggest you read my post again and do a walk-through if needed.

---

