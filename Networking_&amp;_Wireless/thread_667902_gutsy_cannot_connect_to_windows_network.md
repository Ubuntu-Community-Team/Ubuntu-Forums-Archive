---
title: "gutsy cannot connect to windows network"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by frogotronic on 2008-01-14
Gutsy cannot connect to a windows network.  Wasn't a problem in Fiesty, just clicked on the windows computer icon in the network menu

Any ideas?

---

### Post by frogotronic on 2008-01-14
I have SAMBA configured, I can ping machines via IP, I can connect to printers via HJ direct (IP).  So the connections are sort of there, but using Places>Network>Windows Network doesn't show anything.

---

### Post by Dwiman89 on 2008-01-14
I dont even have samba installed but I can access My parents files from my linux box. But I dont show up on there network places.....

---

### Post by frogotronic on 2008-01-14
> **Dwiman89 said:**
> I dont even have samba installed but I can access My parents files from my linux box. But I dont show up on there network places.....

weird thing is that can connect to the windows share printer via IP address and to the windows machines via IP addresses, but NOT using the NetBIOS names.  So it's working but, not completely.

There is a setting that is default different in Gutsy as compared to Feisty.

---

### Post by evanchu on 2008-01-15
Let us collect some basic diagnostic information.  I wrote a script, samba-net-diag1, that collects some basic samba diagnostic information.  It is in the "[Basic Samba diagnostics]("http://www.evanchu.com/linux2")" section.

Don't worry, it is a safe script.  You can read it.  Post the output and let us take a look.

---

### Post by frogotronic on 2008-01-15
okay, cool.  I'll try it tonight.

- CH

---

### Post by frogotronic on 2008-01-16
Okay here's the output:

```

enter other computer's IP address and press enter: 192.168.2.101
enter other computer's name and press enter: oskar2
##########
try pinging 192.168.2.101
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
64 bytes from 192.168.2.101: icmp_seq=1 ttl=128 time=3.42 ms
64 bytes from 192.168.2.101: icmp_seq=2 ttl=128 time=1.32 ms
64 bytes from 192.168.2.101: icmp_seq=3 ttl=128 time=0.939 ms

--- 192.168.2.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 0.939/1.894/3.421/1.091 ms
press enter to continue
##########
try pinging oskar2
ping: unknown host oskar2
press enter to continue
##########
is 192.168.2.101 on local subnet?
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
64 bytes from 192.168.2.101: icmp_seq=1 ttl=128 time=0.885 ms
64 bytes from 192.168.2.101: icmp_seq=2 ttl=128 time=0.922 ms
64 bytes from 192.168.2.101: icmp_seq=3 ttl=128 time=0.923 ms

--- 192.168.2.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.885/0.910/0.923/0.017 ms
press enter to continue
##########
try Samba node status query 192.168.2.101
Looking up status of 192.168.2.101
        OSKAR2          <00> -         B <ACTIVE> 
        LIFE            <00> - <GROUP> B <ACTIVE> 
        OSKAR2          <20> -         B <ACTIVE> 
        LIFE            <1e> - <GROUP> B <ACTIVE> 

        MAC Address = ############# (removed)

press enter to continue
##########
try Samba node status query oskar2
querying oskar2 on 172.16.184.255
querying oskar2 on 172.16.78.255
querying oskar2 on 192.168.2.255
192.168.2.101 oskar2<00>
Looking up status of 192.168.2.101
        OSKAR2          <00> -         B <ACTIVE> 
        LIFE            <00> - <GROUP> B <ACTIVE> 
        OSKAR2          <20> -         B <ACTIVE> 
        LIFE            <1e> - <GROUP> B <ACTIVE> 

        MAC Address = ########### (removed)

press enter to continue
##########
try Samba node status query on local subnet
querying * on 172.16.184.255
172.16.184.1 *<00>
press enter to continue
##########
try Samba list services on oskar2
Domain=[OSKAR2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        LINUX (L)       Disk      
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Documents       Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        L$              Disk      Default share
        Canon_i550      Printer   Canon i550
Domain=[OSKAR2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
press enter to continue

```


