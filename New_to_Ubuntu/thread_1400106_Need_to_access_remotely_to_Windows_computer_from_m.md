---
title: "Need to access remotely to Windows computer from my 9.04 - what software to use?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Ubunser on 2010-02-06
Please!

---

### Post by halitech on 2010-02-06
personally I use the free version of logmein.com to remotely control my parents windows computers but there is VNC and numerous others that you can use.

---

### Post by falconindy on 2010-02-06
A quick search of these forums will reveal that VNC is insecure and extremely unfit for use outside of a LAN. Use rdesktop.

---

### Post by halitech on 2010-02-06
> **falconindy said:**
> A quick search of these forums will reveal that VNC is insecure and extremely unfit for use outside of a LAN. Use rdesktop.

you can setup ssh and run vnc over that. there is a windows version of ssh. I only gave VNC as an example as I couldn't think of others of the top of my head.

---

### Post by sylvester_0 on 2010-02-06
As stated earlier, the free version of LogMeIn is your best option if you're not on the same LAN and you don't want to worry about NAT port forwarding/public IPs changing.

rdesktop is compatible with the remote desktop system built into Windows (right click My Computer -> Properties -> Remote (tab)). There are GUI interfaces to rdesktop (Applications -> Internet -> Terminal Server Client) available for Linux.

VNC is insecure by default (although it can be secured) and in my experience I've found it dreadfully slow, even over LANs.

---

### Post by Ubunser on 2010-02-06
Does that remote computer need to have something installed? Before I read your posts I went to synaptic and fished out a rdesktop, so I'm kind of eager to use it, could you please gimme some hints on it's usage

---

### Post by falconindy on 2010-02-06
rdesktop should be useable via the terminal service client program in Gnome. If the remote is Windows ______ Pro (not Home), then it already has the RDP client installed to accept remote connections.

---

