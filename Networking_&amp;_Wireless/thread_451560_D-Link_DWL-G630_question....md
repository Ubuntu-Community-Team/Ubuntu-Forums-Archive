---
title: "D-Link DWL-G630 question..."
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by chr3681 on 2007-05-22
Hey I just went and bought a new D-Link DWL-G630 wireless card from CompUSA in hopes to get aircrack and other wireless tools working. I have a Cisco AiroNet350, but it doesn't support the right mode needed for scanning. I was just wondering if anyone knows if there are native drivers for my new card, and how well they work, and ease of installation (if anyone else has this card). I just wanted to get these questions answered before opening the box. Thanks for your time!

---

### Post by tturrisi on 2007-05-22
Yes, the card will work fine.  It has an atheros chipset and needs the madwifi drivers which can be installed by installing the linux-restricted-modules package in Ubuntu.  The card also works well w/ kismet & aircrack-ng. I'm using that card right now.

---

### Post by chr3681 on 2007-05-22
Good news! Thanks for the quick response. I'll get back to you on here with any issues if that's alright.

Thanks again!

---

### Post by chr3681 on 2007-05-22
card works fine as far as connectivity but when i try to run kismet i get this:

sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface ath0 channel 6...
WARNING: ath0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: 'get_mode' does not return integer parameters.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

---

### Post by tturrisi on 2007-05-22
sudo gedit /etc/kismet/kismet.conf

```
# User to setid to (should be your normal user)
#suiduser= YOUR USERNAME HERE

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
#source=acx100,wlan0,acx
#source=orinoco,eth2,hermes1
#source=rt8180,wlan0,Realtek

# OTHER SOURCES
#source=prism54g,eth1,PrismGT
#source=hostap,wlan0,Prism2
#source=wlanng,wlan0,Prism2
#source=ipw2100,eth1,Centrino_b
#source=ipw2200,eth1,Centrino_g
#source=rt2500,ra0,Ralink_g
#source=rt2500,rausb0,Ralink_g
#source=kismet_drone,192.168.2.252:3501,kismet_drone

# WANT SOUND?
# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=true
# Path to sound player
soundplay=/usr/bin/aplay


```

---

### Post by chr3681 on 2007-05-22
okay i did that and kismet now works... but doesnt detect anything... here's what i found in the terminal when i exited kismet:

```
sudo kismet
Server options:  none
Client options:  none
Starting server...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (madwifi): Enabling monitor mode for madwifi_ag source interface wifi0 channel 6...
NOTICE:  Created Madwifi-NG VAP kis
WARNING: wifi0 appears to be using Madwifi-NG.  Some versions of the Madwifi-NG drivers have problems in monitor mode, especially if non-monitor VAPs are active.  If you experience problems, be sure to try the latest versions of Madwifi-NG and remove other VAPs
Waiting for server to start before starting UI...
Source 0 (madwifi): Opening madwifi_ag source interface kis...
Allowing clients to fetch WEP keys.
WARNING:  Disabling GPS logging.
SSID cloak file did not exist, it will be created.
IP track file did not exist, it will be created.
Logging networks to /var/log/kismet/Kismet-May-22-2007-1.network
Logging networks in CSV format to /var/log/kismet/Kismet-May-22-2007-1.csv
Logging networks in XML format to /var/log/kismet/Kismet-May-22-2007-1.xml
Logging cryptographically weak packets to /var/log/kismet/Kismet-May-22-2007-1.weak
Logging cisco product information to /var/log/kismet/Kismet-May-22-2007-1.cisco
Logging data to /var/log/kismet/Kismet-May-22-2007-1.dump
Writing data files to disk every 300 seconds.
Mangling encrypted and fuzzy data packets.
Tracking probe responses and associating probe networks.
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
Using network-classifier based data encryption detection
Dump file format: wiretap (local code) dump
Crypt file format: airsnort (weak packet) dump
Kismet 2006.04.R1 (Kismet)
Logging data networks CSV XML weak cisco
Listening on port 2501.
Allowing connections from 127.0.0.1/255.255.255.255
Registering builtin client/server protocols...
Registering requested alerts...
Registering builtin timer events...
Gathering packets...
Starting UI...
NOTICE:  Group file did not exist, it will be created.
Looking for startup info from localhost:2501.... found.
Connected to Kismet server 2006.04.R1 on localhost:2501
Reading AP manufacturer data and defaults from //etc/kismet/ap_manuf
Reading client manufacturer data and defaults from //etc/kismet/client_manuf
[2] + Stopped                    ${BIN}/kismet_client ${client}
Killing server...
Didn't detect any networks, unlinking network list.
Didn't detect any networks, unlinking CSV network list.
Didn't detect any networks, unlinking XML network list.
Didn't detect any Cisco Discovery Packets, unlinking cisco dump
Didn't capture any packets, unlinking dump file
Didn't see any weak encryption packets, unlinking weak file
Kismet exiting.
[1] - Done                       ${BIN}/kismet_server --silent ${server}
Kismet exited.

```

