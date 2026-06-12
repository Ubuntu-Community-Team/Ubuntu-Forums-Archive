---
title: "Lenovo X131e no ethernet/wireless internet ubuntu 16.04"
date: 2017-07-11
forum: Networking &amp; Wireless
---

### Post by rikuo on 2017-07-11
Hi, I had internet a couple days ago but now there's no  connection either via ethernet nor wifi. It can see available networks and attempt to connect(require password) via Wifi but it will get stuck trying to connect/keep disconnecting and re attempting.

I've tried rfkill list all and restarting the network-manager which hasn't worked. All other devices are connected to my network (some via ethernet some WiFi) fine and it has not worked on other networks I've tried.

When I run 
[HTML]
  $ lspci -nn | grep Network 
[/HTML]

it returns 

[HTML]
  02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
[/HTML]


Edit: This is a fresh install ( Just reinstalled to try to fix ) Could this be a missing driver issue?

---

### Post by chili555 on 2017-07-11
> Could this be a missing driver issue?Not if you can see available networks. It could, however, be a *wrong* driver issue. Did you install the correct one?

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by rikuo on 2017-07-11
I haven't installed any drivers.. Even during installation my laptop couldn't connect to a network in order to install anything. It returned BCM 4313 [14e4:4320] (rev01) Not sure how I would install this (my other linux laptop broke) but I do have windows linux bash shell installed on my pc. Could I sudo apt-get the correct driver and somehow place it on  a usb drive to install onto my ubuntu laptop from my windows pc?

---

### Post by chili555 on 2017-07-11
What driver is loaded?```
lsmod | grep -e wl -e brcm
```Are there any clues in the log?```
dmesg | grep brcm
```

---

### Post by chili555 on 2017-07-11
> It returned BCM 4313 [14e4:[COLOR="#FF0000"]4320[/COLOR]] (rev01) What? In your original post, you said:> Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:[COLOR="#FF0000"]4727[/COLOR]] (rev 01)Is there a typo?

It makes a *big* difference as to how we proceed.

---

### Post by rikuo on 2017-07-11
Sorry, my internet went down for a bit. But [14e4:4727] (rev 01) is correct. 

when I type dmesg | grep bcrm it returns 

[HTML] [12.684636] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0a5c-21f4.hcd failed with error-2 
[12.684649] Bluetooth: hci0: BCM: Path brcm/BCM20702A1-0a5c-21f4.hcd not found]
[/HTML]

Then two more lines similar except  with [852.897674] and [825.896769]

Sorry I'm typing these out myself since my laptop has no internet..

---

### Post by chili555 on 2017-07-11
Let us see:```
sudo modprobe brcmsmac && dmesg | grep brcm
ls /etc/modprobe.d
```After we fix the wireless, we'll look at the bluetooth!

---

