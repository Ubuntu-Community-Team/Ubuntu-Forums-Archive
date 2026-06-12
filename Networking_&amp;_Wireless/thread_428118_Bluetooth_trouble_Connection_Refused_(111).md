---
title: "Bluetooth trouble: Connection Refused (111)"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by hopestorm on 2007-04-30
Hello everyone,
I tried to connect my Cell phone with my IBM T23 with Ubuntu. 
If i use :
>> sudo hidd --search
Nothing is found, but if I use:
>> sudo hcitool scan
My cell phone can be found as:
00:18:AF:B0:EC:6C       MyCellPhone

I then try to connect to my cell phone via:
>> sudo hidd --connect 00:18:AF:B0:EC:6C

My cell phone ask me to input PIN to pair, I don't know what to input, then just try the PIN of the cell phone. After the input, I was given the following message on my Ubuntu terminal:
"Can't connect: Connection refused (111)"
I tried different PINs, results are the same.

Installed almost all Bluetooth packages found in Synaptic Package Manger. Something else I should try?   thanks.

---

### Post by RavanH on 2007-05-08
Hi,

Got the same problem :(

I found the bluetooth config file /etc/bluetooth/hcid.conf where is said:
> 	# Default PIN code for incoming connections
 passkey "1234";


So I'd assume that 1234 would work, but... same result :confused:

---

### Post by Chemist on 2007-05-20
has anyone had any luck with this I'm getting the same error

---

### Post by RavanH on 2007-05-21
Since my prev post, I have been able to make a connaction. Synchonizing Evolution with my mobile phone has not been without problems but at least bluetooth works... I have forgotten what finally did the trick, though, sorry :/

Just for comparison, here's my hcid.conf file content
```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security auto;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x3e0100;

	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}
```

Have you got an USB bluetooth device? And did you open Bluetooth-management (System > Preferences > Bluetooth preferences... or somthing like that - I use a dutch language version) to allow 'Other devices can connect' and change your system tray notification prefs?

---

