---
title: "Bluetooth on Z97 Pro (wifi ac)?"
date: 2016-02-08
forum: Networking &amp; Wireless
---

### Post by eezacque on 2016-02-08
Decided to give Bluetooth a try, but hcitool dev shows no devices.
However, dmesg shows
[    3.062074] Bluetooth: Core ver 2.20
[    3.062093] Bluetooth: HCI device and connection manager initialized
[    3.062095] Bluetooth: HCI socket layer initialized
[    3.062096] Bluetooth: L2CAP socket layer initialized
[    3.062099] Bluetooth: SCO socket layer initialized
[    3.085978] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0b05-17cf.hcd failed with error -2
[    3.085980] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0b05-17cf.hcd not found


Any clue?

---

### Post by chili555 on 2016-02-08
This is highly experimental. It may or may not help and another of my colleagues may jump in and propose a better method, but please try, with a working internet connection:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/geyslan/configs.git
cd configs/lib/firmware/brcm
sudo cp BCM*.hcd  /lib/firmware/brcm 
```Reboot and tell us if the bluetooth is working. If not, post again:```
dmesg | grep -i blue
```

---

### Post by eezacque on 2016-02-11
> **chili555 said:**
> This is highly experimental. It may or may not help and another of my colleagues may jump in and propose a better method, but please try, with a working internet connection:```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/geyslan/configs.git
cd configs/lib/firmware/brcm
sudo cp BCM*.hcd  /lib/firmware/brcm 
```Reboot and tell us if the bluetooth is working. If not, post again:```
dmesg | grep -i blue
```

Thanks, that is one step in the right direction.
However, I was able to discover my phone and pair it once, got a message 'connection failed', and since then, I have not been able to discover it.

dmesg gives:
[    2.727352] Bluetooth: Core ver 2.20
[    2.727368] Bluetooth: HCI device and connection manager initialized
[    2.727370] Bluetooth: HCI socket layer initialized
[    2.727372] Bluetooth: L2CAP socket layer initialized
[    2.727376] Bluetooth: SCO socket layer initialized
[    2.757913] bluetooth hci0: Direct firmware load for brcm/BCM20702A0-0b05-17cf.hcd failed with error -2
[    2.757917] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0b05-17cf.hcd not found
[    4.607806] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.607808] Bluetooth: BNEP filters: protocol multicast
[    4.607811] Bluetooth: BNEP socket layer initialized
[    4.618842] Bluetooth: RFCOMM TTY layer initialized
[    4.618846] Bluetooth: RFCOMM socket layer initialized
[    4.618849] Bluetooth: RFCOMM ver 1.11
[ 6257.505437] Bluetooth: Failed to start inquiry: status 18
[ 6262.627432] Bluetooth: Failed to start inquiry: status 18

Any clue how to proceed?

---

### Post by jeremy31 on 2016-02-11
Post ```
ls /lib/firmware/brcm
```

I think it is strange that it worked once and now the firmware is simply not found

---

### Post by eezacque on 2016-02-12
I agree. However, the experimental patch from chili555 copies BCM20702A1-0b05-17cf.hcd, while dmesg signals BCM20702A0-0b05-17cf.hcd.
Without chili555's patch I couldn't even activate Bluetooth, with the patch I have been able to discover and pair my phone once, was able to discover it a few times more, but have never seen a successful connection.

---

### Post by jeremy31 on 2016-02-12
Post ```
ls /lib/firmware/brcm
```

---

### Post by eezacque on 2016-02-13
$ ls /lib/firmware/brcm 
BCM20702A1-0b05-17cf.hcd  brcmfmac43143.bin         brcmfmac43241b4-sdio.bin  brcmfmac4335-sdio.bin
bcm4329-fullmac-4.bin     brcmfmac43143-sdio.bin    brcmfmac4329-sdio.bin     brcmfmac43362-sdio.bin
bcm43xx-0.fw              brcmfmac43236b.bin        brcmfmac4330-sdio.bin     brcmfmac4354-sdio.bin
bcm43xx_hdr-0.fw          brcmfmac43241b0-sdio.bin  brcmfmac4334-sdio.bin     brcmfmac4356-pcie.bin

---

### Post by chili555 on 2016-02-13
> **eezacque said:**
> I agree. However, the experimental patch from chili555 copies BCM20702A1-0b05-17cf.hcd, while dmesg signals BCM20702A0-0b05-17cf.hcd.
Without chili555's patch I couldn't even activate Bluetooth, with the patch I have been able to discover and pair my phone once, was able to discover it a few times more, but have never seen a successful connection.Indeed. We downloaded and installed BCM20702A[COLOR="#FF0000"]1[/COLOR]xx and it really wants BCM20702A[COLOR="#FF0000"]0[/COLOR]xx.

Please try this and remember the disclaimer:> This is highly experimental. It may or may not help and another of my colleagues may jump in and propose a better method, but please try, with a working internet connection:Please do:```
cd /lib/firmware/brcm
sudo wget https://gist.github.com/zamabe/f43656760b08c5818d64/raw/0f16543f4089ac597b23e42348997c0d70014b9c/lib%2520firmware%2520brcm%2520BCM20702A0-0b05-17cf.hcd
sudo mv lib%20firmware%20brcm%20BCM20702A0-0b05-17cf.hcd BCM20702A0-0b05-17cf.hcd 

