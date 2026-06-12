---
title: "Reverting to DHCP?"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by paparoof on 2008-01-03
Yesterday I completed an installation of 6.06 LTS Server (LAMP option). Everything's just fine, with one small but significant issue.

The installer set up the box as a DHCP client. After the install was complete, I modified /etc/network/interfaces to set the box as static. Here's the content of that file:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.10.10.102
        netmask 255.255.255.0
        gateway 10.10.10.1


After modifying the file, I issued an ifdown and ifup for the proper interface and everything was golden. I did not reboot the machine. I accessed the machine from home late last night so I know everything was okay at that point. This morning I couldn't remotely access the box anymore, so when I got back to my office, I sat down at the console, pinged 4.2.2.2 successfully, did an ifconfig and found the box had reverted back to the IP it originally received from my DHCP server during the install (10.10.10.25). I did a full reboot on the machine and it came back up as 10.10.10.102 as directed by the /etc/network/interfaces file. Since then so far so good, but it's only been a couple of hours.

So what did I do wrong? Do you *have to* reboot after switching from DHCP to static? How *should* I have gone about this?

---

### Post by paparoof on 2008-01-03
someone at work suggested a cron job did it. I know nothing about cron or how to manage it - can someone point me to something I can read on this?

---

### Post by paparoof on 2008-01-03
hmmm.... 27 reads and no replies yet. must have stumped all 'yall. :confused:

"man crontab" says all cron jobs are stored in /var/spool/cron/crontabs. So this looks like there are no cron jobs at all:
```
francis@norwood:~$ sudo ls /var/spool/cron/crontabs
francis@norwood:~$
```

So I'm back to square one. I found in /etc/passwd that there IS a "dhcp" user. Since this is a server I will never use the DHCP client, so can I just whack this user?

I know someone out there knows what easy little thing I'm missing....

---

### Post by rosserver on 2008-01-03
I don't think you are missing anything, I don't think anyting happened out of the ordinary -- that kinda stuff happens around here all the time.

With that said you may not want my advice and I'm guessing that "That" is why no one else felt like commenting, because it is the same experience that they have.  Situation is normal.

Now I do not reboot either, I happily gave that up when I said "no" to windows; no ifup or ifdown for me; but I do restart the network right after any change to the interfaces file:

/etc/init.d/networking restart

I didn't see you say that you did that and that always works (when I spell everything correctly) for me.

Good luck

---

### Post by paparoof on 2008-01-03
well I can appreciate that... I did not actually try "networking restart".

However, I did find an installed package called "dhcp3-client" so I removed it. I guess I'll know in the morning....

```
francis@norwood:~$ sudo apt-get remove dhcp3-client
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  dhcp3-client ubuntu-minimal
0 upgraded, 0 newly installed, 2 to remove and 73 not upgraded.
Need to get 0B of archives.
After unpacking 664kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 16149 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing dhcp3-client ...
```

---

### Post by paparoof on 2008-01-03
and THEN I find this:

[https://lists.ubuntu.com/archives/ubuntu-server/2007-August/000602.html](https://lists.ubuntu.com/archives/ubuntu-server/2007-August/000602.html)

That actually explains it - I think.

---

### Post by paparoof on 2008-01-04
Well the machine stayed on it's static IP all night, so I think I can call this solved.

However, I can't say 100% for sure what fixed it since I broke the cardinal rule of troubleshooting and made several changes at once. That said, I'm relatively certain the real problem was only issuing the ifdown/ifup as opposed to actually restarting networking. Just bouncing the interface didn't actually stop the DHCP client.

---

### Post by Russianspi on 2008-01-14
I'm using Gutsy as a bind9 server, and I had a similar problem - except that it kept happening at random and inconvenient times.  (I don't want to hear, "help, help, I can't connect to the server!" early on a Sunday morning ever again.)  I just ran aptitude purge dhcp3-client.  We'll see how it works.  I am sure, from log files, that it was my dhcp client changing my IP address, but I did nothing to ask it to do so.  Wish me luck!

---

### Post by sqrt2 on 2008-01-14
What caused the problem was the fact that dhclient was still running after you reconfigured /etc/network/interfaces. When the DHCP lease exipred, it requested a new IP address from the DHCP server (which in most cases is the same as you got last time) and assigned it to the interface.

Be sure to kill the dhclient process of the corresponding interface when moving from dhcp to static.

---

