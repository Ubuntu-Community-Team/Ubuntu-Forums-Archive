---
title: "Please help.  Ubuntu can't see windows workgroup"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by yankeeairpirate on 2008-03-15
I've been through two installs just to get a clean slate.  I'm trying to hook my Ubuntu laptop to my home network.  I have no issue doing this wired.  Everything changes once I switch to wireless.  I've looked at just about every HOWTO and thread on this subject and I haven't been able to solve this problem.  I was wondering if someone could take a look with fresh eyes.  Here's my config and a smbtree:

[global] 
    ; General server settings 
    netbios name = portofcall 
    server string = 
    workgroup = THE FLIGHTLINE 
    announce version = 5.0 
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192 

    passdb backend = tdbsam 
    security = share 
    null passwords = true 
    username map = /etc/samba/smbusers 
    name resolve order = lmhosts hosts wins bcast 

    wins support = yes 

    printing = CUPS 
    printcap name = CUPS 

    syslog = 1 
    syslog only = yes 

; NOTE: If you need access to the user home directories uncomment the 
; lines below and adjust the settings to your hearts content. 
;[homes] 
    ;valid users = %S 
    ;create mode = 0600 
    ;directory mode = 0755 
    ;browseable = no 
    ;read only = no 
    ;veto files = /*.{*}/.*/mail/bin/ 

; NOTE: Only needed if you run samba as a primary domain controller. 
; Not needed as this config doesn't cover that matter. 
;[netlogon] 
    ;path = /var/lib/samba/netlogon 
    ;admin users = Administrator 
    ;valid users = %U 
    ;read only = no 

; NOTE: Again - only needed if you're running a primary domain controller. 
;[Profiles] 
    ;path = /var/lib/samba/profiles 
    ;valid users = %U 
    ;create mode = 0600 
    ;directory mode = 0700 
    ;writeable = yes 
    ;browseable = no 

; NOTE: Inside this place you may build a printer driver repository for 
; Windows - I'll cover this topic in another HOWTO. 
[print$] 
    path = /var/lib/samba/printers 
    browseable = yes 
    guest ok = yes 
    read only = yes 
    write list = root 
    create mask = 0664 
    directory mask = 0775 

[printers] 
    path = /tmp 
    printable = yes 
    guest ok = yes 
    browseable = no 

; Uncomment if you need to share your CD-/DVD-ROM Drive 
;[DVD-ROM Drive] 
    ;path = /media/cdrom 
    ;browseable = yes 
    ;read only = yes 
    ;guest ok = yes 

[MyFiles] 
    path = /media/samba/ 
    browseable = yes 
    read only = no 
    guest ok = no 
    create mask = 0644 
    directory mask = 0755 
    force user = yankeeairpirate 
    force group = yankeeairpirate


smbtree
THE FLIGHTLINE 
        \\PORTOFCALL     
                \\PORTOFCALL\IPC$               IPC Service () 
                \\PORTOFCALL\MyFiles        
                \\PORTOFCALL\print$         
        \\HANGAR18       
Error connecting to 192.168.2.5 (No route to host) 
cli_start_connection: failed to connect to HANGAR18<20> (192.168.2.5). Error NT_STATUS_HOST_UNREACHABLE 

I've tried with SWAT and without.  I've tried just about everything that I can find.  I'm very new at Ubuntu, but I'm sure I can get this working with a little coaching.  Thank you.

---

### Post by Iowan on 2008-03-17
I'll give your thread a bump...
You say it works wired - just not wireless?

---

### Post by Eiríkr on 2008-03-17
To follow up on Iowan's comment, your issue sounds like it has nothing to do with Samba, and everything to do with your wireless network connection failing out.  The [font=courier]smbtree[/font] error message "No route to host" reinforces this view.  Please post the results of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

Cheers,

Eiríkr

---

### Post by yankeeairpirate on 2008-03-18
I'm at work right now, so I'll post that when I get home.

---

