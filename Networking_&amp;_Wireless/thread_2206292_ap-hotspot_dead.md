---
title: "ap-hotspot dead?"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by Ertai87 on 2014-02-18
I use the package ap-hotspot (ppd webupd8) to do a lot of mobile browsing from home through my computer's wireless connection.  However, just now I tried to start up ap-hotspot and it appears to have died.  I have no idea why.  I see there was a package update around the middle of last week, and while I've used the package since then I may have been on an old version.  I used the package without trouble for multiple months, so the problem is not with my setup; it appears something was updated or changed that causes ap-hotspot to no longer work.  I've tried resetting it by reinstalling the PPAs and updating the package (which was able to solve a similar problem in the past), but that doesn't work either.  In fact, one of the recommended PPAs for ap-hotspot, ppa:network-manager, no longer supports 13.10 as far as I can tell (there is no /saucy directory for that PPA).

The error, to be more precise, is that I can attempt to run the start script, but it hangs.  It does not give any output except for "Starting Wireless Hotspot..."; it simply hangs.  When I CTRL-C to kill it and try again, it says it's already running, but when I try to run the stop script, it says it's not running, so I have to reboot to kill the process.

Does anyone use ap-hotspot and can help me solve this problem?  I'd like to submit a bug report directly to the PPA maintainers, but I'm not sure how to do that, so I need help from you guys.

Thanks a lot.

---

### Post by Ertai87 on 2014-02-18
Just found out there's an ap-hotspot debug script.  Here's the output from that:

```
Starting Wireless Hotspot...
* Stopping DNS forwarder and DHCP server dnsmasq
* (not running)
update-rc.d: warning:  start runlevel arguments (none) do not match hostapd Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (none) do not match hostapd Default-Stop values (0 1 6)
Disabling system startup links for /etc/init.d/hostapd ...
Removing any system startup links for /etc/init.d/hostapd ...
/etc/rc0.d/K20hostapd
/etc/rc1.d/K20hostapd
/etc/rc2.d/K80hostapd
/etc/rc3.d/K80hostapd
/etc/rc4.d/K80hostapd
/etc/rc5.d/K80hostapd
/etc/rc6.d/K20hostapd
Adding system startup for /etc/init.d/hostapd ...
/etc/rc0.d/K20hostapd -> ../init.d/hostapd
/etc/rc1.d/K20hostapd -> ../init.d/hostapd
/etc/rc6.d/K20hostapd -> ../init.d/hostapd
/etc/rc2.d/K80hostapd -> ../init.d/hostapd
/etc/rc3.d/K80hostapd -> ../init.d/hostapd
/etc/rc4.d/K80hostapd -> ../init.d/hostapd
/etc/rc5.d/K80hostapd -> ../init.d/hostapd
update-rc.d: warning:  start runlevel arguments (none) do not match dnsmasq Default-Start values (2 3 4 5)
update-rc.d: warning:  stop runlevel arguments (none) do not match dnsmasq Default-Stop values (0 1 6)
Disabling system startup links for /etc/init.d/dnsmasq ...
Removing any system startup links for /etc/init.d/dnsmasq ...
/etc/rc0.d/K85dnsmasq
/etc/rc1.d/K85dnsmasq
/etc/rc2.d/K85dnsmasq
/etc/rc3.d/K85dnsmasq
/etc/rc4.d/K85dnsmasq
/etc/rc5.d/K85dnsmasq
/etc/rc6.d/K85dnsmasq
Adding system startup for /etc/init.d/dnsmasq ...
/etc/rc0.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc1.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc6.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc2.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc3.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc4.d/K85dnsmasq -> ../init.d/dnsmasq
/etc/rc5.d/K85dnsmasq -> ../init.d/dnsmasq
* Restarting DNS forwarder and DHCP server dnsmasq
...done.
net.ipv4.ip_forward = 1

```

At this point, the script hangs.  Anyone have any idea what's up?

---

### Post by ezzy1980 on 2014-04-03
what version of hostapd?

if hostapd is newer (2.0+) , there is an issue with it trying to acquire a resource that it thinks is busy (network manager if you have installed a desktop version of ubuntu)

these command lines shall free up the resource.   you can add them to the start of your ap script.

> 
sudo nmcli nm wifi off
sudo rfkill unblock wlan


---

### Post by Ertai87 on 2014-04-04
I ended up contacting the developer and we debugged it together.  He said he was putting up a fix targetted at 13.10 which rolled back the update since we couldn't figure it out.  Anyway, the problem was fixed.  If anyone else is having this problem, contact the developer.  He's a really cool guy.

---

### Post by jinalthecool on 2014-04-20
Ubuntu Gnome 14.04
Had the same issue you described. Executing those two commands before ap-hotspot works for me. Thank you.

---

### Post by baharudinafifsurya on 2014-05-04
Yeaaah finally after trying 2 day, I've solved this problem with that two magical command hahahahaha :D
Thank you very  much :D

---

### Post by 7apeswild on 2014-10-26
Can you share the solution. I am having the same issue with hotspot.

---

### Post by sammiev on 2014-10-26
> **7apeswild said:**
> Can you share the solution. I am having the same issue with hotspot.

This thread is dead. Best to start a fresh one and add more info like the OS you are using.

---

