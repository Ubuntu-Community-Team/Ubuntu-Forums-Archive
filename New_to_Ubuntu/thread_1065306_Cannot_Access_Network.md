---
title: "Cannot Access Network"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2009-02-09
My system has been working flawless since a few days after startup.

Now all of a sudden I'm having problem accessing the server for a WinXP Home desktop.

I get down to MSHOME and it gives me this error
My Network Places
Entire Network
Microsoft Windows Network
MSHOME
---------------------------
Windows Explorer
---------------------------
Mshome is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The list of servers for this work group is not currently available 
---------------------------
OK   
---------------------------
I have de-activated my firewall, still no success. The PC is connected to the system thru a Linksys Wireless G card, the router is a Linksys WRT150N.

/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.125
 netmask 255.255.255.0
 network 192.168.1.1
 broadcast 192.168.0.255
 gateway 192.168.1.1

Appreciate your help.

CarolinaGuy

---

### Post by bgates on 2009-02-09
Broadcast needs to be 192.168.1.255, it is broadcasting to a different subnet than the one you are actually on.  

I'm not sure if this is causing your exact error, but it could certainly cause some issues.  Try to resolve that first, and then reboot and try again and see if the message changes any.

---

### Post by CarolinaGuy on 2009-02-10
bgates,

I changed it and everything seem to be working.

THANK YOU.

CarolinaGuy

---

### Post by bgates on 2009-02-10
You're welcome!  I'm glad it's working.

---

### Post by CarolinaGuy on 2009-02-11
Well, I was a little hasty. Tried logging on tonight with my wireless Desktop PC with WinXP and am receiving the same report.

---------------------------
My Network Places
---------------------------
\\ubuntu8\MOVIES is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.

---------------------------
OK   
---------------------------
```


charlie@ubuntu8:~$ charlie@ubuntu8:~$ ls
music  photos  webmin_1.420_all.deb

df -l


charlie@ubuntu8:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             56413888   1497520  52073272   3% /
varrun                  257648       184    257464   1% /var/run
varlock                 257648         0    257648   0% /var/lock
udev                    257648        64    257584   1% /dev
devshm                  257648         0    257648   0% /dev/shm
/dev/sda3             19465424   7174860  11301764  39% /mnt/Documents
/dev/sdb1            251891248 152432744  99458504  61% /mnt/photos
/dev/sdb2            230636880   4864576 214148880   3% /mnt/music
/dev/sdc1            480719056    202796 456097060   1% /mnt/movies
charlie@ubuntu8:~$

```

CarolinaGuy

---

### Post by Iowan on 2009-02-11
> **CarolinaGuy said:**
> 
# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.125
 netmask 255.255.255.0
 network 192.168.1.[COLOR="Red"]1[/COLOR]
 broadcast 192.168.0.255
 gateway 192.168.1.1Probably not the issue, but the network address should probably be 192.168.1.0
BTW, the network and broadcast addresses *may* not be necessary at all.

---

### Post by CarolinaGuy on 2009-02-12
Iowan,

Still no go. Removed the two lines, no go, added them back in and changed last digit on network line to 1, still no go.

This NETWORK had been working flawless for some time.

After running for a few hours I may go to log on and it will again work flawless. Most of the time I will go to my WIRED desktop and log on then the wireless portion works perfectly.

CarolinaGuy

---

