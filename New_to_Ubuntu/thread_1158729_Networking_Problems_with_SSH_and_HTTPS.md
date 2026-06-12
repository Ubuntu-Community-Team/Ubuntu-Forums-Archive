---
title: "Networking Problems with SSH and HTTPS"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by tobyjoiner on 2009-05-14
I am having an issue with networking.  I am brand new at this, and have figured out a few things, but could use some advice / help.

Every 30 min or so, I cannot connect to our ubuntu server (8.04) from outside our network, https (443) or ssh (222) ours is on 222 for security. 

if I restart networking with 

```
sudo /etc/init.d/networking restart
```

it works fine for another random amount of time.  I setup a cron job to run this every hour now so I can keep connecting to it but would like to know if I am doing something wrong, or if it might be some sort of hardware error.  I know the cron job is wrong, but it is a work around for now.

Thank you,

Toby

---

### Post by hw-tph on 2009-05-14
Power management disabling your network card or putting the computer to sleep, perhaps? Anyhow, it's a good idea to have a look at the system logs in /var/log.

---

### Post by Peter09 on 2009-05-14
What card have you got

```
lshw -C network
```

---

### Post by tobyjoiner on 2009-05-14
Thanks to both of you for your replies and help.

hw-tph:

In the file /var/log/syslog I only found this that looked weird, but this is happening hourly, and looks like its happening when I run the cronjob

May 14 04:00:04 ny kernel: [135664.253907] 0000:01:00.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
May 14 04:00:04 ny kernel: [135664.253918] eth1: Setting full-duplex based on MII#1 link partner capability of 41e1.
May 14 04:00:11 ny kernel: [135671.612079] eth1: no IPv6 routers present

I can't find any good info on power management settings.  Is that all controlled in the bios, or is there a command line tool to change those settings?


Peter:

  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 11
       serial: 00:1e:e5:d6:41:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=10.1.1.15 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes

---

### Post by tobyjoiner on 2009-05-14
Just to add some more info, we have a windows machine that I can Remote Desktop into then access the linux box from inside the network even when its down to the outside, sometimes it takes a minute to bring up the login prompt, but it always works there.

---

### Post by tobyjoiner on 2010-05-06
I realize this is a year old now, but wanted to update it to let everyone know it was our crappy ISP.

---

