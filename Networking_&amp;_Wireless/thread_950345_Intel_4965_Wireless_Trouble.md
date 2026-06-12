---
title: "Intel 4965 Wireless Trouble"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by Manillien on 2008-10-17
I just bought a Compal JFT00 Laptop with Intel 4965 Wireless card. I installed Kubuntu on it, but it can't find, or somehow utilize, the wireless card. KNetworkmanager just allows me to turn wireless on or off, but it doesn't find any wireless networks, (or the wireless device in the configuration window for that matter).

After doing a whole lot of googling, (I'm a Linux noob) I tried the lshw -C Network command, and the wireless card shows up, with configuration: driver=iwl4965, latency=0, module=iwl4965, as it should be. It has, however, no logical name, as opposed to the ethernet interface. I also did the dmesg command, and one of the messages says iwl4965: Radio disabled by HW RF Kill Switch
Following up on another advice, I did cat /sys/bus/pci/drivers/iwl4965/0000\:01\:00.0/rf_kill which returned the value 0.

On the computer, there is a LED button that has a Wireless/Bluetooth symbol on it. When I press it, the Bluetooth symbol shows up in the desktop tray, and another LED lights up with the Wireless/bluetooth symbol, and it's blue. I have tried all the stuff both with turning this button on and off. There is no way to turn off any Wireless Kill Switch in BIOS.

Also, on the F2 key, there is a wireless symbol (only wireless, no bluetooth), which may indicate that I could press Fn+F2 to activate the wireless. All the other Fn+something button combinations work (e.g. increasing volume, sleep mode and so on), but when I do Fn+F2, nothing happens. I have also tried all of the above things after doing this, with no change. When I did showkey, it did not register Fn at all, so I'm a bit surprised this button works at all in Linux. (But maybe I don't know what showkey really indicates)

This is all the info I have about this. What can I do? Thanks in advance.

---

