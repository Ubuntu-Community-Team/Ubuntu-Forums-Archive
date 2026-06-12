---
title: "Connect to network, but no internet"
date: 2013-10-12
forum: Networking &amp; Wireless
---

### Post by stevenpmacneil on 2013-10-12
I'm using Ubuntu 13.04 on an older Gateway for several months with no issues. Had a brief (5 second) power failure about 2 weeks ago, and lost the ability to connect to the internet. The Windows computers and Apple computers in the house can still connect to the network and the internet, but now the Ubuntu computer can connect to the network, but not the internet.

I tried reinstalling Ubuntu 13.04 from scratch, but it didn't help. 

I read several forum threads on similar problems, but am unable to find a solution.  Please note that my command line knowledge is really bad.

I ran some of the commands that had been recommended to see what the feedback looks like, and here they are "ifconfig", "route -n" and "ping google.com":

 ```
steven@steven-GM5091H:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:26:70:08  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe26:7008/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7874639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5246751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2014873843 (2.0 GB)  TX bytes:2402127989 (2.4 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:56222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56222 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4171759 (4.1 MB)  TX bytes:4171759 (4.1 MB)

```

  ```
steven@steven-GM5091H:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
steven@steven-GM5091H:~$ 

```

```
steven@steven-GM5091H:~$ ping google.com
ping: unknown host google.com
steven@steven-GM5091H:~$ 
```

Until 2 weeks ago, I had perfect internet connection, and my other computers still connect no problem, so I don't think it's a hardware issue, but I'm at a loss.  Has anyone seen this before, and perhaps know what's wrong?  Thank you so much!

---

### Post by sanderj on 2013-10-13
Useful first steps. Next steps:

```

traceroute -n 8.8.8.8
mtr -nrc2 8.8.8.8
```

Post the output here.

---

### Post by stevenpmacneil on 2013-10-13
traceroute -n 8.8.8.8 command gave the following output:

  ```
steven@steven-GM5091H:~$ traceroute -n 8.8.8.8
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute
 * traceroute
Try: sudo apt-get install <selected package>
steven@steven-GM5091H:~$ 

```
  

mtr -nrc2 8.8.8.8 command gave the following output

  ```
steven@steven-GM5091H:~$ traceroute -n 8.8.8.8
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute
 * traceroute
Try: sudo apt-get install <selected package>
steven@steven-GM5091H:~$ 

```

---

### Post by varunendra on 2013-10-13
> **stevenpmacneil said:**
> 
The program 'traceroute' can be found in the following packages:
 * inetutils-traceroute
 * traceroute

..please do what those messages suggested -
```
sudo apt-get install traceroute
```
..then try again what sanderj asked for and post back the results.

**PS:**
And it would be better to use '**Code**' box to post commands & terminal outputs instead of manually formatting them. :) Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by stevenpmacneil on 2013-10-13
Thank you for the input, I have much to learn.  I ran the command sudo apt-get install traceroute and got the following output:

```
  [FONT=&quot]steven@steven-GM5091H:~$ sudo apt-get install traceroute
[sudo] password for steven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'traceroute' has no installation candidate
steven@steven-GM5091H:~$ 
[/FONT]
  
```


Thank you for the help!

---

### Post by varunendra on 2013-10-13
Hmm.. make sure the "Universe" repository is enabled in Software Soruces -

Press **Alt+F2** > type **software-properties-gtk** > press **Enter** or click the item that comes up >  Supply your login password when asked > under "**Ubuntu Software**" tab in the opened box, make sure the **(universe)** repository is enabled (has a tick in the checkbox) > Close it and in a terminal, do -
```
sudo apt-get update
sudo apt-get install traceroute
```
Let me know if having any difficulty again.

---

### Post by stevenpmacneil on 2013-10-13
I opened this GTK software properties window as instructed above, and under the "Ubuntu Software" tab,the option for the universe repository is already selected.  Since my Ubuntu computer can't connect to the internet, I'm guessing that it can't connect to the universe repository to get and install the traceroute package. I'd really appreciate any ideas. Thanks!

---

### Post by sanderj on 2013-10-13
When you live-boot from CD or USB stick, is Internet working?

We're talking your *wired* ethernet connection, I hope? Not wireless?
And: hopefull no firewall installed?

---

### Post by stevenpmacneil on 2013-10-13
Hi, that's correct.
1) My Ubuntu is connected via a wired ethernet connection
2) When I use the "try Ubuntu" option on the live DVD, I can't get onto the internet. Firefox responds with "server not found". However, in both my installed O/S and in the DVD "try Ubuntu" mode, I can open the "files" icon, and "browse network" and access the other computers and network drives in the house.
3) I don't have a firewall.

