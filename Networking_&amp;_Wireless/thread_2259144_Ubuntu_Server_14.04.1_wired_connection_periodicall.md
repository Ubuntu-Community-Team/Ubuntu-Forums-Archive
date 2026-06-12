---
title: "Ubuntu Server 14.04.1 wired connection periodically drops off the network"
date: 2015-01-02
forum: Networking &amp; Wireless
---

### Post by rkillcrazy on 2015-01-02
Not sure if this thread belongs in the server forums or in the networking forums; feel free to move it if need be.

Seeing a strange issue with Ubuntu Server 14.04.1 LTS.  **It periodically drops off the network.**  It's a VM and sits with many other Ubuntu & Windows VMs that remain on the network just fine.  It was upgraded from 12.04 LTS in November 2014.  It was fine after the upgrade and has only started doing this since last week.

**VMware Info:**
[LIST]
[*]VMware ESXi Version: 5.5.0, build 2302651
[*]vCenter Server Version: 5.5.0, build 1891313
[*]VMware Guest Compatibility: ESXi 5.5 and newer (VM version 10)
[*]VMware Tools Version: 2147483647 (3rd-party/Independent) = open-vm-tools
[/LIST]

**OS Info:**
```

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

```

So, as I've said, it drops off the network for no apparent reason.  What I tend to do to get it back online is open the console in VMware and log into it that way.  Once I ping something (anything - public or private via FQDN or IP) from the server (via the console), I can then ping it and SSH into it from my machine like I'd normally do.  I can't seem to find any pattern...  I've even been SSH'd into it and had to drop off the network long before the typical *inactivity-timeout*.  When I drop into it via the console, **I don't see a mess of errors** like I've seen on some of our servers when something goes awry.  The only reason I knew I was having the issue was because my Zmanda Backup server (a separate server) was reporting failing jobs which started last week.  All the other servers backed up just fine but this one server in question keeps failing.  I then have to log into it via the VMware console to get it back online and then jump into my Zmanda Backup server and rerun the failed job.

Let me know what else you think would help with troubleshooting.  At this time, I'm at a loss...

---

### Post by rkillcrazy on 2015-01-02
Update: In the few minutes it took me to type out the 1st post, it dropped again!  I looked over at my SSH session and it was dead.

I looked around the forums and one mentioned to check the logs.  Below are the details I found but they don't show much.  The only thing I found was from a time that was not on par with the event I witnessed.  

```

grep link /var/log/syslog
Jan  2 08:12:46 h1p-glpi1 kernel: [    0.393904] audit: initializing netlink socket (disabled)
Jan  2 08:12:46 h1p-glpi1 kernel: [   14.722546] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

---

### Post by rkillcrazy on 2015-01-05
Update: I ran a continuous ping all weekend from a my Windows machine to the aforementioned Ubuntu Server and I only had a 1% loss  Now, that 1% accounted for 2853 lost packets and, while that's not ideal, it does look like the ping acted like a *keep-alive*.

```

Ping statistics for 10.224.212.15:
    Packets: Sent = 224271, Received = 221418, Lost = 2853 (1% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 509ms, Average = 0ms

```

---

### Post by rkillcrazy on 2015-01-06
Update: I reloaded the VM from scratch and worked in it all day.  Within 30 minutes of me calling it "good enough" and logging out of it, it dropped off the network again and I had to jump back into the console.  I ran a continuous ping from my machine all night and only lost 7 packets.  There's definitely something to be said about the keep-alive action the ping provides.  Still not sure why nobody else has any ideas...

```

Ping statistics for 10.224.212.15:
    Packets: Sent = 57062, Received = 57055, Lost = 7 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 210ms, Average = 0ms

```

---

### Post by mr_cygi on 2015-04-09
Hello,

have you solved this problem? My problem is very similar: [http://ubuntuforums.org/showthread.php?t=2272958&highlight=vmware+network](http://ubuntuforums.org/showthread.php?t=2272958&highlight=vmware+network)

---

### Post by rkillcrazy on 2015-04-09
> **mr_cygi said:**
> Hello,

have you solved this problem? My problem is very similar: [http://ubuntuforums.org/showthread.php?t=2272958&highlight=vmware+network](http://ubuntuforums.org/showthread.php?t=2272958&highlight=vmware+network)

No, I never did figure out the issue.  I gave up and moved it off that vlan - which makes me think there could be an issue with the vlan but I'm not entirely sure.

---

