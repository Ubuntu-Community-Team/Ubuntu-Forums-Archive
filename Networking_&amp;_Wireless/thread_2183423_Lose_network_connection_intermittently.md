---
title: "Lose network connection intermittently"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by brichert on 2013-10-24
Howdy,

I've got a problem I can't solve. At work I am migrating my old workstation to the new and running ubuntu 12.04 (on both). Everything is going fine except ... if I let the new machine sit for a while, I lose internet access. This is especially troubling when I leave for the night, try to login at home, and can't connect. Possibly it occurs when the screen goes to sleep, but I'm not sure about that. It occurs during the day as well. How does one fix it? sudo service network-manager restart doesn't seem to work. But if I pull out the ethernet cord and immediately plug it back in, within a few moments I'm up and running. One suspects the cable, but if I plug in the old workstation (in theory running the same system ... although 12.04 was upgraded from an old version there and on the new machine it is a clean install) it works fine, and stays online all day and all night. I found out about the pull the cord fix when I was swapping the cord back and forth between machines so I could google the problem on the old connected machine, and then try it on the new; eventually I realized that just pulling and replacing the cord fixed it. I'm running gnome classic. The new machine is a Dell optiplex 7010 (dual booting).

ifconfig

eth0      Link encap:Ethernet  HWaddr 90:b1:1c:78:87:26  
          inet addr:129.65.56.22  Bcast:129.65.56.255  Mask:255.255.255.0
          inet6 addr: fe80::92b1:1cff:fe78:8726/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:311191 errors:0 dropped:901 overruns:0 frame:0
          TX packets:58242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52445697 (52.4 MB)  TX bytes:5766377 (5.7 MB)
          Interrupt:20 Memory:f7f00000-f7f20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10735 (10.7 KB)  TX bytes:10735 (10.7 KB)

content of /etc/network/interfaces

uto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 129.65.56.22
      netmask 255.255.255.0
      gateway 129.65.56.250
      dns-nameservers 129.65.16.254 129.65.21.254


On the old machine, the network/interfaces file is

auto lo
iface lo inet loopback

iface eth0 inet dhcp
#address 129.65.56.22
#netmask 255.255.255.0
#gateway 129.65.56.250

I see the difference of course, but both result in the same problem.

Any help would be appreciated!

---

### Post by Hadaka on 2013-10-24
Hi, not sure if you posted a copy and paste error
or if its the actual configuration. You have "uto lo" instead
of "auto lo"  for the loopback via your /etc/network/interfaces file.
Beyond that,my knowledge of such is VERY limited,hopefully its
a quick and easy fix. Good luck !!

---

### Post by brichert on 2013-10-25
Alas, yes, that is just a copy error. I must not have grabbed all the text when I copied the file over. It does read auto lo.

---

### Post by Michael_Kolonay on 2013-10-25
If you are using the interfaces file than the network manager has nothing to do with your problem (they are two seperate ways of connecting). Make sure your network manager is set to unmanaged; however,  I do not think that is your problem. I had the same issue with one of my network machines, but I cant remember what solved it. I will think and poke around and get back to you...

By the way, what does **route -n **display when the machine wont connect?

---

### Post by brichert on 2013-10-25
The network manager is set to unmanaged. I'll get back to you about route -n. I have to wait for the connection to fail, and like taking your car to the mechanic ...

---

### Post by brichert on 2013-10-31
Sorry for the delay. I've been busy at work and can't leave the bad connection plugged in overnight (I need to log in from home and can't risk it)

Below I've posed a route -n. The first is with no connection. The second is just after the internet started working (I pulled the cord and plugged it back in, as usual).

brichert@richert:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.65.56.250   0.0.0.0         UG    100    0        0 eth0
129.65.56.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
brichert@richert:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.65.56.250   0.0.0.0         UG    100    0        0 eth0
129.65.56.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
brichert@richert:~$

---

### Post by brichert on 2014-01-15
I don't suppose anyone has any advice to give me on this problem. I've googled the living daylights out of it, and made no headway. A few other bits of information.

The lspci command lists my ethernet card as:

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

I tried updating the driver, but that didn't seem to fix things.

The output of dmesg | tail -f (which I confess I don't really understand what it is doing or if it is relevant) is:

brichert@richert:~$ dmesg | tail -f
[26298.145826] e1000e: eth0 NIC Link is Down
[26301.842947] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[82915.357981] e1000e: eth0 NIC Link is Down
[82921.230165] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[97562.766900] e1000e: eth0 NIC Link is Down
[97566.116795] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[97583.132689] e1000e: eth0 NIC Link is Down
[97586.518510] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[170046.792498] e1000e: eth0 NIC Link is Down
[170051.734780] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx


Thanks for any help you can provide.

---

### Post by brichert on 2014-01-15
Oh, and here is the output of ethtool -i eth0

brichert@richert:~$ ethtool -i eth0
driver: e1000e
version: 2.5.4-NAPI
firmware-version: 0.13-4
bus-info: 0000:00:19.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
brichert@richert:~$

---

### Post by brichert on 2014-01-17
I notice in various log files that before the network goes down, the message (printed below) shows up, or so I think ... I'm a bit new reading the log files and can't completely parse what is going on ... In any event, I'm not trying to print, so what is cupsd doing anything at all. This message seems to show up frequently in the log. I don't see how it could possibly be related, but perhaps it will help with the puzzle?


Jan 17 14:52:08 richert kernel: [ 7482.256856] type=1400 audit(1389999128.963:30): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=985 comm="cupsd" pid=985 comm="cupsd" capability=36  capname="block_suspend"

---

### Post by brichert on 2014-01-21
One other bit of information. I asked tcpdump -i eth0 and it merrily churned away all night. When Firefox could no longer connect, it continued to report on various activitiy, so the card still seems to think that it is up and running. Any ideas?

---

### Post by brichert on 2014-01-22
Yet another bit of information as I waste away trying to figure this out. If I start tcpdump after the ethernet goes down, nothing happens. Finally, one hits ^C, and it prints out one line and stops after thinking a bit. If I ping [www.google.com](www.google.com) it doesn't do anything, that is, it doesn't report failure ... it just sits there until I kill it.

Anyone have any ideas? I'm having this nice conversation with myself about it, but don't seem to be getting anywhere.

---

### Post by brichert on 2014-01-28
A new twist. Things are getting worse ... now pulling the cable out and plugging back in doesn't fix it immediately like it did before. It takes three or four times doing this, but then things come right back on line. In the past, it only seemed to drop the connection while I wasn't using the system, but now, it dropped the connection about one minute after I had googled something.

---

### Post by brichert on 2014-05-21
This problem is solved in [http://ubuntuforums.org/showthread.php?t=2224094]("http://ubuntuforums.org/showthread.php?t=2224094")

---

