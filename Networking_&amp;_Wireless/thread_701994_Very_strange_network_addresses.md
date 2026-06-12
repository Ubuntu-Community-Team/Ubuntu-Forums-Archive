---
title: "Very strange network addresses?"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by windyweather on 2008-02-19
I'm new to Ubuntu but have been using SUSE for a while.
Ubuntu 7.10 is running fine on my system. Network to the internet is fine.
I'm behind a router on the normal local network of 192.168.1.x and ubuntu is configured with DHCP.

I'm trying to set up SAMBA with the other Windows systems on my net and it wouldn't work. So I took at look - learned how to use gksudo - at the samba.conf file and it was cool. Somewhere along the way I ran a program that filled in my put my work group - 
System>> Administration >> Shared Folders.
Apparently this program - whatever it is - has set the Workgroup and created a share properly in the samba.conf file.

Still no joy in connecting with other systems.
The windows boxes can see the linux box, and the linux box can see the windows boxes under System >> Network. but not the contents.

Along the way I tried a PING and got a very strange address...

```
darrell@squall-ubuntu:/etc$ ping typhoon
PING typhoon (64.158.56.56) 56(84) bytes of data.

```

Since my network is 192.168.1.x it is no wonder that this won't work.

Anybody seen this before? Any idea about how this could happen?

Thanks,

Windy

---

### Post by jhetrick62 on 2008-02-19
Can you ping your router?  If you can see your windows box, you have to be on the network in some capacity.  What is the output of ifconfig?

Samba can be easily set up through the smb.conf file.  I don't use the gui setups myself, so they may work, but I can only do it manually.

Jeff

---

### Post by Iowan on 2008-02-19
"Something" seems to think **typhoon** is an external machine. Depending on resolution set in **/etc/resolv.conf**, it could be in the **/etc/hosts** file, the router, or another nameserver.> The windows boxes can see the linux box, and the linux box can see the windows boxes under System >> Network. but not the contents. I have better luck with the "Connect to Server"option, but sometimes it takes a couple of tries - sometimes I change the domain to my workgroup, sometimes I leave it alone (still haven't got that completely figured out).

---

### Post by windyweather on 2008-02-19
Yes, pinging the router or another other machine by IP address works just fine.

Here's the hosts file: No changes made by me.
```
darrell@squall-ubuntu:/etc/samba$ more /etc/hosts
127.0.0.1       localhost
127.0.1.1       squall-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
darrell@squall-ubuntu:/etc/samba$ 
```

Presumably ubuntu ships with working hosts and resolve.conf files...

And like I said, I can reach the internet beyond the router with no problem. This post was made from the ubuntu system.

Any more ideas??
Thanks
- windy

---

### Post by jhetrick62 on 2008-02-19
Post your /etc/samba/smb.conf file here.

Jeff

---

### Post by Iowan on 2008-02-19
> **windyweather said:**
> Any more ideas??
Thanks
- windyDoes the "Connect to Server"option give any different results?

---

### Post by i_m_bobo on 2008-02-19
I'm having the exact same problem - I can see my local network boxes in the network browser, and they show up fine in **smbclient -L localhost -U%** . The network browser also lets me see my Windows shares, if I key in the IP address instead of double-clicking the icon. And i get the same weird name resolution if I try to ping, and it's a different one every time.

I've spent hours poring over [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/) (which was very helpful getting my printers working with the Windows boxes), but no joy in getting Samba to pass the local network IP addresses to the rest of the system.

IOW, ME TOOOO!](*,)

---

### Post by i_m_bobo on 2008-02-19
root@BoboII:/etc/samba# testparm -s smb.conf
Load smb config files from smb.conf
Processing section "[homes]"
Processing section "[printers]"
WARNING: The "printer admin" option is deprecated
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = HERRICK
        server string = Samba server on %h
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        printcap name = cups
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 

[homes]
        comment = Home Directories
        valid users = %S
        browseable = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        printer admin = root, @herrick
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

---

### Post by jhetrick62 on 2008-02-19
Okay, I see two issues and a strong recommendation.

First the only share that you have listed is your homes directory and that is not browseable so it will not list out as an available share when browsing on windows.  Second, you have no other share listed to use so none are being seen.

I really am not fond of that configuration file  if I were doing it as it lacks some things that I like to use like netbios naming and it has a couple of complex things in it also.  I learned a long time ago to make samba as utterly simple as possible to start, get it working, then add complexities in one at a time so that you know how it effects everything.  

