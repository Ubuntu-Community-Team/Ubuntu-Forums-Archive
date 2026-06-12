---
title: "Mac address not recognized!! (Lucid 10.04 64bits)"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-07-19
Greetings!

I installed 10.04 server 64 bits on a machine at work. Setup went flawlessly and everything is working....EXCEPT...my network connection.

My network admin gave me a static IP to use and the server is apparently not wanting it

a) System->Preferences->Network connection->Add

-`Wired` tab is blank: entered MAC address ; 
-`IP 4` tab is set to Automatic DHCP : change it to `manual` with the static IP and DNS info I got.

I check `Available to all users`....and EVERYTHING GETS BLANKED OUT!

b) I re-enter all in the info above and do not check `Available to all users`. 

-Click ok
-Open terminal session and `ifconfig` gives me an IP address that IS NOT MATCHING what I entered. WTF???:shock:

Not sure if it matters...my host info

```
albert@gordeaux:~$ uname -a
Linux gordeaux 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux
```Bottom-line: I can only use DHCP but I need to use the static IP my admin gave me ; otherwise my network traffic will be limited. The weird part is that I have a 32bits machine next this one running Lucid desktop version. MAC address is recognized and static IP is working fine.

Is it a bug or do I mess something up during the setup?? Can I fix this? Any help is welcome.

Al.

---

### Post by cariboo on 2010-07-19
Instead of adding a connection, why not edit the existing one? Or do you have more than one nic in the system?

---

### Post by kristo5747 on 2010-07-19
> **cariboo907 said:**
> Instead of adding a connection, why not edit the existing one? Or do you have more than one nic in the system?


There is nothing to edit in the "Network connections" widget. It is blank. Ergo, me having to create a new connection...


Only one NIC on this box...

---

### Post by hackerseraph on 2010-07-19
could you post up a screenshot and also can we get a full output of your ifconfig

---

### Post by Linux000 on 2010-07-19
To clarify, DHCP does work with the same network card?

---

### Post by kristo5747 on 2010-07-19
> **hackerseraph said:**
> could you post up a screenshot and also can we get a full output of your ifconfig

ifconfig output ...........

```
albert@gordeaux:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:45:de:21  
          inet addr:10.8.30.153  Bcast:10.8.30.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe45:de21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5780897 (5.7 MB)  TX bytes:897002 (897.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:484604 (484.6 KB)  TX bytes:484604 (484.6 KB)

```three screenshots.......

[IMG]file:///tmp/moz-screenshot.png[/IMG]

-FIRST screenshot: tab was blank ; I have done 4 Lucid installs where "Wired" tab read "Auto eth0". First time I saw that. I had to click `Add`.
-SECOND screenshot: I entered MAC address manually. If I check "Available to all users" and Apply, all the text boxes get emptied, blanked out.

---

### Post by kristo5747 on 2010-07-19
> **Linux000 said:**
> To clarify, DHCP does work with the same network card?


Correct. DHCP works fines with the same network card.

---

### Post by Linux000 on 2010-07-19
If you have used DHCP, then there should be an auto eth0 or so connection in network manager, could so post the output of "cat /etc/network/interfaces"

---

### Post by kristo5747 on 2010-07-19
> **Linux000 said:**
> If you have used DHCP, then there should be an auto eth0 or so connection in network manager, could so post the output of "cat /etc/network/interfaces"


BINGO!!  That was my fault. Doing "cat /etc/network/interfaces" gave me all that crap

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:1e:c9:45:de:21

```Ater comparing to another machine's interface file I commented out all the "primary network interface" section which I manually created myself tried to fix this....:redface:

Rebooted the machine and voila. Mac address is recognized, so is static IP.

Gents, thanks for your input/patience with an idiot like me.

Al.

---

### Post by Linux000 on 2010-07-19
Anytime, Happy I could help.

---

