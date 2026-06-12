---
title: "Broadcom BCM4312 / HP Pavilion DV-6000"
date: 2013-09-24
forum: Networking &amp; Wireless
---

### Post by Djkotsios on 2013-09-24
Hello,

I have recently installed Ubuntu on my HP Pavilion DV-6000 and I have to say I am greatly disappointed so far. I was expecting something not so complicated (just a bit more than Windows), but instead I've been trying for the past 5 hours to get the WiFi working! Not to do anything complex, but for the WiFI!!!! 


Firstly I did connect a wired connection so I can have Internet access. I tried accessing the Additional Drivers section of System settings, I do get 2 drivers but when I try to install them, I keep  getting error after error. I searched the web further and I followed some codes on the Terminal up to one saying sudo apt-get install bf43-fwcutter. I did that and it installed (I think) I restarted my computer but still nothing. Then I go to try again, I write down the exact same code and when I am asked to type in my password, I am not allowed to type in anything. So basically I cannot do anything right now. I tried askubuntu for exactly the same thing but I got a too complicated and useless answer. I am extremely disappointed and too angry to eventually find out that I wasted hours of my life on nothing! Please give me some help from here in CLEAR STEP BY STEP INSTRUCTIONS as I'VE NEVER USED UBUNTU BEFORE. This is my last hope before uninstalling it once and for all and returning to the familiar Windows.

Thank you

---

### Post by Kopkins on 2013-09-24
Okay, firstly, I'm sorry te hear about your misfortune. Second, welcome to the community. And third, let's se if we can help. 

When you use the sudo command you will be prompted for your password, but it will not show any input. It will stay blank. Don't worry, just type in your password and press enter. 

Let's see if we can find your wireless card. For the following please open a terminal window and copy and paste the following commands. One command at a time. Please post the output of the command back here. When you do please use CODE tags like this:

[noparse]```

```[/noparse] 

And put your output in between. It makes it much easier to read.

Lets try this:
```
lspci -vnn | grep -i network
```

If you could, let us know what drivers ubuntu tried to install for you in the additional driver. And to get your wireless working we won't use those. 

Also, please post back the output of:
```

ls /etc/modprobe.d/

lsmod | grep b43

lsmod | grep wl

cat /etc/modules

```

Hope that was good for you. 

Kopkins

---

### Post by Djkotsios on 2013-09-25
Hello and thank you very much. I cannot thank you enough for your help.

Okay these are the codes shown to me: 

```
 Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
```

and for the rest in order:
```
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-bcm43.conf    blacklist-modem.conf        dkms.conf
blacklist.conf          blacklist-oss.conf          vmwgfx-fbdev.conf 
```

for the second and third codes, when I type them in the terminal, nothing appears.

And the fourth code:
```
 # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored. 
```

Once again thank you very much for answering and I hope I'll get this problem solved so I start learning Ubuntu :D

---

### Post by Kopkins on 2013-09-25
So I'm having trouble connecting to the official kernel wireless site. wireless.kernel.org

But I think your card does need the b43 driver. If not we can change that later, but for now let's see if we can get it working.

You'll need your wired collection.

So we'll unblacklist b43:
```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf

sudo apt-get purge bcmwl-kernel-source

sudo apt-get update

sudo apt-get install firmware-b43-installer b43-fwcutter

```

Then post back your output of:
```

sudo rmmod b43

sudo modprobe -v b43

dmesg | grep b43

```

Unplug your wired connection and see if you can find any wireless connections.

Good Luck!
Kopkins

---

### Post by Djkotsios on 2013-09-25
When I typed in the last code to install b43 I got this: ```
No chroot environment found. Starting normal installation
An unsupported BCM4312 Low-Power (LP-PHY) device was found.
Use b43 LP-PHY firmware (firmware-b43-lpphy-installer package) instead.
Aborting. 
```

also for the other codes you told me here are the outputs: 
```
sudo: smmod: command not found
```

```
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43. 
```


```
[  723.091055] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  723.132171] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[  723.170550] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[  723.170555] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[  723.170558] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
```

I'm guessing it did not work so I am waiting for further instructions. Thank you! :)

---

### Post by Kopkins on 2013-09-25
Okay so the linux wireless site is back up [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43).

And it says that you do need the low power version, so lets start over.

```

sudo apt-get purge firmware-b43-installer

sudo apt-get install firmware-b43-lpphy-installer

```

Then it should work.

Again
```

modprobe -r b43

modprobe b43

dmesg | grep b43

```

Now it should be working. 

To make it auto load everytime:
```

echo b43 | sudo tee -a /etc/modules

```

Then reboot and you should have working wireless.

Kopkins

---

### Post by Djkotsios on 2013-09-26
It finally works :D I can now start learning Ubuntu better! 

I cannot thank you enough for your help! I was about to give up! Thank you very much! :)

---

### Post by Kopkins on 2013-09-26
Well I'm glad I could help you and that you're able to try ubuntu now! 

You can mark your thread solved to help other people find the solution by going to your first post and clicking thread tools and then clicking mark as solved.

Kopkins

---

### Post by Taimur_Saleem on 2013-10-15
I am running the same wifi network adaptor as the OP but I dont understand the process after you told him to install the b43 driver. I also have the issue of wifi not working. I know the thread is solved but I did post a new thread on this as well. 

> **Kopkins said:**
> Well I'm glad I could help you and that you're able to try ubuntu now! 

You can mark your thread solved to help other people find the solution by going to your first post and clicking thread tools and then clicking mark as solved.

Kopkins

---

