---
title: "Cannot mount samba share"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by mority on 2007-06-02
Hi,

in my home network I run a file server with a samba server installed. Now I want to mount my samba shares on my notebook running Ubuntu 7.04.

I'm trying to do it like this:
```

root@ash:~# mount -t smbfs -o username=mo,password=xxx //apparat/mo/ /mnt/apparat/
mount: wrong fs type, bad option, bad superblock on //apparat/mo/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
Everytime I try it, this line appears in dmesg and in /var/syslog:
```

[427701.408000] smbfs: mount_data version 1919251317 is not supported

```

When I try to do it with CIFS instead of SMBFS like this:
```

root@ash:~# mount -t cifs -o username=mo,password=xxx //apparat/mo/ /mnt/apparat/
mount: wrong fs type, bad option, bad superblock on //apparat/mo/,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
this line appears in dmesg and syslog:
```

[427008.144000]  CIFS VFS: cifs_mount failed w/return code = -22

```

And I'm pretty sure the error is not caused by the samba server, because I have a Gentoo system from which I am able to mount the samba share perfectly with the CIFS variant. I'm using exactly the same mount command there...

I would be very happy about any suggestions :)

---

### Post by alan1974us on 2007-06-02
I'm a newbie, but why not use smbmount?

---

### Post by dmizer on 2007-06-02
you're in a root prompt, i'd suggest avoiding that.

as root:
```
aptitude install smbfs
```
or as normal user:
```
sudo aptitude install smbfs
```

if that doesn't work, can you ping apparat?

---

### Post by mority on 2007-06-02
Thanks for your answers!

alan1974us: smbmount is just a wrapper for 'mount -t smbfs'. Look at 'man smbmount'.

dmizer: I installed smbfs package, but now I get a different error.

```

root@ash:~# ping apparat
PING apparat.lan.agrav.org (192.168.1.50) 56(84) bytes of data.
64 bytes from apparat.lan.agrav.org (192.168.1.50): icmp_seq=1 ttl=64 time=0.187 ms

```

```

root@ash:~# mount -t cifs -o username=mo,password=xxx //apparat/mo/ /mnt/apparat/
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

The login credentials are certainly correct. As I said, I am able to mount the share with the exact same command on my Gentoo box...

---

### Post by dmizer on 2007-06-02
change "apparat" to apparat's actual ip address and you should be fine.  if it's dhcp ... you should consider configuring your router so that your server pulls the same ip.  that, or you can check out the second link in my sig for more information on configuring winbind which will allow host names to work in samba.

---

### Post by mority on 2007-06-04
Using the IP address instead of the hostname does not change anything. And I don't see at all why it should. apparat does have a fix IP address in my home network which is resolvable through an internal DNS server. And, if name resolving issues were the source of the problem, why does it work when I use the exact same command on my Gentoo box?

---

### Post by dmizer on 2007-06-04
well, frankly it doesn't matter how many other machines have no problems.  the fact is that the error says that it can't find the server's location as you've typed it.  it doesn't matter if you have a local dns server resolving your host names, or wins resolving, or hosts resolving ... the error says it can't find the server.  so ... the easiest way to determine if the host name is the issue is to replace the host name with it's ip address.  it's a simple troubleshooting technique, not an affront to your ability to set up a proper network.

please try this mount command instead:
```
mount -t cifs //apparat/mo/ /mnt/apparat/ -o username=mo,password=xxx
```
again ... simple troubleshooting technique here.  the syntax order you have given is incorrect.  reality is that it shouldn't make a difference, but you have an error ... so the best way to track down an error is to eliminate all potential trouble spots.

---

### Post by mority on 2007-06-04
dmizer, first of all: Thanks for your help and sorry if I sounded somewhat rude. I don't feel offended and hope you do neither.

And I think I found the source of the problem. It's rather stupid: The mount command does not like the trailing slash after the remote host.

So, this doesn't work:
```

mount -t cifs //apparat/mo**[COLOR=Red]/[/COLOR]** /mnt/apparat -o username=mo,password=xxx

```But this does work:
```

mount -t cifs //apparat/mo /mnt/apparat -o username=mo,password=xxx

```

---

### Post by dmizer on 2007-06-04
> **mority said:**
> dmizer, first of all: Thanks for your help and sorry if I sounded somewhat rude. I don't feel offended and hope you do neither.

And I think I found the source of the problem. It's rather stupid: The mount command does not like the trailing slash after the remote host.

So, this doesn't work:
```

mount -t cifs //apparat/mo**[COLOR=Red]/[/COLOR]** /mnt/apparat -o username=mo,password=xxx

```But this does work:
```

mount -t cifs //apparat/mo /mnt/apparat -o username=mo,password=xxx

```
no offense taken.  i didn't intend to come off as though i was offended.  i just wanted to take the opportunity to add a little insight into how i approach a problem.  sometimes simple fixes to problems are missed because of, "i don't see why it should make a difference"

lol ... that said, i can't believe i missed the "/" at the end of the path name.  i know that breaks things.  so much for practicing what i preach eh?

---

### Post by mority on 2007-06-04
> **dmizer said:**
> 
lol ... that said, i can't believe i missed the "/" at the end of the path name.  i know that breaks things.  so much for practicing what i preach eh?

Hehe, anyways, I'm glad to have this issue solved. Thanks again for your time :)

---

