---
title: "MacBook C2D and the new madwifi 0.9.4  =("
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by danoglam on 2008-02-14
I'm almost crying.... I cannot do it.... 
I have just reinstalled Ubuntu 7.10 and then the new madwifi drivers release 0.9.4 uploaded 2 days ago...

I'm following the steps from: 
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

But when I go to this line...
$ wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device

That's because the ath0 its not being created....
damn!! why is so complicated???
please please someone help me  :________________________________________(
thanks!!


ps: my card info:
Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

---

### Post by mrsteveman1 on 2008-02-14
Are you sure the module for the driver is actually loaded?

Do:

```
sudo ifconfig -a
```

and post the results. Is ath0 listed?

---

### Post by danoglam on 2008-02-14
no it's not!!

dano@patagonia:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:63:30:E3:0A  
          inet addr:192.168.1.38  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe30:e30a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97327304 (92.8 MB)  TX bytes:4198708 (4.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



and that is the problem I guess. but I would like to make a non-fishy solution to this. I can't believe that people from madwifi never tried this before... 
I would really appreciate any piece of information you might send me!

---

### Post by mrsteveman1 on 2008-02-14
Ok, before you installed this new driver, your running system had a driver for this wireless chip, right?

In other words there was in fact a pre-existing kernel module for this chip, and it was loading automatically at boot, right?

You may just have to blacklist the old module and make sure the new one loads correctly.

Post (or attach as a file) the output of lsmod and dmesg

---

### Post by mrsteveman1 on 2008-02-14
I looked over the driver source you are using, there is supposed to be a script that removes the old module from the system, and the new module is called ath_pci

So try and load ath_pci by hand first

```
sudo modprobe ath_pci
```

then check ifconfig -a again and see if your interface shows up, if not it could be a module loading error which should show up in dmesg

---

### Post by danoglam on 2008-02-15
Dear Steve,

here are the steps from madwifi howto that i've executed:

$ make
$ make install
$ modprobe ath_pci
$ wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device

at the last one, throws me the error that I've mentioned you before. :(
about de dmesg on $ sudo modprobe ath_pci
the result is:


[  322.736000] ath_hal: module license 'Proprietary' taints kernel.
[  322.736000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  322.848000] wlan: 0.9.4
[  322.888000] ath_pci: 0.9.4


so, what do you think???

---

### Post by mrsteveman1 on 2008-02-15
Did you run the script that removes the old module?

It's listed on the howto page you posted earlier.

I suspect perhaps that the old module is still loaded.

---

### Post by danoglam on 2008-02-15
I'm afraid that I already run the scripts before successfully... 
I've followed the instructions carefully...
I could show you a log if you want to see it... just tell me

:confused:

---

### Post by mrsteveman1 on 2008-02-15
I believe you  :D

I'm looking over the driver to rule stuff out. I had thought perhaps the HAL needed to be updated but its part of the driver itself so that shouldn't be an issue. 

So no matter what you do, rebooting the system, loading ath_pci, nothing gets ath0 to show up with ifconfig, right?

The site mentions something about "wlanconfig ath0 destroy" being used if wlanconfig doesn't work right, but that may be just to clear the virtual interfaces.

---

### Post by danoglam on 2008-02-19
Ok guys. Some news... Problem Solved (?). 
Not at all. But something important you might know:

**madwifi 0.9.4 doesn't support the Atheros AR5418 (present on MacBook C2D)**

So I'm stuck. I'm going to download the lastest trunk for my MacBook from the svn ([http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk)), because that is the only thing that "works".

It seems that if you buy a MAC, you should use your MACOS and that's it... if you want to change your OS, think twice!

Regards and many thanks! :popcorn:

---

### Post by mrsteveman1 on 2008-02-19
I think the issue was that the HAL doesn't yet support these new chips, but the driver can.

There does seem to be some indication that the newest SVN source supports this chip, so thats a good thing to try.

---

### Post by jwhendy on 2008-06-03
I realize this is old news now... but could someone please post the results of this endeavor? I have a 2nd gen MacBook (the white one, not a MBP) and have been having the damndest time getting madwifi to work as well with the same error - 'ioctl: no such device'. Everything (make, make install, modprobe ath_pci, etc.) works without flaw but from there on, no dice.

Many other posts offer other solutions that I just don't think apply to me so it's been quite the journey to FINALLY find a post that reports the same conditions (madwifi version & computer) as I have.

PLEASE followup your post with the solution or the results or your attempt to use the snapshot!

Thanks,
John

---

