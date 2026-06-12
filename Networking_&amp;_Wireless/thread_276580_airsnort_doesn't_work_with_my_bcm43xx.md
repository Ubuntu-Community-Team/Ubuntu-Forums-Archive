---
title: "airsnort doesn't work with my bcm43xx"
date: 2006-10-13
forum: Networking &amp; Wireless
---

### Post by laurentgedm on 2006-10-13
Hi,

I just installed airsnort. I put my NIC in monitor mode, and it works with kismet (had to compile the latest version though).

But airsnort still gives me the message "you must place your card into monitor mode manually. Channel scan may not be available."

Any idea of what i could be doing wrong?

```
$ sudo iwconfig eth1
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Monitor  Frequency=2.417 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=19 dBm
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by gnomer_ on 2006-10-13
Airsnort...Packet sniffer right?

Use Ethereal, if you're sniffing wireless packets. It works really well, and requires two clicks of a button to configure.

---

### Post by laurentgedm on 2006-10-13
Actually, it's a WEP cracking tool.

I'll try other tools, but airsnort should work...

---

### Post by spd106 on 2006-10-13
You could use aircrack-ng instead [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

---

### Post by papoyan on 2008-03-23
Hello,

I have a problem with Kismet to get it working, since you were successful, could you please advise what am I doing wrong.

CentOS 5.1
Kernel 2.6.18-53.1.14.el5

I have Acer 5570z laptop with  (lspci output)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)


I tried using bcm43xx, but didn't work so I had to use ndiswrapper

Now my card is working fine, 

Here is kismet.conf file
# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=kismet

# User to setid to (should be your normal user)
suiduser=papoyan

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=bcm43xx,eth1,kismet

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:


When I start kismet, I get the following 

Launching kismet_server: /usr/local/bin/kismet_server
Will drop privs to papoyan (500) gid 500
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 (kismet): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.
[root@acer ~]#



Thank you in advance,

---

