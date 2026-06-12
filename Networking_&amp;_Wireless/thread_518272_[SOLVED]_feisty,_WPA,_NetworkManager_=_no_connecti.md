---
title: "[SOLVED] feisty, WPA, NetworkManager = no connection"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by dcollamore on 2007-08-05
I have a broadcom 4306 wireless adapter that I just cannot get to authenticate against a WPA2, AES wireless network with NetworkManager.  I've tried with both ndiswrapper and the bcm43xx driver, with WiFi Radar, NetworkManager, and  wicd.  I can easily connect to 128 bit WEP, or to unsecured networks, but WPA appears to be a complete no-go.  Thing is, it worked perfectly with a test drive of Sabayon, and it works fine under (*cringe*) windows.  

I connect to a lot of different (often only one time) wireless networks, so statically setting entries is not going to work for me; I need the ability to easily roam.  This is a clean installation of feisty on this notebook, so I don't have any fishy configurations hanging around.  I'm just completely stumped.  Has anyone else run into this issue?  And if so, how did you go about resolving it?  Functional answers will result in instant eternal gratitude ;)!  Thanks in advance!

---

### Post by moore.bryan on 2007-08-05
*i had a ton of problems with my network and was turned-on to [wicd]("http://wicd.sourceforge.net/").  i don't know why it works and network-manager doesn't, but it works and that's all i care about.*

---

### Post by dcollamore on 2007-08-05
> **moore.bryan said:**
> *i had a ton of problems with my network and was turned-on to [wicd]("http://wicd.sourceforge.net/").  i don't know why it works and network-manager doesn't, but it works and that's all i care about.*

I gave that a shot, and I couldn't authenticate with it either...

---

### Post by moore.bryan on 2007-08-05
*did you install wpasupplicant?*

---

### Post by dcollamore on 2007-08-05
> **moore.bryan said:**
> *did you install wpasupplicant?*

Yes, wpasupplicant is installed.

---

### Post by binduwavell on 2007-08-06
I'm having this problem too. wicd seems to have the same issue. It seems to get authenticated, seems to bail getting an ip address assigned... How can I get logs out of knetworkmanager or wicd?

Any advice would be greatly appreciated!

---

### Post by imdano on 2007-08-06
The wicd log is in /opt/wicd/data/wicd.log.  Odds are the problem is with the configuration file wpa_supplicant is using though, which wouldn't show up in the wicd log.

Try this from the terminal ```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo wpa_supplicant -B -Dwext -iwlan0 -c/opt/wicd/encryption/configurations/<your router's bssid> -dd
sudo ifconfig wlan0 up
sudo dhclient wlan0
```Replace wlan0 with your wireless interface (eth1, ra1, etc), and make sure you find your access point's configuration file in /opt/wicd/encryption/configurations/ and use that with wpa_supplicant.  If that fails to connect, the problem is probably with your configuration file.  Kevdog was able to get his WPA2 AES/TKIP network to connect with this wpasupplicant.conf file
> network={
       ssid="<your essid here>"
       scan_ssid=$_SCAN
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=TKIP
       psk=<hex version of your psk here>
}You could try using that as your wpa_supplicant configuration file and see if you're able to connect.

---

### Post by kevdog on 2007-08-06
The first thing to probably do is to fish out any problems with the WPA authentication process by forcing the connection manually.  Once a problem is diagnosed, there is probably a workaround with wicd/networkmanager

Here is what I want you to do:

First set your router to WPA-PSK (WPA1) not 2.  We can change this later.

Create a /etc/wpa_supplicant.conf file:
```
gksu gedit /etc/wpa_supplicant.conf
```

With the file add the following  (Some tips are added, do not include these):

```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="<your networks essid>" <--Keep the quotes
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="ASCII Password"  <---Keep the quotes
}
```

Assuming your wireless interface name is wlan0 (if not substitute eth1,ra1,etc), do the following

```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```

If everything goes OK, you should be presented with an IP address.

---

### Post by imdano on 2007-08-06
Hey, we basically made the same post at the same time. :)

---

### Post by kevdog on 2007-08-06
Sorry, I noticed this once I typed and then submitted my scrip:KS

---

### Post by dcollamore on 2007-08-06
> **kevdog said:**
> The first thing to probably do is to fish out any problems with the WPA authentication process by forcing the connection manually.  Once a problem is diagnosed, there is probably a workaround with wicd/networkmanager

Here is what I want you to do:

First set your router to WPA-PSK (WPA1) not 2.  We can change this later.

Create a /etc/wpa_supplicant.conf file:
```
gksu gedit /etc/wpa_supplicant.conf
```

With the file add the following  (Some tips are added, do not include these):

