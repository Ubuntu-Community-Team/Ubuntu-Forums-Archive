---
title: "&quot;service networking stop&quot; makes computer die"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by Zhivargo on 2014-01-20
I found this strange problem when i type 

```
sudo services networking stop
```

My computer becomes *Completely* unresponsive until hard reset

All i could think of doing was typing 

```
sudo services networking stop && dmesg | tail > ~/Desktop/file.txt
```

And that returned this:

```
[  233.733813] hid-generic 0005:0D62:01BF.0002: unknown main item tag 0x0
[  234.260410] input: Acer Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.6/1-1.6:1.0/bluetooth/hci0/hci0:21/input13
[  234.261092] hid-generic 0005:0D62:01BF.0002: input,hidraw1: BLUETOOTH HID v1.37 Mouse [Acer Bluetooth Mouse] on 68:94:23:48:fa:42
[  301.560206] init: cups-browsed main process ended, respawning
[  301.617906] device wlan0 left promiscuous mode
[  301.618058] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  301.655236] init: systemd-logind main process (692) killed by TERM signal
[  301.663682] init: lightdm main process (1023) terminated with status 1
[  301.663994] init: whoopsie main process ended, respawning
[  301.677180] init: Disconnected from system bus
```

(mouse connection unrelated) 


i am running 
Linux AcerOne 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I really have no clue what is going on here any info you need i will post

i am running ath9k driver

---

### Post by Iowan on 2014-01-20
I vaguely remember a similar thread about _restarting_ networking services and the ensuing problem... 
As I recall, the solution there was to restart** network-manager** instead of** networking**.

---

### Post by ian-weisser on 2014-01-20
Bug report: [https://bugs.launchpad.net/ubuntu/+bug/1072518](https://bugs.launchpad.net/ubuntu/+bug/1072518)
One previous thread: [http://ubuntuforums.org/showthread.php?t=2139490](http://ubuntuforums.org/showthread.php?t=2139490)

Iowan's recollection is correct. Do not stop network services that way until fixed.

---

### Post by Zhivargo on 2014-01-20
Ah ok it is a bug. Thanks!

---

