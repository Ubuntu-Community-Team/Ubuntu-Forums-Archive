---
title: "Wired Network Stops Working"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by steve_c on 2008-01-25
I have a computer that's mostly accessed remotely running 64-bit Ubuntu.

For some reason it occasionally stops responding to the SSH connection. I can ping it remotely. If I go to the computer I can't ping anything past localhost. I don't see any signs of strangeness in /var/log/messages or /var/log/syslog. Using /etc/init.d/networking restart does not fix the problem. Using ifup -a *usually* fixes the problem, but not always.

Any thoughts?

Thanks for any help.

---

### Post by andguent on 2008-01-25
For troubleshooting info, could you post the output for the following commands(feel free to hide any external network settings):

cat /etc/network/interfaces
lspci|grep -i ethernet
route -n
ps -ef|grep dhclient

The output from the following commands should be compared when the connection is working vs when the connection is not working. Posting this info here is optional, and possibly excessive:
iptables -L
netstat -ntlp

Are you running any firewall software? Any special wiring? When you say you connect to it remotely, is this from across the house or across the town?

---

### Post by steve_c on 2008-01-28
When working:
```
root@obsidian:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 10.79.136.39
netmask 255.255.255.0
gateway 10.79.136.254

auto eth0

root@obsidian:~# lspci|grep -i ethernet
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)

root@obsidian:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.79.136.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.79.136.254   0.0.0.0         UG    100    0        0 eth0

root@obsidian:~# ps -ef|grep dhclient
root     11061 11014  0 12:45 pts/3    00:00:00 grep dhclient

root@obsidian:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

root@obsidian:~# netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:49613           0.0.0.0:*               LISTEN     4475/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4457/portmap        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5336/cupsd          
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN     10945/2             
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN     11012/3             
tcp6       0      0 :::22                   :::*                    LISTEN     5234/sshd           
tcp6       0      0 ::1:6010                :::*                    LISTEN     10945/2             
tcp6       0      0 ::1:6011                :::*                    LISTEN     11012/3             

```

When broken:
```

root@obsidian:/home/stevec/Desktop# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

root@obsidian:/home/stevec/Desktop# netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:49613           0.0.0.0:*               LISTEN     4475/rpc.statd      
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4457/portmap        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5336/cupsd          
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN     11429/0             
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN     11012/3             
tcp6       0      0 :::22                   :::*                    LISTEN     5234/sshd           
tcp6       0      0 ::1:6010                :::*                    LISTEN     11429/0             
tcp6       0      0 ::1:6011                :::*                    LISTEN     11012/3             

```

I'm not running any firewall software. By remotely, I mean this machine is actually in the server room and I connect from my office in the same building. The problem is definitely local to this machine as there are other computers sharing the switch that don't experience this difficulty.

---

### Post by andguent on 2008-01-28
Well, the fact that sshd does not disappear in the "broken" netstat means sshd is not crashing. I would completely agree you are not running any firewalling of any sort. It is possible that your dns server is failing on you, and ssh is just taking a very long time to allow logins. Not able to ping anywhere is still confusing though.

A few more tests to run from the server are below, mostly while it is in "broken" mode. Please run these tests in healthy mode for your own comparison. Also keep in mind that if one fails, most others after it will fail. I am somewhat logically working further out from the box. If any of these fail, you probably just narrowed down your problem.


telnet 127.0.0.1 22 (if you get SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1 and some other garbage, this means the ssh process is responding, press CTRL+], then type quit to exit)

ssh 127.0.0.1 (just to see if ssh works for anyone anywhere, might take 3 minutes to respond, be patient, let it time out for full testing)

ssh 10.79.136.39 (is the main adapter functional at all, even to itself?)

ping 10.79.136.254 (can we get to default gateway by IP? testing for dns weirdness)

host [www.google.com](www.google.com) (does basic dns lookups work?)

mtr [www.google.com](www.google.com) (traceroute on steriods, will probably fail if ping above fails, lost packets and bold hostnames are bad)


