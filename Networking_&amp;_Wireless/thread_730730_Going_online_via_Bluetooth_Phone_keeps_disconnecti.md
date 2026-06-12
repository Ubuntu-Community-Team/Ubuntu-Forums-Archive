---
title: "Going online via Bluetooth Phone: keeps disconnecting"
date: 2008-03-21
forum: Networking &amp; Wireless
---

### Post by grenness on 2008-03-21
Here is my "rig":
Lenovo Thinkpad X60s with bluetooth capabilites
Ubuntu 7.10
KPPP 3.2.3
Treo 680 GSM smartphone with Bluetooth and GPRS data connection

Network info:
Norwegian Carrier: Ventelo, using the Telenor Mobil network

After trying on and off for several months to get my laptop online via a Bluetooth connection to my GPRS enabled Treo 680 GSM phone, I finally succeeded yesterday.
The "missing link" to get it all working was KPPP, the old PPP dialler software made for KDE. With this installed and configured I finally (after finding out I needed to run it as admin rights (sudo) got connected and was able to surf the web. For 2 minutes... It seems that after approximately 2 minutes KPPP looses contact with the Treo, and it just dies with the message "Unable to open modem.".
Restarting KPPP with the "sudo kppp" command gets me online again, but it would be cool to stay online longer, so if anyone has any idea what I have done wrong or what I shoud have done, please let me know!

The Terminal output looks like this from beginning to end:
```

[sudo] password for christopher:
kbuildsycoca running...
Error: "/var/tmp/kdecache-christopher" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-christopher" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-christopher" is owned by uid 1000 instead of uid 0.
Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 6170
Couldn't find interface ppp0: No such device
Kernel supports ppp alright.
Opener: received OpenResolv
Opener: received RemoveSecret
Opener: received RemoveSecret
It was pppd that died
pppd exited with return value 15
Sending 6143 a SIGUSR1
ioctl(SIOCGPPPSTATS): No such device
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received PPPDExitStatus
Opener: received OpenDevice
error opening modem device !
```

KPPP is configured as follows:

Login ID: [my phone number]
Password: [my phone number]


Account:

*Dial*
Phone number: *99***1#
Authentication: Script-based
Store password: yes
Callback type: none

*IP*
Dynamic

*Gateway*
Default

*DNS*
Automatic

*Login script*
[none]

*Execute*
[None]

*Accounting*
[none]


Modem:

device: /dev/rfcomm0
Flow control: Hardware
Line termination: CR
Connection speed: 115200
Use lock file: no
Modem timeout: 120 sec (max)

*Modem commands*
Init string 2: AT+cgdcont=1,IP,telenor


My /etc/bluetooth/rfcomm.conf file:
```

#
# RFCOMM configuration file.
#

rfcomm0 {
#	# Automatically bind the device at startup
	bind yes;
#
#	# Bluetooth address of the device
	device 00:07:E0:C7:C8:C2;
#
#	# RFCOMM channel for the connection
	channel	2;
#
#	# Description of the connection
	comment "Bluetooth PPP Connection";
}

```


My /etc/bluetooth/hcid.conf file:

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
	passkey "0000";
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

```


If I need to attach more info from my setup, let me know.
If anyone struggling with getting online can find any tips from the above settings, nothing would please me more (except maybe some help to make my connection a bit more persistant!)

Thanks,
Christopher

(of course posting this "on the road" using the bluetooth/gprs setup!)

---

### Post by grenness on 2008-03-21
> **grenness said:**
> Here is my "rig":
Lenovo Thinkpad X60s with bluetooth capabilites
Ubuntu 7.10
KPPP 3.2.3


Sorry, it's KPPP 2.3.2

And it's appearant to me that the 2 minute drop of connection must have something to do with the Ubuntu setup, not the phone, as I have just successfully paired the same Thinkpad with a Nokia 6310i and managed to get on line the same way as with the Treo 680, but the connection is dropped after approximately 2 mins 2 seconds just as with the Treo 680.

I'm happy that I am able to get online at all, but it is of course a bit annoying that I have to reconnect every two minutes, as you probably can imagine... ;-)

~Christopher

---

### Post by bowsercake on 2008-04-23
Did you figure out this problem? I keep getting disconnected from my bluetooth modem after about 2 mins as well.  This does not happen with I connect my phone via usb.

---

### Post by grenness on 2008-04-24
> **bowsercake said:**
> Did you figure out this problem? I keep getting disconnected from my bluetooth modem after about 2 mins as well.  This does not happen with I connect my phone via usb.

I actually did, and I'm sorry I didn't update this thread with the solution.

In /etc/ppp/peers there's a file called kppp-options.
It had just one single codeline, saying
```
noauth
```
I added the following two lines:
```
lcp-echo-failure 0
lcp-echo-interval 0
```
That did the trick, and I have had success going online via bluetooth and GPRS since, and not being hung up until I want to...

Let me know if this works for you too!

Regards,
Christopher

---

