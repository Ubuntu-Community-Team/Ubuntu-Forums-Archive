---
title: "NFS vs Firewall - NFS Loses"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by l951b951 on 2007-02-19
I'm trying to set up NFS sharing between my Fedora 6 desktop and my Ubuntu Dapper laptop.  The Fedora machine has the folder I want exported.  I got my export set up but Ubuntu kept giving me the error "mount to NFS server 'linuxbox' failed: server is down."  I tried alot of export settings and finally had a moment of clarity and went to Fedora's "Security Level and Firewall" native program.  I disabled the firewall, and suddenly my mount was successful.  I re-enabled the firewall and opened port 2049 (I believe this is the UDP port needed for NFS to work) and I can no longer mount.  

So obviously, 2049 is not the port I have to enable.  Can anyone tell me how to open this firewall to allow nfs without having to leave my firewall open?

---

### Post by timcredible on 2007-02-19
according to /etc/services, nfs uses both udp and tcp, so try opening tcp 2049 also.

```

tim@ubuntu-desktop:~$ grep nfs /etc/services
nfs             2049/tcp                        # Network File System
nfs             2049/udp                        # Network File System

```

---

### Post by l951b951 on 2007-02-19
> **timcredible said:**
> according to /etc/services, nfs uses both udp and tcp, so try opening tcp 2049 also.

Didn't work.  There must be something else, but thanks for the effort.  I didn't think of that.  Any other ideas?

---

### Post by super-user on 2007-02-20
Google for "nfs firewall fixed port". You have to fix several ports for the different daemons in order to get NFS to work. At the moment I could only find a german how to: [http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html](http://blog.basquiat.de/archives/305-NFS-und-Brandschutzmauern.html) But you should get the idea by looking at the code snippets!

---

### Post by HereInOz on 2007-02-24
Can you perhaps just permit access through the firewall for the particular IP address of the laptop?  That way, all ports are permitted but only from the laptop.  This can be done with Firestarter - is it possible with the Fedora firewall application?

---

### Post by super-user on 2007-02-24
Hi,

It looks like anyone is really posting a solution here so I will direct you to (shame on me) my small writeup of a how to: [http://software.hence22.org/blog/ubuntu/server/nfs-fixed-ports-2007-02-10-17-33.html]("http://software.hence22.org/blog/ubuntu/server/nfs-fixed-ports-2007-02-10-17-33.html"). This is working on server side on dapper and edgy for me.

cheers

---