So, how does one interpret this output?

- CH

---

### Post by MariusSilverwolf on 2008-01-16
I've been having a similar issue with my system.  I cannot connect to my wife's XP Pro system when looking for the NetBIOS name, but if I look for smb://her.ip.address.here I get in no problem.  I think it's an issue with Samba not properly interpreting LMHosts or NetBIOS assignments, but since she's on a static IP address it isn't an issue for me, really.

---

### Post by frogotronic on 2008-01-16
> **MariusSilverwolf said:**
> I've been having a similar issue with my system.  I cannot connect to my wife's XP Pro system when looking for the NetBIOS name, but if I look for smb://her.ip.address.here I get in no problem.  I think it's an issue with Samba not properly interpreting LMHosts or NetBIOS assignments, but since she's on a static IP address it isn't an issue for me, really.


Yep, okay that's good that it not a one-off bug.  You are correct in that it's not a problem when you know the IP that you want to connect to; BUT it was nice (in FF) to be able to browse to a given computer.  It must be a setting, bcs SMB works with IPs.

Let's see what EVANCHU says.

- CH

---

### Post by mimada on 2008-01-16
I believe it'a a problem with the iptables firewall. Disable it and see if you can access your shares. Install Firestarter if you want to. It's a gui front end for iptables.

---

### Post by frogotronic on 2008-01-16
> **mimada said:**
> I believe it'a a problem with the iptables firewall. Disable it and see if you can access your shares. Install Firestarter if you want to. It's a gui front end for iptables.

Hi,

  Got Firestarter installed.  Problem persists even when firestarter is enabled, or disabled (via the GUI).  Is there another way?

- CH

---

### Post by evanchu on 2008-01-16
> **cement_head said:**
> 
So, how does one interpret this output?
- CH

Do you have multiple network interfaces on your linux machine?  In the section "node status query oskar2," I see the following possible interfaces: 172.16.184.x, 172.16.78.x, and 192.168.2.x.

In the section "node status query on local subnet," Samba only tried to query the 172.16.184.x interface.  And it found 1 machine: 172.16.184.1.  It did not query the 192.168.2.x interface, which is where your Windows machine is located.  I am expecting Samba to query all the interfaces.

If you do have multiple network interfaces, Samba may need to be configured to query the proper interfaces.  The configuration  item is "interfaces" in the smb.conf file.

If you want, can you post the output of ifconfig for us to take a look?

---

### Post by frogotronic on 2008-01-16
Yep, I've got VMWare installed for running a WindowsXP O/S. 

Here's the output of the ifconfig command:

```
eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXX 
          inet addr:134.53.9.36  Bcast:134.53.9.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fec0:5d62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:17469664 (16.6 MB)  TX bytes:486867 (475.4 KB)
          Base address:0x5000 Memory:d8500000-d8520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3480 (3.3 KB)  TX bytes:3480 (3.3 KB)

vmnet1    Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXX 
          inet addr:172.16.184.1  Bcast:172.16.184.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr XXXXXXXXXXXXX  
          inet addr:172.16.78.1  Bcast:172.16.78.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:d8000000-d8004000
``` 

