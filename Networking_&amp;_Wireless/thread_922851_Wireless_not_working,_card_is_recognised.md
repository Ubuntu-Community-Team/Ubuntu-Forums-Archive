---
title: "Wireless not working, card is recognised"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by vikpaul on 2008-09-17
Hi,

I have an IBM Lenovo laptop. The wireless card is
atheros. The router is NETGEAR. I have Ubuntu 8.04 as
my OS (I also have Windows XP as a virtual machine, but
I dont think this is an issue; I dont start the virtual machine; so only Ubuntu is active.) My internet provider is COMCAST.

My status is as follows:

Wired connection works i.e. I can use internet. But if I use the NETGEAR router
then the wireless does not work. I am pretty sure that
card is recognised and most probably I have the correct driver.
This is because I can see the wireless icon in the top right
of screen. When I click on this icon I can see NETGEAR as one
of the available options and the signal strength is very good.
But the internet does not work. I have used the System>Administration>Network
to configure the wireless.

In the "Network" window I can see the "wireless" and "wired" options.
I click on wireless and click on properties. Here there are as
such 3 options - 
(1) roaming
(2) another one where you choose ESSID, WPA etc
(3) Static IP

I dont want Static IP so that is ruled out. If I enable "roaming"
then other 2 options are not highlighted. But enabling roaming
does not work i.e. I dont get internet. So I configured by
choosing NETGEAR in the dropdown menu of ESSID. Questions are:

