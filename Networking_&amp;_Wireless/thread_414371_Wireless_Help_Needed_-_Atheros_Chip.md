---
title: "Wireless Help Needed - Atheros Chip"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by nullfactor on 2007-04-19
I just downloaded and booted via Live CD the brand spanking new version of Ubuntu.  I'm very impressed, other than the inability to connect to my WEP-enabled network via my built-in Atheros wireless adapter.

The system appears to have found the card, however I can't get a DHCP-assigned address.  I entered the following to attempt:

```
sudo iwconfig ath0 essid "xxxxx' key xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx open
```

iwconfig ath0 returns the following:
```
ath0      IEEE 802.11g  ESSID:"xxxxxx"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:31:5F:9B   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:xxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xx   Security mode:open
          Power Management:off
          Link Quality=0/94  Signal level=-93 dBm  Noise level=-93 dBm
          Rx invalid nwid:43  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Notice the Rx invalid nwid:43... should I be concerned about that?

Also, when I try a dhclient ath0, I receive the following:
```
There is already a pid file /var/run/dhclient.pid with pid 19211
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:16:e3:aa:4a:00
Sending on   LPF/ath0/00:16:e3:aa:4a:00
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Since I am a complete and utter N00B, if you need to see any log or command outputs, let me know and I will be happy to post them.

Thank you in advance.

---

### Post by tturrisi on 2007-04-19
put this in /etc/network/interfaces:

iface ath0 inet dhcp
wireless-essid YOUR-SSID
wireless-key YOUR-WEPK-EY
auto ath0

(sometimes it is necessary to use a hypen after ever 4 characters in a wep key, do that if the the key is not accepted.)

---

### Post by nullfactor on 2007-04-19
> put this in /etc/network/interfaces:

iface ath0 inet dhcp
wireless-essid YOUR-SSID
wireless-key YOUR-WEPK-EY
auto ath0

I just attempted that and restarted the interface... unfortunately, I get the same results.  Is there anything further I need to do after adding those lines?  Thanks for the input!

---

### Post by tturrisi on 2007-04-20
A couple things to try:
1. change the channel the AP uses.
2. try 64 bit hex wep instead of 128 bit.  (use 10 character key)
3. re-config your AP, likely that's where the cause of the problem lies.

It appears that you have no signal picked up by the card.  Your iwconfig Bit Rate shows 0 kb/sec.  It also shows your Security mode: "open" and should be "restricted".

Here's mine:
```
v240:~# iwconfig ath0
ath0      IEEE 802.11g  ESSID:"xxxx"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:9F:DD:04
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:30B8-0E72-81   Security mode:restricted
          Power Management:off
          Link Quality=50/94  Signal level=-42 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by nullfactor on 2007-04-20
Awesome tips.  I'll try those when I get home from work, this evening and repost whether I was met with success, or not.  Thanks, again.

Cheers.

---

### Post by nullfactor on 2007-04-20
Okay... I've tried all of the suggestions above, and I'm still having no luck.  I even turned off encryption completely to give it a try.  Nothing.  My signal is still 0/94 and I am racking up the invalid nwid's.  

Anybody have anything I could try?  I would love to ditch Windows... and this is the only thing holding me back!  Thanks!

---

### Post by tturrisi on 2007-04-20
1. remove card
2. sudo gedit /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# uncomment if use wired interface
# allow-hotplug eth0
# iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid YOURSSIDHERE

auto ath0
auto eth0
```
3. reinsert card
4. go to System>Administration>Networking
5. select wifi interface in list
6. click Properties button
7. enter or select your ssid
8. key type plain(ascii)
9. configuration dhcp
10. Ok button

If does not connect then may have to press activate button in earlier window.  make sure AP has ssid broadcast enabled.

---

### Post by nullfactor on 2007-04-20
Sadly, still no go.  

Don't know if this will help, at all, but I am using a Toshiba Satellite notebook with an Atheros (built-in) wireless adapter.  In following your previous suggestion, rather than removing the card (as it is built-in), I turned it off at the switch on the front of the computer.

If you have any other ideas, I am up for the challenge.  Thanks, as always.

---

### Post by nullfactor on 2007-04-21
Bumping this topic.  Still need help.  Thanks.

---

### Post by tturrisi on 2007-04-21
Does the laptop have a button-switch that toggles wifi on/off?

---

### Post by nullfactor on 2007-04-21
Yes... there is a toggle switch on the front of the laptop.

The good news is... I GOT IT WORKING!!!  For future use, here's how:

Download the new madwifi drivers from [http://sourceforge.net/projects/madwifi/]("http://sourceforge.net/projects/madwifi").

Once downloaded, unpack:
```
gunzip madwifi-0.9.3.tar.gz
tar xvf madwifi-0.9.3.tar
```

Install the new drivers:
```
make
make install
```

Answer "remove" when asked during the installation process, above.

Configure the card according to your network setup under System -> Administration -> Network.

If you use DHCP to obtain an address, type:

```
sudo dhclient ath0
```

Sub your interface where I have "ath0", if needed.

WIRELESS AT LAST!!!  Now, I just need to get my audio working... :)

Thank you, everybody for the help.

---

### Post by tturrisi on 2007-04-21
Very Well Done!
You now be a hacker!

re audio:
in terminal type:
alsaconf
follow thye prompts.

---

### Post by nullfactor on 2007-04-21
My hacker status has just been revoked.  Followed the alsaconfig prompts and still no audio.  My plea for help on this topic can be found at [http://ubuntuforums.org/showthread.php?p=2500808]("http://ubuntuforums.org/showthread.php?p=2500808")

---

### Post by dRock1286 on 2007-04-21
Just to let you know...and to let you feel good about yourself...I used this to get my internet back working in 7.04 (it worked fine in 6.10).  There...you helped one poor, innocent soul today.

---

### Post by Intangir on 2007-04-21
im having the exact same problem with the exact same driver

i cant get it to work with my dlink wireless card to work with my dlink router..
worked fine on dapper
worked GREAT out of the box on edgy
doesnt work on feisty.. seems to be unable to dhcp

---

