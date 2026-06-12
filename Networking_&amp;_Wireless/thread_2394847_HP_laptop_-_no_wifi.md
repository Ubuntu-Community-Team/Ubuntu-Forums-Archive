---
title: "HP laptop - no wifi"
date: 2018-06-22
forum: Networking &amp; Wireless
---

### Post by lilliseahorse on 2018-06-22
Hi All,
I have jusat installed 18.04 on a HP laptop.
But there's no WiFi.
As far as I can tell it needs a Realtek driver.
All ideas I've found on the web say I have to connect using an Ethernet cable to download drivers.
But the only internet connection I have is via a phone's 'hotspot', so no Ethernet.
I have access to another computer (hence this post) also using the hotspot.
Is there a way of downloading whatever driver is required to the other computer, and taking it across on a SD card perhaps?
Obviously I can't do any 'update' commands from the terminal when there's no internet connection.
All help appreciated.

(As a slight aside, I have to say I was expecting more, especially with all the hype about this latest version.)

---

### Post by Mark Phelps on 2018-06-22
I don't know what you mean in terms of "hype" -- but the general rule with laptops is to try the Live Version first -- to see if there are any driver problems, BEFORE you force an installation of a Linux distro on it.

Why?  Because most laptop vendors take shortcuts with hardware to keep the costs down and do NOT provide Linux drivers for that hardware.

You mentioned RealTek but my guess is that is the Wired Ethernet chipset, not the WiFi.  So, having that driver will do you no good for the WiFi.

You need to find out the WiFi chipset and post that information, or post the model number of the laptop.  With those details, you might be able to get some help on locating drivers.

---

### Post by slickymaster on 2018-06-22
Moved to the **Networking & Wireless** forum.

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

If you aren't able to connect to the internet with the affected system, including via a wired connection, just [navigate to this link]("https://ubuntuforums.org/showthread.php?t=2082305&p=12350385&viewfull=1#post12350385") and follow the instructions there on how to the run wireless script without an internet connection.

---

### Post by jeremy31 on 2018-06-22
Can you use USB tethering from the phone to the Ubuntu 18.04 computer to have internet access?

---

