---
title: "Wireless Not Working after update"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by adrian13 on 2014-02-03
Hey guys i have an asus rc510ca with 6gb ram and 750gb hdd as well as an intel i5 1.8GHz processor. I installed Ubuntu 13.10 and when i was installing it, it connected to the internet or wifi network and then when it was fully installed i updated with the software updater and now the wireless is not working. It says its disabled by a hardware switch but the hardware switch is enabled. I have a Qualcomm wireless card in my laptop. PLEASE HELP!

---

### Post by Bucky Ball on 2014-02-03
*Thread moved to **Networking & Wireless**.*

Can you post the output of:
```

sudo lshw -C network
```

---

### Post by adrian13 on 2014-02-06
Sorry for the late response i had forgotten to bookmark this page and since im new to ubuntu forums and i didnt know how to navigate to the my threads page. It says a whole bunch of stuff but i dont know how to upload the picture on the forum as well as when i try to copy something from the os it doesnt work.

---

### Post by varunendra on 2014-02-06
You may copy paste the output from the terminal to a text file using your mouse cursor. While saving the file, make sure to select the "Line Ending" to "Windows" (if you are going to open it in Windows).

Copy this file to a pen drive > open it on another computer with internet connection > copy-paste the contents in your next post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

**PS:**
Alternatively, Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report file it generates. It will give us much more info about your wireless and related settings.

---

### Post by adrian13 on 2014-02-08
I tried again but it wouldn't work and the sound doesn't work either anymore so i deleted Ubuntu and installed windows because i did research but nothing came up. I'm sorry if I wasted your time.

---

### Post by Bucky Ball on 2014-02-08
Please mark the thread as solved. Thanks.

---

### Post by varunendra on 2014-02-09
> **adrian13 said:**
> I tried again but it wouldn't work and the sound doesn't work either anymore so i deleted Ubuntu and installed windows because i did research but nothing came up. I'm sorry if I wasted your time.

No problem at all! Not everyone has time to do the tinkering Linux may require sometimes.

Maybe try Ubuntu 14.04 in May or June when its initial bugs would have been fixed and it would have become reasonably stable. Of course feel free to get back to us whenever you feel like it. :)

---

### Post by adrian13 on 2014-02-09
Thank you very much and I will definitely try out the new Ubuntu 14.04. I am going to keep trying if I have the time to see if I could find the drivers to make it work. I recently actually installed the latest version of Xubuntu onto my friends HP MINI 2140 and the wireless wasn't working but I did research about the problem and they said you have to go to the settings and click on the additional drivers option which i did and successfully it detected the drivers and installed it. So i am going to try that whenever i have to on my computer because I still need to create partitions in windows because I want to install Zorin OS 8 and try that out.

---

### Post by varunendra on 2014-02-09
> **adrian13 said:**
> ..they said you have to go to the settings and click on the additional drivers option which i did and successfully it detected the drivers and installed it. So i am going to try that whenever i have to on my computer because I still need to create partitions in windows because I want to install Zorin OS 8 and try that out.
The "Additional Drivers" program does make things easier most often. But it _does not always_ offer the correct drivers, especially in case of "Broadcom" chips. So if you happen to have a Broadcom chip, take a look at the "Supported Devices" table on this page : [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

If it shows your device to be supported by the native "b43" driver, then DON't install what "Additional Drivers" program proposes, because that would most probably be a wrong driver for the card. Instead, you'd need to install the correct firmware in that case, which is as easy as running the command "sudo apt-get install linux-firmware-nonfree" with a wired connection (or install it manually otherwise).

To determine which wireless card you have, try the command -
```
lspci -nn | grep 0280
```

If it happens to be some chip other than Broadcom, the "Additional Drivers" program may be trusted.

---

### Post by adrian13 on 2014-02-10
It is compatible fortunately and it works nicely. Thank you for the advice though.

---

### Post by varunendra on 2014-02-10
You're welcome!

How about marking the thread as [SOLVED] then? If the sta driver works for your card on one Linux distro, it will almost certainly work with all other distros. If you ever face problems and think it may be the driver, you may take a look at the page I linked to to find out if "b43" can be an alternative. :)

---

### Post by adrian13 on 2014-02-13
No problem and I think I marked it as solved and I will definitely look at that if I have future driver problems. Thanks

---

