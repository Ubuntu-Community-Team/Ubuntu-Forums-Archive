---
title: "Internet works sorta?"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by wingsfan on 2006-12-22
help.  I have the internet up and running except that I cn only get to about half of the web pages and even then it is iffy if they will load or not.  I have DSL for my service and I also have a router in between my box and the dsl modem.  Any help you can give me would be appreciated

---

### Post by wingsfan on 2006-12-23
OK after reading around here for a while I was able to get the Internet completely up and running as fas as web browsing goes.  However, I still can't get synaptic to work for me.  I am really quite new to all this so any help would be great.  Thanks.

---

### Post by dbott67 on 2006-12-23
Hi Wingsfan (Detroit Red Wings?),

Many people have posted that they have had issues with name resolution with Ubuntu.

Most have had success by disabling ipv6 (see this thread [http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798) - post 50 & up is where it applies to Dapper & Edgy).

The basic steps are as follows for Dapper & Edgy:

1. Blacklist the ipv6 module:
```
sudo su 
echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6 
```
2. Disable ipv6 in Firefox
    - type **about:config** in the address bar
    - in the filter field type **ipv6**
    - set the value to TRUE (just double-click the entry to toggle between TRUE and FALSE)

3. Reboot
4. Verify ipv6 is disabled.  Issue the 2 commands below:
```
lsmod | grep ipv6
```
```
ip a | grep inet6
```
Both should not return anything.

5. Test it out... Firefox, Synaptic, Gaim, etc.

The thread above discusses the pros & cons of disabling ipv6.  In theory, having ipv6 **enabled** should not cause any problems, however, the reality is that it's causing grief for some.  Disabling ipv6 generally cures the problem.

If you're still having issues after this, can you please post the output of:
```
cat /etc/resolv.conf
```

-Dave (**[COLOR="Blue"]LeafsFan[/COLOR]**)

---

### Post by wingsfan on 2006-12-23
OK I am still having the synaptic problems.  There was no output about the ipv6 stuff.  Here is the output of 
cat /etc/resolv.conf
nameserver 192.168.1.1

---

### Post by dbott67 on 2006-12-23
A few things:

1. Are there any error messages that appear when you access Synaptic?  If so, can you post the output before trying the solution below?

2. 'nameserver 192.168.1.1' is your router.  Most routers have built-in DNS relay services that forward all internal requests to your ISP's DNS server, so this is normal.  Some users experience name resolution problems with the configuration above and have added the OpenDNS servers to the resolv.conf file.

Personally, I have a D-Link DI-614+ and have the same configuration as you do right now and have never had any problems (with either ipv6 or name resolution).  **What make & model router do you have?**

You can try manually adding the OpenDNS servers to your /etc/resolv.conf file and comment out your current one:
```
sudo gedit /etc/resolv.conf
```
```
[B][COLOR="Red"]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/B]
**[COLOR="Red"]#[/COLOR]** nameserver 192.168.1.1
```

If you notice an improvement (or it cures the problem) then you can make it permanent.  By default, the dhclient.conf file will overwrite the resolv.conf file each reboot, so you need to edit the file:

1. Backup the file first:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.bak
```

2. Edit the dhclient.conf file:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

3. Look for the following line:
```
#prepend domain-name-servers 127.0.0.1;
```
Remove the comment (#) and change it to:
```
prepend domain-name-servers **[COLOR="Red"]208.67.222.222, 208.67.220.220[/COLOR]**;
```

4. Next, look for the **[COLOR="Red"]domain-name-servers,[/COLOR]** and ***remove*** it:

```
**[COLOR="Blue"]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

5. Restart your network
```
dbott@edgy:~$ sudo/etc/init.d/networking restart
```

Like I said, I've never had to resort to this, however, there are a number of people in this forum that this technique has helped them (as well as the ipv6 hack).

-Dave

---

### Post by wingsfan on 2006-12-24
Alright.  Everything is working perfectly now.  Thank you very much for all the help.  UBUNTU RULES and so does the community.

---

