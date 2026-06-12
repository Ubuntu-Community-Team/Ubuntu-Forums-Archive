---
title: "Noob - Wireless Issues with WPA"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by Asurratt on 2008-04-04
Ok…..I’m a Noob and have been going in circles all day and finally have decided post my own post.  I have searched and searched and have made progress but now I am stumped and cannot find anything that works for me. 

I have Ubuntu 7.1 Gutsy with a wireless Broadcom 4306 with restricted driver enabled.  After reading several other posts suggested that I install Wicd and did so. I am now able to see my network (as well as others) but I’m unable to connect. I turned off all security in my netgear router to verify it works and I’m able to connect. When WPA is enabled I’m unable to connect.

I followed instructions on how to install and configure [wpa_supplican]("http://ubuntuforums.org/showthread.php?t=263136")t but still unable to connect.  Can anyone please help?

Thanks in advance!

---

### Post by cuervo73 on 2008-04-05
OK As,

We need to know more about what you have setup and what you are trying to do, in order to assist you in solving your problem.

1)  What does the wpa_supplicant logfile say?  (/var/log/wpa_supplicant.log) Any errors?  Post the last 30-40 lines in that logfile here.  (as root user, type: tail -30 /var/log/wpa_supplicant.log)

2) What does the wpa_supplicant cmdline looks like? ( ps awlx | grep wpa_supplicant )  So we can see what options/settings are being used.

3) what does your config file look like?  (/etc/wpa_supplicant.conf)  Before copying that into your reply here, replace the key value parts with asterisks so as to protect your secrets.

cuervo

---

