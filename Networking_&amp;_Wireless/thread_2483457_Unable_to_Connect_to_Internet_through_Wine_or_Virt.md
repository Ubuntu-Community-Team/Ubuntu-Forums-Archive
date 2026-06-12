---
title: "Unable to Connect to Internet through Wine or VirtualBox"
date: 2023-01-30
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2023-01-30
I am running ubuntu 22.04LTS under which I have installed both wine and virtualbox. Under virtualbox, I've installed Windows XP. The internet is just fine under linux, but no program running under wine or virtualbox is able to connect to the internet. This worked just fine under ubuntu 18.04LTS. I've found mention online of issues running 32 bit programs under a 64 bit system and that I might need lib32-gnutls or libnss-mdns-i386 but neither are available under apt. Could someone help me out with this? 

I don't know how/where to find a log for wine, but this is what I get when I do a "diagnose issues" under Windows XP in virtualbox. 


```
Last diagnostic run time: 01/30/23 19:51:55 HTTP, HTTPS, FTP Diagnostic 
HTTP, HTTPS, FTP connectivity 

info HTTP: Successfully connected to www.microsoft.com. 
warn HTTPS: Error 12157 connecting to www.microsoft.com: An error occurred in the secure channel support  
warn FTP (Passive): Error 12031 connecting to ftp.microsoft.com: The connection with the server was reset  
warn HTTPS: Error 12029 connecting to www.passport.net: A connection with the server could not be established  
warn FTP (Active): Error 12031 connecting to ftp.microsoft.com: The connection with the server was reset  
error Could not make an HTTPS connection. 
error Could not make an FTP connection. 
info Redirecting user to support call 
 


DNS Client Diagnostic 
DNS - Not a home user scenario 

info Using Web Proxy: no 
info Resolving name ok for (www.microsoft.com): yes 
No DNS servers 

DNS failure 

 


Gateway Diagnostic 
Gateway 

info The following proxy configuration is being used by IE: Automatically Detect Settings:Disabled Automatic Configuration Script: Proxy Server: Proxy Bypass list:  
info This computer has the following default gateway entry(ies): 10.0.2.2 
info This computer has the following IP address(es): 10.0.2.15 
info The default gateway is in the same subnet as this computer 
info The default gateway entry is a valid unicast address 
info The default gateway address was resolved via ARP in 1 try(ies) 
info The default gateway was reached via ICMP Ping in 1 try(ies) 
info TCP port 80 on host 23.33.242.16 was successfully reached 
info The Internet host www.microsoft.com was successfully reached 
info The default gateway is OK 
 


IP Layer Diagnostic 
Corrupted IP routing table 

info The default route is valid 
info The loopback route is valid 
info The local host route is valid 
info The local subnet route is valid 
Invalid ARP cache entries 

action The ARP cache has been flushed 
 


IP Configuration Diagnostic 
Invalid IP address 

info Valid IP address detected: 10.0.2.15 
 


Wireless Diagnostic 
Wireless - Service disabled 

Wireless - User SSID 

Wireless - First time setup 

Wireless - Radio off 

Wireless - Out of range 

Wireless - Hardware issue 

Wireless - Novice user 

Wireless - Ad-hoc network 

Wireless - Less preferred 

Wireless - 802.1x enabled 

Wireless - Configuration mismatch 

Wireless - Low SNR 

 


WinSock Diagnostic 
WinSock status 

info All base service provider entries are present in the Winsock catalog. 
info The Winsock Service provider chains are valid. 
info Provider entry MSAFD Tcpip [TCP/IP] passed the loopback communication test. 
info Provider entry MSAFD Tcpip [UDP/IP] passed the loopback communication test. 
info Provider entry RSVP UDP Service Provider passed the loopback communication test. 
info Provider entry RSVP TCP Service Provider passed the loopback communication test. 
info Connectivity is valid for all Winsock service providers. 
 


Network Adapter Diagnostic 
Network location detection 

info Using home Internet connection 
Network adapter identification 

info Network connection: Name=Local Area Connection, Device=Intel(R) PRO/1000 T Server Adapter, MediaType=LAN, SubMediaType=LAN 
info Ethernet connection selected 
Network adapter status 

info Network connection status: Connected 
 


HTTP, HTTPS, FTP Diagnostic 
HTTP, HTTPS, FTP connectivity 

warn FTP (Passive): Error 12031 connecting to ftp.microsoft.com: The connection with the server was reset  
info HTTP: Successfully connected to www.microsoft.com. 
warn HTTPS: Error 12157 connecting to www.microsoft.com: An error occurred in the secure channel support  
warn HTTPS: Error 12029 connecting to www.passport.net: A connection with the server could not be established  
warn FTP (Active): Error 12031 connecting to ftp.microsoft.com: The connection with the server was reset  
error Could not make an HTTPS connection. 
error Could not make an FTP connection. 
 

```