### Post by yankeeairpirate on 2008-03-18
> **Eiríkr said:**
> To follow up on Iowan's comment, your issue sounds like it has nothing to do with Samba, and everything to do with your wireless network connection failing out.  The [font=courier]smbtree[/font] error message "No route to host" reinforces this view.  Please post the results of the following:
```
ifconfig
iwconfig
cat /etc/network/interfaces
```

Cheers,

Eiríkr

yankeeairpirate@portofcall:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:97:8A:0A  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:14:A4:D1:EE:44  
          inet addr:192.168.2.7  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fed1:ee44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:198 errors:0 dropped:324 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:198130 (193.4 KB)  TX bytes:32051 (31.2 KB)
          Interrupt:10 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KB)  TX bytes:2772 (2.7 KB)

yankeeairpirate@portofcall:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"The Hangar"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:17:3F:96:02:F9   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level=-50 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:127  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

yankeeairpirate@portofcall:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by Eiríkr on 2008-03-18
Okay, your wireless looks like it's connecting just fine.  This makes me wonder if it's connecting to a different subnet than where your share server is located.  Please also post [font=courier]route -n[/font] from your Ubuntu machine.  Then, if your share server is Linux, please post the output of [font=courier]route -n[/font] and [font=courier]ifconfig[/font] for that machine; if it's Windows, run [font=courier]route print[/font] and [font=courier]ipconfig[/font] instead.  

Cheers,

Eiríkr

---

### Post by yankeeairpirate on 2008-03-18
> **Eiríkr said:**
> Okay, your wireless looks like it's connecting just fine.  This makes me wonder if it's connecting to a different subnet than where your share server is located.  Please also post [font=courier]route -n[/font] from your Ubuntu machine.  Then, if your share server is Linux, please post the output of [font=courier]route -n[/font] and [font=courier]ifconfig[/font] for that machine; if it's Windows, run [font=courier]route print[/font] and [font=courier]ipconfig[/font] instead.  

Cheers,

Eiríkr




C:\Users\Yankee Air Pirate>route print
===========================================================================
Interface List
  9 ...00 1a a0 b3 9c 36 ...... Broadcom NetXtreme 57xx Gigabit Controller
  1 ........................... Software Loopback Interface 1
  8 ...02 00 54 55 4e 01 ...... Teredo Tunneling Pseudo-Interface
 13 ...00 00 00 00 00 00 00 e0  isatap.The Hangar
===========================================================================

IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.2.1      192.168.2.5     20
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      169.254.0.0      255.255.0.0         On-link       192.168.2.5     30
  169.254.255.255  255.255.255.255         On-link       192.168.2.5    276
      192.168.2.0    255.255.255.0         On-link       192.168.2.5    276
      192.168.2.5  255.255.255.255         On-link       192.168.2.5    276
    192.168.2.255  255.255.255.255         On-link       192.168.2.5    276
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link       192.168.2.5    276
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link       192.168.2.5    276
===========================================================================
Persistent Routes:
  None

IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
  8     18 ::/0                     On-link
  1    306 ::1/128                  On-link
  8     18 2001::/32                On-link
  8    266 2001:0:cf2e:308c:2c3f:2672:3f57:fdfa/128
                                    On-link
  9    276 fe80::/64                On-link
  8    266 fe80::/64                On-link
 13    281 fe80::5efe:192.168.2.5/128
                                    On-link
  8    266 fe80::2c3f:2672:3f57:fdfa/128
                                    On-link
  9    276 fe80::b938:1f06:f451:6215/128
                                    On-link
  1    306 ff00::/8                 On-link
  8    266 ff00::/8                 On-link
  9    276 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

C:\Users\Yankee Air Pirate>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Hangar18
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : The Hangar

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : The Hangar
   Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Controll