```
ctrl_interface=/var/run/wpa_supplicant

network={
       ssid="<your networks essid>" <--Keep the quotes
       proto=WPA
       key_mgmt=WPA-PSK
       pairwise=TKIP
       group=TKIP
       psk="ASCII Password"  <---Keep the quotes
}
```

Assuming your wireless interface name is wlan0 (if not substitute eth1,ra1,etc), do the following

```
sudo ifconfig wlan0 down
sudo killall dhclient wpa_supplicant dhclient3
sudo rm /var/run/dhclient.pid
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```

If everything goes OK, you should be presented with an IP address.

Nothing, sadly.  I'm not sure where wpa_supplicant logs it's data, otherwise I'd post it.  I get no indication from dmesg or the syslog of anything happening when I manually run it.  All I see for information regarding the connection is a timeout on dhclient.

---

### Post by kevdog on 2007-08-06
So as basically you are telling me you can use every command until the last one -- then you get a no DHCP offers???

Can you connect without WPA (I didnt review the whole thread)?  Can you post your wpa_supplicant.conf file?  Is your router set for WPA (1)?  Again for me to help you, you need to confirm some of the steps suggested since  I really have no idea what you did, other than it doesnt work.

Can you post
iwlist scan

---

### Post by imdano on 2007-08-06
If you run the sudo wpa_supplicant line without the -Bw flag, you'll get debugging output in the console.

---

### Post by dcollamore on 2007-08-06
> **kevdog said:**
> So as basically you are telling me you can use every command until the last one -- then you get a no DHCP offers???

Can you connect without WPA (I didnt review the whole thread)?  Can you post your wpa_supplicant.conf file?  Is your router set for WPA (1)?  Again for me to help you, you need to confirm some of the steps suggested since  I really have no idea what you did, other than it doesnt work.

Can you post
iwlist scan

Yes, I can connect with my AP either open or configured for WEP; any WPA configuration is non-functional.  I set my AP to WPA-1, TKIP per recommendation for testing.  iwlist scan gives the following output:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:16:01:AD:25:6E
                    ESSID:"<my wireless essid>"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

My /etc/wpa_supplicant.conf is as follows, per previous entry in this thread:

network={
        ssid="<my wireless SSID>"
        proto=WPA
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="<my ASCII pre-shared key>"
}


Here is a play-by-play, one line at a time, of what happens:
-----------------------------------------------------------------------
dcollamore@mercury:~$ sudo ifconfig wlan0 down
Password:
dcollamore@mercury:~$ sudo killall dhclient wpa_supplicant dhclient3
dhclient3: no process killed
dcollamore@mercury:~$ sudo rm /var/run/dhclient.pid
dcollamore@mercury:~$ sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Daemonize..
dcollamore@mercury:~$ sudo ip route flush dev wlan0
Nothing to flush.
dcollamore@mercury:~$ sudo ifconfig wlan0 up
dcollamore@mercury:~$ sudo iwconfig wlan0 mode managed
dcollamore@mercury:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:90:4b:ed:47:7a
Sending on   LPF/wlan0/00:90:4b:ed:47:7a
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.1.157
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
dcollamore@mercury:~$ 
-----------------------------------------------------------------------------------------------
The recorded lease referenced above is a leftover of successfully connecting with 128-bit WEP.


Please, let me know if any other information would be helpful!  And thanks for the input so far! Someday I'll connect to a WPA secured network ;).

---

### Post by kevdog on 2007-08-06
Substitute this command:

```
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
```

for this

```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
```

This should give us some more debugging info.

I hate when this happens!!!

---

### Post by dcollamore on 2007-08-07
> **kevdog said:**
> Substitute this command:

```
sudo wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
```

for this

```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
```

This should give us some more debugging info.

I hate when this happens!!!

Thanks, I'll give that a try when I get home (working).  Anything in particular I should be looking for?

---

