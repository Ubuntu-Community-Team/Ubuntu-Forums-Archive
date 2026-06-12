---
title: "Broadcom BCM 4312 / 4322"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by user987 on 2014-05-03
i have 2 net books that have different broadcom wireless card.

I have created a live USB CD of Linux Mint 15  with persistence and use their software center to install the b43-LP-PHY driver for my BCM4312 netbook and have perfect wireless access.

When i try to install the BCM 4322 driver, the software center want me to remove the 4312 but then i cannot boot the other netbook for wireless access.

So my question is how can i install the drivers for both cards to my USB so i can use the same usb to boot up in either netbook and get wireless access?

---

### Post by varunendra on 2014-05-04
Please open a terminal (Ctrl-Alt-T) and show us the output of -
```
lspci -nnk | grep -iA2 net
```
..from the netbook that has the BCM4322 card.

---

### Post by user987 on 2014-05-06
Varunendra,

               The results are as follow:
  03:00.0 network controller[0280] : Broadcom corp BCM4322 802.11a/b/g/n wireless lan controller [14e4:432b] (rev 01)

Subsystem: Dell wireless 1510 wireless -n wlan mini-card [1028:000d]
kernel driver in use:wl


04:00.0 Ethernet controller [0200]: Realtek semiconductor co., LTD. RTL810E/RTL8102E
 
PCI Express fast ethernet controller [10ec:8136] (rev 02) 

Subsystem:Dell Device [1028:02f4] 
kernel driver in use:r8169

---

### Post by varunendra on 2014-05-06
Both your cards (4312 and 4322) work with both the native "b43" and the proprietary "wl" driver (see [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices")). The BCM4312 works well with the b43 driver (with "LP" firmware, which isn't 'uninstalled' once installed in the system), while the BCM4322 works well with the "wl" which is shown in your above output.

As such, you may try three things -

**1)** Keep the current "wl" driver and see if it works with the BCM4312 as well.

**2)** If it doesn't work with the 4312, try using "b43" on both. To do so, install the following package (needed only once) -
```
sudo apt-get install linux-firmware-nonfree
```
The above package contains (among others) a collection of all broadcom firmware that the "b43" driver may require for different cards. After doing this, simply purge the "wl" driver with the following command -
```
sudo apt-get purge bcmwl-kernel-source
```
The "b43" will load automatically *(loading the correct firmware)* since next boot after purging the "wl" driver.

**3)** If the "b43" doesn't work with the BCM4322 card, you *may* have to manually install/uninstall the "wl" driver each time you switch the netbooks. However, that is not too painful and doesn't require internet connection for installation, because once you install a package, it remains 'cached' in "/var/cache/apt/archives" directory (unless you manually 'Clean' the cache). So what you'll need to do is :

***** When on the "BCM4312" netbook -
[indent]```
sudo modprobe -rv wl
sudo modprobe -v b43
```
This may or may not work, because sometimes the "wl" driver doesn't get unloaded easily, and returns error like "module is in use". In that case, you must purge it with -
```
sudo apt-get purge bcmwl-kernel-source
```
..followed by a reboot.[/indent]