*Should I choose WPA, WPA2 ? 
*What should I put in the password field? Is this password something I should ask for from NETGEAR?
*Does making the wireless work involve "configuring" the NETGEAR
router ? I found this link:
[http://kbserver.netgear.com/kb_web_files/n101675.asp](http://kbserver.netgear.com/kb_web_files/n101675.asp)
From this website I understand that some "configuring" is needed
and then you use the same "configuration details" when you try
to connect to wireless i.e. the password etc that I put int
the "network" window has to be consistent with the configuration
of the router.
*Does making wireless work involved changing the DNS servers in
the "DNS tab"? I found a post this forum which suggested that
changing the DNS server in accordance with that found on 
[https://www.opendns.com/homenetwork/start/device/netgear](https://www.opendns.com/homenetwork/start/device/netgear)
should work.
*By reading the information I have given can it be said for
sure that my wireless card is being recognised by the laptop
and my driver is working? The "wireless indicator" on my IBM
laptop does not turn on. By the "wireless indicator" I mean
the indicator at the bottom of the monitor (not an icon on the
screen). This indicator used to switch on when I used the Windows
operating system (before I loaded Ubuntu my laptop had Windows
on it; Now I have Ubuntu and Windows as VMware).
*In the "Network window" should I disable the "wired connection"
option? Or is it ok to enable both "wired" and "wireless" option.

Thanks

---

### Post by funkydan2 on 2008-09-18
I think that you're best off leaving everything set to 'roaming' mode in the System->Administration->Network settings.

Then, to connect to a wireless network left-click on the network manager icon in your system tray (this is usually in the top right of your screen and looks like a picture of some computers).  In the menu that appears, click to select the wireless network you want to connect to (in your case, NETGEAR).  If this network is password protected, you'll then be asked to enter the password/key, which is either something that you've already setup on your router, or maybe is a default password (which will be in the manual).  Then your machine should simply log onto the wireless network and if the router is set up correctly, you'll be on the internet.

(BTW, if you live around lots of other people, it's possibly a good idea to give your wireless a less generic name and to change the wireless key from the default or else you may find that you're helping giving free internet access to your neighbourhood.)

---

### Post by tachyon4 on 2008-09-18
I have a similar problem.

Previously, my card was NOT recognized.  I installed new firmware and now that problem is solved.  But now I have a new problem (didn't happen before):

In the "network" menu I only see the "wired" option.  I can't change any of the settings for "wireless" because the option doesn't exist.

Any tips?  Thanks.

---

### Post by funkydan2 on 2008-09-19
@tachyon - if there aren't any wireless networks listed how do you know that your wireless care is working?  (Sorry, that sounded antagonistic when I re-read it.  My question is what things show you that your wireless card is working?)  What's the output of commands like 'ifconfig' and 'iwlist scan' at the command prompt?

---

### Post by djjonex on 2008-09-19
I think your problem is that  you have to add the network macadress to the router....... Do that and then tell me!

---

### Post by tachyon4 on 2008-09-20
I suppose I don't know it's "working," but some things did change when I added new firmware.

As a Ubuntu n00b, I'm afraid I'm mixing up terminology.  Here's my best explanation: I downloaded, extracted and installed ndiswrapper.  Using "gksudo nautilus," I edited "etc/modprobe.d/blacklist" to include "blacklist bcm43xx," "blacklist b43" and "blacklist ssb."  I rebooted.

Here's what changed: the network icon changed from a picture of two monitors to a picture of two monitors and an orange triangle with an exclamation point on it.  Also, I can now use "windows wireless drivers" in the "administration" menu.  In "wireless network dirvers," I see "bcmwl5" (one of the files I installed) listed in the text field.  A note says "hardware present: Yes."  That's all I know.

"ifconfig" yields...

```

eth0      Link encap:Ethernet  HWaddr 00:1b:24:ae:17:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9700 (9.4 KB)  TX bytes:9700 (9.4 KB)


```

"iwlist scan" yields...

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

FYI, on Vista (did i mention I'm dual-booting?), which works fine, I ran "ipconfig/all" and got...

```
Windows IP Configuration

   Host Name . . . . . . . . . . . . : Alex-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : home

Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : Broadcom 802.11a/b/g WLAN
   Physical Address. . . . . . . . . : 00-1A-73-8F-CE-06
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::51d3:de97:6232:6018%12(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.6(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Friday, September 19, 2008 3:52:52 PM
   Lease Expires . . . . . . . . . . : Saturday, September 20, 2008 8:39:29 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 00-1A-6B-F2-60-7A
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : dsl.integraonline.com
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-1B-24-AE-17-55
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.dsl.integraonline.com
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.{ADA8B624-A980-4ED2-B711-BA56C75EC84F}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 10:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 12:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:834:36c7:3f57:fef9(Preferred) 
   Link-local IPv6 Address . . . . . : fe80::834:36c7:3f57:fef9%13(Preferred) 
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 13:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : isatap.home
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
```

I hope this helps.  I'm not sure which MAC address to add to the router.  The ethernet "HWaddr" and "Physical Address" are the same.  But I think I want "LAN," not "ethernet," yes?

:confused: I'm a bit confused, and I really appreciate the help. :)

---

### Post by funkydan2 on 2008-09-20
From the output of ifconfig it appears that your wireless card isn't properly setup yet.  Unfortunately I haven't used ndiswrapper for a while, so I've forgotten how to do this.  Have you looked at the [wiki](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)?  From your description you may have not done step 3.5, and also you may not have blacklisted all the required modules (3.1).

---

### Post by tachyon4 on 2008-09-20
I found an ethernet cable and connected to the internet that way.  I updated my files and rebooted.  I redid what I did before.

And it worked wirelessly!

As far as I know, everything is working as it should.

Thanks everyone.

---

### Post by HeronLover on 2008-09-25
I am having a similar problem.  after loading Hardy on my laptop only eth0 wired connection would work.  after further reading through the forums I found out that Broadcom 802.11 cards are somewhat of a pain in Ubuntu.  After hours of twiddling and following many ndiswrapper tutorials Hardy will recognize the card.

I could not manually configure the wireless card using the settings given by my ISP.  I then switched to roaming mode and selected enable wireless in network manager.  Now i can see the wireless indicator and enter the pass phrase.  I can also click the indicator and see a list of wireless networks in my apartment, and various neighbors.

I am connected to my network with 95% signal strength.  I open firefox and attempt to get to google and i get the unable to retrieve error message.  Used the opendns settings as mentioned above still unable to connect.

In the terminal i have tried:
wget google.com
host google.com
ping google.com
dig google.com

each command comes up nil.  (My apologies im not using my Ubuntu machine right now so i don't know the exact output for each command.)

I'm close to going wireless if anyone has any further suggestions i would be greatly appreciative

---

### Post by funkydan2 on 2008-09-29
Why do you need to use opendns?  If your router is setup correctly it should tell your ubuntu laptop what DNS servers to use (which I think will either be a small DNS cache sitting in the router or redicted straight through to your ISP).

---

