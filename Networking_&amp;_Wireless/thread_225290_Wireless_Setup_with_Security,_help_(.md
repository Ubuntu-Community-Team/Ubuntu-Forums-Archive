---
title: "Wireless Setup with Security, help :("
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by pfs01089 on 2006-07-29
Hi everybody,

Im having some trouble. Working off an older Dell Inspiron 7000 laptop, using a D-Link DGL-4300 router and D-Link WNA-2330 wireless pcmcia card. The only way i can get a connection between the latop and the router is to not have the SSID hidden and to have all security turned off. Which I dont want to do. Ive been working on this now for 3 weeks, searching the forums and google. Tyring everyones steps and walk throughs but i still cannt keep the connection the second i turn security on. I can give you any information about that hardware you might need just let me know what you looking for. Ive been using ubuntu for about a month now but this is first time setting up wirless with it on a laptop.

Thanks for any helps thats given

---

### Post by wieman01 on 2006-07-29
Hi,

Would be indeed nice what hardware you have (i.e. wireless card) and what driver you are using (Ndiswrapper? Linux driver?). Then what kind of wireless connection have you got, what security would you need, and if static IPs are used. Tell us everything that you think is worthwhile so that we can help...

Cheers / He

---

### Post by pfs01089 on 2006-07-29
Hi and thanks for replying

Hardware: 
Router - DLINK DGL-4300
NIC -Dlink  WNA-2330 (pcmcia)
Driver - Currently what it uses on a fresh install (im new to linux, not sure of how to check the specific driver is being used)

Everything is using DHCP so no static IP's anywhere
Running off comcast cable, would like to be able to hid my SSID and use WAP.

Its running of 802.11G connection

**_lsmod | grep ath_**

ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
[B][U]

iwconfig | grep ath[/U][/B]

lo        no wireless extensions.
sit0      no wireless extensions.
ath0      IEEE 802.11g  ESSID:"Strong"

**_iwlist ath0 scan_**

ath0      Scan completed :
          Cell 01 - Address: 00:13:46:F0:C3:91
                    ESSID:"Strong"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=74/94  Signal level=-21 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

[B][U]
ifconfig | grep ath[/U][/B]

ath0      Link encap:Ethernet  HWaddr 00:15:E9:5E:DA:84

Installed NDISWRAPPER and now im using the windows driver

---

### Post by pfs01089 on 2006-07-29
Deleted

---

### Post by wieman01 on 2006-07-29
Ok, looks good. Your wireless network device is up & running, so we don't have to go through that.

There are two ways to configure your wireless network:

a. Graphical mode & tool
b. Text mode through terminal

I prefer to start with the terminal because that gives you full control. Try this:

> sudo gedit /etc/network/interfaces

Edit the file and add these lines (delete all the other stuff that's in there):
> auto lo 
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid Strong

Save the file and restart your network:
> sudo /etc/init.d/networking restart

Ideally this should be it. Fire up your browser and see if you are on line. I will then show you how to use another graphical tool to achieve the same thing in a more convenient way. 

If it doesn't work could you post the output window after your have restarted the network? A restart sometimes helps as well (so it did in my case).

I assume you are not using WEP or any other kind of encryption & authentication, right?

---

### Post by pfs01089 on 2006-07-29
No thats where i run into the problem of not connecting, is when i turn on security any level...im going to try those steps now and ill let you know how it goes. thanks again very much for the help

---

### Post by wieman01 on 2006-07-29
> **pfs01089 said:**
> No thats where i run into the problem of not connecting, is when i turn on security any level...im going to try those steps now and ill let you know how it goes. thanks again very much for the help

Ok, security can be a hassle. But let's do one thing at a time. If you get to work this one, we are one step in the right direction. :-)

---

### Post by pfs01089 on 2006-07-30
Ok i followed all those commands, i have an active internet connection and there were no errors.

---

### Post by wieman01 on 2006-07-30
Great. So so you want to use WEP as you preferred encryption/authentication method? If so this is the way to go:

> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid Strong
wireless-key your_wep_key

You simply have to add one line with your WEP HEX-key. Then restart the network, that's it.

---

### Post by pfs01089 on 2006-07-30
I was hoping to use WAP or WAP2, if its possible if not WEP is ok to

---

### Post by wieman01 on 2006-07-30
Ok, WPA and WPA2 are a much better option. You could try this howto which I wrote a while ago:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834")

Note this is my approach, there are other solution out there as well including a tool called NetworkManager.

auto ath0
iface ath0 inet dhcp
    wpa-driver wext
    wpa-conf managed
    wpa-ssid <your_essid>
    wpa-ap-scan 1
    wpa-proto RSN
    wpa-pairwise CCMP
    wpa-group CCMP
    wpa-key-mgmt WPA-PSK
    wpa-psk <your_hex_key>

The 3rd line (wpa-driver) may not be the appropriate driver for your device... I am not sure, but try it. 

Please have your ESSID broadcast turned on for the time being.

---

### Post by wieman01 on 2006-07-30
You could also try NetworkManager. This is a good howto:

[http://www.ubuntuforums.org/showthread.php?t=125150]("http://www.ubuntuforums.org/showthread.php?t=125150")

NetworkManager has 2 restrictions:

1. DHCP only (no static IPs)
2. No hidden ESSID

---

### Post by pfs01089 on 2006-07-30
Ok, ive gone ahead and added those lines to the file. ive restarted but now have no connection. wap is enable on the router. line 3 that references the driver, how could i find the name for the driver thats installed for the pcmcia card, maybe thats causing a problem.

So as we stand with no security i have connection. Add any security it suddenly cannot connect anymore.

Here us whats in /etc/network/interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver net5211   (this is whats listed in windows wireless drivers)
wpa-conf managed
wpa-ssid Strong
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 2f66ef4e12b52f31c6849e8af9ab3f9eb01e69d06076534d47e82dc52a45fe7d

---

### Post by pfs01089 on 2006-07-30
from what ive read wpa doesnt work or work well under ubuntu,is this true? i still cant get any security to work

---

### Post by wieman01 on 2006-07-30
WPA and WPA2 do work under Linux. Setting it up can be a bit tricky though. NetworkManager would be a good option to make it simpler, however, it has the mentioned restrictions.

Have you enabled WPA or WPA2? WPA2 is using AES as encryption method whereas WPA is using TKIP. This configuration is meant for WPA2 (AES).

---

### Post by pfs01089 on 2006-07-30
Im not sure what exactly it is im doing wrong, router is set to WAP2 AES

here is what the /etc/network/interfaces looks like

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver net5211
wpa-conf managed
wpa-ssid Strong
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk LDP68Ba108owV (this is what my router gave me as the key)
*wpa-psk 970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1*
the above line was from using this command:wpa_passphrase Strong LDP68Ba10owV
wireless-essid Strong (this line keeps getting put in when i have to reestablish connection through system > adminstration > networking)

Im not sure what im missing or not doing but it still only works with no security on. If im using WPA2 does any of the WPA in the above file need to be changed to WPA2 ?

i really do appreciate all your help

---

### Post by wieman01 on 2006-07-31
RSN indicates that this is a WPA2 network. WPA2 is an alias for RSN actually. So no worries.

I am still not sure about the driver though. It should be "wext" as you are using ndiswrapper. "wext" is a generic driver used by ndiswrapper and others. So we should stick with it. 

Can you try again? Please restart the network twice and see if it works. I always have to start it up twice before is works (so does my boot script). A minor annoyance but you won't notice it during the boot process later on.

Do you have any terminal output when restarting the network? Could you post it?

---

### Post by wieman01 on 2006-07-31
If this still does not work, we go for plan B. :-)

---

### Post by wieman01 on 2006-07-31
Another stupid question... wpa_supplicant is installed, right? I think you would not be able to generate a HEX passkey if it wasn't. Just asking because I am not sure.

---

### Post by pfs01089 on 2006-07-31
> **wieman01 said:**
> Another stupid question... wpa_supplicant is installed, right? I think you would not be able to generate a HEX passkey if it wasn't. Just asking because I am not sure.


I didnt install it seperatly, so unless it got installed with something else, i didnt install it. Im at work atm, but will change the driver back and restart twice when i get home  tonight

---

### Post by pfs01089 on 2006-07-31
Update:

Using this /etc/network/interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Strong
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk LDP68Ba10owV

results in this network restart

paul@paul-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:15:e9:5e:da:84
Sending on   LPF/ath0/00:15:e9:5e:da:84
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODE]: Invalid argument
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/ath0/00:15:e9:5e:da:84
Sending on   LPF/ath0/00:15:e9:5e:da:84
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

yes i confirm wpa_supplicant is installed

---

### Post by wieman01 on 2006-07-31
Ok, the problem is that your Windows driver or the current version of ndiswrapper do not seem to support WPA2. 

> ioctl[SIOCSIWENCODEEXT]: Operation not supported

I checked yesterday and it seemed that I had done an upgrade of ndiswrapper at some point although I cannot tell you right now what version I am using because it's my turn to be at work. :-)

I found something else for you to test WPA(1). Could you try following this guide? 

[http://www.ubuntuforums.org/archive/index.php/t-186548.html]("http://www.ubuntuforums.org/archive/index.php/t-186548.html")

I have made use of a similar setup before so it should work. Have your router accept WPA rather than WPA(2) and try it out. If that works, I will help you upgrade to WPA2 using the same approach.

---

### Post by wieman01 on 2006-07-31
Perhaps again post your files... Both the "interfaces" file and "wpa_supplicant" that you are going create.

---

### Post by pfs01089 on 2006-07-31
**_/etc/network/interfaces_**

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Strong
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk LDP68Ba10owV
wireless-essid Strong
[B][U]
/etc/wpa_supplicant/wpa_supplicant.conf[/U][/B]

ctrl_interface=/var/run/wpa_supplicant#
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
ssid="Strong"
proto=WPA
key_mgmt=WPA-PSK
wep_key=LDP68Ba10owV

in the router it is set to WPA only with TKIP and AES selected (option to choose one or the other or both)

I lost all connections as soon as i tried this

---

### Post by wieman01 on 2006-08-01
Ok, two things:

They WPA key (WPA-PSK) needs to be in a HEX format (use wpa_supplicant to generate it). It appears that one you have provided is the ASCII text key. This for sure will contribute to the problem.

Secondly, your interfaces file is somehow incorrect. I cannot validate it right now as I am not in front of my home computer, but I'll try to figure it out tonight and post the right settings here.

Keep trying, we'll get there eventually.

---

### Post by wieman01 on 2006-08-01
Again me. Let's try the following step by step:

1. Create wpa_supplicant file:
> sudo gedit /etc/wpa_supplicant.conf

2. Add these lines & save the file:
> ctrl_interface=/var/run/wpa_supplicant
network={
    ssid=Strong
    scan_ssid=1
    proto=WPA
    pairwise=TKIP
    key_mgmt=WPA-PSK
    psk=your_hex_key
}

3. Run wpa_supplicant:
> sudo wpa_supplicant -D wext -i ath0 -c /etc/wpa_supplicant.conf -w -dd

4. Request IP from router:
> sudo dhclient ath0

If this works, we will try WPA2 and create a boot script later on. Don't forget that you ought to generate a passphrase and replace the corresponding part of the line that says "psk=your_hex_key" with your key.

Secondly your "interfaces" file should dispose of only 4 lines (simply delete the remaining ones):

> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

Any luck? What's the output?

---

### Post by pfs01089 on 2006-08-01
**_/etc/network/interfaces_**

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

**_/etc/wpa_supplicant.conf_**

ctrl_interface=/var/run/wpa_supplicant

network={
ssid=Strong
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
wep_key=970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1
[B][U]
output from sudo wpa_supplicant -D wext -i ath0 -c /etc/wpa_supplicant.conf -w -dd [/U][/B]

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
Line 3: failed to parse ssid 'Strong'.
Line 3: failed to parse ssid 'Strong'.
scan_ssid=1 (0x1)
proto: 0x1
pairwise: 0x8
key_mgmt: 0x2
Line 8: Invalid PSK '=970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1'.
Line 8: failed to parse psk '=970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1'.
Line 8: network block was not terminated properly.
Line 8: WPA-PSK accepted for key management, but no PSK configured.
Line 8: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Line 8: failed to parse network block.
Failed to read read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface ath0
Cancelling scan request

I had taken them out but i think i copied this before i changed it, they are gone now

---

### Post by wieman01 on 2006-08-01
Hello... Just a comment before you post the rest. You may have to drop the quotation marks, although I am not sure (ESSID line).

---

### Post by wieman01 on 2006-08-01
Ok, two obvious errors that I have spotted:

1. The last line should read "psk=", not "wep_key".
2. Your PSK key has a 65 characters, but it should be 64. There is a space character that does not belong there.

The correct line should read:

> psk=970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1

This should do if the key you provided is correct.

---

### Post by wieman01 on 2006-08-01
Plus there was a parsing error in connection with the SSID. If it does not appear, try to add quotation marks as I am not sure here.

---

### Post by wieman01 on 2006-08-01
Somehow the space characters reappear in this post after removing them. Strange...

Just make sure there are no spaces in your .conf file... they key must consist of 64 characters.

---

### Post by pfs01089 on 2006-08-01
OK im confused, my router says the shared key needs to be 8-63 even when i take the space out the key im using in that file is still to long

ctrl_interface=/var/run/wpa_supplicant
network={
ssid=Strong
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=970cc9cf32ba4c180b0be560121fc9c4199640b4408448b57f65472b77b69ea1

---

### Post by wieman01 on 2006-08-01
Your routers key is ASCII text and will be between 8 - 63 characters long. That's ok. 

But when you generate the HEX key for your client/computer, it will be 64 characters long. 

The HEX key and the router's look different although they are the same just in a different format if you know what I mean.

Can you try again and post the output? Please make sure there are no spaces in between.

---

### Post by pfs01089 on 2006-08-02
paul@paul-laptop:~$ sudo wpa_supplicant -D wext -i ath0 -c /etc/wpa_supplicant.c onf -w -dd
Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl _interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=6):
     53 74 72 6f 6e 67                                 Strong
scan_ssid=1 (0x1)
proto: 0x1
pairwise: 0x8
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Line 8: network block was not terminated properly.
Line 8: removed CCMP from group cipher list since it was not allowed for pairwis e cipher
Line 8: failed to parse network block.
Failed to read read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface ath0
Cancelling scan request

**_wpa_supplicant.conf_**

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=e395160c9b4b909ce7d5682724c1a864e39399c037f78d44ff6a7d137c867038
[B][U]
etc/network/interfaces[/U][/B]

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

should we update to the newest version of ndiswrapper and try again this way using the windows wireless driver rather than wext ?

---

### Post by wieman01 on 2006-08-02
Ahem... The final "}" in the .conf file is missing. Again this is a parser error... Try that first.

> ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=e395160c9b4b909ce7d5682724c1a864e39399c037f78d44ff6a7d137c867038
}

---

### Post by wieman01 on 2006-08-02
> **pfs01089 said:**
> should we update to the newest version of ndiswrapper and try again this way using the windows wireless driver rather than wext ?

"wext" refers to ndiswrapper and the Windows driver. So it the right driver for wpa_supplicant.

---

### Post by wieman01 on 2006-08-02
Man... according to your terminal output we are close... very close. Don't give up.

---

### Post by pfs01089 on 2006-08-02
> **wieman01 said:**
> Man... according to your terminal output we are close... very close. Don't give up.

nah to stubborn to give up, but i gotta get some sleep. will do try again with the { in the file tomorrow and will update ya, u rock for helping out so much

---

### Post by wieman01 on 2006-08-02
> **pfs01089 said:**
> nah to stubborn to give up, but i gotta get some sleep. will do try again with the { in the file tomorrow and will update ya, u rock for helping out so much

Hey, don't worry. I had similar sh..y problems so I understand how frustrating this can be. We'll get there eventually. 

It's just becoming more and more obvious that Ubuntu needs a real good & easy-to-configure GUI that can cater to exactly what we need. NetworkManager is a good approach but it's still insufficient.

Let's continue tomorrow, dude.

---

### Post by amp_man on 2006-08-02
hey folks, before you get any further, just a reminder:

```
amp@amplifier:~$ wpa_supplicant
--snip--
drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  [COLOR="Red"]ndiswrapper = Linux ndiswrapper[/COLOR]
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
```

wext may work also, but seems to me if you're using ndiswrapper, you probably should use it throughout.

edit: this card should work with madwifi ([link](http://madwifi.org/wiki/Compatibility#WNA2330)) which should be included with dapper, so that's probably why it's showing up as ath0 (as opposed to wlan0, like ndiswrapper usually does). Get rid of ndiswrapper (ndiswrapper -e <drivername>) and try using madwifi in place of wext.

---

### Post by wieman01 on 2006-08-02
Good point... "wext" seems to work though from what I can see. And it is definitely ok for ndiswrapper (including ipw).

But you are right about ath0 referring to an Atheros chipset. Let's see how this works out.

---

### Post by AzureCrystal on 2006-08-02
> **wieman01 said:**
> You could also try NetworkManager. This is a good howto:

[http://www.ubuntuforums.org/showthread.php?t=125150]("http://www.ubuntuforums.org/showthread.php?t=125150")


THANK YOU !!, great information on network manager, I had the same problem setting up WPA, did some digging on the forum, found this and it worked !!!  

Here is what I had to do:

- tried installing the package via SUDO, noticed it hung trying to get the last package off security.ubuntu(or something like that), looked like it failed to authenticate me.

- Went into the Synaptic Package Manager and installed it from there, it worked !!

- Turned off my laptop, rebooted(I use a LiveCd with a USB stick, works like a charm, no multi-partitions needed)

- Noticed new networking icons on my taskbar, doubled clicked on those

- Entered my WPA password

- Voila !!  

THANKS !!!

---

### Post by wieman01 on 2006-08-02
> **AzureCrystal said:**
> - Voila !!  

THANKS !!!

You are welcome although NetworkManager is not my preferred way. :-) It has two constraints... no static IPs and the ESSID must not be hidden. But apart from that, it's a great tool (with known issues).

Glad it worked for you.

BTW: Use WPA2... WPA is WEP-based and not safe. But I am a security nerd, perhaps you don't need it. ;-)

---

### Post by AzureCrystal on 2006-08-02
> **wieman01 said:**
> You are welcome although NetworkManager is not my preferred way. :-) It has two constraints... no static IPs and the ESSID must not be hidden. But apart from that, it's a great tool (with known issues).

Glad it worked for you.

BTW: Use WPA2... WPA is WEP-based and not safe. But I am a security nerd, perhaps you don't need it. ;-)

Will look at that, thanks again weiman01, learned something useful today !

BTW, Ubuntu really rocks, can't believe it works so well right out of the box !!

---

### Post by pfs01089 on 2006-08-02
UPDATE:

etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=ad1a224f110647f9c47509944e491da5ff37443e5228fa4430505c3366e93812
}


sudo wpa_supplicant -D wext -i ath0 -c /etc/wpa_supplicant.conf -w -dd


wpa_driver_wext_associate
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 0 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 1 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 2 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 3 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 8 value 0x0 - Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b04 len=12
Wireless event: cmd=0x8b1a len=15
Wireless event: cmd=0x8b19 len=8
Received 260 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:46:f0:c3:91 ssid='Strong' wpa_ie_len=28 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:13:46:f0:c3:91 (SSID='Strong' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 6 value 0x1 - WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - State: ASSOCIATING -> ASSOCIATING
wpa_driver_wext_associate
ioctl[SIOCSIWGENIE]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 0 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 1 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 2 value 0x4 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 3 value 0x2 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 10 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 8 value 0x0 - Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b04 len=12
Wireless event: cmd=0x8b1a len=15
Wireless event: cmd=0x8b19 len=8
Received 260 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:46:f0:c3:91 ssid='Strong' wpa_ie_len=28 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:13:46:f0:c3:91 (SSID='Strong' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 6 value 0x1 - WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2


I tried to not put double info from the scan since it just keeps running.

---

### Post by wieman01 on 2006-08-02
Ok, can you try the "madwifi" driver instead of "wext" as has been suggested earlier? Just to see what happens.

Just a dumb question... Have you got your router configured to use WPA? I find this error message strange:

> No keys have been configured - skip key clearing

---

### Post by pfs01089 on 2006-08-02
Just change wext to madwifi ? and yes it is setup for WPA

---

### Post by wieman01 on 2006-08-02
Yes, just replace "wext" with "madwifi" in the interfaces file.

---

### Post by pfs01089 on 2006-08-02
> **wieman01 said:**
> Yes, just replace "wext" with "madwifi" in the interfaces file.

in the interfaces or wpa_supplicant, one of ur previos posts had me take everything but 4 lines out of interfaces.

---

### Post by wieman01 on 2006-08-02
Man, I am stupid. ;-) This one it is:

> 
sudo wpa_supplicant -D **madwifi** -i ath0 -c /etc/wpa_supplicant.conf -w -dd

Can you post the output again?

---

### Post by pfs01089 on 2006-08-02
Heheh i will just before i crash for the nite ill run it all again.

---

### Post by wieman01 on 2006-08-02
Great, it'd be all a question of minutes if I was sitting in front of your computer. Plus the time difference makes it all a bit more complicated, but well, we are getting there.

---

### Post by pfs01089 on 2006-08-03
Update: Good News I think. i reran that command with the madwifi in it

**_etc/network/interfaces _** (this file seems to keep changing by it self)

auto lo
iface lo inet loopback


iface ath0 inet dhcp
wireless-essid Strong


etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
proto=WPA
pairwise=TKIP
key_mgmt=WPA-PSK
psk=4426b6e74070ed15b9ca5b691feb74f3e6876ce9661c605a46d33071a81083f2
}


sudo wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w -dd



Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=6):
     53 74 72 6f 6e 67                                 Strong
scan_ssid=1 (0x1)
proto: 0x1
pairwise: 0x8
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Line 9: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Strong'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:15:e9:5e:da:84
wpa_driver_madwifi_del_key: keyidx=0
wpa_driver_madwifi_del_key: keyidx=1
wpa_driver_madwifi_del_key: keyidx=2
wpa_driver_madwifi_del_key: keyidx=3
wpa_driver_madwifi_set_countermeasures: enabled=0
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
Setting scan request: 0 sec 100000 usec
Added interface ath0
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=6):
     53 74 72 6f 6e 67                                 Strong
Wireless event: cmd=0x8b1a len=15
Wireless event: cmd=0x8b19 len=8
Received 260 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
0: 00:13:46:f0:c3:91 ssid='Strong' wpa_ie_len=28 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
Trying to associate with 00:13:46:f0:c3:91 (SSID='Strong' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2
WPA: set AP WPA IE - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_madwifi_set_drop_unencrypted: enabled=1
State: SCANNING -> ASSOCIATING
wpa_driver_madwifi_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b1a len=15
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:13:46:f0:c3:91
State: ASSOCIATING -> ASSOCIATED
Associated to a new BSS: BSSID=00:13:46:f0:c3:91
No keys have been configured - skip key clearing
Associated with 00:13:46:f0:c3:91
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
RX EAPOL from 00:13:46:f0:c3:91
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 05 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 89 00 20 00 00 00 00 00 00 00 05 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:13:46:f0:c3:91 (ver=1)
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Renewed SNonce - hexdump(len=32): b4 50 57 6f 75 ef 6c 44 7a 65 46 fd 25 dc 18 31 9d 46 6b 4f 76 4b 23 f9 eb 7e 6a 75 2a 67 71 0e
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 09 00 20 00 00 00 00 00 00 00 05 b4 50 57 6f 75 ef 6c 44 7a 65 46 fd 25 dc 18 31 9d 46 6b 4f 76 4b 23 f9 eb 7e 6a 75 2a 67 71 0e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8c 17 73 92 5f 07 da 54 7b a2 c6 15 9b 66 5e 9c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK, IFLA_IFNAME: Interface 'ath0' added
RX EAPOL from 00:13:46:f0:c3:91
RX EAPOL - hexdump(len=127): 01 03 00 7b fe 01 c9 00 20 00 00 00 00 00 00 00 06 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6a 2f a6 45 75 f6 4c 7a d3 cf fb 74 07 32 7b 60 00 1c dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=123
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=127): 01 03 00 7b fe 01 c9 00 20 00 00 00 00 00 00 00 06 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 6a 2f a6 45 75 f6 4c 7a d3 cf fb 74 07 32 7b 60 00 1c dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:13:46:f0:c3:91 (ver=1)
WPA: IE KeyData - hexdump(len=28): dd 1a 00 50 f2 01 01 00 00 50 f2 02 02 00 00 50 f2 02 00 50 f2 04 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 09 00 20 00 00 00 00 00 00 00 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e2 81 84 8a 4f df 07 15 e2 b8 d3 e5 e9 dc d8 93 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:13:46:f0:c3:91
RX EAPOL - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 07 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e1 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e1 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5b 38 7c 1b 3f b9 f9 bc 33 d3 13 68 4b 52 d7 21 00 20 b1 87 91 4c 29 8a e4 30 91 b0 1c 8d 38 a7 52 b6 c4 d9 24 6e 5a b3 28 9c 80 02 05 c1 2a 68 3c b5
IEEE 802.1X RX: version=1 type=3 length=127
  EAPOL-Key type=254
WPA: RX EAPOL-Key - hexdump(len=131): 01 03 00 7f fe 03 91 00 20 00 00 00 00 00 00 00 07 f1 fb ea 44 b4 97 28 17 d5 65 ee 52 e2 64 3f e6 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e1 22 44 6d 8d 4f 04 4c 52 ca 56 4b ca 76 86 df e1 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 5b 38 7c 1b 3f b9 f9 bc 33 d3 13 68 4b 52 d7 21 00 20 b1 87 91 4c 29 8a e4 30 91 b0 1c 8d 38 a7 52 b6 c4 d9 24 6e 5a b3 28 9c 80 02 05 c1 2a 68 3c b5
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: RX message 1 of Group Key Handshake from 00:13:46:f0:c3:91 (ver=1)
WPA: Group Key - hexdump(len=32): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): 05 00 00 00 00 00
wpa_driver_madwifi_set_key: alg=TKIP key_idx=1 set_tx=0 seq_len=6 key_len=32
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 11 00 20 00 00 00 00 00 00 00 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 bc 54 0f 42 d9 a5 ff 49 c8 e7 2a 9e 0e ec f0 b4 00 00
WPA: Key negotiation completed with 00:13:46:f0:c3:91 [PTK=TKIP GTK=TKIP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:13:46:f0:c3:91 completed (auth)
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
EAPOL: startWhen --> 0

After that last line it just sits there with a blinking cursor, it appears to be working, but at this point there is no internet connection, i went into System > Adminstration > Networking and reselected Strong network, once that went and activated, the internet connection was working.

Whats next ?

---

### Post by wieman01 on 2006-08-03
Congrats, I'd say. You have made it!

The next steps are:

1. WPA2 instead of WPA.
2. Boot-script so the network & wpa_supplicant are started automatically.

I will right more tonight... Need to dig out the WPA2 configuration first of all. :-)

So you can browse the web and everything?

---

### Post by wieman01 on 2006-08-03
We are more or less there. Once we have done all that, we'll speed up your internet connection by disabling "ipv6". But let's see.

---

### Post by wieman01 on 2006-08-03
This is a good README by the way... with examples and everything:

[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain]("http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain")

---

### Post by pfs01089 on 2006-08-03
Yup, if you knew how i was doing this going and back and forth between to computers, disabling securty so i could copy and paste these outputs, then restarting security to try it again and be able to post on the forums...lol

yup i can browse the web...should i be using that System>Administration>network window at all, i had to to get the internet going after i ran that script

---

### Post by wieman01 on 2006-08-03
> **pfs01089 said:**
> Yup, if you knew how i was doing this going and back and forth between to computers, disabling securty so i could copy and paste these outputs, then restarting security to try it again and be able to post on the forums...lol

Hahaha... Very true! :-)

