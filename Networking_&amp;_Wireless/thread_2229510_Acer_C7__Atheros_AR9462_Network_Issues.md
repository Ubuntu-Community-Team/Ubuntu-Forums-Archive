---
title: "Acer C7 / Atheros AR9462 Network Issues"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by acts1-8b on 2014-06-13
I just did a fresh install of Ubunbu 12.04 on my Chromebook. Everything seems to be working just fine, except that I can not get an internet connection. It just says 'No network Devices Available'. Can anyone help?

(I know there is another thread talking about this, but it didn't work)

---

### Post by Mar Komus on 2014-06-13
First things first: have you run the *ifconfig* command? If so, may we see the results? (I like your screen name, btw :) )

---

### Post by acts1-8b on 2014-06-13
Thanks! 

I ran the command and got: 

```
user@ChrUbuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53376 (53.3 KB)  TX bytes:53376 (53.3 KB)
```

---

### Post by slickymaster on 2014-06-13
Hi acts1-8b, output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.
Please [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to make the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by acts1-8b on 2014-06-13
Oups, sorry. This look better? 

```


user@ChrUbuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53376 (53.3 KB)  TX bytes:53376 (53.3 KB)



```

---

### Post by Mar Komus on 2014-06-13
Okeeee...so slight problem from the get-go: the only network interface listed is the loop back. What is the exact make and model of your Chromebook?

Also, will you give us the feedback from this command (run as *root* or *superuser*):

> lshw -C network -sanitize

---

### Post by Mar Komus on 2014-06-13
One other question I have: is there a particular reason you're running 12.04? Just curious because perhaps the 14.04 would contain drivers for the specific hardware that 12.04 would not? Just a thought

---

### Post by Bucky Ball on 2014-06-13
Please run this command and post the result:

```
sudo lshw -C network
```

Thanks.

> **Mar Komus said:**
> One other question I have: is there a particular reason you're running 12.04? Just curious because perhaps the 14.04 would contain drivers for the specific hardware that 12.04 would not? Just a thought

Let's keep on topic and find out which wireless card is in there first. 12.04 LTS is rock solid and the Acer C7 has been out for ages now so doubt the release is the issue. ;)

---

### Post by Mar Komus on 2014-06-13
Kinda what #6 is about... ;)

---

### Post by Mar Komus on 2014-06-13
By the way, someone had a similar problem [here]("http://ubuntuforums.org/showthread.php?t=2161506")

---

### Post by Bucky Ball on 2014-06-13
> **Mar Komus said:**
> By the way, someone had a similar problem [here]("http://ubuntuforums.org/showthread.php?t=2161506")

Indeed they did, and praseodym is a bit of a wireless guru here. I'd advise following his post #4 there and seeing if it works first up. Good find.

---

### Post by acts1-8b on 2014-06-13
I got:


```


user@ChrUbuntu:~$ sudo lshw -C network
[sudo] password for user: 
PCI (sysfs)  


  *-network UNCLAIMED     
       description: Network controller
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:e0400000-e047ffff memory:e0480000-e048ffff
  *-network
       description: Ethernet controller
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom
       configuration: driver=tg3 latency=0
       resources: irq:18 memory:e0500000-e050ffff memory:e0510000-e051ffff memory:e0600000-e06007ff
user@ChrUbuntu:~$ 



```

---

### Post by acts1-8b on 2014-06-13
I found that thread before, and ran the code, here is what I got:


```


user@ChrUbuntu:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
user@ChrUbuntu:~$ sudo modprobe -rfv ath9k
user@ChrUbuntu:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
FATAL: Error inserting ath9k (/lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): No such device
user@ChrUbuntu:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
user@ChrUbuntu:~$ 



```

---

### Post by Bucky Ball on 2014-06-13
Go to the link provided by Mar Komus (click on the link in post #11 above your post) and perform the steps outlined in post #4 there.

---

### Post by acts1-8b on 2014-06-13
[COLOR=#000000]I found that thread before, and ran the code, here is what I got:[/COLOR]


```

[COLOR=#000000]
user@ChrUbuntu:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
user@ChrUbuntu:~$ sudo modprobe -rfv ath9k
user@ChrUbuntu:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
FATAL: Error inserting ath9k (/lib/modules/3.4.0/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): No such device
user@ChrUbuntu:~$ sudo iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; No such device.
user@ChrUbuntu:~$

[/COLOR]
```

---

### Post by Bucky Ball on 2014-06-13
Got you. I guess because its not identifying that card as wlan0, or anything else. If we look under 'network controller' in the info you give in post #12 we find:

physical id: 0

That should be 'wlan0' or wlan some number ...

It also has no driver, as yet, which is odd as I'm pretty sure that driver is part of the kernel, or should be, and shouldn't need to be installed manually. Bit busy today, but back tonight so good luck until then and hope one of our wireless experts notices your thread in the meantime.

* Stab in the dark: Try going to 'Additional Drivers' (or may be hardware drivers in your release) and seeing if there's anything there for the card. Takes a minute or two for the system to search.

---

### Post by acts1-8b on 2014-06-14
Tryed it, nothing, thanks thought :)

And it is really werid, I've used the same method before pf the same chromebook (It got reset, so I had to re do it) and it worked fine.

---

### Post by varunendra on 2014-06-15
It looks like a broken update/kernel-upgrade to me. When booting, do you see the advanced grub menu? Do you get an option to boot into an older kernel? If yes, try booting with an older kernel and let us know if the network works there.

You may have to press 'Shift' ('Esc' in some systems) key while booting to get the advanced grub menu.

For now, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
Please also post the outputs of -
```
locate ath9k.ko
modinfo ath9k
```

---

### Post by acts1-8b on 2014-06-19
> **varunendra said:**
> It looks like a broken update/kernel-upgrade to me. When booting, do you see the advanced grub menu? Do you get an option to boot into an older kernel? If yes, try booting with an older kernel and let us know if the network works there.

You may have to press 'Shift' ('Esc' in some systems) key while booting to get the advanced grub menu.

For now, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
Please also post the outputs of -
```
locate ath9k.ko
modinfo ath9k
```



Hey, sorry this took me so long, I did a fresh install and its fine now. But thanks for all of your help!

---

### Post by Bucky Ball on 2014-06-20
Good to hear. Please mark the thread as solved from 'Thread Tools' at top right of this page.

---

