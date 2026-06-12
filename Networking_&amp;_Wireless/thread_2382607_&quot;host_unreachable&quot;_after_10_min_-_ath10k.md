---
title: "&quot;host unreachable&quot; after 10 min - ath10k QCA6174 4.13.0-26-generic (ubuntu 16.04)"
date: 2018-01-15
forum: Networking &amp; Wireless
---

### Post by h3ct0r2 on 2018-01-15
Hi,

I'm having problems with my wireless card ath10k QCA6174 on Ubuntu 16.04.
The card was behaving as normal for several months and after the last upgrade to 4.13.0-26-generic my wifi connection started to give messages like "Host unreachable" to the gateway, but the computer was connected to the wifi hotspot and no errors were logged on dmesg, /var/log/syslog or /var/log/kern.log.

I did update my drivers and restart using the Kvalo's firmware ([https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)) but it didn't stop the connection problems.

After getting back to 4.10.0-42-generic the problems went away. After testing I modified my grub config to always load that specific kernel.

Can I report this as a bug on launchpad? 

The wifi report is on pastebin: [https://pastebin.com/6UuQBesA](https://pastebin.com/6UuQBesA)

Thanks!

---

### Post by andrebrait on 2018-01-15
> **h3ct0r2 said:**
> Hi,

I'm having problems with my wireless card ath10k QCA6174 on Ubuntu 16.04.
The card was behaving as normal for several months and after the last upgrade to 4.13.0-26-generic my wifi connection started to give messages like "Host unreachable" to the gateway, but the computer was connected to the wifi hotspot and no errors were logged on dmesg, /var/log/syslog or /var/log/kern.log.

I did update my drivers and restart using the Kvalo's firmware ([https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)) but it didn't stop the connection problems.

After getting back to 4.10.0-42-generic the problems went away. After testing I modified my grub config to always load that specific kernel.

Can I report this as a bug on launchpad? 

The wifi report is on pastebin: [https://pastebin.com/6UuQBesA](https://pastebin.com/6UuQBesA)

Thanks!

This has already been fixed upstream, it seems.

There's a bug report here: [https://bugs.launchpad.net/bugs/1743279](https://bugs.launchpad.net/bugs/1743279)
Please check that it affects you as well in the bug report to contribute so Ubuntu developers will give it the proper attention.

Also, updating the firmware should fix it. Can you please tell me how you updated the firmware? Can you please post the output of the following command?

```
ls -lha /lib/firmware/ath10k/QCA6174/hw3.0/
```

Thank you!

---

### Post by h3ct0r2 on 2018-01-15
Hi @andrebfait,

Yes it seems like its the same bug, thank you for locating it.

The result of the command is:
```

[FONT=courier new]&#10140; ~ ls -lha /lib/firmware/ath10k/QCA6174/hw3.0/[/FONT]
[FONT=courier new]total 2,9M[/FONT]
[FONT=courier new]drwxr-xr-x 5 root root 4,0K Jan 15 01:24 .[/FONT]
[FONT=courier new]drwxr-xr-x 4 root root 4,0K Fev 15 2017 ..[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4.1[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4.1.c1[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 539K Jan 15 01:24 board-2.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 8,0K Jan 15 01:24 board.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 717K Dez 1 2016 firmware-4.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 717K Jan 15 01:24 firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 695K Nov 15 19:44 firmware-6.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 78K Dez 1 2016 notice_ath10k_firmware-4.txt[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 81K Nov 15 19:44 notice_ath10k_firmware-6.txt[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 78K Jan 15 01:24 notice.txt_WLAN.RM.2.0-00180-QCARMSWPZ-1[/FONT]
```

The upgrade process was simply to backup and delete the */lib/firmware/ath10k/ *folder and then replace it with the ath10k folder from [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware). The upgrade process was ok?

Edit: I didn't notice that you were the one that created the bug report!

---

### Post by andrebrait on 2018-01-15
> **h3ct0r2 said:**
> Hi @andrebfait,

Yes it seems like its the same bug, thank you for locating it.

The result of the command is:
```

[FONT=courier new]&#10140; ~ ls -lha /lib/firmware/ath10k/QCA6174/hw3.0/[/FONT]
[FONT=courier new]total 2,9M[/FONT]
[FONT=courier new]drwxr-xr-x 5 root root 4,0K Jan 15 01:24 .[/FONT]
[FONT=courier new]drwxr-xr-x 4 root root 4,0K Fev 15 2017 ..[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4.1[/FONT]
[FONT=courier new]drwxr-xr-x 2 root root 4,0K Jan 15 01:24 4.4.1.c1[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 539K Jan 15 01:24 board-2.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 8,0K Jan 15 01:24 board.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 717K Dez 1 2016 firmware-4.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 717K Jan 15 01:24 firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 695K Nov 15 19:44 firmware-6.bin[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 78K Dez 1 2016 notice_ath10k_firmware-4.txt[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 81K Nov 15 19:44 notice_ath10k_firmware-6.txt[/FONT]
[FONT=courier new]-rw-r--r-- 1 root root 78K Jan 15 01:24 notice.txt_WLAN.RM.2.0-00180-QCARMSWPZ-1[/FONT]
```

The upgrade process was simply to backup and delete the */lib/firmware/ath10k/ *folder and then replace it with the ath10k folder from [https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware). The upgrade process was ok?

Edit: I didn't notice that you were the one that created the bug report!

Oh, that won't work, unfortunately. The folder structure in kvalo's repository isn't the same as the one required for the firmware to be loaded, etc. so what you've done has no effect at all (the old firmware-6.bin is what's being loaded there).

Delete the ath10k folder and reinstall the linux-firmware package, as per the following commands (which need to be issued without any reboots or interruption in between).

```
sudo rm -rf /lib/firmware/ath10k/
sudo apt update && sudo apt install linux-firmware --reinstall
```

Then download and replace the following files (which are the ones kvalo has committed when he fixed the bug) (the commands below will already replace the files where they belong, so it's all you need to do):

```
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw3.0/board-2.bin -O /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA6174/hw3.0/firmware-6.bin -O /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin
```

Alternatively, you can grad the firmware-6.bin file form kvalo's repository directly:

```
sudo wget https://github.com/kvalo/ath10k-firmware/raw/master/QCA6174/hw3.0/4.4.1/firmware-6.bin_WLAN.RM.4.4.1-00051-QCARMSWP-1 -O /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin

```

Now reboot.

The firmware files always need to have the correct names in order to be loaded properly.

EDIT: In order to check which firmware was loaded, use the following command:

```
dmesg | grep ath10k | grep firmware
```

It'll output something like 

> [   14.941461] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411

For the bug to be fixed it needs to be at least this version or some newer one. The one that ships with Ubuntu as of now is WLAN.RM.4.4-00022-QCARMSWPZ-2, and the fix was introduced in WLAN.RM.4.4.1-00051-QCARMSWP-1. I've also tested WLAN.RM.4.4.1-00065-QCARMSWP-1 and WLAN.RM.4.4.1-00079-QCARMSWPZ-1 and they work as well.

---

### Post by h3ct0r2 on 2018-01-16
Hi @andrebrait, thank you for the detailed response!

Doing the correct driver update procedure worked for the newest kernel installed on my machine! (4.13.0-26-generic)

The command ```
[COLOR=#000000][FONT=&amp]dmesg | grep ath10k | grep firmware[/FONT][/COLOR]
``` returned:

> [   14.740467] ath10k_pci 0000:02:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411

So now we have the same working version. Maybe it is good to add a link to this thread on the bug report? That way more people can reach the fix while its deployed on the official version.

Thanks again, my wifi is working perfectly now!

---

### Post by andrebrait on 2018-01-16
> **h3ct0r2 said:**
> Hi @andrebrait, thank you for the detailed response!

Doing the correct driver update procedure worked for the newest kernel installed on my machine! (4.13.0-26-generic)

The command ```
[COLOR=#000000][FONT=&amp]dmesg | grep ath10k | grep firmware[/FONT][/COLOR]
``` returned:



So now we have the same working version. Maybe it is good to add a link to this thread on the bug report? That way more people can reach the fix while its deployed on the official version.

Thanks again, my wifi is working perfectly now!

Great! You're welcome ;)

I posted a quick one-liner as a workaround in the bug report.

---

