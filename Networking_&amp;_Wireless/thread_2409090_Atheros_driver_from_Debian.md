---
title: "Atheros driver from Debian"
date: 2018-12-27
forum: Networking &amp; Wireless
---

### Post by arvigeus on 2018-12-27
For some reason newer version of this driver does not work on my machine. I tried Debian and it was working perfectly. The package version there is [http://ftp.us.debian.org/debian/pool/non-free/f/firmware-nonfree/firmware-atheros_20161130-4_all.deb]("https://packages.debian.org/stretch/all/firmware-atheros/download")
How can I install it without breaking linux-firmware on Ubuntu?

---

### Post by chili555 on 2018-12-27
That is not the driver; it is, as the name implies, firmware that is needed by some drivers.

Please run:```
lspci -nnk | grep 0280 -A3
```Where is says, 'kernel driver in use' , run:```
modinfo <driver_name> | grep firmware
```Here is an example from my machine:```
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
	Kernel driver in use: [COLOR="#FF0000"]iwlwifi[/COLOR]
	Kernel modules: iwlwifi
```So I run:```
modinfo iwlwifi | grep firmware
```And I find:```

firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-38.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-38.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-38.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-38.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-38.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-38.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-38.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-38.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-38.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-38.ucode


```Then we'll examine the Debian package to see how it differs and copy over just the file we need.

---

### Post by arvigeus on 2018-12-27
```
[FONT=monospace][COLOR=#000000]Kernel driver in use: ath10k_pci[/COLOR][/FONT]
```

[FONT=monospace][COLOR=#000000]modinfo ath10k_pci | grep firmware              [/COLOR]
```
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA9377/hw1.0/board.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA9377/hw1.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-5.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw3.0/board-2.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw3.0/board.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw3.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-6.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw3.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-5.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw3.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-4.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw2.1/board-2.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw2.1/board.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw2.1/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-5.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA6174/hw2.1/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-4.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA9887/hw1.0/board-2.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA9887/hw1.0/board.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA9887/hw1.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-5.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/board-2.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/board.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-5.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-4.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-3.bin[/COLOR]
[COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]:       ath10k/QCA988X/hw2.0/[/COLOR][COLOR=#FF5454]**firmware**[/COLOR][COLOR=#000000]-2.bin[/COLOR]
```

[/FONT]

---

### Post by chili555 on 2018-12-27
Now may we see:```
lscpi -nnk | grep 0280 -A3
dmesg | grep ath
```

---

### Post by praseodym on 2018-12-28
You can update the firmware via

```
sudo apt-get install git
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Debian might use an even older driver with older firmware?!

---

### Post by arvigeus on 2018-12-28
> **praseodym said:**
> You can update the firmware via

I don't want to upgrade, I want to downgrade. After December 2017 my perfectly working driver drops connection constantly. Because Debian uses older version of it, it is the only distro that works for me. And when they update it: kaput.

lspci -nnk | grep 0280 -A3
```
[FONT=monospace][COLOR=#000000]05:00.0 Network controller [[/COLOR][COLOR=#FF5454]**0280**[/COLOR][COLOR=#000000]]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)[/COLOR]
        Subsystem: ASUSTeK Computer Inc. QCA6174 802.11ac Wireless Network Adapter [1043:86cd]
        Kernel driver in use: ath10k_pci
        Kernel modules: ath10k_pci
[/FONT]
```

dmesg | grep ath
```
[FONT=monospace][COLOR=#000000][  +0,081184] [/COLOR][COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: enabling device (0000 -> 0002)[/COLOR]
[  +0,000750] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0[/COLOR]
[  +0,189579] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Direct firmware load for [/COLOR][COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k/pre-cal-pci-0000:05:00.0.bin failed with error -2[/COLOR]
[  +0,000010] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Direct firmware load for [/COLOR][COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k/cal-pci-0000:05:00.0.bin failed with error -2[/COLOR]
[  +0,194123] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1043:86cd[/COLOR]
[  +0,000002] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0[/COLOR]
[  +0,000361] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: firmware ver WLAN.RM.4.4.1-00079-QCARMSWPZ-1 api 6 features wowlan,ignore-otp crc32 fd869beb[/COLOR]
[  +0,111845] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: board_file api 2 bmi_id N/A crc32 20d869c3[/COLOR]
[  +0,275424] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Unknown eventid: 118809[/COLOR]
[  +0,002938] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Unknown eventid: 90118[/COLOR]
[  +0,000678] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: htt-ver 3.47 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1[/COLOR]
[  +0,081530] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: EEPROM regdomain: 0x6c[/COLOR]
[  +0,000001] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: EEPROM indicates we should expect a direct regpair map[/COLOR]
[  +0,000001] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Country alpha2 being used: 00[/COLOR]
[  +0,000000] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]: Regpair used: 0x6c[/COLOR]
[  +0,089224] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0 wlp5s0: renamed from wlan0[/COLOR]
[  +0,125321] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Unknown eventid: 118809[/COLOR]
[  +0,002936] [COLOR=#FF5454]**ath**[/COLOR][COLOR=#000000]10k_pci 0000:05:00.0: Unknown eventid: 90118[/COLOR]
[/FONT]
```

---

### Post by praseodym on 2018-12-28
> ```
[  +0,189579] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:05:00.0.bin failed with error -2
[  +0,000010] ath10k_pci 0000:05:00.0: Direct firmware load for ath10k/cal-pci-0000:05:00.0.bin failed with error -2
```

Check if the Debian firmware file contains these?! The FW blob doesn't.

---

### Post by arvigeus on 2018-12-28
> **praseodym said:**
> Check if the Debian firmware file contains these?! The FW blob doesn't.
pre-cal-pci.bin
cal-pci.bin
No. Nothing remotely connected

---

### Post by chili555 on 2018-12-29
It appears that the driver is downloading files from the directory /lib/firmware/ath10k/QCA6174/hw3.0. My directory, using the latest version of linux-firmware, shows:```
drwxr-xr-x 2 root root   4096 Nov 29 11:11 .
drwxr-xr-x 4 root root   4096 Apr 21  2018 ..
-rw-r--r-- 1 root root 551128 Apr 25  2018 board-2.bin
-rw-r--r-- 1 root root   8124 Mar 29  2017 board.bin
-rw-r--r-- 1 root root 733784 Mar 29  2017 firmware-4.bin
-rw-r--r-- 1 root root 730788 Nov  6 10:42 firmware-6.bin
-rw-r--r-- 1 root root  79689 Mar 29  2017 notice_ath10k_firmware-4.txt
-rw-r--r-- 1 root root  78564 Nov  6 10:42 notice_ath10k_firmware-6.txt

```Extracting the deb file you linked above shows:```
drwxr-xr-x 2 chili chili   4096 Oct 13 15:27 .
drwxr-xr-x 4 chili chili   4096 Oct 13 15:27 ..
-rw-r--r-- 1 chili chili 337204 Oct 13 15:27 board-2.bin
-rw-r--r-- 1 chili chili   8124 Oct 13 15:27 board.bin
-rw-r--r-- 1 chili chili 733784 Oct 13 15:27 firmware-4.bin

```As you see, there are differences.

I suggest that you back up the current files so that we can revert if needed:```
cd /lib/firmware/ath10k/QCA6174/
sudo mkdir backups
sudo mv hw3.0/*  backups
```Now, please download the deb file you linked. By default it will go to your Downloads directory. Find it and right-click it and select 'Extract Here.' A new directory will be created called firmware-atheros_20161130-4_all. Within it will be a compressed file data.tar.xz. Right-click it and select 'Extract Here.'

Now, back to the terminal:

```
sudo cp ~/Downloads/firmware-atheros_20161130-4_all/data/lib/firmware/ath10k/QCA6174/hw3.0/*   /lib/firmware/ath10k/QCA6174/hw3.0
```Verify that the files are there:

```
ls -al /lib/firmware/ath10k/QCA6174/hw3.0
```You should see only:

```
total 1068
drwxr-xr-x 2 chili chili   4096 Oct 13 15:27 .
drwxr-xr-x 4 chili chili   4096 Oct 13 15:27 ..
-rw-r--r-- 1 chili chili 337204 Oct 13 15:27 board-2.bin
-rw-r--r-- 1 chili chili   8124 Oct 13 15:27 board.bin
-rw-r--r-- 1 chili chili 733784 Oct 13 15:27 firmware-4.bin
```Reboot and tell us if the performance has improved.

---

### Post by arvigeus on 2019-01-09
Sorry for the very late reply, but I had to test it to make sure it is working for real (in normal circumstances wifi dropping was very inconsistent and not happening all the time). Confirming that **@chili555**'s solution works. Hopefully one day they will fix the newer drivers.

---

### Post by praseodym on 2019-01-09
Hi Chili,

would this git fit in here?

[https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)

---

### Post by chili555 on 2019-01-09
> **praseodym said:**
> Hi Chili,

would this git fit in here?

[https://github.com/kvalo/ath10k-firmware](https://github.com/kvalo/ath10k-firmware)I don't know for sure. The files are a bit different.```

chili@T440p:~/Desktop/Forum/kvalo/ath10k-firmware/QCA6174/hw3.0$ ls -al
total 1388
drwxr-xr-x 6 chili chili   4096 Jan  9 18:01 .
drwxr-xr-x 4 chili chili   4096 Jan  9 18:01 ..
drwxr-xr-x 2 chili chili   4096 Jan  9 18:01 4.4
drwxr-xr-x 2 chili chili   4096 Jan  9 18:01 4.4.1
drwxr-xr-x 2 chili chili   4096 Jan  9 18:01 4.4.1.c1
drwxr-xr-x 2 chili chili   4096 Jan  9 18:01 4.4.1.c2
-rw-r--r-- 1 chili chili 567608 Jan  9 18:01 board-2.bin
-rw-r--r-- 1 chili chili   8124 Jan  9 18:01 board.bin
-rw-r--r-- 1 chili chili 733784 Jan  9 18:01 firmware-4.bin_WLAN.RM.2.0-00180-QCARMSWPZ-1
-rw-r--r-- 1 chili chili  79801 Jan  9 18:01 notice.txt_WLAN.RM.2.0-00180-QCARMSWPZ-1

```firmware-4.bin, after it is renamed, appears to be the same as above. board-2.bin is different.

As OP hasn't shared dmesg with us, we are unsure what firmware loads and works. Until we have more information, I don't think we know for sure.

At least for me, ath10k_pci is about guesswork and luck.

---

### Post by jaspolino on 2019-08-03
+++Straightforward simple solution+++
Using the above mentioned repository github.com/kvalo/ath10k-firmware
i simply got placed the appropriate binary in the /lib/firmware folder.
Keep in mind you might need to change "ath10k" or "QCA6174" to your value.

```

dmesg | grep ath10k #you can replace ath10k of course
# it will read something like "failed to load firmware ath10k/QCA6174/hw3.0/firmware-6.bin     #<- remember this path

# if there is no folder for ath10k create it
cd /lib/fimware
mkdir ath10k

cd
git clone github.com/kvalo/ath10k-firmware
cd ath10k-firmware/
# pick the right firmware 
cd QCA6174/hw3.0
# there are differemt versions directories, i just took the newest one
cd 4.4
# now copy one of these to the location where the kernel expects it to be and rename it
cp firmware-6.bin_WLAN.RM.4.4-00022-QCARMSWPZ-2 /lib/firmware/ath10k/QCA6174/hw3.0/firmware-6.bin


```
see [https://wireless.wiki.kernel.org/en/users/Drivers/ath10k/firmware](https://wireless.wiki.kernel.org/en/users/Drivers/ath10k/firmware) for the explaination of the different binaries.
it worked immediately for me

---

