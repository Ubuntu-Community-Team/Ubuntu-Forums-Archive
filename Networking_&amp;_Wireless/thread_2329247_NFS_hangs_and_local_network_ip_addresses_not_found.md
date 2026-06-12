---
title: "NFS hangs and local network ip addresses not found but names are"
date: 2016-06-29
forum: Networking &amp; Wireless
---

### Post by Michael_Staggs on 2016-06-29
It may not matter, but this is on an ARM machine....an Odroid c1+. I asked over there and haven't gotten a reply and I imagine the solution isn't going to be platform specific.

After a couple of minutes of NFS transmission, NFS hangs. In dmesg I can see:

"nfs: server 192.168.1.69 not responding, still trying"

I've  tried mounting nfs with the options async, sync, nolock, and  nfsvers=3....separate or altogether (except async and sync). The  behavior continues. However, this is where it gets weird.... if I try to  ping the server or any machine, I get "unknown host"...and I'm pinging  by the 192.168.1.69....not a name. I try pinging other machines on the  network and get the same. However, I can still ssh into the machine  fine....so the network IS working. 

Once this happens, if I ssh in and do anything I'm fine...UNTIL I type "ls" and then it hangs up too.

Here is my ifconfig output:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:06:10:68:88
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:3047:75b0:29fc:f27e:6033:6164/64 Scope:Global
          inet6 addr: fe80::21e:6ff:fe10:6888/64 Scope:Link
          inet6 addr: 2602:306:3047:75b0:21e:6ff:fe10:6888/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:96403771 (96.4 MB)  TX bytes:3642318 (3.6 MB)
          Interrupt:40

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240231 (240.2 KB)  TX bytes:240231 (240.2 KB)

```

I tried to ping google, both on IPV4 and  IPV6. It worked. I just can't ping or reach the local network....but it  can reach me

Also, an interesting tidbit....apparently I can ping the network hub by NAME "homeportal", but not by IP address 192.168.1.254

I tried restarting networking and the problem remains until I reboot.

Running nmcli dev list eth0 gives me the proper dns server: IP4.DNS[1]:                             192.168.1.254 

and I CAN ping it....but not the other machines...but they can connect to me...

And again, it works perfectly until I mount an nfs volume and start transferring

Thanks for any help

---