### Post by chessmani on 2008-10-17
Have you tried updating to the latest kernel? (2.6.24-21-generic) The wireless switch has worked for the first time for me with this new kernel. (ad-hoc still doesn't work though)

Otherwise, you could try enabling wireless in Windows and rebooting into Ubuntu again. Sounds weird, but that solved the problem for me some time ago.

---

### Post by Manillien on 2008-10-17
I don't really know how to update the kernel, but it was just a couple of days ago that I downloaded the Kubuntu iso, so it should be pretty up-to-date?

As for the windows solution, first of all, I don't have windows (I have a windows cd for Dell pc's, but I'm not sure if that will work on this compal pc?) . Second of all, it seems like a pretty unsatisfactory solution to me, I would like to keep this PC windows-free...

Edit: Alternatively, if anyone knows of a light 12,1'' laptop that is tested to work with Linux and which is not too expensive (9k max), I can still return this Compal pc and get this other one.

Edit2: I have the newest kernel, I just checked!

---

### Post by soxs on 2008-10-17
I installed intrepid (beta) and it just works fine (at least wlan, didn't manage to connect my phone via bluetooth to my laptop yet). I didn't even try to install hardy as I knew from a install of my friend that there were ugly hacks required to make wlan work (I had to install ubuntu, becuase he was just starting to get a linux-pro ;-) )

---

### Post by Manillien on 2008-10-17
Ok, I guess I can try this, just have to wait to see if some other advice I got works first. I would still appreciate any further advice on my current version, though!

---

### Post by soxs on 2008-10-17
> **Manillien said:**
> Ok, I guess I can try this, just have to wait to see if some other advice I got works first. I would still appreciate any further advice on my current version, though!

I understand that, but I must say intrepid(beta) works flawlessly for me. (I just got a laptop myself which uses the same wlan chip/card)

---

### Post by soro2005 on 2008-10-17
> **Manillien said:**
> Ok, I guess I can try this, just have to wait to see if some other advice I got works first. I would still appreciate any further advice on my current version, though!

There apparently is a conflict between the new kernel version (2.6.24-21), which has the driver for the Intel 4965 built in, and the package linux-backport-modules, which had provided some of the functionality for the device in the past. So I and some others have been able to get our wireless back on by searching in synaptic for linux-backport-modules and unchecking all of them, perhaps with the exception of version 2.6,24-19.17 which might be useful if you want to boot into the older kernel version. Then "apply".

Btw.: If you want to boot an older kernel which you might still have lying around on your machine: Hit <esc> after switching on the computer, before ubuntu starts booting, and select an older version from the list. This only works if you've done at least one kernel update in the past, and haven't removed all of your old kernels.

---

### Post by Manillien on 2008-10-17
Hi, thanks for the advice. As I said, I'm a noob, so I don't know what searching through synaptic means... could you do a rough step-by-step?

Thanks

---

### Post by soro2005 on 2008-10-17
Well, you're using KDE (Kubuntu), so I guess you're not using Synaptic but Adept? Look for either of the two in the "System" entry of your start menu, then use the search function (in Synaptic "ctr + f" or the big search button, must be similar in Adept) to locate all entries that start with "linux-backports-modules". There are several, one for each kernel version and some that are there to ensure that others are correctly updated. Uninstall all of them, or if you want, keep the ones that have a version number that ends in 19.17 or lower.

Alternatively, you can open a terminal/command line and enter:
```
sudo apt-get remove linux-backports-modules*
```
But: NEVER trust anyone who gives you this sort of command line advice unless you are absolutely sure that you are not being set up. Read the man page first. (man apt-get or [here](http://manpages.ubuntu.com/manpages/hardy/man8/apt-get.html)).

---

### Post by Manillien on 2008-10-18
Thanks for the advice, soro. I will try that later. However, now I installed Kubuntu Intrepid Ibex, and now my wireless shows up in Knetworkmanager! Yay! However, it does not seem to search for any wireless networks, but then again, I don't know how it's *supposed* to look when it does so. I also don't know if there are any wireless networks where I am, so I don't know if it's just because it can't find any or because it's not searching. 

The device is now called wlan0 and it shows up, as said, in Knetworkmanager. From windows, I'm used to the "network manager" just displaying a list of wireless networks. Where is that list in Kubuntu?

Again, thanks all!

Edit: After doing a bit of further looking, I think the problem is still the HW RF Kill message that I get with dmesg|grep iwl (Radio disabled by HW RF Kill Switch). When I switch wireless off and on again via Knetworkmanager, dmesg gives that message again. Also, when I do cat /sys/bus/pci/drivers/iwlagn/*/rfkill/rfkill0/state it returns 2, which, as far as I understand, means that the hardware kill switch is turned on. Normally, I think the way to turn it off is by Fn+f2, but when I do that, dmesg then shows that it doesn't recognize the key combination, or the key Fn for that matter. The Bluetooth/Wireless LED button doesn't do anything either.

I'm about to give up on this: It doesn't seem to be any way of turning off the HW RF Kill switch that Linux recognizes.

---

### Post by soxs on 2008-10-18
don't give up: first give us the output from ```
lspci
```

---

### Post by Manillien on 2008-10-18
heh, thanks for being positive!
Here's the output from lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)                                                                  
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)                                                 
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)                                                        
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)                                                                  
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)                                                                 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)                                                                       
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)                                                                          
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)                                                                          
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)                                                                          
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller(rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)

---

### Post by soxs on 2008-10-18
> **Manillien said:**
> 
01:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
 I am sorry, I mixxed that up, my friend had your one and I have a 3945..

I will do some resaerch and will get back on tomorrow

---

### Post by soro2005 on 2008-10-19
Have you uninstalled the backports-modules packages? There may be other problems with the kill switch, and I haven't tried out in a long time whether toggling with keyboard shortcuts works. I think that, several months ago, I could get the device back up by suspending or hibernating. With the backports-modules package installed, I had the same kill switch related dmesg output you report. The device seemed to be working for a couple of moments at boot, but then was switched off with no intervention of mine. Uninstalling the backports-modules solved that one.

---

### Post by soxs on 2008-10-19
Due to the new intrepid kernel, this migth be enough to make it work (at least as long as you don't reboot):
```
sudo modprobe mac80211
sudo modprobe iwl4965
```
post the ouput these commands spit at you.
Taken from: [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095) and [http://ubuntuforums.org/archive/index.php/t-526945.html](http://ubuntuforums.org/archive/index.php/t-526945.html)

---

### Post by Manillien on 2008-10-19
@soxs: Those two commands gave no output!

@soro: I looked for the packages in adept, but none were found. Any idea where they went?

---

### Post by soxs on 2008-10-19
> **Manillien said:**
> @soxs: Those two commands gave no output!

perfect!

when you boot again, execute them again and check wether it works or not, including your phsical switch

Try to play around with the switch at boot time.

---

### Post by soro2005 on 2008-10-19
> **Manillien said:**
> @soro: I looked for the packages in adept, but none were found. Any idea where they went?

Are you using Intrepid or Hardy now? You can open a terminal and enter
```
dpkg -l | grep linux-backports-modules
```
If you get one or several lines listing packages like that, and at least one of them is prefixed with "ii", then you have the backports modules package installed. If you don't get any output, or if each of the lines is prefixed by "rc", then the backports modules thing is not your problem, because you don't have the package installed.

You could post the entire output, if you want.

As for soxs's suggestion to load the kernel module manually: You may want to check whether it's loaded first. If it isn't then adding it to the list of modules to be loaded at start may help. My hunch is that that's not the problem. After all, the module should now come with the kernel, which I take to mean that it's loaded if needed.

To check whether the module is loaded:
```
lsmod | grep iwl
```
If you get no output, it isn't loaded. If you get some output, you can post it here so we can see further.

---

### Post by Manillien on 2008-10-19
Soxs: I tried turning it on during boot, and I tried turning it on after boot, I tried turning it off and on... nothing's working. I really think the problem is that the card is switched off but I can't seem to get it on...

soro - the first command you gave got no output, so I guess there are no backport modules. I'm running Intrepid now, maybe that's why...  The second command

eirik@eirik-laptop:~$ lsmod | grep iwl
iwlagn                 99588  0
iwlcore                92740  1 iwlagn
rfkill                 17048  2 iwlcore
led_class              12164  1 iwlcore
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211

---

### Post by soro2005 on 2008-10-19
Ok, seems like your diagnosis is correct and the killswitch is just hung in a bad state, or your Ubuntu always starts with the killswitch on (wireless off). You could try to:
 - Use a Live CD and see whether the same problem occurs.
 - Use a Live CD of a different Distro (OpenSuse for example) to see whether you can switch.
 - Do what soxs has suggested, but first remove the kernel module, then load it again. If it doesn't work that way, try removing the module, toggling the switch physically (or hitting the button once), then adding the module.

To remove the kernel module:
```
sudo modprobe -r iwlagn
```
To add it:
```
 sudo modprobe iwlagn
```

[Here is a bugreport](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269264) that seems to match your problem quite closely.

---

### Post by Manillien on 2008-10-20
Ok, I will try to boot it from a Live CD, I have one with Ubuntu and one with Kubuntu. I also now remembered that there was a driver cd which came with the laptop, and one of the drivers was the driver for this switch. Is there any way to run windows drivers in Linux? Sort of like ndiswrapper, but with non-wireless drivers?

---

### Post by Manillien on 2008-10-20
OK, tried booting Kubuntu from LiveCD, didn't work. It was Hardy, so it didn't even recognize any card. The same happened when I tried Ubuntu (I think Hardy as well).

---

### Post by soro2005 on 2008-10-20
> **Manillien said:**
> Ok, I will try to boot it from a Live CD, I have one with Ubuntu and one with Kubuntu. I also now remembered that there was a driver cd which came with the laptop, and one of the drivers was the driver for this switch. Is there any way to run windows drivers in Linux? Sort of like ndiswrapper, but with non-wireless drivers?

There's a way to run windows drivers for wireless devices under linux, but that's not what you need since your wireless device is natively supported by linux. There is a separate driver for the switch? What's the computer model, by the way? Perhaps you could use an Ibex Live CD, or even an OpenSuse one? If the switch is just stuck in that position, your best bet might be to see whether you can run Windows without too much of a hassle. Perhaps you have an old harddrive somwhere which you could swap in for that purpose. :confused:

---

### Post by Manillien on 2008-10-20
The model is a Compal JFT00, and yes, there was a separate driver for the switch. I could run windows, but that will get tedious at length. So then I think I'll just return the pc and get one that works. Do you know if the ThinkPad SL300 has these problems? Or do you recommend another ThinkPad?

---

### Post by soro2005 on 2008-10-20
I was thinking that, if you run Windows once to switch the switch, and then see whether it works afterward. That might do the job already.

I think that the Thinkpads are quite excellent, also with Ubuntu, but my only experience is with an older model. I'm currently using a Asus backbone which I got from Zareason, and I'm extremely happy with it. They sell hardware for Linux, and their guarantee encourages you to open the box and upgrade if you feel like it.

---

### Post by esoterican on 2009-02-22
Hi,
I got the same problems with WLAN and the JFT00.
The only workaround is to install Windows in a small partition (e.g. 10GB).
Install the WLSS (wlan switch software) and use Win only to switch the WLAN on.
I've tried _many_ other live-distros (OpenSuse 11.1, Knoppix X.X, DSL 4.X, GRML ... and Ubuntu 8.10, 9.04) but they ALL got this problem.

I assume that there is a only a bug in this keycode thing. Because - funny enough - you can switch the WLAN _OFF_ under Ubuntu... no problem. 
But you had to use Windows to switch it on.
And if WLAN is switched ON it worked like a charm under Ubuntu.

With best regards
 Eric

---

### Post by soxs on 2009-02-22
> **esoterican said:**
> Hi,
I got the same problems with WLAN and the JFT00.
The only workaround is to install Windows in a small partition (e.g. 10GB).
Install the WLSS (wlan switch software) and use Win only to switch the WLAN on.
I've tried _many_ other live-distros (OpenSuse 11.1, Knoppix X.X, DSL 4.X, GRML ... and Ubuntu 8.10, 9.04) but they ALL got this problem.

I assume that there is a only a bug in this keycode thing. Because - funny enough - you can switch the WLAN _OFF_ under Ubuntu... no problem. 
But you had to use Windows to switch it on.
And if WLAN is switched ON it worked like a charm under Ubuntu.

With best regards
 Eric

Did you file a bugreport?? If not, do so. [www.launchpad.net](www.launchpad.net)

---