Take a look at this thread as it gives a very good starting point for a smb.conf file.  You can copy your current file and name it like smb.conf.archive for now and load this file, modify it slightly as directed, restart smb services and it should work.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+howto)

Don't do the PDC stuff and only add one share to test and see if that works.


Goodluck,
Jeff

---

### Post by i_m_bobo on 2008-02-19
Everything on the server is being seen just fine by the Win clients. When I had browsing enabled in [homes] I was seeing 2 copies of the server shares from the clients. One named *bobo*, the other named *homes* (*wife* and *homes* on her machine, *kid* and *homes* on hers).

Thanks for the link. I'll have a look. But my problem is outgoing, from ubuntu to the Win boxes.

---

### Post by jhetrick62 on 2008-02-19
Did you use the "connect to server" option in Ubuntu?  The Samba file should have  very little to do with outgoing connections.  It's primarily used to control the incoming connections.

I do use the netbios server feature as it then helps to control the network domain and I make it the master browser.  I also make sure that all windows boxes have the same workgroup name as the sambe server.

Jeff

---

### Post by i_m_bobo on 2008-02-20
Everybody is in the right workgroup, everyone can get to their own home directory on the server, everybody can print through the server. Yes my, smb.conf is a bit clunky - I started from the built-in, ran all over the web trying to solve the newbie printer issues, and the duplicate presentation of the samba shares under the alias "homes".

I'm trying to make the network as "peer-to-peer" as I can, so I haven't enabled netBios. I tried it over the weekend, but I don't recall which problem it didn't help with, so it's worth another shot.

Thanks for the help.

---

### Post by windyweather on 2008-02-20
Here is my samba.conf file.


```
darrell@squall-ubuntu:/etc/samba$ testparm -s smb.conf
Load smb config files from smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[darrell]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = WINDYWEATHER
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        wins server = ALIENSTORM
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[darrell]
        path = /home/darrell
        guest ok = Yes
darrell@squall-ubuntu:/etc/samba$ 

```

Do we think that the bad network addresses are somehow due to SAMBA or something else?

I'm not clear on where the "Connect to Server" option is or how to change it.

Thanks, 
- Windy

---

### Post by Iowan on 2008-02-20
I presume you have a server named **ALIENSTORM** on your network acting as WINS server?  You might check it so see if it has linked **typhoon** with that address. Windows machine is also in workgroup **WINDYWEATHER**?

Connect to Server option is under Places>Connect to Server - try it instead of Places>Network.
Might see if adding the line **   browseable = yes** to the [darrell] share helps.

---

### Post by windyweather on 2008-02-20
> **Iowan said:**
> I presume you have a server named **ALIENSTORM** on your network acting as WINS server?  You might check it so see if it has linked **typhoon** with that address. Windows machine is also in workgroup **WINDYWEATHER**?

Connect to Server option is under Places>Connect to Server - try it instead of Places>Network.
Might see if adding the line **   browseable = yes** to the [darrell] share helps.

There is a windows machine on the network called ALIENSTORM. I confess I do not know if it is a WINS server. It is a Vista x64 system. Is there a way to set it to be a WINS server? It certainly is serving some shares on the net.

Pings between the windows machines, ALIENSTORM and TYPHOON, etc., get the correct addresses.

I'll give those other two things a try.
Thanks,
windy

---

### Post by i_m_bobo on 2008-02-20
Windyweather,

Someone on another thread mentioned smbtree. I got this when I ran it.
```
bill@BoboII:~$ smbtree
Password: 
session request to 192.168.42.23 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
session request to 192.168.42.23 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
HERRICK
session request to 192.168.42.23 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
        \\BOBOII                        Samba server on BoboII
timeout connecting to 66.150.2.134:445
timeout connecting to 66.150.2.134:139
Error connecting to 66.150.2.134 (Operation already in progress)
cli_start_connection: failed to connect to BOBOII<20> (66.150.2.134). Error NT_STATUS_ACCESS_DENIED
        \\BOBO                          Little guy
timeout connecting to 66.150.2.134:445
timeout connecting to 66.150.2.134:139
Error connecting to 66.150.2.134 (Operation already in progress)
cli_start_connection: failed to connect to BOBO<20> (66.150.2.134). Error NT_STATUS_ACCESS_DENIED[/PHP]

```
The first address is good, but for some reason the call to it failed. Then when it tried to resolve BOBO and BOBOII by name it got stupid addresses. Is yours the same?

---

