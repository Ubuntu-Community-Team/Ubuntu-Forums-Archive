---
title: "ping works, nslookup works; firefox &amp; wget don´t"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by adieb on 2007-01-26
**SOLVED +++ SOLVED**

hey guys,

this is actually my first post and it´s describing a problem i did not found anything for in the internet.

i´m running ubuntu feisty, everything works fine, networking to, my VPN-connection through university too.
suddenly, i think it came from trying to de-install vmware-workstation an vmware-player and stuff, my internet didn´t work anymore.

it only works (e.g. in firefox), when I type the IP-Adress. if I type [www.google.com](www.google.com) it says, couldn´t find server...

but.... If i ping [www.google.com](www.google.com), it works and it (of course) shows me the ip of google.

but.... wget says cant resolve hostname when i type the same

nslookup works fine too...


-----

my configuration:

eth0 over DHCP
ppp0 over VPN          | that works fine...

in etc/resolv.conf y find the correct namervers (from DHCP)

-----

i tried everything, flushing the route´s cache, the routing table too, restarting networking a thousand times.

i just don´t understand! how can ping work but wget not????

please help

thx

PS: the problem didn´t occur in any context of updating testing software (feasty)

---

### Post by Stephen Howard on 2007-01-27
Hmm, interesting problem.  Just fishing around for an answer, could you provide the following additional info...

cat /etc/host.conf

cat /etc/hosts

cat /etc/resolv.conf

cat /etc/nsswitch.conf

netstat -rn

netstat -r

ifconfig

ip route show

---

### Post by adieb on 2007-01-27
alright here are the outputs:

**cat /etc/host.conf:**
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

**cat /etc/hosts:**
127.0.0.1 localhost
127.0.1.1 zibby1

# The following lines are desirable for IPv6 capable hosts
192.168.44.129 easy


**cat /etc/resolv.conf**
search dhcp.stw-bonn.de
nameserver 192.168.1.10
nameserver 192.168.1.130


**cat /etc/nsswitch.conf**
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


**netstat -rn**
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
192.168.1.130   192.168.44.1    255.255.255.255 UGH       0 0          0 eth0
192.168.1.41    0.0.0.0         255.255.255.255 UH        0 0          0 ppp0
192.168.1.10    192.168.44.1    255.255.255.255 UGH       0 0          0 eth0
192.168.44.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     192.168.44.1    255.255.0.0     UG        0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 ppp0


*interesting thing here was that the last line (i think it should be the the default route) changed itself from 192.168.44.1 (Router-field) to 0.0.0.0 when i start my vpn connection...*


**netstat -r**
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
dns-b.stw-bonn. int-ve-26.stw-b 255.255.255.255 UGH       0 0          0 eth0
vpn-02-a.stw-bo *               255.255.255.255 UH        0 0          0 ppp0
dns-a.stw-bonn. int-ve-26.stw-b 255.255.255.255 UGH       0 0          0 eth0
192.168.44.0    *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.0.0     int-ve-26.stw-b 255.255.0.0     UG        0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 ppp0


**ifconfig** 
eth0      Protokoll:Ethernet  Hardware Adresse 00:14:85:42:2A:97  
          inet Adresse:192.168.44.27  Bcast:192.168.44.255  Maske:255.255.255.0
          inet6 Adresse: fe80::214:85ff:fe42:2a97/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1504585 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1553177 errors:0 dropped:0 overruns:7 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:1134199244 (1.0 GiB)  TX bytes:285574600 (272.3 MiB)
          Interrupt:20 Basisadresse:0x8000 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5204 (5.0 KiB)  TX bytes:5204 (5.0 KiB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung  
          inet Adresse:212.201.77.229  P-z-P:192.168.1.168  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1490  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:63 (63.0 b)  TX bytes:69 (69.0 b)


**ip route show**
192.168.1.130 via 192.168.44.1 dev eth0 
192.168.1.10 via 192.168.44.1 dev eth0 
192.168.1.168 dev ppp0  proto kernel  scope link  src 212.201.77.229 
192.168.44.0/24 dev eth0  proto kernel  scope link  src 192.168.44.27 
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 via 192.168.44.1 dev eth0 
default dev ppp0  scope link

-------

thx

---

### Post by adieb on 2007-01-27
**[SIZE="4"]SOLVED![/SIZE]**

wow, what a strange thing

the error was in /etc/nsswitch.conf :

network: files dns    ## dns was missing


i don't know how that could happen, but anyway before your reply i didn't even know about that file.
Thx a lot

---

### Post by Stephen Howard on 2007-01-27
Not entirely sure why your fix works - in fact, it shouldn't work because dns has nothing to do with the networks: database.  But who are we to argue!

I was going to suggest editing the hosts: line by moving 'dns' so that its second in the list - just after 'files'.  It seemed logical because the mDNSminimal lookup would fail for everything except domain names ending in .local.  Another potential solution might have been to delete the square brackets and their contents so that the lookup would continue to try other methods to resolve the domain name.

---

### Post by adieb on 2007-01-27
yes, right you are!

the /etc/nsswitch.conf file must look like this: (in that section)

hosts:  files dns
networks: files dns

so thx a lot again ;-)

bye

---

### Post by Stephen Howard on 2007-01-28
I don't think you need to change the Networks: line - certainly not by adding 'dns' to it.

Also note that the hosts: edit solution effectively turns off Zeroconf/Avahi name resolution (ie typically domains ending in .local ).   If you want zeroconf to work its probably best to update libnss-mdns to the latest version and see if the problem persists (I suspect the problem would stop).  Unfortunately, as of this date Ubuntu's repositories are two versions behind the latest release.

---

### Post by adieb on 2007-01-28
well, thats all far behind my horizon ;-)

i don't understand the fine mechanics of network related stuff.

hehe, so i am happy if my network works. the name says it

---

### Post by munpfazy on 2007-07-29
Hey guys - just wanted to say thanks.  

I wound up with the exact same problem, and the same fix worked like a charm.  

In my case, the problem *was* tied to a specific administrative event.  In case it's useful as google bait, here's the description.

I'm running Slackware 11.0.
While trying to install some software with an annoying set of a la carte gnome related dependencies, I decided to try out Dropline Gnome for the first time.  I installed it, played around with it a bit, and later decided to remove it.  I used the dropline gnome installer to remove the software, and found that it left my system a huge mess, with missing packages and new unofficial packages and all sorts of random config file changes.  (You can bet that's the last time I *ever* try dropline gnome on a system that I'm planning to use again....  yuck!)  

After an hour of reinstalling things and pruning stuff in /etc by hand, I wound up with a system that looked normal and seemed to work fine except for the weird DNS problem described above.  Ping worked, dig worked, but everything else (firefox, elinks, fetchmail, ssh) failed to resolve any host name.  Turns out my nsswitch.conf file had exactly the same wacky new hosts line described above.

Anyway, thanks for the help.  For all but a serious networking guru, this one was a stumper!

---

