---
title: "Bluetooth on 8.04 detects adapter but not display icon"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Clivemunday on 2008-08-23
Hi,

I have just installed Ubuntu 8.04 on my laptop and it seems to work well apart from Bluetooth. It detects the adapter I have and in the command line interface I can bring the interface up and scan and find other devices. I cannot connect to anything. No Bluetooth icon appears to manage Bluetooth. I installed kbluetooth and can use the OBEX client to send files to another laptop this is the only connection I can make and it connects for the transfer then disconnects. If I run kbluetooth it says no adapter is attached. I have been at this for hours can anyone help me? I am a complete beginner with linux.

Best regards,
Clive

---

### Post by bunny rabbit on 2008-08-23
Hi, I'm kind of a n00b myself but maybe this will suffice>

Search in synaptic for things like bluez-gnome, gnome bluetooth, libpam blue and so forth. 
Then go to *system*->*preferences*->*sessions* and check the box for bluetooth manager if it isn't already.
Also when you go to *system*->*administration*->*services* you may find a box for bluetooth device management that can be checked.

regards

---

### Post by Clivemunday on 2008-08-23
Thanks Bunny Rabbit,

I looked at all of this and the packages are definitely installed. System->preferences->Sessions Bluetooth Manager is checked and System->Administration->Services Bluetooth Device Management is checked.
It seems like the Bluetooth Manager is not recognizing the adapter even though the system says there is one and I can work with it from a console as below:
clive@clive-laptop:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:00:00:00:00:00 ACL MTU: 0:0 SCO MTU: 0:0
        DOWN
        RX bytes:0 acl:0 sco:0 events:0 errors:0
        TX bytes:0 acl:0 sco:0 commands:0 errors:0

clive@clive-laptop:~$ hciconfig hci0 up
Can't init device hci0: Permission denied (13)
clive@clive-laptop:~$ sudo hciconfig hci0 up
[sudo] password for clive:
clive@clive-laptop:~$ hciconfig
hci0:   Type: USB
        BD Address: 00:1B:10:00:12:B5 ACL MTU: 1017:8 SCO MTU: 64:0
        UP RUNNING
        RX bytes:348 acl:0 sco:0 events:11 errors:0
        TX bytes:38 acl:0 sco:0 commands:11 errors:0

clive@clive-laptop:~$

The device at system start is always down but comes up with no issues. I can do a scan once it is up:

clive@clive-laptop:~$ hcitool scan
Scanning ...
        00:1C:CC:C6:F6:15       BlackBerry 8707
clive@clive-laptop:~$

I can find any other device I turn on in range.
My hcid.conf file is posted below I made changes based on some threads I read:

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
	passkey "1111";
        pin_helper /usr/bin/bluez-pin;

}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	# name "%h-%d";
        name "clive";

	# Local device class
	class 0x000100;

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

I hope this gives enough information for someone to help.

Best regards,
Clive

---

### Post by Clivemunday on 2008-08-30
I have managed to get this working by downgrading to bluez-utils_3.9-0ubuntu4_i386. File is available from here:

[http://de.archive.ubuntu.com/ubuntu/pool/main/b/bluez-utils/](http://de.archive.ubuntu.com/ubuntu/pool/main/b/bluez-utils/)

YOu have to remove previous version and bluez-audio to get it too install.

Best regards,
Clive

---

