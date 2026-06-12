---
title: "Ubuntu 18.04 &amp; Realtek R8822BE"
date: 2018-04-30
forum: Networking &amp; Wireless
---

### Post by francis-lemeunier on 2018-04-30
Hi,

I've installed Ubuntu 18.04 x64 on a Intel Z370 motherboard (Asus Z370-I). The integreated wifi/bt card is a Realtek R8822BE.
The wifi seems to works after desactivating of the secure boot option on the Bios but the bluetooth doen't work.
I tried those methods [here]("https://ubuntuforums.org/showthread.php?t=2383787&p=13739449#post13739449") and [there]("https://forum.ubuntu-fr.org/viewtopic.php?pid=21829752")... Without success, kernel error ([here the make.log]("https://pastebin.com/uYtCTq4U")) :
```
root@Hostname:~# dkms install bluetooth-4.4/0.1 
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area...(bad exit status: 2)
make -j12 KERNELRELEASE=4.15.0-20-generic -C /lib/modules/4.15.0-20-generic/build M=/var/lib/dkms/bluetooth-4.4/0.1/build...(bad exit status: 2)
ERROR (dkms apport): binary package for bluetooth-4.4: 0.1 not found
Error! Bad return status for module build on kernel: 4.15.0-20-generic (x86_64)
Consult /var/lib/dkms/bluetooth-4.4/0.1/build/make.log for more information.
```

I tried on the french forum to resolve my problem but no chance for now. You can see some practical info on the topic.
[https://forum.ubuntu-fr.org/viewtopic.php?id=2025513](https://forum.ubuntu-fr.org/viewtopic.php?id=2025513)

Thanks !

---

### Post by jeremy31 on 2018-04-30
Your kernel should already have what I added to the bluetooth-4.4 on github.  I think the Linux firmware for the device isn't quite correct

---

### Post by francis-lemeunier on 2018-06-01
Hi, some updates has resolve my issue. Thanks ;)

---

