---
title: "Wireless connection: problem with automatic connection on boot-up"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by wwastro on 2008-06-24
I recently sought help with wireless connection on a Dell Inspiron 6400 laptop with Gutsy installed via the following thread:

[gnome] Problem with Gutsy wireless setup on a Dell Inspiron 6400 laptop
(see: [http://ubuntuforums.org/showthread.php?t=836069](http://ubuntuforums.org/showthread.php?t=836069))

This was happily solved by a manual setup guided by the extremely useful post "How To: Manual Network Configuration without the need for Network Manager"
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495) (many thanks, kevdog!!).

However, on editing the /etc/rc.local file to get connection on boot-up, I still had to connect manually. The /etc/rc.local file looks like this (with my encryption key replaced by dashes):

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing. 
ifconfig eth0 down
ifconfig eth1 down
dhclient -r eth1
ifconfig eth1 up
iwconfig eth1 key open
iwconfig eth1 key S:ASCII_KEY ----------
iwconfig eth1 mode Managed
dhclient eth1
exit 0

Any ideas as to the cause of this problem? Alternatively, would it be possible to write a small script file which can be run from a terminal window to do the manual setup in one go?

Any help appreciated!

---

### Post by pokipoki08 on 2008-06-24
change
```
iwconfig eth1 key [COLOR="Red"]S:ASCII_KEY ----------[/COLOR]
```
to
```
iwconfig eth1 key [COLOR="Blue"]**s**:password[/COLOR]
```

password = encryption key in ascii

---

### Post by wwastro on 2008-06-24
Thanks pokipoki08, I can see the error in my version of the file, and I'm sure yours should work.

Unfortunately the system is now telling me that I have no permission (even as superuser) to modify /etc/rc.local, even though I was able to edit it yesterday (why? what's changed? - I don't understand!?):confused:

---

### Post by kevdog on 2008-06-24
What does:

ls -la /etc/rc.local

show?

Also if/when you can edit the file, put a sleep 20 prior to your first statement -- this will give networking services possibly some extra time to be brought up and running prior to you passing commands.

---

### Post by wwastro on 2008-06-28
Thanks for the latest suggestions, kevdog. My problem with editing the /etc/rc.local file was a silly beginner's mistake: not starting with sudo.

This problem has now been overcome. In fact I can now usually get the WiFi connection from boot-up, or if the modem/router service drops out for a while, I can recover it by running a shell script containing essentially the instructions in the /etc/rc.local file.

However, in some sessions I cannot get a WiFi connection at all, even when I know the ethernet output from the router is working. I suspect this is due to poor S/N ratio or low signal strength - in Windows days this was sometimes a problem too - hence not really a software problem. However there was one curious thing I noticed on typing ifconfig as a diagnostic when there was no WiFi connection - here is an example of the response to ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:18:DE:94:65:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x8000 Memory:efdff000-efdfffff 

eth1:avah Link encap:Ethernet  HWaddr 00:18:DE:94:65:62  
          inet addr:169.254.7.15  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x8000 Memory:efdff000-efdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1520 (1.4 KB)  TX bytes:1520 (1.4 KB)

- notice the eth1:avah in the above? *I really don't understand what this is telling me*.

Thanks again for you help so far. Keep up the good work!

---

