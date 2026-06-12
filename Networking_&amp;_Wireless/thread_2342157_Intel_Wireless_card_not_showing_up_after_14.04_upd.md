---
title: "Intel Wireless card not showing up after 14.04 update"
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by ahmeds93 on 2016-11-04
[B]SOLVED
It was a problem with "Secure Boot"
Please refer to the solution here "[/B][http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)"

Hello all,
I just got my Dell Inspiration 15 and it had ubuntu installed on it by default, I updated it by running the following:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```
It ran fine, finished updating over Wifi and asked me to restart, after the reset, My wifi is not working and not even showing up in ifconfig or anywhere.

The output of :
```
lspci -nn | grep 280
lsusb
rfkill list all
```

```
batee5a@Bat335a:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
batee5a@Bat335a:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 1bcf:2b90 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
batee5a@Bat335a:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

I've tried solutions in other threads and non worked thats why I'm posting this here as a new thread, Any help please?

EDIT: Output of further commands
```
batee5a@Bat335a:~$ sudo modprobe iwlwifi
modprobe: ERROR: could not insert 'iwlwifi': Required key not available
batee5a@Bat335a:~$ dmesg | grep iwl
batee5a@Bat335a:~$ 
```

---

### Post by chili555 on 2016-11-04
What is the result of:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by ahmeds93 on 2016-11-04
> **chili555 said:**
> What is the result of:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

There you go, also result is edited in topic.

```
batee5a@Bat335a:~$ sudo modprobe iwlwifi[sudo] password for batee5a: 
modprobe: ERROR: could not insert 'iwlwifi': Required key not available
batee5a@Bat335a:~$ dmesg | grep iwl
batee5a@Bat335a:~$ 
```

---

### Post by chili555 on 2016-11-04
Please see: [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by joturos on 2016-11-04
If this does not work you can get a wireless usb adapter and it should work.

---

### Post by chili555 on 2016-11-04
> **joturos said:**
> If this does not work you can get a wireless usb adapter and it should work.Really? Do you suppose that secure boot imposes a signing key requirement on PCI wireless drivers but not USB??

---

### Post by joturos on 2016-11-04
A wireless usb will will show all connections because I tried It

---

### Post by QIII on 2016-11-04
Did you try it with identical hardware and an identical installation?

---

### Post by chili555 on 2016-11-04
> **joturos said:**
> A wireless usb will will show all connections because I tried ItAny and every USB adapter? I doubt it.

Is your kernel version 4.4.0-20 or later? Is secure boot turned *on* in your BIOS? If either or both of these are not true, then your situation is not the same and you comment is not relevant.

---

### Post by ahmeds93 on 2016-11-04
> **chili555 said:**
> Please see: [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

Thank you so much, It turns out to be a problem with Secure boot.

Thank you.

---

### Post by jeremy31 on 2016-11-05
Can you post the results for ```
dkms status
```
You may have a file that would be a great help to us

---

