---
title: "sudden internet death syndrome"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by polkadotchickens on 2008-02-06
So, my internet connection keeps on crapping out, and although this is due in part to my terrible service (not a Clearwire fan, curse their two-year contract!), I think there are also some software issues at play that I'm hoping someone will have some insight on.

My setup:
Clearwire modem, plugged in directly to a desktop running 7.10.
Internet connection shared through another ethernet port on same, set up using firestarter.
Ethernet cable connecting laptop (also running 7.10) to desktop.
Firestarter is set to give a fixed ip address.

I can probably dig up more specifics if you need it -- I didn't actually do the setup, and the weirdness of it is to allow multiple people to use the internet at once without buying a router.  

My problem is: laptop browsing is very unstable.  I'll be happily browsing away, click a link, and BAM no connection.  Weird thing is that the internet on the desktop is unaffected.  A couple times, it's turned out that firestarter wasn't running (which is weird, because it's supposed to start up on boot), but right now firestarter's running, the clearwire connection is good, and internet is fine on desktop (that's where I'm posting), but no go on the laptop.  My general fix-it procedure that works about 30% of the time is to: 1. restart modem, 2. dhclient the net connection on the desktop, 3. restart firestarter, 4. restart networking on the laptop.  This is inconvenient even when it works, and most of the time it doesn't.

Ideas?

---

### Post by zekica on 2008-02-06
Could you please post the output of:
On the desktop (where internet sharing is enabled)
```
sudo iptables -L
sudo iptables -t nat -L
cat /proc/sys/net/ipv4/ip_forward
cat /etc/dhcpd.conf
ifconfig
ps ax | grep dhcpd
route
```
and on laptop:
```
ifconfig
route
```

You can enter these commands in Terminal (Applications -> Accessories -> Terminal).

---