### Post by Asurratt on 2008-04-05
1:  What does the wpa_supplicant logfile say?

 cannot open `/var/log/wpa_supplicant.log' for reading: No such file or directory


2:  What does the wpa_supplicant cmdline looks like? 

0  1000  7817  7664  17   0   2976   760 -      R+   pts/0      0:00 grep wpa_supplicant

3: what does your config file look like?

ctrl_interface=/var/run/wpa_supplicant

#ap_scan=2



network={

       ssid=”*******"

       scan_ssid=1

       proto=WPA RSN

       key_mgmt=WPA-PSK

       pairwise=CCMP TKIP

       group=CCMP TKIP

       psk=************************************************************



}

Ok so it's obvious I'm a green noob at best.  Thank you for your patience and offering to help!

---

### Post by kevdog on 2008-04-05
You have seen this thread?:[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Asurratt on 2008-04-05
WPA-PSK

(updated) wpa_supplicant.conf:

ap_scan=1

ctrl_interface=/var/run/wpa_supplicant 



network={

        ssid="Mozilla"

        scan_ssid=0

        proto=WPA

        key_mgmt=WPA-PSK

        psk="XXXXXXXXX"

        pairwise=TKIP

        group=TKIP

}



asurratt@laptop:~$ sudo wpa_supplicant -w -D bcm43xx -i eth1 -c/etc/wpa_supplicant.conf


**[COLOR="Red"]Unsupported driver 'bcm43xx'.[/COLOR]**



asurratt@laptop:~$ sudo ifconfig eth1 up

asurratt@laptop:~$ sudo iwconfig eth1 mode Managed

asurratt@laptop:~$ sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 24265

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:90:4b:45:5b:c9

Sending on   LPF/eth1/00:90:4b:45:5b:c9

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

No DHCPOFFERS received.

No working leases in persistent database – sleeping.



So, I went to the section at the bottom “References for Specific Wireless Chipsets” and followed the bcm43xx firmware but can't seem to get the firmware to load.  I guess I need someone willing to hold my hand.

Thanks guys....!!!!

---

### Post by kevdog on 2008-04-05
Ok 

First couple things,  what driver are you using -- please post lshw -C network so we can see.

I hate to tell people these things, but try consulting the man pages for wpa_supplicant (that is where I get a lot of my information).  You can do this with google, or just from the command line

man wpa_supplicant

Straight off the manual page:
Available Drivers

The available drivers to specify with the -D option are:

hostap
    (default) Host AP driver (Intersil Prism2/2.5/3). (this can also be used with Linuxant DriverLoader). 
hermes
    Agere Systems Inc. driver (Hermes-I/Hermes-II). 
madwifi
    MADWIFI 802.11 support (Atheros, etc.). 
atmel
    ATMEL AT76C5XXx (USB, PCMCIA). 
wext
    Linux wireless extensions (generic). 
ndiswrapper
    Linux ndiswrapper. 
broadcom
    Broadcom wl.o driver. 
ipw
    Intel ipw2100/2200 driver. 
wired
    wpa_supplicant wired Ethernet driver 
bsd
    BSD 802.11 support (Atheros, etc.). 
ndis
    Windows NDIS driver.

Again Im not sure if the bcm43xx driver is broadcom or simply wext (wext if the fallback driver if you don't know what to pick).  Also if you are using ndiswrapper, you want to use wext and not ndiswrapper.  Yes I know this is contrary to what the manual would suggest, however this is what the forums are for.

---

### Post by Asurratt on 2008-04-05
*-network:0

             description: Wireless interface

             product: BCM4306 802.11b/g Wireless LAN Controller

             vendor: Broadcom Corporation

             physical id: 9

             bus info: pci@0000:00:09.0

             logical name: eth1

             version: 02

             serial: 00:90:4b:45:5b:c9

             width: 32 bits

             clock: 33MHz

             capabilities: bus_master cap_list ethernet physical wireless

             configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by kevdog on 2008-04-05
So based on the info provided, your old statement:

sudo wpa_supplicant -w -D bcm43xx -i eth1 -c/etc/wpa_supplicant.conf

would either be:

sudo wpa_supplicant -w -D broadcom -i eth1 -c/etc/wpa_supplicant.conf -dd

or 

sudo wpa_supplicant -w -D wext -i eth1 -c/etc/wpa_supplicant.conf -dd

---

### Post by Asurratt on 2008-04-05
I ran both commands and posted below:

asurratt@laptop:~$ sudo wpa_supplicant -w -D bcm43xx -i broadcom -c/etc/wpa_supplicant.conf -dd

[sudo] password for asurratt:

Initializing interface 'broadcom' conf '/etc/wpa_supplicant.conf' driver 'bcm43xx' ctrl_interface 'N/A' bridge 'N/A'

Unsupported driver 'bcm43xx'.



Failed to add interface broadcom

Cancelling scan request

Cancelling authentication timeout

asurratt@laptop:~$ sudo wpa_supplicant -w -D bcm43xx -i wext -c/etc/wpa_supplicant.conf -dd

Initializing interface 'wext' conf '/etc/wpa_supplicant.conf' driver 'bcm43xx' ctrl_interface 'N/A' bridge 'N/A'

Unsupported driver 'bcm43xx'.



Failed to add interface wext

Cancelling scan request

Cancelling authentication timeout



Again,  Thank you for your assistance and patients!!!

---

### Post by kevdog on 2008-04-05
reread what I posted again ... Thanks

---

### Post by Asurratt on 2008-04-08
Kevdog, not sure how I missed the command you gave and sorry.  Must have been in a hurry since I had company.  Anyway so I ran with the broadcom command I get the error “bcm43xx unsupported.” so I ran the 2nd command you gave me: sudo wpa_supplicant -w -D wext -i eth1 -c/etc/wpa_supplicant.conf -dd. It is still running and unsure if I need to let it continue or what and how much you would like to see.  I'm a windows user and trying to make the jump but it things like this where I'm banging my head on the wall that makes me say “just forget it”and have in the past but if you and or anyone else is willing to hang in there with me and hold my hand I want to get this figured out.  I will post data below and if this is not want you want to see let me know what yosu do want.

WPA: Key negotiation completed with 00:0f:b5:20:45:72 [PTK=TKIP GTK=TKIP]

Cancelling authentication timeout

Removed BSSID 00:0f:b5:20:45:72 from blacklist

State: GROUP_HANDSHAKE -> COMPLETED

CTRL-EVENT-CONNECTED - Connection to 00:0f:b5:20:45:72 completed (reauth) [id=0 id_str=]

wpa_driver_wext_set_operstate: operstate 0->1 (UP)

WEXT: Operstate: linkmode=-1, operstate=6

EAPOL: External notification - portValid=1

EAPOL: External notification - EAP success=1

EAPOL: SUPP_PAE entering state AUTHENTICATING

EAPOL: SUPP_BE entering state SUCCESS

EAP: EAP entering state DISABLED

EAPOL: SUPP_PAE entering state AUTHENTICATED

EAPOL: SUPP_BE entering state IDLE

RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])

RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added

---

### Post by Asurratt on 2008-04-08
Had a chance to run again and this is what I got this time.  Thanks again for your help and patients:

asurratt@laptop:~$ sudo ifconfig eth1 down

[sudo] password for asurratt:

asurratt@laptop:~$ sudo dhclient -r eth1

There is already a pid file /var/run/dhclient.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:90:4b:45:5b:c9
r 
Sending on   LPF/eth1/00:90:4b:45:5b:c9

Sending on   Socket/fallback

DHCPRELEASE on eth1 to 192.168.2.1 port 67

asurratt@laptop:~$ sudo wpa_supplicant -w -D wext -i eth1 -c/etc/wpa_supplicant.conf -dd

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'

Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'

Reading configuration file '/etc/wpa_supplicant.conf'

ap_scan=1

ctrl_interface='/var/run/wpa_supplicant'

Line: 4 - start of a new network block

ssid - hexdump_ascii(len=7):

     4d 6f 7a 69 6c 6c 61                              Mozilla         

scan_ssid=0 (0x0)

proto: 0x1

key_mgmt: 0x2

PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]

pairwise: 0x8

group: 0x8

PSK (from passphrase) - hexdump(len=32): [REMOVED]

Priority group 0

   id=0 ssid='Mozilla'

Initializing interface (2) 'eth1'

EAPOL: SUPP_PAE entering state DISCONNECTED

EAPOL: KEY_RX entering state NO_KEY_RECEIVE

EAPOL: SUPP_BE entering state INITIALIZE

EAP: EAP entering state DISABLED

EAPOL: External notification - portEnabled=0

EAPOL: External notification - portValid=0

SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf

  capabilities: key_mgmt 0xf enc 0xf

WEXT: Operstate: linkmode=1, operstate=5

Own MAC address: 00:90:4b:45:5b:c9

wpa_driver_wext_set_wpa

wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0

wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0

wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0

wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0

wpa_driver_wext_set_countermeasures

wpa_driver_wext_set_drop_unencrypted

Setting scan request: 0 sec 100000 usec

Using existing control interface directory.

ctrl_iface bind(PF_UNIX) failed: Address already in use

ctrl_iface exists and seems to be in use - cannot override it

Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore

Failed to initialize control interface '/var/run/wpa_supplicant'.

You may have another wpa_supplicant process already running or the file was

left by an unclean termination of wpa_supplicant in which case you will need

to manually remove this file before starting wpa_supplicant again.



Failed to add interface eth1

State: DISCONNECTED -> DISCONNECTED

wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)

WEXT: Operstate: linkmode=-1, operstate=5

No keys have been configured - skip key clearing

EAPOL: External notification - portEnabled=0

EAPOL: External notification - portValid=0

wpa_driver_wext_set_wpa

wpa_driver_wext_set_drop_unencrypted

wpa_driver_wext_set_countermeasures

No keys have been configured - skip key clearing

Cancelling scan request

Cancelling authentication timeout

WEXT: Operstate: linkmode=0, operstate=6

asurratt@laptop:~$ sudo ifconfig eth1 up

asurratt@laptop:~$ sudo iwconfig eth1 mode Managed

asurratt@laptop:~$ sudo dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 134519120

Internet Systems Consortium DHCP Client V3.0.5

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)



Listening on LPF/eth1/00:90:4b:45:5b:c9

Sending on   LPF/eth1/00:90:4b:45:5b:c9

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

---

### Post by kevdog on 2008-04-08
Did you try to do what it stated?:


Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore

Failed to initialize control interface '/var/run/wpa_supplicant'.

You may have another wpa_supplicant process already running or the file was

left by an unclean termination of wpa_supplicant in which case you will need

to manually remove this file before starting wpa_supplicant again.


Either that or reboot?

---

### Post by Asurratt on 2008-04-09
Ok....I got the same thing I posted the first time or at least from what I can tell.  If you want to see output  let me know what portion you want to see or if you want the whole thing. Now, I feel like a complete idiot cause I can't seem to get this to work and I know I'm making it harder than it really is.  This morning I came across antoher forum post where you assisted another guy who had the same issue but also suggested ndiswrapper included below.  I am at a loss at this point and not sure which way to turn however I'm ready to scrap everything and start over and if ndiswrapper is faster and with step by step instructions  than I'm all for it.  What would do you suggest?  Keep Wicd or reinstall network manager?  Use Broadcom, wext, or ndiswrapper?  Thanks again!

kevdog
August 10th, 2007, 02:45 PM
You have a broadcom chipset.

You have two options to install the driver

bcm43xx
ndiswrapper

Do you have a preference?? bcm43xx is easier but maxes out at 11 Mb/sec Ndiswrapper requires a little bit more patient to setup but supports 54 Mb/sec. You need a windows xp driver, either on a disk or downloaded to work with ndiswrapper.

Once you decide I can give you instructions. If you decide ndiswraper DO NOT install this from repository. Its best to compile from source code -- I have the instructions if you need them.

---

### Post by Asurratt on 2008-04-10
Ok..WPA Issue resolved for now.  I disabled the broadcom driver and put a Netgear WPN511 card in.  I removed wicid and reinstalled network manger.  I also installed the madwifi as suggested by other post but not sure if it does anything....Anyway, it works but now my wireless connection is only at 70% sitting next to my Netgear router and drops to 45% if I walk 10 feet to the next room.  I disabled IPv6 but doesn't seem to make a difference.   Arghhhhh....Making progress though......

---

