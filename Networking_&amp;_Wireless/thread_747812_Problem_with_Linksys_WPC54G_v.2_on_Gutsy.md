---
title: "Problem with Linksys WPC54G v.2 on Gutsy"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by ptychoptera on 2008-04-06
I just converted to Ubuntu from XP and have had no luck getting my wireless card (Linksys wpc54g v.2) working. I've followed all the tutorials posted on this forum and elsewhere to no avail. I used ndiswrapper and got the correct driver. I made sure the files were capitalized properly. I blacklisted acx and bcmxx. Everything I have seen in the forum threads I have tried.

On two different occasions my card was lit up and detecting wireless networks, but both times it stopped working. Unfortunately I haven't been able to figure out why it seemed to work then, or why it quit working.

 When I enter ndiswrapper -l it tells me:

lstinds : driver installed
        device (104C:9066) present (alternate driver: acx)

... but the lights on my card are off and there isn't a wireless connection in the Network Manager.

I am very much at a loss at to what to do now short of reinstalling Ubuntu. Please help this poor noob.

---

### Post by ptychoptera on 2008-04-06
also, ifconfig gives me:

eth0      Link encap:Ethernet  HWaddr 08:00:46:99:29:72  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe99:2972/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12527 errors:4 dropped:0 overruns:0 frame:4
          TX packets:6866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8618182 (8.2 MB)  TX bytes:920873 (899.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

and when I try sudo lshw I get:

-network UNCLAIMED
          description: Network controller
          product: ACX 111 54Mbps Wireless Interface
          vendor: Texas Instruments
          physical id: 1
          bus info: pci@0000:03:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          capabilities: pm cap_list
          configuration: latency=64

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by dmizer on 2008-04-07
you'll have to edit one of the driver inf files for this to work.  i wrote a howto:

[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

let me know if that works for you.

---

### Post by ptychoptera on 2008-04-07
> **dmizer said:**
> you'll have to edit one of the driver inf files for this to work.  i wrote a howto:

[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

let me know if that works for you.

I've done all the steps in that thread previously. Tomorrow morning I will try uninstalling ndiswrapper and starting again. 

Could you clarify what you meant by 'edit one of the drivers'? The only editing of the lstinds.inf file I've done so far was capitalizing the 'TNET'.

Thanks

---

### Post by dmizer on 2008-04-07
> **ptychoptera said:**
> The only editing of the lstinds.inf file I've done so far was capitalizing the 'TNET'.

you actually need to open LSTINDS.INF and manually edit it, as per this line in the howto:
> ** Please read this line carefully ** We're not done fixing the file naming problem. Use your favorite text editor, and open LSTINDS.INF and make sure every instance of tnet1130.sys reads TNET1130.sys (some are all caps, some are all lower case). All instances of tnet1130 MUST be all uppercase.

okay ... let's kill network manager:
1) stop network manger with the following commands:
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
2) prevent network manager from starting on reboot with the following commands:
```
sudo touch /etc/default/NetworkManager
sudo echo exit > /etc/default/NetworkManager
sudo touch /etc/default/NetworkManagerDispatcher
sudo echo exit > /etc/default/NetworkManagerDispatcher
```

instead of using network manger, you will configure your card by going to: system > administration > networking
if you want to re-enable network manager, you need only delete the above two files (/etc/default/NetworkManager and /etc/default/NetworkManagerDispatcher)

post the output of these commands:
```
lsmod | grep ndiswrapper
lsmod | grep acx
```

finally, when you input "ndiswrapper -l", it needs to look like this:
```
Installed drivers:
lsbcmnds                driver installed
lstinds         driver installed, hardware present
```

in other words, you must install _both_ inf files from the windows driver for this to work.

---

### Post by him610 on 2008-04-07
I recently successfully configured my Linksys WPC54G v.2 using this thread
[http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm43xx]("http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm43xx")

The very first post will take you to another link, [BCM43xx HowTo.]("BCM43xx HowTo.") follow it and take the path to step 2f.

---

### Post by ptychoptera on 2008-04-07
A problem arose,,,

joe@joe-laptop:~$ sudo echo exit > /etc/default/NetworkManager
bash: /etc/default/NetworkManager: Permission denied

joe@joe-laptop:~$ sudo echo exit > /etc/default/NetworkManagerDispatcher
bash: /etc/default/NetworkManagerDispatcher: Permission denied

joe@joe-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           185240  0 
usbcore               138632  6 usbhid,ndiswrapper,usb_storage,libusual,uhci_hcd
joe@joe-laptop:~$ lsmod | grep acx

... the grep acx didnt bring anything up, which is what we want, no?

joe@joe-laptop:~$ ndiswrapper -l
lsbcmnds : driver installed
lstinds : driver installed

... and now the hardware isnt being detected with lstinds. I haven't changed anything with that file since last night when it was still being deteted. I've noticed it seems to be detected only sporadically.

And I have already edited the file as per the instructions so that tnet is changed to TNET.

Any help you can provide would be appreciated, as this wireless card is making me pull my hair out.

Sincerely,
linux noob

---

### Post by dmizer on 2008-04-07
okay ... sorry about the command not working for you.  i wasn't sure it would or not.

use nano to edit the files instead:
```
sudo nano /etc/default/NetworkManager
```
type the word:
**exit**
and save the file.

do the same with /etc/default/NetworkManagerDispatcher

and now i at least know that the ndiswrapper module is loading into the system, but for some reason it is not driving the card.  are you using hardy by chance?

anyway, try editing those files as mentioned above, reboot, and check ndiswrapper -l as well as the output of ifconfig, and check if you can see the card in system > administration > network

---

### Post by dmizer on 2008-04-07
> **hgh9mrp said:**
> I recently successfully configured my Linksys WPC54G v.2 using this thread
[http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm43xx]("http://ubuntuforums.org/showthread.php?t=475963&highlight=bcm43xx")

The very first post will take you to another link, [BCM43xx HowTo.]("BCM43xx HowTo.") follow it and take the path to step 2f.

this will not work, as this card is not being driven by the bcm43xx module.

---

### Post by ptychoptera on 2008-04-07
I did everything you suggested, but it doesn't seem to have had much success so far. (FYI, I'm using Gutsy). I'm on the verge of reinstalling Ubuntu, but let me know if you have another suggestion. 

