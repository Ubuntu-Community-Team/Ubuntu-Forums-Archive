---
title: "New user NEED HELP"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Dzrigger on 2009-12-28
Im new to Ubuntu, I just installed it 3 days ago. So far I like it. The problem I am having is with my 
ATI TV Wounder 200 USB 2.0 Ubuntu does not see it when I plug it in and I can not find any drivers for it as well.
Does any one have any idea on how to properly install this and were I can find the drivers for this. Any help will be much appreciated...Thanks
 
HP G60-200
Vista 64x
Uvuntu 64X

---

### Post by Cooter2543 on 2009-12-28
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.5](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.5)

Select TV Tuner and your model. Then click on the Drivers and Downloads tab.

---

### Post by mlentink on 2009-12-28
Might I also suggest that you use a more descriptive title next time you post? It helps if people knowledgeable in your problem area spot your post faster and prevents those less expert to have to read your post.

Thanks

---

### Post by Dzrigger on 2009-12-28
I went to the link, download the drivers but all the drivers are for Windows. I did not see anything under the Linux download.

---

### Post by halitech on 2009-12-28
with the device not plugged in, open a terminal and run
```
lsusb
```
then plug the device in and wait 30 seconds and run the command again. Post the info here so we can help out.

---

### Post by Dzrigger on 2009-12-28
Ok I typed in lsusb and this is what came up.

israel@israel-laptop:~$ lsusb
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
israel@israel-laptop:~$ lsusb
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1002:a001  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
israel@israel-laptop:~$

---

### Post by Dzrigger on 2009-12-29
Does anyone have any Idea what it is what I am doing wrong?

---

### Post by glubbdrubb on 2009-12-29
It seems you are not the only one battling to find drivers for this card. A newer kernel might help. 

Type:
```
uname -r
```

into a terminal and paste the output here please.

---

### Post by Dzrigger on 2009-12-29
This is what came up after typing  in the command.

israel@israel-laptop:~$ uname -r
2.6.31-16-generic

---

### Post by sandyd on 2009-12-29
thats the current newest kernel thats in the repos.

---

### Post by halitech on 2009-12-29
I'm guessing this is the USB ATI device
[color="red"]Bus 002 Device 003: ID 1002:a001 [/code]
based on it not giving any info about the manufactorer I'm also guessing that it doesn't know what it is.

There is some info here for a similiar model (the wonder 600) [http://ubuntuforums.org/showthread.php?t=941188](http://ubuntuforums.org/showthread.php?t=941188)

Also, post the output of ```
dmesg | tail -n10
```

---

### Post by glubbdrubb on 2009-12-30
You have the latest kernel available, as carlee said, so updating that wont help.

I have done extensive searching online and can't find any linux drivers. 

Does anyone know if there is a way to use a Windows driver instead?

---

### Post by Dzrigger on 2009-12-30
the device is a ATI TV WOUNDER 200 USB 2.0 
Here is what came up after typing dmesg | tail -n10


 israel@israel-laptop:~$ dmesg | tail -n10
[   30.494843] CPU1 attaching NULL sched-domain.
[   30.540114] CPU0 attaching sched-domain:
[   30.540118]  domain 0: span 0-1 level MC
[   30.540120]   groups: 0 1
[   30.540125] CPU1 attaching sched-domain:
[   30.540127]  domain 0: span 0-1 level MC
[   30.540129]   groups: 1 0
[   33.320023] eth0: no IPv6 routers present
[45009.970156] usb 2-5: new high speed USB device using ehci_hcd and address 3
[45010.122987] usb 2-5: configuration #1 chosen from 1 choice
israel@israel-laptop:~$

---

