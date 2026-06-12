---
title: "Avahi unicast .local domain"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by PerH on 2007-04-27
Hi after upgrading to Feisty I get an error message each time I login about Avahi not being able to start.

Trying to start the daemon manually gives me:
```

per@pers:~$ sudo /etc/init.d/avahi-daemon start
* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon
* avahi-daemon disabled because there is a unicast .local domain

```

The standard answer everyone seems to give is this site: 
[http://avahi.org/wiki/AvahiAndUnicastDotLocal]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")
Which says: 
*If you come across a network where .local is a unicast DNS domain, please contact the local administrator and ask him to move his DNS zone to a different domain.*.

I would really like to get avahi running and since I i'm the local home network administrator what should I do?

Here are some of my config files:
```

per@pers:~$ cat /etc/hosts

127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

```

per@pers:~$ cat /etc/nsswitch.conf

passwd:         compat
group:          compat
shadow:         compat

#hosts:          files dns mdns
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
#hosts: files dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

My Ubuntu router does not have any DNS services installed and only serves DHCP and NAT and I've not configured any domains as far as I know. Can suggest how to solve this?
I've tried assigning a random domain name using the System->Administration->Network tool, but without any differences.

// Per Hermansson

---

### Post by timrichardson on 2007-04-28
The original post describes my question exactly. Posting this is my attempt to subscribe to this thread.

---

### Post by FilCab on 2007-04-29
Bump?
I also have this problem and can't figure out how to fix it :s

---

### Post by perstromgren on 2007-05-01
Same problem here, only that I don't know what is not working!

What is Avhi?

Per.

---

### Post by keptang on 2007-05-01
Same issue here, how do we get rid of the message and fix the issue?

---

### Post by PerH on 2007-05-02
> **perstromgren said:**
> Same problem here, only that I don't know what is not working!

What is Avhi?

Per.

As said on [wikipedia]("http://en.wikipedia.org/wiki/Avahi_%28software%29"): 
> It allows programs to publish and discover services and hosts running on a local network with no specific configuration.
For example you can find printers connected to the network or explore shared network files without the need for any configuration you simple explore the network like you explore your local file system.

If you don't want Avahi enabled you can disable the service from the menu:
System->Administration->Network. In the General tab uncheck the *Automatic service discovery* checkbox.

What I don't know is how to enable Avahi when it complains about having a .local domain.

// Per Hermansson

---

### Post by PerH on 2007-05-05
I've had some updates on this issue.

After I login I still get the Avahi error about using a unicast .local domain and the avahi daemon is not started.

After login I open a terminal and type the following:
```

sudo rm /var/run/avahi-daemon/disabled-for-unicast-local
sudo /etc/init.d/avahi-daemon start

* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ]

```

So the avahi daemon actually starts now. I've also tested to revert my changes in */etc/nsswitch.conf* as the suggested workaround on [http://avahi.org/wiki/AvahiAndUnicastDotLocal]("http://avahi.org/wiki/AvahiAndUnicastDotLocal").

The *disabled-for-unicast-local* file that I delete gets created after I reboot so this is only a temporary solution. Something is probably going wrong during my boot process.
This problem could be related to [bug #111834]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/111834"). I don't know if I should open a new bug ticket on this?

// Per Hermansson

---

### Post by moixa on 2007-05-06
me having the same problem

---

### Post by abdulet on 2007-06-21
me too

---

### Post by reacocard on 2007-08-12
I am also afflicted by this problem, a solution would be great.

---

### Post by pelle.k on 2007-08-21
> I've tried assigning a random domain name using the System->Administration->Network tool, but without any differences.
Well, you're not supposed to assign a domain name in the _client_ (that is your _computer_) but rather the router. My router has a "local domain name (optional)" in it's "LAN" settings. Setting this value to "lan" (without a dot, in my case...) solved this issue for me. That gets added to my computer name, so in effect my computer is pelle-desktop.lan as well as just pelle-desktop.
As a side note, it was _not_ enough to leave that setting untouched (or blank if you will) in my router. I had to set a domain name.

I no longer have this message;
```
your current network has a .local domain, which is not recommended and incompatible with the Avahi network service directory...
```

If this doesn't work, then just turn of "avahi" or "mdns name resolution" in "network manager".

---

### Post by Gabbe on 2007-08-30
There is a work around and some information on Avahi's site: [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal)

---

### Post by notwen on 2007-09-12
Might this be the same error I'm having during startup and Avahi mDNS/DNS-SD service fails to start correctly, interrupts my nice transition from the Ubuntu loading screen to GDM w/ a glimpse of services starting and right before GDM kicks in I see Avahi failing?  Please say this issue would be the cause. =]

---

### Post by merlin666 on 2007-09-12
I had a few devices with an avahi extension, such as wlan0:avahi - when I did searches I got the impression that this may refer to a faulty device. Fortunately, re-booting or re-starting the device has removed avahi and made the device functional again.

---

### Post by nealmcb on 2007-11-21
> **pelle.k said:**
> Well, you're not supposed to assign a domain name in the _client_ (that is your _computer_) but rather the router. My router has a "local domain name (optional)" in it's "LAN" settings. Setting this value to "lan" (without a dot, in my case...) solved this issue for me. That gets added to my computer name, so in effect my computer is pelle-desktop.lan as well as just pelle-desktop.
As a side note, it was _not_ enough to leave that setting untouched (or blank if you will) in my router. I had to set a domain name.

pelle.k, Thanks for this report.  This is the first I've heard of a router grabbing .local, seemingly by default.

Which router is it?  Can you explain in a bit more detail how you found that configuration parameter, for others that may not know how to find it?  E.g. via a browser?

---

### Post by pelle.k on 2007-11-21
The router is a "d-link dl-624+", and you can administer it through a browser (use the gateway address...)
I'll attach a screenshot of this from my particular router.

---

