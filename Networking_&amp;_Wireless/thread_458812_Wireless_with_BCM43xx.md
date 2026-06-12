---
title: "Wireless with BCM43xx"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by motoyogi on 2007-05-30
Hi All,
I am trying to configure the wireless in my laptop with the following things:
OS: ubuntu 6.06 server edition.
Kernel: 2.6.15-26-server

When I looked into the kernel configuration, I found:
# cat /boot/config-2.6.15-26-server | grep BCM
CONFIG_BCM43XX=m
CONFIG_BCM43XX_PIO=y
CONFIG_BCM43XX_DMA=y
CONFIG_BCM43XX_DMA_AND_PIO_MODE=y

I think, it means kernel has bcm43xx modules.

When I did:
# lspci -n | grep 14e4:43
0000:0c:00.0 0280: 14e4:4311 (rev 01)

When I did:
# lsmod | grep bcm
bcm43xx                   142348  0
ieee80211softmac     32512  1  bcm43xx
ieee80211                    39496  2  bcm43xx, ieee80211softmac

I have installed firmware files using bcm43xx-fwcutter and wl_apsta.o 

BUT, when I did:
# ifconfig -a
It does not show me eth1 anywhere

When I did:
# iwconfig
lo       no wireless extension
eth0  no wireless extension

I am unable to find the eth1 as my wireless interface.
Please help me.

-Yogesh

---

### Post by floke on 2007-05-30
Try this, worked flawlessly for me.

[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm)

---

