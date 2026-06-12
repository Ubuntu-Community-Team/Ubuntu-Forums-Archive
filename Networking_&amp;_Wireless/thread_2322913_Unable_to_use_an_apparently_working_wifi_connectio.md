---
title: "Unable to use an apparently working wifi connection, Plasma, 16.04"
date: 2016-05-01
forum: Networking &amp; Wireless
---

### Post by valentin15 on 2016-05-01
Hi all,
I recently installed Kubuntu 16.04 on a Lenovo T460s. The wifi worked briefly. After post-installation updates and a reboot, i am unable to use it.

Following answers on other threads, i ran the "[wireless script]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222")" and attached the output to this post.

It looks like everything works, I recognize the name of networks i should be able to connect to. However I can't connect to any wireless network:
[LIST]
[*]There is no wireless icon in the taskbar, only wired connections 
[*]I didn't find anything in the system settings /network interface 
[/LIST]

Do you know how to fix this issue?
Any help would be greatly appreciated!

---

### Post by jeremy31 on 2016-05-01
It might be the result of a network manager bug.  The script results show your wifi device as ethernet
```
GENERAL.DEVICE:                         wlp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
```

I would try the following and see if wifi works
```
systemctl stop NetworkManager.service
```
```
systemctl enable NetworkManager.service
```
This will likely have to been done after every reboot if it works

---

### Post by valentin15 on 2016-05-01
Thank you for your answer!
The second command with "enable" didn't do much.

I tried
```
systemctl restart NetworkManager.service
```
and this worked.

It might be a bug as you pointed out.
Thanks again!

---

### Post by jeremy31 on 2016-05-01
The fix is [https://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/?id=dd4d8b24da29abfc786ce0b3030c74559b93d034](https://cgit.freedesktop.org/NetworkManager/NetworkManager/commit/?id=dd4d8b24da29abfc786ce0b3030c74559b93d034) but that involves editing source code, there is a bug report for this that is being worked on

---

