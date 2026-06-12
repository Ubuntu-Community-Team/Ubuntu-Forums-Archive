---
title: "eth0 not detectet in dapper"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by erkka on 2007-05-29
Hello,

I just upgraded to dapper.
The result is, that my external mouse and ADSL-connection
are not working anymore. (they used to work fine in all
the previous distros I was using.)

I can do with the external mouse,
but internet connection is quite a necessary...


ifconfig eth0 says : ... device not found

I have tried in /etc/network/interfaces

both

  auto eht0

and
 
  mapping hotplug
  script grep
  map eth0

but no result


any ideas?

---

### Post by erkka on 2007-05-29
well, in GRUB I tried to boot with
kernel 2.6.12-10-386

result: external mouse working,
eth0 found

I still had to manually activate eth0,
then it works fine.

By default GRUB boots with kernel
2.6.15-28-386, which seems not to
recognize eth0 nor external mouse.

I'm rather new to linux/ubuntu, so could
somebody please help me, where to look at?


I guess it has something to do with
boot-up scripts?

---

