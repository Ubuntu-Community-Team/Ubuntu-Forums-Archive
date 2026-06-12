---
title: "Remote Desktop doesn't work."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by richeerichhh on 2009-05-25
Hi guys. Thanks for the help in advance.

 I've seemed to have done everything right to configure remote desktop, however everytime I try to connect to my Remote Desktop using Jaunty Remote Desktop Viewer I get a host not reachable. I've tried to ping my remote PC but get a Destination Host not reachable message. Not sure what to do next. Any suggestions?

Rich.

---

### Post by kvizz on 2009-05-25
is your computer with enabled remote desktop windows based or ubuntu based? are both computers on the same subnet or one is behind the router? is there any firewall software installed on machine with remote desktop enabled?

---

### Post by procras on 2009-05-25
Please give network details.

Are both computers on the same local area network?
$ ifconfig eth0
Where eth0 is the interface connected to the network
Should give you the ip address of the box you are typing on.

You should be able to ping each box from each other.
$ ping 192.168.1.9
Where 192.168.1.9 is the address of the other box.

Make sure the vnc server is working on the machine you want to look at.

$ netstat -lnp | grep 5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6       0      0 :::5900                 :::*                    LISTEN      4072/vino-server


You should be able to telnet on port 5900 to the other box
$ telnet localhost 5900
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
RFB 003.007

Substitiure the IP address of the box you are trying to connect to for localhost.

Good luck

---

### Post by HermanAB on 2009-05-25
Hmmm, it pains me to see all these threads on Ubuntu Forums about using and abusing VNC.  Please, don't use VNC.  It is insecure.  It is an abomination. Leave VNC server running on a public machine and it will be hacked.  VNC will make your hair fall out and your toe nails grow in...

Rather use SSH.  It can do everything VNC does only better.  SSH is secure and can do many other things too that VNC cannot.

So, install ssh-server, open port 22/TCP in the firewall, connect to it like this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

That even works from Windows with Cygwin.

---

### Post by richeerichhh on 2009-05-25
Thanks for the replys. First off I'm both computers are behind a router. I will only be connecting inside the router. Both computers are running Ubunut Jaunty 9.04. Both computers are connected wirelessly. The computer I'm connecting with is a Laptop with a built in card, not sure what the brand is. The computer I'm trying to connect to is a desktop, the wireless card is a Linksys WUSB54G. There is no firewall software running on each machine.

The plot thickens though. I had set both computers to static IP's. The laptops work fine, the desktop doesn't. That's I think pretty much the problem. The Static IP is set on the routers end. While my laptop has no problem with it, my desktop can't be connected to or even pinged with it on. With it off however I can Remote Desktop to my hearts content. Should I start a new post about connecting to a Remote Desktop via Static IP's or can you guys help me with that here.

@procras I don't know I should type after ifconfig since I'm not connected to eth0. This is what I get when I type ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:03:25:3d:d8:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

Thats not even my wireless MAC address..

netstat -lnp | grep 5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6       0      0 :::5900                 :::*                    LISTEN      5712/vino-server

Not really sure what that means.

@HermanAB Good idea but it won't even connect via SSH, Static IP or not. RD at least works wothout static IP.

---

### Post by xavierp94 on 2009-05-25
> **richeerichhh said:**
> Thanks for the replys. First off I'm both computers are behind a router. I will only be connecting inside the router. Both computers are running Ubunut Jaunty 9.04. Both computers are connected wirelessly. The computer I'm connecting with is a Laptop with a built in card, not sure what the brand is. The computer I'm trying to connect to is a desktop, the wireless card is a Linksys WUSB54G. There is no firewall software running on each machine.

The plot thickens though. I had set both computers to static IP's. The laptops work fine, the desktop doesn't. That's I think pretty much the problem. The Static IP is set on the routers end. While my laptop has no problem with it, my desktop can't be connected to or even pinged with it on. With it off however I can Remote Desktop to my hearts content. Should I start a new post about connecting to a Remote Desktop via Static IP's or can you guys help me with that here.

@procras I don't know I should type after ifconfig since I'm not connected to eth0. This is what I get when I type ifconfig eth0

eth0      Link encap:Ethernet  HWaddr 00:03:25:3d:d8:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

Thats not even my wireless MAC address..

netstat -lnp | grep 5900
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp6       0      0 :::5900                 :::*                    LISTEN      5712/vino-server

Not really sure what that means.

@HermanAB Good idea but it won't even connect via SSH, Static IP or not. RD at least works wothout static IP.
You maybe will need to port foward your computer on your router so your other computer can access the closed port.

---

### Post by GOfree on 2009-05-25
...[deleted]

---

### Post by GOfree on 2009-05-25
> eth0 Link encap:Ethernet HWaddr 00:03:25:3d:d8:0d
UP BROADCAST MULTICAST MTU:1500 Metric:1

Thats not even my wireless MAC address..

If it's a wireless interface you are looking for, the interface name should be something like wlan0.

"ifconfig wlan0 up" ?

---

### Post by GOfree on 2009-05-25
:guitar:

---

### Post by Blue Sassley on 2009-05-25
> **HermanAB said:**
> $ ssh -X -C -c blowfish user@server gnome-panel

Sorry to high jack this thread but what does the "blowfish" part of the command do?

Thanks,
Blue

---

### Post by Blue Sassley on 2009-05-25
Never mind, I just ran the man command on SSH and I know what blowfish is.

Thanks,
Blue

---

### Post by asmoore82 on 2009-05-25
Personally, I turn on VNC temporarily with

```
ssh -X user@remotehost vino-preferences
```

Then use it, then turn it back off the same way.

I can't SSH a whole new Gnome session because I typically need to
open or adjust torrent downloads and leave them open on the local X.

If I am across the open Internet I tunnel VNC over SSH:

```
ssh -L 5901:remotehost:5900 user@remotehost
```
^leave that open; then, in a different local terminal:
```
vncviewer localhost::5901
```

---

### Post by resonanttoe on 2009-06-01
> **HermanAB said:**
> Hmmm, it pains me to see all these threads on Ubuntu Forums about using and abusing VNC.  Please, don't use VNC.  It is insecure.  It is an abomination. Leave VNC server running on a public machine and it will be hacked.  VNC will make your hair fall out and your toe nails grow in...

Rather use SSH.  It can do everything VNC does only better.  SSH is secure and can do many other things too that VNC cannot.

So, install ssh-server, open port 22/TCP in the firewall, connect to it like this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

That even works from Windows with Cygwin.


Much obliged for this HermanAB!
Solved my solution quite eloquently. Ditched VNC completely in the end.

---

### Post by XCan on 2009-06-01
> **HermanAB said:**
> Hmmm, it pains me to see all these threads on Ubuntu Forums about using and abusing VNC.  Please, don't use VNC.  It is insecure.  It is an abomination. Leave VNC server running on a public machine and it will be hacked.  VNC will make your hair fall out and your toe nails grow in...

Rather use SSH.  It can do everything VNC does only better.  SSH is secure and can do many other things too that VNC cannot.

So, install ssh-server, open port 22/TCP in the firewall, connect to it like this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

That even works from Windows with Cygwin.

Is it possible then to bring forward applications already running on the remote computer?

---

