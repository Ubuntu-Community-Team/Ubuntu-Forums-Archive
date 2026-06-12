---
title: "Ubuntu 16.04 fresh install, won't connect to WiFi"
date: 2016-05-29
forum: Networking &amp; Wireless
---

### Post by sunnybubblegum on 2016-05-29
Hello,

I've just done a fresh install of Ubuntu 16.04 on my desktop, but unfortunately I can't connect to our home WiFi network.

All of our other devices in the house have Internet connection (there are over eight devices between my family members), including my iPad and my PlayStation. But on a fresh install of 16.04 (I've literally touched nothing), it won't make a connection to my router.

It can see my router up in the top right corner dropdown (it has two bars signal strength), but when I try to connect to it, it asked for the password the first time, but on every attempt it never actually connects.

I had bought my network adapter because it said it specifically works with Ubuntu (it is the Qualcomm Atheros AR928X). Connecting with an Ethernet cable is not an option in my house; my desktop is just too far away from our router and modem, and too awkward.

I just really wanted the wireless to work, since I need operational Internet on my desktop for work and for pleasure.

Any help is welcome.

---

### Post by jeremy31 on 2016-05-29
There have been a couple other complaints about that same chipset recently.  It was reported that it last worked with Ubuntu 14.04.3

---

### Post by sunnybubblegum on 2016-05-29
Thank you for responding so quickly. Other than going and installing Ubuntu 14.04 on my system, do you think they will be adding/patching support for this chipset in the near future?

---

### Post by jeremy31 on 2016-05-29
Without a bug report getting filed, it is hard to tell if it will get fixed

A similar post is [http://ubuntuforums.org/showthread.php?t=2323816](http://ubuntuforums.org/showthread.php?t=2323816)

I wish I had better news for you

---

### Post by sunnybubblegum on 2016-05-29
I'm actually relieved to know it's a known problem. I thought it was something wrong with my computer setup. If it will help, I can file a bug for this. I will mark this thread as Solved since there is at least closure about the issue. Thank you again, you've calmed my mind.

---

### Post by sunnybubblegum on 2016-05-29
I'm in the process of filing a bug report.

Just out of curiosity, what is a good WiFi chipset or network adapter that is known to work well with Ubuntu 16.04?

---

### Post by sunnybubblegum on 2016-05-29
Here is the bug report I just filed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1586875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1586875)

I didn't know which package to file it under (I'm not a programmer), but hopefully it will find its way to the right people.

In the meantime I'm trying Ubuntu 14.04.

---

### Post by sunnybubblegum on 2016-06-03
Hello,

I just thought I'd give an update on the bug I filed regarding this issue with 16.04.

I've since gone and done a fresh install of Ubuntu 14.04.1. Software Updater got me updated to 14.04.4. My Internet has been working great, without a single problem.

Someone on AskUbuntu.com suggested that the issue might have something to do with the newer Linux kernel being used. By starting with 14.04.1, I have kernel 3.13 on my system, and don't intend to upgrade unless I learn that my WiFi card is supported.

Below I've attached two comments I've added to the bug I filed a few days ago. I hope I'm not alone in this issue, and that someone at Canonical will take notice and the problem will be resolved soon.

----------

*N (sunnybubblegum) wrote (#3):*
                        
Hi,

Here is the AR928X network adapter I bought in April of 2015 from ThinkPenguin.com:

[URL="https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-pcie-card-gnu-linux-v4-tpe-n300pcie4"]https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-pcie-card-gnu-linux-v4-tpe-n300pcie4
[/URL]
It says it works with Ubuntu 16.04, as well as Linux kernels 2.6.29  and newer. The best I had with it were very intermittent, spotty  connections to the Internet, and often not even to my router.

I've since gone back and done a fresh install of Ubuntu 14.04.1, and my Internet is working great now.

Upon further inquiries on AskUbuntu.com, someone suggested that the  problem had something to do with the newer Linux kernel being used in  newer Ubuntu versions.

Ubuntu 14.04.1 comes with kernel 3.13. Updating my system through  Software Updater automatically brought me up to 14.04.4, but thankfully  keeps kernel 3.13 if you started with 14.04.1.

Although I'd love to use Ubuntu 16.04, I don't want to install  anything newer than 14.04.4 unless I know that my WiFi adapter is  supported. I hope that will be sooner than later.

----------

*N (sunnybubblegum) wrote (#4):*

I should also just add that this WiFi adapter has worked great for me previously under Ubuntu 12.04 (.1 through .5).

---

### Post by tx4k4l on 2016-06-09
> **sunnybubblegum said:**
> 
Although I'd love to use Ubuntu 16.04, I don't want to install  anything newer than 14.04.4 unless I know that my WiFi adapter is  supported. I hope that will be sooner than later.


Ieup!! No, you are not alone. I'm making ready a course of Ubuntu16.04 for beginners and I have found the same problem when I was probing it in live mode at the Acer Extensa 5230. It has the Qualcomm Atheros ar928x Wireless network adapter. 
Also, I have happily see that when I was rebooting the PC (after installing 16.04 with 3rd party modules agreement), it can lisen, so greatly!!:guitar:

---

### Post by jeremy31 on 2016-06-09
I actually bought one of these cheap recently to see if I could diagnose any issues first hand and it backfired on me, it worked perfectly in an older Toshiba laptop running the Ubuntu 16.04 ISO.  And at this time I have no other laptop that I can test with as my Lenovo has a whitelist in BIOS and won't boot with it and I don't have the will to take apart the Dell N411z again- that is like going through the muffler of a car to change the spark plugs

There is an old fix that may help some of you
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Then reboot and see if it helps

---

### Post by dozycat on 2016-06-13
I got the same problem, I already did the: 

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf


no change.

This machine was working with 12.04 before, the wireless works however the connection is very slow.

I am including the output wireless-info.txt

---

### Post by jeremy31 on 2016-06-13
I would put the wifi router on channel 6 for now as it is vacant

Set the country codes with

```

sudo iw reg set CO
sudo sed -i 's/^REG.*=$/&CO/' /etc/default/crda

```

Go into Network Manager and change IPv6 to ignore

Reboot

---

### Post by dozycat on 2016-06-13
> **jeremy31 said:**
> I would put the wifi router on channel 6 for now as it is vacant

Set the country codes with

```

sudo iw reg set CO
sudo sed -i 's/^REG.*=$/&CO/' /etc/default/crda

```

Go into Network Manager and change IPv6 to ignore

Reboot


no change, the wireless connects however the speed of connection jumps from 39 mbps to 1 mbps.
The pc is dual windowx xp and xubuntu 16.04, and in windows xp the speed is of 130 mbps.

---

