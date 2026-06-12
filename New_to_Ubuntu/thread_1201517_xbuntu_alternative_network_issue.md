---
title: "xbuntu alternative network issue"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by mistypotato on 2009-07-01
Hello,

I installed xbuntu alternative on an old laptop.

I can ping OUT from the laptop to the Local Network but I cannot ping TO the laptop from any computer in the network.

It seems obvious that something on the laptop is blocking inbound traffic.

It is a pure vanilla default install, nothing at all has been added or modified.

My understanding is that xbuntu does NOT install a firewall by default so I'm at a loss as to what's going on here.  Any advice is appreciated.

thx

---

### Post by linoob13 on 2009-07-01
did you check the firewall setting?
there are settings that prevent ping answers!

---

### Post by mistypotato on 2009-07-02
There are 3 computers on the same local network including the xbuntu laptop.

I can ping (and get a reply from) all computers on the LOCAL network, but I cannot reach the Internet from the xbuntu laptop..

Only the xbuntu laptop is unable to connect to the Internet.  The other two connect fine.

It appears that the xbuntu laptop is preventing an Internet connection.

NO FIREWALLS are installed.

/etc/resolv.conf on the xbuntu laptop is identical to resolv.conf on the other 2 computers that are connecting to the Internet.

To me, this appears to be a firewall issue on the xbuntu laptop....but there is no firewall installed by default.

---

### Post by mistypotato on 2009-07-06
Well,

The solution was odd.

Since I could ping local network computers I knew the network was working....

I read the solution in another thread somewhere...

sudo /etc/init.d/networking restart

that's it....when I did that the Internet started working.

Not sure WHY I have to do that after booting and logging in but at least it works.

---

