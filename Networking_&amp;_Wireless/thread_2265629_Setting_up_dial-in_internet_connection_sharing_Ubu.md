---
title: "Setting up dial-in internet connection sharing Ubuntu 14.04"
date: 2015-02-16
forum: Networking &amp; Wireless
---

### Post by jremington on 2015-02-16
I'm having trouble setting up an old-fashioned dial-in server at work. I have a US Robotics 56K modem on COM1 and have successfully installed pppd so that from home, I can dial up the computer and log in, or *attempt* to connect to the internet (I live in the country and have no other reliable internet connection). The work computer is connected to the rest of the world via eth0.

However, the dial-up connection cannot talk to to the world via eth0. The proxyarp option of pppd does not seem to work, and I've also tried setting up iptables to do address translation and forwarding (as in a router), but that doesn't seem to work either. 

In other words, from home I can dial up the work computer, get a connection and successfully ping the work computer (at 192.160.1.1), but not ping 8.8.8.8

Current pppd options:
```

root@xenon:/etc/ppp# ./options.sh
asyncmap 0
noauth
crtscts
lock
hide-password
modem
netmask 255.255.255.0
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

root@xenon:/etc/ppp# cat options.ttyS0
192.168.1.1:192.168.1.2
    noauth
```

After I've dialed up, ifconfig and route provide (with my work ip address partially set to xxx)

```
root@xenon:/etc/ppp# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5b:cd:f7:95  
          inet addr:xxx.xxx.130.192  Bcast:xxx.xxx.131.255  Mask:255.255.254.0
          inet6 addr: fe80::206:5bff:fecd:f795/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1111735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15691 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171579521 (171.5 MB)  TX bytes:2460871 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:390643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:334180418 (334.1 MB)  TX bytes:334180418 (334.1 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.1.1  P-t-P:192.168.1.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:874 (874.0 B)  TX bytes:112 (112.0 B)

root@xenon:/etc/ppp# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         xxx.xxx.130.1   0.0.0.0         UG    0      0        0 eth0
xxx.xxx.130.0   0.0.0.0         255.255.254.0   U     1      0        0 eth0
192.168.1.2     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
```

The netmask assigned to the remote computer seems to be wrong, but the remote computer shows 255.255.255.0 as expected.

Yes, ipv4_forward is set to 1 in /etc/sysctl.conf
```
root@xenon:/etc/ppp# cat /proc/sys/net/ipv4/ip_forward
1

```

I've tried different combinations for the local IP(192.168.x.y) addresses without success.

Suggestions would be viewed with enthusiasm!  
Note: there are many, many forum and web postings on this topic, and most of them seem to be outdated or wrong.

---

### Post by jremington on 2015-02-16
Making a little progress, trying iptables again.

Following the directions in the "Official Ubuntu Documentation" on internet connection sharing here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

I set up iptables as follows:
```
sudo iptables -A FORWARD -o eth0 -i ppp0 -s 192.168.1.2 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables-save | sudo tee /etc/iptables.sav
#Edit /etc/rc.local and add the following line before the "exit 0" line: 
iptables-restore < /etc/iptables.sav
```

This works and from home I can now dial up the work computer, connect to the internet and ping 8.8.8.8.

However, I can't access any DNS servers, so nameserving isn't working.

/etc/resolv.conf is OK and has my company's DNS servers and search domain.

Continuing to follow the directions in the "Official Documentation" I find that they are incorrect or outdated.

