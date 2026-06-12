---
title: "Re: what is my computer's internal IP address?"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by stevieP on 2008-06-21
> **tturrisi said:**
> ```
ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'
```

Nice command [tturrisi]("http://ubuntuforums.org/showthread.php?p=5235032#post5235032").

I tried to put into my .bashrc file as an alias:
```
alias getip="/sbin/ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | gawk '{print $1}' "
```
but it gives output:
```
%  192.168.xxx.xxx Bcast
```

i.e. my ip address with the text "Bcast" after it.
(for both awk and gawk)
For some reason gawk is not working on the alias line?...

---

### Post by Sef on 2008-06-21
Moved from the archives to the networking and wireless forum.

> For some reason gawk is not working on the alias line?... 

The command is not gawk, but awk.  

>  Originally Posted by tturrisi  View Post
Code:

ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'



---

### Post by stevieP on 2008-06-22
> **Sef said:**
> The command is not gawk, but awk.

Thanks Sef, however as I mentioned above, this alias did not work for either "awk" or gnu's implementation of awk ("gawk"). In fact at least on my computer gawk and awk are the same command, with awk eventually linking over to gawk:
```

 $ ll /usr/bin/gawk 
-rwxr-xr-x 1 root root 299124 2007-05-15 10:50 /usr/bin/gawk*
$ ll /usr/bin/awk 
lrwxrwxrwx 1 root root 21 2008-03-21 15:17 /usr/bin/awk -> /etc/alternatives/awk*
$ ll /etc/alternatives/awk
lrwxrwxrwx 1 root root 13 2008-04-14 01:13 /etc/alternatives/awk -> /usr/bin/gawk*
```

---

### Post by kevdog on 2008-06-22
Not sure why that isnt working but how about this:

ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | cut -d' ' -f1

---

### Post by xebian on 2008-06-22
> **stevieP said:**
> Nice command [tturrisi]("http://ubuntuforums.org/showthread.php?p=5235032#post5235032").

I tried to put into my .bashrc file as an alias:
```
alias getip="/sbin/ifconfig  | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | gawk '{print $1}' "
```
but it gives output:
```
%  192.168.xxx.xxx Bcast
```

i.e. my ip address with the text "Bcast" after it.
(for both awk and gawk)
For some reason gawk is not working on the alias line?...

Why make it so complicated?  To find out your box ip address, just type ifconfig and it will show the address of each nic card.  Here is what mine looks like

```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a9:3c:e0
          [COLOR="Red"]inet addr:192.168.1.3 [/COLOR] Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea9:3ce0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2959705 (2.8 MB)  TX bytes:363111 (354.6 KB)
          Interrupt:18 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```

---

### Post by steveneddy on 2008-06-22
An IP address that starts with 192. is for a LAN, and the PC's internal IP for itself is always 127.0.0.1 (home).

I guess define "internal"

Private LAN address or inside of the PC?

---

### Post by stevieP on 2008-06-25
> **kevdog said:**
> Not sure why that isnt working but how about this:
ifconfig | grep 'inet addr:'| grep -v '127.0.0.1' | cut -d: -f2 | cut -d' ' -f1
Yes, that worked! I'm also not sure why the command with gawk didn't work... it works fine from the command line.  

> Why make it so complicated? To find out your box ip address, just type ifconfig and it will show the address of each nic card. Here is what mine looks like
kevdog's script lines are just parsing through that output xebian- if you alias a command to that in your bash file you only ever have to type it once. Now I can type "getip" on the command line and I have mine.

---