joe@joe-laptop:~$ ndiswrapper -l
lsbcmnds : driver installed
lstinds : driver installed

joe@joe-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:99:29:72  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe99:2972/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163730 (159.8 KB)  TX bytes:18781 (18.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5176 (5.0 KB)  TX bytes:5176 (5.0 KB)

---

### Post by dmizer on 2008-04-07
no ... no need to reinstall.

okay ... let's remove the lsbcmnds driver because you seemed to have better results without it.  not sure why that might be, but let's do it anyway.

```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r lsbcmnds
sudo modprobe ndiswrapper
```
see if that makes lights come on on the card.  if so, try to configure the card in system > administration > network

---

### Post by ptychoptera on 2008-04-07
When I first started fooling around with this wireless card (and briefly had it working) I only had the lstinds.inf installed. Unfortunately I don't know what happened since then to make it  stop working. I removed the other .inf as per your suggestion, but nothing changed.

One problem I've noticed is that when I attempt to install the drivers with the terminal I get a message that says:

"No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181."

... so I've been using the GUI for ndiswrapper. I've read in various forum threads that it's supposed to say something about forcing radio to 0. Perhaps this is part of the problem?

Any other ideas?

---

### Post by dmizer on 2008-04-08
> **ptychoptera said:**
> One problem I've noticed is that when I attempt to install the drivers with the terminal I get a message that says:

"No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181."

this tells me that it's possible there may still be some instances of tnet1130.sys that have not been edited (specifically on line 181 of LSTINDS.INF).

the problem with doing things in the gui instead of the terminal is that the terminal will output errors that can be extremely helpful in finding out what could be causing the problem.

remove lstinds from the wrapper, and look at it again:
```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r lstinds
```

edit LSTINDS.INF again.  this time, make sure all instances of BOTH tnet1130.sys AND tnet1130 show TNET1130.sys AND TNET1130 respectively.  then try readding the driver into the wrapper:
```
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
```

if there were no errors, check the output to see if it reads correctly in the wrapper:
```
ndiswrapper -l
```

if it does read correctly, then load the module and your card should work:
```
sudo modprobe ndiswrapper
```

edit:
make sure to look for this line in LSTINDS.INF:
```
ServiceBinary   = %12%\tnet1130.sys
```
this line should also be changed to read:
```
ServiceBinary   = %12%\[COLOR="Red"]TNET1130.sys[/COLOR]
```

---

### Post by dmizer on 2008-04-08
alternatively, you can try this copy of LSTINDS.INF that i have edited.

---

### Post by ptychoptera on 2008-04-08
I double-checked the LSTINDS.inf file and every instance of 'TNET' is capitalized. I'm still unable to install it with the terminal. I can't install lsbcmnds.inf in terminal either.

joe@joe-laptop:~$ sudo ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.

... any other ideas?

EDIT: just to be thorough, I tried using the LSTINDS.inf file you provided, but no luck

---

### Post by dmizer on 2008-04-08
i'm looking through lsbcmnds.inf now ... it's possible that linksys changed the driver again.

edit:
okay, i can't find anything quickly.  i'm at work now.  i'll take a closer look at this when i get home.  sorry i couldn't resolve it quickly for you.

---

### Post by dmizer on 2008-04-08
sent you a pm.

---

