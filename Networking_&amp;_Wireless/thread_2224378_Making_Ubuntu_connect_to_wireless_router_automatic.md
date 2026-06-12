---
title: "Making Ubuntu connect to wireless router automatically"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by mikeavison on 2014-05-16
Hi
I am trying to get my laptop to connect to my wireless router _automatically_ on start up.
-------------

The Ubuntu version is 12.04

I can connect to the router OK but, every time I power up, I have to go into: system settings / network / wireless / network name = other / connection = (my ssid) / connect (and it connects fine). The latter dialogue box is headed "Hidden Network" but my router is not set to hidden it is set to broadcast.see....

==============================================================

My router is a TP-Link TD-W8951ND

Here are the main wireless settings on my router:
Access point = activated
channel = 06
transmit power = high
beacon interval (ms) = 100
RTS/CTS Threshold = 2347
Fragmentation Threshold (bytes) = 2346
DTIM = 1 ms
Wireless mode = 802.11b+g+n
Channel bandwidth = 20/40 MHz
Extension channel = below the control pannel
Guard Interval = auto
MCS = auto
SSID Index = 1
Broadcast SSID = yes
Use WPS = yes
WPS state = configured
WPS mode = PBC
Authentication type = WPA-PSK/WPA2-PSK
Encryption = AES
WDS mode = off

============================================================

The laptop is an Acer Extensa 5220 which has an on-board Broadcom 4311 wireless card. Its running Ubuntu 12.04 LTS

============================================================

The network settings in Ubuntu are as follows:-

Wireless...
Connect Automatically = ticked
Mode = infrastructure
BSSID = blank
MTU = automatic
Available to all users = ticked

IPv4 Settings...
Methos = Automatic (DHCP)
all the rest geyed out and blank

IPv6 settings...
method = Automatic
Requires IPv6 settings for this connection to complete = not ticked

Wireless security... 
WPA & WPA2 Personal

=============================================================

Once I connect it works fine. Ubuntu has rememebered the password for the netrwork, I don't have to re-type it.

Several other devides in the house connect automatically to the wireless router automatically without problem:-
Internet Radio, 2x Android phones, an Android tablet.