---

### Post by rebeltaz on 2023-02-13
I have tried several things, so I am updating this with the steps I've taken, as posted elsewhere with no replies there, either:

I am running wine-6.0.3 (Ubuntu 6.0.3~repack-1) under Ubuntu 22.04 LTS, installed via apt. I have several programs installed that need access to the internet. Before I migrated to Ubuntu 22.04, everything worked properly under 18.04. Now, no program under wine can access the internet.

I ran 'wine cmd' and tried 'ping [www.google.com](www.google.com)' and even though that nameserver is translated to an IP address, the ping fails. If, however, I run 'sudo wine cmd' (just as a test), the ping works as expected.

I found this - [https://wiki.winehq.org/FAQ#Failed_to_u](https://wiki.winehq.org/FAQ#Failed_to_u) ... ermissions - which seems to maybe be a possible solution, except that there is no wine-preloader file that I can find anywhere, either in the locations noted or through a search of the filesystem.

I saw the recommendation to run 'dpkg-reconfigure wine-<branch>-amd64 wine-<branch> wine-<branch>-i386' and I tried that as well, substituting 'stable' for '<branch>'. It tells me that the command must be run as root and when I do, it tells me that wine-stable-amd64 is not installed. If I try one at a time, it says that none of those [wine-stable-amd64;wine-stable; wine-stable-i386] are installed.

I also saw on this sub a recommendation to install libnutls30 - [https://www.reddit.com/r/winehq/comments/qeiafl/connect_to_internet/](https://www.reddit.com/r/winehq/comments/qeiafl/connect_to_internet/). I checked with apt-cache policy and it says that I already have that installed - " Installed: 3.7.3-4ubuntu1.1"

Could someone please tell me what I am missing here? Thank you.

---

### Post by kc1di on 2023-02-13
I'm not sure but on one of the programs I run in wine I have to also have Mono installed in order for it to use the internet connection.  Worth a try.

---

### Post by SeijiSensei on 2023-02-13
Make sure the virtual machines are running in NAT mode. That insures they will have the same permissions as the host.

---

### Post by rebeltaz on 2023-02-13
> **kc1di said:**
> I'm not sure but on one of the programs I run in wine I have to also have Mono installed in order for it to use the internet connection.  Worth a try.

Would that be mono-runtime-common? dpkg shows that that is installed. 

> **SeijiSensei said:**
> Make sure the virtual machines are running in NAT mode. That insures they will have the same permissions as the host.

What is NAT mode and how would I do that?

---

### Post by SeijiSensei on 2023-02-14
You did read the manual, right?

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by rebeltaz on 2023-02-14
> **SeijiSensei said:**
> You did read the manual, right?

[https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

Oh... virtualbox. I forgot that I included that in the "isn't working". I was think wine, which is main main concern. Since internet isn't working in either, I was thinking maybe it might be something in common between the two. 

I will try that tonight when I get home and see what happens.

---

### Post by rebeltaz on 2023-02-15
So, Virtualbox **was** set to NAT. Oddly enough, I can ping [www.google.com](www.google.com) and it works fine. internet explorer doesn't connect, though, and the troubleshooter says it doesn't know what's wrong, it just can't access http, ftp, or (something else). These are the settings it shows:
Physical Address: 08-00-27-E1-33-C5
IP Address: 10.0.2.15
Subnet Mask: 255.255.255.0
Default Gateway: 10.0.2.2
DHCP Server: 10.0.2.2
Lease Obtained: 2/15/2023 7:06:50 PM
Lease Expires: 2/16/2023 7:06:50 PM
DNS Server: 10.0.2.3
WINS Server: 

For the hell of it, I changed it to Bridged mode and tried again. This time, the settings look more like what I expect:
Physical Address: 08-00-27-E1-33-C5
IP Address: 192.168.1.118
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.254
DHCP Server: 192.168.1.254
Lease Obtained: 2/15/2023 7:00:18 PM
Lease Expires: 2/16/2023 7:00:18 PM
DNS Server: 192.168.1.254
WINS Server: 

but I still can't access web sites, even though I can ping just as before.

I'd really rather wine have internet access, though, but I'll settle for either one of I have to choose.

---

### Post by rebeltaz on 2023-02-15
> **kc1di said:**
> I'm not sure but on one of the programs I run in wine I have to also have Mono installed in order for it to use the internet connection.  Worth a try.

just in case mono-common-runtime wasn't what you meant, I tried installing wine-mono-6.0.0-x86.msi as well... still no connection.

---

### Post by rebeltaz on 2023-02-15
OK... I even went a whole different route. I installed PlayOnLinux and installed Kindle through that. I STILL cannot get the program t access the internet.

---

### Post by SeijiSensei on 2023-02-16
I bet you're running afoul of this rule.

In /etc/sysctl.conf, you'll see the line

```
#net.ipv4.ip_forward=1
```

That controls whether packets can be sent between interfaces on the same machine. It's designed as a security measure to block external machines from seeing the network behind the host.

Try this:

First, edit /etc/sysctl.conf as root with sudo. The easiest way is to run the command
```
sudo nano /etc/sysctl.conf
```

Find the line above and remove the hash mark ("#") from the beginning of the line. (Lines with # at the beginning are treated as comments.) Then save the file and run the command
```
sudo sysctl -p
```

to read the file and update the kernel. Work any better now?

---

### Post by rebeltaz on 2023-02-16
> **SeijiSensei said:**
> I bet you're running afoul of this rule.

In /etc/sysctl.conf, you'll see the line

```
#net.ipv4.ip_forward=1
```

That controls whether packets can be sent between interfaces on the same machine. It's designed as a security measure to block external machines from seeing the network behind the host.

Try this:

First, edit /etc/sysctl.conf as root with sudo. The easiest way is to run the command
```
sudo nano /etc/sysctl.conf
```

Find the line above and remove the hash mark ("#") from the beginning of the line. (Lines with # at the beginning are treated as comments.) Then save the file and run the command
```
sudo sysctl -p
```

to read the file and update the kernel. Work any better now?

Unfortunately, no. I even rebooted the computer just to be sure. Still unable to connect :(

---

### Post by rebeltaz on 2023-02-25
Just to update this issue...

I found instructions that libnss-mdns:i386 was needed, so I installed that... still no internet access through wine or virtualbox
I tried PlayOnLinux, which creates it's own, new wine prefix... still no internet access through wine

Still looking for a solution if anyone has anything....

---

### Post by rebeltaz on 2023-03-29
I hate to keep bumping this, but I have still not found a solution to this. I even tried installing PlayOnLinux to see if that would help... nope. Any one have any other ideas I haven't tried?

Since this is happening with wine, PlayOnLinux (which I know  is just a wine wrapped) and virtuabox, this has got to be some issue with Ubuntu. And since it only began when I "upgraded" it has to be an issue with 22.04. 

I appreciate all of the help so far, and will a appreciate even more a solution! :)

---