> **pfs01089 said:**
> yup i can browse the web...should i be using that System>Administration>network window at all, i had to to get the internet going after i ran that script

I've seen this before. I remember that I had to apply this trick once but that's a while ago. Ever since it worked without it.

---

### Post by wieman01 on 2006-08-03
Can you try this configuration _**AFTER**_ enabling WPA2 / AES in the router?

**_etc/wpa_supplicant.conf:_**

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
pairwise=CCMP
group=CCMP
key_mgmt=WPA-PSK
psk=ad1a224f110647f9c47509944e491da5ff37443e5228fa4430505c3366e93812
}

If this works we can continue with the boot-script. ONLY if it doesn't try to add this line above "pairwise=...":

> proto=RSN

That should do.

---

### Post by pfs01089 on 2006-08-03
well im calling it a nite lol, ill read over that link at work tomorrow, and then we can try upgrading to wpa2...talk to u tomorrow :)

---

### Post by wieman01 on 2006-08-03
If WPA2 works, we create a little start script so that you don't have to start up WPA_SUPPLICANT manually all the time.

Please note that these steps were "stolen" from :

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa+howto+boot]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa+howto+boot")

Now we have to create a small script (first provided by fulco and edited by me) in order to get wpa starting automatically at boot:
Code:

> sudo gedit /etc/init.d/wifi_wpa.sh