### Post by rikuo on 2017-07-11
These are the returns of both of the commands. 
[http://imgur.com/a/utAjs](http://imgur.com/a/utAjs)

---

### Post by chili555 on 2017-07-12
I am still persuaded that the correct driver for the device is not wl, but brcmsmac. Let's see if we can change it. We'll do so in a way that can be easily reversed if needed.

Please do:```
sudo gedit /etc/modprobe.d/blacklist-bcm43.conf 
```Use nano or kate or leafpad if you don't have the text editor gedit.

The file now reads:```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

```Please comment out brcmsmac and add wl so it reads like this:```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
#blacklist brcmsmac
blacklist bcma
blacklist wl
```Proofread carefully, save and close the text editor. Reboot.

Next, show us again:```
iwconfig
lsmod | grep -e wl -e brcm
```Is your wireless working?

If this helps, we'll need to do a few additional steps to make it persistent.

---

### Post by rikuo on 2017-07-12
[COLOR=#000000]sudo nano /etc/modprobe.d/blacklist-bcm43.confThis file actually didn't exist and was created when I opened it, so I entered 
all of these lines 

[FONT=&amp]blacklist b43[/FONT]
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
#blacklist brcmsmac
blacklist bcma
blacklist wl

This is my iwconfig and lsmod now 
[http://imgur.com/a/T5vWb](http://imgur.com/a/T5vWb)


oh my god, it's working! what would have caused that file to disappear? possibly something I did? Also what did I just do I take it blacklist doesn't mean I'm literally black listing these (or does it?)
Also I am connected however it keeps trying to connect to the ethernet connection and disconnecting while remaining connected is this a problem?
[/COLOR]

---

### Post by vocx on 2017-07-12
> **rikuo said:**
> [COLOR=#000000]sudo nano /etc/modprobe.d/blacklist-bcm43.confThis file actually didn't exist and was created when I opened it, so I entered 
all of these lines 

[FONT=&amp]blacklist b43[/FONT]
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
#blacklist brcmsmac
blacklist bcma
blacklist wl

This is my iwconfig and lsmod now 
[http://imgur.com/a/T5vWb](http://imgur.com/a/T5vWb)

[/COLOR]

Please do not take pictures. Instead, copy the terminal output to a text file, save that text file, then move it to the computer you are using now that has an Internet connection, open the file, and paste the contents, the text, in this forum. This is preferable than taking pictures. Image hosting sites go out of order, and addresses change, but if the text file is in this forum post it will live forever, and also text is easily found by search engines. Your problem and solution will also be found by future users and they will be thankful that you placed the terminal output in the forum and not in an image hosting site.

Put the terminal output inside CODE tags. There is an opening, and a closing tag.
[PHP]
```

The terminal output goes here.
It uses a monospace font and preserves spaces in the output.

lsmod | grep 'bla bla'

```
[/PHP]

---

### Post by rikuo on 2017-07-12
I wish I could, there's no internet connection on the laptop i'm trying to diagnose and I had to manually type the terminal output on my pc...

---

### Post by vocx on 2017-07-12
> **rikuo said:**
> I wish I could, there's no internet connection on the laptop i'm trying to diagnose and I had to manually type the terminal output on my pc...
Did you read what I wrote?

Copy the text, and paste it into a file. Then save the file, and then move the file from the laptop to the PC. You can do this by using USB memory stick. Is this clear?

This is better than taking pictures.

---

### Post by rikuo on 2017-07-12
<3

---

### Post by vocx on 2017-07-12
> **rikuo said:**
> Yeah because I have no internet **I can't download the drivers to allow usb port access with a memory stick**, but thanks for all your help man you're the best. I'm just waiting for Chili to come back with the final part of the fix, the other thread with a similar reply wasn't for my use case specifically.
You cannot use USB memory sticks in the laptop? I'm sorry but, did you try?

> **rikuo said:**
> I haven't installed any drivers.. Even during installation my laptop couldn't connect to a network in order to install anything. It returned BCM 4313 [14e4:4320] (rev01) Not sure how I would install this (my other linux laptop broke) but I do have windows linux bash shell installed on my pc. Could I sudo apt-get the correct driver and somehow **place it on  a usb drive** to install onto my ubuntu laptop from my windows pc?
In this quote of yours, you seem to indicate that you can download things from your Windows computer and move it to the Linux laptop with a USB drive. So, it seems this works. Why do you say you need to download USB drivers?

Linux is not Windows where you go online and "download drivers" for different peripherals. The "drivers" come with the Linux kernel, so if you can boot up Ubuntu, the drivers are probably already in your system. The problem you seem to be experiencing is that somehow the kernel did not load the correct drivers, thus why Chilli asked you to blacklist some modules here and there. But the drivers were already in your system.

So, this is just my humble suggestion. Do not take pictures of the terminal. I know it's easier for you, but really, it's much better for all of us (and for users that will read this thread in the future) if you can copy and paste the terminal commands and the output as plain text in CODE tags. That's it. You do not need to be offended.

---

### Post by rikuo on 2017-07-12
<3

---

### Post by Hadaka on 2017-07-12
Hi...
post#8
shows you did in fact have /etc/modprobe.d/blacklist-bcm43.conf file

When you did this..you overwrote it and now it only contains what you entered.
* sudo nano /etc/modprobe.d/blacklist-bcm43.conf This file actually didn't exist and was created when I opened it, so I entered
all of these lines

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
#blacklist brcmsmac
blacklist bcma
blacklist wl

post #10 where you say and show..
This is my iwconfig and lsmod now 
It is showing 2 things that need to be fixed.

1. - wl is still loaded as shown  by the  "lsmod " printout.

2. - power management is ON and needs to be off... "iwconfig" printout.

Now that you have internet access..let's fix things. PLEASE COPY and paste one line at a time
* IGNORE ANY ..file not found..or other error..  COPY and past every line...one at a time.
*This removes the unwanted *wl* module.
```
sudo modprobe -rf wl
sudo sed -i '/wl/ d' /etc/modprobe.d/blacklist-bcm43.conf
```
*This makes your needed wireless module *brcmsmac* load on every boot and start up.
it is the permanent fix.
```
echo brcmsmac | sudo tee -a /etc/modules
sudo sed -i '/brcmsmac/ d' /etc/modprobe.d/blacklist-bcm43.conf
```
*This turns your power mgmt.off..*iwconfig*
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*Next let's see if we can get your wired connection working. It is
IMPORTANT to be patient and let these files run to completion.
Please COPY and paste each line ONE line at a time.
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoclean
sudo apt-get autoremove
```
*Remove Any usb units.
Boot and test wireless..then insert wired connection
boot and test wired connection 
Thanks

---

### Post by rikuo on 2017-07-12
Sorry, nevermind i restarted my router and it's working again. 
Updating my apt-get now, at 121 kb/s..

---

