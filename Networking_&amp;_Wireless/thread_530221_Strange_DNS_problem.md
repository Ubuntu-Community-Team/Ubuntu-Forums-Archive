---
title: "Strange DNS problem"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by Cherubim on 2007-08-20
I have a really strange problem with the DNS resolution.

I have a Windows 2003 DNS Server in my homenetwork that handles all DNS requests.

Internet works fine, but the resolution for the local network has bugs :(

If i try to ping a local machine in the format "machine.domain.local" it does not work.
I get "unknown host".
If i try to ping the machine in the format "machine" then the dns suffix gets appended and i recieve answers from "machine.domain.local".

I only have those problems on my Ubuntu box, the Windows clients work fine.

The question is: Is this a problem with Ubuntu or is there some sort of misconfiguration on my Windows Server that only shows up when using linux clients ? :confused:

---

### Post by jakev383 on 2007-08-20
> **Cherubim said:**
> I have a really strange problem with the DNS resolution.

I have a Windows 2003 DNS Server in my homenetwork that handles all DNS requests.

Internet works fine, but the resolution for the local network has bugs :(

If i try to ping a local machine in the format "machine.domain.local" it does not work.
I get "unknown host".
If i try to ping the machine in the format "machine" then the dns suffix gets appended and i recieve answers from "machine.domain.local".

I only have those problems on my Ubuntu box, the Windows clients work fine.

The question is: Is this a problem with Ubuntu or is there some sort of misconfiguration on my Windows Server that only shows up when using linux clients ? :confused:

It is probably appending the domain suffix for you.  I'm not sure where to stop it from doing that, but please post back if you find out!

---

### Post by Cherubim on 2007-08-21
I found the problem: you have to edit /etc/nsswitch.conf

Other had the problem too and mentioned the solution here:
[http://ubuntuforums.org/showthread.php?p=2682229](http://ubuntuforums.org/showthread.php?p=2682229)

---

### Post by jakev383 on 2007-08-22
Glad it worked for you.  I'm thinking of setting up something similar here at my house - now that I have Asterisk, Mythtv, file-server, etc. all running it would be nice to access them by name instead of IP address.

---

