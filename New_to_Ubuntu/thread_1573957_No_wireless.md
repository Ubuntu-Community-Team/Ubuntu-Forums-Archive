---
title: "No wireless"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by rosehipzero on 2010-09-13
I have a Linksys WMP300N and a USB Sabrent USB A11N, neither which i am able to get working. 

The Linksys WMP300N i had first and i got it to work back in Karmic but with my new computer i can. The broadcom drivers didnt work but were installed (now removed).

I did some research i read that the Sabrent USB A11N (Realtek chipset) worked with linux. So i bought it, and i tried to download the drivers off of their site and i cant download the driver (the URL must be broken cuz when i click on linux, the page refreshes)

So, i downloaded the right Realtek chipset drivers (Realtek RTL8191SU Wireless LAN 802.11n USB) and i tried to make it work in the Windows Wireless Drivers program but nothing happened. The driver is installed (the .inf file) but i dont think it did anything...
Also, i installed the Windows Drivers for the WMP300N through the Windows Wireless Drivers tool and nothing either...

Any help with any of those 3 issues?

---

### Post by ubunterooster on 2010-09-13
> **rosehipzero said:**
> The Linksys WMP300N i had first and i got it to work back in Karmic but with my new computer i can. The broadcom drivers didnt work but were installed (now removed)
try this link:[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)> I did some research i read that the Sabrent USB A11N (Realtek chipset) worked with linux. So i bought it, and i tried to download the drivers off of their site and i cant download the driver (the URL must be broken cuz when i click on linux, the page refreshes)If the link from their site continues to fail working try the two below (first is the official, second is a mirror)
[http://www.sabrent.com/drivers/USB-11N_RTL8191&8188.zip](http://www.sabrent.com/drivers/USB-11N_RTL8191&8188.zip)

[http://download.wireless-driver.com/driver/Sabrent/USB-11n/USB-11N_RTL8191&8188.zip](http://download.wireless-driver.com/driver/Sabrent/USB-11n/USB-11N_RTL8191&8188.zip)> So, i downloaded the right Realtek chipset drivers (Realtek RTL8191SU Wireless LAN 802.11n USB) and i tried to make it work in the Windows Wireless Drivers program but nothing happened. The driver is installed (the .inf file) but i dont think it did anything...
Currently on Windows I'm unable to check but I don't think the utility is for ndiswrapper aka,windows Wireless drivers but is most likely source for linux.

---

### Post by rosehipzero on 2010-09-13
Thank you Ubunturooster, i'll have to try it out tomorrow though... gotta study for my sociology and social enviroment classes first before my quizes.

thank you very much, it looks good and promising

---

### Post by rosehipzero on 2010-09-15
Ok, im having issues with the installation of the wireless drivers now. 

Whenever i type the following
```
sudo depmod -a
sudo modprobe ndiswrapper
```

The following is told back to me
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

What do i do?

PS, im using this guide : [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
I'm stuck on #13 in the instructions

---

### Post by bkratz on 2010-09-15
Those warnings are just that warnings, not errors--you can pretty much ignore them.

---

### Post by SonicLizzz on 2010-09-15
My best shot at this would be to wire it up to the internet, then go on Drivers and update and then go to System - Administration and the Update tools (or what it's called in English) and update everything. Then restart and it should work. Has done it for me on all my computers every time, at least

---

### Post by rosehipzero on 2010-09-15
I restarted, but now instead of having wireless that doesnt connect, i have no wireless at all now =/ i need to reverse everything

---

