---
title: "Samba: can only connect by ip"
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by williumbillium on 2008-04-06
I have two ubuntu machines I'm trying to share folders between with samba.  A wired kubuntu gutsy desktop and a wireless ubuntu gutsy laptop, both on the same subnet.

I can connect to samba shares if I request using the ip.  e.g. 

smbclient //192.168.1.2/Share

However, if I use the hostname I get:

Connection to host_name failed (Error NT_STATUS_BAD_NETWORK_NAME)

Thus, if I go to Places -> Network.  None of the shared folders on either computer are listed.

Having read this thread:

[http://ubuntuforums.org/showthread.php?t=629130&highlight=samba](http://ubuntuforums.org/showthread.php?t=629130&highlight=samba)

I edited /etc/nsswitch.conf so it now has a line that looks like this:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 wins

And I installed the winbind package.

But I'm still not having any success.

Any ideas where to go from here?

---

### Post by williumbillium on 2008-04-06
Solved.

I had the line:

wins support = no

in my /etc/samba/smb.conf

:oops:

It was down near the printer definition so even when I added wins support = yes near the top of the config, it of course just got canceled out!

---

