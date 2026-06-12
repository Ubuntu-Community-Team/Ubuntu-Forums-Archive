---
title: "Application layer firewall?"
date: 2014-01-14
forum: Networking &amp; Wireless
---

### Post by DigiAngel on 2014-01-14
Does anyone know of a true application layer firewall for Ubuntu?  Something that will say let a PID have access to this IP, but not that IP?  Thanks all.

---

### Post by ian-weisser on 2014-01-14
No. Never seen such using a firewall.
Seen lots of IP blacklisting and whitelisting using /etc/hosts.* by the system (not per-user or -application)

Why would you deny some applications from an IP, but allow others?
Why would you install an untrusted application in the first place?

---

### Post by DigiAngel on 2014-01-15
Well...I just switched from OS X to Ubuntu on this here iMac and that was a standard application to install.  I've got an egress firewall, but eh...an application like Little Snitch was instrumental in stopping apps that may have wanted to phone home.  Or, for example, an application that I don't want to go to a site to get ads.  I'm betting it's not super relevent on Linux, but eh...thought I'd shoot it out there :)  Thanks Ian.

---

### Post by ian-weisser on 2014-01-15
It's trivial to monitor what IP addresses your system connects to. Several applications in the Ubuntu Repositories do that. I use Etherape for that purpose.

> **DigiAngel said:**
> an application like Little Snitch was instrumental in stopping apps that may have wanted to phone home.
On OSX, that may be merely considered undesirable behavior of an otherwise convenient app...but in this community it's generally considered to be pure-and-simple malware. If you discover an application in the Ubuntu Repositories that behaves like malware ("phones home" for a purpose other than the user's intent), please speak up.

  > **DigiAngel said:**
> Or, for example, an application that I don't want to go to a site to get ads
That's what /etc/hosts.deny is for. If you don't want ads from a specific server in one application, you probably don't want ads from the same server in *any* of your applications.

---

### Post by DigiAngel on 2014-01-16
Thanks Ian..loving ubuntu on the desktop :)

---

