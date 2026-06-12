---
title: "Joining a Windows Domain Ugghh"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by PoopyTheJ on 2008-10-31
Ok, so I've got this pretty Wubi (8.10) install that I'm trying to use as a test box for migrating my companies workstations and POS machines over to Ubuntu. The problem is our IMs and POS software needs to be server from a windows server. Ok, not too big of a problem except, I can't seem to join the domain. I keep getting an error using Likewise about the time server and then a failure to setup a valid account on the domain. I know the admin password is correct so that's not a problem, the server doesn't have a software firewall, but a hardware firewall thats setup to allow internal connections. Any ideas where I can start, what I can check to get this resolved?

---

### Post by PoopyTheJ on 2008-11-02
ok not a lot of play on this topic so far so I'll bump it with this. I can map to network shares using this command.

sudo mount -t cifs //192.168.1.102/share_name /media/my_share -o username=theuser,password=thepass,iocharset=utf8,file_mode=0777,dir_mode=0777

I can access and use the files on the shares, now I need to install network printers... Mind you I haven't joined the domain, but I can access the shared folders, wierd huh? Ok any suggestions? Network printers are shared on the win2003 server box as well as on client computers, but going through the gui I can see the shared folders but not access them, and I cannot see any shared printers through the gui...

Help????

---

### Post by helgman on 2008-11-02
For accessing the shares, that's not so strange, is it? If you supply username/password (that's done in the background when using an AD-joined Windows client) you should be able to (give you use samba etc).

I've never used Likewise but have you gone through the "Troubleshooting Domain Join Problems" in the "Likewise Open Installation and Administration Guide"? It has some stuff about NTP and a whole lot of other stuff too (like a few tips and pointers).

[http://www.likewisesoftware.com/resources/product_documentation/Likewise-Open-5-Guide.pdf](http://www.likewisesoftware.com/resources/product_documentation/Likewise-Open-5-Guide.pdf)

And if you still don't make it, maybe you can come back with more info about the problem ...

Regards,
Helgman

---

### Post by PoopyTheJ on 2008-11-02
I haven't gone through that but will on Monday, the system is at work, and let you know. Thanks for the RTFM. ;)

---

### Post by likeWiseGuy on 2008-11-10
> **PoopyTheJ said:**
> I haven't gone through that but will on Monday, the system is at work, and let you know. Thanks for the RTFM. ;)

It was nice of helgman to point you to the Likewise documents. :-)

An issue that you may have overlooked is the time skew with the Active Directory domain. For the join to be successful, the time skew can be no larger than 3 minutes between the AD time and the client clock. Keep in mind that it is based on GMT so double check your clocks. 

Let me know when you're able to attempt a domain join again and how it all goes for you.

Thanks.

---