---

### Post by tturrisi on 2007-05-23
You may need the latest version of madwifi rather than the unpatched version in the restricted modules package.  This will enable it to work w/ aircrack as well:
[http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)

---

### Post by chr3681 on 2007-05-23
went well until the last step!! when i run modprobe i get this msg:

$ sudo modprobe ath_pci
FATAL: Error inserting ath_pci (/lib/modules/2.6.20-15-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

also... once this is complete, i wont have to do any of this after each restart will i?

---

### Post by tturrisi on 2007-05-23
No.
Reboot.
If no joy post dmesg output.

---

### Post by chr3681 on 2007-05-23
Okay, the card works now and I assume it's patched and everything, but when I run kismet it's still not seeing the wireless networks around me. As I am on one right now in a hotel and there was more than one option to connect to I know there are at least a couple (also they both show up with iwlist scan). =\

i was reading a tutorial for airecrack-ng and found that i have something wrong with my athx devices... a few days ago i created an athx device that was not real in order to get into monitor mode for some reason now i get this

$ sudo airmon-ng start wifi0 9


Interface       Chipset         Driver

wifi0           Atheros         madwifi-ng
ath0            Atheros         madwifi-ng VAP (parent: wifi0)
ath1            Atheros         madwifi-ng VAP (parent: wifi0) (monitor mode enabled)

which i read is wrong as i should only have one athx device. when i stop ath0 my connection is lost. when i stop ath1 nothing bad happens which lets me know that ath1 needs to be deleted. however simply doing wlanconfig ath1 destroy does nothing since as soon as i enter "sudo airmon-ng start wifi0 9" the ath1 interface comes right back. i need to get rid of the ath1 interface all together.... thanks for the help so far by the way!!

---

### Post by tturrisi on 2007-05-23
What happens when you run ksimet?  Does it just sit there doing nothing?
try this in kismet.conf:

source=madwifi_ag,ath0,madwifi
or
source=madwifi_b,ath0,madwifi

Also, since you had those restriced-modules installed, you may have to uninstall them using synaptic and reinstall the madwifi again.  The restricted packe can interfere w/ madwifi building, which is why you got that error earlier when you ran make & mak install. Found this:
[http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

---

### Post by chr3681 on 2007-05-23
i'm now at a hotel with only wireless so i can't take the interface down and still have access to the madwifi files again so i'm gonna do that in the morning and i'll post results

---

### Post by chr3681 on 2007-05-24
ok i followed the instructions at that link and got no errors this time when setting up the madwifi drivers and patching. now though when i try to run kismet i got an error saying to set source to wifiX not athX so i set it to wifi0 and now it is working. my problem now is with airodump-ng:

```
9$ sudo airodump-ng wifi0 capture1
"airodump-ng --help" for help.
```

it doesnt actually run.. which is an issue =P

any ideas?

also, how would i use kismet to pass packets to aircrack, or is that not how you go about it? because then i would not need airodump right?

---

### Post by tturrisi on 2007-05-24
[http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=79fe6ce4f12ecfc1c1fc183a93c6379b](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack&DokuWiki=79fe6ce4f12ecfc1c1fc183a93c6379b)
injection test:
[http://www.aircrack-ng.org/doku.php?id=injection_test](http://www.aircrack-ng.org/doku.php?id=injection_test)

---