### Post by imdano on 2007-08-07
You're going to get a ton of output when you run it, just look for anything that looks like an error message.  You might want to try running ```
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -d
```Which will give less verbose debugging output and might be a little easier to follow.

---

### Post by dcollamore on 2007-08-07
Okay, so I've captured quite a bit of output from wpa_supplicant.  I watched it cycle through authentication attempts for (literally) 10 minutes straight before I stopped it.  The only things that really jumped out to me are the following several lines:

State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Authentication with 00:16:01:ad:25:6e timed out.
Added BSSID 00:16:01:ad:25:6e into blacklist
State: GROUP_HANDSHAKE -> DISCONNECTED

and:

WPA: EAPOL-Key Replay Counter did not increase - dropping packet

They seem relevant, but I wasn't able to turn up any really useful information on them.  I have reams of other data from that attempt as well, if I should be looking for anything else.  BTW, the MAC address listed above is accurate, that is my access point it's trying to authenticate with.

---

### Post by kevdog on 2007-08-07
Could you provide some more debugging output?  All I got from what you were posting is that the authentication procedure timed out.  That was basically it.

What version of ndiswrapper/wpa_supplicant are you running?
Any way you could try resetting/reflashing the router to restore factory defaults and then re-enter you specific network parameters (in the router)?

Where did you get the broadcom driver for your card -- I dont think I know any specifics about the card.

---

### Post by dcollamore on 2007-08-07
> **kevdog said:**
> Could you provide some more debugging output?  All I got from what you were posting is that the authentication procedure timed out.  That was basically it.

What version of ndiswrapper/wpa_supplicant are you running?
Any way you could try resetting/reflashing the router to restore factory defaults and then re-enter you specific network parameters (in the router)?

Where did you get the broadcom driver for your card -- I dont think I know any specifics about the card.

Sure!  Ndiswrapper is version 1.38, wpa supplicant is version 0.5.5; just the versions available in the repositories.  As for the AP, I've tried resetting and reflashing the firmware; I have a pismo powerbook that's able to connect, and I can connect with this laptop under Sabayon with any security settings, I'd just prefer to use feisty.  As for debugging info, I'll post it as an attachment so I don't swamp the board.  

The card is a standard 802.11B/G Broadcom 4306 (HP branded):
Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Again, thanks for the help!

---

### Post by kevdog on 2007-08-07
Ok the version of wpa_supplicant is OK, but your ndiswrapper version is a no-no -- 1.38 definitely is very old, and you need to update your version -- I cant promise this will make any difference however Im just trying to eliminate possibilities of why things are not working for you.  Here are some instructions (on how to uninstall, install).  You seem to know what you are doing, so I apologize for the "basic" nature of these instructions -- I usually give them to the noobies who need a thorough guide on how to due this.  If you feel comfortable, you can always make some shortcuts.  I need to review your output -- just thought I would start you on this task while Im reviewing it.

Here is how to uninstall your current ndiswrapper version:
**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

Here is how to install the newest version of ndiswrapper:
**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

---

### Post by kevdog on 2007-08-07
I read your output -- yea its a lot of stuff.  Not being a wpa_supplicant programmer it doesnt mean too much to me -- nothing obvious in there that is giving me clues why its not working!!  Ive been in the forums a while and I dont know a wpa_supplicant expert.

Hopefully upgrading the ndiswrapper version will help.  Lets find out!

---

### Post by dcollamore on 2007-08-08
> **kevdog said:**
> I read your output -- yea its a lot of stuff.  Not being a wpa_supplicant programmer it doesnt mean too much to me -- nothing obvious in there that is giving me clues why its not working!!  Ive been in the forums a while and I dont know a wpa_supplicant expert.

Hopefully upgrading the ndiswrapper version will help.  Lets find out!

As I mentioned at the beginning of this long thread, instant eternal gratitude ;).  After compiling and installing that newer release of ndiswrapper, I can authenticate to my heart's content.  WPA-2 AES with MAC filtering...WOO-HOO!  Take that cheapskate neighbors!

Note to anyone who runs across this thread, all of the poor folks having the same issue I was (trying to authenticate against WPA), in case you don't read the whole thread, it appears that compiling and installing a newer version of ndiswrapper is the solution.  Even NetworkManager is fully functional at this point.  Thanks yet again for the input and troubleshooting suggestions!

Oh, one thing I want to mention: I also had to remove the ndiswrapper module here as well - 
/lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko

As this problem presented itself on multiple clean installations of Feisty, and this seems to be the solid fix, maybe it should be written up as a howto for this specific issue:  I read TONS of threads and posts with the same issue before kevdog helped me sort it out!

---

### Post by kevdog on 2007-08-08
Glad you got it working

I'll add your suggestion, however I thought the statement
sudo rmmod ndiswrapper

did the same thing as:
/lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko

---

### Post by dcollamore on 2007-08-08
I would have thought so as well, but when I ran ndiswrapper -v after installation was complete, it was still showing the 1.38 version, and it loaded the module from that location...strange, but removing it from there specifically resolved it.

---

### Post by bittis on 2007-08-08
I am having the excact same problems, with perhaps the only diff being that i got connected for a few seconds and then everything died
I will give this a try though

---

Update: well unfortunatly i was wrong, followed you instructions step by step, got the correct version of ndiswrapper running.  I managed to connect for a few seoncds the first time, atleast the network manager said that, then it died, refuses to connect me no matter what.

---

