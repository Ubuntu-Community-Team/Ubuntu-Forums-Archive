---
title: "Permissions on /etc/resolv.conf changing at boot"
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by mariner09 on 2006-11-13
This just started happening recently.  I'm not sure what's causing it, but every time I hard boot my machine, something is changing the permissions on /etc/resolv.conf from 644 to 600.  I'm going to start looking through the init scripts, but has anyone heard of this happening before and tracked it to anything?

I'm running Edgy...

---

### Post by stream303 on 2006-11-13
If you are running dhcp, dhclient is rewriting that file every time it gets a new lease.

---

### Post by mariner09 on 2006-11-13
I have a problem with it changing the file permissions.  The result is that firefox or anything relying on resolution fails.  Can this process be logged to identify the script or culprit?

---

### Post by stream303 on 2006-11-13
Common situation.

Usually dhclient-script is the one doing it.  However, you can force it to obey by editing **/etc/dhcp3/dhclient.conf** as root. (see the 'prepend' line).  I wrote this about a year ago, except I don't use opendns).  I don't like ripping out the make resolv.conf{} function in dhclient-script, so I use instructions in the dhclient.conf file instead.

[http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf](http://www.ubuntuforums.org/showthread.php?t=282034&highlight=resolv.conf)

If you are using a router, an even easier way is to just place your isp's dns addresses in the router setup page.

---

### Post by mariner09 on 2006-11-13
Question, how is anything in that file going to prevent the permissions change that's happening.

It's getting the right info, it's just that permissions are changing from 644 to 600.

request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;

This is th only uncommented section of the file...

---

### Post by digivore on 2006-11-14
I'm having a similar problem.  Every few minutes, my DNS is changing from 192.168.0.1 to 192.168.1.1.   What is causing this to happen??  at the same time i am trying to get my wireless wusb11 to work, but have the wired nic going.  What is making the resolve.conf change the name server?  how can i stop this from happening?

---

### Post by mariner09 on 2006-11-20
My DNS isn't being changed, it's just the permissions on the file making it impossible for any web-based applets or browsing to work.

---

### Post by deanlinkous on 2006-11-20
the permissions on the file wont affect browsing
the information in the file is what will affect it

---

### Post by dbott67 on 2006-11-20
> **digivore said:**
> I'm having a similar problem.  Every few minutes, my DNS is changing from 192.168.0.1 to 192.168.1.1.   What is causing this to happen??  at the same time i am trying to get my wireless wusb11 to work, but have the wired nic going.  What is making the resolve.conf change the name server?  how can i stop this from happening?

Are there multiple access points on the network?  Can you post the output of **iwlist scanning**?
```
dbott@breezy:~$ iwlist wlan0 scanning

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s
```

-Dave

---

### Post by stream303 on 2006-11-23
This may not help at this point, but I've kind of summarized a few issues with /etc/resolv.conf and dhcp:

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

### Post by mariner09 on 2006-11-30
Deanlinkous,

I beg to differ.  Try it as a test.  chmod 600 /etc/resolv.conf and see how far you get.  You'll trip over the doormat.

If only root can have rw access to /etc/resolv.conf, then no app run as a user will be able to read or write the file.  

When I chmod to 644 like it's supposed to be, then all is well.

All I want to do is figure out how to determine which agent or daemon is changing the permissions, because it's wrong.

---

### Post by deanlinkous on 2006-12-01
sorry I should of explained that a LOT better, I didn't say what I meant :(

---

### Post by deanlinkous on 2006-12-01
Who is the owner of the file?

---

### Post by mariner09 on 2006-12-01
/etc/resolv.conf is owned by root.  It's permissions are normally set to 644.  When I do a cold boot, they get set to 600.  Sometimes it happens when resuming from hibernation, but usually not.

I suspect that since permissions are being set to 600, it's not something malicious and that it's probably a daemon or dhcp script that's recreating the file as root and thus leaving it permissioned as such.

I did some digging in the dhcp3 scripts, but they didn't seem to indicate anything other than a process called make_resolv_conf.  If this is run as root, which it should be, then that could explain it. 

The challenge is how to change it so the file is usable system-wide.

---

### Post by halfvolle melk on 2006-12-01
[http://ubuntuforums.org/showthread.php?t=310453](http://ubuntuforums.org/showthread.php?t=310453)

---

### Post by mariner09 on 2006-12-01
I implemented the IPV6 off in bad_list.  What worries me is that every source keeps mentioning a mk_resolv_conf process and the only thing I find anywhere in the scripts is make_resolv_conf.  I wonder if my yearning for rogue repos has bitten me here.

---

### Post by mariner09 on 2006-12-01
It looks like /sbin/dhclient-script has a section where it looks to find root rw permissions on $new-resolv-conf, if it finds this, it moves it to /etc/resolv.conf.  I added a chmod 644 /etc/resolv.conf to the end of that script, so we'll see if that takes care of things.

---

