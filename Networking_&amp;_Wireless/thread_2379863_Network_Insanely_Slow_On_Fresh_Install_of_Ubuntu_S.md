---
title: "Network Insanely Slow On Fresh Install of Ubuntu Studio 17.10"
date: 2017-12-10
forum: Networking &amp; Wireless
---

### Post by Darth4212 on 2017-12-10
Ok so today I reinstalled Ubuntu Studio, and lost all my files cause I was dumb and forgot to back them up, because my wifi wouldn't connect, well now it connects but is insanely slow. Now upon initial connection the speed is faster for about 10 seconds (though this *faster *is a relative term as it is still pretty slow)  then it goes back to super slow mode. 

My output for the wireless-info script is  [http://paste.ubuntu.com/26160774/](http://paste.ubuntu.com/26160774/)

---

### Post by chili555 on 2017-12-10
First, I'd blacklist the probably conflicting driver b43:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb"  >>  /etc/modprobe.d/blacklist.conf
exit
```Next, we see about a dozen access points named xfinitywifi. You might have better luck if you bind to the strongest as I describe here: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Finally, I notice:> Cell 01 - Address: <MAC 'xfinitywifi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    [COLOR="#FF0000"]Encryption key:off[/COLOR]
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007072201e7d
                    Extra: Last beacon: 2008ms agoNot only is this dangerously insecure, but I think your driver and hardware combination might work better with WPA2-AES.

---

### Post by Darth4212 on 2017-12-11
> **chili555 said:**
> First, I'd blacklist the probably conflicting driver b43:```
sudo -i
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb"  >>  /etc/modprobe.d/blacklist.conf
exit
```Next, we see about a dozen access points named xfinitywifi. You might have better luck if you bind to the strongest as I describe here: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Finally, I notice:Not only is this dangerously insecure, but I think your driver and hardware combination might work better with WPA2-AES.

Okay I will blacklist the drivers when I get home, but about

> Next, we see about a dozen access points named xfinitywifi. You might have better luck if you bind to the strongest as I describe here: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Finally, I notice:Not only is this dangerously insecure, but I think your driver and hardware combination might work better with WPA2-AES.

I get it is insecure but I have to use it

---

### Post by chili555 on 2017-12-11
> I get it is insecure but I have to use it
At least bind the strongest as I suggested so that your device doesn't drop and reconnect looking for a better xfinitywifi.

---

### Post by Darth4212 on 2017-12-11
I have done everything you have said to do and it is still slow it is a bit better but it is still slow. ;_;

---

### Post by Darth4212 on 2017-12-11
I ran ```
dmesg
``` and I seem to be getting the same error message consistently which is: ```
brcmsmac bcma0:1: START: tid 1 is not agg'able
```

---

### Post by chili555 on 2017-12-12
> [ 1848.952072] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1848.952085] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1848.952104] wlp8s0b1: associated
[ 1849.283297] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1873.715190] brcmsmac bcma0:1: START: tid 1 is not agg'able (repeated 12 times)
[ 2254.631967] brcmsmac bcma0:1: START: tid 2 is not agg'able
[ 2343.028953] brcmsmac bcma0:1: START: tid 1 is not agg'able (repeated 8 times)

I have Googled these messages extensively over the past few days. There are many bug reports but no firm solution. There are many forum posts for Ubuntu, Arch, Debian, Kali, etc. Again, there are almost never any firm solutions. So, since there is no clear, solid path, we are explorers on our own.

First, I notice that the driver brcmsmac uses firmware. From* modinfo brcmsmac*:

```
filename:       /lib/modules/4.13.0-19-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
<snip>
```

Let’s be sure you have the latest and uncorrupted firmware. Please run from the terminal:

```
cd /lib/firmware/brcm
md5sum bcm43xx*
```

On my fully updated system, I get:

```
b0736e3590b05d27284fbb8a3efd50e1  bcm43xx-0.fw
5e51778ee011badcb42f1e2cb4ab3956  bcm43xx_hdr-0.fw
```

If you get any different, we’ll update the firmware.

The only other suggestion that I have is contrary to my own good advice. That is to try the ***wrong*** driver. 

```
sudo apt-get install bcmwl-kernel-source
```

Reboot. Does your wireless work? Does it work well?

---

### Post by praseodym on 2017-12-12
There are several networks with the same ESSID available, even on different channels. Add the MAC address of the strongest AP into the field "BSSID" of the network-manager profile to connect to that one

---

### Post by Darth4212 on 2017-12-12
> **chili555 said:**
> I have Googled these messages extensively over the past few days. There are many bug reports but no firm solution. There are many forum posts for Ubuntu, Arch, Debian, Kali, etc. Again, there are almost never any firm solutions. So, since there is no clear, solid path, we are explorers on our own.

First, I notice that the driver brcmsmac uses firmware. From* modinfo brcmsmac*:

```
filename:       /lib/modules/4.13.0-19-generic/kernel/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
<snip>
```

Let’s be sure you have the latest and uncorrupted firmware. Please run from the terminal:

```
cd /lib/firmware/brcm
md5sum bcm43xx*
```

On my fully updated system, I get:

```
b0736e3590b05d27284fbb8a3efd50e1  bcm43xx-0.fw
5e51778ee011badcb42f1e2cb4ab3956  bcm43xx_hdr-0.fw
```

If you get any different, we’ll update the firmware.

The only other suggestion that I have is contrary to my own good advice. That is to try the ***wrong*** driver. 

```
sudo apt-get install bcmwl-kernel-source
```

Reboot. Does your wireless work? Does it work well?

Well like you said I ran ```
]cd /lib/firmware/brcm
md5sum bcm43xx*
```
and got 
```
b0736e3590b05d27284fbb8a3efd50e1  bcm43xx-0.fw
5e51778ee011badcb42f1e2cb4ab3956  bcm43xx_hdr-0.fw
```
So I have no clue what to do besides installing the incorrect driver

---

### Post by chili555 on 2017-12-12
> So I have no clue what to do besides installing the incorrect driverNeither do I. It seems that we are down to two choices:

***** Try something perhaps a bit crazy which can quickly and easily be reversed, by the way; or

***** Do nothing and live with Insanely slow speeds forever.

Please proceed.

---

### Post by Darth4212 on 2017-12-12
> **chili555 said:**
> Neither do I. It seems that we are down to two choices:

***** Try something perhaps a bit crazy which can quickly and easily be reversed, by the way; or

***** Do nothing and live with Insanely slow speeds forever.

Please proceed.

Maybe if i reinstall the firmware but I don't know how to go about that

---

### Post by chili555 on 2017-12-12
The md5sum suggests that your firmware is just perfect.

Again, I suggest that you try the wrong driver.```
sudo apt-get install bcmwl-kernel-source
```Reboot.

---

### Post by Darth4212 on 2017-12-14
Okay I don't get why but installing the wrong firmware did the trick this is bamboozling

---

### Post by chili555 on 2017-12-14
> **Darth4212 said:**
> Okay I don't get why but installing the wrong firmware did the trick this is bamboozlingThe Ubuntu moves in a mysterious way, its wonders to perform.

Glad it's working. We have both learned something new today!

---

### Post by Darth4212 on 2017-12-19
Okay so sometimes the wl driver seems to act up but I have found a relatively easy way to get it back to normal you need to open a terminal and run:
```
sudo rmmod wl
sudo modprobe bcma
sudo modprode brcmsmac
sudo rmmod brcmsmac
sudo rmmod bcma
sudo modprobe wl
```

---

