---
title: "No network devices available"
date: 2017-10-27
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2017-10-27
Hi, I'm the same person from this thread: [https://ubuntuforums.org/showthread.php?t=2316533](https://ubuntuforums.org/showthread.php?t=2316533). I have an Acer laptop running Ubuntu 16.04 whose wireless card has traditionally not wanted to find network connections. Recently I accidentally hit the power button on the side of the laptop, shutting it off without a proper shutdown. Since then, I've had a "No network devices available" status and no wifi. I've entered some standard commands you all taught me in an attempt to figure out what's going on.

```
dmesg | grep ath
modinfo ath10k_pci
lspci -n | egrep '0200|0280' 

```
all return nothing.
```

sudo modprobe ath10k
```

returns
```

"modprobe: FATAL: Module ath10k not found in directory /lib/modules/4.4.0-97-generic"

```
But ```
locate ath
``` shows all the files you'd expect to live in 

```
/lib/firmware/ath10k
```

do. What can I do to get back my wireless?

---

### Post by praseodym on 2017-10-28
Please show
```

dpkg -i linux-image-* | grep ii
```

---

### Post by jdkcarlson on 2017-10-28
I get this.

```
dpkg: error encountered processing archive linux-image-* (--install):
cannot access archive: No such file or directory 
Errors were encountered while processing:
linux-image-* 
```

---

### Post by jeremy31 on 2017-10-28
I would try this ```
sudo apt-get install --reinstall linux-image-extra-4.4.0-97-generic
```
Reboot

---

### Post by praseodym on 2017-10-28
Sorry, typo, its 
```

dpkg -l linux-image-* | grep ii
```

---

### Post by jdkcarlson on 2017-10-28
Hi and thanks again, Jeremy.

I was incorrect earlier about "modinfo ath10k_pci"; that returns things normally.

I reinstalled and rebooted.

No network devices are available, still.

"dmesg | grep ath" still yields nothing.

"lspci -n | egrep '0200|0280" returns what I think is my modem, "01:00.0 0280: 168c:003e (rev 32)".

"sudo dpkg -i linux-image-* | grep ii" returns the same errors as previously.

---

### Post by jeremy31 on 2017-10-28
See the wireless script link in my signature and post results, praseodym did post that "dpkg -i" was supposed to be "dpkg -l" small L rather than small I for that command

---

### Post by praseodym on 2017-10-28
it is "-l" which is a L, not an i (I)

---

### Post by jdkcarlson on 2017-10-28
My eyesight is apparently going, sorry. Here's the result: [https://imagebin.ca/v/3fLrJjJQdFzt]("https://imagebin.ca/v/3fLrJjJQdFzt"). I'll run the script.

---

### Post by jdkcarlson on 2017-10-28
Hi, I've run the script. It posted to here:

