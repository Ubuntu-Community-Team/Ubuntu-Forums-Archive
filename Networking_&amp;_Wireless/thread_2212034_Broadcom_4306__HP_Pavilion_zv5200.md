---
title: "Broadcom 4306 / HP Pavilion zv5200"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by dgomez2 on 2014-03-19
I am completely new to Linux and just installed Lubuntu 13 on a very old HP Pavilion zv5200 laptop. I understand I need to install NDISWRAPPER in order to make the Broadcom 4306 WiFi work. I already have the Windows .inf and .sys files for the wireless adapter.

I downloaded ndiswrapper-1.59.tar in another PC and copied it to to the Linux laptop. 
I extracted the file but when I tried to build it using 'make' it told me 'make' was not installed. 
I found out I had to install 'build-essential' but when I tried this (sudo apt-get install build-essential) it just said there were no candidates.
I tried looking in the Software Center and Package Manager but found no mention of ndiswrapper, make, or build-essential.
I am getting really frustrated as I do not understand how to install or even find these commands.

I would appreciate it very much if someone would be patient enough to show me the way to get ndiswrapper and my wifi adapter working.

Thanks!

---

### Post by su:bhatta on 2014-03-19
Sorry, no help with NDISWrapper, but, 

If you want to compile it  you can refer to this Help page : [URL="https://help.ubuntu.com/community/CompilingEasyHowTo"]https://help.ubuntu.com/community/CompilingEasyHowTo


[/URL]

---

### Post by mörgæs on 2014-03-19
Hi, welcome to the fora.

I suggest that you use Ndiswrapper only as a last resort. You will probably find better solutions for a BCM 4306 (be aware that there are more than one card with that name) if you take a look around here in Networking and Wireless.

---

### Post by varunendra on 2014-03-19
I believe you were lucky that the ndiswrapper didn't compile, otherwise you would have happily installed it and made it more difficult than it really is.

If you have a wired connection or other means to connect to internet, please open a terminal (Ctrl-Alt-T) and run this command -
```
sudo apt-get install linux-firmware-nonfree
```
Reboot and see if wifi is working now.

If you don't have a working internet connection on that machine, download the firmware package from this link : [http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14ubuntu1_all.deb)

Copy the downloaded .deb package to your Ubuntu Desktop, open a terminal, and run the following command to manually install it -
```
sudo dpkg -i Desktop/linux-firmware*.deb
```

If the firmware is installed and it still doesn't work, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by dgomez2 on 2014-03-20
Varun, 

thanks a lot! The problem was solved by following your  directions. Now I have fully functioning Wireless Adapter and Internet  access!

great help!!!

---

### Post by varunendra on 2014-03-21
You're welcome! :)

Just one thing to keep in mind -

During updates, the "Additional Drivers" feature may offer you a **proprietary driver**. **DON't install it**, as it would block the current driver and won't work itself. With this precaution, your wireless should keep working from now on. :)

---

