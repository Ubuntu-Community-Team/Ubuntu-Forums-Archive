---
title: "A wierd networking problem"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2007-07-29
I've got a weird networking problem since recently. I cannot connect to any of my computers. I usually use fusesmb with Thunar, but now although it can see my shares, when I try yo connect it returns:

```
Failed to open directory "diskd".
Connection timed out.
```

I tried LinNeighborhood and got this:

```
~$ LinNeighborhood 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.24]
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.11.2 bcast=192.168.11.255 nmask=255.255.255.0
Client started (version 3.0.24).
resolve_hosts: Attempting host lookup for name AC-PC<0x20>
Connecting to 212.68.205.86 at port 445
timeout connecting to 212.68.205.86:445
Connecting to 212.68.205.86 at port 139
error connecting to 212.68.205.86:139 (Connection refused)
Error connecting to 212.68.205.86 (Connection refused)

```

I do not understand why it tries to connect to 212.68.205.86. 

Another thing which may be also related is that if I now type any word in Firefox address bar to look up it in Google I am taken to this page: [http://212.68.205.67/process?key=00120fe394aaa797eb0c0e2e2a68969070d](http://212.68.205.67/process?key=00120fe394aaa797eb0c0e2e2a68969070d)  instead of Google. 

In Windows everything works fine both networking and Firefox search. Any help, please?

---

### Post by dmizer on 2007-07-29
are you using opendns.org dns servers?

---

### Post by foxy123 on 2007-07-29
> **dmizer said:**
> are you using opendns.org dns servers?

no, I do not use anything... only what is default...

---

