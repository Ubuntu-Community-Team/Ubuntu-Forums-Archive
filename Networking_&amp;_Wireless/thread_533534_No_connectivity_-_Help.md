---
title: "No connectivity - Help"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by dripter on 2007-08-24
i have installed LAMP ubuntu 6.06 and was working fine and i even installed dotproject for me to monitor our projects activities, but recently, i can no longer connect to this server.

**the eth0 is ok**

eth0    Link encap:Ethernet HWaddr 00:0C:29:92:8F:8F
           inet addr:192.168.64.246 Bcast:192.168.71.255 Mask:255.255.248.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collissions:0 txqueuelen:1000
          RX bytes:58868 (57.4 KiB) TX bytes:4158 (4.0 KiB)
         Interrup:185 Base address:0x1080

**if i ping my ip:**

-------------       
myserver:/var/log$ ping 192.168.64.246
PING 192.168.64.246 (192.168.64.246) 56(84) bytes of data.
64 bytes from 192.168.64.246: icmp_seq=1 ttl=64 time0.558 ms
64 bytes from 192.168.64.246: icmp_seq=1 ttl=64 time0.056 ms
64 bytes from 192.168.64.246: icmp_seq=1 ttl=64 time0.098 ms

--- 192.168.64.246 ping statistics ---
3 packets transmitted, 3 received, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 0.056/0.237/0.558/0.227 ms

**if i ping our gateway..**

myserver:/var/log$ ping 192.168.64.1 
PING 192.168.64.1 (192.168.64.1) 56(84) bytes of data.
64 bytes from 192.168.64.246: icmp_seq=1 Destination Host Unreacheable
64 bytes from 192.168.64.246: icmp_seq=2 Destination Host Unreacheable
64 bytes from 192.168.64.246: icmp_seq=3 Destination Host Unreacheable

--- 192.168.64.1 ping statistics ---
5 packets transmitted, 3 received, 0% received, +3 errors, 100% packet loss, time 4066ms
, pipe 3

------------

**the interface setup..**

------------
myserver:/etc/network$ cat interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 static
iface eth0 inet static
         address 192.168.64.246
         netmask 255.255.248.0
         gateway 192.168.64.1

--------
i'm lost on how to check whats wrong with my setup... i'm sure it was running fine before.
though i did run.. 

sudo apt-get update

but it was running fine after the update...

is there a way to revert back to my previous state before the update?
just to check if this is cause by the patch or update. tks.

pls help.

---

### Post by mcdsco on 2007-08-24
A couple of things to check since your network doesn't seem to be the issue:

Is the web server working?
[INDENT]Verify that the web service provided by LAMPP is working by opening Mozilla on the Ubuntu "Server" and typing [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1)[/INDENT]

Do you get the default LAMPP page? Do you get a mysql error?

If the web server is not working, first check the status:
[INDENT]# sudo /opt/lampp/lampp status
... not running?  Start it ... 
# sudo /opt/lampp/lampp start
... or just start apache
# sudo /opt/lampp/lampp startapache[/INDENT]

Look for errors ... 

If you install packages from using Applications --> ADD/Remove it may have inadvertently installed mysql which will conflict with your LAMPP version. 

The last thing I can think of is, check and see if apache outside of lampp is running:
From Ubuntu, click on System --> Administration --> Services and see if it is running, if it is checked, then de-select it.

Oh, one last thing ... see if you firewall is blocking external access to port 80 for your webserver.  If you network seems fine, and you can access the web server from localhost, then your firewall may be a problem.

That is all I can think of off hand ...  <><Scott><>

---