```Now check to make sure you have the correct file:```
ls -al
```You should see:```
drwxr-xr-x  2 root root   4096 Feb 13 09:29 .
drwxr-xr-x 75 root root  32768 Feb  5 10:49 ..
-rw-r--r--  1 root root 147122 Feb 13 09:27 [COLOR="#FF0000"]BCM20702A0-0b05-17cf.hcd[/COLOR]
-rw-r--r--  1 root root  35127 Feb  8 16:07 BCM20702A1-0b05-17cf.hcd
-rw-r--r--  1 root root 269595 Nov 24  2014 bcm4329-fullmac-4.bin
-rw-r--r--  1 root root  96224 Dec  1  2014 bcm43xx-0.fw
-rw-r--r--  1 root root    180 Dec  1  2014 bcm43xx_hdr-0.fw
<snip>
```Reboot and tell us if it's working as expected.

---

### Post by eezacque on 2016-02-21
Followed your instructions, to no avail:
[Sun Feb 21 11:27:42 2016] Bluetooth: Core ver 2.20
[Sun Feb 21 11:27:42 2016] Bluetooth: HCI device and connection manager initialized
[Sun Feb 21 11:27:42 2016] Bluetooth: HCI socket layer initialized
[Sun Feb 21 11:27:42 2016] Bluetooth: L2CAP socket layer initialized
[Sun Feb 21 11:27:42 2016] Bluetooth: SCO socket layer initialized
[Sun Feb 21 11:27:42 2016] Bluetooth: hci0: BCM: patching hci_ver=06 hci_rev=1000 lmp_ver=06 lmp_subver=220e
[Sun Feb 21 11:27:44 2016] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[Sun Feb 21 11:27:44 2016] Bluetooth: BNEP filters: protocol multicast
[Sun Feb 21 11:27:44 2016] Bluetooth: BNEP socket layer initialized
[Sun Feb 21 11:27:44 2016] Bluetooth: hci0 command 0x3030 tx timeout
[Sun Feb 21 11:27:52 2016] Bluetooth: hci0: BCM: patch command 3030 failed (-110)
[Sun Feb 21 11:27:54 2016] Bluetooth: hci0 command 0x0c03 tx timeout
[Sun Feb 21 11:28:02 2016] Bluetooth: hci0: HCI_OP_RESET failed (-110)

---

### Post by chili555 on 2016-02-21
I'm running low on ideas. Is this a dual-boot with Windows? Does the bluetooth work there?

May we see:```
lsusb
```

---

### Post by jeremy31 on 2016-02-21
Might be a slight issue with that firmware.
```
wget https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd
sudo cp fw-0b05-17cf.hcd /lib/firmware/brcm/BCM20702A0-0b05-17cf.hcd
```

Shutdown the computer and do a cold boot

---

### Post by eezacque on 2016-02-22
> **chili555 said:**
> I'm running low on ideas. Is this a dual-boot with Windows? Does the bluetooth work there?


This is no dual-boot system.

> 
May we see:```
lsusb
```

$ lsusb
Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 006: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 003 Device 005: ID 0000:0538  
Bus 003 Device 003: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Let me add that, since the latest 'fix', the Bluetooth settings no longer show a Bluetooth adapter.

---

### Post by jeremy31 on 2016-02-22
You might want to pull the wifi card and reseat as lsusb results don't show the bluetooth, unless it is an USB bluetooth dongle.

---

### Post by eezacque on 2016-02-22
> **jeremy31 said:**
> You might want to pull the wifi card and reseat as lsusb results don't show the bluetooth, unless it is an USB bluetooth dongle.

There is no wifi card that can be reseated, and I don't think it is a hardware problem caused by installing experimental firmware.

---

### Post by jeremy31 on 2016-02-22
It isn't really experimental firmware.  The file I had you try was used first used about a year ago
What kernel are you using ```
uname -a
```

---

### Post by eezacque on 2016-02-22
> **jeremy31 said:**
> It isn't really experimental firmware.  The file I had you try was used first used about a year ago
What kernel are you using ```
uname -a
```

You're going a little too fast. I tried chili555's suggestion, which was flagged as experimental.
Tomorrow, I will try your suggestion, and post the results here.

---

### Post by jeremy31 on 2016-02-22
> **eezacque said:**
> You're going a little too fast. I tried chili555's suggestion, which was flagged as experimental.
Tomorrow, I will try your suggestion, and post the results here.

Chili555's file shows the exact md5sum as my file so it should make no difference

---

### Post by eezacque on 2016-02-24
A cold boot doesn't change a thing.
Running kernel 3.19.0-47-generic.

---

### Post by eezacque on 2016-04-08
> **eezacque said:**
> A cold boot doesn't change a thing.
Running kernel 3.19.0-47-generic.

Upgraded to Ubuntu 15.10 (kernel 4.2.0-35-generic).
Still no luck.

---

### Post by eezacque on 2016-05-09
Upgraded to Ubuntu 15.10, and am able to successfully discover and pair my phone.
I can send files to my phone, but cannot possibly browse it.
Also, the 'Connection' slide in the Bluetooth settings panel shows OFF, and it is greyed out.

So, I am a few steps further, and would like to move one more step.
Any help is appreciated.

---