### Post by dbott67 on 2006-12-24
Glad it's working.

What fixed it?  The OpenDNS server hack?

If so, what is the make & model of your router?  Some routers appear to be affected; others (like my D-Link DI-614+) appear to work fine.

-Dave

---

### Post by wingsfan on 2006-12-24
It was the openDNS hack that fixed the problem.  My router is an off brand.  It is a blitzz the model is BWA 711.  

I do have another problem trying to use samba to get on my wife's windows machine but I will try and play with that some more.

---

### Post by dbott67 on 2006-12-24
That's good to know about the router... it seems most people that experience the problem are using off-brands.

As for samba, I've written up a HOWTO below.  It may get you started.
[http://www.ubuntuforums.org/showthread.php?t=280473](http://www.ubuntuforums.org/showthread.php?t=280473)

-Dave

---

### Post by wingsfan on 2006-12-25
When I run the first part here is the message I get.  If there is any tips you have for me let me know.


wingsfan@wingsfan-desktop:~$ smbclient -L 192.168.1.2 -U%
Domain=[HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.2 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        LISA                 

        Workgroup            Master
        ---------            -------
        HOME                 LISA
        MSHOME               WINGSFAN-DESKTO

---

### Post by dbott67 on 2006-12-25
The 192.168.1.2 address in my HOWTO is the IP address of my NAS device, which may be different from the IP addresses on your network.

Your router is assigning addresses 192.168.1.xxx --- you just need to find out what the xxx is for each computer.

In Windows, click **START > RUN** and then type **cmd**.  In the command prompt type:
```
ipconfig /all
```
This will reveal the IP of the Windows computer.  Once you've got the IP, substitute it for the **192.168.1.2** I used in my example.

Another good command is:
```
dbott@thedrake:~$ **smbtree**
Password:
WORKGROUP
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\PIII-600
        \\OMEGA-XP
        \\NAS-160GB
                \\NAS-160GB\IPC$
                \\NAS-160GB\Videos
                \\NAS-160GB\Music
                \\NAS-160GB\Archive
                \\NAS-160GB\Data
                \\NAS-160GB\PUBLIC

```

Also, make sure that it's not running any sort of software firewall (the built-in XP one or Norton, etc.)

-Dave

---

### Post by wingsfan on 2006-12-26
I double checked the ip and it was correct that is the error message that I got.  I am pretty sure it was working before we did the open DNS hack.  I guess I am kinda stumck again.  I have been playing at it most of today with no result.

---

### Post by dbott67 on 2006-12-27
You can temporarily check to see if the DNS hack has caused the problem by changing the /etc/resolv.conf file to this:
```
#nameserver 208.67.222.222
# nameserver 208.67.220.220
nameserver 192.168.1.1
```
If this fixes it, then try with all 3 name servers:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.1.1
```
If it still works, put the line in red back in the dhclient.conf file:
```
**[COLOR="Blue"]prepend domain-name-servers 208.67.222.222, 208.67.220.220;[/COLOR]**
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, **[COLOR="Red"]domain-name-servers,[/COLOR]** host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
```

If you're still having problems these threads may help:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://www.ubuntuforums.org/showthread.php?p=1174825&highlight=samba+windows+xp+howto#post1174825](http://www.ubuntuforums.org/showthread.php?p=1174825&highlight=samba+windows+xp+howto#post1174825)

---

### Post by venik212 on 2006-12-28
The help provided here is awsome.  
However, I have EXACTLY the same problem of iffy internet performance, but I am at a university, using their routers etc.  I have done the ipv6 disabling thing, and it improved things, so that now things sortof work occasionally, but only about half the time, and I see no pattern here.
Typically, the browser will say: Looking up soandso, then, after a few secons, it will say: connecting to soandso, and then, SOMETIMES, will actually connect.
The same behavior is seen when I send out mail with Thunderbird.  It receives mail just fine, but sends out (or not) randomly.
If I boot the same machine in XP it works just fine.  I am using a Dell Dimension 4300 with a 3com 3c905b NIC card.  I suspected the driver, but could not find a Linux 3c905b-tx driver.  Incidentally, the search for drivers reminds me a lot of the days when IBM left us OS/2 users to look for drivers on our own, which was one of the (many) nails in OS/2's coffin.

---

### Post by venik212 on 2006-12-28
I have now gone through the modifications suggested by Dan in the posts above, and things have gotten worse.  After I rebooted, I cannot even get to Google, let alone the Ubuntu forums.  I am writing this from XP... ;-(
Without a decent, reliable Internet connection, Ubuntu's advantages all melt (for me at least).
Can someone tell me what I need to do to get from UBUNTU the same fast and reliable internet connection I get when I boot the same hardware from XP?
Thanks,

---

### Post by dbott67 on 2006-12-28
I assume you Dave, not Dan (no sense blaming poor Dan for all your troubles!)  :)

How are you connected to the university network?  Are you behind your own NAT router or directly connected via ethernet cable to one of their network jacks?

You'll need to copy & paste the output to floppy/usb and then paste it here from XP, if you still can't connect in Ubuntu.

```
cat /etc/network/interfaces
```
```
ifconfig -a
```
```
route -n
```
```
cat /etc/resolv.conf
```

If you made any modifications to your dhclient.conf file, you can restore the original by typing the following command to backup your borked file:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.conf.borked
```

And then typing this command to restore the original:
```
sudo cp /etc/dhcp3/dhclient.bak /etc/dhcp3/dhclient.conf
```

Reboot and let me know what happens.


-Dave

---

### Post by venik212 on 2006-12-28
Sorry, Dave (and Dan).
Here are the responses, pasted in XP since as I was doing it on Ubuntu, the internet connection became unusable again...I did make changes to the dclient.conf, but undid them using the text editor, and then rebooted before I used the commands you have suggested.

udi@udi-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

udi@udi-desktop:~$ 
udi@udi-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:50:04:24:35:59  
          inet addr:146.203.21.92  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:23 txqueuelen:1000 
          RX bytes:1984028 (1.8 MiB)  TX bytes:265246 (259.0 KiB)
          Interrupt:193 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:760 (760.0 b)  TX bytes:760 (760.0 b)

udi@udi-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
146.203.21.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         146.203.21.1    0.0.0.0         UG    0      0        0 eth0
udi@udi-desktop:~$ cat /etc/resolv.conf
search mssm.edu
nameserver 146.203.1.10
nameserver 146.203.1.9
udi@udi-desktop:~$

---

### Post by dbott67 on 2006-12-28
According to your ifconfig output, your eth0 interface is:
IP: 146.203.21.92
Mask: 255.255.255.0

route -n shows your gateway to be:
GW: 146.203.21.1

And your nameservers are:
146.203.1.10
146.203.1.9

All of this is obtained via DHCP (and it all looks pretty reasonable to me).

The next step is to try to isolate where the issue lies:

1. between you and the university's router/firewall
2. outside the router/firewall

Can you try pinging the following IP addresses and post the output:
- 146.203.21.92 (your IP)
- 146.203.21.1 (your default gateway)
- 146.203.1.10 (university DNS #1)
- 72.14.205.147 ([www.google.com](www.google.com))

If you get results, you have connectivity, but you may be having issues with name resolution.

Next, try pinging by Fully Qualified Domain Name (FQDN):
- [www.mssm.edu](www.mssm.edu) (or some other resources at the school, fusion.mssm.edu, etc.)
- [www.ubunutforums.org](www.ubunutforums.org)
- [www.google.com](www.google.com)

And post the output here.

Thanks,
Dave

---

### Post by venik212 on 2006-12-28
Here it is.  It looks like I am having trouble reaching the default gateway and the University DNS #1.

-----------------------
udi@udi-desktop:~$ ping -c 5 146.203.21.92
PING 146.203.21.92 (146.203.21.92) 56(84) bytes of data.
64 bytes from 146.203.21.92: icmp_seq=1 ttl=64 time=0.057 ms
64 bytes from 146.203.21.92: icmp_seq=2 ttl=64 time=0.052 ms
64 bytes from 146.203.21.92: icmp_seq=3 ttl=64 time=0.047 ms
64 bytes from 146.203.21.92: icmp_seq=4 ttl=64 time=0.051 ms
64 bytes from 146.203.21.92: icmp_seq=5 ttl=64 time=0.058 ms

--- 146.203.21.92 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.047/0.053/0.058/0.004 ms
udi@udi-desktop:~$ ping -c 5 146.203.21.1
PING 146.203.21.1 (146.203.21.1) 56(84) bytes of data.

--- 146.203.21.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4009ms

udi@udi-desktop:~$ ping -c 5 146.203.1.10
PING 146.203.1.10 (146.203.1.10) 56(84) bytes of data.

--- 146.203.1.10 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4010ms

udi@udi-desktop:~$ ping -c 5 72.14.205.147
PING 72.14.205.147 (72.14.205.147) 56(84) bytes of data.

--- 72.14.205.147 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4011ms

udi@udi-desktop:~$ ping -c 5 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (216.239.37.104) 56(84) bytes of data.

--- [www.l.google.com](www.l.google.com) ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4010ms

udi@udi-desktop:~$ ping -c 5 [www.mssm.edu](www.mssm.edu)
PING [www.mssm.edu](www.mssm.edu) (146.203.9.55) 56(84) bytes of data.
64 bytes from [www.mssm.edu](www.mssm.edu) (146.203.9.55): icmp_seq=1 ttl=62 time=0.744 ms
64 bytes from [www.mssm.edu](www.mssm.edu) (146.203.9.55): icmp_seq=2 ttl=62 time=0.447 ms
64 bytes from [www.mssm.edu](www.mssm.edu) (146.203.9.55): icmp_seq=3 ttl=62 time=0.522 ms
64 bytes from [www.mssm.edu](www.mssm.edu) (146.203.9.55): icmp_seq=4 ttl=62 time=0.454 ms
64 bytes from [www.mssm.edu](www.mssm.edu) (146.203.9.55): icmp_seq=5 ttl=62 time=2.53 ms

--- [www.mssm.edu](www.mssm.edu) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 0.447/0.940/2.535/0.805 ms
udi@udi-desktop:~$

---

### Post by dbott67 on 2006-12-28
Routers, firewalls and servers can be programmed to drop ICMP ping requests, so the fact that they do not reply is not conclusive proof that they're not working.  Most home NAT/Routers are programmed to drop external pings.

The fact that you can ping beyond the GW to the [www.mssm.edu](www.mssm.edu) website shows that you have some connectivity.  **Are you able access the school website in firefox?**

The other thing that just occured to me is the use of a proxy server.  Does Mount Sinai use proxy servers?  On your Windows XP machine, check **Internet Explorer > Tools > Internet Options > Connections > LAN Settings.**

Look under Proxy Servers for any settings and then duplicate them in Ubuntu: **SYSTEM > PREFERENCES > NETWORK PROXY**

Let me know if this is the case.

-Dave

---

### Post by venik212 on 2006-12-28
I find nothing in the lan settings of IE-- all the boxes are empty there.  I believe I can access the MSSM.edu site from Firefox, but I am out of the office for an hour, so I cannot check it directly.  I get email just fine, but sending email is very dicey-- sometimes it works fine and other times it fails.
The impression that I get is that after rebooting all is fine, but after I get to the internet once, things become very iffy.
I shall try to find out about proxies, but since New Year's Eve is looming, TI types tend to evaporate around here.

---

### Post by venik212 on 2006-12-28
I have no trouble connecting to the MSSM site from Firefox using Ubuntu.

---

### Post by dbott67 on 2006-12-28
The part that puzzles me is that you are not able to ping by IP address (which you should be able to do).  The other thing is that Windows XP works fine on the same network.

Can you post the following output from your Windows computer:
```
ipconfig /all
```
```
route print
```
Also, can you post the output of the pings from the previous page:

- 146.203.21.xx (your Windows XP IP)
- 146.203.21.1 (your default gateway --- if the same as in Ubuntu)
- 146.203.1.10 (university DNS #1)
- 72.14.205.147 ([www.google.com](www.google.com))

Next, try pinging by Fully Qualified Domain Name (FQDN):
- [www.mssm.edu](www.mssm.edu) (or some other resources at the school, fusion.mssm.edu, etc.)
- [www.ubunutforums.org](www.ubunutforums.org)
- [www.google.com](www.google.com)

Please post the output here.


-Dave

PS - You can try manually adding the OpenDNS servers to the top of your **/etc/resolv.conf** file and leave your current ones alone (the next reboot should overwrite the file):

```
sudo gedit /etc/resolv.conf
```
```
[B][COLOR="Red"]nameserver 208.67.222.222
nameserver 208.67.220.220[/COLOR][/B]
search mssm.edu
nameserver 146.203.1.10
nameserver 146.203.1.9
```

Then try pinging / surfing, etc.

---

### Post by venik212 on 2006-12-28
Below are the results.  I also found that I can "revive" the connection by issuing a restart networking command from the terminal (following your example someplace else).  The revival seems temporary, though.  Adding the OpenDNS nameservers did not help.
.
-------------------------
Windows IP Configuration



        Host Name . . . . . . . . . . . . : V3

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No

        DNS Suffix Search List. . . . . . : mssm.edu



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : mssm.edu

        Description . . . . . . . . . . . : 3Com EtherLink XL 10/100 PCI TX NIC (3C905B-TX)

        Physical Address. . . . . . . . . : 00-50-04-24-35-59

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 146.203.21.152

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 146.203.21.1

        DHCP Server . . . . . . . . . . . : 146.203.127.50

        DNS Servers . . . . . . . . . . . : 146.203.1.10

                                            146.203.1.9

        Lease Obtained. . . . . . . . . . : Thursday, December 28, 2006 5:19:11 PM

        Lease Expires . . . . . . . . . . : Thursday, December 28, 2006 6:19:11 PM


===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 50 04 24 35 59 ...... 3Com EtherLink XL 10/100 PCI TX NIC (3C905B-TX) - Packet Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0     146.203.21.1  146.203.21.152	  20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1	  1
     146.203.21.0    255.255.255.0   146.203.21.152  146.203.21.152	  20
   146.203.21.152  255.255.255.255        127.0.0.1       127.0.0.1	  20
  146.203.255.255  255.255.255.255   146.203.21.152  146.203.21.152	  20
        224.0.0.0        240.0.0.0   146.203.21.152  146.203.21.152	  20
  255.255.255.255  255.255.255.255   146.203.21.152  146.203.21.152	  1
Default Gateway:      146.203.21.1
===========================================================================
Persistent Routes:
  None



Pinging 146.203.21.152 with 32 bytes of data:



Reply from 146.203.21.152: bytes=32 time<1ms TTL=128

Reply from 146.203.21.152: bytes=32 time<1ms TTL=128

Reply from 146.203.21.152: bytes=32 time<1ms TTL=128

Reply from 146.203.21.152: bytes=32 time<1ms TTL=128

Reply from 146.203.21.152: bytes=32 time<1ms TTL=128



Ping statistics for 146.203.21.152:

    Packets: Sent = 5, Received = 5, Lost = 0 (0% loss),

Approximate round trip times in milli-seconds:

    Minimum = 0ms, Maximum = 0ms, Average = 0ms




Pinging 146.203.21.1 with 32 bytes of data:



Request timed out.

Request timed out.

Request timed out.

Request timed out.

Request timed out.



Ping statistics for 146.203.21.1:

    Packets: Sent = 5, Received = 0, Lost = 5 (100%  loss),




Pinging 72.14.205.147 with 32 bytes of data:



Request timed out.

Request timed out.

Request timed out.

Request timed out.

Request timed out.



Ping statistics for 72.14.205.147:

    Packets: Sent = 5, Received = 0, Lost = 5 (100% loss),




Pinging [www.l.google.com](www.l.google.com) [216.239.37.104] with 32 bytes of data:



Request timed out.

Request timed out.

Request timed out.

Request timed out.

Request timed out.



Ping statistics for 216.239.37.104:

    Packets: Sent = 5, Received = 0, Lost = 5 (100% loss),



Pinging [www.ubuntuforms.org](www.ubuntuforms.org) [64.20.33.115] with 32 bytes of data:



Request timed out.

Request timed out.

Request timed out.

Request timed out.

Request timed out.



Ping statistics for 64.20.33.115:

    Packets: Sent = 5, Received = 0, Lost = 5 (100% loss),

------------------------------------------

---

### Post by venik212 on 2006-12-28
I neglected to mention that despite all the "lost data" in the XP experiment, I had no trouble connecting to Google, MSSM, etc.

---

### Post by venik212 on 2006-12-28
I am told that MSSM does not use proxy servers.

---

### Post by M8M on 2006-12-29
Hi Dave,

We're in Welland, not that far away!

We are having a similar problem on our other computer (no internet access). We tried following all the steps you've listed and when we got up the the steps in message #16 we got the following error:

cp: cannot stat " /etc/dhcp3/dhclient.bak": No such file or directory

We had internet last night, then my husband tried adding a plug in for Firefox and it totally messed up. In his frustration he chose to reinstall edubuntu, b/c I had gone to bed and he thinks that's the answer to all problems...

We tried what we did yesterday to get internet and it didn't work this time. Then we tried your instructions here and ran into the above error. Any siggestions?

Thanks,
M8M

---

### Post by venik212 on 2006-12-29
Just curious-- which plugin for FF killed the Internet?  My connection is very temramental, and I wonder whether it was really the plugin that did it, or it was just a coincidence.  That is how religions are started, you know...

---

### Post by dbott67 on 2006-12-29
> **M8M said:**
> Hi Dave,

We're in Welland, not that far away!

We are having a similar problem on our other computer (no internet access). We tried following all the steps you've listed and when we got up the the steps in message #16 we got the following error:

cp: cannot stat " /etc/dhcp3/dhclient.bak": No such file or directory

We had internet last night, then my husband tried adding a plug in for Firefox and it totally messed up. In his frustration he chose to reinstall edubuntu, b/c I had gone to bed and he thinks that's the answer to all problems...

We tried what we did yesterday to get internet and it didn't work this time. Then we tried your instructions here and ran into the above error. Any siggestions?

Thanks,
M8M


Not that far away at all.  I taught at Niagara College Welland Campus in the computer networking program for about 5 years, as well as looked after the network for an accounting firm (plus many of my relatives still live there).

The error message is just stating that the file (in this case dhclient.bak) does not exist.

So, to backup the existing file, you would type:
```
sudo cp /etc/dhcp3/dhclient.conf /etc/dhcp3/dhclient.bak
```

Then, if things went awry and you needed to restore it, you would type:
```
sudo cp /etc/dhcp3/dhclient.bak /etc/dhcp3/dhclient.conf
```

-Dave

---

### Post by venik212 on 2006-12-29
Hi Dave,
Just above M8m's post are some voluminous reports from the various items you were asking about.  
I am still in a state of frustration, since the *only* way I can be sure that I have interent access is to RESTART the network each time I need to send email, or make sure a web page will open.  XP does not look so bad all of a sudden....
If you have any insights, please let me know.  My best guess is that it is a driver issue, but perhaps I need to downgrade to Dapper from 6.10?  I have compared my network settings (dynamic IP address, automatic everything) with someone else in the school, and the settings are the same, but he has not trouble at all (of course his hardware and driver are different).
Thanks, and have a Happy New Year!

---

### Post by dbott67 on 2006-12-29
> **venik212 said:**
> Hi Dave,
Just above M8m's post are some voluminous reports from the various items you were asking about.  
I am still in a state of frustration, since the *only* way I can be sure that I have interent access is to RESTART the network each time I need to send email, or make sure a web page will open.  XP does not look so bad all of a sudden....
If you have any insights, please let me know.  My best guess is that it is a driver issue, but perhaps I need to downgrade to Dapper from 6.10?  I have compared my network settings (dynamic IP address, automatic everything) with someone else in the school, and the settings are the same, but he has not trouble at all (of course his hardware and driver are different).
Thanks, and have a Happy New Year!

Thanks... I did get a chance to look at them and the XP results are consistent with Ubuntu.  A few things you may try before downgrading:

1. Something just occurred to me about a similar problem that happened to some folks a few months ago that had somewhat similar problems.  Can you post the output of the following command:
```
dbott@thedrake:~$ **cat /etc/apt/apt.conf**
APT::Authentication::TrustCDROM "true";
[COLOR="Red"]Acquire::http::Proxy "false";[/COLOR]
```
That last line in red was causing no end of grief for some people --- it seems as though the computer was trying to look for a proxy named "false" (as opposed to not using one).  Anyhow, the fix was simply commenting out the line:
```
dbott@thedrake:~$ **sudo gedit /etc/apt/apt.conf**
APT::Authentication::TrustCDROM "true";
[COLOR="Red"][COLOR="Blue"]# [/COLOR]Acquire::http::Proxy "false";[/COLOR]
```
If this doesn't work/help, then try the next steps.

2. Boot the 6.06 Live CD and see how it performs (compare drivers using **sudo lshw -C network**):
```
dbott@thedrake:~$ sudo lshw -C network
Password:
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes [COLOR="Red"]**driver=8139too driverversion=0.9.27**[/COLOR] duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185

```

If the Live CD stays online, then you may be right about the driver issue (and you'll probably have to downgrade).

3. See if you can scrounge an inexpensive (or free) NIC from an old computer and swap out the existing one. If it still acts goofy, it may be one of those "It's not us, it's them" issues and you'll have to resort to XP for the time-being.

Anyhow, I'm off to Mexico early Sunday morning with my wife for a little R&R, so if you don't hear from me for a while, don't panic.  Hopefully, this will do the trick (crossing fingers now).

Have a great New Year, as well.  Say "Hi" to my sister... she's a nurse at NYU! ;) 

-Dave

---

### Post by venik212 on 2006-12-30
Thanks.  My setup must be different from yours-- I could not find a file named apt.conf anywhere on the system.  Also, in order to respond to your post, I had to (again) restart networking.  Something in there needs to be reset after I use the internet for a short time.  I shall try the LiveCD with 6.06 or rummage for another NIC after recovering from the New Year's hangover, which I intend to use to wipe out my frustration with Linux...
Enjoy Mexico-- wish I was there!
EK

---

### Post by M8M on 2006-12-30
We ended up reinstalling edubuntu but selecting a different network card. After that it worked seemlessly. We´ve played around with both computers so much, we can´t remember what pluggings we´ve used or not and what problems we had after each one. We´ve reinstalled everything on both computers more than once, we´re starting to get the hang of it! LOL (Not that we want to keep doing that, but you know what I mean....)

M8M

---

### Post by Anakist on 2006-12-30
The OpenDNS hack worked for me too. I have a DSL-G604T.

Thanks!

James

---

### Post by venik212 on 2007-01-02
Breaking news-- I changed the NIC from the 3COM905B to an Intel NIC, and now Ubuntu has a fine (and reliable) internet connection.  Just to even the score, XP (on the same machine) has trouble finding the driver for this Intel NIC.  This is called "conservation of trouble" in physics.

---

### Post by Tintinnabulation on 2007-02-12
Eureka!

The open DNS alteration worked a treat!
My router is also the DSL G604T.

The fix resolved the following problems:
Add/remove didn't work
Synaptic didn't work
Gaim was not working
Basically before Firefox was the only Internet app working - after i had disabled ipv6 (using about:config) to get it up and running. 

Mucho Gracious!  :)

---

### Post by mips on 2007-02-12
> **Tintinnabulation said:**
> 
My router is also the DSL G604T.


Upgrading the firmware to v2+ on those routers could also solve the problem at times.

---

