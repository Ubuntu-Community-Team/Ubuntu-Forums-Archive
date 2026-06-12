---
title: "[SOLVED] Static IP help"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by lemmy999 on 2008-10-02
I am trying to setup a small network at home using NFS. I know that I need static IP's on all my machines. 

I have the following settings- router reports that it currently assigns 192.168.1.66 to my PC. Routers IP is 192.168.1.254 ( I think). Using System>Admin>networking I have set up a static IP using those values. However after confirming changes I cannot access the internet. What simple mistake am I making here?

---

### Post by rolnics on 2008-10-02
I've just done  a quick search on the forums and can't find anything else that can help, but I did find a howto elsewhere.

Take a look at this [Static IP HOWto]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html"), I'm not sure if it will help, but it's a start.

---

### Post by dacorr on 2008-10-02
could you tupe ifconfig in terminal and post results?

dac

---

### Post by lemmy999 on 2008-10-02
This is my ifconfig ( but i have changed back to DHCP)
> eth0      Link encap:Ethernet  HWaddr 00:14:2a:ec:d3:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:50:bf:80:2b:a4  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:fe80:2ba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15630675 (14.9 MB)  TX bytes:3175393 (3.0 MB)
          Interrupt:20 Base address:0xe900 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74383 (72.6 KB)  TX bytes:74383 (72.6 KB)


Just checked /etc/network/interfaces
> auto lo
iface lo inet loopback

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


Where does eth2 come from?

---

### Post by wizard10000 on 2008-10-02
> **lemmy999 said:**
> I am trying to setup a small network at home using NFS. I know that I need static IP's on all my machines. 

I have the following settings- router reports that it currently assigns 192.168.1.66 to my PC. Routers IP is 192.168.1.254 ( I think). Using System>Admin>networking I have set up a static IP using those values. However after confirming changes I cannot access the internet. What simple mistake am I making here?

Let's think about this a little differently.  Rather than hardcoding an IP address on a workstation what about using a MAC reservation on the router?  On my work network (and on my home network) all workstation static IPs are assigned by the DHCP server, not reserved on the workstation.  The reason for this is that creating nonstandard configurations increases support costs  :D

So if you wanted your router to assign 192.168.1.66 to your PC all the time all you have to do is tell the router that that address is reserved for MAC address 00:14:2a:ec:d3:b0.

At home I have two Linux boxes, one networked printer and the spousal unit's Windows machine all happily receiving static IP addresses from the router instead of hardcoding them on the local device.  NFS shares between the Linux boxes and Windows shares through samba work just fine.

---

### Post by lisati on 2008-10-02
> **wizard10000 said:**
> Let's think about this a little differently.  Rather than hardcoding an IP address on a workstation what about using a MAC reservation on the router?  On my work network (and on my home network) all workstation static IPs are assigned by the DHCP server, not reserved on the workstation.  The reason for this is that creating nonstandard configurations increases support costs  :D

So if you wanted your router to assign 192.168.1.66 to your PC all the time all you have to do is tell the router that that address is reserved for MAC address 00:14:2a:ec:d3:b0.

At home I have two Linux boxes, one networked printer and the spousal unit's Windows machine all happily receiving static IP addresses from the router instead of hardcoding them on the local device.  NFS shares between the Linux boxes and Windows shares through samba work just fine.

Sounds good....I use address reservation based on MAC address as well, one for my desktop's wireless, another for my laptop's wireless, and another for the same laptop when it's plugged in to a wired port (saves having to remember to disable wireless on it)


<aside>I've just noticed I've started to unconsciously capitalise the word Desktop, corrected in above rant</aside>

---

### Post by lemmy999 on 2008-10-02
@wizard1000

Sounds like a good idea. I'll give that a go instead!

---

### Post by lemmy999 on 2008-10-02
Don't I need static IP addresses to make NFS work?

---

### Post by wizard10000 on 2008-10-02
> **lemmy999 said:**
> Don't I need static IP addresses to make NFS work?

NFS doesn't care what the IP address is or how the workstation got it but if the IP address changes it'll break your connection.  You can do name-based NFS but something has to keep track of hostname to IP address changes - IMO static IPs are the way to go.

---

### Post by rolnics on 2008-10-02
> **wizard10000 said:**
> what about using a MAC reservation on the router?

That's a brilliant answer wizard10000! I will have to keep that answer, as that might be of use to me in the near future!

---

### Post by lemmy999 on 2008-10-02
OK- I have set up the server/client for NFS using Wizard1000's suggestion. I can ping both client and server. I have done all the NSF install stuff on both machines but am stumped mounting the shared folder on the server. this is my output
> chris@chris:~$ sudo mount server 192.168.1.66:/home /mnt/home
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


What am I doing wrong?

---

### Post by Iowan on 2008-10-02
> sudo mount ServerIP:/folder/already/setup/to/be/shared /home/username/folder/in/your/local/computer taken from [https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts]("https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts")

I think I missed the space in your line between "home" and "/mnt"... 
but the word "server" might be confusing the issue.

---

### Post by lemmy999 on 2008-10-03
@Iowan

You are right, the use of server was incorrect and I have removed it. now i am getting the following
> mount.nfs: mount to NFS server 'alpha' failed: timed out, retrying

???????????

I think I have partially solved it. Turning off the firewall on the server now gives 
> mount.nfs: alpha:/home failed, reason given by server: Permission denied


Now I've got it. I've been trying so many different things out that I was trying to mount an old server config.

---

### Post by Iowan on 2008-10-03
> **lemmy999 said:**
> Now I've got it. I've been trying so many different things out that I was trying to mount an old server config.Fixed?  If so, mark this one [SOLVED] (under Thread Tools) and go celebrate.  :popcorn:

---

### Post by lemmy999 on 2008-10-04
I had amended the title of my original post to reflect the resolution of this problem. Unfortunately thats not the correct way to do it:oops:

Now marked appropriately!!

---