r
   Physical Address. . . . . . . . . : 00-1A-A0-B3-9C-36
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b938:1f06:f451:6215%9(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.2.5(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Tuesday, March 18, 2008 5:10:02 PM
   Lease Expires . . . . . . . . . . : Saturday, April 25, 2144 12:18:48 AM
   Default Gateway . . . . . . . . . : 192.168.2.1
   DHCP Server . . . . . . . . . . . : 192.168.2.1
   DHCPv6 IAID . . . . . . . . . . . : 201333408
   DNS Servers . . . . . . . . . . . : 192.168.2.1
   Primary WINS Server . . . . . . . : 192.168.2.7
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:cf2e:308c:2c3f:2672:3f57:fdfa(Pre
erred)
   Link-local IPv6 Address . . . . . : fe80::2c3f:2672:3f57:fdfa%8(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . : The Hangar
   Description . . . . . . . . . . . : isatap.The Hangar
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.2.5%13(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.2.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\Yankee Air Pirate>

---

### Post by yankeeairpirate on 2008-03-18
yankeeairpirate@portofcall:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1
yankeeairpirate@portofcall:~$

---

### Post by yankeeairpirate on 2008-03-18
By the way, I'm sorry I'm taking so long between replies.  I really do appreciate the help.

---

### Post by Eiríkr on 2008-03-18
Oookay, that's one possibility ruled out (different subnets / broadcast addresses).  A few things occur to me at this point --
[list=1][*]It's curious that your eth1 interface is missing from your /etc/network/interfaces file.  Did you remove that yourself?  Any ideas what brings your eth1 interface up on boot, then?  Is it getting its settings via DHCP?
[code]
[*]What's in your /etc/resolv.conf file?  
[*]The DNS suffix on your Windows machine is showing as **The Hanger**, only I didn't think spaces were allowed in DNS suffixes.  Might this be throwing things off?  
[*]Now that we've seen the route for your server, please also post [font=courier]route -n[/font] results for your Ubuntu Samba client machine.  And for good measure, also try to ping the Samba server from the Ubuntu machine, using both the IP address and the hostname:
[code]ping -c 4 192.168.2.5
ping -c 4 hangar18[/list]

Cheers,

Eiríkr

PS -- No trouble taking your time -- just saw your route -n, so no worries there.  I'll give a look in a bit -- have to run on a couple errands for the next few hours.

PPS -- Can the Windows machine ping the Ubuntu one?

---

### Post by yankeeairpirate on 2008-03-18
Just below the results from my Windows machine is the result of the route -n.

---

### Post by yankeeairpirate on 2008-03-18
> **yankeeairpirate said:**
> Just below the results from my Windows machine is the result of the route -n.


I didn't remove the eth1 interface from the interfaces file.  and I am pulling settings via DHCP

Nothing in the resolv.conf file.  Changed "The Hangar" to "TheHangar"

Pinging 198.162.2.5 gets "Network is unreachable"

Pinging hangar18 gets "unknown host hangar18"

---

### Post by Eiríkr on 2008-03-18
Hmmm...  Can Hangar18 ping PortOfCall?  And can either / both of them ping the gateway, 192.168.2.1?  I'm running out of ideas here.  :confused:

---

### Post by Iowan on 2008-03-19
What is providing wireless access to your network?
>  Pinging 198.162.2.5 gets "Network is unreachable"
I presume that was a typo for 192.168.2.5...

---

### Post by yankeeairpirate on 2008-03-19
> **Iowan said:**
> What is providing wireless access to your network?

I presume that was a typo for 192.168.2.5...

Yeah, that was a typo.  I'm using a belkin router.  I'm at work, so I can't give you specifics.  I'll post them later.

And i'll try those other pings when I get home too.

---

### Post by yankeeairpirate on 2008-03-19
> **Eiríkr said:**
> Hmmm...  Can Hangar18 ping PortOfCall?  And can either / both of them ping the gateway, 192.168.2.1?  I'm running out of ideas here.  :confused:

Neither one can ping the other, but they can both ping the router.

---

### Post by Eiríkr on 2008-03-19
All I can think at this point is that there might be a firewall somewhere, possibly even within your router's settings, that is interfering with wireless traffic within your LAN.  I don't suppose you have ZoneAlarm installed on the Windows side?  There was another thread recently where that was the issue.  

Puzzled,

Eiríkr

---

### Post by yankeeairpirate on 2008-03-19
No zone alarm.  i'll check my settings again and see what's going on.

---

