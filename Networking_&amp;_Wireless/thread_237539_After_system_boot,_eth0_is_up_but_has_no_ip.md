---
title: "After system boot, eth0 is up but has no ip"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by do77 on 2006-08-16
my env: ubuntu 6.06

my config:
All is OK,
and eth0 in /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp

description:
After system boot, eth0 cannot get IP though dhcp.
But if I ifdown eth0 & ifup eth0, then I can get IP.
Then I check my /etc/rcS.d/, find in /etc/init.d/networking, when "ifup -a", the eth0 has already up(but do not get IP), so /etc/init.d/networking do nothing.
then I find in /etc/init.d/udev, when run "udevplug", eth0 is up without IP.

I find when system is booting, after /etc/rcS.d/S10udev run, the 2 thead is appeared and keep exist.
root 2322 1 0 22:24 ? 00:00:00 /sbin/ifup --allow auto eth0
dhcp 2382 2322 0 22:24 ? 00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0


Please tell me why I have this problem, 
Should udevplug make eth0 up?
Or This is a bug of ubuntu?

---

### Post by do77 on 2006-08-18
I find when system is booting, after /etc/rcS.d/S10udev run, the 2 thead is appeared and keep exist.
root 2322 1 0 22:24 ? 00:00:00 /sbin/ifup --allow auto eth0
dhcp 2382 2322 0 22:24 ? 00:00:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0

---

### Post by davesgonebananas on 2006-10-07
I have exactly the same the problem.  I get no IP address after boot but a simple ifdown eth0; ifup eth0 solves the problem.  

Any further help/info would be appreciated as this is my first Ubuntu install  and no config files have been touched by me as yet.

---

### Post by Abiezer on 2006-10-14
Bumping this as I have the same problem too, on 6.06. 
My DSL connection used to start fine on boot, but now doesn't. I have a suspicion it started after the last kernel upgrade, but can't be sure as I have this box up for a long time and only noticed after an infrequent restart.
Reactivating eth0 does get me online, but would love a proper fix. I have checked a number of threads on the forum mentioning similar problems but haven't seen a fix.

---

### Post by myfreelunch on 2006-10-15
I was having the same problem, no IP granted from my Linksys router.  My fedora system had been up for 6 months without problem, it reset over night (no apparent reason) and when I logged back in, no IP.  I powered down, removed my card (3 com), installed another one I had laying around (HP), rebooted, fedora recognized my old HW was gone, and a new card was installed.  Ran the configuration program for the new card, still no IP...  I installed my old 3com card again and this time, I got the IP address assigned.  

Not a very elegant fix but it worked...

---

### Post by NeoLithium on 2006-10-15
Check to make sure all your auto eth0 and pre-up information is in the /etc/network/interfaces above your provider information, as it appears below.

That was how I fixed my problem with it.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

    pre-up /sbin/ifconfig eth0 up
#Lines below this point, should be on the bottom of the file for you as well.

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```

---

