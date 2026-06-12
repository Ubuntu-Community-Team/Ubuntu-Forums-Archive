---
title: "FTP, local networking"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Ole Juul on 2008-08-17
(first forum post)
I need some ideas first so that I can ask intelligent questions.

I'm not clear on the Linux options for an FTP server setup.
I do a lot of writing on a DOS box and wish to transfer text files easily to and from my Kubuntu system. DOS has limited networking capabilities, but it is easy to set up an FTP client and I have all the "fixins" for that ready to go.

The Linux box needs to connect an FTP client to the net as usual. The FTP server needs to be isolated from the net and only locally available.

The Linux box is connected to a router which has no more available space and I would like to avoid purchasing more stuff, such as a switch, if possible.

The Linux box has eth0 connected to the router and eth1 is up and available.

Hoping to isolate the server from the net, I tried setting up an FTP server to access eth1 only, but soon realized that this was way over my head.

Is that a bad approach?
Any better ideas?

- Cheers,
          Ole

---

### Post by cariboo on 2008-08-17
As long as you don't have any ports forwarded on your router you should be safe enough running an ftp server on your kubuntu computer.

I would suggest proftpd, it is available in the repositories, you can use Add/Remoce Programs, Synaptic Package Manager and of course the command line to install it. Proftpd is easy to setup, once it is installed it just works. Then you can just ftp to the ip address of the computer proftpd is running on and start transferring files.

Jim

---

### Post by Ole Juul on 2008-08-17
Jim said: "As long as you don't have any ports forwarded on your router you should be safe enough running an ftp server on your kubuntu computer."

Thanks! I won't worry about that then. I already tried vsftpd and (although easy configuration) doesn't work on my system. I'll try proftpd.

The other problem is, how do I hook in on the second NIC? My gateway is 192.168.1.1 which is the router on eth0, so I gave eth1 the address of 192.2.100 so it would be on a subnet and wouldn't interfere. Is that the right idea? 

PS: I'm comfortable moving about in a terminal BUT, I don't really know anything about networking.

---

### Post by Ole Juul on 2008-08-18
Update: (with a big grin)

   I installed proftpd and once I added a line with "DefaultAddress 192.168.2.100" I was able to access it with the DOS machine on eth1. That saves buying a switch and, I guess, keeps the dos box safe from the internet.

   I'm on track now. Honestly, I didn't think it would be that easy, since I still don't know what I'm doing.

---