***** When on the BCM4322 netbook -
[indent]**IF** the "modprobe -rv.." command suggested above worked, and you didn't need to purge the "wl" driver, you won't have to do anything here. Otherwise -
```
sudo modprobe -rv b43
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
Note that you won't have to be connected to internet while installation, since the required packages are already in your 'apt-cache' (the "/var/cache/apt/archives" directory).[/indent]

Of these three, I think the 2nd solution is the best, if works. Otherwise the 3rd one can be a bit confusing for the first couple of times, but is doable.

---

### Post by user987 on 2014-05-07
[SUB]Varun,
         When i get the chance i will give your solutions a try and get back to you.
[/SUB]

---

### Post by bobmoyer on 2014-05-07
You might need to comment out the b43 driver in /etc/modprobe.d/blacklist.conf.I beleive that that is what I had to do to get my bcm4318 to work

---

### Post by varunendra on 2014-05-07
> **bobmoyer said:**
> You might need to comment out the b43 driver in /etc/modprobe.d/blacklist.conf.I beleive that that is what I had to do to get my bcm4318 to work

Not a good idea if the "wl" driver is also installed and loaded. It blacklists the "b43" to avoid conflict which may even freeze the system or cause kernel panic. It is important to unload the "wl" driver before loading "b43".

Unless both the cards work satisfactorily with any ONE of the two drivers (either solution 1 or 2 in my post), the best we can do is to try adding a script to udev rules to automatically do what I suggested doing manually. But that may take a few trials and tinkering.

---

### Post by user987 on 2014-05-09
Varun,
           I tried your #2 solution on a live usb with the Zorin 6.4 LTS OS and it work perfectly on both the BCM 4312 & 4322 Netbooks.

I did not have to use the 2nd command to purge the WL.

I did a lspci on both of the netbooks and the kernel driver being use is b43-pci-bridge.

I have a new problem now, for fun i went to the live usb with Mint 15 and use their software center to install their b43 installer which they say support BCM4322.

I did this with the USB plug into a 3rd computer which does not have broadcom wireless card and can access the wireless internet.

I then plug the Mint 15 USB into the BCM4322 Netbook and software center show that b43 installer is installed but i don't have wireless access.

Is it because i need to use ethernet on the BCM4322 netbook to do the install and not what i did via wireless on a 3rd laptop that is casusing this problem?

Is there a command i need to execute in terminal to get this to work, other then using your #2 solution.

I also did a lspci on this OS and it show the Kernel driver as B43-PCI-Bridge

---

### Post by varunendra on 2014-05-09
> **user987 said:**
> Varun,
           I tried your #2 solution on a live usb with the Zorin 6.4 LTS OS and it work perfectly on both the BCM 4312 & 4322 Netbooks.

I did not have to use the 2nd command to purge the WL.

I did a lspci on both of the netbooks and the kernel driver being use is b43-pci-bridge.
Unless some manual tweakings are done, the "wl" driver keeps the native "b43" blacklisted, thus preventing it from loading automatically. So I'm a bit mystified how it showed "b43-pci-bridge" (an alias for "b43+bcma" drivers combination) when the "wl" was still installed. Did you manually load it? Or did some manual editing somewhere?

In any case, I would like to see the current situation myself, which you can provide by running "wireless_script" created by forum moderator "Wild Man". I have tried to add a few more functions to it and we are currently testing that new version. Please download this 'testing' version from this link : [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) , then follow the "Wireless Script" link in my signature below. Follow the "No Internet" method (2nd one) to run the downloaded test script (not the one suggested in that post). Post back the report it generates.

I think you need to purge the "wl" driver as originally suggested, but just want to make sure there are no custom stuff to fix additionally.

---

### Post by user987 on 2014-05-12
Varun,
          I must aplogize, i have been using a couple usb live CDs with different OS and got confused.
The output i showed was from my Zorin 6.2 lite OS which use the wl kernel driver.

From my running lspci on my mint 15 and zorin 6.4 LTS OS they show the b43 bridge, i thhink that was why i did not have to purge the wl driver when i use your solution on the zorin 6.4 LTS OS.

If you have time can you explain what happen on my Mint 15 when i installed the b43 installer which should work with BCm4322 and it did not.

---

### Post by varunendra on 2014-05-13
> **user987 said:**
> If you have time can you explain what happen on my Mint 15 when i installed the b43 installer which should work with BCm4322 and it did not.

My brain is so messed up these days, I am making all the wrong guesses. So I'd rather prefer to see the diagnostics report of the wireless_script that I suggested in my previous post, and guess on basis of that information. :p

And just to help me help you, can you please reiterate what exactly the current problem is and what do we need to solve?

**PS:**
I do have time, just too little to analyze stuff deeply or make thorough posts. I'll try my best not to make any stupid mistakes while suggesting anything though. ;)

---

