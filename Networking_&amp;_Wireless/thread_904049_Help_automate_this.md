---
title: "Help automate this?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by scamper_22 on 2008-08-28
Hi all, 

My wireless works fine... HOWEVER, everytime I reboot, I have to perform some actions manually.  I was wondering if anyone could help me automate this.  Sorry if this is a bit of a noob question.

So these are the actions I perfrom upon reboot to get wireless to work:
1.  sudo ifdown eth1
2.  sudo ifup eth1
3.  System->Network and manually add my dns server (for some reason this information is never saved)

Without these steps, the wireless connection doesn't work.

How do I automate this so it happens on startup.  It would be really helpful if the sudo steps could be done without me having to type the password each time.

---

### Post by scamper_22 on 2008-08-29
anyone?

---

### Post by Iowan on 2008-08-29
Check your /**etc/network/interfaces** file - there should be an "auto eth1" line to make it active on bootup. I don't do wireless, so  eth1 seems like wired connection.  It's possible that wlanX may need an auto line too(instead). If you use dhclient to get an IP address, you can change the "prepend" line to include your DNS server.

---

### Post by scamper_22 on 2008-08-29
Hi Iowan,

I checked.  My Wireless lan is somehow set to eth1.  

My /etc/network/interfaces file is as follows:
--------
auto lo
iface lo inet loopback


iface eth1 inet static
address 192.168.1.181
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key XXXXXX
wireless-essid XXXXXX

auto eth1
-------

This is ifconfig when it is up and running
------------
:~/system$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:09:57:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x7000 

eth1      Link encap:Ethernet  HWaddr 00:90:4b:54:8b:9e  
          inet addr:192.168.1.181  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fe54:8b9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163031280 (155.4 MB)  TX bytes:18293886 (17.4 MB)
------------

I dunno.  Not sure what to do at this point.

---

### Post by hal0920 on 2008-09-01
Hi!

The file to be monitoring in the case for the DNS is '/etc/resolv.conf'
This file is a merge of (at least) two other files which lies elsewhere.
They are

  /etc/resolvconf/resolv.conf.d/head

which is placed at the top of '/etc/resolv.conf' and

  /etc/resolvconf/resolv.conf.d/tail

which is inserted last in '/etc/resolv.conf'

The first file '/etc/resolvconf/resolv.conf.d/head' we do not want to touch at all (here you will find the comments that is added first to '/etc/resolv.conf'). If you want the reolver to automagically update to what you want you can do it like so:

Open a terminal emulator window and type:

```
sudo gedit /etc/resolvconf/resolv.conf.d/tail
```

You will need to be root to do this. This file is normally empty, so we need to append a few lines to it. About like this:

```
# Added from '/etc/resolvconf/resolv.conf.d/tail'

nameserver 1.2.3.4
nameserver 5.6.7.8

# End of '/etc/resolvconf/resolv.conf.d/tail'
```

You need to replace the adress(es) above with the ones that applies to you. Now, every time the resolver kicks in, the lines in '/etc/resolvconf/resolv.conf.d/tail' will be inserted last into '/etc/resolv.conf'.

Hope this helps :)

---

### Post by scamper_22 on 2008-09-01
Hi Hal,

these files do not exist on my system:

/etc/resolvconf/resolv.conf.d/head
/etc/resolvconf/resolv.conf.d/tail

---

### Post by hal0920 on 2008-09-02
Hi (again)!

In this case... Hmmm.

Try to make the target for '/etc/resolv.conf' read-only after you have made your changes to the DNS via the configuration utility.

First, you need to make sure that the configuration has been written to disk. Open a terminal and type:

```
sync
```

This will save any unsaved data from the disk cache to disk.

Second, determine if the file '/etc/resolv.conf' is a file or a link.

```
ls -l /etc/resolv.conf
```

On my system this gives:

lrwxrwxrwx 1 root root 31 2008-08-28 22:58 resolv.conf -> /etc/resolvconf/run/resolv.conf

The 'l' bit in the 'lrwxrwxrwx' gives us the hint that this is indeed a link to the file. In my case, then, I would write:

```
sudo chmod u-w /etc/resolvconf/run/resolv.conf
```

If *your* '/etc/resolv.conf' points elsewhere then use that location instead.

If '/etc/resolv.conf' is indeed a file (the first letter is a '-') then you just need to 'chmod' that.

Here we try again... :)

---

