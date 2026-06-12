---
title: "Ubuntu version information behind a firewall"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by Steve_Henderson on 2015-02-08
I'm sorry if this information is out there somewhere.   I can't think of and appropriate search to turn it up.

Here is my issue.   Our company just went through a PCI compliance scan from a company called Trustwave.   They obviously scan ports and figure out which are being used for what, I get that.

One of the things they reported was the version of Ubuntu we have installed on our server.  

My question is what TCP request to Ubuntu will reply with the version information and how do I stop that from happening.  I can't see how this is a good thing.   Also how the heck are they doing it from the untrusted side of a router/firewall (3com).   The only thing I can think of is that the information is included in header of some sort when a connection is attempted.

I've changed the default port for everything and the server is most certainly NOT in a DMZ anyway.   Is this info included in some of the headers for SSH connections, for example, prior to an actual login?

I don't want people from the internet to know my server version for obvious reasons.  If Trustwave can do it I'm sure someone will figure out how to exploit that if a vulnerability is documented for a particular version.   I'm on a downlevel version 12.04.1 of Ubuntu LTS.

Thanks in advance.

---

### Post by veddox on 2015-02-09
I'm not a professional, but here are two things possibilities I can think of:
1. TCP packets can themselves tell you something about the source computer. See [here]("http://www.windowsecurity.com/articles-tutorials/intrusion_detection/Operating-System-Fingerprinting-Packets-Part1.html").
2. HTTP packet headers contain a user-agent field that gives some detail (if your server ever handles http)

I don't know if that's any help to you. Have you tried asking the people at Trustwave how they did it?

---

### Post by Lars Noodén on 2015-02-09
They are probably using nmap and p0f or something built on them.  It's not anything to worry about.  But if you want to read, start with those two tools' manual pages.  The nmap page has a whole section on OS detection.

---

### Post by Lars Noodén on 2015-02-09
> **Steve_Henderson said:**
> I've changed the default port for everything and the server is most certainly NOT in a DMZ anyway.   Is this info included in some of the headers for SSH connections, for example, prior to an actual login?

For what it's worth you can see this header information by using a telnet client to connect to your SSH port.  

```

telnet xx.yy.zz.aa 22

```

Obviously supply your addresds and set the port if it is different than 22.  It will show something like this upon connection:

```

SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2

```

From that you can get a good guess at which version of Ubuntu has version 6.6p1-2ubuntu2

---

