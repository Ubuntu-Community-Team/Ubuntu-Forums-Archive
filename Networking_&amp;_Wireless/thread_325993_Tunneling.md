---
title: "Tunneling"
date: 2006-12-26
forum: Networking &amp; Wireless
---

### Post by malfist on 2006-12-26
I have a Windows XP computer connected to my home network. Is there any way that I can have atleast command line access to that computer though my Ubuntu PC? (I can adjust the firewall as needed)

---

### Post by kidders on 2006-12-26
Hi there,

I may be wrong (I'm not a Windoze user), but afaik getting command line access is tougher than getting the graphical interface ... at least out of the box. If you enable desktop sharing in XP (or whatever they call remote login), you should be able to plug into it from Ubuntu. I *think* it tends to operate on port 3389 (since you mentioned a firewall).

---

### Post by dbott67 on 2006-12-26
As Kidders posted, Windows XP (Pro) ships with the capability of graphical remote connections via RDP (remote desktop protocol; port 3389).  Ubuntu ships with Terminal Server Client (APPLICATIONS > INTERNET) that can connect graphically to Windows computers that are running RDP.  You can also use VNC if you're not running XP Pro (or you just want to use it).

Outside of that, if you want to connect via command line, certain versions of Windows had the Telnet Server included (but not installed by default).  I wouldn't recommend it anyhow, as it's not secure.

Another alternative is using OpenSSH for Windows (port 22):
[http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/)

-Dave

---

### Post by malfist on 2006-12-27
It's just the home edition, I'll try the OpenSSH first. Is there a way to get it to listen on a port and require a password for commandline access though that port?

---

### Post by kidders on 2006-12-27
SSH servers tend to like to use port 22 (as mentioned by dbott67). I doubt there's a way to suppress authentication terribly easily, so the answer is "Yes" and "Yes". :-)

---

### Post by dbott67 on 2006-12-27
According to the documentation in OpenSSH for Windows, you can edit the **C:\Program Files\openssh\etc\sshd_config file** (using WordPad) and change the port from 22 to whatever you desire.

By default, you will need to configure the user accounts (it uses the local user accounts from your XP computer):
```
mkgroup -l >> ..\etc\group
```
```
mkpasswd -l -u <xp-username> >> ..\etc\passwd
```
replace <xp-username> with the username you use to login to Windows XP.

-Dave

---

### Post by malfist on 2006-12-27
How do I connect to it now that I have the OpenSSH running on it.

---

### Post by dbott67 on 2006-12-27
From the command line in Ubuntu you can type:
```
ssh ip.address.of.xp
```
or you can use the graphical program called PuTTY:
```
sudo apt-get install putty
```
Then **APPLICATIONS > INTERNET > PUTTY**

---

### Post by malfist on 2006-12-27
jerome@ubuntu:~$ ssh 192.168.1.101
ssh: connect to host 192.168.1.101 port 22: No route to host
Putty throws same error

---

### Post by dbott67 on 2006-12-27
You need to make sure the firewall in XP is disabled (or preferably, permits traffic on port 22).

1. Open the Windows Firewall (**START > SETTINGS > CONTROL PANEL > WINDOWS FIREWALL**)
2. Select the **EXCEPTIONS** tab
3. Click **ADD PORT**
4. In the NAME field type: **SSH**
5. In the PORT field type:** 22 (TCP)**
6. Click **OK**.

-Dave

---

### Post by malfist on 2006-12-27
Same thing, I use ZoneAlarm on windows mainly and set it to allow access but it's still throwing the same error. I shut the firewall completely down and I still can't get access. Only thing I did with OpenSSH is that I downloaded and installed it and added the pswrd(or what ever it called it) file.

---

### Post by malfist on 2006-12-27
More info, ping for that computer:
jerome@ubuntu:~$ ping 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
From 192.168.1.102 icmp_seq=2 Destination Host Unreachable
From 192.168.1.102 icmp_seq=3 Destination Host Unreachable
From 192.168.1.102 icmp_seq=4 Destination Host Unreachable
From 192.168.1.102 icmp_seq=6 Destination Host Unreachable
From 192.168.1.102 icmp_seq=7 Destination Host Unreachable
From 192.168.1.102 icmp_seq=8 Destination Host Unreachable
From 192.168.1.102 icmp_seq=10 Destination Host Unreachable
From 192.168.1.102 icmp_seq=11 Destination Host Unreachable
From 192.168.1.102 icmp_seq=12 Destination Host Unreachable

--- 192.168.1.101 ping statistics ---
13 packets transmitted, 0 received, +9 errors, 100% packet loss, time 12012ms
, pipe 3

192.168.1.101 is the IP for that computer and I should be able to ping it, we are on the same network and the firewall was disabled when I pinged.

---

### Post by malfist on 2006-12-27
Stupid mistake IP is 192.168.1.100, I assumed sense I was 102 that (because it is DHCP) 101 would be the other computer but it was infact the left over IP address from when I had wired access (just recently switched). SSH is now throwing connection refused even though firewall is shut down (windows and ZoneAlarm). Have I not configured it correctly even on the windows computer it cannot connect to itself through ssh, connection refused.

---

### Post by dbott67 on 2006-12-27
Can you post the output of:
```
dbott@thedrake:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

-Dave

---

### Post by malfist on 2006-12-27
```
jerome@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by dbott67 on 2006-12-27
Also, can you post the output of **ipconfig /all** on your Windows XP comp:
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\WINDOWS>**ipconfig /all**

Windows IP Configuration

        Host Name . . . . . . . . . . . . : omega-xp
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : 00-15-C5-0C-xx-xx

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-31-xx-xx
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.105
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1
        Lease Obtained. . . . . . . . . . : Saturday, December 23, 2006 3:25:06
PM
        Lease Expires . . . . . . . . . . : Saturday, December 30, 2006 3:25:06
PM

C:\WINDOWS>
```

and **netstat -a**
```

C:\Documents and Settings\dbott>=~=~=~=~=~=~=~=~=~=~=~= PuTTY log 2006.12.27 21:23:17 =~=~=~=~=~=~=~=~=~=~=~=

login as: dbott 
dbott@192.168.1.105's password: 
Last login: Wed Dec 27 21:21:39 2006 from 192.168.1.106

Microsoft Windows XP [Version 5.1.2600]

(C) Copyright 1985-2001 Microsoft Corp.
C:\Documents and Settings\dbott>netstat -a

Active Connections

  Proto  Local Address          Foreign Address        State

  **[COLOR="Red"]TCP    omega-xp:22            omega-xp:0             LISTENING[/COLOR]**
  TCP    omega-xp:epmap         omega-xp:0             LISTENING
  TCP    omega-xp:microsoft-ds  omega-xp:0             LISTENING
  TCP    omega-xp:3389          omega-xp:0             LISTENING
  TCP    omega-xp:5679          omega-xp:0             LISTENING
  TCP    omega-xp:5800          omega-xp:0             LISTENING
  TCP    omega-xp:5900          omega-xp:0             LISTENING
  TCP    omega-xp:1030          omega-xp:0             LISTENING
  TCP    omega-xp:1031          omega-xp:0             LISTENING
  TCP    omega-xp:1033          omega-xp:0             LISTENING
  TCP    omega-xp:1034          omega-xp:0             LISTENING
  TCP    omega-xp:1088          localhost:1089         ESTABLISHED
  TCP    omega-xp:1089          localhost:1088         ESTABLISHED
  TCP    omega-xp:2585          omega-xp:0             LISTENING
  TCP    omega-xp:2750          omega-xp:0             LISTENING
  TCP    omega-xp:10110         omega-xp:0             LISTENING
[COLOR="Blue"]  TCP    omega-xp:22            192.168.1.106:46344    ESTABLISHED[/COLOR]
  TCP    omega-xp:netbios-ssn   omega-xp:0             LISTENING
  TCP    omega-xp:1064          209.123.81.41:http     CLOSE_WAIT
  TCP    omega-xp:2177          72.14.207.104:http     TIME_WAIT
  TCP    omega-xp:2195          72.14.207.104:http     TIME_WAIT
  TCP    omega-xp:2287          static-fxfeeds.nslb.sj.mozilla.com:http  TIME_WAIT
  TCP    omega-xp:2390          a209-202-96-214.deploy.akamaitechnologies.com:http  TIME_WAIT
  TCP    omega-xp:2393          a209-202-96-214.deploy.akamaitechnologies.com:http  TIME_WAIT
  TCP    omega-xp:netbios-ssn   omega-xp:0             LISTENING
  TCP    omega-xp:netbios-ssn   omega-xp:0             LISTENING
```

-Dave

---

### Post by dbott67 on 2006-12-27
> **malfist said:**
> ```
jerome@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

This looks good.

You can try the equivalent command in XP :
```
route print
```

It should have the same info (i.e. default gateway = 192.168.1.1).

-Dave

---

### Post by malfist on 2006-12-27
```

I:\>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : chvlva.adelphia.net
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

Tunnel adapter Teredo Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : fe80::ffff:ffff:fffd%4
        Default Gateway . . . . . . . . . :

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . : chvlva.adelphia.net
        IP Address. . . . . . . . . . . . : fe80::5efe:192.168.1.100%2
        Default Gateway . . . . . . . . . :

I:\>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : home
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : chvlva.adelphia.net

Ethernet adapter Local Area Connection 2:

        Connection-specific DNS Suffix  . : chvlva.adelphia.net
        Description . . . . . . . . . . . : Realtek RTL8139 Family PCI Fast Ethe
rnet NIC
        Physical Address. . . . . . . . . : 00-11-2F-9E-04-69
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 70.34.117.6
                                            70.34.117.7
        Lease Obtained. . . . . . . . . . : Wednesday, December 27, 2006 5:47:07
 PM
        Lease Expires . . . . . . . . . . : Thursday, December 28, 2006 5:47:07
PM

Tunnel adapter Teredo Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
        Physical Address. . . . . . . . . : FF-FF-FF-FF-FF-FF-FF-FF
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::ffff:ffff:fffd%4
        Default Gateway . . . . . . . . . :
        NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Automatic Tunneling Pseudo-Interface:

        Connection-specific DNS Suffix  . : chvlva.adelphia.net
        Description . . . . . . . . . . . : Automatic Tunneling Pseudo-Interface

        Physical Address. . . . . . . . . : C0-A8-01-64
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : fe80::5efe:192.168.1.100%2
        Default Gateway . . . . . . . . . :
        DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                            fec0:0:0:ffff::2%1
                                            fec0:0:0:ffff::3%1
        NetBIOS over Tcpip. . . . . . . . : Disabled

```

I:\>netstat -a

Active Connections

  Proto  Local Address          Foreign Address        State
  TCP    home:22                home:0                 LISTENING
  TCP    home:epmap             home:0                 LISTENING
  TCP    home:microsoft-ds      home:0                 LISTENING
  TCP    home:2869              home:0                 LISTENING
  TCP    home:3260              home:0                 LISTENING
  TCP    home:3261              home:0                 LISTENING
  TCP    home:14238             home:0                 LISTENING
  TCP    home:1025              home:0                 LISTENING
  TCP    home:1033              home:0                 LISTENING
  TCP    home:10110             home:0                 LISTENING
  TCP    home:netbios-ssn       home:0                 LISTENING
  TCP    home:1127              ohiggins.ubuntu.com:http  TIME_WAIT
  TCP    home:1128              ohiggins.ubuntu.com:http  TIME_WAIT
  TCP    home:1179              ohiggins.ubuntu.com:http  TIME_WAIT
  TCP    home:epmap             home:0                 LISTENING       0
  TCP    home:2869              home:0                 LISTENING       0
  UDP    home:microsoft-ds      *:*
  UDP    home:isakmp            *:*
  UDP    home:1026              *:*
  UDP    home:1038              *:*
  UDP    home:1041              *:*
  UDP    home:1083              *:*
  UDP    home:4500              *:*
  UDP    home:9370              *:*
  UDP    home:14237             *:*
  UDP    home:ntp               *:*
  UDP    home:1057              *:*
  UDP    home:1081              *:*
  UDP    home:1900              *:*
  UDP    home:ntp               *:*
  UDP    home:netbios-ns        *:*
  UDP    home:netbios-dgm       *:*
  UDP    home:1900              *:*
  UDP    home:7483              *:*
  UDP    home:14175             *:*
  UDP    home:15858             *:*
  UDP    home:63690             *:*
```



```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

I:\Documents and Settings\Hollon>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 11 2f 9e 04 69 ...... Realtek RTL8139 Family PCI Fast Ethernet NIC - P
acket Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1   192.168.1.100       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.1.0    255.255.255.0    192.168.1.100   192.168.1.100       20
    192.168.1.100  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.1.255  255.255.255.255    192.168.1.100   192.168.1.100       20
        224.0.0.0        240.0.0.0    192.168.1.100   192.168.1.100       20
  255.255.255.255  255.255.255.255    192.168.1.100   192.168.1.100       1
Default Gateway:       192.168.1.1
===========================================================================
Persistent Routes:
  None

I:\Documents and Settings\Hollon>
[CODE]

---

### Post by malfist on 2006-12-27
update: it will allow access (I hadn't created group and password properly), saying something about key can not be athenticated. then it asks for my password. The password the the windows computer uses is blank(I'm not incharge of that part of the computer, ease over security) and it won't accept that, invalid password what should I use?

---

### Post by dbott67 on 2006-12-27
EDIT: Oops.. too slow typing.  Ignore this post.

[COLOR="Silver"]The routing tables look good for both.

1. I can see the SSH service running on the XP machine (TCP home:22 home:0 LISTENING)
2. Can both machines get on the internet?
3. Try pinging the router from both machines and let me know if you can ping it.  
4. From the Windows XP computer, try pinging the Ubuntu computer.

If you are able to ping everything except the Windows XP computer, I would say that there's some remnants of ZoneAlarm or some firewall still running.

Let me know what you find out.

-Dave[/COLOR]

---

### Post by dbott67 on 2006-12-27
> **malfist said:**
> update: it will allow access (I hadn't created group and password properly), saying something about key can not be athenticated. then it asks for my password. The password the the windows computer uses is blank(I'm not incharge of that part of the computer, ease over security) and it won't accept that, invalid password what should I use?

I think each account requires a password.  Can you get them to setup a special admin account for you with a password so that you can login?

-Dave

---

### Post by malfist on 2006-12-27
I'm simi-owner of it, I can do that but they want it to be where it automaticly logs them in on boot up

---

### Post by malfist on 2006-12-27
Thanks by the way, you've been a BIG help

---

### Post by dbott67 on 2006-12-28
You can still create another account for yourself and then have their's be the one automatically logged on:

**_Windows XP Auto Login_**

You can configure Windows XP to automate the logon process if your computer is not part of a domain. Computers configured in a business environment generally have a domain and for those machines the option "Users must enter a username" does not appear because a password must be given to access the local area network or domain.

1. Click **Start**, click **Run**, and type **control userpasswords2**.
2. Uncheck the "Users must enter a username and password to use this computer" check box.
3. Click Apply.
4. Enter the user name and password you wish to automatically log on with, and then click OK.
5. Click OK again and you're all done. 

Now, the computer will login using their account, and you can SSH over using your account.

Don't forget to run the **mkgroup** & **mkpasswd** commands for your new user account in SSH.

-Dave

---

### Post by Lothas on 2007-11-19
Hi, I've been using a DC++ hub outside of my university by using a program called Tunneling MIRC. The guys at my school managed to bypass the network's blockages by using it and that way we can get through to the outside world (HTTP is one of the few ports open )

So, how do I connect to this other hub from Ubuntu???

---

