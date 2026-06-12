---
title: "No Wireless after hours of random sys changes."
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by greyspace2004 on 2008-05-01
Help me please, I am a MS-Dos expert; however, a newbe at all Linux systems.

Question One: Is there a way I can let you, or someone accessed my "wired" system to configure, test, and resolve my "wireless less" issues?
Since it is a new and clean system I have nothing to protect...

Question Two: I would like to have Wireless, is it possible to have Wireless internet actually work on Ubuntu?

My system is as follows:
I just finished upgrading to Ubuntu released April 29 8.02
on a Dual boot Windows XP Pro System.

The Computer is a 17 inch Toshiba M60 and I would like to configure this computer to use the following Wireless interfaces:

Cardbus
DLink DWL-AG660 and I have a DWL-G650 which could be used for testing
both of which I believe use "Atheros"

Internal
Intel Corporation PRO/Wireless 2915ABG

Attached to a Dlink Router DI-624 which is configured as follows:
[http://192.168.0.1/](http://192.168.0.1/)
SSID:			greyspace
Channel:		Auto Select
Super G Mode:		Disabled  (as I found less drops on Internal card)
Extended Range: 	Enabled
WMM Function:           Enabled
802.11g Only mode:	Enabled
SSID Broadcast:		Enabled
Security:		WPA personal
Cipher type:		TKIP
PSK/EAP:		PSK
Passphrase:		dynamicXXXXX 

The Goal
Is to use Ubuntu to program MicroChips.com devices and
enjoy Wireshark type software as I am interested in Electronics and
Computers related knowledge.

Email (nospaces just as it reads)
sir douglas cook 2004 at hotmail dot com 

Confused with
Instructions never tell you how to; or where to install the package 
or what to do when unpacking, making, installing a Tar results in
a mess of errors.

What I have discovered, short version:

I have Internet via a Internet cable
And after typing a ton of commands
I was to UNPlug the Internet cable and use a undetermined Wireless
Which all disappeared after a reboot.

When I was Wireless the, "network manager"
and the "wireshark" couldn't show a the "Interface" and hence
wouldn't work.
--------------------------------------------------------------------------

Points to Ponder
==========================================================================
as root administrator
# lshw -C network
Showed that the driver is missing
for PRO/Wireless 2915ABG Network Connection
also note: network:1 UNCLAIMED
           physical id: 0
and 
# ifconfig
 shows that eth0, wifi0 doesn't have an ip address assigned to the device.

and
# dhclient
 wifi0: unknown hardware address type 801
 No DHCPOFFERS received.

and
 ping -c 4 212.58.224.131
 ping -c 4 bbc.co.uk
 both work with no packet loss.

and 
After a REBOOT I have no wireless .... again arrrrrrrrrrg
==========================================================================

---

