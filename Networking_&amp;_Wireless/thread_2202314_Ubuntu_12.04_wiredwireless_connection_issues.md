---
title: "Ubuntu 12.04 wired/wireless connection issues"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by bill25 on 2014-01-28
Hi all, 

I'm new to ubuntu and would really appreciate help with an issue im having. 

I recently tried to breath new life into an old HP Pavillion dv9000 PC by installing ubuntu 12.04. I successfully manager to install it; now I have duel boot machine with ubuntu 12.04 and windows Vista. 

The problem I am experiencing is that ubuntu does not seem like its capable of going online with either wireless and wired connections. It just doesnt seem to be able to detect anything. I initially thought it was a hardware issue but when I used vista I'm able to get on the internet with no issues. Now I think that the issue might be a driver problem. 

I get some error messages when I boot up ubuntu which may have something to do with my problem. They are as follows:

8.1564181 kvm: disabled by bios
9.832702 b43-phy0 ERROR: Firmware file "b43/ucode11.fw" not found
9.832702 b43-phy0 ERROR: Firmware file "b43-open/ucode11.fw" not found 
9.832742 b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please fully read all instructions on this website.


I tried to go on that website but im not really sure what to do . 

Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2014-01-28
Please paste this in to a terminal and post the output here, please:

```
sudo lshw -C network
```

You will also find some tips here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

---