Thanks!

---

### Post by sandyd on 2013-10-13
Whats the output of
```

ping -c 10 8.8.8.8
cat /etc/resolv.conf
```

---

### Post by stevenpmacneil on 2013-10-13
The output from the ping command was:
```
  [FONT=&quot]steven@steven-GM5091H:~$ ping -c 10 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9072ms

steven@steven-GM5091H:~$ 

```

The output from the resolv.conf command was:
```
[/FONT]
[FONT=&quot][/FONT]
[FONT=&quot]  [FONT=&quot]steven@steven-GM5091H:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hm.shawcable.net
steven@steven-GM5091H:~$ 

```
Thanks!
[/FONT]
   [/FONT]

---

### Post by Iowan on 2013-10-13
Well, that didn't work. Can you ping the gateway?
(ping -c 10 192.168.0.1)

---

### Post by sandyd on 2013-10-13
Have you tried
a) Deleting the DHCP reservations on the router (all of them).
b) Restarting the router

---

### Post by stevenpmacneil on 2013-10-13
Ping'ed the gateway as indicated above, and got this:
```
  [FONT=&quot]steven@steven-GM5091H:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9070ms

steven@steven-GM5091H:~$ 

```
Thanks.
[/FONT]

---

### Post by sanderj on 2013-10-13
> **stevenpmacneil said:**
> Ping'ed the gateway as indicated above, and got this:
```
  [FONT=&quot]steven@steven-GM5091H:~$ ping -c 10 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9070ms

steven@steven-GM5091H:~$ 

```
Thanks.
[/FONT]

No, you should:

```
ping 192.168.0.1
```

HTH

---

### Post by Iowan on 2013-10-13
> **Iowan said:**
> (ping -c 10 192.168.[COLOR="#FF0000"]0[/COLOR].1)Looks like the (pinged) gateway address is wrong.

---

### Post by stevenpmacneil on 2013-10-13
Sorry about that typo. Ran the amended ping, and got this:
```
  [FONT=&quot]steven@steven-GM5091H:~$ ping -c 10 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 8999ms

steven@steven-GM5091H:~$

```
[/FONT]

---

### Post by sanderj on 2013-10-13
So you can't reach your default gateway. That's bad.

How did your Ubuntu machine get the IP address? Automatically (thus via DHCP), or did you fill it out manually?

---

### Post by stevenpmacneil on 2013-10-13
Ubuntu must have gotten it automatically, because I didn't type it in.  When I run an ipconfig command in my Windows computer, it returns with an IP address of 192.168.0.101 and a default gateway of 192.168.0.1.  When I open the "network connection information" window in Ubuntu, it shows that my IP address is 192.168.0.100 (whereas the Windows computer's IP address has the last three digits as "101")  Is this just because they're different computers and need a unique ending to the IP address, or is Ubuntu getting the wrong IP address?
Thanks!

---

### Post by sanderj on 2013-10-13
Your IP address look allright. Strange.

Disconnect the ethernet cable, wait two seconds, and connect it again. Then

```
grep -i dhcp /var/log/syslog
```

and post the output here.

---

### Post by stevenpmacneil on 2013-10-13
Progress!  I changed the 3-digit ending for the IP address that Ubuntu was using (100) to 101 to match my Windows computer, and Firefox can now connect to the internet, albeit brutally slow, while my other computers' internet access is still blazing fast (40 seconds to load the Google.com search page in Ubuntu versus 2 seconds in Wiindows).  Something is still off.

---

### Post by varunendra on 2013-10-13
> **stevenpmacneil said:**
> Firefox can now connect to the internet, albeit brutally slow
Make sure that IPv6 is set to "Ignore" for the connection in Network Manager -

**nm-applet** at the top-right corner > **Edit Connections..** > "**Wired**" tab > double-click your connection to **edit** it > "**IPv6 Settings**" tab > set "**Method**" to "**Ignore**"

Try browsing a bit and see if the speed is improved. If not, please install "**ethtool**" (if not already installed) -
```
sudo apt-get install ethtool
```
Then post back the outputs of the following -
```
sudo ethtool eth0
ifconfig
lspci -nnk | grep -iA2 net
nm-tool
ping -c4 google.com
```

---

### Post by sanderj on 2013-10-14
> **stevenpmacneil said:**
> Progress!  I changed the 3-digit ending for the IP address that Ubuntu was using (100) to 101 to match my Windows computer, and Firefox can now connect to the internet, albeit brutally slow, while my other computers' internet access is still blazing fast (40 seconds to load the Google.com search page in Ubuntu versus 2 seconds in Wiindows).  Something is still off.

Is the Windows computer still on? If so: if you turn it off, is your Linux connection fast?

---

