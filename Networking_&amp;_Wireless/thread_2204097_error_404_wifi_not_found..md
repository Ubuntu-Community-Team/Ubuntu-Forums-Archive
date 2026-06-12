---
title: "error 404 wifi not found."
date: 2014-02-06
forum: Networking &amp; Wireless
---

### Post by jon32 on 2014-02-06
hello all, im a fairly new linux user and i finally figured out the partition install to run ubuntu 13 on my macbook pro alongside windows 7.
i am having an issue however that i know has been addressed a lot (seeing as i tried almost every method to solve it, with no luck)
my wi-fi is not being discovered at all, no hardware, no driver, nothing, i know that the type of driver i need is a BCM57765. 
ive run many scripts and such and also found out that BCM4331 came up when i ran a few of them. 

what can i do to connect to the internet on my linux os? 
thanks,

---

### Post by varunendra on 2014-02-07
Welcome to the forums jon32 !

> **jon32 said:**
> ive run many scripts and such and also found out that BCM4331 came up when i ran a few of them.

Maybe you also tried the 'Additional Drivers' or "bcmwl-kernel-source" or "sta" or "wl" driver then? All of these are the names of the same thing which may not be as good as the native driver "b43" for your card.

Check -
```
lspci -nnk | grep -iA2 net
```
Do you see "14e4:4331" in the output? If yes, please try the following while you are connected to internet via cable -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```

If you don't have a wired connection or other means to connect to internet available, manually download the "linux-firmware-nonfree" file and install it as mentioned in this thread : [http://ubuntuforums.org/showthread.php?t=2203312](http://ubuntuforums.org/showthread.php?t=2203312) (posts #4 and #6)

Reboot and check if the wifi is working. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

