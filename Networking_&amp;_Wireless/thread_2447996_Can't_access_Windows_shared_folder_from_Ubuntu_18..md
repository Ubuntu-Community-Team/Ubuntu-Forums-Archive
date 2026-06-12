---
title: "Can't access Windows shared folder from Ubuntu 18.04"
date: 2020-07-30
forum: Networking &amp; Wireless
---

### Post by matteo-dagord on 2020-07-30
Hi all,
I'm currently working from home and I need to connect to a Windows share from a server placed in my company headquarters.
The problem is that when I try to access from Nautilus, I simply cannot access, as it keeps asking username and password in a loop.
Actually I can connect normally to other Windows shares: I'm having problems only with this particular one. I tried with my Windows 10 laptop and it worked, so it's a problem related to my Ubuntu client.

The problem is that I don't have access to the server, and I don't know it's configuration; the company technical helpdesk offers support only for Windows client.
I've read of similar problems and usually the solution involves modifications on Samba configuration but, as said, I don't have access to it.
Any suggestion?

---

### Post by TheFu on 2020-08-01
No clue on my side.  Some VPNs block older Windows sharing protocols or require specific settings to allow them. Those protocols really harm the VPN performance. I've always disabled them on my VPN deployments.

As for connecting to Windows from Ubuntu, there are some threads here about that. Take a look to see if these apply:
[https://ubuntuforums.org/showthread.php?t=2434383](https://ubuntuforums.org/showthread.php?t=2434383)
[https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468](https://ubuntuforums.org/showthread.php?t=2435292&p=13925468#post13925468)
[https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480](https://ubuntuforums.org/showthread.php?t=2444358&p=13961480#post13961480)
[https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310](https://ubuntuforums.org/showthread.php?t=2447575&p=13974310#post13974310)

Please validate they are going the right way - Linux to Windows, not Windows -to- Linux. My notes aren't always clear.

---

### Post by matteo-dagord on 2020-08-04
Hello,
it's not a VPN issue since I can connect using a Windows 10 machine.
Moreover, the thread you linked request modifications to Samba settings... and I don't have access to the server!

---

### Post by TheFu on 2020-08-04
> **matteo-dagord said:**
> Hello,
it's not a VPN issue since I can connect using a Windows 10 machine.
Moreover, the thread you linked request modifications to Samba settings... and I don't have access to the server!

You mentioned samba, so I assumed you were trying to access the system using either CIFS or SMB protocols. You didn't say which. The title says "Windows shared folder" ... so my assumption was reasonable.

You also mentioned using a VPN, so I assumed the VPN was running on the Linux client.  Seems like a reasonable assumption from here, but perhaps saying where the VPN client runs would be useful too?

If you can't ping that server, that is a completely different problem.

---