e.g.:
```
Unless your ICS gateway can also perform [DNS]("http://en.wikipedia.org/wiki/Domain_Name_System"), you must manually configure the client with your ISP DNS servers. If you do not know your ISP's DNS servers, you can use [OpenDNS servers]("https://www.opendns.com/start?device=ubuntu") instead. 

[LIST]
[*]Backup your current /etc/resolve.conf file: 
[/LIST]
sudo cp /etc/resolv.conf /etc/resolv.conf.backup
[LIST]
[*]Open /etc/dhcp3/dhclient.conf with your favorite text editor: 
[/LIST]
sudo nano /etc/dhcp3/dhclient.conf
[LIST]
[*]Search for the line that starts "prepend domain-name-servers", and change it to look like this: 
[/LIST]
prepend domain-name-servers 208.67.222.222,208.67.220.220;208.67.222.222  and 208.67.220.220 are OpenDNS DNS servers. If you wish to use your  ISP's DNS servers, use them here instead of the OpenDNS servers. 
 
**Restart networking**

 sudo /etc/init.d/networking restartOnce this is finished, your client will now have access to the Internet via ICS. Please direct any questions/comments to the [Internet Connection Sharing Documentation]("http://ubuntuforums.org/showthread.php?t=503287") thread. 
```

Of course there is no directory /etc/dhcp3  
so I modified /etc/dhcp/dhclient.conf as suggested above, to use the OpenDNS servers.

"sudo /etc/init.d/networking restart" also fails, so I rebooted instead.

After reboot, my original /etc/resolv.conf remains unchanged, so the file /etc/dhcp/dhclient.conf modification did not take effect. Not that I actually cared, as it should not have made a difference even it the modification had been done!  Obviously, don't bother with this step.

I'm still stuck, so suggestions will still be much appreciated!

---

### Post by jremington on 2015-02-16
Solved, sort of. My home machine is a Windoze machine, so I set the home ppp connection to look up the public DNS servers 208.67.222.222,208.67.220.220

I also disabled the proxyarp option in pppd, since it doesn't seem to do anything.

I can now Google to my heart's content, at 26.6 K baud! And it took only 3 days of work. I have to say that most of the documentation on these arcane subjects sucks, and the rest is either misleading or wrong.

For others that may follow my lonely road, here are the options for setting up mgetty and pppd.** Note that the DNS problem is still unsolved,** that is, the host machine running pppd does not seem to consult /etc/resolv.conf  and setting the pppd option ms-dns x.y.z.c doesn't seem to work either.

```

root@xenon:/etc/mgetty# cat login.config
# login.config
# standard user login, as a remote terminal connection (uncomment -> tested and works on ubuntu 14.04)
#*      -       -       /bin/login @

#
# Automatic PPP startup on receipt of LCP configure request (AutoPPP).
#
/AutoPPP/ -     a_ppp   /usr/sbin/pppd auth -chap +pap login debug


```
```

root@xenon:/etc/mgetty# cat mgetty.config
#
# mgetty configuration file

# set the global debug level to "4" (default from policy.h)
debug 4

# set the local fax station id
fax-id  

# access the modem(s) with following speed
speed 115200

# use an alternate issue file, to avoid being bitten by linuxlogo
issue-file /etc/issue.mgetty
# ----- port specific section -----
# USR Sportster 56K v2 connected to ttyS0: don't do fax, less logging
#
port ttyS0
init-chat "" ATS0=0
debug 4
data-only y

```

```

#/etc/init/ttyS0.conf as follows
# This service maintains mgetty on /dev/ttyS0.

start on stopped rc RUNLEVEL=[2345]
stop on starting rc RUNLEVEL=[!2345]

respawn
exec /sbin/mgetty -n 2 ttyS0

```

#options for pppd:
```

root@xenon:/etc/ppp# ./options.sh
asyncmap 0
noauth
crtscts
lock
hide-password
modem
netmask 255.255.255.0
lcp-echo-interval 30
lcp-echo-failure 4
noipx

```
```

root@xenon:/etc/ppp# cat options.ttyS0
192.168.1.1:192.168.1.2
        noauth

```

#pap-secrets just runs regular login authentication

```

root@xenon:/etc/ppp# cat pap-secrets
#
# /etc/ppp/pap-secrets
#
# INBOUND connections

# Every regular user can use PPP and has to use passwords from /etc/passwd
*       *       ""      *

# UserIDs that cannot use PPP at all. Check your /etc/passwd and add any
# other accounts that should not be able to use pppd!
guest   *       "*"     -
master  *       "*"     -
root    *       "*"     -
support *       "*"     -
stats   *       "*"     -


```

Let me know if I've forgotten anything!

---

