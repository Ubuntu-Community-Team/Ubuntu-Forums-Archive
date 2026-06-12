---
title: "bind permission denied for jnl file"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by twistedtwig on 2006-10-10
Hi all,

I thought i had bind working correctly but seems i dont fully.

i want to have a static ip that is given out from the dhcp server.  That is working but it doesnt seem to be able to create the jnl file.

> 
Oct 10 12:05:06 localhost named[3726]: journal file /etc/bind/db.10.168.192.jnl does not exist, creating it
Oct 10 12:05:06 localhost named[3726]: /etc/bind/db.10.168.192.jnl: create: permission denied
Oct 10 12:05:06 localhost dhcpd: unable to add reverse map from 100.10.168.192.in-addr.arpa. to bobby.ponywarshome.local: timed out


my permissions are as follows:

> 
-rwxrwxr-x 1 bind bind   237 2006-08-30 19:21 db.0
-rwxrwxr-x 1 bind bind   368 2006-08-30 19:21 db.10.168.192
-rwxrwxr-x 1 bind bind   271 2006-08-30 19:21 db.127
-rwxrwxr-x 1 bind bind   237 2006-08-30 19:21 db.255
-rwxrwxr-x 1 bind bind   353 2006-08-30 19:21 db.empty
-rwxrwxr-x 1 bind bind   256 2006-08-30 19:21 db.local
-rwxrwxr-x 1 bind bind   279 2006-08-30 19:21 db.ponywars
-rwxrwxr-x 1 bind bind 12442 2006-10-10 08:28 db.ponywars.jnl
-rwxrwxr-x 1 bind bind  1507 2006-08-30 19:21 db.root
-rwxrwxr-x 1 bind bind   388 2006-08-30 19:21 logging.conf
-rwxrwxr-x 1 bind bind  2383 2006-08-30 20:13 named.conf
-rwxrwxr-x 1 bind bind   412 2006-08-30 20:11 named.conf.local
-rwxrwxr-x 1 bind bind   685 2006-08-30 19:21 named.conf.options
-rwxrwxr-x 1 bind bind    77 2006-08-30 19:21 rndc.key
-rwxrwxr-x 1 bind bind  1317 2006-08-30 19:21 zones.rfc1918


not sure what else i shoudl be posting to be honest.  any and all help MORE than welcome.  rather confused to be honest.

Cheers

Twiggy

---

### Post by twistedtwig on 2006-10-10
reposted in server thread as i feel that was more approprate.  sorry for double post.

Twiggy

---

### Post by djdvant on 2008-04-24
After much hair pulling over several months I finally got to the problem.  My DNS and DHCP files were OK and always had been.

I finally tracked down an kernel audit message


kernel:  audit(1209076817.081:16): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/bind/xxxxx.com.hosts.jnl" pid=16561 profile="/usr/sbin/named" namespace="default"

So I had a look in:
/etc/apparmor.d/usr.sbin.named

and changed this line:
  /etc/bind/** r,

to this:
  /etc/bind/** rw,

End of problems

---

### Post by twistedtwig on 2008-04-25
HUH!!! is the a dodgy post????

---

### Post by NIT006.5 on 2008-05-25
> **djdvant said:**
> 
So I had a look in:
/etc/apparmor.d/usr.sbin.named

and changed this line:
  /etc/bind/** r,

to this:
  /etc/bind/** rw,

End of problems

First off, thank you! Having previously been running dynamic dns on fedora servers, I'm not too familiar with apparmor so hadn't even thought of looking there.

Since I'm also running this in a fairly "closed" environment, I've just done what you suggested, and yes it solves the problem for me. However, this might not be the correct route to follow on a public server. As stated in usr.sbin.named comments, /etc/bind should be read only to bind and dynamic zones as well as journal files should be stored in /var/lib/bind/, which already has rw permissions set for bind. However, dynamic zones and journal files seem to be stored in /etc/bind/ by default. So ideally, you'd want to change this location to /var/lib/bind. I would assume this has been done for security reasons.

---