I think this laptop even did before I wiped the old version of Ubunto and put on 12.04 (although I changed the router about that time so I am not 100% certain.

I can't think of any other background information but if there is anything I should have added please let me know

Best Wishes and thanks,

Mike A

---

### Post by mikeavison on 2014-05-25
Further info: I have swapped the router for a different model (Huahei) the problem remains the same.

The basic problem seems to me to boil down to Ubuntu thinking my network is hidden when it isn't. Am I right in thinking that the thing that makes a network not hidden is that it periodically broadcasts it's SSID? If so I guess the service in Ubuntu which looks out for SSID broadcasts is not running? Is there a way of checking this?

In practical terms I can see 2 possible routes to a fix/workround. 
1 Make Ubuntu recognise my network as not hidden or 
2 Configure Ubuntu to connect to a hidden network automatically. (May be easier?)

Can anyone suggest how I could achieve either of these?

Thanks

Mike A

---

### Post by gordintoronto on 2014-05-25
If you click on the network icon, does your router show up? The vast majority of Ubuntu users do not experience your issue.

---

### Post by mikeavison on 2014-05-26
Thanks for the reply Gord, I gathered that most users do not have this problem. I don't know why I do... I did have a lot of trouble getting Ubunto to install the correct drivers for my wireless card (Broadcom) and only managed it thanks to the help from this forum. Maybe during that process the default connection behaviour changed inadvertantly ?? The only other change I have made to the system is downloading Gnome classic desktop (aka fallback).

To answer your question...

No usually when I click on the icon I just see ticks against :
-enable wired network 
-enable wireless network

and there are lines:

-connection information (greyed out)
-edit connections

Sometimes after a while I get additional options:
-connect to hidden wireless network
-create new wirelss network
-VPN connections

I used "edit connections" to add my wireless network credentials. Then when I click "connect to a hidden network" I see my network on the drop down list (its the only entry of course)

I haven't tried dabbling with "create new wireless network" because I think this is an option to make the laptop act as something like a proxy server for other computers (??). Also not touched "VPN connections" as I think that is irrelevant too.

Mike A

---

### Post by Hadaka on 2014-05-26
hi, try these settings

8.8.8.8,8.8.4.4 < Google

[ATTACH=CONFIG]253455[/ATTACH][ATTACH=CONFIG]253456[/ATTACH]

---

### Post by mikeavison on 2014-05-26
Thanks Hadaka but I am afraid these sttings made no difference

Mike A

---

### Post by gordintoronto on 2014-05-26
Simple answers first: "create a wireless network" turns your computer into a Wi-Fi hotspot, not what you want. Likewise, VPN is for accessing remote computers, or having remote computers access yours. (I have complete access from home to all the computers at my office thanks to VPN. Lets me do updates and software installs in the late evening.)

What is the SSID of your network? I have found that having a complex SSID can cause grief. A simple name, up to eight characters with lower-case letters and numbers makes life simpler -- and not just in Linux.


> **mikeavison said:**
> ... I did have a lot of trouble getting Ubunto to install the correct drivers for my wireless card (Broadcom) and only managed it thanks to the help from this forum. Maybe during that process the default connection behaviour changed inadvertantly ?? The only other change I have made to the system is downloading Gnome classic desktop (aka fallback).

To answer your question...

No usually when I click on the icon I just see ticks against :
-enable wired network 
-enable wireless network

and there are lines:

-connection information (greyed out)
-edit connections

Sometimes after a while I get additional options:
-connect to hidden wireless network
-create new wirelss network
-VPN connections

I used "edit connections" to add my wireless network credentials. Then when I click "connect to a hidden network" I see my network on the drop down list (its the only entry of course)

I haven't tried dabbling with "create new wireless network" because I think this is an option to make the laptop act as something like a proxy server for other computers (??). Also not touched "VPN connections" as I think that is irrelevant too.

Mike A

---

### Post by mikeavison on 2014-05-28
Hi Gord

My SSID is just a 6 letter lower case word (edimax). So I don't think that is the problem?

Thanks

---

### Post by mikeavison on 2014-05-29
Hi again, searching the internet I found this suggestion

[http://askubuntu.com/questions/355522/ubuntu-12-04-thinks-my-wireless-network-is-hidden-but-its-not](http://askubuntu.com/questions/355522/ubuntu-12-04-thinks-my-wireless-network-is-hidden-but-its-not)

I am a bit nervous about trying it since it took me ages to get my wireless card working with the correct driver, I definietly don't want to screw that up again! And the person posting that link does not seem very sure as to why it should work.

Should I try it?

---

### Post by Harsh_Parikh on 2014-05-29
> **mikeavison said:**
> 

UseThe network settings in Ubuntu are as follows:-

Wireless...
Connect Automatically = ticked
Mode = infrastructure
:o[COLOR=#ff0000]**BSSID = blank**[/COLOR]:o
MTU = automatic
Available to all users = ticked

Mike A

What is that...???
why the BSSID is blank......
It should be your wireless access point's MAC address.....

---

### Post by mikeavison on 2014-05-29
Well I don't know I just found it on the internet, I don't understand it either.

However since then I tried this

[http://dirtycoding.blogspot.co.uk/2011/12/easy-way-to-auto-connect-to-hidden.html](http://dirtycoding.blogspot.co.uk/2011/12/easy-way-to-auto-connect-to-hidden.html)

and wheyhey it works.

Its not perhpas a real fix since Ubuntu still wrongly regards my network as hidden. This fix just automatically connects to a hidden wireless network, but it providrs a practical solution.

Should I close this as solved now?

---

### Post by mikeavison on 2014-05-29
Hunhh! my last thread just disappeared?

Anyway this works for me
[http://dirtycoding.blogspot.co.uk/2011/12/easy-way-to-auto-connect-to-hidden.html](http://dirtycoding.blogspot.co.uk/2011/12/easy-way-to-auto-connect-to-hidden.html)

Ubuntu still ignoring SSID broadcasts but it connects automatically to "hidden" network

---

