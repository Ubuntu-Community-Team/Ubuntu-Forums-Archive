---
title: "Wifi connects, but no internet access - Ubuntu 12.04.5 LTS - HP Mini 210"
date: 2015-06-12
forum: Networking &amp; Wireless
---

### Post by arysar on 2015-06-12
Hi, 

I have an HP mini 210 that works quite well an have no problems with wifi, but after an update  the wifi connects but it doesnt give me internet access, i put a cable between my router and the laptop, i get internet access and run the wireless-info script.

Attached are the results

Thanks!

[ATTACH]262537[/ATTACH]

---

### Post by ajgreeny on 2015-06-12
Try command ```
ping -c 3 91.189.94.12
```followed by ```
ping -c 3 ubuntuforums.com
```and show us the output of each.

I suspect that you may have a DNS server problem and if so the the first command should be successful but the second command will fail.  There are ways around this that are quite easy to deal with buit let's go one step at a time.

---

### Post by arysar on 2015-06-12
The result is:

```

$ ping -c3 91.189.94.12 
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms

$ ping -c3 ubuntuforums.com
ping: unknown host ubuntuforums.com
```

---

### Post by ajgreeny on 2015-06-12
OK, so neither command is working.

Are there any other computers on your LAN that you can ping to check that you can at least do that successfully?  
For example, assume your machine is connected to the router with IP 192.168.1.2 and another machine is connected with IP 192,168.1.3
Now run **ping -c 3 192.168.1 3** from your computer to see if you can reach the other machine.

You can get the IPs of machines from command **ifconfig** in Linux, but I've no idea how in Windows if the other is running that OS.

---

### Post by wyliecoyoteuk on 2015-06-12
In windows it is  **ipconfig**.
It may be a firmware issue on the wifi card.
Try a cold boot.

---

### Post by arysar on 2015-06-12
I hibernated the netbook and started it again then it can connects but after a short time it cant, here are the ping's results:


```

$ ping -c3 91.189.94.12 
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=51 time=457 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=51 time=470 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=51 time=470 ms

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 457.798/465.990/470.123/5.792 ms

leonardo@lypMini:~$ ping -c3 91.189.94.12 
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=51 time=234 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=51 time=234 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=51 time=987 ms

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 234.134/485.508/987.635/355.057 ms

leonardo@lypMini:~$ ping -c3 91.189.94.12 
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
From 192.168.0.30 icmp_seq=2 Destination Host Unreachable
From 192.168.0.30 icmp_seq=3 Destination Host Unreachable

--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, +2 errors, 100% packet loss, time 1999ms
pipe 2


```


Then I ping to another computer in the LAN


```

leonardo@lypMini:~$ ping -c3 192.168.0.11
PING 192.168.0.11 (192.168.0.11) 56(84) bytes of data.
From 192.168.0.30 icmp_seq=1 Destination Host Unreachable
From 192.168.0.30 icmp_seq=2 Destination Host Unreachable
From 192.168.0.30 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.11 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
pipe 3


```

---

### Post by arysar on 2015-06-12
I reset the modem-router and the problem was solved

thanks for your help!!

---

