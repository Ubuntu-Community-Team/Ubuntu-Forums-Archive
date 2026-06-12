---
title: "Gutsy - How I got my Linksys WiFi working @ 108Mbps - WMP54gx"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by bmullan on 2007-11-23
**_BACKGROUND_**

I have 5 computers in my house.  All have WMP54GX Linksys wifi NICs.

see: [http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859962297&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6229740888B13]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859962297&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6229740888B13")

They all connect to the "world" through my WRT54GX2 Access Point

see:
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859965521&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6552141396B24]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859965521&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6552141396B24")

using:
[INDENT][LIST]
[*]infrastructure mode (versus ad-hoc)
[*]WEP encryption
[/LIST][/INDENT]

I had recently downloaded Ubuntu 7.10 - Gutsy to see what was new.

I followed all the instructions regarding getting my Wifi working using my Linksys WMP54GX.

I added/installed NDISWRAPPER using Synaptic Package Manager.

I added the command - ndiswrapper to the end of the /etc/modules file

I copied the Linksys drivers to a directory (I called it _linksys_ on my Ubuntu system

I changed to the _linksys_ directory then to the _Drivers_ directory under that.

I then ran successfully the command -  sudo ndiswrapper -i netani.inf

I then loaded Ndiswrapper -
[INDENT]sudo modprobe ndiswrapper[/INDENT]

and made sure that Ndiswrapper is loaded during system bootup by the command -
[INDENT]ndiswrapper -m[/INDENT]

**_PROBLEM and SOLUTION_**

I then naively thought I could just use Ubuntu's menu driven Network tools (System/Administration/Network tab) to configure my Wifi.

I went to that menu.  Clicked-on/Selected 

[INDENT]_Wireless connection_ then _Properties_[/INDENT]

deselected _Enable roaming mode_
entered my _Network name ESSID_
selected my Password type:  WEP key (ascii)   _note: you enter whatever you use here_
entered my Network password:  _enter whatever your password is_
then
selected under _Configuration Settings_ I set the _Configuration_ option to _Automatic configuration (DHCP)_

Clicking OK... I then checked the /etc/network interfaces filed using:

[INDENT]sudo gedit /etc/network/interfaces[/INDENT]

I found that the Network manager had put in the following

[I][INDENT]more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-key _my-encryption key_
wireless-essid _my-ESSID_


auto wlan0[/INDENT][/I]

***[COLOR="Red"]this would NOT work ![/COLOR]***

but I found that I could always get the Wifi working by manually executing the commands:

[INDENT][LIST]
[*]sudo iwconfig wlan0 essid _my-ESSID_
[*]sudo iwconfig enc _my-encryption key_
[*]sudo dhclient wlan0
[/LIST][/INDENT]

However --- even though that worked I'd have to do it each time I rebooted and I spent 3 days trying to figure out why.

I finally noticed in the system log after using the Network Manager that there was an error about setting the Encryption Key for my Wifi....?????

I finally broke down and and read the man page info on wireless ... by running 

[INDENT]man wireless[/INDENT]

which made me realize that the Ubuntu Network Manager just wasn't doing enough or doing it correctly to get my Linksys WMP54GX working.   I also was suspicious of the fact that when I used the command line and successfully got Wifi working I used the command

[INDENT]sudo iwconfig wlan0 **[COLOR="Red"]enc[/COLOR]** _my-encryption key_[/INDENT]

but after using the *Ubuntu Network Manager* menu method to configure my Wifi the file _etc/network/interfaces_ contained the command:
[INDENT]
wireless-[COLOR="Red"]**key**[/COLOR] _my-encryption key_[/INDENT]

I then manually edited  /etc/network/interfaces file and changing it to:

[B][INDENT]]more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-key _leave the encryption key Network Manager put here alone - can't hurt_
[COLOR="Blue"]**wireless-enc**[/COLOR] _put your WEP encryption key here_
wireless-essid _put your ESSID here_
**[COLOR="Blue"]wireless-mode infra[/COLOR]**
**[COLOR="Blue"]ifconfig wlan0 up[/COLOR]**

auto wlan0[/INDENT][/B]

NOTE:   the changes above in [COLOR="Blue"]**Blue**[/COLOR]

changed 

I added the command _wireless-enc_
I added command to configure for INFRASTRUCTURE mode _wireless-mode infra_
I added command_ ifconfig wlan0 up_ to _make sure_ wlan0 (re Ndiswrapper) is turned on


_**RESULTS**_

I now have my Linksys WMP54GX on my Ubuntu Gutsy system running at **_108Mbps _and BEST OF ALL ....**
[COLOR="Red"]
[B]Wifi starts automatically after a reboot.
[/B][/COLOR]

which is shown by executing - iwconfig

PC:~$ iwconfig
lo        no wireless extensions.

[COLOR="Blue"][INDENT]wlan0     IEEE 802.11g  ESSID:"my-ESSID"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:10:B5:92:6A   
          **Bit Rate=_108 Mb/s_  ** 
          Power Management:off
          Link Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/INDENT][/COLOR]

---

### Post by Varadin on 2007-12-03
Thank you... Thank you.... Thank you

Great work....

---

### Post by Varadin on 2007-12-03
Confirmed and working....

---

### Post by sethvath on 2007-12-03
Great work and thanks

---

### Post by 1976saint on 2007-12-03
Hi, would this work for WPA ?

I noticed that the network manager tool only has WEP in the drop down.
I posted last Friday with an identical problem (Auto start wireless)  but go no response. I will try your method tonight with WPA and let you all know. 

Cheers Paul.

---

### Post by bmullan on 2007-12-07
I don't think its necessary to use the built-in Network Mgr at all if you edit the interfaces file and follow info pertinent to your needs that you look up in the MAN pages for "wireless"

---

### Post by yomna on 2007-12-07
For WPA: When you click on the connection icon, there should be the option connect to another wireless network. After selecting it, input the network's name and change the security to WPA.  All you need then is your key and you're set.

That's how I do it.

---

