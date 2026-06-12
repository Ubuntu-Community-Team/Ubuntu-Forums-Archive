---
title: "any good brute force attack blocker for ssh?"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-07-10
used to use fail2ban , now after an upgrade from 7.10 to 8.04 it stopped to work (start).
any idea for another good app with a good log file?? (except from denyhosts... )

---

### Post by jimv on 2008-07-10
I just changed the port that my router maps to my ssh server from 22 to 42135 (or any other large, random port).  Potential hackers are much less likely to find a server running on a non-standard port.

---

### Post by dfreer on 2008-07-10
> **jimv said:**
> I just changed the port that my router maps to my ssh server from 22 to 42135 (or any other large, random port).  Potential hackers are much less likely to find a server running on a non-standard port.

Not likely. Changing ports pretty much only protects against dumb scripts that only search for a specific port. A well written script or hacker will almost surely scan your machine for open ports.

As for the OP, I'd look into why fail2ban has "failed". Logs would be a great place to start. Also, look into changing SSH from using a password to auth to using a public/private key auth.

---

### Post by jimv on 2008-07-10
> **dfreer said:**
> Not likely. Changing ports pretty much only protects against dumb scripts that only search for a specific port. A well written script or hacker will almost surely scan your machine for open ports.

As for the OP, I'd look into why fail2ban has "failed". Logs would be a great place to start. Also, look into changing SSH from using a password to auth to using a public/private key auth.

Why spend the time searching for services running on non-standard ports when you can just hop over to the next IP address and do a check?  Most "hackers" are just punks running scripts.  My logs used to be filled up with people attempting to log into my ssh server as root, and since I changed the port a few months ago, there have been NO attempts...not one.

Even if someone did do a port scan and saw that the port was open, they still don't have any idea what service is running on it, and unless they know that you have something extremely valuable stored on your machine, no one is going to put that much effort into breaking in.

I suppose if he wanted to be near 100% secure, he could do key based authentication instead of password based.

---

### Post by handaxe on 2008-07-10
> **dfreer said:**
> Also, look into changing SSH from using a password to auth to using a public/private key auth.

This is good advice. And if I may clarify - set up public/private key AND disable password logins altogether. The 2 can coexist but that serves no purpose in suppressing brute force attempts.

HA

---

### Post by StOoZ on 2008-07-11
> **dfreer said:**
> Not likely. Changing ports pretty much only protects against dumb scripts that only search for a specific port. A well written script or hacker will almost surely scan your machine for open ports.

As for the OP, I'd look into why fail2ban has "failed". Logs would be a great place to start. Also, look into changing SSH from using a password to auth to using a public/private key auth.

it had error 100 in the fail2ban.log file.
I have no idea what to do , im sure there are other similiar programs.

---

### Post by dfreer on 2008-07-11
> **jimv said:**
> Why spend the time searching for services running on non-standard ports when you can just hop over to the next IP address and do a check?  Most "hackers" are just punks running scripts.  My logs used to be filled up with people attempting to log into my ssh server as root, and since I changed the port a few months ago, there have been NO attempts...not one.

True, a lot of the scans and brute force attacks you see in your logs are from script kiddies. In which changing ports does throw off the "dumb" scripts. But changing ports doesn't protect you from brute force attacks, only script kiddies. The OP didn't ask how to protect from script kiddies.

Also, what happens when those kiddies get an intelligent script that checks non-standard ports?

> **jimv said:**
> Even if someone did do a port scan and saw that the port was open, they still don't have any idea what service is running on it, and unless they know that you have something extremely valuable stored on your machine, no one is going to put that much effort into breaking in.

nmap, a very common port scanner, has the ability to detect what services are running on non-standard ports (see [http://nmap.org/book/man-version-detection.html](http://nmap.org/book/man-version-detection.html) ). Furthermore, nc can be used to determine that SSH is running as well, version information and all:
```
$ nc myhostname.domain.com *22*
SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
## Note that port 22 can be any port.
```

> **jimv said:**
> I suppose if he wanted to be near 100% secure, he could do key based authentication instead of password based.

Why not be 100% secure?

To the OP - Here's some links you might want to check up if you don't want to use fail2ban:

[http://ubuntuforums.org/showthread.php?t=568100](http://ubuntuforums.org/showthread.php?t=568100)
[http://ubuntuforums.org/showthread.php?t=852893](http://ubuntuforums.org/showthread.php?t=852893)
[http://ubuntuforums.org/showthread.php?t=796774](http://ubuntuforums.org/showthread.php?t=796774)

In particular they mention denyhosts, fail2ban, sshguard. As for your particular fail2ban error, I see through google that there have been several issues with this, but on quick glance I don't really see the cause or solution.

You can try doing a remove --purge of fail2ban, which will delete it's configuration files and then a reinstall. Also, if you know what you are doing (and sure it won't mess with any existing firewall/script), you can flush your iptables rules. It could possibly be that fail2ban is not working somehow due to a misconfigured iptables.

---

