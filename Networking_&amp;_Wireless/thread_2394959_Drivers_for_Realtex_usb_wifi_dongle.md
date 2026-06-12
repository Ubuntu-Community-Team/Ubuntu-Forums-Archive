---
title: "Drivers for Realtex usb wifi dongle"
date: 2018-06-24
forum: Networking &amp; Wireless
---

### Post by ruberad on 2018-06-24
Hi, I searched a bit, and couldn't find instructions that seemed to get me to drivers for my specific usb wifi dongle. There are lots of threads about Realtek, but I can't figure out how to identify the model of my dongle

I ran the wireless-info script and sent it to pastebin:

[http://paste.ubuntu.com/p/n3B7NhWtTH/](http://paste.ubuntu.com/p/n3B7NhWtTH/)

I ran the script with the ethernet plugged in and the the wifi dongle in a usb port so that lsusb recognized it.

Note for some reason the little led doesn't come on when this (allegedly brand new) dongle is plugged in, but I'm hoping that the fact that it's recognized by lsusb means it's working anyways. (Maybe drivers are needed so the computer can instruct the dongle to turn on its LED?)

Note also this old craptop has a non-working internal wifi (which is why I'm trying to revive it with a dongle)

If anyone can point me to a thread that shows how to install the appropriate drivers I'd appreciate it.

[SOLUTION] thanks to jeremy31! see post #20 that directs to the driver that got it done

---

### Post by jeremy31 on 2018-06-24
Your internal seems to pick up wifi signals fine but your USB dongle has 2 drivers loaded and that might be causing a problem so lets prevent one from loading
```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu-blacklist.conf
```
Reboot

---

### Post by praseodym on 2018-06-24
Check for the internal card

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by ruberad on 2018-07-02
Hi, thx for posts, I was expecting email notification but didn't get any is why it took me so long to get back. I will give a try to those commands and post back later, but 

> Your internal seems to pick up wifi signals fine

Note the internal sees plenty of wifi networks, and I can select mine and enter password, but it fails to connect. If doing something in software will fix the internal, that's a great option too.

---

### Post by ruberad on 2018-07-05
> **jeremy31 said:**
> Your internal seems to pick up wifi signals fine but your USB dongle has 2 drivers loaded and that might be causing a problem so lets prevent one from loading
```
echo "blacklist rtl8192cu" | sudo tee /etc/modprobe.d/rtl8192cu-blacklist.conf
```
Reboot
I tried that, it didn't seem to do anything. What should I check? I tried grepping for anything called rtl or 8291 in the output of lsmod and before and after there was only one with a number 81920 that seemed to be all about sound, not wireless.

---

### Post by ruberad on 2018-07-05
> **praseodym said:**
> Check for the internal card

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

I tried that -- what is that supposed to accomplish? Because what I have now is two network icons in my tray lower right, they seem identical. They both had the same bad behavior of the internal card, i.e. they see the available networks, but when you try to authenticate it just keeps flashing back asking for the password -- and no I know the password is right. This machine/install was previously able to use a different wifi dongle to connect, and when that was working the network tray popup would show that both the internal and the dongle were seeing all the networks; connecting through the dongle worked, but connecting through the internal didn't.

Should I run wireless-info again and pastebinit?

---

### Post by ruberad on 2018-07-05
How do I turn off or block the internal wifi which is not working, to get it out of the way?

---

### Post by jeremy31 on 2018-07-05
So ```
lsmod | grep rtl
```
Didn't show the rtl8xxxu module as loaded?  That would be strange.
Now I understand, you must have manually loaded those modules. try
```
sudo apt-get install git dkms build-essential
git clone https://github.com/jeremyb31/rtl8812au-driver-5.2.20.git
sudo dkms add ./rtl8812au-driver-5.2.20
sudo dkms install rtl8812au/5.5.20
```
Reboot

If you don't want the internal to work ```
echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
sudo modprobe -r ath5k
```

---

### Post by ruberad on 2018-07-05
Also I am seeing now that the package for the dongle came with a little cd with a directory called Linux. There are two subdirectories with very long names, like RTL8811CU and RTL8812BU. I assume the CU one is what I want?

I tried to compile them with the install.sh script but that was a massive fail, even after installing make and gcc -- what else am I likely to need?

---

### Post by jeremy31 on 2018-07-05
See post [https://ubuntuforums.org/showthread.php?t=2394959&p=13781384#post13781384](https://ubuntuforums.org/showthread.php?t=2394959&p=13781384#post13781384) in case you missed it

---

### Post by ruberad on 2018-07-05
Hi so I followed the steps of adding build-essentials, cloning the repo and those two dmks commands (typo in the second with the version number, but got past that) The last command took a while but seemed successful.

Also added ath5k to blacklist.conf (just sudo vi /etc/modprobe.d/blacklist.conf because that was a pre-existing file with a lot of stuff in it already -- or does tee concatenate?) and did the modprobe -r ath5k and rebooted (just one reboot after doing both parts)

So now, my networking popup in the tray it's back to just one of them, but it doesn't seem to know anything about wifi at all.

I did the wireless-info script again if that helps
[http://paste.ubuntu.com/p/Bvws2WhP7c/](http://paste.ubuntu.com/p/Bvws2WhP7c/)

FWIW I never added rtl anything manually before, this is a pretty fresh install of Lubuntu 17.10 and I wouldn't know how to do that anyways.

---

### Post by jeremy31 on 2018-07-06
Is Secure Boot disabled in BIOS/UEFI?

---

### Post by ruberad on 2018-07-06
mm I'll have to check, but if that were set wrong I wouldn't even be able to boot, would I?

---

### Post by jeremy31 on 2018-07-06
Check with terminal ```
mokutil --sb-state
```

---

### Post by ruberad on 2018-07-06
It said "EFI variables are not supported on this sytem". I guess this laptop is too old, pre-EFI

BTW lsmod | grep rtl still shows no new module, is there some way I can check the status of that attempted driver install?

---

### Post by jeremy31 on 2018-07-06
Post new results for the wireless script and results for ```
dkms status; modprobe -c | grep -i c811
```

---

### Post by ruberad on 2018-07-06
The dkms status said

rtl8812au, 5.2.20, 4.13.0-45-generic, x86_64: installed

but the modprobe -c | grep -i c811 returned nothing

Note at this point my networking popup seems to know only about wired connection. THere's a check for enable networking, but no check for enable wifi, and no group showing detected networks. I guess this is to be expected with the internal wifi deactivated and the usb not working (yet -- thx for your help!)

---

### Post by jeremy31 on 2018-07-06
What about new wireless script results?

---

### Post by ruberad on 2018-07-06
Here you go:

[http://paste.ubuntu.com/p/SBdnzKjh62/](http://paste.ubuntu.com/p/SBdnzKjh62/)

---

### Post by jeremy31 on 2018-07-06
Ok, I missed a detail in the source code, lets try
```
git clone https://github.com/whitebatman2/rtl8821CU.git
cd rtl8821CU
make
sudo make install
```
Reboot

---

### Post by ruberad on 2018-07-06
And that did it, thanks so much! I am now connected to my wifi using the dongle to make this post.

For my own education, what is the particular detail in the wireless-info.txt that points to just the right driver to use? I grepped and it doesn't have rtl in there anywhere. Is there a website for looking this kind of stuff up, or are you just so deep into wifi drivers that you know all this stuff?

---

### Post by ruberad on 2018-07-06
Also, my teenage son (who this laptop is for) also says THANK YOU SO MUCH because now he is not tethered to the router

---

### Post by jeremy31 on 2018-07-06
I just had to search to find what the 0bda:c811 was, it showed up in the source code of the first suggestion but I didn't notice the heading was for the rtl8821cu, after a kernel update it will not work until you
```
cd rtl8821CU
make clean
make
sudo make install
```
And reboot

---

### Post by ruberad on 2018-07-06
OK, so although it's working now, you're saying when automatic updates happen to bring in a new kernel I'll have to recompile the driver code against the new kernel headers and reinstall? That would be for every kernel update going forward?

Note this is for 17.10 (kind of a dead end I think) does that roll out new kernels much?

---

### Post by jeremy31 on 2018-07-06
17.10 is EOL by the end of the month but that source code might work in 18.04 also

---