Lets see if we can get a definitive failure here, it should point us in the right direction. Are there any other computers within the same basic wiring area that behave similarly OR behave perfectly fine all of the time? Duplicate, duplicate, duplicate. Plug in a tester laptop on the same spot of the switch and repeat some of these tests from it too, and connectivity to the server maybe.

---

### Post by andguent on 2008-02-01
Steve,

Any word on this? I would be curious to know how it turned out. If it is an intermittent problem, I understand that it simply might not show itself for a while.

---

### Post by steve_c on 2008-02-01
More from when it's broken:
```

root@obsidian:~$ telnet 127.0.0.1 22
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
^]

telnet> quit
Connection closed.

```
Took a long time for both the "connected" message and for the connection to close and give me a command prompt again.
```

root@obsidian:~$ ssh 127.0.0.1
The authenticity of host '127.0.0.1 (127.0.0.1)' can't be established.
root@127.0.0.1's password: 
Linux obsidian 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
etc--So it works.

root@obsidian:~$ ping 10.79.136.39
PING 10.79.136.39 (10.79.136.39) 56(84) bytes of data.
64 bytes from 10.79.136.39: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 10.79.136.39: icmp_seq=2 ttl=64 time=0.007 ms

--- 10.79.136.39 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.007/0.014/0.022/0.008 ms

root@obsidian:~# ping 10.79.136.254
PING 10.79.136.254 (10.79.136.254) 56(84) bytes of data.

--- 10.79.136.254 ping statistics ---
110 packets transmitted, 0 received, 100% packet loss, time 109358ms

root@obsidian:~# host www.google.com
;; connection timed out; no servers could be reached

root@obsidian:~# mtr www.google.com
Name or service not known: No such file or directory

```

To answer some of your other questions, I'm fairly sure the problem exists on the machine. Seven other computers plug into the same switch which then plugs into the larger network. I've tried switching ports on the switch (though I haven't switched cables, I think it's slightly less likely a bad cable would cause intermittent connectivity problems).

My big concern is that it's the hardware. This is a Dell server and the only expansion slots it has are PCIe x4 and x8, and a couple PCI-X. While it's under warranty, warranty work or trying to find a PCIe/X NIC is time-consuming and possibly costly. If it's not the hardware then it's possibly the OS. Unfortunately the only way I can think to test that is by booting it from something like a Knoppix live-CD, leaving it up for a day and seeing if the problem repeats itself.

I'd be thrilled if you had any other suggestions for me that could result in a better solution. Thank you for your help!

---

### Post by andguent on 2008-02-01
It might be worth picking up a Network USB adapter like one of these:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2002810027+1162810710&name=USB](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2002810027+1162810710&name=USB)

As for cables: Don't assume. :) Cables are cheap, replace it with a known good one, and then test the original somewhere else. I would run that ping test to your gateway, and then wiggle the current network cable all over the place, different angles, pull on it, be just a little mean to it. See if the pings change/drop.

Is it correct that most/all other devices on the same switch can ping the gateway ok? I just want to make sure that gateway usually responds.

If the gateway usually does respond, then your issue is probably one of the following:
* Bad network driver
* Bad network card
* Bad network cable
* Bad port on switch (some ports can fail while others work fine)

Change out one thing at a time, the cheapest item first. See if the problem goes away. I've never seen a bad network card driver in ubuntu for a wired connection. However I just did a search on your NIC and found a few hits,
including:
[http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114)
more specifically:
[http://ubuntuforums.org/showpost.php?p=1391210&postcount=4](http://ubuntuforums.org/showpost.php?p=1391210&postcount=4)

The specific post above sounds very similar to your problem. jbaloul implemented an ugly hack, but it sounds like it works. I may be taking my foot out of my mouth for saying it should not be a bad network driver. :)

---

### Post by andguent on 2008-02-01
Another thought would be, based on jbaloul's issue, to verify your server is not rebooting on it's own. Regularly running the command 'uptime' should give you that info. If uptime does not display the word 'days' anywhere in the output, then it has been up less than 24 hours.

---

