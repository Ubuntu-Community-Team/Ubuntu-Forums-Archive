---
title: "Problem with browser"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-02-11
I have a strange problem going on. I've searched, and find nothing to help.

I've installed Ubuntu on my work notebook, with authorization from my IT department, but on the condition that "you're on your own with support".

Our timecard application is web-based, and I have no trouble accessing it, as long as I open it within the first couple of minutes after booting up. If I wait, or if I open other programs (particularly Lotus Notes, the native Linux version) I get an error message that it can't connect. It's using a non-standard port, way up above 15000, but as this is a client app, it doesn't seem like that should matter.

Very default installation, with the exception of Likewise-open and Samba. I ran iptables -L and got this:

```
sudo iptables -L
[sudo] password for username: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```So it doesn't appear that any firewall app is doing anything. Could another app be grabbing the port and not releasing it? Would I get the same error message (unable to connect)?

---

### Post by mwcrowley on 2010-02-11
In this case I suspect iptables is not going to tell you anything relevant to your issue.
I'm just guessing here, but.
Is your network connection at work wireless or do you plug an ethernet cable into your laptop?

In a terminal window enter ifconfig.  It should give you output similar to this.  lo is simply your loopback, ignore that.  Instead of eth0 it might show wlan0 or something, but it should show something. The relevant text is "inet addr:" you should have an ip address after it.  You might be getting an ip address and then your netbook is loosing connectivity.  The dmesg command might also show your connection going up and down.
```
eth0      Link encap:Ethernet  HWaddr 00:13:8f:37:53:d3  
          inet addr:10.0.0.203  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe37:53d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2534147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2222699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1105272329 (1.1 GB)  TX bytes:365044497 (365.0 MB)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:890503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:890503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:328853542 (328.8 MB)  TX bytes:328853542 (328.8 MB)

```

---

### Post by kanikilu on 2010-02-11
Along those same lines, at my work the wireless and wired networks are segregated, and we have certain applications that are only available if connected to the wired network or through vpn if on the wireless network. This should be OS independent, though, so it's probably not applicable to your case, but maybe just ask your IT guys if the timecard application is restricted to certain networks, subnets, etc. :???:

// Edit: oh, also, I think you can see what ports applications are using...haven't used it in a while, but I think it was something along the lines of **netstat -nl**, if memory serves(?)

---

### Post by ScottinSoCal on 2010-02-11
The app isn't segregated, but pointing out the wireless made me think. Under Windows, something was messed up with my wireless, and it never managed to connect to the network. Under Ubuntu, I get a great connection. Either through not thinking about it, or through laziness, I'm usually connected through both - and I've noticed some extreme latency issues.

I'm now sitting in a conference room, connected only via the wireless, and the network is much faster. I'm also able to connect to the timecard app with Notes open, and my computer has been running for over an hour. So I guess the answer is, stop being lazy and disable the wireless when I'm docked. Duh.

Thanks, guys, you might not have typed the answer, but you led me to it anyway.

---

