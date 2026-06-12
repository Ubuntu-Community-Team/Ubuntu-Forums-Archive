---
title: "Installed ndiswrapper but not working"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by dragonboss on 2008-08-23
i've installed ndiswrapper and the driver (copied from windows) for my card, bcm 4318, and when i run the command ndiswrapper -l i think, the output is something like bcmwl5.inf installed and alternate driver ssb.
How do i get rid of the ssb alternate driver cause i gather thet it is probably what is restricting the driver from working.:confused:

---

### Post by caljohnsmith on 2008-08-23
You can blacklist the ssb driver if it is getting in the way of ndiswrapper, and while you're at it, make sure you also blacklist the other broadcom drivers. Just do:
```
gksudo gedit /etc/modprobe.d/blacklist
```
And then add the following lines to the file:
```

blacklist ssb
blacklist b43
blacklist b43legacy
blacklist bcm43xx
```
Save, reboot, and hopefully your ndiswrapper will work fine after that.

---

### Post by dragonboss on 2008-08-23
Thanks for the info. But why is it that the broadcom 4318 card has so many issues its like that card and ubuntu = a horrible curse!

---

### Post by caljohnsmith on 2008-08-23
> **dragonboss said:**
> Thanks for the info. But why is it that the broadcom 4318 card has so many issues its like that card and ubuntu = a horrible curse!
In two words: proprietary drivers. Unfortunately, that's why it is so much hassle to make it work in Linux. :)

---

### Post by dragonboss on 2008-08-24
I blacklisted all you said i should blacklist and now when you click the icon on the panel it does not display the wireless part neither does the configurations when you open it.

---

### Post by caljohnsmith on 2008-08-24
Please post the output of:
```
ndiswrapper -l
lsmod | grep -e ssb -e 43
ifconfig
iwconfig
```
And if you run:
```
sudo iwlist scan
```
Does it list any available wifi networks?

---

### Post by dragonboss on 2008-08-25
Here's the output...
Sorry if the formatiing is not correct, I copied it to a text file in ubuntu and when i opened it in windows(have to use it to access the net) it was all messed up.
jeremy@jeremy's-laptop:~$ ndiswrapper -l


bcmwl5 : driver installed

	device (14E4:4318) present (alternate driver: ssb)


jeremy@jeremy's-laptop:~$ lsmod | grep -e ssb -e 43


nf_nat_ftp              4352  0 

ndiswrapper           193436  0 

b44                    28432  0 

ssb                    34308  1 
b44
scsi_mod              151436  
4 sg,sr_mod,sd_mod,libata


jeremy@jeremy's-laptop:~$ ifconfig


eth0      Link encap:Ethernet  HWaddr 00:16:d4:5e:1b:85
  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000
 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:22 

lo
        Link encap:Local Loopback
  
          inet addr:127.0.0.1  Mask:255.0.0.

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1778 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1778 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0
 
          RX bytes:88900 (86.8 KB)  TX bytes:88900 (86.8 KB)


jeremy@jeremy's-laptop:~$ iwconfig


lo        no wireless extensions.



eth0      no wireless extensions.



jeremy@jeremy's-laptop:~$ sudo iwlist scan

[sudo] password for jeremy: 


lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.

---

### Post by caljohnsmith on 2008-08-25
Jeremy, from your lsmod output, it looks like ssb is still getting loaded somehow. If you do:
```
cat /etc/modprobe.d/blacklist
```
Are you sure you have a line in that file that says "blacklist ssb"? Just want to make sure, because if you do, then you can "brute-force" blacklist that ssb module by doing the following:
```
cd /lib/modules/`uname -r`/kernel/drivers/ssb/
sudo mv ssb.ko ssb.ko.backup
```
The above gives the ssb module a modified name so that the kernel won't find it and therefore won't be able to load it.

---

### Post by dragonboss on 2008-08-25
Sorry, i forgot i removed that blacklisting to see if the config would come back.I'll put it back and try what you said.

---

### Post by dragonboss on 2008-08-25
my settings manager still is not showing wireless!... I attached a screenshot...

---

