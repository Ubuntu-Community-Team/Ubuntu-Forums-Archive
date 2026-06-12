---
title: "USB Share only when wifi is offline"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2014-01-29
I have this hardware: pc with 12.04, Netgear N600 router. I am trying to config the Ubuntu to talk with the router. This computer has internet access via wifi only. If the wifi is connected (via Net Mgr) then I cannot access the Netgear webgui (192.168.1.1) and Nautilus shows nothing connected but the Windows folder and it is "Unable to Mount Connection" state.

If I disconnect the wifi, then I can access the Netgear webgui (192.168.1.1). It shows no USB device connected. But Linux/Ubuntu/12.04 cannot "see" it. I know that MS and MAC users have an applet to make these connections, but haven't been able to find one, or a How-To or Tutorial for 12.04.

For clarity's sake: the pc and the router connect to each other via an ethernet cable. The pc has internet access only via another wifi router. That wifi router is also the dsl modem (AT&T). I want to stick to a cable connection for now.

---

### Post by varunendra on 2014-02-01
Maybe outputs of -
```
route -n
```
from both situations could make the situation more clear? Just hoping.., with reference to this : [http://ubuntuforums.org/showpost.php?p=12819114](http://ubuntuforums.org/showpost.php?p=12819114) (not sure if your problem can be related in any way).

---

### Post by Mark_in_Hollywood on 2014-02-04
mark@Lexington:~$ route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

---

### Post by brokenhachi on 2014-02-04
im guessing 192.168.1.254 is the AT&T router? assuming that the netgear and the at&t router are not physically connected, the reason you cannot access the netgear when connected to the wifi is that all traffic is passing to the at&t router, rather than going to the netgear since they both are in the same subnet: 192.168.1.0/24

can you change the subnet on the netgear to 192.168.2.0/24 and see if that works?

---

### Post by Mark_in_Hollywood on 2014-02-05
Thanks for the reply. 

Yes, AT&T.

I have attached a screenshot of the Netgear's interface, showing the LAN configs. It shows that the device has an IP address of: 192. 168.1.1 and also is acting in DHCP Server mode and the address range of: 

192.168.1.2 through .254.

Now I must ask, which (or all) must be set to 192.168.**2**.x, because I already destroyed my entire OS last week, changing these addresses without understanding what I'm doing. So, for completeness sake, I've also attached a screenshot of the WAN settings, too, because I'm not sure what I should change or whether changing the LAN requires changing the LAN or vice-versa.

Many thanks for your support.

---

### Post by fdrake on 2014-02-05
on the ip address field "under lan tcp/ip setup" cange 192.168.1.1  to 192.168.2.1
same for the dafualt DMZ server: 192.168.1.0 to 192.168.2.0

than you'll be able to access your settings from Netgear on 192.168.2.1 and the AT&T on 192.168.1.1.

if you enconter probles for future references just take a pin an press the reset button behind the reouter to go back to default settings.

---

### Post by Mark_in_Hollywood on 2014-02-05
It seems to not have made a difference to change the

192.168.1.1

to

192.168.**2**.1

Is this the IP address that is to change?

I can login to the Netgear web interface (192.168.2.1), but it is still either wired connection (without internet access or wifi with internet but not access to the Netgear web interface.)

See attached screenshots, if necessary.

---

### Post by varunendra on 2014-02-06
I asked for outputs or 'route -n' from both situations. By 'both' I mean once when you are connected to internet, and once from when you are NOT connected to internet and CAN access the USB share.

Comparing these two 'route -n' tables should tell us something that your description can't.

And by the way, your description is confusing -
> If I disconnect the wifi, then I can access the Netgear webgui (192.168.1.1). It shows **[COLOR="#FF0000"]no[/COLOR]** USB device connected. But Linux/Ubuntu/12.04 **[COLOR="#FF0000"]cannot[/COLOR]** "see" it.
Of course the OS won't "see" it if the Netgear shows No USB device connected. A typo? Once or twice?

---

### Post by Mark_in_Hollywood on 2014-02-07
I apologize. There were responses from others and I have become more confused. The first 3 are route -n without the Raspberry PI (Raspbmc) being powered up.

With the computer (Ubuntu) connected to the wifi ('net access, the ISP is AT&T)

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags    Metric Ref       Use    Iface
0.0.0.0         192.168.1.254   0.0.0.0           UG           0      0        0      wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0    0                wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0             wlan0
```

With the computer disconnected from the wifi, and connected to "Wired connection 1" and "Shared to other computers" selected in panel's net mgr.

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0         0.0.0.0         255.255.255.0   U     1        0         0 eth0
169.254.0.0     0.0.0.0         255.255.0.0       U     1000   0        0 eth0
```

With the "Wired connection 1" set to DHCP

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask           Flags    Metric    Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0                 UG          0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0            U        1000   0    0 eth0
192.168.1.0     0.0.0.0         255.255.255.0         U     1      0      0 eth0
```

If I have been unclear, it is due to having no understanding of what I'm doing. What I want to do is have the Ubuntu talk to the Raspbmc via the Netgear N600 (wndr3400v2) router via wired connection, the ubuntu to get to the internet via wifi. The raspbmc has it's own wifi adapter for streaming (Youtube). I assume I'm trying to network _all_ these devices. I'm almost certain of it.

---

### Post by varunendra on 2014-02-08
No problem, your confusion is understandable. But please always use **'Code' tags** whenever posting commands or their outputs. Please follow the **"Using Code Tags"** link in my signature below to see how. Its necessity becomes even more when you are posting things like tabular outputs.

For now, please read the following, and carefully confirm all the questions -

[INDENT]**1.** How many devices we are considering in your problem? I think the following -

[INDENT]**1)** One desktop PC (what are its LAN IPs for both WiFi and Ethernet?)
**2)** One Netgear Router. It is NOT connected to Internet in any way. (What is its LAN IP? Is it connected to the Wireless router in any way?)
**3)** One WiFi Router/Modem. This is the devices that is connected to Internet, and is sharing the Internet wirelessly, not through any cable on the LAN side. (What is its LAN IP?)
**4)** A USB Storage device. It is connected via USB to the Netgear Router, and also has wireless interface. Its storage feature can ONLY be shared via the Netgear Router (is it also connected to the Wifi Router in any way? What is the current use of its wifi interface? Does it matter in our problem in hand?)[/INDENT]

**2.** When you connect to the Netgear via Ethernet, does the WiFi automatically get disconnected? Or have you manually disconnected it while taking the outputs of "route -n"?

**3.** If you manually disconnected the WiFi while taking the outputs, please leave both the Ethernet and WiFi connected, and post the output of "route -n" from that scenario.

**4.** I have asked the above output assuming that _your Final Goal_ is to **be able to access Internet via WiFi, and rest of everything on your LAN via Ethernet**. Please confirm if you want something else.
[/INDENT]

You have already answered a few of the questions above, I just need confirmation - to all of above. Sorry if I seem too confused.

I am quoting below your already posted outputs of "route -n" within 'Code' tags for easy reading. *(Edit : Looks like you had tried some formatting manually. Just copy-paste from terminal within code tags, don't worry how it looks while writing your post, it'll automatically make it exactly as in terminal once posted.)*
> **Mark_in_Hollywood said:**
> 
With the computer (Ubuntu) connected to the wifi ('net access, the ISP is AT&T)
```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref     Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0         0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0         0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0         0 wlan0
```

With the computer disconnected from the wifi, and connected to "Wired connection 1" and "Shared to other computers" selected in panel's net mgr.
```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```

With the "Wired connection 1" set to DHCP
```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask          Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0          UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0      U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0    U     1      0        0 eth0
```

By the way, did you read the entire thread that I linked to in my first post? From what I have understood so far, you seem to be trying to accomplish the same thing - Access internet via WiFi, Access everything else on the LAN via Ethernet -
> **Mark_in_Hollywood said:**
> What I want to do is have the Ubuntu talk to the Raspbmc via the Netgear N600 (wndr3400v2) router via wired connection, the ubuntu to get to the internet via wifi.[COLOR="#FF0000"] The raspbmc has it's own wifi adapter for streaming (Youtube).[/COLOR]
..and How does that wifi adapter in the raspbmc figure in out problem here? Is it something we need to consider in whatever we are trying here? If not, may we safely ignore it while troubleshooting the current problem?

---

### Post by Mark_in_Hollywood on 2014-02-08
Thank you for the help with "Code Tags". I have never seen that before after 5 years on this forum.

There are 7 devices and a network of 4 devices in total. Let me explain. That is: a desktop pc (connects to the internet via wifi due to inaccessibility of cable (cat 5e). The pc must via a separate networking scheme to connect to: a Netgear router (in LAN mode). The router's connections are all via cat5e or for the external usb drive, a usb cable. The router next connects to a Raspberry PI (running Raspbmc media center), again, via cable and lastly, the router connects to a SiliconDust HDHomeRun (ATSC Dual TV Tuner), via cable.

The reason the pc must connect to the router is only to see the webgui's (web interface?) of the router and the Raspbmc's in-built software called: "TVHeadend"). It does not need to have internet access within the media center network. The pc must retain it's wifi network. (as the devices currently exist and are configged: the pc (Ubuntu) gets wifi to the 'net, the remainder: raspberry pi, netgear router, tv tuner, have their own wifi adapter.) Sorry, that sentence is a mouthful. I wish I knew enough to write more simply. In an ideal world of all this, the pc would have it's own, unshared internet access. It's ethernet port would be used exclusively to communicate with the media center and the router. The media center has it's own wifi adapter and can get to the internet (Youtube, Hulu) on it's own, it doesn't need to go to and through the pc.

Then next you ask for the various LAN ip addresses for both wifi and ethernet. 

I have no idea how to find those numbers in an authoritative manner. If I did "ifconfig" I would not know whether those IP's would be for the wifi or wireless version. A quick read at [Network Configuration]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html") gives me a place to start. And, I humbly ask your patience, while I find a way to answer those questions you pose, above this post.

Answering the remainder of what you ask, as best as I can for now:

[COLOR="#FF0000"]2. When you connect to the Netgear via Ethernet, does the WiFi automatically get disconnected? Or have you manually disconnected it while taking the outputs of "route -n"?[/COLOR]

If the panel Net Mgr. has the "Wired Connection 1" set to Ip4V's DHCP, trying to access the 'net disconnects with wifi for the pc in order to use the wired connection to the router. If the panel Net Mgr. has the "Wired Connection 1" set to Ip4V's set to "Shared to other computers", the Network Connections shows both a wired and wireless connection. (current wired ip: 10.42.0.1 - current wifi ip: 192.168.1.81). But to see the router's web interface (192.168.1.1) I have to disconnect the wifi. That the "Wired Connection 1" shows in the panel's Net. Mgr. does but I cannot access the Netgear's web interface. (IP conflict? Subnet conflict?)

Also, I manually disconnected to get the "route -n" data, above post's info.

Per your request for "route -n" with both a wired and wireless connection simultaneously:

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

[COLOR="#FF0000"]1) One desktop PC (what are its LAN IPs for both WiFi and Ethernet?) [COLOR="#000000"]One desktop PC, maybe the attached screenshots give the proper IP addresses.[/COLOR]

2) One Netgear Router. It is NOT connected to Internet in any way. (What is its LAN IP? Is it connected to the Wireless router in any way?) [COLOR="#000000"][COLOR="#000000"]The Netgear Router is NOT connected to the internet in any way. LAN IP - I'm working on that info[/COLOR].[/COLOR]

3) One WiFi Router/Modem. This is the devices that is connected to Internet, and is sharing the Internet wirelessly, not through any cable on the LAN side. (What is its LAN IP?) [COLOR="#000000"]The internet is accessed to the Ubuntu pc, via a wifi router in another room. There is no cable on the LAN side. LAN IP? -- I can't find that in the ATT dsl modem-router-wifi web if (192.168.1254), it only shows data throughput for a LAN.[/COLOR]

4) A USB Storage device. It is connected via USB to the Netgear Router, and also has wireless interface. Its storage feature can ONLY be shared via the Netgear Router (is it also connected to the Wifi Router in any way? What is the current use of its wifi interface? Does it matter in our problem in hand?)[/COLOR] ---- The USB Storage device is connected to the Netgear Router via usb cable. It is not connected via wifi. "What is the current use of its wifi interface?" --- Sorry, I cannot understand what you are asking. If you mean what does the Netgear web interface show about the storage device, it shows it as connected. If you mean does the pc have access to it, I can't answer that just yet, either. I'm too new at this stuff. I would not like a wifi connection to the usb storage device. Things is tough enough already.

Lastly, for now, is it easier to make Ubuntu control all these IP address and networking scheme? The problem to me is, I have Ubuntu up and running. I connect the Raspbmc/PI-router and power it up. The router? tries to issue ip addresses to what it finds, but then, inexplicably, conflicts with Ubuntu. So, I'm either offline with the internet and online with the other devices, or vice-versa.

Trying to get the right combination of wired and wireless (wifi) network settings on the PI last night, it bit the dust and I'll have to reformat the sd card and re-install the raspbmc before I can get those IP addresses.

Seven devices: 2 wifi adapters, 1 pc, 1 router, 1 raspberry pi, 1 tv tuner, 1 usb external hard drive. I sure hope I've given you some help, as you have given me.

---

### Post by varunendra on 2014-02-09
Sorry for the late reply, had to take care of a mountain of laundry at home :P

I think I have 'Almost' enough information now to understand the situation and formulate a solution. Only a couple more things to confirm -

Is the Netgear router setting same as its last screenshot you posted? That is, with IP 192.168.2.1? If yes, please try this and let us know the result -

In Network Manager, select "DHCP" instead of "Shared to other computers", as that option would cause your Ethernet IP change to "Ad-hoc" mode. Let it get its IP from the Netgear router and post back another screenshot of the Network Manager's "Connection Information" when it seems connected (don't worry about the wireless being disconnected at this point).

Along with the screenshot, also post back the output of the following from this situation -
```
route -n
nm-tool
```

Remember - you don't want "Shared to other computers" mode for IP settings.

I hope today I'll have enough time to reply back quicker (going away for about an hour now..).

---

### Post by Mark_in_Hollywood on 2014-02-10
Info from route -n and nm-tool just below the preliminary info.

I have done a hard reset on the Netgear router. As I said in my PM, I had to reformat, re-install and update the entire Raspbmc. That would not happen until the pc's net. mgr. was set to "Shared to other computers". That process eventually allowed the software to call 10.41.0.14 the Raspbmc's IP address. I include this here, not knowing if it matters just yet.

Next, disconnecting the pc from it's wifi (192.186.1.81), enabling "Wired connection1" and establishing a connection to the Netgear (selecting "Wired connection1 and under Ip4V - Method: Automatic (DHCP)  in the panel net. mgr.) shows:

```
IP:      192.168.1.2
B'cst address: 192.168.1.255
Subnet Mask: 255.255.255.0
Default route: 192.168.1.1
Primary DNS: 192.168.1.1
```

with the wired connection active, I have no internet access on the pc. Also, when making the wired connection under Ip4V - Method, I chose DHCP and not Automatic DHCP. Oddly 

 The Raspbmc says that it is internet connected. 

In my pc's browser, calling 192.168.1.1 (Netgear's webgui), I get the wizard/genie page, which, if the router had a wired internet cable available, would auto config the devices for the internet and such. As we are going to config a static IP and etc., I will be choosing the manual setup option pretty soon, but not just yet.

A word about the Raspbmc's "settings". 

Always confusing, the raspbmc shows several IP addresses. In "Settings - Network" the IP is: 192.168.1.89 (and I see this address regularly upon re-install - I'm up to about 25 times). The other infos are:

MAC address: 80:1F:02:B6:B1:50
Subnet mask: 255.255.255.0
Gateway is blank
Primary DNS is: 10.41.0.1
2ary DNS is: 192.168.1.254
and it reports the internet is "connected".

From a different screen within the Raspbmc (xbmc) called:

Network Configuration (Programs / Settings / Raspbmc Settings)

Both wifi and wired show:

Use DHCP
Use Unique DHCP Name
IP: 192.168.1.101
Subnet mask 255.255.255.0
Gateway: 192.168.1.1
Primary DNS: 192.168.1.1

All the foregoing with the pc's wired IP address as: 192.168.1.2.

Then I did the following:

```
mark@Lexington:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

AND

```
mark@Lexington:/$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        40:61:86:06:56:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0  [ATT176] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           no
  HW Address:        90:F6:52:0C:2D:A4

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
     NETGEAR82:       Infra, 9C:D3:6D:A5:43:9F, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2

    *ATT176:         Infra, B0:77:AC:DC:3F:B0, Freq 2427 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2
   
  IPv4 Settings:
    Address:         192.168.1.81
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

with the "Wired connection 1" disconnected and the **wifi connected**:

```
mark@Lexington:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```

AND 

```
mark@Lexington:/$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        40:61:86:06:56:14

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [ATT176] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        90:F6:52:0C:2D:A4

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
   
    NETGEAR82:       Infra, 9C:D3:6D:A5:43:9F, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2
   
    *ATT176:         Infra, B0:77:AC:DC:3F:B0, Freq 2427 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
   

  IPv4 Settings:
    Address:         192.168.1.81
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

```

Lastly, even though this may be irrelevant, when the pc has a "wired" connection, the PI says it has an internet connection - I'm not at all sure this is true. When the pc has a wifi conneciton, the PI says it has no internet connection. 

The Netgear webgui shows the current states as:

```

Router Information
Hardware Version	 WNDR3400v2
Firmware Version	 V1.0.0.44_1.0.71
GUI Language Version	 V1.0.0.44_2.1.28.2
LAN Port	
MAC Address	 9C:D3:6D:A5:43:9F
IP Address	 192.168.1.1
DHCP	On

	Internet Port
MAC Address	9C:D3:6D:A5:43:A0
IP Address	0.0.0.0
Connection	DHCP
IP Subnet Mask	0.0.0.0
Domain Name Server	0.0.0.0

 
Wired Devices
#	IP Address	Device Name	MAC Address
1	192.168.1.2	Lexington	40:61:86:06:56:14
2	192.168.1.3	HDHR-101A799A	00:18:DD:01:A7:99
3	192.168.1.4	xbmc-fbf7	B8:27:EB:30:FB:F7


Internet IP Address
Get Dynamically from ISP 
Use Static IP Address
IP Address	... 0.0.0.0.
IP Subnet Mask	... 0.0.0.0.
Gateway IP Address	... 0.0.0.0
 
Domain Name Server (DNS) Address
Get Automatically from ISP
Use These DNS Servers
Primary DNS	... blank
Secondary DNS	... blank
 
Router MAC Address not in use
Use Default Address not in use
Use Computer MAC Address not in use
Use This MAC Address not in use

**WAN Setup**

 Disable Port Scan and DoS Protection
 
 Default DMZ Server	... 192.168.1.0
 
 Respond to Ping on Internet Port
 
 Disable IGMP Proxying
 
 MTU Size(in bytes)	
 
 NAT Filtering	Secured  Open
 Disable SIP ALG	


**LAN Setup**

LAN TCP/IP Setup

IP Address	.  .  .  192.168.1.1
IP Subnet Mask	.  .  .  255.255.255.0
RIP Direction	          both
RIP Version	          disabled
 
 Use Router as DHCP Server
Starting IP Address	.  .  .  192.168.1.2
Ending IP Address	.  .  .  192.168.1.254
```

---

### Post by varunendra on 2014-02-11
For sake of clarity and simplicity, let's keep the xmbc (Raspberry Pi) machine out of our equation, we can deal with it later if required.
For now, I am talking about only three devices -
1) The PC with Ubuntu that we are working on
2) The Netgear router
3) The wifi router

And my suggestion is based on assumption that this -
> **Mark_in_Hollywood said:**
> 
```
mark@Lexington:/$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

```
..was the output from Ubuntu when the Wired connection was set to DHCP.

Now, please do the following in the above same situation (both Wired & WiFi connected, Ethernet set to DHCP) -

**1)** In the Network Manager settings for the **Wired connection**,
go to **"IPv4 Settings" tab > make sure the "Method" is set to "Automatic (DHCP)" > click on "Routes..." button > put a Tick in both check-boxes *("Ignore automatically obtained routes" and "Use this connection only for resources on this network")* > click "Ok" > "Save" > "Close"**. Reboot if required.

If this solves the problem, Stop here, test whatever you want to and post back whatever else you want to achieve. If the problem persists, follow the next points below -

**2)** If the above alone doesn't help connecting to Internet, while being able to access the router's webgui, run "route -n" command and copy its output > keep safe for posting here.

**3)** Run the following commands in a terminal -
```
sudo route del default
sudo route add default gw 192.168.1.254
sudo route add -host 192.168.1.254 wlan0
```
..then run the "route -n" command again. Post back this output as well as the one saved in point 2) above, and clearly mention which one is from when.

Apart from this, please also post a link to the user manual of your router, so that I can see if it is possible to configure your DHCP correctly if required. Keep in mind that I have a gprs connection which doesn't go above 4-5 KB/s speed (so if possible, don't give me a 'heavy' link :P).

---

### Post by Mark_in_Hollywood on 2014-02-11
Upon booting up the pc:

```
mark@Lexington:~$ route -n **[this is wifi ONLY]**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

Next, clicking the Net. Mgr's. "Wired connection 1" 

```
mark@Lexington:~$ route -n **(with both wifi and wired)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

Following via copy & paste:

```
mark@Lexington:~$ sudo route del default
[sudo] password for mark: 
mark@Lexington:~$ sudo route add default gw 192.168.1.254
mark@Lexington:~$ sudo route add -host 192.168.1.254 wlan0
```

and then running:

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.254   0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
```

Trying to be clear, in the steps, I followed:

While wired is disconnected, I ran the del and add commands, as above, via copy & paste. After running those commands, in Net. Mgr., I selected "Wired connection 1". Next looking at Connection Information, I see both a wired and wifi connection with the following info:

WIFI's IP Address: 192.168.1.81

and

Wired's IP Address: 192.168.1.4

**the above is seen before a reboot**

and route -n in this state shows** before the reboot**:

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.254   0.0.0.0         255.255.255.255 UH    0      0        0 wlan0
```

While in this state, I have both access to the Netgear's webgui (192.168.1.1) as well as internet access for my desktop pc. (192.168.1.81).

For Reference the Netgear N600 (WNDR3400v2) Manual in .pdf is:

[https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CCcQFjAA&url=http%3A%2F%2Fwww.downloads.netgear.com%2Ffiles%2FGDC%2FWNDR3400V2%2FWNDR3400v2_UM_03APR2012.pdf&ei=UWH6UoifOKOiyAH0-ICwDA&usg=AFQjCNEFlq_IDMVHsS4SHvyOCmO2PXiBJg&sig2=TULxt5SVVTPQDaEGHyd5ww&bvm=bv.61190604,d.aWc](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CCcQFjAA&url=http%3A%2F%2Fwww.downloads.netgear.com%2Ffiles%2FGDC%2FWNDR3400V2%2FWNDR3400v2_UM_03APR2012.pdf&ei=UWH6UoifOKOiyAH0-ICwDA&usg=AFQjCNEFlq_IDMVHsS4SHvyOCmO2PXiBJg&sig2=TULxt5SVVTPQDaEGHyd5ww&bvm=bv.61190604,d.aWc)

Configging LAN and WAN manually starts on page 37. May I suggest I copy & paste whatever you need? Otherwise the size of the .pdf is 6.2 meg. (that's about a 20 minute download).

**Next another reboot.**

Connection Information shows a WiFi connection IP address as: 192.168.1.81 and a wired connection IP address as: 192.168.1.4

The panel's Network Manager icon shows the wifi icon and a signal strength of 3, yet there is no internet access. I tried both pinging yahoo.com, google.com and calling some pages from within my browser with no returns. Next I opened the panel manager and selected my wifi SSID. A moment later the OSN (on-screen notification) reported that the wifi is disconnected, even though the panel shows the wifi icon (and signal strength of 3). Still no internet access.

Next, trying disconnecting the wired network. The OSN confirms the disconnected state. I am now able to access the internet and ping yahoo.

**With wifi only:**

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

**With BOTH wired and wifi connected**

```
mark@Lexington:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

I have put my heart into following your instructions and believe I have not made any mistakes, but I am human.

--- a few hours later ---

I tried to ssh into the raspbmc, only to find "no route to host", so I disabled the wifi, re-enabled the wired only to find "no route to host". So I reset the "Wired connection 1" to "Shared to other computers", rebooted, ssh'd into the PI, copied some files over to the PI, exited ssh, reset the "Wired connection 1" to Automatic (DHCP) and can now be networked with the router via wired, but cannot be internet connected as above and only put this here -just in case it matters- therefore:

```
mark@Lexington:~$ route -n **(wifi only)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
mark@Lexington:~$ route -n **(wired only)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
mark@Lexington:~$ route -n **(BOTH wifi and wired)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

So, it's still either/or. Either wifi or wired, but not both simultaneously.

---

### Post by varunendra on 2014-02-11
Okay, so far we seem to be on the right track, the situation being probably exactly the same as I suspected, and thus the solution being the same as well. I'm still keeping the Raspberry Pi out of the equation, we'll deal with it later.

Supported by the last outputs of "route -n" I trust that you have correctly set the "Routes..." button options as I suggested, and no additional steps were required to make the Gateway "192.168.1.254" in the last output. That's exactly what we want.

Now before I proceed to further instructions, some explanation so you know what is happening and what we need *(for quick explanations and better understanding of the terms used, please read the initial part of the post I linked to in my first post)* :

When both ethernet and wifi are connected, your current routing table is like this (quoting one of them) -
```
mark@Lexington:~$ route -n (BOTH wifi and wired)
Kernel IP routing table
Destination     **[COLOR="#006400"]Gateway[/COLOR]**         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         **[COLOR="#006400"]192.168.1.254[/COLOR]**   0.0.0.0         UG    0      0        0 **[COLOR="#0000CD"]wlan0[/COLOR]**
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
**192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 [COLOR="#FF0000"]eth0[/COLOR]**
[COLOR="#0000CD"]192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0[/COLOR]
```
In the first route, the gateway is now 192.168.1.254 - this is your WiFi router's IP address, hence the correct one to reach the Internet.

However, in order to reach the gateway (and hence the Internet), the gateway MUST be accessible first. Means, we MUST have a ROUTE to reach the gateway. Do we have it? Let's see...

Further down, we see that there exists a route to the NETWORK 192.168.1.0. It being a network means all the devices having IP **192.168.1.[COLOR="#006400"]xxx[/COLOR]** type address (hence 192.168.1.264 too) can be reached via THIS ROUTE. So it seems that we do have a route to reach the gateway, BUT CAN WE really??

The answer is - No, because this route is using the interface **[COLOR="#FF0000"]eth0[/COLOR]**, which is not connected to the **[COLOR="#006400"]gateway[/COLOR]** (the WiFi router). Instead, it is connected to the Netgear router (whose IP is 192.168.1.1), and the Netgear router doesn't know how to deliver the packets to the gateway because it itself is not connected to it. So all traffic that tries to reach the gateway, tries to go through eth0, but eth0 has no way to deliver the packets to the gateway. Result - a black-hole where all traffic to internet goes, but gets lost then.

To reach the gateway, we must set up the route to use the interface wlan0 instead, which is directly connected to the gateway (the wifi router) and thus can deliver the packets. Do we have such a route?

Yes, looking further down, we do have the same route again, using interface wlan0 this time. But if two duplicate routes are present simultaneously, which one the OS should prefer? Preference is simple - whichever is higher in the routing table (considering "Higher" as "Preferable").

The result is that everything that is connected to the Netgear router plus the router itself is accessible, but the Internet gateway (the Wifi router) is not. In this situation, you are able to access the Netgear's webgui, but not the internet.

To make it clear with a quick summary here's your last observation (with my comments) -
```
mark@Lexington:~$ route -n **(wifi only)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0    *[COLOR="#0000CD"]<---- Gateway is accessible via wlan0[/COLOR]*
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0    *[COLOR="#0000CD"]<---- Route to network is using wlan0 # Internet - Success # Netgear webgui - Fail ![/COLOR]*
mark@Lexington:~$ route -n **(wired only)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0    *[COLOR="#0000CD"]<---- Route to network is using eth0 # Netgear webgui - Success # Internet - Fail ![/COLOR]*
mark@Lexington:~$ route -n **(BOTH wifi and wired)**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0    *[COLOR="#0000CD"]<---- Gateway CAN be accessed via wlan0[/COLOR]*
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0    *[COLOR="#0000CD"]<---- But the _preferred_ route is via eth0 # Netgear webgui - Success # Internet - Fail![/COLOR]*
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0    *[COLOR="#0000CD"]<---- Duplicate of above route, lower in list # Hence Ignored/useless[/COLOR]*
```


**_So What Do We Need To Do_ ?**

To keep the Netgear webgui and the USB connected to it accessible, we need to keep the route via eth0 the preferred one. Fortunately, that is already being done automatically. Unfortunately, it won't allow us to connect to the internet, UNLESS -

Either we change the subnet of one of the routers, as was originally proposed by others in the beginning of the thread, OR..
We define route specific to the Gateway Host (Host = a particular device on the network), not the whole network.

The former (change the subnet of one of the routers) is the standard practice, may require changing some configurations of each connected device if has been done manually.

The latter (add a route specific to the gateway) is a non-standard, but quick solution. May require some manual tweaking, but only on the Ubuntu PC.

So.. which one do you prefer?
If the former one, which of the router would you prefer to change settings of?
If the latter one, it is as easy as running the command (on Ubuntu) -
```
sudo route add -host 192.168.1.264 wlan0
```
We'd just have to find a decent way (I already have crude ones) to make this automatic at startup.

---

### Post by Mark_in_Hollywood on 2014-02-12
I took the chance that resetting the Netgear's Server and DMZ settings to **192.168.2.1** would help. It does. I have both internet access for my pc. I have Netgear's webgui simultaneously. I have ssh into the Raspberry PI/Raspbmc. 

For Reference:

Raspbmc's IP address is: 192.168.2.4 (sort of a default it selected at change of Netgear's sub-net address to ".2").

I cannot get the Raspberry PI/Raspbmc access to the internet via it's own, separate wifi adapter.

To reiterate, this network has 2 routers and 2 wifi adapters. One router is for obtaining internet access for my desktop pc. The other router is for networking the media center devices and the computer for interfacing to the media center.

BUT WHOA a moment -

While I configged more settings, trying to get this network setup, I had several reboots. After those reboots, I cannot have both internet access and wired (non-internet) access simultaneously after all. On a re-boot, the wifi comes up on the pc, but the Netgear network is missing, unless, I call the Wired connection 1 from the drop down list on the panel.

What I do have, after re-establishing a wired conneciton is access in both Raspbmc and on my desktop pc of the files in the usb connected to the Netgear router via a usb cable. (smb://readyshare/USB_Storage/videos or /music). Clicking the file name from within Nautilus calls the video player or music player. And in RaspBMC I can find a list of the movies and music.

---

### Post by varunendra on 2014-02-12
At the first glance, I thought the thread is [Solved] now. But reading it carefully, it seems it is not yet? -
> **Mark_in_Hollywood said:**
> Raspbmc's IP address is: 192.168.2.4 (sort of a default it selected at change of Netgear's sub-net address to ".2").

I cannot get the Raspberry PI/Raspbmc access to the internet via it's own, separate wifi adapter.

I have no experience with Rasbpmc, so I'd need your help regarding the configuration of its interfaces. For that, I need to know -

[LIST]
[*]What kind of OS is running on it?
[*]How do you configure its network interfaces? Is there a comprehensive guide which maybe you can give me link of?
[/LIST]

What we need to achieve in order to grant it access to internet is to configure its wifi interface to use an IP of the pattern **192.168.[COLOR="#006400"]1.xxx[/COLOR]**, and use the IP **[COLOR="#006400"]192.168.1.254[/COLOR]** as its (only or preferred) gateway.

If DHCP is enabled in the WiFi gateway (the wifi router) this should be automatic once we just tell it to use the other subnet for wifi, otherwise we should be able to do this manually.

I hope this one is going to be a quick one. :)

---

### Post by Mark_in_Hollywood on 2014-02-12
> **varunendra said:**
> At the first glance, I thought the thread is [Solved] now. But reading it carefully, it seems it is not yet? -


I have no experience with Rasbpmc, so I'd need your help regarding the configuration of its interfaces. For that, I need to know -

[LIST]
[*]What kind of OS is running on it?
[*]How do you configure its network interfaces? Is there a comprehensive guide which maybe you can give me link of?
[/LIST]

What we need to achieve in order to grant it access to internet is to configure its wifi interface to use an IP of the pattern **192.168.[COLOR="#006400"]1.xxx[/COLOR]**, and use the IP **[COLOR="#006400"]192.168.1.254[/COLOR]** as its (only or preferred) gateway.

If DHCP is enabled in the WiFi gateway (the wifi router) this should be automatic once we just tell it to use the other subnet for wifi, otherwise we should be able to do this manually.

I hope this one is going to be a quick one. :)

Preliminary findings:

1 - The OS is a stripped down version of Debian. By stripped down I mean Raspbmc has no X-Server. Because the R PI has it's own GPU, the Raspbmc drives the TV/Monitor via HDMI. 

2 - the Raspbmc has a Settings "page". On that page, the Wired and/or Wifi can be configured to use DHCP and Unique DHCP name or can be configured to (what I will call) "static" addresses. By "call" I mean that the Settings page and the System page often show different IP addresses for the same Wifi or Wired net address (or so it seems to me.)

Yet, rather than use more of your time, if this doesn't go quickly, say no more than one or two more posts by us, that we call it good and I will try to get help at the Raspbmc forum instead. Yay or Nay?

---

### Post by varunendra on 2014-02-12
Yay from me. No problem replying as long as it goes beyond my understanding and so far it hasn't.

But I just noticed your "WHOA" moment in the previous post. Is the simultaneous access broken again? If so, current output of "route -n" and "nm-tool" with both connected?

Or it fixed itself and we should focus on the Raspbmc?

---

### Post by Mark_in_Hollywood on 2014-02-13
Editing some of the screenshots I made a mess of it. Two are attached which show the current state of Networking.

Upon cold boot this morning, I have access to the Netgear (192.168.2.1), and I have access to the external USB connected hard disk drive plugged into the router, too.

This is my preliminary understanding of what this stack of stuff is doing or trying.

The raspbmc wants to use the Netgear router. Very much does raspbmc want to use that router. I have tried several methods of configging, with DHCP and DHCP Unique Name and then with one or the other of those. I have tried to assign IP addresses and Gateway addresses and DNS Server addresses. That is I have tried to set the IP, Gateway, and DNS with and without using DHCP.

All that results in is the Raspbmc reporting: "Not connected to the internet" or staying on "Busy", where the IP, Gateway, and DNS Primary and Secondary servers cannot get online.

Attached are screenshots of the Network Configuration in it's current state.  The first one shows the WiFi settings. It is a hybrid of xxx.xxx.xxx.xxx as I set a static IP for the wifi and then re-enabled DHCP and Unique Name.

The third screenshot shows what the PI has for for it's IP address (192.168.1.111) but from the 3rd screenshot you can see that the MAC address is labeled: busy and the IP is with the Negear's subnet of ".2", so I'm not able to disable the wired networking part of the PI and connect to the wifi. Talking with a nerd, here, he says set the Primary DNS to 8.8.8.8 and 2ard to 8.8.4.4 (Google's DNS numbers). I have tried to set he Pri DNS to 8.8.8.8 but that doesn't connect me to the internet, either.

So, to review:

The Raspbmc (Raspberry PI) has selected some of it's own configurations and currently the WIRED state is set as:

MAC Address is all zero - this is a feature under development. Not showing in this window is not more than window dressing, I'm told by the developer of raspbmc.
Use DHCP - not enabled
Unique DHCP Client name: Enabled
IP Address: 192.168.2.22
Subnet Mask: 255.255.255.0
Gateway: 192.168.2.1
DNS Server: 192.168.2.1

Wireless (WiFi)

Use DHCP - Enabled
Unique DHCP Client name: Enabled
IP Address: 192.168.1.111
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.254
DNS Server: 192.168.1.254

The Network Information Screen (3rd last screenshot) has:

Link: Connected
MAC address: Busy
IP address: 192.168.2.22
Subnet Mask: 255.255.255.0
Gateway: 192.168.2.1
Primary DNS: 192.168.2.1
Secondary DNS: -blank-
Internet: Busy

When the Raspbmc has an internet connection, rather than "Busy" it reads: "Connected" - I have seen this in prior installations of the raspbmc.

The words in the left hand column of the screenshots, are for different information and not relevant to networking. These screenshots are from the "Network" page of information. I apologize the the blurriness, I had to take photographs of this as there is not a template for them I can find using Google's "Image" search.

Next, I tried to change some of the Wired and Wireless settings. Those changes seems to have had little or no effect on getting online via wifi. I have attached a second set of screenshots to show that.

---

### Post by varunendra on 2014-02-14
Try manual (No DHCP) IP configuration for the Ethernet _WITHOUT Gateway and DNS_. That is, assign only IP (**192.168.[COLOR="#006400"]2[/COLOR].xxx** type) and Subnet (255.255.255.0) to the Ethernet interface.

For WiFi interface, keep DHCP enabled, don't do anything manually in it. Here I am assuming that DHCP 'Server' is enabled in your wifi rotuer which is able to do its job and the Raspbmc can get its IP, Subnet, Gateway and DNS via that DHCP, you don't have to configure it manually (if you have to, configure ALL these fields for the WiFi).

With two gateways defined (both for ethernet and wifi), the Raspbmc is probably trying to use the one that looks faster (obviously the Ethernet). When it will have only one (the WiFi), it should only that one.

Let me know if that lets it connect to the Internet.

Assuming this should work, you may have to re-configure the DHCP range of the Netgear router to 'EXCLUDE' the IP which you assigned to the Raspbmc, otherwise IP conflict may occur at times and you may not be able to access the PI via ethernet.

---

