---
title: "[Jaunty] network history in system monitor shows continuous data inflow"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by wolfie2x on 2009-06-01
Why does the network history in system monitor show continuous data inflow of around 20kb/s from the moment I connect to my LAN? I have no applications running and no downloads at all. This didn't happen in Hardy.
After leaving for around 8 hrs, now the total data received is shown as 700MiB!!?
Can someone pls explain what's going on?

---

### Post by steeleyuk on 2009-06-01
Have you got any services running? SSH, NFS, Samba. Unless something is being transferred to another machine, it should be 0.

---

### Post by superprash2003 on 2009-06-01
do you use this machine for ICS??do you share files/folders?

---

### Post by freak42 on 2009-06-01
You can use wireshark (in root mode) to look at what kind of traffic it is.

I get around 10kb/s (kilobits per second) from background noise in my network (dhcp, network sharing, printerstuff), so having a little traffic is usually normal.

hth

---

### Post by wolfie2x on 2009-06-02
> **steeleyuk said:**
> Have you got any services running? SSH, NFS, Samba. Unless something is being transferred to another machine, it should be 0.

It's a clean default installation of jaunty. I didn't specifically enable any services. I did install smbfs for samba mounting, but this happens before mounting shares, just after booting.

> do you use this machine for ICS??do you share files/folders? 
No ICS, and no shared folders.

> You can use wireshark (in root mode) to look at what kind of traffic it is.
I get around 10kb/s (kilobits per second) from background noise in my network (dhcp, network sharing, printerstuff), so having a little traffic is usually normal.
I think you are right; background noise might be the reason. But I don't recall this happening in Hardy, so some network stuff has changed?
I'll try wireshark; Does it show application wise network traffic too? If so I can kill any misbehaving app (if any).

---

### Post by freak42 on 2009-06-02
> **wolfie2x said:**
> 
I think you are right; background noise might be the reason. But I don't recall this happening in Hardy, so some network stuff has changed?
I'll try wireshark; Does it show application wise network traffic too? If so I can kill any misbehaving app (if any).

No, afaik it doesn't show you which app the traffic resultet from (or is intended for), but from the type and destination of the traffic you can usually tell wheter it is noise or not. 

(for instance my gf's apple, sends a lot of icmp messages)

hth

---

