---
title: "Ongoing x11vnc connection refused error problem"
date: 2020-03-19
forum: Networking &amp; Wireless
---

### Post by thewoose on 2020-03-19
Hi,
For months now I have been dealing with an issue connecting to x11vnc servers.  Here is the brief log of a recent attempt:
```
TigerVNC Viewer 64-bit v1.7.0
Built on: 2017-12-05 09:25
Copyright (C) 1999-2016 TigerVNC Team and many others (see README.txt)
See http://www.tigervnc.org for information on TigerVNC.


Thu Mar 19 14:09:57 2020
 DecodeManager: Detected 1 CPU core(s)
 DecodeManager: Decoding data on main thread
 CConn:       connected to host 192.168.2.66 port 5900
 CConnection: Server supports RFB protocol version 3.8
 CConnection: Using RFB protocol version 3.8
 CConnection: Choosing security type VncAuth(2)


Thu Mar 19 14:09:58 2020
 CConn:       read: Connection reset by peer (104)

```After much googling I have come up with nothing.  This 'connection reset by peer' seems to have no antidote.  I have two other machines, both running the same server, and they work fine.  I have no other connectivity problems with the machine.  Does anyone know how this obnoxious error can be fixed?

Thanks,
Steve

---

### Post by TheFu on 2020-03-19
Use an ssh-tunnel.
Really, no VNC or RDP should be used without either an ssh-tunnel or a full VPN to the machine.  Both VNC and RDP have terrible security, if any at all.

---

### Post by thewoose on 2020-03-19
> **TheFu said:**
> Use an ssh-tunnel.
Really, no VNC or RDP should be used without either an ssh-tunnel or a full VPN to the machine.  Both VNC and RDP have terrible security, if any at all.

Thanks for your reply.  I agree that I should use an SSH tunnel.  And I have.  But strangely enough, the reset connection error follows me inside the tunnel.  I'm serious, it doesn't even work that way.  I tried tightvncserver and it worked but it's no good since I can't access the active destop.  I don't know why x11vnc is so fussy.  Just odd.  

Thanks,
Steve

---

### Post by TheFu on 2020-03-20
Are you sure the correct process is listening on the port you expect?
I don't use VNC.  We use x2go here when straight X11 forwarding through  ... cough ... and ssh tunnel ... is too slow due to WAN connections. x2go uses the NX protocol, which goes over ssh and has more bandwidth compression techniques and controls. I've used x2go from 5 different continents.

---

### Post by thewoose on 2020-03-20
> **TheFu said:**
> Are you sure the correct process is listening on the port you expect?
I don't use VNC.  We use x2go here when straight X11 forwarding through  ... cough ... and ssh tunnel ... is too slow due to WAN connections. x2go uses the NX protocol, which goes over ssh and has more bandwidth compression techniques and controls. I've used x2go from 5 different continents.
I can confirm that the x11vnc instance is listening on :5900.  I am using the identical config on other machines but don't have this problem.  I'll check into x2go ... thanks for the tip.

---

### Post by TheFu on 2020-03-20
Anything in the system or firewall logs?

Aren't there 2 ports for VNC?

---

### Post by thewoose on 2020-03-22
> **TheFu said:**
> Anything in the system or firewall logs?

Aren't there 2 ports for VNC?
No there is nothing in the logs.  I have had this problem before but it doesn't seem to be solvable.  But ... it is intermittent, and for some unknown reason, that machine is now working.  I have no idea what changed, but at least for now I'm able to connect.

---