I set up a shared folder on Ubuntu called "sharer" using these instructions: [http://ubuntuforums.org/showthread.php?t=652640](http://ubuntuforums.org/showthread.php?t=652640)

Also attached is my smb.conf file.

- CH

P.S.  Thanks for helping

---

### Post by evanchu on 2008-01-16
cement_head

In the smb.conf, I see a "workgroup = MSHOME".  But in the samba-net-diag1 output, in section "node status query oskar2," I see a group name of LIFE.  That is a mismatch.  Change one of them to match the other.  Reboot and see what happens.  Run samba-net-diag1 and post output.

If you don't care about browsing for all available Windows machines.  You can try connecting to a specific machine by using Places -> Connec to Server... -> Service type = Windows Share -> fill in Server name -> so on.

---

### Post by frogotronic on 2008-01-16
Partial Success.

Here's the diagnostic output:

```

enter other computer's IP address and press enter: 192.168.2.101
enter other computer's name and press enter: oskar2
##########
try pinging 192.168.2.101
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
64 bytes from 192.168.2.101: icmp_seq=1 ttl=128 time=0.962 ms
64 bytes from 192.168.2.101: icmp_seq=2 ttl=128 time=0.898 ms
64 bytes from 192.168.2.101: icmp_seq=3 ttl=128 time=0.911 ms

--- 192.168.2.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.898/0.923/0.962/0.044 ms
press enter to continue
##########
try pinging oskar2
ping: unknown host oskar2
press enter to continue
##########
is 192.168.2.101 on local subnet?
PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
64 bytes from 192.168.2.101: icmp_seq=1 ttl=128 time=4.38 ms
64 bytes from 192.168.2.101: icmp_seq=2 ttl=128 time=0.887 ms
64 bytes from 192.168.2.101: icmp_seq=3 ttl=128 time=0.927 ms

--- 192.168.2.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.887/2.067/4.387/1.640 ms
press enter to continue
##########
try Samba node status query 192.168.2.101
Looking up status of 192.168.2.101
        OSKAR2          <00> -         B <ACTIVE> 
        LIFE            <00> - <GROUP> B <ACTIVE> 
        OSKAR2          <20> -         B <ACTIVE> 
        LIFE            <1e> - <GROUP> B <ACTIVE> 
        LIFE            <1d> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 

        MAC Address = ##############

press enter to continue
##########
try Samba node status query oskar2
querying oskar2 on 172.16.184.255
querying oskar2 on 172.16.78.255
querying oskar2 on 192.168.2.255
192.168.2.101 oskar2<00>
Looking up status of 192.168.2.101
        OSKAR2          <00> -         B <ACTIVE> 
        LIFE            <00> - <GROUP> B <ACTIVE> 
        OSKAR2          <20> -         B <ACTIVE> 
        LIFE            <1e> - <GROUP> B <ACTIVE> 
        LIFE            <1d> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 

        MAC Address = ##############

press enter to continue
##########
try Samba node status query on local subnet
querying * on 172.16.184.255
172.16.184.1 *<00>
press enter to continue
##########
try Samba list services on oskar2
Domain=[OSKAR2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        LINUX (L)       Disk      
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Documents       Disk      
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        L$              Disk      Default share
        Canon_i550      Printer   Canon i550
Domain=[OSKAR2] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
press enter to continue
```

Not much different; *however*, When I open up the GUI for Places>Network I get this (attached screenshot).  And I can see my local "LIFE" network/workgroup.

However, when I click Windows Network, still nothing.

Interesting extra bit of info (which may be related to MIMADA's comment on IP tables).  I had to start Firestarter get it set up and running and then stop it to see the LIFE workgroup computers.

I think the [B][COLOR="Red"]<STOP!>

--------------------------------------------------

Okay - FIXED THE PROBLEM.

JUST ADDED RULE TO FIRESTARTER.  UNDER POLICY>ALLOW SERVICE FOR SAMBA (EVERYONE).

Now it works!

However, Is this secure?
[/COLOR][/B]
- CH

---

### Post by evanchu on 2008-01-17
> **cement_head said:**
> 
JUST ADDED RULE TO FIRESTARTER.  UNDER POLICY>ALLOW SERVICE FOR SAMBA (EVERYONE).
Now it works!
However, Is this secure?


If your Linux machine is on your home network, and if it is not connected directly to the internet, and your home-network router has a firewall, I would consider it safe.

Personally, I turned off my firewall on my Linux machine.  I just rely on my home-network router's firewall.

---

