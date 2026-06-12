---
title: "Need help with wi fi connection..."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by memecs on 2009-08-20
Hello,
i just installed ubuntu 9.04 2 weeks ago and i am having problemswith the internet connection... it is much slower than usual and i lost it every 3 minutes for 10 seconds.
I tried some stuff i found on internet ( disabling ipv6 etc..) but nothing i have still problems... I use a wifi connetion with airport express as router...

someone could help me?
thanks a lot

---

### Post by sandyd on 2009-08-20
can you post  the output of
```

lspci

```

it doesn't come to me how to do this right now, but did you try lowering the bitrate?

EDIT: memory came back
```

iwconfig wlan0 rate 5.5M fixed

```

---

### Post by iver2435 on 2009-08-21
Could it be as simple as you're too far away from the wireless router??

Weak/failing connection + slow speed...  it could be.

Try checking if the connection improves if you move next to the router.

---

### Post by memecs on 2009-08-21
hello Carly,

```
lspci | grep Network:
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)


```i tried to set up the bitrate, but nothing changed... i am downloading the same file at 1.7MB with my laptop and 160kb with ubuntu...

---

### Post by memecs on 2009-08-21
> **iver2435 said:**
> Could it be as simple as you're too far away from the wireless router??

Weak/failing connection + slow speed...  it could be.

Try checking if the connection improves if you move next to the router.


Actually it couldn' be closer, i am using a wifi connection just because Airport doesn't have any ethernet port...

---

### Post by sandyd on 2009-08-21
perhaps you need
```

sudo apt-get install linux-backports-modules-jaunty
```
according to

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/354548](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/354548)

---

### Post by sandyd on 2009-08-21
also, please take a look at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297965)

and

[https://bugs.launchpad.net/bugs/333730](https://bugs.launchpad.net/bugs/333730)

and

[http://ubuntuforums.org/showthread.php?t=955814](http://ubuntuforums.org/showthread.php?t=955814)

p.s. on the last link, the solution is on the last page, not the first

---

### Post by memecs on 2009-08-21
carlee... great, problem solved... the solution was changing the drivers...
> **carlee said:**
> [http://ubuntuforums.org/showthread.php?t=955814](http://ubuntuforums.org/showthread.php?t=955814)

thanks a lot for your help...
federico

---

### Post by cataztrophe on 2009-08-22
many-many thanx for carlee!!
coz i got some problem like this too!

---

