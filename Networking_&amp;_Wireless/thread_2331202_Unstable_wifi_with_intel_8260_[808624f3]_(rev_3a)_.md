---
title: "Unstable wifi with intel 8260 [8086:24f3] (rev 3a) on ubuntu 16.04 runnung on Lenovo"
date: 2016-07-19
forum: Networking &amp; Wireless
---

### Post by dahumph on 2016-07-19
Hi, I have a brand new Lenovo P50 with intel 8260 wifi. Using ubuntu  16.04 with kernel 4.4.0.31 generic. wifi often stops working or simply shows no  networks in network mnager. from time to time the up and down arrows are  display in the network manager, even with no network cable connected. 
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware*.deb
```

has been done. 

editing ```

/etc/default/crda
```
to my reg domain has no effect, still 

```

sudo iw reg get
```

shows

```

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

using 

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

solves the issue. so I tried to make it permanent with 

```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```

after reboot wifi n mode seems to be disabled, howeve, the problem comes back. only doing a manual 

```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

helps as long as I do do not reboot.

Any help is appreciated to establish a permanent fix

---

### Post by jeremy31 on 2016-07-19
You will likely have to wait for updates to package network-manager and its counterparts for this issue to be fixed

---

### Post by Keith_Helms on 2016-07-20
jeremy31, I'm having similar problems with the Intel 7260 card.  Is this a known bug and a fix is being worked on?

---

### Post by dahumph on 2016-07-20
thx for the reply, yes, will probably have to wait. but any idea how i can automate the fix i figured out in my post. its sort of annoying to every time after reboot unload and load back the kernel modules...

---

### Post by jeremy31 on 2016-07-21
This is  a known bug and it is in the process of being fixed.  I have Ubuntu 16.04 on a couple laptops and am not affected by the bug

---

### Post by Keith_Helms on 2016-07-21
Is the bug specifically in the Intel iwlwifi driver/firmware or is it in Network Manager?  I've seen some suggestions to use wicd instead of network manager and was wondering if that would do any good.

---

