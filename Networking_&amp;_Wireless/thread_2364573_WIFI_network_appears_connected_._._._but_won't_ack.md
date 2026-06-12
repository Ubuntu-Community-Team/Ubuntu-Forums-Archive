---
title: "WIFI network appears connected . . . but won't ackowledge ping or allow browsing"
date: 2017-06-24
forum: Networking &amp; Wireless
---

### Post by rocky3 on 2017-06-24
My WIFI network appears connected from UBUNTU . . . but won't ackowledge ping from windows or allow browsing. My windows machine was hacked on Wednesday . . . . so I removed the trojans and got it back up and connecting to my WIFI network named "ELDRIDGE"  Then I also set up so I looks like I am connected from my UBUNTU to my WIFI "Eldridge" but I can't open a browser, nor can I ping the UBUNTU from the DELL.   When I go to settings, I have a gateway and a IPV4 IP address, (though different from the ones I had prior to hack).   I can ping the UBUNtu gateway as well as the UBUNTU IPV4 address from the UBUNTU machine. . . .  but I can't ping the UBUNTU addresses from the windows machine.  further, the UBUNTU machine connects fine via HOTSPOT and VIA CAT V wired connection.

Please see my WIFI info report below:

[https://pastebin.ubuntu.com/24943481/](https://pastebin.ubuntu.com/24943481/)


Anything you can do to assist would be much appreciated!!:mad:

---

### Post by rocky3 on 2017-06-25
Bump

---

### Post by johndough2 on 2017-06-25
Hi

I see a lot of info.

The most obvious thing is TWO distinctly different networks.  192.168.0.xxx and 192.168.3.xxx

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0

wlp7s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp7s0b1' [IF2]>  
          inet addr:192.168.3.102  Bcast:192.168.3.255  Mask:255.255.255.0

So I do not know what ping numbers you are trying, 
but I would look at the IP values used in Windows and try to copy them.

Hi

Is every WiFi around you on channel 11?

If so try 6 or something.

---

### Post by rocky3 on 2017-06-26
Thanks!  I'm working on it.

Rocky3

---

### Post by rocky3 on 2017-07-01
Thanks for your suggestions! . . . . Since I posted this thread, the network is behaving more favorably, and my windows laptop connects fine through my WIFI network "Eldridge" to web sites using browsers, but still . . . neither the Firefox nor Chrome browsers on my UBUNTU are allowing me to connect to web sites.  You talked about the two separate networks.  It appears the  wlp7s0b is associated with 192.168.3.102 (UBUNTU laptop) and the 3.1 WIFI gateway address which are associated with my Broadcom WIFI card on my WIFI network called "Eldridge".  The  eno1 is associated with 192.168.0.14 and 0.1 gateway address which are associated with my real tec CAT V wired network card.  Since I posted this thread, I can now Ping from both of my UBUNTU network cards, (Wired and wireless) through my gateway to my windows Laptop (192.168.3.100 and 192.168.0.10) and my printer (3.104) . . . no problem.   You are correct in that the networks around me are all on channel 11, but now that I can PING freely, what would you suggest my next step would be.  Please see current WIFI report below.   

[https://paste.ubuntu.com/24995490/](https://paste.ubuntu.com/24995490/)

Anything you can do to help would be greatly appreicated!!

---

### Post by johndough2 on 2017-07-02
Hi

I did mention the Windows IP values, if you could produce then in a txt file, and compare them to the Ubuntu values it may show a discrepency.
```

Netfixer.bat
##############
:: NetFixer.bat, Copy, Paste & Save As..
:: Using a text editor like Notepad.
:: You can edit the file to your needs.
:: EG-Removing the :: in front of
:: ::ipconfig -all >>IPs.txt to create
:: a text file called IPs.txt to study.
:: Run as Administrator for best effect.
@ECHO  THIS MIGHT HELP TO REPAIR/RECTIFY
@ECHO  SOME SIMPLE NETWORK DIFFICULTIES.
@ECHO....................................
@ECHO  THE RESULTS MAY VARY ACCORDING TO
@ECHO  YOUR CONFIGURATION AND USER LEVEL
@ECHO  A RE-START SHOULD BE MADE AFTER 
@ECHO  RUNNING SOME OF THE ABOVE TESTS
@ECHO....................................
:MENU
@ECHO  TYPE IN THE RELEVANT MENU CHOICE
@ECHO....................................
@ECHO.
@ECHO  0 - PING_LO Ping test to 127.0.0.1
@ECHO  1 - PING_MS Ping test to Microsoft
@ECHO  2 - GET_MAC Obtain MAC address(es)
@ECHO  3 - GET_IPs Lists all IP addresses
@ECHO  4 - IPvFOUR Reset to remove errors
@ECHO  5 - IP_RNEW Force/Renew IP address
@ECHO  6 - IPv_SIX Reset to remove errors
@ECHO  7 - NBTSTAT NETBIOS -Renew -Repair
@ECHO  8 - NETSTAT All Network Statistics
@ECHO  9 - SH_WLAN Display WLAN interface
@ECHO  A - ARP_TAB Displays ARP IP tables 
@ECHO  B - NS_LKUP Shows your Name Server
@ECHO  C - SYS_SUM System Summary Windows
@ECHO  D - DNS_FIX Flush and Register DNS
@ECHO  E - WINSOCK Reset to remove errors 
@ECHO  F - FINISHD Close this Command Box
@ECHO ...................................
@ECHO OFF
COLOR B1
SET /P M= _Select 0-9,A-F, then press ENTER:
IF %M%==0 GOTO PING_LO
IF %M%==1 GOTO PING_MS
IF %M%==2 GOTO GET_MAC
IF %M%==3 GOTO GET_IPs
IF %M%==4 GOTO IPvFOUR
IF %M%==5 GOTO IP_RNEW
IF %M%==6 GOTO IPv_SIX
IF %M%==7 GOTO NBTSTAT
IF %M%==8 GOTO NETSTAT
IF %M%==9 GOTO SH_WLAN
IF /I %M%==A GOTO ARP_TAB
IF /I %M%==B GOTO NS_LKUP
IF /I %M%==C GOTO SYS_SUM
IF /I %M%==D GOTO DNS_FIX
IF /I %M%==E GOTO WINSOCK
IF /I %M%==F GOTO FINISHD
:PING_LO
ping LOOPBACK
GOTO MENU
:PING_MS
ping MICROSOFT.COM
GOTO MENU
:GET_MAC
getmac | more /c
:: getmac >> GetMac.txt
:: Notepad GetMac.txt
GOTO MENU
:GET_IPs
ipconfig -all | more /c
:: ipconfig -all >>IPs.txt
:: Notepad IPs.txt
GOTO MENU
:IPvFOUR
netsh int ipv4 reset reset.log
GOTO MENU
:IP_RNEW
ipconfig /release
ipconfig /renew
GOTO MENU
:IPv_SIX
netsh int ipv6 reset reset.log
GOTO MENU
:NBTSTAT
nbtstat -RR
GOTO MENU
:NETSTAT
netstat -e -r -s | more /c
:: netstat -e -r -s >> NetStat.txt
:: Notepad NetStat.txt
GOTO MENU
:SH_WLAN
netsh wlan show drivers | more /c
netsh wlan show interfaces | more /c
GOTO MENU
:ARP_TAB
arp /a
GOTO MENU
:NS_LKUP
nslookup /ns
GOTO MENU
:SYS_SUM
msinfo32
GOTO MENU
:DNS_FIX
ipconfig /flushdns

ipconfig /registerdns

GOTO MENU
:WINSOCK
netsh winsock reset catalog

GOTO MENU
:FINISHD
EXIT
######################################

```

Specifically look at the Gateway numbers and NetMask;  (255.255.0.0 - 192.168.3.0) as used by Windows

---

### Post by rocky3 on 2017-07-02
John Doe 2,  Thanks for looking at this!   Just to make sure I understand.  
I am going jump on my Windows machine,  
Create a notepad .txt file  under C:\Users\Lori>, 
call it something like "Netfixer"
enter one of the tests such as: 
@echo 0 - PING_LO Ping test to 127.0.0.1
open up a command terminal
go into .txt called Netfixer
run the command @echo 0 - PING_LO Ping test to 127.0.0.1
if this works:  go back into Fixer on note pad and customize with other commands from the menu you provided

thanks

Rocky

---

### Post by johndough2 on 2017-07-02
Hi

I use notepad, copy the text into notepad.  
Check its tidy and save as netfixer.txt.  
Then save as netfixer.bat

Netfixer.bat runs from a command prompt, best as administrator.  You get an on screen menu 0-9 and A-F.

Type your choice, F finishes, so you can select any, all or none.

getmac | more /c
:: getmac >> GetMac.txt
:: Notepad GetMac.txt

ipconfig -all | more /c
:: ipconfig -all >>IP.txt
:: Notepad IP.txt

the double :: colons need to be removed to provide output after you have run it, to prove it's working.

If in doubt please ask.

---

### Post by rocky3 on 2017-07-02
JD2,  I followed your instructions and did the following:

I Ran the Netfixer.bat file and got the 0-9, a-f menu.  THANKS!!
I ran (2) Get_MAC and (3) GET_IPs  (8) NETSTAT (9) SH-WLAN, 
I also ran (A) ARP_TABLE (B) NSLKUP (C) SYS SUM
Then I ran commands you suggested to get an output files on (2) and (3) - see output from files below (or see attached)
Please note, I did not run any of the repair/ reset / nenew commands from Netfixer.bat menu because this windows machine is connecting fine to t the internet through my Eldridge WIFI

What is my next step to troubleshoot to see why UBUNTU won't connect to the internet through a browser using my ELDRIDGE WIFI even though it PINGS fine to both 192.168.3.1 (gateway) and 192.168.3.100 (windows laptop) shown on windows output below?

Please see output from (2) (or see attached) and (3) below:
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

```
Windows IP Configuration

   Host Name . . . . . . . . . . . . : Yvonne
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : ampedwireless

Wireless LAN adapter Wireless Network Connection 3:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter #2
   Physical Address. . . . . . . . . : 60-6C-66-1A-F4-B0
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 60-6C-66-1A-F4-B0
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : ampedwireless
   Description . . . . . . . . . . . : Intel(R) Centrino(R) Wireless-N 2230
   Physical Address. . . . . . . . . : 60-6C-66-1A-F4-AF
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::4834:8413:9b86:9698%19(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.3.100(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, July 02, 2017 1:54:38 PM
   Lease Expires . . . . . . . . . . : Sunday, July 02, 2017 9:54:39 PM
   Default Gateway . . . . . . . . . : 192.168.3.1
   DHCP Server . . . . . . . . . . . : 192.168.3.1
   DHCPv6 IAID . . . . . . . . . . . : 526412902
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-F4-14-0D-B8-CA-3A-D0-29-6F
   DNS Servers . . . . . . . . . . . : 8.8.8.8
                                       8.8.4.4
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network) #2
   Physical Address. . . . . . . . . : 60-6C-66-1A-F4-B3
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek PCIe FE Family Controller
   Physical Address. . . . . . . . . : B8-CA-3A-D0-29-6F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 15:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:9d38:953c:8f3:1b15:bb9b:c054(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::8f3:1b15:bb9b:c054%22(Preferred) 
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter isatap.ampedwireless:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : ampedwireless
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{1ECEFFC9-7FC9-49A2-A132-7D07F0895D19}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{442C6320-362A-406C-BDFD-4FB9ED616328}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{D9FBF773-C1FC-44BA-BC83-7D5C72A444D5}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #5
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{469CA48A-4249-4538-9B90-DE32460E85D9}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx
OUTPUT FROM test (3) GET_MAC

Physical Address    Transport Name                                            
=================== ==========================================================
B8-CA-3A-D0-29-6F   Media disconnected                                        
60-6C-66-1A-F4-AF   \Device\Tcpip_{A76FFA93-FC89-4B5D-8307-024C1DA46FFB}      
60-6C-66-1A-F4-B0   Media disconnected                                        
60-6C-66-1A-F4-B0   Media disconnected                                        
60-6C-66-1A-F4-B3   Media disconnected
```

---

### Post by johndough2 on 2017-07-03
Hi

The IP address 68.105.28.11 belongs to Cox Communications ISP in Atlanta (Georgia, GA), United States (33.7490005493 and -84.3880004883). The hostname is cdns1.cox.net.
United States (United States of America, USA) is a High income: OECD country in North America. The currency is U.S. dollar.

The above is a value in your Ubuntu DNS server.list. [http://www.ipillion.com/ip/68.105.28.11](http://www.ipillion.com/ip/68.105.28.11)
As of Jul 03, 2017 05:16:15 we have 12 complaint(s) about 68.105.28.11. Based on our records, the 68.105.28.11 has been involved in brute force, DDOS, hacking, port scanning, sync flood, etc.


Your Windows ones seem to be 

[http://www.linux-magazine.com/Online/News/Google-Starts-Own-DNS-Service-8.8.8.8-and-8.8.4.4](http://www.linux-magazine.com/Online/News/Google-Starts-Own-DNS-Service-8.8.8.8-and-8.8.4.4)

IPv4 Address. . . . . . . . . . . : 192.168.3.100(Preferred)
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Lease Obtained. . . . . . . . . . : Sunday, July 02, 2017 1:54:38 PM
Lease Expires . . . . . . . . . . : Sunday, July 02, 2017 9:54:39 PM
Default Gateway . . . . . . . . . : 192.168.3.1
DHCP Server . . . . . . . . . . . : 192.168.3.1
DHCPv6 IAID . . . . . . . . . . . : 526412902
DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-F4-14-0D-B8-CA-3A-D0-29-6F
DNS Servers . . . . . . . . . . . : 8.8.8.8
8.8.4.4


######

I would look carefully thru your config / setup values and see if you are pointing to the wrong DNS.

So maybe your WiFi is working and connecting, but to the wrong places.

---

### Post by johndough2 on 2017-07-03
Hi

Much as I would like to help further, I find this microsoft style forum very limiting (FUD and security thru obscurity) I cannot find a way to post screen shots etc.

I know the facility exists, but it is hidden and only obliquely referred to.

So you need to go to your network setting for the WiFi and for DHCP and DNS settings and avoid automatic settings where you can replace with fixed/manual and type in your values.  Include IPv6 just in case, and either disable or set to manual.

Well there may be a viable attachment, but the concept of 'inline' is beyond me.

---

### Post by vasa1 on 2017-07-04
> **johndough2 said:**
> Hi

Much as I would like to help further, I find this microsoft style forum very limiting (FUD and security thru obscurity) I cannot find a way to post screen shots etc.

I know the facility exists, but it is hidden and only obliquely referred to.

...

Well there may be a viable attachment, but the concept of 'inline' is beyond me.

If you need help with a forum feature, post in [Forum Feedback & Help]("https://ubuntuforums.org/forumdisplay.php?f=48"). Although I doubt anyone can help with "I find this microsoft style forum very limiting (FUD and security thru obscurity) I cannot find a way to post screen shots etc."

---

