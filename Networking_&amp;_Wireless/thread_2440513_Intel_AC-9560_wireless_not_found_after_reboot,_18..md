---
title: "Intel AC-9560 wireless not found after reboot, 18.04"
date: 2020-04-11
forum: Networking &amp; Wireless
---

### Post by janderson9er on 2020-04-11
Hi! 

I am running into issues with my wifi not being available after I rebooted.

[Wireless info]("https://pastebin.com/L740wtwX") available here.

Some highlights:
##### lspci #############################
00:14.3 Network controller [0280]: Intel Corporation Wireless-AC 9560 [Jefferson Peak] [8086:a370] (rev 10)
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi
 
05:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2500 Gigabit Ethernet Controller [1969:e0b1] (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E2500 Gigabit Ethernet Controller [1462:7b12]
    Kernel driver in use: alx

[COLOR=#333333]##### rfkill ############################
[/COLOR][COLOR=#333333]0: hci0: Bluetooth
[/COLOR][COLOR=#333333]Soft blocked: no
[/COLOR][COLOR=#333333]Hard blocked: no

[/COLOR][COLOR=#333333]##### iwconfig ##########################
[/COLOR][COLOR=#333333]enp5s0    no wireless extensions.
[/COLOR][COLOR=#333333]lo        no wireless extensions.
[/COLOR][COLOR=#333333]docker0   no wireless extensions.
[/COLOR][COLOR=#333333]bnep0     no wireless extensions.[/COLOR][COLOR=#333333]
[/COLOR]
I think that script includes everything needed, I wasn't doing anything (that I know of) that would have created these problems. I verified I am booting in Legacy + UEFI.

However, after I lost it, I did the classic try commands and hope they work without really knowing what they are doing. That mostly consisted of following along with [Wireless Trouble Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers"), where I verified the driver is loaded with `lsmod`, but am stuck on with no results from iwconfig. I also tried installing lwfinger/rtlwifi_new and removing, but obviously that wasn't a good idea. Lesson learned, apologies if I created more work for those who are trying to help. 

Thank you everyone!

---

### Post by janderson9er on 2020-04-12
And doing a little more research, I think this is narrowing it down...

lspci -nnk | grep 0280 -A3
00:14.3 Network controller [0280]: Intel Corporation Wireless-AC 9560 [Jefferson Peak] [8086:a370] (rev 10)
	Subsystem: Intel Corporation Device [8086:0034]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

dmesg | grep wl
[   60.962505] iwlwifi 0000:00:14.3: loaded firmware version 34.3125811985.0 op_mode iwlmvm
[   61.182040] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[   61.331360] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[   61.331363] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[   61.331432] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x3, CPU2 Status: 0x2458
[   61.331433] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[   61.343752] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5

I'm not really finding anything from the error messages, though.

---

### Post by chili555 on 2020-04-12
Let's be certain that you have the latest firmware. With a working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:

```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.183.2_all.deb
sudo dpkg -i linux*.deb

```
Reboot and let us see:

```
dmesg | grep iwl
```

We'll troubleshoot from there.

---

### Post by janderson9er on 2020-04-12
Thank you for replying!

I did as requested, here's the output:

```
dmesg | grep iwl
[  248.160845] iwlwifi 0000:00:14.3: loaded firmware version 34.3125811985.0 op_mode iwlmvm
[  248.235762] iwlwifi 0000:00:14.3: Detected Intel(R) Dual Band Wireless AC 9560, REV=0x318
[  248.280546] iwlwifi 0000:00:14.3: Microcode SW error detected. Restarting 0x0.
[  248.280550] iwlwifi 0000:00:14.3: Not valid error log pointer 0x00000000 for Init uCode
[  248.280581] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x3, CPU2 Status: 0x2458
[  248.280583] iwlwifi 0000:00:14.3: Failed to start INIT ucode: -5
[  248.292031] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -5



```

---

### Post by chili555 on 2020-04-12
Please try this: [https://unix.stackexchange.com/questions/555784/iwlwifi-failed-to-run-init-ucode-5](https://unix.stackexchange.com/questions/555784/iwlwifi-failed-to-run-init-ucode-5) In your case, the relevant PCI bus is:> 
iwlwifi [COLOR="#FF0000"]0000:00:14.3[/COLOR]: Failed to run INIT ucode: -5
 Therefore, the sequence will be:```

sudo echo 1 > /sys/bus/pci/devices/0000:00:14.3/remove
sleep 3
sudo echo 1 > /sys/bus/pci/rescan
```

If it works, we'll attempt to automate it.

Is this at all a factor? [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi#about_dual-boot_with_windows_and_fast-boot_enabled)

---

### Post by janderson9er on 2020-04-12
Thank you again for your help!

I ended up having to run:
```

sudo echo 1 > sudo /sys/bus/pci/devices/0000:00:14.3/remove
sleep 3
sudo echo 1 > sudo /sys/bus/pci/rescan

```
No errors in output, please let me know if that is not accomplishing what we wanted. 

Pasting it exactly I was seeing:
```

sudo echo 1 > /sys/bus/pci/devices/0000:00:14.3/remove
bash: /sys/bus/pci/devices/0000:00:14.3/remove: Permission denied

```

I am not dual booting, unfortunately. Just Ubuntu.

In reading some more following links from your post, it does seem common that the wifi device itself may have crapped out. It's unfortunately onboard, so I can't easily swap it out, etc (though maybe that was obvious..)

Thank you again for your help, I really appreciate it.

---

### Post by chili555 on 2020-04-12
Please try:

```
sudo -i
echo 1 > /sys/bus/pci/devices/0000:00:14.3/remove
sleep 3
echo 1 > sudo /sys/bus/pci/rescan
exit
```> 
it does seem common that the wifi device itself may have crapped out. It's unfortunately onboard, so I can't easily swap it out, etc (though maybe that was obvious..)
Is this a laptop? Actually, they are pretty easy to replace. Either get the exact same device or beware of the dreaded whitelist: [https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/)

> At this time, it is known that some recent Lenovo, Toshiba, Dell, HP and Compaq follow this whitelisting practice. From my experience, it appears that Asus, Acer, and MSI don’t.

---

### Post by janderson9er on 2020-04-13
Thanks for quick reply!

Ran that, no errors, wifi still not available.

It is a desktop.

---

### Post by chili555 on 2020-04-13
I am a bit concerned here. At the outset of your thread, the driver loads the -34 version of the firmware:

> iwlwifi 0000:00:14.3: loaded firmware version [COLOR="#FF0000"]34[/COLOR].3125811985.0 op_mode iwlmvm

I suggested that you update the package linux-firmware and thereafter, we see:

> iwlwifi 0000:00:14.3: loaded firmware version 34.3125811985.0 op_mode iwlmvm

In other words, there was no change at all.

Intel's site says that the appropriate firmware is iwlwifi-9000-pu-b0-jf-b0. [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html)

I believe, however, that the latest linux-firmware package contains not only -34 but also -38, -41, -43 and -46. I wonder why the driver doesn't load the later and possibly better versions. 

Let's confirm that the latest package was installed properly:

```
sudo dpkg -s linux-firmware | grep Version

```
We hope we see 1.183.2.

Next, I'm interested in the exact version of the driver:

```
modinfo iwlwifi | grep -e filename -e 9000-pu-b0

```
Thanks.

---

### Post by janderson9er on 2020-04-13
Thanks!

> [COLOR=#000000]We hope we see 1.183.2.[/COLOR]

We do see "Version: 1.183.2"

```

modinfo iwlwifi | grep -e filename -e 9000-pu-b0
filename:       /lib/modules/4.15.0-96-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode

```

---

### Post by chili555 on 2020-04-13
> /lib/modules/[COLOR="#FF0000"]4.15[/COLOR].0-96-genericWe need a newer driver! Are you able to try out a live session for Ubuntu 19.10 or even 20.04 to see if the wireless works?

Or else, are you able to get a temporary internet connection so we can git one? git! Ha ha ha!

---

### Post by janderson9er on 2020-04-14
Can do! It's going to be a few days before I can get it, but I will post back here with results.

Thank you again for all your help!

---

