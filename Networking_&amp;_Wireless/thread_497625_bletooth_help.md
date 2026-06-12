---
title: "bletooth help"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by eier on 2007-07-10
i've installed all kbluetooth and bluez utils packages,and can transfer files to my mobile phone, but i can't find my computer with my mobile phone, and sometimes when i start or restart my bluetooth i get an error that says that i need to start my sdpd.

anyone know what to do?

---

### Post by eier on 2007-07-10
with hcid -s i get one "Failed to connect to the SDP server." error message without it i get 3

---

### Post by eier on 2007-07-11
i've figured it out, i just changed my class in /etc/bluetooth/hcid.conf to class 0x000100;
and it worked.

here's my hcid.conf if anyone has the same problem:

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
	security user;

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

---

### Post by amoore on 2007-07-11
[https://help.ubuntu.com/community/BluetoothSkype]("https://help.ubuntu.com/community/BluetoothSkype")


This always works for me! I know that it contains info on skype with a BT headset but it will get file transfers going too.

---

