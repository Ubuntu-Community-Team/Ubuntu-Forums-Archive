---
title: "LAN: Win &gt; Lin, limited low speed"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by lenux- on 2007-02-15
Hello,
For some reason looks like maximum upload/download speeed is about 30-80kb/s @ lan..
i'am using DHCP and connectinung to linux server using, servers public ip... iptraf tells me that it uses eth0, shoulnt it be using lo (local area...)?

Windows >-< windows is wokring correctly...

---

### Post by Floppyjoe on 2007-02-15
> **lenux- said:**
> Hello,
For some reason looks like maximum upload/download speeed is about 30-80kb/s @ lan..
i'am using DHCP and connectinung to linux server using, servers public ip... iptraf tells me that it uses eth0, shoulnt it be using lo (local area...)?

Windows >-< windows is wokring correctly...

The lo interface is a loopback interface and like you I am ignorant of what it actually does.

---

### Post by wantime on 2007-02-15
My basic idea of the lo interface is that the looback interface is generally the singular network of your machine (or your local network).  The localhost, usually 127.0.0.1 is a reference to your lo interface.  Basically it is useful for network testing and, for example, testing your web pages etc.  You can imagine it to be a virtual circuit from your local machine and back to it - a kind of self loop.  The internet creates virtual circuit connections from one machine to another somewhere else, and this one is just the trivial loop onto itself.

---