[http://paste.ubuntu.com/25839462/](http://paste.ubuntu.com/25839462/)

---

### Post by jeremy31 on 2017-10-29
See if it works in an older kernel, press and hold left shift key during boot until Grub menu appears, scroll to Advanced options, then scroll to an older kernel, likely use down arrow button 3 times

---

### Post by praseodym on 2017-10-29
Lets see
```

sudo modprobe -v ath10k_pci
dmesg | grep ath
```

---

### Post by jdkcarlson on 2017-10-29
Jeremy, yes, it works on .96
What on earth is going on?

---

### Post by jdkcarlson on 2017-10-29
praseodym: 
```
sudo modprobe -v ath10k_pci
``` returns nothing.
```
dmesg | grep ath
``` on the 4.4.0-96 Jeremy had me switch to, gives this:
```
[    2.009287] ath10k_pci 0000:01:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.258888] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    4.450845] ath10k_pci 0000:01:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 11ad:0807) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 5 bdapi 2 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.450849] ath10k_pci 0000:01:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.518062] ath: EEPROM regdomain: 0x6c
[    4.518064] ath: EEPROM indicates we should expect a direct regpair map
[    4.518066] ath: Country alpha2 being used: 00
[    4.518067] ath: Regpair used: 0x6c
[    4.524745] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   16.347086] ath: EEPROM regdomain: 0x807c
[   16.347089] ath: EEPROM indicates we should expect a country code
[   16.347090] ath: doing EEPROM country->regdmn map search
[   16.347091] ath: country maps to regdmn code: 0x3a
[   16.347093] ath: Country alpha2 being used: CA
[   16.347093] ath: Regpair used: 0x3a
[   16.347095] ath: regdomain 0x807c dynamically updated by country IE

```

The computer is, however, online. I'm sending it from this computer.

---

### Post by jeremy31 on 2017-10-29
I think it is what praseodym and I both suspected but your results showed that we were wrong.  The linux-image-extra package contains the wireless drivers.  Use file manager to navigate through /lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/ 
There should be 20 directories and 13 files

---

### Post by jdkcarlson on 2017-10-29
Hi Jeremy, what did you suspect? I navigated and counted, and there are indeed 20 subdirectories and 13 files in that directory.

---

### Post by praseodym on 2017-10-29
Firmware is not loaded correctly, see "dmesg":

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by jeremy31 on 2017-10-29
Also check /lib/modules/4.4.0-97-generic/kernel/drivers/net/wireless/ath/ath10k see if ath10k_pci and ath10k_core are there

---

### Post by jdkcarlson on 2017-10-29
praseodym. Did this. Had to install git. No complaints from the system though. Did you want me to cd to 

```
/usr/share/documents/linux-firmware
```

? Because that's the only matching location I found. Then I did the cp you asked. There was no feedback. I restarted to 4.4.0-97 and had no wifi, so I'm typing this from 4.4.0-96 again.

---

### Post by jdkcarlson on 2017-10-29
Jeremy, they're there. Those filenames with the extension ".ko"

---

### Post by jeremy31 on 2017-10-29
I would just stick with the 96 kernel until something newer than 97 comes out

---

### Post by jdkcarlson on 2017-10-29
Okay, I'll do that, but two questions:

1. Is there way to make that the default so that I can avoid the extra effort every time I reboot?
2. The wireless card was working fine in 97 until that fateful day I bumped the power button, at which point it just stopped. What happened?

---

### Post by jeremy31 on 2017-10-29
Check ```
sudo apt-get remove --dry-run linux-image-4.4.0-97-generic
```
Check to make sure it only removes linux-image linux-image-extra and linux-headers for 4.4.0-97 if that is all that is removed, then
```
sudo apt-get remove  linux-image-4.4.0-97-generic
```
Then the 96 kernel will be default

---

### Post by jdkcarlson on 2017-10-29
I get this:

```
The following packages were automatically installed and are no longer required:
  libllvm3.8 libmircommon5 libsnapd-glib1 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-generic
  linux-image-4.4.0-31-generic linux-image-4.4.0-93-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-93-generic
  linux-signed-image-4.4.0-93-generic snapd-login-service thermald
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-image-4.4.0-97-generic
  linux-image-extra-4.4.0-97-generic linux-image-generic linux-signed-generic
  linux-signed-image-4.4.0-97-generic linux-signed-image-generic
0 upgraded, 0 newly installed, 7 to remove and 22 not upgraded.
Remv linux-generic [4.4.0.97.102]
Remv linux-signed-generic [4.4.0.97.102]
Remv linux-signed-image-generic [4.4.0.97.102]
Remv linux-signed-image-4.4.0-97-generic [4.4.0-97.120]
Remv linux-image-generic [4.4.0.97.102]
Remv linux-image-extra-4.4.0-97-generic [4.4.0-97.120]
Remv linux-image-4.4.0-97-generic [4.4.0-97.120]

```

Does this look right, or will I be crippling my system?

---

### Post by jeremy31 on 2017-10-29
That looks safe to run the second command

---

### Post by jdkcarlson on 2017-10-29
Thanks, done. Looks like it freed 220MB of disk space!

Uh-oh:

```
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
```

Will this require action?

---

### Post by jeremy31 on 2017-10-29
Try ```
sudo apt-get install  linux-image-4.4.0-97-generic
```
See if any strange errors show up

---

### Post by jdkcarlson on 2017-10-29
No errors

---

### Post by jeremy31 on 2017-10-29
Try a reboot and see if wifi works in 4.4.0-97 this time

---

### Post by jdkcarlson on 2017-10-29
It detects the card and connects to the network, but no data makes it through. Googling and pinging 192.168.1.1 fails. The same holds in 4.4.0-96 too now, actually.

---

### Post by jeremy31 on 2017-10-29
Try ```
sudo dpkg-reconfigure resolvconf
``` choose yes to enable dynamic updates and reboot

---

### Post by jdkcarlson on 2017-10-29
I've done this. Same problem, in both kernel versions

---

### Post by jeremy31 on 2017-10-29
I really don't know at this point unless an even older kernel still works and that would be even stranger unless dkms is involved, post results for
```
dkms status
```

---

### Post by jdkcarlson on 2017-10-29
dkms status
returns nothing.

If I uninstall 97, is there a chance 96 will work again? I'm feeling dumb for reinstalling it when I had wireless working. I feel like Icarus: just flew too close to the sun.

---

### Post by jeremy31 on 2017-10-30
It is possible that removing 97 might allow 96 to work as I am not sure how doing anything with 97 could have affected 96

---

### Post by praseodym on 2017-10-30
Please run the wireless script again

---

