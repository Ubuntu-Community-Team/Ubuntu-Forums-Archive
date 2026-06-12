---
title: "vncviewer internal v. external"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by nycjeff on 2008-02-24
so I'm trying to connect to my desktop with vncviewer.
I can get it internally:> vncviewer 192.168.1.3
does the trick.
but if I want to connect via the internet it always seems to time out on me.
so something like option A: vncviewer 74.73.24.128
or even option B: vncviewer 74.73.24.128:5800

My router is set up to forward the ports 5500, 5800, 5900 to 192.168.1.3 which is the machine that I'm trying to get to.

Any other thoughts on what I'm missing? Thanks in advance.

-jeff

---

### Post by k_grdn on 2008-02-24
Hi,

Use tcpdump on your inteface to see the packet traverse:

tcpdump -i eth0 port 5900.

You will then be able to pinpoint the problem to your router not forwarding or your host not accepting remote vnc connections.  If you have no traffic on port 5900 then your router is not forwading.

I wouldn't recommend opening your router up for vnc a safer option is to use ssh port forwarding, which only requires port 22 to be open plus all traffic will be encrypted.

Remote host: ssh -N -L 5900:localhost:5900 -l user 74.73.24.128

Then when connecting remotely use vncviewer 127.0.0.1:5900 on the remote host.

Regards,

k_grdn

---

### Post by nycjeff on 2008-03-08
Hi K_grdn, Thanks for the response. 
Hmm, I don't see much with the tcpdump, although I think I've been able to work beyond that. I went with Putty as an SSH client. 

I can get to my computer at home from elsewhere. 
So, at this point my router is forwarding the port to my desktop.
So using these settings:
Host name: 74.73.22.145 Port:22
Tunnels: Source Port: 5900
             Destination: 127.0.0.1:5900

So then I connect. I get to my home pc. I log in. Great!! It looks about like a shell system. I can do normal shell stuff as far as I can tell. 

But then the trouble now is this.
When I fire up vncviewer  with:
vncviewer 127.0.0.1
or:
vncviewer 127.0.0.1:0

I get the message:
Unable to connect to host: connection refused (111)

I can make it work with the same settings on a Windows Putty and VNC client. I'm sort of suspecting that it has to do with the 5900 settings, but am not quite sure. 

Any other thoughts are appreciated.

-jeff






> **k_grdn said:**
> Hi,

Use tcpdump on your inteface to see the packet traverse:

tcpdump -i eth0 port 5900.

You will then be able to pinpoint the problem to your router not forwarding or your host not accepting remote vnc connections.  If you have no traffic on port 5900 then your router is not forwading.

I wouldn't recommend opening your router up for vnc a safer option is to use ssh port forwarding, which only requires port 22 to be open plus all traffic will be encrypted.

Remote host: ssh -N -L 5900:localhost:5900 -l user 74.73.24.128

Then when connecting remotely use vncviewer 127.0.0.1:5900 on the remote host.

Regards,

k_grdn

---

