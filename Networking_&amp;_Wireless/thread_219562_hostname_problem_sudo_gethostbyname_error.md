---
title: "hostname problem: sudo gethostbyname error"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by naught101 on 2006-07-20
ok, this is the same error as [this one]("http://ubuntuforums.org/showthread.php?t=78324"), but since there was no resolution there from me, and as I am having this problem in dapper, I decided to post it here as well.
--------
> **MoshNet said:**
> Ok, whenever I try to complete a command, like sudo, I get this error..
```

ssga@:~$ sudo chmod 666 /dev/dsp
sudo: unable to lookup  via gethostbyname()

```
--------
got exactly the same problem here, except my /etc/hosts appears all correct:
```
127.0.0.1 localhost.localdomain localhost np

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
and my nsswitch.conf:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns mdns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
and the eth0 entry from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:21:23:9E
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe21:239e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4683 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5327544 (5.0 MiB)  TX bytes:426476 (416.4 KiB)
          Interrupt:169


```
ping localhost works fine.

when I run hostname as root, it looks like this:
```
root@naughttop:/home/naught101# hostname

root@naughttop:/home/naught101# 
```ie. ther is no hostname, which makes me think, I deleted my host name from kcontrol>>network settings>>hostnames (can't remember, I can't open it right now). and that was probably the point where it all went sideways.
if I run "hostname np" as root, it fixes it, so that sudo works, and the response to "hostname" is "np", but then I get "KLauncher could not be reached via DCOP" errors when ever I try to open something from a KDE icon. I've tried searching the forums for ways to fix the DCOP errors, but I haven't found anything to help.

the host name resets everytime I reboot, to ""
[QUOTE=stevea1210]Thank you so much nocturn. I've been battling this one for days. Everything in the forums say it is your /etc/hosts file. I knew that wasn't the case in my situation. For me, It was my nsswitch.conf. I had joined all of ubuntu boxes to my win 2k3 AD domain, and screwed up the nsswitch.conf on this one. I owe you one.[/QUOTE]that looks promising, but I don't know what I should be fixing in my nsswitch.conf if that is the problem. I tried putting "np" in the "hosts:" field after the others, but it didn't work.

when you change the hostname in the network setting through kcontrol, what files does it change? perhaps if I know that I can change it back. I figure changing it back through kcontrol would fix it, but either sudo doesn't work, or if sudo does work, DCOP stuffs up (I don't understand it), and I can't open kcontrol anyway. I tried opening kcontrol from a root terminal, but I get error messages saying that, among other x errors, "kcontrol: cannot connect to X server :0.0"

PLEASE, any help with this would be greatly appreciated.

---

### Post by naught101 on 2006-07-20
HAHA!! got it!

need to edit **/etc/hostname** and add <hostname> to read simply:
```
np
```
simple. won't do that again.

thanks to **aleoje** in [this thread]("http://http://ubuntuforums.org/showthread.php?t=188337")

someone can delete this thread, I will post this answer in the other one.

---

### Post by naught101 on 2006-07-20
_Suggestion to Ubuntu maintainers:_
NEVER let anyone put a zero-sized entry into the Kcontrol>>Network Settings>>Domain Name System>>Hostname field. this will kill all newbies on the spot.

---