### Post by windyweather on 2008-02-20
Here's my smbtree output:

```
darrell@squall-ubuntu:/etc/samba$ smbtree
Password: 
WINDYWEATHER
        \\TYPHOON        
                \\TYPHOON\DVD_RW_Drive   
                \\TYPHOON\C$                    Default share
                \\TYPHOON\H$                    Default share
                \\TYPHOON\ADMIN$                Remote Admin
                \\TYPHOON\Video2         
                \\TYPHOON\C_Drive        
                \\TYPHOON\hpphotos              hp photosmart 7550 series
                \\TYPHOON\EPSONR200             EPSON  R200
                \\TYPHOON\DVD_ROM_Drive  
                \\TYPHOON\print$                Printer Drivers
                \\TYPHOON\IPC$                  Remote IPC
                \\TYPHOON\Public         
        \\SQUALL-UBUNTU                 squall-ubuntu server (Samba, Ubuntu)
                \\SQUALL-UBUNTU\IPC$            IPC Service (squall-ubuntu server (Samba, Ubuntu))
                \\SQUALL-UBUNTU\darrell        
                \\SQUALL-UBUNTU\print$          Printer Drivers
        \\BREEZE-XP                     Win XP Development
                \\BREEZE-XP\Printer             Quicken PDF Printer
                \\BREEZE-XP\C$                  Default share
                \\BREEZE-XP\PRESARIO (C)   
                \\BREEZE-XP\ADMIN$              Remote Admin
                \\BREEZE-XP\SharedDocs     
                \\BREEZE-XP\print$              Printer Drivers
                \\BREEZE-XP\D$                  Default share
                \\BREEZE-XP\IPC$                Remote IPC
        \\ALIENSTORM     
                \\ALIENSTORM\SD_CardSlot    
                \\ALIENSTORM\QVCS           
                \\ALIENSTORM\IPC$               Remote IPC
                \\ALIENSTORM\D_Drive        
                \\ALIENSTORM\D$                 Default share
                \\ALIENSTORM\C_Drive        
                \\ALIENSTORM\C$                 Default share
                \\ALIENSTORM\ADMIN$             Remote Admin
darrell@squall-ubuntu:/etc/samba$ 

```

Looks pretty good to me.

Connect to server ALIENSTORM user darrell share C_Drive fails with "The folder contents could not be displayed". Same thing when I try to browse it. Same thing with TYPHOON.
No prompts show up for passwords.

- Windy

---

