---
title: "School Wireless"
date: 2005-05-23
forum: Networking &amp; Wireless
---

### Post by sontek on 2005-05-23
I'm cross-posting this from newbie forum. Not sure what is the best place for it.




I just completed an install of Ubuntu on my laptop. The laptop is an IBM Thinkpad R50. It was able to detect the network card but I was unable to connect to my schools network. But I am able to connect to it through the windows configuration that my school had setup on it.

Here are the settings I can see:
The WEP Key is provided for me automatically
Network Authentication: Open
Data Encryption: WEP
EAP Type: Protected EAP (PEAP) - EAP-MSChap v2


It is DHCP. We login to the network through a radius server so i'd like to do that at sometime. (Not a big deal right now)




Here is the windows ipconfig /all for it



Windows IP Configuration



Host Name . . . . . . . . . . . . : JANDERSON

Primary Dns Suffix . . . . . . . : Student.School.local

Node Type . . . . . . . . . . . . : Unknown

IP Routing Enabled. . . . . . . . : No

WINS Proxy Enabled. . . . . . . . : No

DNS Suffix Search List. . . . . . : Student.School.local

student.School.local

School.local



Ethernet adapter Wireless Network Connection:



Connection-specific DNS Suffix . : Student.School.local

Description . . . . . . . . . . . : 11a/b/g Wireless LAN Mini PCI Adapter

Dhcp Enabled. . . . . . . . . . . : Yes

Autoconfiguration Enabled . . . . : Yes

IP Address. . . . . . . . . . . . : 10.225.24.34

Subnet Mask . . . . . . . . . . . : 255.255.252.0

Default Gateway . . . . . . . . . : 10.225.24.1

DHCP Server . . . . . . . . . . . : 10.245.27.15

DNS Servers . . . . . . . . . . . : 10.245.27.3

10.245.27.10

Lease Obtained. . . . . . . . . . : Monday, May 23, 2005 9:41:17 AM

Lease Expires . . . . . . . . . . : Monday, May 23, 2005 1:41:17 PM



Ethernet adapter Local Area Connection:



Media State . . . . . . . . . . . : Media disconnected

Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Mobile Connection





Plus any tools/config files that I need to set this up would be helpful since this is my first time using ubuntu.

---

### Post by f.prisson on 2005-05-23
> Here are the settings I can see:
The WEP Key is provided for me automatically What do you mean with this?

Generelly you have to use System -> Management -> Network for configuring your wireless device. If you prefer the bash, you can also use iwconfig for configuration. You need to provide an essid and WEP key for your school's configuration.

For details you'll find a lot of Howtos about configuring WLAN on Linux.

---

### Post by Arthemys on 2005-05-23
Windows has this sketchy way of allowing a WEP key to be "given" to a client in some fashion. I've only heard of it, I've never used it or seen it in action. It must have something to do with DHCP, Group Policies or something similar.

---

### Post by f.prisson on 2005-05-23
Strange option in my opinion. As I know WEP isn't able to make any encryption without the WEP key. So if the process of getting the key is unencrypted, it maybe possible to sniff it with annother WLAN card?

---

### Post by Arthemys on 2005-05-23
This is true, my guess is that it must be obtained prior to a wireless connection is made, such as a preprovided key or something that Windows recognizes. Like I said, it's some mythical creature.

Probably why it doesn't exist in linux. ;)

---

### Post by f.prisson on 2005-05-23
Ok, about **The WEP Key is provided for me automatically** I found this in google:> If you are planning to use EAP-TLS or PEAP, which uses dynamic WEP keys, check the "The Key is provided for me automatically" check box So I think you can authenticate using wpa_supplicant, but no idea which key to use.

I think it would be a good idea to ask the responsibles for the WLAN what kind of authentication they use.

---

### Post by anders.ostling on 2005-05-24
I have used xsupplicant on Ubuntu, and here is how it works (WPA and/or WPA2)

1. You have to configure a pre-authentication method. We use Cisco ACS for VPN and WPA, so I have specified EAP-LEAP (you have another method like Pre-shared keys or MS-CHAP)

2. I did a manual association using a dummy wep key with an access point. Obviously this is needed with xsupplicant for some reason since our AP's are <hidden>

  iwconfig eth1 essid XXX
  iwconfig eth1 key 000000000000000 open

  iwconfig eth1 (should display a MAC address for the AP)

3. Run xsupplicant with proper parameters (hang on). Now this will happen

  a) xsup will send the "network username" which is my AD userid to the Cisco ACS
  b) The ACS will verify that I exist, and then return a calculated challenge token
  c) I will use my (hardcoded) windows password to create a response to the challenge.
  d) ACs will then verify that my password matched the one in Active Directory

  At this point I am authenticated. Your debug should display that fact in clear text

  e) xsup will now request a WEP key from the AP. Since the AP can "see" that you are authenticated properly, it will return that key for you.

4. Run dhclient to obtain an IP address

This seem to be not-so-well-integrated yet. I have created a script that does this for me. Exactly what changes "MS-CHAP" means for you (as I noted, we uses LEAP) I can not say. I guess that you have to edit the "mschapv2" section in the configuration file.

#!/bin/sh

rmmod ipw2100
modprobe ipw2100
ifconfig eth1 up
iwconfig eth1 essid XXXX
iwconfig eth1 key 00000000000000 open
iwconfig eth1
sleep 1
/usr/local/sbin/xsupplicant -dA -W -i eth1 -c /etc/xsupplicant/xsupplicant.conf
sleep 1
dhclient eth1

My config file looks like this (change AD-xyz and network_list)

root@ubuntu:/etc/xsupplicant # cat xsupplicant.conf
network_list = XXXX (ie ESSID)
default_netname = default
startup_command = <BEGIN_COMMAND>iwconfig eth1 essId XXX<END_COMMAND>
first_auth_command = <BEGIN_COMMAND>dhclient %i<END_COMMAND>
logfile = /var/log/xsupplicant.log
allow_interfaces = eth1
deny_interfaces = eth0, sit0, lo, vmnet8, cipsec0

XXXX
{
  type = wireless
  wireless_control = yes
  allow_types = eap-leap
  identity = <BEGIN_ID>AD-DOMAIN\AD-USERID<END_ID>
  eap-leap {
      username = <BEGIN_UNAME>AD-DOMAIN\\AD-USERID<END_UNAME>
      password = <BEGIN_PASS>AD-PASSWORD<END_PASS>
  }

  eap-mschapv2 {
      username = <BEGIN_UNAME>eapmschapv2user<END_UNAME>
      password = <BEGIN_PASS>eapmschapv2userpass!<END_PASS>
  }
}

There is one catch here. I had problems with the ubuntu version of xsupplicant, so I built a newer one from source (1.2PRE). I have seen that parameters and config options have changed between the two, so you might need to experiment a bit...

Hope that this helps to explain how WPA2 works

Anders

---