Here's the script:
Code:

> 
#! /bin/sh 
# wifi: wpa_supplicant init 
echo " * [Wifi]: Enabling WPA supplicant..." 
if [ -x /sbin/wpa_supplicant ]; then 
/sbin/wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w
fi 

exit 0

Change the script's permissions to allow it to be executed:
Code:

> sudo chmod +x /etc/init.d/wifi_wpa.sh

And create a symlink to define the relative service:
Code:

> sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/S40netwifiwpa

I have modified the script so that it fits your adapter. I also dropped the "-dd" which refers to the terminal output. After you have done these steps, you should reboot and be able to connect to the Internet right away.

---

### Post by pfs01089 on 2006-08-03
Ok WPA2 works problem is something with the script...when i boot up, and its at the ubuntu spalsh screen loading things, it drops to text screen loading the wifi, problem is though it just sits at CTRL-EVENT-CONNECTED and it shows the mac of the router, its been about 5 min and it hasnt booted into gnome yet

---

### Post by wieman01 on 2006-08-03
Can you change this line?

> sudo ln -s /etc/init.d/wifi_wpa.sh /etc/rcS.d/**S99netwifiwp**a

What happens?

Great to hear WPA2 works. The rest is easy. :-)

Please make sure that you can run this command from command line/terminal and connect to the Internet:

> /sbin/wpa_supplicant -D madwifi -i ath0 -c /etc/wpa_supplicant.conf -w

---

### Post by wieman01 on 2006-08-03
Could you also tell me where it exactly hangs?

---

### Post by pfs01089 on 2006-08-03
ok i had to control c on the part that it was hanging at, ill see if i can get the line again where it stops. im booting up the rest of the way and then i can change the script

---

### Post by pfs01089 on 2006-08-03
the last line that is printed to the screen before it hangs is:

CTRL-EVENT-CONNECTED - Connection to (router mac address) completed (auth) 

i can hit contrl C and it will keep loading

even when i run it in terminal it just sits at that line

ok after about 20-30 min it goes from that line to:
WPA: group rekeying completed with (mac of router) [GTK=CCMP]

---

### Post by wieman01 on 2006-08-03
Ok, could you add another 2 lines to the "interfaces" files and remove "wireless-essid"?

**_/etc/network/interfaces:_**

> auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver ath0
wpa-conf /etc/wpa_supplicant.conf

Please also remove the 2 files we have just created (start-script and symblink):

1. wifi_wpa.sh
2. S40netwifiwpa

Then restart. If this doesn't work we need to taker a closer look at the boot-logfile.

---

### Post by pfs01089 on 2006-08-03
You want me to keep S99netwifiwpa ?

---

### Post by wieman01 on 2006-08-03
No, please also delete it. :-)

---

### Post by pfs01089 on 2006-08-03
Ok restarting now

---

### Post by pfs01089 on 2006-08-03
ok it loaded up fine that time, was at the splash screen so i didnt see anything loading..no errors and im at the desktop

---

### Post by wieman01 on 2006-08-03
Mate, you have JUST DONE IT. WPA2 secured network! Jeee... Took us a bit longer, but that's it!

Would you do me a favor please... For the sake of helping others, could you post both the "interfaces" & the "wpa_supplicant.conf" file so that others can follow? Just to wrap it up & close this thread.

---

### Post by pfs01089 on 2006-08-03
just tested and no connection ill post the files

etc/network/interfaces

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver ath0
wpa-conf /etc/wpa_supplicant

wpa_supplicant.cond

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
pairwise=CCMP
group=CCMP
key_mgmt=WPA-PSK
psk=sfhgiuerhgipuqehguierghiuerq(example)
}

---

### Post by wieman01 on 2006-08-03
Mmm... Can you ping your router? 'xxx.xxx.xxx.xxx' stands for your routers IP address.

Terminal:
> ping xxx.xxx.xxx.xxx

---

### Post by pfs01089 on 2006-08-03
network is unreachable

since we made those changes should i go to system > adminstration > networking and re select the wireless network

---

### Post by wieman01 on 2006-08-03
> **pfs01089 said:**
> network is unreachable

Aeh... there is an error in your "interfaces" file...

> wpa-conf /etc/wpa_supplicant

[B][U]Should be:
[/U][/B]
> wpa-conf /etc/wpa_supplicant.conf

This points to your wpa_supplicant config file.

---

### Post by pfs01089 on 2006-08-03
> **wieman01 said:**
> Aeh... there is an error in your "interfaces" file...



[B][U]Should be:
[/U][/B]


This points to your wpa_supplicant config file.



damn typos...trying again

---

### Post by pfs01089 on 2006-08-03
Still no connection, whats odd is the lights on the nic are solid, where as when i had conenction they were flashing, according to linksys one should be steady one should be flashing..

---

### Post by wieman01 on 2006-08-03
Can you post your files again so that I can validate them? It's odd indeed. 

Please also ping your router again. Sometimes Internet does not work although your are connected to the router. Has to do with the DNS settings.

---

### Post by pfs01089 on 2006-08-03
ping 192.168.0.1
Connect: Network Unreachable

interfaces

auto lo

iface ath0 inet dhcp
wpa-driver ath0
wpa-conf /etc/wpa_supplicant.conf

wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant  (should this have .conf?)
network={
ssid="Strong"
scan_ssid=1
pairwise=CCMP
group=CCMP
key_mgmt=WPA-PSK
psk= (blah blah)
}

not able to copy and past why i didnt include passkey

---

### Post by wieman01 on 2006-08-03
Man, I am stupid... This is the right one:

**_/etc/network/interfaces:_**

> auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.conf

If this does not work, please try:

> auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

We chose the wrong driver! This should work now (I know I have been saying this for a while).

---

### Post by wieman01 on 2006-08-03
> **pfs01089 said:**
> 
ctrl_interface=/var/run/wpa_supplicant  (should this have .conf?)

No, it's referring to the wpa_supplicant client/executable and not the conf-file.

Please try my latest post. There has been a typo that has tripped us up.

---

### Post by pfs01089 on 2006-08-03
Interfaces:

auto lo
iface lo inet loopback
wpa-driver wext (tried madwifi)
wpa-conf /etc/wpa_supplicant.conf

wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
scan_ssid=1
pairwise=CCMP
group=CCMP
key_mgmt=WPA-PSK
psk=c6b62fa380cec26f005bd1e89b9c83a237b59f70eff201a03f3c99b9f79a43c2
}

still no pingage

---

### Post by wieman01 on 2006-08-03
> **pfs01089 said:**
> Interfaces:

auto lo
iface lo inet loopback
wpa-driver wext (tried madwifi)
wpa-conf /etc/wpa_supplicant.conf

Typo again? Should read:

> auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver madwifi [or wext]
wpa-conf /etc/wpa_supplicant.conf

---

### Post by pfs01089 on 2006-08-03
sorry i checked the file this is interface really

auto lo
iface lo inet loopback

iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.conf

---

### Post by wieman01 on 2006-08-03
Ok, we'll have to continue tomorrow then. Need to think about it. The same approach was quoted in here:

[http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice]("http://madwifi.org/wiki/UserDocs/Distro/Debian/ConfiguringtheMadWifidevice")

So I cannot tell right now what's wrong with it. You could check the content of "/var/log/boot.log" or similar and look at the latest boot entries (end of the file). Perhaps that reveals something.

Get back to you tomorrow. I will test this using my own computer.

---

### Post by pfs01089 on 2006-08-03
i went into system > adminsitration > networking and the ath0 was not active, trying to activate it now and then restart see what happes

---

### Post by wieman01 on 2006-08-03
Man, again? Yes, I have heard about this before... Although we should have activated it with our script, this step may be necessary once more.

Working (perspiring... sigh)?

---

### Post by wieman01 on 2006-08-03
By the way... it's likely that it should be the "wext" driver and not "madwifi".

---

### Post by pfs01089 on 2006-08-03
> **wieman01 said:**
> By the way... it's likely that it should be the "wext" driver and not "madwifi".

that attempt after activating was with madwifi i will change to wext now


Sigh no go on both i dont get it, we had it and now back to where we were. no connection with security

---

### Post by wieman01 on 2006-08-03
Please restart after activating the wireless adapter. WPA won't be loaded until after your have rebooted your computer.

---

### Post by pfs01089 on 2006-08-03
> **wieman01 said:**
> Please restart after activating the wireless adapter. WPA won't be loaded until after your have rebooted your computer.

yea i did after each activate

in my router i have option for cypher type, options are TKIP, AES or TKIP and AES?

---

### Post by wieman01 on 2006-08-03
Should be AES (=WPA2) only. Nothing else. But to please choose "AES + TKIP" for the time being until we have resolved the current issue.

---

### Post by wieman01 on 2006-08-04
After reading a few other posts & howtos it appears that the location of the "conf" file can be a problem. Could you try this:

1. Move "wpa_supplicant.conf" from "/etc/" to folder "/etc/wpa_supplicant/".
2. Change "interfaces" according to this:
> auto lo
iface lo inet loopback

**auto ath0**
iface ath0 inet dhcp
wpa-driver wext [or madwifi]
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

I had to add a line **_("auto ath0")_**. Damnit, I am pretty sure that's the problem. You need to have this line so that the adapter is activated during boot. Seems I have lost focus. ;-) This explains why the system was hanging earlier while your wireless card was inactive.

Now to bring up your network you either restart your computer or type these commands:
> sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

Alternatively:
> sudo /etc/init.d/networking restart

See this... we are on the right track:

[http://www.ubuntuforums.org/showthread.php?t=185484&highlight=wpa-conf]("http://www.ubuntuforums.org/showthread.php?t=185484&highlight=wpa-conf")

---

### Post by pfs01089 on 2006-08-04
after doing the sudo /etc/init.d/networking start

*configuring network interfaces
run-parts: run -parts: component /etc/network/if-pre-up.d/wpasupplicant is broken symbolic link


DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7

then it just keeps repeating that line with a different interval

Interfaces

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
wireless-essid Strong  (this keeps getting put in when i activet the connection in system > administration > Networking)

ctrl_interface=/var/run/wpa_supplicant
network={
ssid="Strong"
pairwise=CCMP
group=CCMP
key_mgmt=WPA-PSK
psk=(key)
}

---

### Post by wieman01 on 2006-08-04
Hello,

Perhaps we need to reboot... But I am on line now. Let's continue here with the final settings once we have resolved the issue.

He

---

### Post by wieman01 on 2006-08-04
Perhaps move the wpa_supplicant.conf file back to "/etc/". Then we start again from there.

---

### Post by wieman01 on 2006-08-04
Tell you what (while I am off line)... Could try out the previous suggestion once again? I think the "auto ath0" thing kept us from doing it successfully. Please move the conf-file back to "/etc/" as a consequence.

**_/etc/wpa_supplicant.conf:_**
> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

Now create the startup script and symblink as we talked about earlier & reboot.

---

### Post by pfs01089 on 2006-08-04
Ok  trying now

---

### Post by wieman01 on 2006-08-04
**_/etc/network/interfaces:_**
> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

The driver line is not necessary as it appears in the wpa_supplicant line. My fault again.

---

### Post by pfs01089 on 2006-08-04
I go to run the script and this is what i get..


ln: creating symbolic link '/etc/rcs.d/S99netwifiwpa' to /etc/init.d/wifi_wpa.sh : no such file or directory

btw im on msn

---

### Post by wieman01 on 2006-08-04
Do the steps as in here:

[http://www.ubuntuforums.org/showthread.php?t=225290&page=7]("http://www.ubuntuforums.org/showthread.php?t=225290&page=7")

The wifi_wpa.sh needs to be created first.

I suggest that we try this via chat tommorrow... I'll be offline now.

---

### Post by pfs01089 on 2006-08-04
yea i followed those steps, odd maybe im just tired ill try again tomorrw
...goos nite

---

### Post by pfs01089 on 2006-08-05
im on line now on msn....its sitting on the boot up at the line that says

{wifi]: enabling WPA supplicant... and hasnt moved

before it gets to that part its still saying run-parts: run-parts: component /etc/network/if-pre-up.d/wpasupplicant is a broken symbolic link

all the files have been created and i dont get any errors when i do the ln command u gave

---

### Post by wieman01 on 2006-08-05
"/etc/network/if-pre-up.d/wpasupplicant" is a link and points to "/etc/wpa_supplicant/ifupdown.sh". The system cannot find the latter, so it's likely that you mistakenly moved it together with "wpa_supplicant.sh" earlier.

Can you find "ifupdown.sh" in the folder "/etc/" by chance? If so please move it back to "/etc/wpa_supplicant/" and this error message should disappear.

---

### Post by pfs01089 on 2006-08-05
its not finding that ifupdown.sh

i found directorys in the /etc/network called if-down.d if-postdown.d if-pre-up.d and if-up.d


i did a search in gnome in all the file system and its not finding that ipupdown.sh

---

### Post by pfs01089 on 2006-08-06
We finally got it working, with WPA only at this time. Below is the /etc/network/interface file:

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf managed
wpa-ssid (you sside name here without the ()  )
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk (your key here without the ()  )

I have a WNA-2330 D-Link PCMCIA card running off Atheros chipset connecting to a DGL-4300 D-Link router.

We are still working on trying to get this working with WPA2

---

### Post by wieman01 on 2006-08-06
To enable WPA2 normally you'd have to change 3 lines according to this:

> wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP

However, this does not seem to work with the current Atheros Linux driver, therefore we'll try "ndiswrapper" next and keep you posted on the progress.

This may also be of help in case you want need a static IP and hidden ESSID in connection with WPA2 and ndiswrapper:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by wieman01 on 2006-08-07
Some users reported (including myself) that the network has to be restarted every time after startup... Apparently this is a bug.

Here is a workaround that helps restart the network during boot so that one does not have to do it manually after logging on to the system.

_Terminal:_
> cd /etc/init.d/
sudo gedit wireless-network.sh
sudo chmod +x wireless-network.sh
_Add 1 line:_
> /etc/init.d/networking restart
_Create symbolic link:_
> cd /etc/rcS.d/
sudo ln -s /etc/init.d/wireless-network.sh S35wireless-network
Restart...

---

### Post by pfs01089 on 2006-08-07
I have it all setup but im at work so i will try it once i get home

---

### Post by The Caped Crusader on 2007-08-22
Hello guys!

I'm sorry to invade your thread like this, but I have some questions that I feel  fellow Wieman01 here might know the answers. And that would be of great help, because I've tried some of the suggestions posted here but to no avail.

Here's my situation:

I'm running Feisty Fawn 64bits with a NETGEAR WG311T pci adapter (atheros chipset). I can connect to the internet through my NETGEAR router ok, but the connection drops frequently sometimes, others it can run for several hours straight without a single drop (i guess that can be something internet provider related...).
I'm using network manager out of the box since the Ubuntu installation because it worked and i just wanted to focus myself into work and setting up everything the way i like.
Thing is, both network manager and keyring manager are constantly asking for passwords when i log in, and although i do have the same password for both programs, it can be quite annoying.
I've tried to pass into /etc/network/interfaces the manual configuration entries (ip, gateway, domain, password, ssid, etc, etc) but either it keeps asking for passwords, or it simply won't connect.

The only thing i haven't tried to was to uninstall network manager and see if ubuntu connects to the router during boot. everything else i think i'v pretty much covered. or maybe i am overlooking something about my config files.

I don't mind to keep using network manager, although my workstation uses always the same local address (192.168.1.2), but what i really wanted is to have ubuntu work everything out at boot. my router uses WPA (WPA2 not supported, i'm afraid...), and my home network consists of another PC running Feisty 32bits and XP Pro dual-boot. the other PC is 192.168.1.3 and if i manage to work this out on this one, i'll try to do it on the second computer. he's running the same wifi adapter, WG311T.

I'd really appreciate any help on this :)

BTW, I'm from Lisbon, Portugal.

Peace,

---

### Post by wieman01 on 2007-08-23
@The Caped Crusader:

Nice talking to you.

First of all, there are a number of threads concerning keyring and keyring password. I am sure there is a solution for you, I cannot advise here simply because I use Kubuntu, not GNOME. That said if you wish to configure the network manually -  which is perfectly reasonable if you happen to have a desktop PC - so that the PC connects at boot, you can follow my HOWTO (signature). Prior to this, you will have to disable Network Manager.

If you go for the manual configuration, static IP won't be an issue at all.

As for the reception issue, what router have you got? I used to have a very similar issue, connections dropping at random with no obvious reason. I figured out, however, that I had to change a few radio settings on the router (default beacon interval, etc.) and after some testing & fiddling with the router, it worked. No more dropouts. That's where you have to start... Change a few settings (e.g. reduce beacon interval), then test it. I might take a couple of days, but there is light at the end of the tunnel. :-)

Post in the other threads if you have troubles configuring WPA.

---

### Post by The Caped Crusader on 2007-08-23
Thanks Wieman01, much appreciated!

I'll try your how-to AFTER uninstalling/disabling network manager (i guess stopping its service will do the trick).

As for the router, i use a NETGEAR WGT634U (108Mbits). I had to change it's broadcast settings to 'g and b' because with the settings that worked in XP - auto 108, my cards wouldn't find the router.
I also disabled 'extended range' setting because i found out it was causing much more connection drops than i have now.
Even after all this, and knowing that both computers are less than 15 feet away from the router (no walls in the way), I have to say that 40% (sometimes 35%) of signal strenght is not acceptable - i see only two bars in the network manager applet. under windows, with the same settings i got 95%/100% signal strenght. I'm thinking: maybe this is causing the connection drops?

Anyway, i can surf the web, email, everything with no problems and fast. I just want to automate the network login process because is driving me crazy, lol!

Thanks anyway, for for being always that helpful and available :)

Peace.

---

### Post by wieman01 on 2007-08-23
> **The Caped Crusader said:**
> Thanks Wieman01, much appreciated!

I'll try your how-to AFTER uninstalling/disabling network manager (i guess stopping its service will do the trick).

As for the router, i use a NETGEAR WGT634U (108Mbits). I had to change it's broadcast settings to 'g and b' because with the settings that worked in XP - auto 108, my cards wouldn't find the router.
I also disabled 'extended range' setting because i found out it was causing much more connection drops than i have now.
Even after all this, and knowing that both computers are less than 15 feet away from the router (no walls in the way), I have to say that 40% (sometimes 35%) of signal strenght is not acceptable - i see only two bars in the network manager applet. under windows, with the same settings i got 95%/100% signal strenght. I'm thinking: maybe this is causing the connection drops?

Anyway, i can surf the web, email, everything with no problems and fast. I just want to automate the network login process because is driving me crazy, lol!

Thanks anyway, for for being always that helpful and available :)

Peace.
No problem, my pleasure. If you want to continue the discussion and share thoughts, drop me a line. I am pretty sure you'll find the reason for the drop-outs. I did so too and I am by no means an expert. Good luck & see you later!

---

### Post by The Caped Crusader on 2007-08-23
Sure! I'm always interested to learn more from the amazing linux OS.

You know, back in 93/94, when i was into Systems Architecture major (i dropped college soon after and signed into Architecture somewhere else, don't ask...) linux was the hype of the moment. I was running Slackware on an old 486 with 1Mb of RAM and fiddling with X windows configurations. eheh, at the time, network issues were, well... a non-issue, because nobody had internet at home.

Anyway, soon after that i had to let go of linux and dedicate myself to college, work and stuff like that... with microsoft windows as my base OS. But i always kept my eye on the linux platform development. Along the way I had SUSE, Mandrake and Redhat (before the fedora thing).
Only now i'm delving again into linux, but preparing myself for a definite switch from windows, as i feel i don't need it anymore for my work (as long as i'm able to get dreamweaver and photoshop running inside the box).

Again, all this wi-fi settings and stuff is completely knew to me, and I'm asking for help here because i've read many threads here and there are many helpful and capable people at Ubuntu forums. This is really a great community!

To sum it up: Wireless and networking were never my strong points as a linux user, and I will really need this community's help to understand this one. :)

Maybe later you can tell me what kind of program feedback i need to collect.

Thanks again!

Peace.

---

### Post by wieman01 on 2007-08-23
> **The Caped Crusader said:**
> Sure! I'm always interested to learn more from the amazing linux OS.

You know, back in 93/94, when i was into Systems Architecture major (i dropped college soon after and signed into Architecture somewhere else, don't ask...) linux was the hype of the moment. I was running Slackware on an old 486 with 1Mb of RAM and fiddling with X windows configurations. eheh, at the time, network issues were, well... a non-issue, because nobody had internet at home.

Anyway, soon after that i had to let go of linux and dedicate myself to college, work and stuff like that... with microsoft windows as my base OS. But i always kept my eye on the linux platform development. Along the way I had SUSE, Mandrake and Redhat (before the fedora thing).
Only now i'm delving again into linux, but preparing myself for a definite switch from windows, as i feel i don't need it anymore for my work (as long as i'm able to get dreamweaver and photoshop running inside the box).

Again, all this wi-fi settings and stuff is completely knew to me, and I'm asking for help here because i've read many threads here and there are many helpful and capable people at Ubuntu forums. This is really a great community!

To sum it up: Wireless and networking were never my strong points as a linux user, and I will really need this community's help to understand this one. :)

Maybe later you can tell me what kind of program feedback i need to collect.

Thanks again!

Peace.
Yeah, Linux has gone a long way. Nowadays there is little reason why one should not make the switch. I completely switched over a year ago and basically banned Windows. I use CrossOver Office for critical MS applications that I still need or I am too lazy to replace with appropriate open-source programs. You know, sometimes laziness gets the better of you. I think CrossOver Office might be the perfect solution for you as well (Photoshop, Dreamweaver).

As for networking & wireless, you know where you find me. It can be confusing in the beginning but isn't that much of a problem if you have others to help you. Just make sure you get yourself (wirless) components that are supported "out of the box". That spares you the initial frustration.

That said, I much agree that you don't need Windows any longer nowadays, even if you aren't an IT savvy nerd. I am the living proof so to say. :-)

---

### Post by The Caped Crusader on 2007-08-23
Ok, feedback from the stuff:

**lsmod | grep ath**

ath_rate_sample        15360  1 
ath_pci               102448  0 
wlan                  219592  5 wlan_tkip,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               220016  3 ath_rate_sample,ath_pci

**iwconfig**

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"NETGEAR"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:0E:5A:1E   
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key:AA69-8754-4C7B-6FC9-C6FC-7787-32AA-7187   Security mode:restricted
          Power Management: off
          Link Quality=31/94  Signal level=-61 dBm  Noise level=-92 dBm
          Rx invalid nwid:327  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**iwlist ath0 scan**

Cell 01 - Address: 00:0F:B5:0E:5A:1E
ESSID:"NETGEAR"
Mode:Master
Frequency:2.437 GHz (Channel 6)
Quality=31/94  Signal level=-64 dBm  Noise level=-95 dBm
Encryption key: on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 48 Mb/s; 54 Mb/s
Extra:bcn_int=100
IE: WPA Version 1
Group Cipher : TKIP 
Pairwise Ciphers (1) : TKIP 
Authentication Suites (1) : PSK  
Extra:ath_ie=dd0900037f01010006ff7f

**ifconfig**

Link encap:Ethernet  HWaddr 00:0F:B5:86:C3:CE  
inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::20f:b5ff:fe86:c3ce/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

---

### Post by wieman01 on 2007-08-24
So what happens when you restart the network?
> sudo ifdown -v ath0
> sudo ifup -v ath0
What's the output like? And what does this file's contents look like?
> sudo gedit /etc/network/interfaces
The card appears to be working fine.

---

### Post by The Caped Crusader on 2007-08-24
**etc/network/interfaces**

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

wpa-driver madwifi
wpa-ssid NETGEAR
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
mtu 1492

wpa-psk 9857d541b52ff54848f98c8ed34a7f5ac449b8b4c0a2709336fd16e7f06c985e

--------------------------

the PSK hex code it was me who put it there, in a vain attempt at automatizing the process. I think it's not doing anything there, anyway.

---

### Post by The Caped Crusader on 2007-08-24
**sudo ifdown -v ath0**

Configuring interface ath0=ath0 (inet)
run-parts --verbose /etc/network/if-down.d
run-parts: executing /etc/network/if-down.d/avahi-autoipd
run-parts: executing /etc/network/if-down.d/wpasupplicant
dhclient3 -r -pf /var/run/dhclient.ath0.pid -lf /var/lib/dhcp3/dhclient.ath0.leases ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 5922
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:86:c3:ce
Sending on   LPF/ath0/00:0f:b5:86:c3:ce
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.1.1 port 67
ifconfig ath0 down
run-parts --verbose /etc/network/if-post-down.d
run-parts: executing /etc/network/if-post-down.d/avahi-daemon
run-parts: executing /etc/network/if-post-down.d/wireless-tools
run-parts: executing /etc/network/if-post-down.d/wpasupplicant

sudo ifup -v ath0

Configuring interface ath0=ath0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -pf /var/run/dhclient.ath0.pid -lf /var/lib/dhcp3/dhclient.ath0.leases ath0
There is already a pid file /var/run/dhclient.ath0.pid with pid 6552
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:86:c3:ce
Sending on   LPF/ath0/00:0f:b5:86:c3:ce
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.2 -- renewal in 290097 seconds.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/mountnfs
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/wpasupplicant

---

### Post by wieman01 on 2007-08-24
> **The Caped Crusader said:**
> [B]Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
[COLOR="Red"]bound to 192.168.1.2 -- renewal in 290097 seconds.[/COLOR]
Well, it's up! Can you ping the router and do you get a response?
> ping 192.168.1.1

---

### Post by The Caped Crusader on 2007-08-24
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.024 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.018 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=64 time=0.018 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=5 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=6 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=7 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=8 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=9 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=10 ttl=64 time=0.018 ms
64 bytes from 192.168.1.2: icmp_seq=11 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=12 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=13 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=14 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=15 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=16 ttl=64 time=0.018 ms
64 bytes from 192.168.1.2: icmp_seq=17 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=18 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=19 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=20 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=21 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=22 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=23 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=24 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=25 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=26 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=27 ttl=64 time=0.020 ms
64 bytes from 192.168.1.2: icmp_seq=28 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=29 ttl=64 time=0.021 ms
64 bytes from 192.168.1.2: icmp_seq=30 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=31 ttl=64 time=0.019 ms
64 bytes from 192.168.1.2: icmp_seq=32 ttl=64 time=0.020 ms

--- 192.168.1.2 ping statistics ---
32 packets transmitted, 32 received, 0% packet loss, time 31001ms
rtt min/avg/max/mdev = 0.018/0.019/0.024/0.003 ms

---

### Post by wieman01 on 2007-08-24
Well, network is definitely up & running... Can you browse the web? If not, then there might be either a DNS issue or something to do with 'ipv6'... 
> ping [www.google.com](www.google.com)

---

### Post by The Caped Crusader on 2007-08-24
wieman01, internet is running great, apart from the connection drops now and then... but what i really wanted is for ubuntu to connect automatically ideally during boot. no keyring anb no network manager asking for passwords, if possible...

is that feasible?

---

### Post by The Caped Crusader on 2007-08-24
another thing that's very annoying is whenever i boot into ubuntu (after previously have been working in windows xp) he won't cooperate into re-connecting to the router. i have to unplug and re-plug the router (do a cold reboot) and wait 1 minute before attempting to connect again with network manager.

i've made a small script, that has the following line:

gksudo /etc/init.d/networking restart

and i'll try to see if he does the trick. windows has the 'repair connection' trick, which always works when i want to renew the router's connection to the ADSL modem.

---

### Post by wieman01 on 2007-08-24
> **The Caped Crusader said:**
> another thing that's very annoying is whenever i boot into ubuntu (after previously have been working in windows xp) he won't cooperate into re-connecting to the router. i have to unplug and re-plug the router (do a cold reboot) and wait 1 minute before attempting to connect again with network manager.

i've made a small script, that has the following line:

gksudo /etc/init.d/networking restart

and i'll try to see if he does the trick. windows has the 'repair connection' trick, which always works when i want to renew the router's connection to the ADSL modem.
Yes, there is a similar script in post #2 of my HOWTO. Could you try that? It should you get hooked up right after boot.

Could you post a screenshot of your router settings? See mine for reference.

---

### Post by The Caped Crusader on 2007-08-24
> **wieman01 said:**
> Yes, there is a similar script in post #2 of my HOWTO. Could you try that? It should you get hooked up right after boot.

Could you post a screenshot of your router settings? See mine for reference.

Could you point me to that HOW-TO you're mentioning? I'll be happy to try your script.

As for the screenshots, let me see if i can post them:

[http://www.monocromatica.com/fez/Screenshot-0.png](http://www.monocromatica.com/fez/Screenshot-0.png)

[http://www.monocromatica.com/fez/Screenshot-1.png](http://www.monocromatica.com/fez/Screenshot-1.png)

Peace.

---

### Post by The Caped Crusader on 2007-08-24
****, I thought this forum auto-resized images!!

SORRY O_O

---

### Post by The Caped Crusader on 2007-08-24
Ok, better this way :)

---

### Post by wieman01 on 2007-08-25
I was referring to the WAP HOWTO as shown in my signature. :-) Post #2.

First thing you could try is to change the network channel and set it to... say... 11 to avoid inteference with other networks. Then there is the option "Enable extended range". Maybe tick this one?

You know what I mean... We should do something along these lines and test various settings, see if the situation gets any better.

---

### Post by The Caped Crusader on 2007-08-25
> **wieman01 said:**
> I was referring to the WAP HOWTO as shown in my signature. :-) Post #2.

First thing you could try is to change the network channel and set it to... say... 11 to avoid inteference with other networks. Then there is the option "Enable extended range". Maybe tick this one?

You know what I mean... We should do something along these lines and test various settings, see if the situation gets any better.

I peeked at your HOW-TO (nice work, btw) but I saw WPA2 only and gived up. My router only gives regular WPA-PSK with TKIP and I have to manage that way. In any case, around my place there are just a couple more wifi networks and no security risks whatsoever. I'll be moving out of the city next year or so, which will make the security issue pretty much non-existant.

As for the extended range setting. I'll give it a try again. Last time I used it I had more connection drops, but could have been a coincidence...

Thanks for your patience!

Peace.

---

### Post by wieman01 on 2007-08-25
> **The Caped Crusader said:**
> I peeked at your HOW-TO (nice work, btw) but I saw WPA2 only and gived up. My router only gives regular WPA-PSK with TKIP and I have to manage that way. In any case, around my place there are just a couple more wifi networks and no security risks whatsoever. I'll be moving out of the city next year or so, which will make the security issue pretty much non-existant.

As for the extended range setting. I'll give it a try again. Last time I used it I had more connection drops, but could have been a coincidence...

Thanks for your patience!

Peace.
Mate, the HOWTO is definitely relevant to you as well if you face the reconnection issue as described in post #2. Post #2 describes a workaround which fixes manual reconnecting issue after boot. Thought that applies to you as well.

---

### Post by The Caped Crusader on 2007-08-27
> **wieman01 said:**
> Mate, the HOWTO is definitely relevant to you as well if you face the reconnection issue as described in post #2. Post #2 describes a workaround which fixes manual reconnecting issue after boot. Thought that applies to you as well.

Ok, after some rough fight with Feisty Fawn and network-manager, I worked out my situation. I read somewhere about WICD connection manager and I thought: 'why not give it a try?'. I did and I completely removed network-manager, I couldn't stand the damn thing anymore!

WICD works great! Connects at boot, uses WPA1 and my password without asking me anything. I haven't had any connection drops since yesterday when I installed it. :D

I recommend it to whoever has similar problems/annoyances with network-manager/keyring frantic password asking.

Thanks wieman01 for all the effort! :)

Peace!

---

### Post by buddha.with.shades on 2008-04-20
I (almost) got everything running by following the first post of this thread. Maybe you should try to give a look there first? The link is [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by quixote on 2008-06-04
I'm running Hardy.  Suddenly in the last couple of days, the network-manager stopped activating wpasupplicant when it needed to.  So no network. :(

I found a workaround here [http://ubuntuforums.org/showthread.php?t=676117](http://ubuntuforums.org/showthread.php?t=676117) which removes all wpa settings from /etc/network/interfaces and then requires a restart (at least of dbus).  In my case, nm-applet disappears after restart, so I have to do $sudo nm-applet and keep the terminal window open for as long as I need nm-applet.  :(  :(

Judging by bug reports on Hardy, this is something that hasn't been solved yet.  

May I just say . . . AAAARRRGH!

Ahem.  Back to my actual question:  which of the many links and instructions are the best ones to follow if I want *nm-applet* to Just Work with WPA1?  

(I do use dhcp, not static IP, and my essid does not need to be hidden.)  I have an old router and I don't think it does WPA2.  I also tried wicd, but I seem to be the only person in the world who couldn't get it to wake wpasupplicant up either.  Looked nice in other respects.

---

### Post by hardingfele on 2008-06-05
hi,

i tried to establish internet access on my laptop for two wireless points, one at a library and one at home. the one at the library is unencrypted and i managed to get it working using this thread:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

and the following part out of it:
```

sudo ifconfig eth1 down
sudo dhclient -r eth1
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "DNBWLANF"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
```

and putting it into 
```

gksu gedit /etc/rc.local
```

so that it connects at boot worked fine as well.

at home i would like to use wpa1, dhcp, broadcast essid. i tried to get that working yesterday using this thread:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

and since then i don't even have ethernet anymore. i also tried to delete network manager using synaptic. was that maybe the problem? am new to ubuntu and also know very little about how all the communication work and really have no idea how to set it all up other than what i've tried (and messed up :-S).
is it actually possible to run two different kinds of connections for different places (unencrypted and WPA1)?
here is what i tried at home in more detail and i would be grateful if somebody could help :-)! thanks a lot in advance!!!

iwconfig gives:

```
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-105 dBm
          Rx invalid nwid:30060  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35490   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-105 dBm  Noise level=-95 dBm
          Rx invalid nwid:30060  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35490   Missed beacon:0
```

iwlist scan gives:
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results

wifi0     No scan results
```

unfortunatly i don't have record from before anymore...this is from the time after my cable connection had stopped working. but i definatly remember that both eth1 and wifi0 found my AP at home when i did the scanning.

i put into =>

```
sudo gedit /etc/network/interfaces 
```

the following code:

```
auto lo
iface lo inet loopback 

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid WLAN_HOME
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <ps-hex-key>
```

i also managed to get the key in hex by typing 

```
wpa_passphrase <your_essid> <your_ascii_key>
```

(8x8 hex-numbers for an 8dig-psk).

after saving i tried 

```
sudo /etc/init.d/networking restart 
```

twice, also after rebooting, and it gave (again this is from the time after things had stopped working):

```
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth1.pid with pid 5509
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:f1:fd:a0
Sending on   LPF/eth1/00:02:8a:f1:fd:a0
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 1.1.1.1 port 67
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:02:8a:f1:fd:a0
Sending on   LPF/eth1/00:02:8a:f1:fd:a0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Ignoring unknown interface wifi0=wifi0.





```

---