### Post by i_m_bobo on 2008-02-20
Yours looks good to me too. Mine not so much :-(

---

### Post by windyweather on 2008-02-20
Looks like my linksys wrt54g router is not sending back the addresses for local machines. The windows systems know each other by name. But Linux is out of the loop - so to speak.

```
darrell@squall-ubuntu:/etc/samba$ tracepath typhoon
 1:  squall-ubuntu.local (192.168.1.104)                    0.162ms pmtu 1500
 1:  192.168.1.1 (192.168.1.1)                              1.530ms 
 2:  10.213.64.1 (10.213.64.1)                              9.103ms 
 3:  68-116-79-201.or.charter.com (68.116.79.201)          17.043ms 
 4:  g1-0.er01.mdfd.or.charter.com (68.116.79.1)           17.828ms 
 5:  svl-edge-09.inet.qwest.net (65.113.33.109)           asymm  6  33.920ms 
 6:  svl-core-02.inet.qwest.net (205.171.14.97)           asymm  7  25.424ms 
 7:  snj-core-02.inet.qwest.net (67.14.32.10)             asymm  8  27.475ms 
 8:  sjp-brdr-02.inet.qwest.net (205.171.214.46)           26.302ms 
 9:  Te-9-3.car4.SanJose1.Level3.net (4.68.111.173)        25.313ms 
10:  vlan89.csw3.SanJose1.Level3.net (4.68.18.190)         31.436ms 
11:  ae-84-84.ebr4.SanJose1.Level3.net (4.69.134.249)      42.335ms 
12:  ae-2.ebr4.NewYork1.Level3.net (4.69.135.186)         asymm 11 109.052ms 
13:  ae-3.ebr4.Washington1.Level3.net (4.69.132.93)       asymm 11  97.878ms 
14:  ae-84-84.csw3.Washington1.Level3.net (4.69.134.186)  asymm 10 108.992ms 
15:  ae-31-89.car1.Washington1.Level3.net (4.68.17.131)   asymm 10 149.627ms 
16:  CO-LOCATION.car1.Washington1.Level3.net (63.210.59.250) asymm 12 106.250ms 
17:  unknown.level3.net (64.158.56.34)                    asymm 12  99.954ms reached
     Resume: pmtu 1500 hops 17 back 12 
darrell@squall-ubuntu:/etc/samba$ 

```

Something I missed?? I'd rather not just edit these addresses into the hosts file since they are DHCP addresses and might change if I boot systems in a different order some day.

So looks like I have two unrelated problems. Or maybe not so unrelated.
(1) Samba can't connect, even tho smbtree seems very happy with the network.
(2) Linux gets the wrong addresses for hosts on the local network. Somebody seems to be sending requests for these hosts off the local network for resolution.

Thanks,
- windy

---

### Post by i_m_bobo on 2008-02-20
Looks like we have different problems. Do you have the smb client library installed? It's called libgnomevfs2-extra. Nautilus needs it to get IP addresses and stuff from samba. Hope that helps.

As for me, part of the problem with smbtree above is my old W98SE box was acting WINS server. I shut it down and let Ubuntu/Samba take over. Now I get bad results, but fewer lines of it.
```
bill@BoboII:~$ smbtree -U%
HERRICK
        \\GAK                           Gail's laptop
Error connecting to 63.251.179.13 (Connection refused)
cli_start_connection: failed to connect to GAK<20> (63.251.179.13). Error NT_STATUS_CONNECTION_REFUSED
        \\BOBOII                        Samba server on BoboII
Error connecting to 8.15.7.117 (Connection refused)
cli_start_connection: failed to connect to BOBOII<20> (8.15.7.117). Error NT_STATUS_CONNECTION_REFUSED

```

---

### Post by information_entropy on 2008-02-21
I do not see this line in your global config section

```
[global]
...
# What naming service and in what order should we use to resolve host names
# to IP addresses

   name resolve order = lmhosts host wins bcast

 ...

```

I think, your Samba is trying to resoleve by broadcast first.

---

### Post by windyweather on 2008-02-21
> **i_m_bobo said:**
> Looks like we have different problems. Do you have the smb client library installed? It's called libgnomevfs2-extra. Nautilus needs it to get IP addresses and stuff from samba. Hope that helps.


I already have libgnomevfs2-extra installed... so still no joy. Thanks for the pointer tho.

- windy

---

### Post by windyweather on 2008-02-21
> **information_entropy said:**
> I do not see this line in your global config section

```
[global]
...
# What naming service and in what order should we use to resolve host names
# to IP addresses

   name resolve order = lmhosts host wins bcast

 ...

```

I think, your Samba is trying to resoleve by broadcast first.

Ok turned that on, but no change. Not sure how that would help the ping resolving the addresses tho. Is there some samba setting that tells it to let IP know the addresses of LM hosts? My DNS is apparently still going outside to try to resolve local nodes for IP. The DNS addresses are outside - set by DHCP and network manager. 

```
darrell@squall-ubuntu:~$ ping typhoon
PING typhoon (64.158.56.56) 56(84) bytes of data.

--- typhoon ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

darrell@squall-ubuntu:~$ ping alienstorm
PING alienstorm (64.158.56.56) 56(84) bytes of data.

--- alienstorm ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1002ms

darrell@squall-ubuntu:~$ cd /etc/samba
darrell@squall-ubuntu:/etc/samba$ testparm -s smb.conf
Load smb config files from smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[darrell]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = WINDYWEATHER
        server string = %h server (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        name resolve order = lmhosts host wins bcast
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[darrell]
        path = /home/darrell
        guest ok = Yes
darrell@squall-ubuntu:/etc/samba$ 

```

Still no joy in mudville.

Thanks,
- windy

---

### Post by windyweather on 2008-02-21
Here's what one of the Windows DHCP enabled machines looks like on my local network:

```
C:\Windows\system32>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : AlienStorm
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection 2:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller #2
   Physical Address. . . . . . . . . : 00-04-4B-02-9A-49
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::111f:4af:8d9:1370%9(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.100(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, February 16, 2008 6:19:27 PM
   Lease Expires . . . . . . . . . . : Friday, February 22, 2008 6:19:28 AM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 234882123
   DNS Servers . . . . . . . . . . . : 68.116.46.115
                                       68.116.46.70
                                       68.185.34.67
   NetBIOS over Tcpip. . . . . . . . : Enabled
[...] remainder of interfaces are disabled.

```

I note that the DNS servers are outside, which is what the linux box shows too in /etc/resolv.conf. Network manager is automatically creating that file on the linux box. Same addresses.

[LIST]

[*]Do we know from my smb.conf that Samba is using tcp/ip for lanmanager? 
[*]Does NetBIOS over TCPIP : Enabled above mean that windows is using TcpIP?
[*]If so, and the nodes cannot resolve themselves because they are looking outside and getting bogus addresses, then is that the cause of the Samba failure to connect?
[/LIST]

thanks
- windy

---

### Post by Iowan on 2008-02-21
> **windyweather said:**
> There is a windows machine on the network called ALIENSTORM. I confess I do not know if it is a WINS server. It is a Vista x64 system. Is there a way to set it to be a WINS server?According to your smb.conf, it IS the WINS server.
```
 wins server = ALIENSTORM
```Dunno if IT knows it's the Wins server - or how to see if it has bogus network address for **typhoon**.
BTW, **squall-ubuntu** has no browseable shares, either - but should still show up on the radar.

---

### Post by windyweather on 2008-02-21
I've changed smb.conf - still to no joy...

Not clear why testparm does not show this, but here's how it looks, and these edits were made with one of the applications, and not manually.

The WINS line is commented out. I don't know what a WINS server is really, and have not made ALIENSTORM a WINS server, so I've commented that line out. 

The end of the smb.conf file looks like this.

```
[darrell]
path = /home/darrell
available = yes
browsable = yes
public = yes
writable = no

```

testparm - s smb.conf reports this only:

```
[darrell]
        path = /home/darrell
        guest ok = Yes

```

see complete smb.conf attached.

Thanks,
- windy

---

### Post by windyweather on 2008-02-21
In this post: [http://ubuntuforums.org/archive/index.php/t-88206.html](http://ubuntuforums.org/archive/index.php/t-88206.html)

The fellow mentions installing winbind and
changing the configuration of /etc/nsswitch.conf

My nsswitch.conf now looks like this:

```
darrell@squall-ubuntu:/etc$ more nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4 
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

Now my linux box can ping my other windows boxes, either DHCP or static IP...

Still no joy for samba however.

- Windy

---

### Post by i_m_bobo on 2008-02-22
You have to wonder how to get in touch with the people who know how all this stuff plugs together. I've got Samba installed, and smbclient. But between them they can't resolve the names of the computers on my LAN to IP addresses in a usable way.

WINS is apparently running fine on my network. All my machines can ID each other, even my former W98SE server that I'm trying really really hard to decommission. This applies whether my new Ubuntu server has won the WINS election, or some other machine on my LAN has. And all the Windows clients can access the printers and home directories I've set up on my brand shiny new zigahertz zigabyte 64-bit Ububtu server, and that's a good thing. 

But I can't for the life of me convince the WINS functions running on the server to pass IP addresses for the local-network machines in to the rest of the system and it's very very 

FRUSTRATING!!!](*,)](*,)](*,)

YMMV, one can only hope.

---

### Post by information_entropy on 2008-02-22
I think, you have to tell SAMBA it is either a WIN server or a client.
If you want it to be a client then the wins server = w.x.y.z 
line needs an IP address NOT a name

```

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server

   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both

;   wins server = w.x.y.z

```

On my network, which no longer has a running Windows system most of the time,
I have wins support = yes in the three systems most likely to be on
and wins server = 192.168.y.z in the others.

P.S.
 It is a lot harder to figure out what is wrong with a non-working system
than is to set up one that works.
All of the answers are easy just not always obvious.

---

### Post by i_m_bobo on 2008-02-22
Joy at last! I uninstalled everything I could find - samba, samba-common, smbclient, winbind, smbfs. That was to undo whatever damage I might have done thrashing around on this.

Then I made the edit to /etc/nsswitch.conf that windy recorded above
```
hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4 
```
And I commented out some of the shots-in-the-dark I made in /etc/samba/smb.conf, especially ```
# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast
```
Then I rebooted.

Then I reinstalled samba, samba-common, smbclient and winbind, **but not smbfs**.

Then I rebooted again. Then it worked!:guitar: The Places/Network browser sees my network, and now it shows the shares when I double-click. I can type "vncviewer bobo" and I instantly get the password prompt from my old W98SE box. No more strange messages about 5.117.34.8 not accepting calls on port 3900.

---

### Post by rome-NY on 2008-02-22
you are trying to ping a computer named typhoon. You have no computer in your host file with the name typhoon so its going out to the internet and finding one. Put the address of your computer typhoon in the hosts file.

---

### Post by windyweather on 2008-02-22
> **rome-NY said:**
> you are trying to ping a computer named typhoon. You have no computer in your host file with the name typhoon so its going out to the internet and finding one. Put the address of your computer typhoon in the hosts file.

rome,

This problem is solved. typhoon has a static IP address and the rest of the windows boxes have dynamic IP addresses on my local network. I don't want to edit the hosts file but want these guys to find themselves automatically. Esp for the dynamic ones for obvious reasons.

Installing winbind and editing the nsswitch.conf file fixed this problem right up. No editing the hosts file. All the systems find each other for ping.

Looks like info and bobo's fixes may fix samba's problems. I'll give those a try. :)

When in doubt, just keep hammering away at the problem. We may be close...

- windy

---

### Post by windyweather on 2008-02-23
My network now shares files among ubuntu and the windoze boxes.
:guitar:
All systems provide read-only shares. I don't do RW shares as a matter of policy.

The key parts of the solution are:

[LIST=1]
[*]Install winbind.
[*]Adjust the nsswitch.conf file to include wins. I've done wins before DNS reasoning that the searches were made in the order provided. I don't want the external DNS to be searched if the node name is on the local network.
[*]Installing smbfs is apparently ok. My network seems fine with it installed.
[*]I'm using WORKGROUP and not a domain solution.
[*] wins support = no since samba is not a wins server
[*] name resolve order = lmhosts host wins bcast
[*]security = share I was unable to get the windows boxes to connect to the linux box with security = user. After reading the documentation provided with samba I'm still in the dark about how to make security = user work.Some of the windows boxes ask for passwords and then are willing to connect, notably Vista, and some don't ask - a Win XP system that I've configured in some forgotten way. But while the windows boxes asked for the name and password, the connect was always refused by linux.
[/LIST]

I've enclosed the smb.conf file in case anybody has an idea.
Thanks for all your help...

- windy

---

### Post by i_m_bobo on 2008-02-24
Congratulations, windy! I think there are 3 key issues here:

1. The Samba package available through *Add/Remove...* doesn't provide out-of-the-box joy like one would expect. Use /System/Administration/Synaptic Package Manager (that's a GUI menu path, not a posix path) to make sure samba, samba-common, smbclient and winbind are installed. Those are the basics you need to interact with a WINS-based local network. 

2. A key element in getting Linux boxes to see local-area Windows shares, as opposed to querying some machine halfway around the world, is adding "wins" in the "hosts" line of /etc/nsswitch.conf, BEFORE dns! Here for like the 5th time in this thread is how the line should look to support local-area browsing from Ubuntu.```
hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
```

3. The other key element in getting Linux boxes to see local-area Windows shares, as opposed to querying some machine halfway around the world, is having winbind installed.

There's a ton of documentation on the various options you can impose on your mixed Windows / Samba networks. But if you're relying on your router's DHCP service to assign network addresses, like windy and bobo do, you'll need to do 2 & 3 to see the network properly from your Ubuntu boxes. There's a great HOW-TO somewhere in these forums that says this in its first post. I'd provide a link if I could find it again...

It's up to you, windy, but I think this one belongs in the SOLVED category.

---

### Post by windyweather on 2008-02-24
Thanks for the wrapup, i_m_bobo, but not all the items are solved in your wrap up of my summary...

There remains the issue of **security = user** not working. Right now I have 2 ubuntu boxes on my network, but I need to use security = share for them to be available on the net. If I use security=user file sharing does not work. The passwords are requested on the windows machine when connecting to Linux, but continually refused, even after automatically updated to \\nodename\username

Any insights on this issue would be appreciated.

Thanks much,

- windy

---

### Post by i_m_bobo on 2008-02-24
You've set up your users with smbpasswd? They need to have a valid account on your machine, then you need to add them to the samba password database, like so:
```
**root**@BoboII:/home/bobo# smbpasswd -a bobo
New SMB password:
Retype new SMB password:
root@BoboII:/home/bobo# 

```

---

### Post by windyweather on 2008-02-24
And for Ubuntu, it's more like this maybe...

```
darrell@squall-ubuntu:/etc/samba$ sudo smbpasswd -a darrell
[sudo] password for darrell:
New SMB password:
Retype new SMB password:
darrell@squall-ubuntu:/etc/samba$ 
```

Shucks... :)

Looks like that takes care of the last little problem.

Thanks much,

- windy

---

