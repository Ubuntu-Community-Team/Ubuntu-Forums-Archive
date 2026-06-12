---
title: "sudo: unable to resolve host"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by czaravm on 2011-05-09
Im getting the "sudo:unable to resolve host ubuntu" every time i use the sudo command, but my /etc/hostname and my /etc/hosts files match up exactly.

applications start crashing all the time now and i dont know what to do.

---

### Post by bodhi.zazen on 2011-05-09
reboot and if the problem persists post the relevant contents of those files.

---

### Post by czaravm on 2011-05-09
This is my /etc/hosts file:

```
alec@ubuntu:~$ more /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

and this is my /etc/hostname file:

```
ubuntu

```
and just for good measure this is what happens while trying to use apt-get:


```
alec@ubuntu:~$ sudo apt-get install sabnzbdplus
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sabnzbdplus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up bcm5974-dkms (1.1.4) ...
Loading new bcm5974-1.1.4 DKMS files...

Error! Cannot locate /usr/src/bcm5974-1.1.4.dkms.tar.gz.
File does not exist.
dpkg: error processing bcm5974-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

(this error code is returned any time i try to use apt-get, and is not specific to the sabnzbd packages)

---

### Post by collisionystm on 2011-05-09
First thing to check is, can you ping the hostname? Ping ubuntu

Change your hosts file to read

Ubuntu 127.0.0.1 and try

Why is ubuntu in your hosts file anyways?

---

### Post by jtarin on 2011-05-09
[You can change your hostname (computername) easily.]("http://www.liberiangeek.net/2010/06/how-to-quickly-change-computer-name-in-ubuntu-10-04-lucid-lynx/")

---

### Post by czaravm on 2011-05-09
i tried to ping ubuntu, but that returned "unknown host ubuntu". and for my /etc/hosts file, what exactly do you want me to change?

---

### Post by jtarin on 2011-05-09
> **czaravm said:**
> i tried to ping ubuntu, but that returned "unknown host ubuntu". and for my /etc/hosts file, what exactly do you want me to change?I suggest to read the link I gave you and attempt to just change your hostname entirely form Ubuntu. Your files you submitted are in order. Maybe a re-generation of a hostname will take.

---

### Post by czaravm on 2011-05-09
Thanks, I tried that, but still am getting the exact same errors. I think that I will just have to reinstall ubuntu from the wubi installer.

---

### Post by compmodder26 on 2011-05-09
Can you post the output of "ifconfig".  I'm specifically wanting to make sure you have lo (loopback) up.

---

### Post by czaravm on 2011-05-10
thanks so much for the help, here it is:
```

alec@lappy3001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:bc:dd:11:c8  
          inet addr:129.210.136.48  Bcast:129.210.137.255  Mask:255.255.254.0
          inet6 addr: fe80::225:bcff:fedd:11c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58893 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75714550 (75.7 MB)  TX bytes:8352835 (8.3 MB)
          Interrupt:45 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:25:00:4d:86:86  
          inet addr:129.210.218.181  Bcast:129.210.219.255  Mask:255.255.252.0
          inet6 addr: fe80::225:ff:fe4d:8686/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2679 errors:0 dropped:0 overruns:0 frame:63313
          TX packets:205 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:162638 (162.6 KB)  TX bytes:33687 (33.6 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)
```

---

### Post by jtarin on 2011-05-10
> **czaravm said:**
> Thanks, I tried that, but still am getting the exact same errors. I think that I will just have to reinstall ubuntu from the wubi installer.
There's no reason to install WUBI......if your going to reinstall do a standard reinstall and pay attention during setup when it ask you to name your host (computername)and give it a name instead of letting setup choose.

---

### Post by czaravm on 2011-05-10
yeah, but i did this install using wubi, is it possible to just wipe the virtual disk and install a new 11.04 distro over it?

---

### Post by jtarin on 2011-05-10
I can't advise about WUBI. I don't use it. I would recommend to install Ubuntu in its own partition as you will get the full benefit without these WUBI-centric problems.I would also advise installing a more stable release than 11.04.

---

### Post by bodhi.zazen on 2011-05-10
It is an odd problem. My only other thought would be to check in network manager and make sure the hostname is set there as well.

---

### Post by collisionystm on 2011-05-10
> **czaravm said:**
> Im getting the "sudo:unable to resolve host ubuntu" every time i use the sudo command, but my /etc/hostname and my /etc/hosts files match up exactly.

applications start crashing all the time now and i dont know what to do.


I figured this out for you.

First do this command

```
cat /etc/hostname
```

Copy the output of the hostname

```
sudo nano /etc/hosts
```

I just tested on mine, making the hostname and hosts file entry different. It messes up sudo. This will make sure your hosts file matches the hostname and get you up and going

---

### Post by sisco311 on 2011-05-10
I had the same issue on a fress oneiric install. Solved it by editng my hosts file to:
```
127.0.0.1	localhost.localdomain localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Don't ask me why, but it worked. :)

---

### Post by bodhi.zazen on 2011-05-10
The OP posted the contents of /etc/hostname and /etc/hosts in post #3 and they match.

---

### Post by The Cog on 2011-05-10
How about the contents of /etc/resolv.conf - maybe it's not using the /etc/hosts file?

---

### Post by debd on 2011-05-10
the problem is, I think , with the /etc/resolve.conf file.
edit the file with
```
sudo nano /etc/resolve.conf
```
and add the namesevers of your service provider like this:
```
nameserver 192.168.1.1
```

replace the ip address with the nameserver address given by your service provider.

---

### Post by The Cog on 2011-05-10
or maybe the problem is with /etc/nsswitch.conf - this says whether to even use /etc/resolv.conf. If it helps, this is the contents of my nsswitch.conf:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by collisionystm on 2011-05-10
Check your files to make sure there are no spaces before or after your host names.

Only tabs can be used for spaces, and there should not be any empty space after the word ubuntu on that line

---

### Post by czaravm on 2011-05-11
THANK YOU GUYS!!!!

I took a look at my /etc/nsswitch.conf file, and changed it, and I also realised that there was an extra space after my hostname... and problem solved I can use sudo now.

Seriously guys, you are what makes ubuntu so great. Thanks a ton!

---

### Post by bodhi.zazen on 2011-05-11
> **czaravm said:**
> THANK YOU GUYS!!!!

I took a look at my /etc/nsswitch.conf file, and changed it, and I also realised that there was an extra space after my hostname... and problem solved I can use sudo now.

Seriously guys, you are what makes ubuntu so great. Thanks a ton!

congrats.

Good call The Cog

---

### Post by BrokeBody on 2012-05-22
I fixed it by adding this line to my hosts file:

```
127.0.0.1	       computer-name
```

---

### Post by oldos2er on 2012-05-22
Old thread closed.

---

