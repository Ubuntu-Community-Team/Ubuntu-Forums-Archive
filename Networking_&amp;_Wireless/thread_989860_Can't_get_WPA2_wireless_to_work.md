---
title: "Can't get WPA2 wireless to work"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by chr75 on 2008-11-22
Hi

Been working with Ubuntu 8.04 for a couple of months now, and I can only get wireless to work without encryption, which is a no-go for me - I want to use the WPA2 encryption.

I've tried so many things and read so many posts that I'm just about ready to give up, but I hope someone on this forum can help me!

I suspect that the problem might be with the configuration of wpa_supplicant in combination with wicd.

I will give you the content of the following commands
Sudo lshw -C network
Sudo iwconfig
sudo iwlist scan
content of /etc/wpa_supplicant.conf
content of /etc/network/interfaces

**christian@Christian:~$ ****sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:0b:5d:95:95:d4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751m-v3.40a latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 05
       serial: 00:15:00:02:20:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=32 link=no maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

**christian@Christian:~$ sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2304 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**christian@Christian:~$ sudo iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: my_routers_ap_adress
                    ESSID:"my ssid"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

**content of /etc/wpa_supplicant.conf**
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
ap_scan=1

network={
	ssid="my ssid"
#	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
#	auth_alg=OPEN
	pairwise= CCMP TKIP
	group= CCMP TKIP
	psk=my hex key
}

**content of /etc/network/interfaces**
auto lo
iface lo inet loopback

iface wlan0 inet dhcp

auto wlan0

Allright, that was a lot of information - hope it's useful!

Any ideas on how to resolve the problem?

---

### Post by chr75 on 2008-11-24
Anyone got an idea to solve my problem?

---

### Post by meastwood on 2008-11-24
seems to be a lot of issues over this though works fine for me:

Assumptions: Card driver supports WPA2, Router set-up for WPA2

Two ways that I have done this -
1. the Ubuntu way
 (a) plug your card in
 (b) # ifconfig
 wlan0  Link encap:Ethernet  HWaddr 00:1f:1f:08:ce:28  

        UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

        RX packets:6 errors:0 dropped:0 overruns:0 frame:0

        TX packets:11 errors:0 dropped:0 overruns:0 carrier:0

        collisions:0 txqueuelen:1000 

        RX bytes:1604 (1.5 KB)  TX bytes:1940 (1.8 KB)


wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-08- 
                CE-28-00-00-00-00-00-00-00-00-00-00 
          		 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 (c) desktop: System->Network (Network Settings – Wireless connection – properties)
   WIRELESS SETTINGS:
     Network Name (should be listed): MINE-KEEP-OUT
     Password Type: WPA 2 Personal 
     Network Password: ************
   CONNECTION SETTINGS:
     Configuration: DHCP
     IP Address:
     Subnet Mask:
     Gateway:
click ok and network manager will then configure the device
 (d) Check it -
  # ps -ef | grep [Ww]pa

root 7229  1  0 18:05 ?   00:00:00 /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D wext -C /var/run/wpa_supplicant

wpa_supplicant must be running. When using the gui as above wpa_supplicant.conf is NOT created and NOT used, instead configuration details are put into /etc/network/interfaces and wpa_supplicant daemon is run with -C <path/to/socket>.
/etc/network/interfaces should include:
-------------------------
  iface wlan0 inet dhcp
  wpa-psk cde99b40af92ac77341ba8f053bb5abeaa63b5be068be378ee6ea5d0045bb734
  wpa-driver wext
  wpa-key-mgmt WPA-PSK
  wpa-proto WPA2
  wpa-ssid MINE-KEEP-OUT

  auto wlan0
--------------------------
you may want to change the driver (wpa-driver)

2. the manual way - NOT using gui
 (a) generate the Passphrase key into hex 
  # wpa_passphrase <essid> <pass-key> >> /etc/wpa_supplicant.conf
 (b) edit /etc/wpa_supplicant.conf
--------------
  ctrl_interface=/var/run/wpa_supplicant
  network={
    ssid="MINE-KEEP-OUT"
    key_mgmt=WPA-PSK
    proto=WPA
    psk=768620f80a8619a9d88b6867f074d01d3836f3fb11735b 917bf3ac6b790895b7
  }
----------------
 (c) edit /etc/network/interfaces
----------------
  # wireless network device using DHCP
  iface wlan0 inet dhcp
  wpa-driver ralink
  wpa-conf /etc/wpa_supplicant.conf   
  auto wlan0
-----------------
**** your driver and interface name may be different.
**** wpa-conf points to your wpa_supplicant.conf file
 (d) take interface down/up
  # ifdown wlan0
  # ifup wlan0
 (e) check as for 1(d) above - you should see that the 'ps -ef | grep -i [Ww]pa daemon is now running with -c /path/to/wpa_supplicant.conf and -D <your driver i.e. ralink in my case>. Also run
  # iwlist wlan0 auth 
  wlan0 Authentication capabilities :
  WPA
  WPA2
  CIPHER-TKIP
  CIPHER-CCMP
  ................................
  Current TKIP countermeasures : yes
  Current Drop unencrypted : yes
  Current Authentication algorithm :
  open (used by WPA)
  shared-key
  LEAP
................................ 

If problems a good place to start is
# ifup --verbose wlan0

Read the docs in /usr/src/doc/wpasupplicant/
The above is for Managed mode, the docs mentioned above cover a lot more.

---

### Post by chr75 on 2008-11-25
Yes, the card driver supports WPA2 (I'm using the wext driver) and the router is already set up to run WPA2 - I'm using it for a windows laptop where it works fine.

Ok, I followed the manual steps described in the post above, but when I got to the part with ifdown and ifup I got some error messages.

**christian@Christian:~$ sudo ifdown wlan0**
ifdown: interface wlan0 not configured


**christian@Christian:~$ sudo ifup wlan0**
Line 8: invalid proto 'wpa'
Line 8: no proto values configured.
Line 8: failed to parse proto 'wpa'.
Line 14: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:00:02:20:25
Sending on   LPF/wlan0/00:15:00:02:20:25
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
receive_packet failed on wlan0: Network is down
Terminated
Failed to bring up wlan0.

EDIT:
Also here the ouput for the grep command
christian@Christian:~$ ps -ef | grep [Ww]pa
root     15693     1  0 20:34 ?        00:00:00 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/0002cf916d00 -D ndiswrapper
root     15712  4965  0 20:34 ?        00:00:00 /bin/sh -c wpa_cli -i wlan0 status
root     15713 15712  0 20:34 ?        00:00:00 [wpa_cli] <defunct>


Any ideas on how to remove the errors? As you can see, I'm quite new to Ubuntu and Linux so please bare with me:)

---

### Post by meastwood on 2008-11-26
sorry but I made a mistake ....
(b) edit /etc/wpa_supplicant.conf
--------------
ctrl_interface=/var/run/wpa_supplicant
network={
ssid="MINE-KEEP-OUT"
key_mgmt=WPA-PSK
***proto=WPA***
psk=768620f80a8619a9d88b6867f074d01d3836f3fb11735b 917bf3ac6b790895b7
}

should read
proto=WPA2

the ***proto=WPA*** works for an old laptop of mine but i built  the wireless related stuff from source as the driver for my card was not built-in/supported .... when I just tried the same configuration on my ubuntu 8.04.1 PC it didn't work!! so I changed the proto line and it's working again.

do this anyway - that's what the unknown prot error is about and lets see what happens from here

---

### Post by meastwood on 2008-11-26
also noticed that you are using the ndiswrapper - should still work after you've made the change from the previous post ....
however:

wpa_supplicant supports your driver (ref: /usr/share/doc/wpasupplicant/README) => no need to build support into wpa_supplicant
[INDENT]"Intel ipw2200 driver
(http://sourceforge.net/projects/ipw2200/)" I used [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net)[/INDENT]

Just checking that the module is the right driver:
# modinfo -d ipw2200
[INDENT]Intel(R) PRO/Wireless 2200/2915 Network Driver[/INDENT]
# modinfo -n ipw2200
[INDENT]/lib/modules/2.6.24-21-generic/kernel/drivers/net/wireless/ipw2200.ko[/INDENT]

Checking that firmware is there:
# find /lib/firmware/2.6.24-21-generic -name ipw22*
/lib/firmware/2.6.24-21-generic/ipw2200-sniffer.fw
[I]/lib/firmware/2.6.24-21-generic/ipw2200-ibss.fw
/lib/firmware/2.6.24-21-generic/ipw2200-bss.fw[/I]

Checking that all required kernel parameters are set, which they are => no need to re-build kernel
# grep -i -E -e '.*(_net_rad|_fw_loa|crypto=|ieee80211=|ipw2200=|crypto_[acm][rie][sc][^=]).*[ym]$' /boot/config-2.6.24-21-generic
CONFIG_CRYPTO=y
CONFIG_CRYPTO_AES_586=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_CRC32C=m
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_FW_LOADER=y
CONFIG_IEEE80211=m
CONFIG_IPW2200=m

Therefore you should'nt need to use (last resort) ndiswrapper :(- can test by:
# ifdown wlan0
check wpa_supplicant has exited
# ps -ef | grep [Ww]pa
Run wpa_supplicant in foreground in debug mode using new driver '-Dipw'
Did this on my system - sure its the wrong driver for card, but wpa_supplicant confirms support for the ipw driver
# wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -Dipw -d
[I]Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='MINE-KEEP-OUT'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called[/I]
************* then the errors start flying pass

If it works okay then simply edit /etc/network/interfaces file to use the 'decent :)' driver
wpa-driver ipw

---

### Post by chr75 on 2008-11-26
Ok, the good news is that by replacing proto=WPA with proto=WPA2, I got rid of two of the errors displayed by the grep command, and now I'm stuck with only the following error/line.

root     11777     1  0 23:13 ?        00:00:00 wpa_supplicant -B -i wlan0 -c /var/lib/wicd/configurations/0002cf916d00 -D ndiswrapper

I have edited/viewed the file /var/lib/wicd/configurations/0002cf916d00 but it is empty - don't know if that is the problem?

You're right about the IPW2200 being the native linux driver for my card, and the only reason I shifted to ndiswrapper was to try something else, and then I didn't know how to switch back:)

I've made the check suggested in your previous post, and everything seemed right except the kernel parameters do not match yours. I have the following:
christian@Christian:~$ grep -i -E -e '.*(_net_rad|_fw_loa|crypto=|ieee80211=|ipw2200=|c rypto_[acm][rie][sc][^=]).*[ym]$' /boot/config-2.6.24-21-generic
CONFIG_CRYPTO=y
CONFIG_FW_LOADER=y
CONFIG_IEEE80211=m
CONFIG_IPW2200=m

...which means that I dont have the same parameters set as you have...could that be the problem?

Anyways, when I run the ifdown wlan0 it always tell me that wlan0 is not configured, and when I then run the manual wpa_supplicant in foreground I get loads of errors.

[B]christian@Christian:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -Dipw -d
[/B]Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='MY SSID'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Linux wireless extensions version 22 detected.
ipw2x00 driver uses driver_wext (-Dwext) instead of driver_ipw.
Own MAC address: my_mac_address
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
ctrl_iface bind(PF_UNIX) failed: Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

I guess the wpa_supplicant is not exited because the command ifdown wlan0 could not be executed?

Though the problem is not solved I have the feeling that we are closing in on it! Thanks so far for the support - it's great to get some much appreciated help:)

---

### Post by kevdog on 2008-11-26
Dont use ifdown ifup, use ifconfig wlan0 up and ifconfig wlan0 down

Also for the -D parameter passed to wpa_supplicant -- try wext

---

### Post by meastwood on 2008-11-27
I agree with previous post - use the wext driver. 

I guess to take all interfaces up/down cleanly should use
# /etc/init.d/networking  { stop | start | restart }

from the output:
[I]"Linux wireless extensions version 22 detected.
ipw2x00 driver uses driver_wext (-Dwext) instead of driver_ipw"[/I]

Looks like support for ipw2* has been built into the wext driver. 

From errors reported it looks as tho' wpa_supplicant doesn't like some/a lot of the ipw driver calls. Maybe the version of the ipw2200 driver shipped is different than that used to build the version of wpa_supplicant that is shipped - which is why wext has to be used ...

When building a rt73 driver for my laptop I had to not only compile the driver but had to re-build wpa_supplicant to include support for the new driver.

On my PC however, with rt73 support built in to the kernel (as for ipw), I cannot use the 'ralink/rt73' driver as on the laptop but have to use wext. 

So it looks as though wext is providing some sort of wrapper functionality for supported drivers and thereby providing a common interface to wpa_supplicant - just guessing mind. It would make maintaining the software easier.

Instead of using my attempted smart-**** :( grep cmd to check for all the config parameters in one go just look for the 'missing ones' separately i.e.
# grep CONFIG_CRYPTO_AES_586 /boot/config-2.6.24-21-generic
# grep CONFIG_CRYPTO_ARC4 /boot/config-2.6.24-21-generic
# grep CONFIG_CRYPTO_CRC32C /boot/config-2.6.24-21-generic
# grep CONFIG_CRYPTO_MICHAEL_MIC /boot/config-2.6.24-21-generic
These modules handle the encryption methods that can be used - I'ld have thought they would have been enabled by default. If you are wanting to use WPA2-AES then yes, the relevant module is required.

I can't help for ndiswrapper - would rather buy another card than use it:). **For me**, I'ld just (remove)purge the ndiswrapper packages - this will unconfigure it for you!! - assuming nothing else is using them.

This will tell you what ndis stuff you have installed
# dpkg-query -s $(dpkg-query -W 'ndis*')
If you are interested in which configuration files were installed with the package
# dpkg-query -W -f='${Conffiles}\n' <package-name>
To purge
# dpkg -P <package-name> 
or use the package manager (probably safer) from the desktop (complete uninstall of package = purge)

---

### Post by chr75 on 2008-11-27
Using the sudo /etc/init.d/networking restart command as well as the sudo ifconfig wlan0 down and up did not do a difference.

I have now removed the ndiswrapper using the add/remove utility, and also I have made a complete uninstall using the synaptic tool. 
I then edited the /etc/network/interfaces to set the driver to wext and restarted the laptop.

After restart there was no wlan0, and I now get an error upon startup that not everything is working correctly (dont recall the exact error message). Also everything is now really slow - e.g. when I ran the sudo gedit /etc/network/interfaces command it took several minutes before the window opened.

I guess it's because wlan0 could not be configured - I just don't know how to get wlan0 up and running again. I've tried running the wpa_supplicant in foreground, but it just complains that wlan0 is not present.

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0 -Dwext -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Priority group 0
   id=0 ssid='MY SSID'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'wlan0' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
WEXT: SIOCSIWAUTH(param 7 value 0x0) failed: No such device)
Failed to disable WPA in the driver.
wpa_driver_wext_set_drop_unencrypted
WEXT: SIOCSIWAUTH(param 5 value 0x0) failed: No such device)
wpa_driver_wext_set_countermeasures
WEXT: SIOCSIWAUTH(param 4 value 0x0) failed: No such device)
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
ioctl[SIOCSIWAP]: No such device
WEXT: Operstate: linkmode=0, operstate=6
ioctl[SIOCGIFFLAGS]: No such device

Seems that removing ndiswrapper was a setback, but should be able to get wlan0 up and running again without ndiswrapper, since wlan0 was up and running before I installed ndiswrapper in the first place.

Running the command modprobe IPW2200 seems to have some sort of effect in the sense that I now have a new wireless network - eth1 (and not wlan0). I think that eth1 was also the name of the network before I got ndiswrapper. The modprobe command will only work for the current session, so I have to run it manually again after the next restart. How do I make it permanent?

---

### Post by meastwood on 2008-11-28
add module to /etc/modules  file.

Check dmesg for any boot errors. Can you provide another listing of 
# lsmod

---

### Post by meastwood on 2008-11-28
also the contents of
/etc/modprobe.d/blacklist file

---

### Post by meastwood on 2008-11-28
also if device is being configured as eth1 on boot then use -ieth1 instead of iwlan0. It will definately fail if told to use an interface that does'nt exist.

---

### Post by chr75 on 2008-11-28
I dont have a file named /etc/modules - should I just create that? I have /etc/modprobe.d and /etc/modutils but no files in those folders are named modules.

For DMESG I ran the following - not entirely sure if it's the right way to call dmesg for this purpose.
**christian@Christian:~$ dmesg | grep -e ndis -e wlan**
[   27.094994] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.798913] usbcore: registered new interface driver ndiswrapper

Also the lsmod output...
[B]
christian@Christian:~$ lsmod[/B]
Module                  Size  Used by
ipv6                  267780  8 
i915                   32512  2 
drm                    82452  3 i915
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_centrino      9152  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  1 
cpufreq_powersave       2688  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
bay                     6912  0 
dock                   11280  1 bay
sbs                    15112  0 
sbshc                   7680  1 sbs
container               5632  0 
af_packet              23812  2 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
lp                     12324  0 
joydev                 13120  0 
pcmcia                 40876  0 
irda                  203068  0 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
crc_ccitt               3072  1 irda
evdev                  13056  6 
snd_hda_intel         344856  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
video                  19856  0 
output                  4736  1 video
serio_raw               7940  0 
psmouse                40336  0 
snd_seq_dummy           4868  0 
sdhci                  19076  0 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket
mmc_core               51460  1 sdhci
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic
battery                14212  0 
button                  9232  0 
ac                      6916  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
ndiswrapper           192920  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
intel_agp              25492  1 
pcspkr                  4224  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                34760  3 drm,intel_agp
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ext3                  136840  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
ahci                   28548  0 
usbhid                 32128  0 
hid                    38784  1 usbhid
ohci1394               33584  0 
ata_piix               19588  2 
ieee1394               93752  2 sbp2,ohci1394
libata                159344  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
tg3                   116228  0 
usbcore               146412  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              37384  2 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 

Content of /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

---

### Post by meastwood on 2008-11-28
do'nt see why not - here's an example
 ls -al modules
-rw-r--r-- 1 root root 213 2008-09-08 14:39 modules
root@cpc1-burn5-0-0-cust66:/etc# cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
loop
lp
sbp2
fuse

you should just put your module in however 'lsmod' is showing that the ndiswrapper is loaded which may cause a conflict.

before doing anything can you post the output of 
# lspci

---

### Post by chr75 on 2008-11-28
sure, heres the output...

**christian@Christian:~$ sudo lspci**
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
06:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 20)
06:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by meastwood on 2008-11-28
things have got a little bit confusing :) can try again 
first: 
check that the correct interface is used (ifconfig) wlan0, eth1 whatever is your wireless card
# sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i<interface> -Dwext -dd
then try:
# sudo modprobe -r ndiswrapper 
# sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i<interface> -Dwext -dd
# sudo modprobe -r ipw2200 
# sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i<interface> -Dwext -dd

and post the output

---

### Post by chr75 on 2008-11-28
I have corrected /etc/network/interfaces to use the correct/new interface eth1, and I have inserted ipw2200 in /etc/modules.

Running sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext -dd gave me a lot of errors that kept looping/coming, so I had to interrupt the command.

Then I ran the modprobe -r ndiswrapper command followed by sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext -dd, and again with the same result (errors kept coming).

Then I ran the modprobe -r ipw2200 followed by sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext -dd, this time errors only came once:confused:

christian@Christian:~$ sudo modprobe -r ipw2200 
christian@Christian:~$ sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth1 -Dwext -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 5 - start of a new network block
ssid - hexdump_ascii(len=16):
     53 69 65 6d 65 6e 73 20 57 69 72 65 6c 65 73 73   MY SSID
proto: 0x2
key_mgmt: 0x2
pairwise: 0x18
group: 0x18
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='my ssid'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth1' UP
ioctl[SIOCGIWRANGE]: No such device
WEXT: Operstate: linkmode=1, operstate=5
ioctl[SIOCGIFINDEX]: No such device
Failed to add interface eth1
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
ioctl[SIOCSIWENCODE]: No such device
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
WEXT: SIOCSIWAUTH(param 7 value 0x0) failed: No such device)
Failed to disable WPA in the driver.
wpa_driver_wext_set_drop_unencrypted
WEXT: SIOCSIWAUTH(param 5 value 0x0) failed: No such device)
wpa_driver_wext_set_countermeasures
WEXT: SIOCSIWAUTH(param 4 value 0x0) failed: No such device)
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
ioctl[SIOCSIWAP]: No such device
WEXT: Operstate: linkmode=0, operstate=6
ioctl[SIOCGIFFLAGS]: No such device

---

### Post by gnusci on 2008-11-28
try including everything in the **/etc/network/interfaces**, here an example:

[PHP]
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 up
        pre-up ifconfig wlan0 down
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 channel 2
        pre-up iwconfig wlan0 essid "WLAN-ESSID-HERE"
        pre-up iwconfig wlan0 mode managed 
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK="************"
        pre-up ifconfig wlan0 up

[/PHP]

and then run the command:

**$ /etc/init.d/networking restart**

---

### Post by meastwood on 2008-11-28
ndiswrapper and ipw2200 seem to be conflicting with wext. So while we are still trying to get this working you need to 
# moprobe -r ndiswrapper ipw2200
before running the wpa_supplicant command

looking at other posts etc.  many people have included the following lines in wpa_supplicant.conf.  May be worth adding to see the effect

*ctrl_interface=/var/run/wpa_supplicant*
ctrl_interface_group=0

eapol_version=1
ap_scan=1   # wpa_supplicant initiates scanning and AP selection
fast_reauth=1

*network { ....*

---

### Post by meastwood on 2008-11-29
From what I've managed to find out there seems to be a bug with using wpa and ndiswrapper (and wext) when using some drivers. The problem being that either wpa_supplicant or the driver is unable to associate with an AP when brought up automatically. This is what the output from last attempt is saying - it can't associate with an AP:

as you've said wext works using WEP.

A possible work around is as gnusci's post suggests - put all cmds into the interfaces file and 'bounce' the interface a couple of times before configuring it. The interface needs to associate with an AP before it can be configured.

I came across another 'cmd' that worked for some people on earlier versions of linux:
- setting the card to "G" mode using (don't know what G mode is mind): 
iwpriv eth1 mode 3
which you may wish to try. May need to check the format when used with pre-up

---

### Post by kevdog on 2008-11-29
If you type 
wpa_supplicant -h
This will list the available driver types you can use with the command.  As of intrepid the only types are the following:
drivers:
  wext = Linux wireless extensions (generic)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wired = wpa_supplicant wired Ethernet driver

Note that ipwxxxx/madwifi are no longer options.  I don't think this means however they don't work since I know for a fact madwifi work work with the generic wext driver.


If you ever look into compiling wpa_supplicant from scatch, wpa_supplicant is compiled against the sources of the particular drivers.  If you want to use madwifi or ipw for example you would have to download the source for the drivers (freely available) along with the wpa_supplicant package, and then compile them together.  I recently did this as an experiment (made no difference), however this is what I was able to produce:

drivers:
  wext = Linux wireless extensions (generic)
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  ndiswrapper = Linux ndiswrapper
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver
  
I guess I could have added more driver types, however I just kind of gave up.

---

### Post by chr75 on 2008-11-29
Ok, I have tried first what Gnusci suggested, entering the following in /etc/network/interfaces:

#auto lo
#iface lo inet loopback

auto eth1
iface eth1 inet dhcp
	pre-up ifconfig eth1 up
	pre-up ifconfig eth1 down
	pre-up ifconfig eth1 up
	pre-up iwconfig eth1 channel 6
	pre-up iwconfig eth1 essid "My SSID"
	pre-up iwconfig eth1 mode managed
	pre-up iwpriv eth1 set AuthMode=WPAPSK
	pre-up iwpriv eth1 set EncryptType=TKIP
	pre-up iwpriv eth1 set WPAPSK="my HEX passkode"
	pre-up ifconfig eth1 up
wpa-driver wext
#wpa-ssid Siemens Wireless
#wpa-ap-scan 2
#wpa-proto WPA
#wpa-pairwise CCMP
#wpa-key-mgmt WPA-PSK
#wpa-psk 94a028f26426db9ce87965d5bcd75162d23075a0b7f936db56196b7b202ccecb
wpa-conf /etc/wpa_supplicant.conf 

...and then running /etc/init.d/networking restart gave me this result

christian@Christian:~$ sudo /etc/init.d/networking restart
[sudo] password for christian: 
 * Reconfiguring network interfaces...                                                                                                         Invalid command : set
Failed to bring up eth1.

I'm gonna remove the 'set' part tomorrow (too late now:)), but it just takes so long to edit the file, since after I removed ndiswrapper just opening a file takes 5 minutes - something is definately not healthy on my laptop right now.

I have also previously wondered about the message that it cant associate with the AP, but I always attributed that to a wrong setup of wpa_supplicant, since I use the same drivers and "setup" when connecting wireless without encryption at all. But as kevdog suggest, it might be because ndiswrapper and ipw2200 does not work with wpa_supplicant.

After removing ndiswrapper I inserted modprobe ipw2200 in the /etc/modules file - should I remove that again? If I do, I will not have a wireless interface after reboot, so do I replace that with something else?

Sorry about all the newbie questions :)

---

### Post by chr75 on 2008-11-29
Having removed the 'set' part, the /etc/init.d/networking restart command now returns this:

christian@Christian:~$ sudo /etc/init.d/networking restart
[sudo] password for christian: 
 * Reconfiguring network interfaces...                                                                                                         Invalid command : AuthMode=WPAPSK
Failed to bring up eth1.

---

### Post by kevdog on 2008-11-29
iwpriv statements are only for ra based cards, not intel chipsets.  I wouldn't use these statements if I were you.  In fact I would only connect try to use the command line since better debugging output can be displayed.  Additionally, you need to check /var/log/syslog for any clues what might be failing.  In fact if you pop open multiple terminal windows, you can run:
sudo tail -f /var/log/syslog
for a continuosly updated syslog file you can read on the fly.  

You need to start providing error messages in addition to configuration options for us to help you appropriately.  I have no idea why the ipw2200 module isn't working -- and a lot of us don't even have this chipset.  In fact I have no idea what driver you are using. 

It is your responsibility to post useful information if you want your problem to be resolved quickly.  It is not our information to drag the information out of you.

---

### Post by chr75 on 2008-11-30
Ok, I have removed the ipriw statements and removed the modprobe ipw2200 from the /etc/modules file.

Regarding errors, youre quite right that I should post all the errors I come across. Already during boot I get the following error, which started to appear after I removed ndiswrapper:
"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

Then everything works (except WPA2 encrypted wireless) - but the system is incredibly slow.

In order to find the error I have run DMESG with the following output:
**christian@Christian:~$ dmesg**
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-22-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Nov 24 18:32:42 UTC 2008 (Ubuntu 2.6.24-22.45-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f680000 (usable)
[    0.000000]  BIOS-e820: 000000001f680000 - 000000001f696000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f696000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0010000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 128640) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   128640
[    0.000000]   HighMem    128640 ->   128640
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128640
[    0.000000] On node 0 totalpages: 128640
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 973 pages used for memmap
[    0.000000]   Normal zone: 123571 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5690 checksum 0
[    0.000000] ACPI: RSDP 000F5690, 0014 (r0 FUJ   )
[    0.000000] ACPI: RSDT 1F68F57F, 0040 (r1 FUJ    FJNB199   1100000 FUJ       100)
[    0.000000] ACPI: FACP 1F695F8C, 0074 (r1 FUJ    FJNB199   1100000 FUJ       100)
[    0.000000] ACPI: DSDT 1F68F5BF, 60C7 (r1 FUJ    FJNB199   1100000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F696FC0, 0040
[    0.000000] ACPI: APIC 1F695686, 005A (r1 FUJ    FJNB199   1100000 FUJ       100)
[    0.000000] ACPI: SSDT 1F6956E0, 0235 (r1 FUJ    FJNB199   1100000 INTL 20030522)
[    0.000000] ACPI: SSDT 1F695B25, 013F (r1 FUJ    FJNB199   1100000 INTL 20030522)
[    0.000000] ACPI: SSDT 1F695D01, 0227 (r1 FUJ    FJNB199   1100000 INTL 20030522)
[    0.000000] ACPI: MCFG 1F695F28, 003C (r1 FUJ    FJNB199   1100000 FUJ       100)
[    0.000000] ACPI: BOOT 1F695F64, 0028 (r1 FUJ    FJNB199   1100000 FUJ       100)
[    0.000000] ACPI: DMI detected: Fujitsu Siemens
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127635
[    0.000000] Kernel command line: root=UUID=8364d226-ccfc-4860-abe0-9a422ba590a9 ro acpi=force noapic quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1729.092 MHz processor.
[    8.771729] Console: colour VGA+ 80x25
[    8.771734] console [tty0] enabled
[    8.771894] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.772103] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.783000] Memory: 498052k/514560k available (2177k kernel code, 15904k reserved, 1005k data, 368k init, 0k highmem)
[    8.783008] virtual kernel memory layout:
[    8.783009]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.783010]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.783011]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[    8.783013]     lowmem  : 0xc0000000 - 0xdf680000   ( 502 MB)
[    8.783014]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.783015]       .data : 0xc0320704 - 0xc041bdc4   (1005 kB)
[    8.783016]       .text : 0xc0100000 - 0xc0320704   (2177 kB)
[    8.783020] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.783057] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.863054] Calibrating delay using timer specific routine.. 3461.85 BogoMIPS (lpj=6923714)
[    8.863079] Security Framework initialized
[    8.863087] SELinux:  Disabled at boot.
[    8.863102] AppArmor: AppArmor initialized
**[    8.863106] Failure registering capabilities with primary security module.**
[    8.863115] Mount-cache hash table entries: 512
[    8.863236] Initializing cgroup subsys ns
[    8.863241] Initializing cgroup subsys cpuacct
[    8.863251] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.863261] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.863264] CPU: L2 cache: 2048K
[    8.863267] CPU: After all inits, caps: afe9fbff 00100000 00000000 00042040 00000180 00000000 00000000 00000000
[    8.863275] Compat vDSO mapped to ffffe000.
[    8.863287] Checking 'hlt' instruction... OK.
[    8.879425] SMP alternatives: switching to UP code
[    8.881261] Freeing SMP alternatives: 11k freed
[    8.881362] Early unpacking initramfs... done
[    9.231713] ACPI: Core revision 20070126
[B][    9.231783] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[/B][    9.234385] ACPI: setting ELCR to 0200 (from 0800)
[    9.264402] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    9.264423] Total of 1 processors activated (3461.85 BogoMIPS).
[    9.370939] Brought up 1 CPUs
[    9.370955] CPU0 attaching sched-domain:
[    9.370957]  domain 0: span 01
[    9.370959]   groups: 01
[    9.371132] net_namespace: 64 bytes
[    9.371142] Booting paravirtualized kernel on bare hardware
[    9.371589] Time:  9:14:53  Date: 11/30/08
[    9.371613] NET: Registered protocol family 16
[    9.371799] EISA bus registered
[    9.371827] ACPI: bus type pci registered
[    9.372028] PCI: PCI BIOS revision 2.10 entry at 0xfd842, last bus=7
[    9.372031] PCI: Using configuration type 1
[    9.372045] Setting up standard PCI resources
[    9.374749] ACPI: EC: Look up EC in DSDT
[    9.381182] ACPI: Interpreter enabled
[    9.381185] ACPI: (supports S0 S3 S4 S5)
[    9.381200] ACPI: Using PIC for interrupt routing
[    9.387687] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.388376] Force enabled HPET at base address 0xfed00000
[    9.388382] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.388387] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    9.389218] PCI: Transparent bridge - 0000:00:1e.0
[    9.389301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.389690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.389884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    9.389981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    9.392867] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.392968] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.393065] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    9.393162] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.393258] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.393355] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.393452] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    9.393549] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    9.393666] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.393697] pnp: PnP ACPI init
[    9.393703] ACPI: bus type pnp registered
[    9.397696] pnp: PnP ACPI: found 12 devices
[    9.397698] ACPI: ACPI bus type pnp unregistered
[    9.397702] PnPBIOS: Disabled by ACPI PNP
[    9.397904] PCI: Using ACPI for IRQ routing
[    9.397906] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.397912] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    9.397914] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    9.397917] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    9.422919] NET: Registered protocol family 8
[    9.422921] NET: Registered protocol family 20
[    9.423074] hpet clockevent registered
[    9.423080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.423084] hpet0: 3 64-bit timers, 14318180 Hz
[    9.424118] AppArmor: AppArmor Filesystem Enabled
[    9.426878] Time: tsc clocksource has been installed.
[    9.434908] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[    9.434914] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    9.434917] system 00:02: ioport range 0x800-0x80f has been reserved
[    9.434920] system 00:02: ioport range 0x1000-0x107f has been reserved
[    9.434923] system 00:02: ioport range 0x1080-0x10ff has been reserved
[    9.434925] system 00:02: ioport range 0x1100-0x111f has been reserved
[    9.434928] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    9.434931] system 00:02: ioport range 0xf800-0xf87f has been reserved
[    9.434934] system 00:02: ioport range 0xf880-0xf8ff has been reserved
[    9.434937] system 00:02: ioport range 0xfc00-0xfc7f has been reserved
[    9.434940] system 00:02: ioport range 0xfc80-0xfcff has been reserved
[    9.434942] system 00:02: ioport range 0xfd00-0xfd7f has been reserved
[    9.434945] system 00:02: ioport range 0xfe00-0xfe01 has been reserved
[    9.434948] system 00:02: iomem range 0xf0000000-0xf0003fff could not be reserved
[    9.434952] system 00:02: iomem range 0xf0004000-0xf0004fff could not be reserved
[    9.434955] system 00:02: iomem range 0xf0005000-0xf0005fff could not be reserved
[    9.434958] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    9.434961] system 00:02: iomem range 0xfec00000-0xfec00fff could not be reserved
[    9.434964] system 00:02: iomem range 0xfee00000-0xfee00fff could not be reserved
[    9.434967] system 00:02: iomem range 0xfef00000-0xfeffffff could not be reserved
[    9.434970] system 00:02: iomem range 0xcf200-0xcf7ff has been reserved
[    9.434973] system 00:02: iomem range 0xffb00000-0xffbfffff could not be reserved
[    9.465363] PCI: Bridge: 0000:00:1c.0
[    9.465365]   IO window: disabled.
[    9.465370]   MEM window: b0100000-b01fffff
[    9.465375]   PREFETCH window: disabled.
[    9.465380] PCI: Bridge: 0000:00:1c.1
[    9.465382]   IO window: disabled.
[    9.465387]   MEM window: disabled.
[    9.465391]   PREFETCH window: disabled.
[    9.465404] PCI: Bus 7, cardbus bridge: 0000:06:03.0
[    9.465406]   IO window: 00001800-000018ff
[    9.465412]   IO window: 00001c00-00001cff
[    9.465418]   PREFETCH window: 34000000-37ffffff
[    9.465422]   MEM window: 38000000-3bffffff
[    9.465427] PCI: Bridge: 0000:00:1e.0
[    9.465429]   IO window: disabled.
[    9.465434]   MEM window: b0200000-b02fffff
[    9.465438]   PREFETCH window: disabled.
[    9.465619] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    9.465622] PCI: setting IRQ 11 as level-triggered
[    9.465626] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    9.465634] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.465795] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    9.465797] PCI: setting IRQ 10 as level-triggered
[    9.465802] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    9.465810] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.465823] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.465839] ACPI: PCI Interrupt 0000:06:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    9.465852] NET: Registered protocol family 2
[    9.502906] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.503091] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.503184] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    9.503279] TCP: Hash tables configured (established 16384 bind 16384)
[    9.503281] TCP reno registered
[    9.514953] checking if image is initramfs... it is
[    9.926710] Switched to high resolution mode on CPU 0
[   10.202402] Freeing initrd memory: 7328k freed
[   10.202652] Simple Boot Flag at 0x7f set to 0x1
[   10.203035] audit: initializing netlink socket (disabled)
[   10.203051] audit(1228036493.288:1): initialized
[   10.205050] VFS: Disk quotas dquot_6.5.1
[   10.205131] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.205276] io scheduler noop registered
[   10.205278] io scheduler anticipatory registered
[   10.205280] io scheduler deadline registered
[   10.205291] io scheduler cfq registered (default)
[   10.205304] Boot video device is 0000:00:02.0
[   10.205502] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.205554] assign_interrupt_mode Found MSI capability
[   10.205600] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.205638] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.205730] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.205781] assign_interrupt_mode Found MSI capability
[   10.205821] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.205854] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.206096] isapnp: Scanning for PnP cards...
[   10.560223] isapnp: No Plug & Play device found
[   10.586441] Real Time Clock Driver v1.12ac
[   10.586549] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.586695] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.586965] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[   10.587422] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.588158] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.588226] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.588324] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.591068] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.592472] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.592476] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.592479] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.592481] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.592483] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.602439] mice: PS/2 mouse device common for all mice
[   10.602545] EISA: Probing bus 0 at eisa.0
[   10.602553] Cannot allocate resource for EISA slot 1
[   10.602583] EISA: Detected 0 cards.
[   10.602586] cpuidle: using governor ladder
[   10.602588] cpuidle: using governor menu
[   10.602678] NET: Registered protocol family 1
[   10.602704] Using IPI No-Shortcut mode
[   10.602735] registered taskstats version 1
[   10.602843]   Magic number: 0:407:223
[   10.602859]   hash matches device ttyu7
[   10.602865]   hash matches device ttyra
[   10.602917] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.602919] EDD information not available.
[   10.603113] Freeing unused kernel memory: 368k freed
[   10.603140] Write protecting the kernel read-only data: 801k
[   10.638379] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.812363] fuse init (API version 7.9)
[   11.830664] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.351682] tg3.c:v3.86 (November 9, 2007)
[   12.351712] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   12.351724] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   12.440764] usbcore: registered new interface driver usbfs
[   12.440788] usbcore: registered new interface driver hub
[   12.441011] eth0: Tigon3 [partno(BCM95751M) rev 4101 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:0b:5d:95:95:d4
[   12.441017] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   12.441020] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   12.445648] usbcore: registered new device driver usb
[   12.457619] USB Universal Host Controller Interface driver v3.0
[   12.457890] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   12.457894] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.457906] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.457910] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.458253] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.458284] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001420
[   12.458418] usb usb1: configuration #1 chosen from 1 choice
[   12.458441] hub 1-0:1.0: USB hub found
[   12.458447] hub 1-0:1.0: 2 ports detected
[   12.521775] SCSI subsystem initialized
[   12.561860] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.561865] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.561878] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.561883] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.561906] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.561935] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001440
[   12.562043] usb usb2: configuration #1 chosen from 1 choice
[   12.562065] hub 2-0:1.0: USB hub found
[   12.562071] hub 2-0:1.0: 2 ports detected
[   12.585541] libata version 3.00 loaded.
[   12.665809] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   12.665815] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.665827] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.665832] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.665856] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.665887] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001460
[   12.665998] usb usb3: configuration #1 chosen from 1 choice
[   12.666021] hub 3-0:1.0: USB hub found
[   12.666027] hub 3-0:1.0: 2 ports detected
[   12.769575] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   12.769591] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.769595] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.769620] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.769648] uhci_hcd 0000:00:1d.3: irq 10, io base 0x00001480
[   12.769755] usb usb4: configuration #1 chosen from 1 choice
[   12.769778] hub 4-0:1.0: USB hub found
[   12.769784] hub 4-0:1.0: 2 ports detected
[   12.873637] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   12.873652] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.873657] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.873681] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   12.877580] ehci_hcd 0000:00:1d.7: debug port 1
[   12.877586] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.877593] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xb0004000
[   12.893411] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.893515] usb usb5: configuration #1 chosen from 1 choice
[   12.893539] hub 5-0:1.0: USB hub found
[   12.893545] hub 5-0:1.0: 8 ports detected
[   12.997635] ata_piix 0000:00:1f.1: version 2.12
[   12.997660] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   12.997695] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.998761] scsi0 : ata_piix
[   12.999321] scsi1 : ata_piix
[   12.999976] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1410 irq 14
[   12.999980] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1418 irq 15
[   13.421186] Clocksource tsc unstable (delta = -22616615178 ns)
[   13.425249] Time: hpet clocksource has been installed.
[   13.427192] ata1.00: ATAPI: UJDA750FDVD/CDRW, 1.22, max UDMA/33
[   13.433837] ata1.00: configured for UDMA/33
[   13.433888] ata2: port disabled. ignoring.
[   13.434364] scsi 0:0:0:0: CD-ROM            MATSHITA UJDA750FDVD/CDRW 1.22 PQ: 0 ANSI: 5
[   13.434441] ata_piix 0000:00:1f.2: MAP [ P0 P2 -- -- ]
[   13.438892] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   13.438927] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.438965] scsi2 : ata_piix
[   13.439100] scsi3 : ata_piix
[   13.439154] ata3: SATA max UDMA/133 cmd 0x14b8 ctl 0x140c bmdma 0x14a0 irq 11
[   13.439157] ata4: SATA max UDMA/133 cmd 0x14b0 ctl 0x1408 bmdma 0x14a8 irq 11
[   13.443562] ata3.00: ATA-8: FUJITSU MHW2080BH, 00000012, max UDMA/100
[   13.443566] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   13.444366] ata3.00: configured for UDMA/100
[   13.458927] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0000 PQ: 0 ANSI: 5
[   13.460224] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   13.460227] ACPI: PCI Interrupt 0000:06:06.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   13.509989] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b0204800-b0204fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.527692] Driver 'sd' needs updating - please use bus_type methods
[   13.527792] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   13.527804] sd 2:0:0:0: [sda] Write Protect is off
[   13.527807] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.527822] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.527868] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   13.527877] sd 2:0:0:0: [sda] Write Protect is off
[   13.527879] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.527894] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.527897]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   13.539793] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   13.539796] Uniform CD-ROM driver Revision: 3.20
[   13.539839] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   13.545980]  sda5 >
[   13.546066] sd 2:0:0:0: [sda] Attached SCSI disk
[   13.555233] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   13.555253] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   13.635371] Attempting manual resume
[   13.635375] swsusp: Resume From Partition 8:5
[   13.635376] PM: Checking swsusp image.
[   13.635513] PM: Resume from disk failed.
[   13.651197] kjournald starting.  Commit interval 5 seconds
[   13.651206] EXT3-fs: mounted filesystem with ordered data mode.
[   13.702541] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e100360cdfd]
[   16.488355] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   16.924074] intel_rng: FWH not detected
[   16.956080] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.008085] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.096008] Linux agpgart interface v0.102
[   17.273452] irda_init()
[   17.273469] NET: Registered protocol family 23
[   17.306586] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x8f8eb1, caps: 0xa04793/0x102000
[   17.306592] serio: Synaptics pass-through port at isa0060/serio4/input0
[   17.366625] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input3
[   17.391825] parport_pc 00:0b: reported by Plug and Play ACPI
[   17.391873] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   17.435888] agpgart: Detected an Intel 915GM Chipset.
[   17.436351] agpgart: Detected 7932K stolen memory.
[   17.454996] agpgart: AGP aperture is 256M @ 0xc0000000
[   17.587907] input: Power Button (FF) as /devices/virtual/input/input4
[   17.619773] ACPI: Power Button (FF) [PWRF]
[   17.619853] input: Lid Switch as /devices/virtual/input/input5
[   17.635846] ACPI: Lid Switch [LID]
[   17.635898] input: Power Button (CM) as /devices/virtual/input/input6
[   17.640293] found SMC SuperIO Chip (devid=0x5a rev=00 base=0x002e): LPC47N227
[   17.640314] smsc_superio_flat(): fir: 0x400, sir: 0x2e8, dma: 03, irq: 3, mode: 0x0e
[   17.640320] smsc_ircc_present: can't get sir_base of 0x2e8
[   17.667739] ACPI: Power Button (CM) [PWRB]
[   17.686519] iTCO_vendor_support: vendor-support=0
[   17.726950] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   17.727039] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   17.727074] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.796922] ACPI: AC Adapter [AC] (on-line)
**[   17.947809] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)**
[   17.957437] ACPI: Battery Slot [CMB1] (battery present)
[   17.957488] ACPI: Battery Slot [CMB2] (battery absent)
**[   17.973901] usbcore: registered new interface driver ndiswrapper**
[   17.988624] Yenta: CardBus bridge found at 0000:06:03.0 [10cf:131e]
[   17.988658] Yenta O2: res at 0x94/0xD4: 00/ea
[   17.988660] Yenta O2: enabling read prefetch/write burst
[   18.116149] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[   18.116155] Socket status: 30000006
[   18.116158] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   18.116164] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   18.409012] sdhci: Secure Digital Host Controller Interface driver
[   18.409017] sdhci: Copyright(c) Pierre Ossman
[   18.409063] sdhci: SDHCI controller found at 0000:06:03.2 [1217:7120] (rev 0)
[   18.409089] ACPI: PCI Interrupt 0000:06:03.2[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   18.409112] sdhci:slot0: Unknown controller version (16). You may experience problems.
[   18.409156] mmc0: SDHCI at 0xb0204000 irq 10 PIO
[   18.774755] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   18.799257] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.640480] ACPI: PCI Interrupt 0000:00:1b.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   19.640508] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.512178] cs: IO port probe 0x100-0x3af: clean.
[   21.513824] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
[   21.514526] cs: IO port probe 0x820-0x8ff: clean.
[   21.515132] cs: IO port probe 0xc00-0xcf7: clean.
[   21.515878] cs: IO port probe 0xa00-0xaff: clean.
[   21.552576] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input8
[   22.134749] lp0: using parport0 (interrupt-driven).
[   22.298591] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x008b2001
[   22.317843] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
[   22.396608] EXT3 FS on sda1, internal journal
[   22.737347] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.365331] No dock devices found.
[   23.367275] ACPI: \_SB_.PCI0.PATA.PRIM.MAST: found ejectable bay
[   23.367282] ACPI: \_SB_.PCI0.PATA.PRIM.MAST: Adding notify handler
[   23.367312] ACPI: Error installing bay notify handler
[   23.367315] ACPI: Bay [\_SB_.PCI0.PATA.PRIM.MAST] Added
[   23.920797] apm: BIOS not found.
[   23.964479] ppdev: user-space parallel port driver
[   23.983893] audit(1228036540.893:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4891 profile="/usr/sbin/cupsd" namespace="default"
[   52.069457] Marking TSC unstable due to: cpufreq changes.
[   54.206673] Bluetooth: Core ver 2.11
[   54.207435] NET: Registered protocol family 31
[   54.207441] Bluetooth: HCI device and connection manager initialized
[   54.207448] Bluetooth: HCI socket layer initialized
[   54.257253] Bluetooth: L2CAP ver 2.9
[   54.257261] Bluetooth: L2CAP socket layer initialized
[   25.093890] Bluetooth: RFCOMM socket layer initialized
[   25.093903] Bluetooth: RFCOMM TTY layer initialized
[   25.093905] Bluetooth: RFCOMM ver 1.8
[   54.563355] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   54.563362] tg3: eth0: Flow control is on for TX and on for RX.
[   27.137104] [drm] Initialized drm 1.1.0 20060810
[   27.140297] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   27.140305] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   27.140366] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   27.309860] NET: Registered protocol family 17
[   61.599808] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   61.599817] tg3: eth0: Flow control is on for TX and on for RX.
[   49.690529] NET: Registered protocol family 10
[   49.691111] lo: Disabled Privacy Extensions
[   66.354318] eth0: no IPv6 routers present
[  357.446000] tg3: eth0: Link is down.
[  384.012543] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  384.012552] tg3: eth0: Flow control is on for TX and on for RX.
[  386.962889] tg3: eth0: Link is down.
[  387.148682] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  387.148690] tg3: eth0: Flow control is on for TX and on for RX.

Seems that it still loads ndiswrapper even though I totally removed it - will include ndiswrapper in the blacklist file and check if that helps.

EDIT: After blacklisting, I will restart and run the wpa_supplicant commands in foreground and post the result here!

---

### Post by kevdog on 2008-11-30
I dont recall if you've told us anything about your chipset.  Because ndiswrapper is a third party kernel module (it was not compiled into the distribution) you don't need to blacklist it.  You just remove the line from the /etc/modules file -- that is where you specified it to be loaded.  blacklist built-in kernel modules, specify that third party kernel modules be loaded in the /etc/modules file.

---

### Post by meastwood on 2008-11-30
After removing ndiswrapper from /etc/modules and checking dmesg that it is not loaded and the system is **still slow **check the last few entries of /var/log/messages and run
# top -c
let it refresh a few times and look at the top processes esp. %cpu & %mem columns - if you can post the ouput even better. (press 'q') to quit. This is a side issue to wpa.

If all agree I think one problem is that different things are tried and things start to get messy. So need to decide on a common approach to try and get the thing working - for me this would be 
- use wext driver: 
make sure ndiswrapper and ipw2200 are not loaded or referenced anywhere. As kevdog said, when you
# wpa_supplicant -h
....
*ipw = Intel ipw2100/2200 driver (old; **use wext with Linux 2.6.13 or newer**)*
....
- use /etc/network/interfaces file for configuring the interface:
this approach has been used successfully to 'work around' associating with AP problems, in which case, correct me if I'm wrong, there does not need to be any reference to wpa_supplicant.conf in the interfaces file

you can then try various configurations to try and get it working.

if still no joy then you can either try using ndiswrapper using the link supplied by kevdog - bearing in mind that there have been similar issues reported with ndiswrapper. 

or
get the source for your driver (ipw2200) and wpa_supplicant v0.5.8 ,build the driver (may need openssl 0.9.8g. source) and build wpa_supplicant with support for the new driver. Replace the old wpa_supplicant binaries and use the newly built ipw driver instead of wext and revert back to using wpa_supplicant.conf. 

How to do this will be documented in the source code READMEs. However, I can understand that this can be quite daunting if you are new to this sort of thing - rarely is the build process 'pain' free so you do need to have some understanding of how to interpret and correct compile errors if and when they occur. 

I'm not a developer and still managed to rebuild wpa_supplicant with rt73/ralink support. In this case the READMEs were very good.

---

### Post by chr75 on 2008-11-30
Chipset - arrgh not really certain what it is - how can I check? I have previously posted the ouput of lspci, and have now done it again and pasted in a few selected lines below...

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
**02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)**
06:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 20)
06:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller
**06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)**
06:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)


I agree on the approach and would like to make sure that ndiswrapper and ipw2200 are not used in any way. However, when I edit the /etc/modules file, there is no entry regarding ndiswrapper - this is the content of the file as it has always looked.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2

System is still slow - took 6 minutes just to open the file.

I would still prefer to make sure that ndiswrapper is not loaded, but alternatively I could upgrade to 8.10, if you think that would help. 
The whole part of getting the source for the driver and building wpa_supplicant is somewhat out of my league I think - ultimately I would have to use a cable in stead.

Just to make sure I have posted below some of the output of /var/log/messages

Nov 30 17:11:40 Christian kernel: [   21.697429] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input8
Nov 30 17:11:40 Christian kernel: [   21.946984] cs: IO port probe 0x100-0x3af: clean.
Nov 30 17:11:40 Christian kernel: [   21.948657] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x407
Nov 30 17:11:40 Christian kernel: [   21.949352] cs: IO port probe 0x820-0x8ff: clean.
Nov 30 17:11:40 Christian kernel: [   21.949947] cs: IO port probe 0xc00-0xcf7: clean.
Nov 30 17:11:40 Christian kernel: [   21.950695] cs: IO port probe 0xa00-0xaff: clean.
Nov 30 17:11:40 Christian kernel: [   22.008246] lp0: using parport0 (interrupt-driven).
Nov 30 17:11:40 Christian kernel: [   22.055968] Adding 1477940k swap on /dev/sda5.  Priority:-1 extents:1 across:1477940k
Nov 30 17:11:40 Christian kernel: [   22.134675] EXT3 FS on sda1, internal journal
Nov 30 17:11:40 Christian kernel: [   22.476595] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 30 17:11:40 Christian kernel: [   23.104501] No dock devices found.
Nov 30 17:11:40 Christian kernel: [   23.106482] ACPI: Bay [\_SB_.PCI0.PATA.PRIM.MAST] Added
Nov 30 17:11:40 Christian kernel: [   23.657722] apm: BIOS not found.
Nov 30 17:11:41 Christian kernel: [   23.701399] ppdev: user-space parallel port driver
Nov 30 17:11:41 Christian kernel: [   23.720741] audit(1228061501.369:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4870 profile="/usr/sbin/cupsd" namespace="default"
Nov 30 17:11:41 Christian kernel: [   30.858937] Marking TSC unstable due to: cpufreq changes.
Nov 30 17:11:44 Christian dhcdbd: Started up.
Nov 30 17:11:45 Christian kernel: [   53.630035] Bluetooth: Core ver 2.11
Nov 30 17:11:45 Christian kernel: [   53.630796] NET: Registered protocol family 31
Nov 30 17:11:45 Christian kernel: [   53.630802] Bluetooth: HCI device and connection manager initialized
Nov 30 17:11:45 Christian kernel: [   53.630809] Bluetooth: HCI socket layer initialized
Nov 30 17:11:45 Christian kernel: [   24.775720] Bluetooth: L2CAP ver 2.9
Nov 30 17:11:45 Christian kernel: [   24.775725] Bluetooth: L2CAP socket layer initialized
Nov 30 17:11:45 Christian kernel: [   24.833504] Bluetooth: RFCOMM socket layer initialized
Nov 30 17:11:45 Christian kernel: [   24.833518] Bluetooth: RFCOMM TTY layer initialized
Nov 30 17:11:45 Christian kernel: [   24.833520] Bluetooth: RFCOMM ver 1.8
Nov 30 17:11:45 Christian kernel: [   53.986750] tg3: eth0: Link is up at 100 Mbps, full duplex.
Nov 30 17:11:45 Christian kernel: [   53.986758] tg3: eth0: Flow control is on for TX and on for RX.
Nov 30 17:11:49 Christian kernel: [   26.760880] NET: Registered protocol family 17
Nov 30 17:11:49 Christian kernel: [   35.306701] [drm] Initialized drm 1.1.0 20060810
Nov 30 17:11:49 Christian kernel: [   35.314654] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Nov 30 17:11:49 Christian kernel: [   35.314744] [drm] Initialized i915 1.6.0 20060119 on minor 0
Nov 30 17:11:51 Christian kernel: [   28.265427] tg3: eth0: Link is up at 100 Mbps, full duplex.
Nov 30 17:11:51 Christian kernel: [   28.265432] tg3: eth0: Flow control is on for TX and on for RX.
Nov 30 17:12:01 Christian kernel: [   66.715039] NET: Registered protocol family 10
Nov 30 17:12:01 Christian kernel: [   66.715775] lo: Disabled Privacy Extensions
Nov 30 17:31:40 Christian -- MARK --

...and here is the output of the command top -c

Tasks: 109 total,   2 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  0.7%sy,  0.0%ni, 95.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    505980k total,   490204k used,    15776k free,     4720k buffers
Swap:  1477940k total,   116460k used,  1361480k free,    49612k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                      
 5212 root      20   0  486m 116m 5524 S  1.7 23.6   3:50.75 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7                     
 4657 root      15  -5     0    0    0 R  0.7  0.0   0:09.52 [kondemand/0]                                                                                
 5787 christia  20   0 25068  15m 6244 S  0.7  3.1   0:14.62 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id def
12855 christia  20   0  194m  94m  18m S  0.7 19.1   1:52.75 /usr/lib/firefox-3.0.4/firefox                                                               
15779 root      20   0  2308 1112  852 R  0.7  0.2   0:00.10 top -c                                                                                       
    1 root      20   0  2844 1428  508 S  0.0  0.3   0:01.16 /sbin/init                                                                                   
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [kthreadd]                                                                                   
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 [migration/0]                                                                                
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [ksoftirqd/0]                                                                                
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 [watchdog/0]                                                                                 
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 [events/0]                                                                                   
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 [khelper]                                                                                    
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 [kblockd/0]                                                                                  
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 [kacpid]                                                                                     
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 [kacpi_notify]                                                                               
  130 root      15  -5     0    0    0 S  0.0  0.0   0:00.38 [kseriod]                                                                                    
  163 root      20   0     0    0    0 S  0.0  0.0   0:00.04 [pdflush]                                                                                    
christian@Christian:~$

EDIT: Looking through the links by kevdog, I saw that one guy stated that he could only get WPA2 to work with a max 8 char long passcode. My passcode is 16 char long, but the router is provided by my employer and is pre-setup with a fixed SSID and passcode (and the WPA2 encryption is also fixed), so I can't change it...If this is true (8 char), I will never get it to work! Another thing is that my SSID is two separate words - is that a problem?

EDIT2: Reading through kevdog's excellent guide, I see that ndiswrapper=wext - so shouldn't ndiswrapper still be loaded then?

---

### Post by meastwood on 2008-11-30
if wext requires/uses ndiswrapper then the module will be dynamically loaded.

the output from 'top' is not revealing anything. Snapshots rarely do, though sometimes you can strike lucky.  Tho' I did not realise how hungry firefox is!!! 

I have a final suggestion &#8211; a shot in the dark based on some old stuff I've read about this card and AP association. It concerned ndiswrapper and WEP not WPA however ....
Basically &#8211; set the key before associating
maybe worth a try e.g.
.................
pre-up iwconfig eth1 channel 6
pre-up iwconfig eth1 mode managed
[I]pre-up iwpriv eth1 setAuthMode WPAPSK
pre-up iwpriv eth1 setEncryptType TKIP
pre-up iwpriv eth1 setWPAPSK "my HEX passkode"[/I]
pre-up iwconfig eth1 essid "My SSID"
..............

***** you need to check the syntax of the iwpriv command - I just had a quick glance at the man pages - you said you had problems with the earlier example.

***** also note that in the example essid is set to &#8220;My SSID&#8221; when yours is &#8220;my ssid&#8221;

---

### Post by kevdog on 2008-11-30
My head is hurting but at least you are providing something (learn however to read your dmesg file and post only the relevant parts).

You are using a broadcom based card I see.  That is enlightening.  That means you either using the b43, STA, or variant broadcom driver, or using ndiswrapper.

Please post the following:
lshw -C network

This will reveal the driver you are using for your card.
Also post the following:

sudo iwlist <interface> scan

Thanks.

---

### Post by chr75 on 2008-12-01
Ok, I installed ndiswrapper again, and tried first the suggestion by meastwood. I searched the web for the right syntax and ended up with the following.

	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 channel 6
	pre-up iwconfig wlan0 mode managed
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncryptType=TKIP
	pre-up iwpriv wlan0 set WPAPSK=myhexpsk
	pre-up iwconfig wlan0 essid "myssid"
	pre-up ifconfig wlan0 up

It still returns 

christian@Christian:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                               Invalid command : set
Failed to bring up wlan0.

@kevdog - lshw and iwlist wlan0 scan:
**christian@Christian:~$ sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:0b:5d:95:95:d4
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5751m-v3.40a ip=10.0.0.4 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 05
       serial: 00:15:00:02:20:25
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.52+Intel,12/19/2007,9.0.4.39 latency=32 link=no maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

**christian@Christian:~$ sudo iwlist wlan0 scan**
wlan0     Scan completed :
          Cell 01 - Address: 00:02:CF:91:6D:00
                    ESSID:"myssid"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-30 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

---

### Post by meastwood on 2008-12-02
oh well ..  i posted that before I read kevdog's post re. iwpriv. Just ran on my system and my card doesn't support any internal cmds either cmds.

# iwpriv wlan0
wlan0     no private ioctls.

sorry to say that there's little more help i can be (if i've been any !!), i think the issues lie at a lower level i.e. not user configuration.  Will keep an eye on this post as am interested in the solution - best of luck with it

---

### Post by chr75 on 2008-12-02
Ok, I will remove the iwpriv settings again - though we didn't get it to work I still appreciate your help - thanks!

---

### Post by meastwood on 2008-12-03
Just a final thought ... have you tried to connect manually?

kevdog's link/doc documents a way of doing this.

Another approach is as below.  This does not use either /etc/network/interfaces nor wpa_supplicant.conf. You configure the interface from scratch.  

Simply take the interface down and the back up - no more
$ sudo ifconfig wlan0 down
$ sudo ifconfig wlan0 up

Now run wpa_supplicant in the foreground without using a configuration file;  you can add -d for debug info if you want tho' the output generated without -d is enough to tell you whether or not you have managed to associate with the AP or not

Note: using -C<socket> and not -c<config file>
$ sudo wpa_supplicant -iwlan0 -C /var/run/wpa_supplicant -Dwext 

There should be no output.

Now open another terminal - 
$ sudo wpa_cli -i wlan0
.......
Interactive mode
> status
wpa_state=INACTIVE
~~~~~
to be expected, nothing has been configured
~~~~~
> list_networks
network id / ssid / bssid / flags
~~~~~
as expected
~~~~~
> ap_scan 0
OK
> scan
OK
> scan_results
~~~~~
nothing is found, may or may not be the case
~~~~~
>ap_scan 1
OK
> scan
OK
> scan_results
bssid / frequency / signal level / flags / ssid
00:0e:2e:fb:7b:63	2462	220	[WPA2-PSK-CCMP]	MINE-KEEP-OUT   
> list_networks
network id / ssid / bssid / flags 
~~~~~
still nothing, yet to configure
~~~~~
> status
wpa_state=INACTIVE
~~~~~
Lets just see what the interface can support (I've tidied up the output, no carriage return when a capability is returned)
~~~~~
> get_capability proto
RSN WPA
> get_capability key_mgmt
NONE IEEE8021X WPA-EAP WPA-PSK
> get_capability pairwise
CCMP TKIP
> get_capability group
CCMP TKIP WEP104 WEP40
~~~~~
Now to configure the network
~~~~~
> add_network
0
> list_networks
network id / ssid / bssid / flags
0		any	[DISABLED]
> set_network 0 ssid "MINE-KEEP-OUT"
OK
> set_network 0 key_mgmt WPA-PSK
OK
> set_network 0 psk cde9xxxxxxxxac77341baxxxxxxxxxxxxxxxx8ee6ea5d00xxxxxx34
OK
~~~~~
use your code generated by wpa_passphrase, in wpa_supplicant.conf
~~~~~
> set_network 0 proto WPA2
OK
~~~~~
WPA2 is an alias for RSN
~~~~~
> list_networks
network id / ssid / bssid / flags
0	MINE-KEEP-OUT	any	[DISABLED]
> enable_network 0
OK
> <2>Trying to associate with 00:0e:2e:fb:7b:63 (SSID='MINE-KEEP-OUT' freq=2462 MHz)
<2>Associated with 00:0e:2e:fb:7b:63
<2>WPA: Key negotiation completed with 00:0e:2e:fb:7b:63 [PTK=CCMP GTK=CCMP]
<2>CTRL-EVENT-CONNECTED - Connection to 00:0e:2e:fb:7b:63 completed (auth) [id=0 id_str=]

~~~~~
Successful association
~~~~~
> list_networks
network id / ssid / bssid / flags
0	MINE-KEEP-OUT	any	[CURRENT]
> status
bssid=00:0e:2e:fb:7b:63
ssid=MINE-KEEP-OUT
id=0
pairwise_cipher=CCMP
group_cipher=CCMP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
> quit

$ sudo dhclient wlan0
.................................
Sending on   LPF/wlan0/00:1f:1f:08:ce:28
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.11 from 192.168.0.1
DHCPREQUEST of 192.168.0.11 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.11 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.11 from 192.168.0.1
bound to 192.168.0.11 -- renewal in 361911611 seconds.

Back to terminal where you ran wpa_supplicant from :
$ CTRL Z
[1]+  Stopped                 wpa_supplicant -iwlan0 -C /var/run/wpa_supplicant -Dwext
To continue running but in the background
$ bg %1
[1]+ wpa_supplicant -iwlan0 -C /var/run/wpa_supplicant -Dwext &
To stop
$ jobs -l
[1]+  6934 Running                 sudo wpa_supplicant -iwlan0 -C/var/run/wpa_supplicant -Dwext &
$ sudo kill 6934
CTRL-EVENT-TERMINATING - signal 15 received
$
[1]+  Done                    wpa_supplicant -iwlan0 -C /var/run/wpa_supplicant -Dwext

---

### Post by chr75 on 2008-12-03
I have tried to connect by using the command line, but wasn't successfull - but I had the wicd still running and with that removed I'm ready to try again.

Following your suggestion gives me the following

christian@Christian:~$ sudo ifconfig wlan0 down
[sudo] password for christian: 
christian@Christian:~$ sudo ifconfig wlan0 up
christian@Christian:~$ sudo wpa_supplicant -iwlan0 -C /var/run/wpa_supplicant -Dwext 
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

due to the error above, the command that I should run in the other terminal gives me the following...

Interactive mode

> <2>Authentication with 00:00:00:00:00:00 timed out.
<2>Trying to associate with 00:02:cf:91:6d:00 (SSID='MySSID' freq=2437 MHz)
<2>Authentication with 00:00:00:00:00:00 timed out.
<2>Trying to associate with 00:02:cf:91:6d:00 (SSID='MySSID' freq=2437 MHz)
...and this continues so I had to break it with ctrl-c. I did not run the remaining commands, since I concluded that there was no point due to the errors.

---

### Post by meastwood on 2008-12-03
yeah .. only one instance of wpa_supplicant can use the socket.  Something must have been left over from previous attempts.  If you have auto wlan0 in /etc/network/interfaces then it will run on boot.

Before doing any of the commands in previous post please first check that wpa_supplicant is not running
# ps -ef | grep [Ww]pa
# sudo kill <process id> of wpa_supplicant if running

Also check that socket does not remain, if it does then delete it
# sudo rm -R /var/run/wpa_supplicant

if /var/run/wpa_supplicant.wlan0.pid exists
then delete also.
# sudo /var/run/wpa_supplicant.wlan0.pid

then follow the cmds in prev. post from the beginning

---

### Post by chr75 on 2008-12-04
Following your guidelines in the last post, I was now able to run the commands in your previous post.

Here is the output...

**christian@Christian:~$ sudo wpa_cli -i wlan0**
[sudo] password for christian: 
wpa_cli v0.5.8

<a bunch of info that I removed>

Interactive mode

> status
wpa_state=INACTIVE
> list_networks
network id / ssid / bssid / flags
> ap_scan 0
OK
> scan
OK
> scan_results
bssid / frequency / signal level / flags / ssid
00:02:cf:91:6d:00	2437	221	[WPA2-PSK-CCMP]	MySSID
> ap_scan 1
OK
> scan
OK
> scan_results
bssid / frequency / signal level / flags / ssid
00:02:cf:91:6d:00	2437	221	[WPA2-PSK-CCMP]	MySSID
> list_networks
network id / ssid / bssid / flags
> status
wpa_state=INACTIVE
> get_capability proto
RSN WPA> get_capability key_mgmt
NONE IEEE8021X WPA-EAP WPA-PSK> 
CCMP TKIP> get_capability group
CCMP TKIP WEP104 WEP40> add_network
0
> list_networks
network id / ssid / bssid / flags
0		any	[DISABLED]
> set_network 0 ssid "SiemensWireless"
OK
> set_network 0 key_mgmt WPA-PSK
OK
> set_network 0 psk 8405xxxxxxxxf11a46xxxxxxxxxea913e6e463axxxxxxxxx53fb25f
OK
> set_network 0 proto wpa2
**FAIL** 

In the other terminal I can see the following messages:
ioctl[SIOCGIFADDR]: Cannot assign requested address
ioctl[SIOCGIFADDR]: Cannot assign requested address
Line 0: invalid proto 'wpa2'
Line 0: no proto values configured.

I stopped here, since it didn't make any sence to continue when I received those kind of errors. Have you any idea to what the origin of the error is?

---

### Post by meastwood on 2008-12-04
It didn't like the wpa2 as a protocol - you've used lower-case, should be WPA2 (ain't unix/linux great?)

You do not need to stop anything/quit wpa_cli if you get something like 
> set_network 0 proto wpa2
FAIL 
it is just saying that that particular command failed so you could have continued with
> set_network 0 proto WPA2

If it doesn't like WPA2 either, use RSN (upper-case :))

** have you meant to set ssid to "SiemensWireless"?
** should be "MySSID" surely  - its the only ssid that has been found!

Its good to see that the configuration is occurring. Also what is good is that setting ap_scan to 0 i.e. get the interface driver to scan, returned a result.

Do not worry about "ioctl[SIOCGIFADDR]: Cannot assign requested address", I get that on mine but it does not stop it from working.
The other two lines are the result of trying to set an invalid proto.  Again there is no need to quit, just retype the cmd with a valid proto value. The cmd > get_capability proto listed valid protos (WPA2 being an alias for RSN)

Remember to make sure processes have stopped etc. before trying again.

Also bear in mind that wpa_cli is also a monitor - periodically you may get messages appearing on the screen, hitting spacebar or return will get you back to the '>' prompt. Sometimes a message will appear as you are typing a command (a pain) in which case just continue typing the command as tho' nothing happened (sometimes tricky as can be confusing) or just hit return, an error will be returned but again it just relates to the cmd you have just typed.

---

### Post by chr75 on 2008-12-05
Ok, i will try again then. I'm writing this from a windows machine because the ubuntu keeps crashing and I think it happens only when I'm online. Will keep you posted on the result :)

Now, I've tried again and when I get to the point where I run enable_network 0, I get the following:

>enable_network 0
OK
> <2>Trying to associate with 00:02:xx:xx:xx:00 (SSID='MySSID' freq=2437 MHz)
<2>Authentication with 00:00:00:00:00:00 timed out
> <2>Trying to associate with 00:02:xx:xx:xx:00 (SSID='MySSID' freq=2437 MHz)
<2>Authentication with 00:00:00:00:00:00 timed out
and so on and so forth...
is it trying to associate with a blank key?

All the previous commands had the exact same output as in your post.

---

### Post by chr75 on 2008-12-05
I've found this post, where the kernel version seemed to the problem. I'm running 2.6.24-22-generic which is the version above the version that was the problem in this post, but maybe the same solution could be applied?

[http://ph.ubuntuforums.com/showthread.php?t=963368](http://ph.ubuntuforums.com/showthread.php?t=963368)

"I have deinstalled linux-backports-modules-* packages and it works now. New backport package contained modules lbm_cw_ieee80211 and lbm_cw_ieee80211_crypt which were loaded automatically instead of proper ieee80211 and ieee80211_crypt."

I haven't got the faintest idea about how to do that, and I dont know if its even worth a try?

---

### Post by meastwood on 2008-12-05
Do you have back-ports enabled? - it is not by default

Check if you have the back-ported modules installed
$ modinfo <module>
e.g. $ modinfo lbm_cw_ieee80211  

From the output 
Trying to associate with 00:02xxx:00 (SSID='MySSID' freq=2437 MHz)
<2>Authentication with 00:00:00:00:00:00
the MAC address being used for authentication is 00:00:00:00:00:00
it should be the same as that which it is trying to associate with - this is what is going wrong at this stage. It's down to authentication.

How to fix it I do not know - I'll look into it.  If anyone knows their input would be welcome.

Have looked into it - no wiser.
 
To my mind this is a bug - there are a few similar ones logged already - whether it's the driver, network manager ,ndiswrapper I have no idea. All I can suggest is double check ndiswrapper implementation. Give launchpad a visit.

If it were my machine I'd build from source, failing that, I'd get a cheap supported usb wireless adapter (e.g. Edimax), but not so cheap that it didn't support WPA2!! 

Still - I've learnt a thing or two about wireless and wpa_supplicant ....

---

### Post by kevdog on 2008-12-05
Your ndiswrapper driver may not support wpa2?  Have you verified this?  What card are you working with and is there possibly a built-in driver you can use other than ndiswrapper?

---

### Post by chr75 on 2008-12-07
@Meastwood - It seems that I have the backport modules installed, and that its the ones that was used to resolve the problem in the post I refered to.

christian@Christian:~$ modinfo lbm_cw_ieee80211 
filename:       /lib/modules/2.6.24-22-generic/updates/lbm_cw-ieee80211.ko
description:    802.11 data/management/control stack
version:        git-1.1.13
srcversion:     5AB09C073C0ED10418D6EF7
depends:        lbm_cw-ieee80211_crypt
vermagic:       2.6.24-22-generic SMP mod_unload 586 

@kevdog - 
I have not verified that my ndiswrapper driver can actually run WPA2 - I have searched sourceforge and launchpad for info, also for the native driver, but couldn't find the info. The driver is w29n51.

This is my card:
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

For the native driver the readme says that WPA is enabled but not supported. I have already tried the IPW2200 driver without success.

---

### Post by kevdog on 2008-12-07
Im not sure but that is a very old chipset.  I don't know for sure but I would put bets that wpa2 doesn't work with your firmware.  Correction -- it should support wpa2 -- I looked.  Have you tried using the native drivers?  Do you get any errors when trying wpa2 or wpa?

---

### Post by chr75 on 2008-12-08
**@ kevdog**:
Yes, I have used the native driver - IPW2200 - but I got the very same error as when I use ndiswrapper - can't associate with access point.

Also, I cant use IPW2200 with wpa_supplicant, but I didn't realize that before you made me aware of that :)

**Bonus info**
In the readme part of the IPW2200 driver there is a FAQ, with the following question: Why am I unable to associate when WEP is enabled?
Though my problem is WPA2, it still resembles my problem.
The answer in the FAQ is:
"The most common reason for this is that the security mode is set to restricted instead of open, since restricted mode means that the driver will only associate with APs that it can first do shared key authentication with. If the AP is not configured to require shared key authentication, association won't happen.
Ensure that you are associating using the steps:

% modprobe ipw2100
% iwconfig eth1 essid <essid>
% iwconfig eth1 key open <key>
% ifconfig eth1 up

I cant see anything in my router regarding restricted vs open under security mode - I can choose 'No security', and then the various WEP, WPA2, WPA2-PSK etc. WPA2-PSK is selected.

Following the suggestions from the readme file I get the following error:

christian@Christian:~$ sudo iwconfig eth1 key open 8405e7xxxxx8ef99xxxxx46890xxxxxe84eaxxxxxe463axxxxxd0d1dxxxxx25f
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; Operation not supported.

---

### Post by kevdog on 2008-12-08
> Also, I cant use IPW2200 with wpa_supplicant, but I didn't realize that before you made me aware of that 

I don't understand this statement?  Why can't you?  Use wext as your driver type?

---

### Post by chr75 on 2008-12-09
Sorry, its just me not fully understanding the connection between IPW2200 and wext - I have used wext, but with the same error message (can't associate).

Been searching and reading regarding the error that is probably the reason why it cant associate:
"Error for wireless request "Set Encode" (8B2A) :
SET failed on device eth1 ; Operation not supported."

Other users have had this problem as well, but I have so far only found posts related to other Linux systems. They suggest something about building/compiling a new kernel 

Mandrake
[http://osdir.com/ml/linux.drivers.ipw2100.devel/2004-09/msg00614.html](http://osdir.com/ml/linux.drivers.ipw2100.devel/2004-09/msg00614.html)

Linuxstorm
[http://lists.berlios.de/pipermail/bcm43xx-dev/2006-September/002661.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2006-September/002661.html)

Ubuntu: Could also be related to the pre-shared key somehow?
[http://ubuntuforums.org/archive/index.php/t-780273.html](http://ubuntuforums.org/archive/index.php/t-780273.html)

---

### Post by meastwood on 2008-12-11
re. backported modules. Can safely remove using synaptic package manager.
The modules are installed in an updates dir in /lib/modules/`uname -r`/
 
Do a search on linux-backports-modules-2.6.24-22-generic.
Select the package and choose complete removal.

The original issue - from post #7
......
ipw2x00 driver uses driver_wext (-Dwext) instead of driver_ipw.
Own MAC address: my_mac_address
wpa_driver_ipw_set_wpa: enabled=1
**ioctl[IPW_IOCTL_WPA_SUPPLICANT]**: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
**Failed to set encryption.**
.......
Some posts say they fixed this by using ipw driver however these are dated and do not apply to hardy. You've tried this and got the result.

Seems to me that the problem is either with the driver/firmware or encryption. 

When trying to associate, use another terminal and just check which encryption modules are being loaded.(lsmod)

You can ensure that the encryption modules are loaded before trying to run i.e.
/lib/modules/2.6.24-22-generic$ sudo find . -name ieee8*
./kernel/net/ieee80211
./kernel/net/ieee80211/softmac/ieee80211softmac.ko
./kernel/net/ieee80211/ieee80211.ko
....
[I]./ubuntu/wireless/rtl8187-usb/ieee80211
./ubuntu/wireless/rtl8187-usb/ieee80211/ieee80211_crypt_tkip-rtl.ko
......[I]

#sudo modprobe ieee80211_crypt_tkip  ieee80211_crypt_ccmp ... ...

NB: on my system the only modules that lsmod list are
aes_generic            27712  0 
aes_i586               33536  2 
blkcipher               8324  2 geode_aes,ecb
geode_aes               7176  0 
these are loaded when I plug the usb wireless in - so what I've said above may well be 'hogwash'!! tho' just offering a response to the links you posted. I renamed all my ieee80211* modules and everything still worked - I guess it is down to the implementation of the driver being used.

AES and MD5 encryption are/should be configured in the generic kernel.

Another suggestion found in an old post is to stop network manager before trying
# sudo pkill nm-applet

I wouldn't mind having another look at the 
# wpa_supplicant -K -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -dd
output - it will make a little bit more sense to me now than it did a couple of weeks back! which may not mean much i.e. see if it gets to the WPA 4-way handshake stage.

---

### Post by chr75 on 2008-12-14
Checking which modules have been loaded...

christian@Christian:~$ sudo find . -name ieee*
[sudo] password for christian: 
./Drivers/ieee80211-1.2.18
./Drivers/ieee80211-1.2.18/ieee80211_module.c
./Drivers/ieee80211-1.2.18/ieee80211_rx.c
./Drivers/ieee80211-1.2.18/ieee80211_crypt_tkip.c
./Drivers/ieee80211-1.2.18/net/ieee80211.h
./Drivers/ieee80211-1.2.18/net/ieee80211_crypt.h
./Drivers/ieee80211-1.2.18/net/ieee80211_radiotap.h
./Drivers/ieee80211-1.2.18/ieee80211_tx.c
./Drivers/ieee80211-1.2.18/ieee80211_crypt_wep.c
./Drivers/ieee80211-1.2.18/ieee80211_crypt.c
./Drivers/ieee80211-1.2.18/ieee80211_crypt_ccmp.c
./Drivers/ieee80211-1.2.18/ieee80211_geo.c
./Drivers/ieee80211-1.2.18/ieee80211_wx.c
find: ./.gvfs: Permission denied

**christian@Christian:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd**
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=15):
     53 69 65 6d 65 6e 73 57 69 72 65 6c 65 73 73      MySSID 
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
key_mgmt: 0x2
proto: 0x3
pairwise: 0x18
group: 0x18
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='MySSID'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:15:00:02:20:25
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 287 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:02:cf:91:6d:00 **ssid=''** wpa_ie_len=24 rsn_ie_len=22 caps=0x11
   skip - SSID mismatch
Try to find non-WPA AP
0: 00:02:cf:91:6d:00 ssid='' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 287 bytes of scan results (1 BSSes)


and then it just continues in circles till I interrupt.

---

### Post by meastwood on 2008-12-15
I wouldn't worry about the modules for now ...
........
Try to find WPA-enabled AP
0: 00:02:cf:91:6d:00 ssid='' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
skip - SSID mismatch
Try to find non-WPA AP
0: 00:02:cf:91:6d:00 ssid='' wpa_ie_len=24 rsn_ie_len=22 caps=0x11
skip - SSID mismatch
No suitable AP found.
-------------------
this is saying that the SSID on your wireless router is not set.

I have finally managed to duplicate your error -
.......
Trying to associate with 00:0e:xx:xx:xx:63 (SSID='MINE-KEEP-OUT' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
.......

Double check your router settings - from 1st. error your router ESSID is no longer set
ALSO ENSURE: 
router mode is set to AP
it's ESSID is set
Broadcast ESSID is enabled
Authentication type is set to Shared key or Auto
Encryption is set to WPA2 pre-shared key
WPA unicast cipher suite is set to WPA2(aes)
Pre-shared key format is set to 'passphrase'
~~~~~~~~~~~~~~~~~~~~~~~~~
Check also if you have MAC address filtering enabled (wireless access control) - if so make sure it will allow your card to connect.
I duplicated your error by 
(a) MAC filtering enabled
(b) removing the MAC address of my card from the MAC filtering table
If you have MAC filtering enabled you must also provide the MAC address of your card in the 'allowed' MAC filtering table
~~~~~~~~~~~~~~~~~~~~~~~~~~

This MIGHT be your problem ....

---

### Post by chr75 on 2008-12-16
I dont think that my problem is that the essid is not set, because I use a laptop from my work (windows based) to connect to the same router, and for that laptop I also connect with WPA2, with a hidden SSID and with the same preshared key.

I see that you state that the SSID should be broadcast, and I had that disabled for security reasons, but will enable now just to rule out another factor.

Router mode - I cant find such a setting, but the system mode is set to routing (as opposed to bridging)

I will post the most relevant information from my router below...

Host Name:	
 	Model Number: 	P-2602HW-D1A
 	MAC Address:	00:02:cf:91:6d:00
 	WLAN Information	 
 	    - SSID:	Myssid
 	    - Channel:	6
 	    - WEP:	Disable
 	Security	 
 	   - Content Filter:	Disable

Under the tab 'Wireless lan' I have the following setup
	 **Wireless Setup**
 
Active Wireless LAN  - ticked
Network Name(SSID) - 'Myssid	
Hide SSID - was ticked, but I have now removed the tick
Channel Selection	- channel 6 - 2437 mhz
 
  	**Security**
 
Security Mode	WPA2-PSK
WPA Compatible - not ticked (have ticked this previously without any effect)
Pre-Shared Key	- mypresharedkey

Under the tab 'MAC filter' I have inserted the MAC-adresses of both laptops (Ubuntu and the windows), but I have not ticked the "Active MAC filter', because I wanted the WPA2 to work first. Anyway, the filter action is already set to 'allow' rather than 'Deny', so even if the filtering was activated it shouldn't make a difference.

I will try to connect again with ssid broadcasted and report back if that makes a difference...

Ok, back with the result - different from before but still in error.

Took the interface down - #**sudo ifconfig wlan0 down** - OK
Got DHCP offer - #**sudo dhclient -r wlan0** - OK

Listening on LPF/wlan0/00:15:00:02:20:25
Sending on   LPF/wlan0/00:15:00:02:20:25
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.0.0.1 port 67

**sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd**
The following is an extract:
Try to find WPA-enabled AP
0: 00:02:cf:91:6d:00 ssid='Myssid' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:02:cf:91:6d:00 ssid='Myssid'
Try to find non-WPA AP
Trying to associate with 00:02:cf:91:6d:00 (SSID='Myssid' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
**No keys have been configured - skip key clearing**

...but the key has been configured in wpa_supplicant.conf.
I did it like in Kevdogs link, where I put the code in ASCI
psk='MYCODE'
...this is my wpa_supplicant.conf:

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="Myssid"
        psk="MYCODE"
        key_mgmt=WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
        group=CCMP TKIP
}

---

### Post by meastwood on 2008-12-16
the router ssid can be hidden but at this stage of play it makes sense to broadcast it.

Unfortunately could do with more output - I believe (I get it on mine as well) that at this stage wpa is checking to see if it has any keys set in its cache - since none are set it skips clearing them.) - this is not a problem.

am looking for something like
.....
Wireless event: cmd=0x8c02 len=173
WEXT: Custom wireless event: 'ASSOCINFO(ReqIEs=00 .....
which occurs later on plus a bit more of the output

By the way, I take it that you do not have OTIST enabled on your router (for your windows client) also what do your router logs report?

---

### Post by meastwood on 2008-12-17
I doubt if the full output (up to where the interface fails to associate) will show what I'm looking for as the fault - to my mind occurs before this stage however no harm in looking.

To-day I started getting exactly the same error - repeatedly failing to associate with 00:00:00:00:00:00 .....

On further investigation I discovered that my router had failed to clear its 'connection table'. The router connection table (device status) claimed that it had one associated client (I have mac filtering enabled and only one client i.e. my usb wireless interface, is allowed). However, my usb interface was not connected and was unable to associate. Resetting the router corrected the problem.

The point here is:
I have twice now duplicated the association error and on both occasions the fix lay with the router.

Further more - encryption to my mind is (at this stage) no longer an issue. In order for any communication to take place the wireless interface must first associate with the AP. Once associated the WPA2 4-way handshake can then take place. 

This is demonstrated by the output below where I used an incorrect passphrase:
# wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf 
Trying to associate with 00:0e:2e:fb:7b:63 (SSID='MINE-KEEP-OUT' freq=2462 MHz)
[B][I]Associated with 00:0e:2e:fb:7b:63
WPA: 4-Way Handshake failed - pre-shared key may be incorrect[/I][/B]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0e:2e:fb:7b:63
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:0e:2e:fb:7b:63
.....

-----------------------------------
To make sure that the router is responding okay can you post the output of
# wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -dd -K

*** please remember the ***-dd -K*** (uppercase K) and also post the whole output up to where it reports 'Associated with 00:00:00:00:00:00 timed out'

This will indicate whether the Router is accepting or dropping EAPOL frames and or if there is a problem with EAPOL
In brief:
NIC driver scans
EAPOL frames are exchanged between client and AP for association
WPA2 is then used for authentication

---

### Post by chr75 on 2008-12-18
I hope you're right, that the error lays with the router.

Regarding OTIST i dont know what it is, but yes, it is enabled in my router settings. Under the tab OTIST there is only two fields - a setup key, which is filled, and a check-box that is ticked, with the following text: "Yes! Please enhance the wireless security level to WPA-PSK automatically if no WLAN security has been set.This will generate a random PSK key for your convenience."

The log is completely empty - I checked the settings, and the router will log the following: "any IP", "SIP", "RTP" and "FSM".

In the following, I will post the full (long) results of the commands.

christian@Christian:~$ sudo ifconfig wlan0 down
[sudo] password for christian: 
christian@Christian:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:00:02:20:25
Sending on   LPF/wlan0/00:15:00:02:20:25
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.0.0.1 port 67
[B]christian@Christian:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd -K
[/B]Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=15):
     53 69 65 6d 65 6e 73 57 69 72 65 6c 65 73 73      Myssid 
PSK (ASCII passphrase) - hexdump_ascii(len=8):
     **59 49 4d 48 50 41 58 4d**                           Mycode        
key_mgmt: 0x2
proto: 0x3
pairwise: 0x18
group: 0x18
PSK (from passphrase) - hexdump(len=32): **84 05 e7 73 f7 28 ef 99 ff 11 a4 68 90 86 1c de 84 ea 91 3e 6e 46 3a ed 34 7d 0d 1d 85 3f b2 5f**
Priority group 0
   id=0 ssid='Myssid'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:xx:00:xx:xx:25
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 270 bytes of scan results (1 BSSes)
Scan results: 1
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:02:cf:91:6d:00 ssid='Myssid' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
   selected based on RSN IE
   selected WPA AP 00:02:cf:91:6d:00 ssid='Myssid'
Try to find non-WPA AP
Trying to associate with 00:02:cf:91:6d:00 (SSID='Myssid' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
RSN: using IEEE 802.11i/D9.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
WPA: clearing AP WPA IE
WPA: set AP RSN IE - hexdump(len=22): **30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00**
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): **30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00**
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=23
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:02:cf:91:6d:00 into blacklist
No keys have been configured - skip key clearing

Hope it makes sence :-)

---

### Post by meastwood on 2008-12-18
yup - could be getting somewhere ....

First:
OTIST stands for One-Touch Intelligent Security Technology (OTIST). It is propriety to your router.
"With ZyXEL&#8217;s OTIST, you set up the SSID and WPA-PSK on the ZyXEL Device. Then, the
 ZyXEL Device ***transfers them to the devices in the wireless networks***. As a result, you do not have to set up the SSID and encryption on every device in the wireless network. The ***devices in the wireless network have to support OTIST"***

Under linux I am almost certain that this will not be supported - primarily because the support comes in the form of 3rd. party software which runs (in addition to everything else) on the client.  It is this 3rd.party software (which will not be installed on your linux client) that is responsible for configuring the client wireless interface. There maybe code out there for it - who knows, how it would interface with existing linux/ubuntu framework is another matter.

The debug info also confirms that the router IS dropping the EAPOL_start frame which is why the client cannot associate:

A working EAPOL example:
.........
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
[B][I]Wireless event: cmd=0x8b1a len=21
RX EAPOL from 00:0e:2e:fb:7b:63[/I][/B]
RX EAPOL - hexdump(len=121): 01 03
....

Your example:
........
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
***Wireless event: cmd=0x8b1a len=23***
Authentication with 00:00:00:00:00:00 timed out.

Either ALL clients must support OTIST or do not use. It's a windows thing in any case!! 

To get your linux box to work switch it off ... (touch wood)
To get both linux and windows switch it off and 'manually' configure the SSID and WPA-PSK on your windows client

---

### Post by chr75 on 2008-12-19
Sorry Meastwood, it seems that the router is not actually using OTIST, but just is prepared to do so (on the users manual request).

It's true that there is a setup key and a box which is ticked, but the only button I can press is "Start". If I remove the setup key and the tick, I can still only press start - the "Apply" button is not available as is the case in the other tabs. I have attached a screenshot.

From that, I guess that the distribution of the SSID and the code happens only when the user press start - which explains why I had to configure my windows laptop manually to connect to the router.

Sorry for the misleading info...

---

### Post by meastwood on 2008-12-19
Well - the EAOPL_start frame is being dropped or it is not being received - the router has not participated in any EAPOL exchange. The last log is quite clear about it.

The router manual says: re. OTIST [yes] checkbox
"Select this if you want the ZyXEL Device to automatically generate a pre-
shared key for the wireless network. Before you do this, click Network >
Wireless LAN > General and set the Security Mode to No Security.

Clear this if you want the ZyXEL Device to use a pre-shared key that you
enter. Before you do this, click Network > Wireless LAN > General, set the
Security Mode to WPA-PSK, and enter the Pre-Shared Key."

So it should be cleared - click on another tab to get your apply button

The manual is unclear what effect setting Security Mode to WPA-PSK and having the [yes] checkbox checked. Which from what I can gather is how it is set up.

OTIST clearly has to run before WPA 4-way handshake as it provides the key - whether it does this after association or in place off (in which case doesl it use EAPOL frames) I do not know.
 
If no joy unchecking OTIST  -
It might be worth having Security Mode set to No Security and OTIST checkbox unchecked.  Open the router up completely and see if any EAPOL frames are received by the client.  

Check that all possible logging is activated. 

Open the router up completely and see if any EAPOL frames are received by the client.

---

### Post by meastwood on 2008-12-20
Actually - there is still a possibility that it is not the router. Though would still switch OTIST off. Need to run wpa_supplicant with verbosity running at max.
Also want to see if it is the router that is not sending EAPOL frames or it is the laptop that is not responding to them.

Once you've done the usual cleaning up before running wpa_supplicant again -
# sudo ifconfig wlan0 up

Open another terminal and type
# sudo tcpdump -i wlan0 -e -tt

then back to the first terminal and run
# sudo wpa_supplicant -iwlan0 -Dwext -c/etc/wpa_supplicant.conf -dddd -t
(yup 4 d's and a 't')

Again posting all the output up to 
Authentication with 00:00:00:00:00:00 timed out.

Also please post the ouput from tcpdump - maybe none

---

### Post by chr75 on 2008-12-21
Tried shutting OTIST down, but switching to another tab means that settings are reset - doesn't matter what I do. Tried without security before deleting the settings, but as soon as I go to another tab, the settings are set again. I suppose it means that OTIST will not be used before I press the start button.

Output from wpa_supplicant
christian@Christian:~$ sudo ifconfig wlan0 down
christian@Christian:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:00:02:20:25
Sending on   LPF/wlan0/00:15:00:02:20:25
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 10.0.0.1 port 67
christian@Christian:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dddd -t
1229843384.406784: Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
1229843384.406843: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
1229843384.406851: Reading configuration file '/etc/wpa_supplicant.conf'
1229843384.428987: ctrl_interface='/var/run/wpa_supplicant'
1229843384.429011: Line: 3 - start of a new network block
1229843384.429026: ssid - hexdump_ascii(len=15):
     53 69 65 6d 65 6e 73 57 69 72 65 6c 65 73 73      Myssid 
1229843384.429045: PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
1229843384.429056: key_mgmt: 0x2
1229843384.429062: proto: 0x3
1229843384.429067: pairwise: 0x18
1229843384.429073: group: 0x18
1229843384.447205: PSK (from passphrase) - hexdump(len=32): [REMOVED]
1229843384.447275: Priority group 0
1229843384.447305:    id=0 ssid='Myssid'
1229843384.447335: Initializing interface (2) 'wlan0'
1229843384.465471: EAPOL: SUPP_PAE entering state DISCONNECTED
1229843384.465507: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
1229843384.465512: EAPOL: SUPP_BE entering state INITIALIZE
1229843384.465521: EAP: EAP entering state DISABLED
1229843384.465530: EAPOL: External notification - portEnabled=0
1229843384.465535: EAPOL: External notification - portValid=0
1229843384.465691: SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
1229843384.465700:   capabilities: key_mgmt 0xf enc 0xf
1229843384.681239: WEXT: Operstate: linkmode=1, operstate=5
1229843384.692809: Own MAC address: 00:15:00:02:20:25
1229843384.692825: wpa_driver_wext_set_wpa
1229843384.694554: wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
1229843384.694567: wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
1229843384.694574: wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
1229843384.694581: wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
1229843384.694588: wpa_driver_wext_set_countermeasures
1229843384.694594: wpa_driver_wext_set_drop_unencrypted
1229843384.694611: Setting scan request: 0 sec 100000 usec
1229843384.694675: Added interface wlan0
1229843384.694709: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.694716: Wireless event: cmd=0x8b06 len=8
1229843384.795676: State: DISCONNECTED -> SCANNING
1229843384.795700: Starting AP scan (broadcast SSID)
1229843384.795706: Trying to get current scan results first without requesting a new scan to speed up initial association
1229843384.795802: Received 270 bytes of scan results (1 BSSes)
1229843384.795809: Scan results: 1
1229843384.795815: Selecting BSS from priority group 0
1229843384.795820: Try to find WPA-enabled AP
1229843384.795824: 0: 00:xx:cf:xx:xx:00 ssid='Myssid' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
1229843384.795835:    selected based on RSN IE
1229843384.795840:    selected WPA AP 00:xx:cf:xx:xx:00 ssid='Myssid'
1229843384.795845: Try to find non-WPA AP
1229843384.795856: Trying to associate with 00:xx:cf:xx:xx:00 (SSID='Myssid' freq=2437 MHz)
1229843384.795863: Cancelling scan request
1229843384.795868: WPA: clearing own WPA/RSN IE
1229843384.795872: Automatic auth_alg selection: 0x1
1229843384.795883: RSN: using IEEE 802.11i/D9.0
1229843384.795888: WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 2
1229843384.795894: WPA: clearing AP WPA IE
1229843384.795899: WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1229843384.795911: WPA: using GTK CCMP
1229843384.795916: WPA: using PTK CCMP
1229843384.795921: WPA: using KEY_MGMT WPA-PSK
1229843384.795926: WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
1229843384.795939: No keys have been configured - skip key clearing
1229843384.795944: wpa_driver_wext_set_drop_unencrypted
1229843384.795949: State: SCANNING -> ASSOCIATING
1229843384.795954: wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
1229843384.795960: WEXT: Operstate: linkmode=-1, operstate=5
1229843384.795981: wpa_driver_wext_associate
1229843384.796041: Setting authentication timeout: 10 sec 0 usec
1229843384.796049: EAPOL: External notification - EAP success=0
1229843384.796058: EAPOL: External notification - EAP fail=0
1229843384.796063: EAPOL: External notification - portControl=Auto
1229843384.796071: RSN: Ignored PMKID candidate without preauth flag
1229843384.796130: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796137: Wireless event: cmd=0x8b06 len=8
1229843384.796143: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796149: Wireless event: cmd=0x8b04 len=12
1229843384.796154: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796159: Wireless event: cmd=0x8b1a len=23
1229843394.799610: Authentication with 00:00:00:00:00:00 timed out.

Output from the tcpdump
christian@Christian:~$ sudo tcpdump -i wlan0 -e -tt
[sudo] password for christian: 
tcpdump: WARNING: wlan0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 96 bytes
tcpdump: pcap_loop: recvfrom: Network is down
0 packets captured
0 packets received by filter
0 packets dropped by kernel
christian@Christian:~$

---

### Post by meastwood on 2008-12-21
The problem (as I see it) is :
The NIC cannot associate because it is unable to get the AP's mac address.
Without the AP's mac address no association can take place, without association, no EAPOL or WPA2 communication.

From your debug info:
....................
1229843384.795815: Selecting BSS from priority group 0
1229843384.795820: Try to find WPA-enabled AP
1229843384.795824: 0: 00:xx:cf:xx:xx:00 ssid='Myssid' wpa_ie_len=0 rsn_ie_len=22 caps=0x11
1229843384.795835: selected based on RSN IE
1229843384.795840: selected WPA AP 00:xx:cf:xx:xx:00 ssid='Myssid'

The driver has scanned and found the AP - it also knows the AP's mac address and ssid

......................
3 calls are then made to the linux wireless API to: 
......................
1229843384.796130: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796137: Wireless event: cmd=0x8b06 len=8				### set the operation mode
1229843384.796143: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796149: Wireless event: cmd=0x8b04 len=12			### set the channel frequency
1229843384.796154: RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
1229843384.796159: Wireless event: cmd=0x8b1a len=23			### set the ESSID
1229843394.799610: Authentication with 00:00:00:00:00:00 timed out.

And this is as far as you are getting.....................

++++++++++++++++++++++++++++++++++
What should happen after setting the ESSID is 
....................
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=21								### set ESSID
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c02 len=173								### set driver specific ascii string
WEXT: Custom wireless event: 'ASSOCINFO(ReqIE8vvvvvvvvvvvvvvvvvvvvvvvvv140100000fac040100000fac040100000fac020000 Res
pIEs=0108vvv40b16vvvvvvvvvvv048606c)'
Association info event
..................
cmd=0x8c02 	Driver specific ascii string
Wireless event: cmd=0x8b15 len=20     								### get AP mac address
Wireless event: new AP: 00:00:yy:fc:7b:63
State: ASSOCIATING -> ASSOCIATED
..................
+++++++++++++++++++++++++++++++++++

Maybe there is a problem with setting the ESSID. The same debug info. is generated when a client is blocked from an AP.

At this stage my money is still on the router (mind it would not be the first time I've lost)
You should be able to switch OTIST off.  The manual says you can. The transfers are initiated by the start button however it may be that while OTIST is enabled, the AP will only accept frames from OTIST supported clients - its an unknown.  And while it is it cannot be ruled out.

If you are happy with it,  you can (after making note of the configuration and are happy in the fact that you can reconfigure it) reset the router to factory defaults and reconfigure it - checking on OTIST settings

Are you able to try accessing other networks, like at work, with your linux client? - ideally with an AP that does not have OTIST

---

### Post by chr75 on 2008-12-22
I'm gonna try and dig up an old router and set it up to see if there is any difference, but I might not be able to do that before Christmas.

I have set the current router back to factory settings, but it comes with the same OTIST setting :confused:

I'm still thinking that if OTIST was the problem, and that IF the router would only accept frames from OTIST supported clients, then my windows laptop would be able to connect. I have changed the ssid and password, and then the windows laptop could not connect before I manually configured the network. Anyway, I dont want to be hard-headed, and will try another router ASAP :)

---

### Post by meastwood on 2009-01-06
I thought you said that the windows client had no problem connecting using wpa2 and that it used OTIST.

If OTIST is enabled on the router and you then change the SSID and passphrase you need to run/start OTIST on both the client and router within a 3 minute window so that the SSID and passphrase are transferred to the client - if not you would need to configure the client manually.

As I said I'm not 100% sure how OTIST works. The problem is - if you configured the windows client manually and it connects (and it still has the OTIST client software running on it), OTIST can not be ruled out. 

We are back to - if OTIST is enabled on the router then clients must also be OTIST 'aware' (the manual) and the linux client is not. 
If all OTIST does is transfer the SSID and passphrase to the client - which can be achieved through manual configuration, then there is no real need (apart from a security feature maybe) to have OTIST aware clients.  Yet the manual is quite specific about using OTIST and having OTIST aware/enabled clients.  This being the case - OTIST is doing a bit more

OTIST appears to be specific to WPA/2, if as I understood, you had both linux and windows connecting using WEP and only windows (with its OTIST client software) able to connect using WPA2 then it kind of ties in.

What's needed is link-layer trace however I do not have the right setup here, chipsets can also be an issue. Ideally you would install aircrack-ng on your windows client and run airmon-ng and airdump-ng to try and capture frames from your linux client as it tries to associate with the AP.   To do this you do need some know-how on datacomms.

I'm not saying it is definitely the router/OTIST but nor can I rule it out. I cannot see it being the driver for a number of reasons not least - no errors are being reported. It seems to be behaving as designed albeit the mechanism it uses to get the SSID is not succeeding. Tho' not 100% sure, this is likely to be via link-layer request frame(s).  

From the manual -
pressing router RESET for 3-8 seconds enables OTIST.  Do not know if it toggles.
pressing router RESET for >9 secs. will restore factory defaults

So, we still need to establish if OTIST is being used.  If it is not then it's down to the wireless network environment or driver/software.
If resetting the router to factory defaults does not switch it of then ... 

Assume OTIST is enabled on the router.
1. Change the ssid and passphrase on the router again.  Use OTIST start and run OTIST on your windows client within the 3 minute window.  Does it connect?
2. Change the ssid and passphrase on the router.  Do not use OTIST on router or windows client, configure manually. Does it connect?

---

### Post by chr75 on 2009-01-07
I may have been unclear in my response regarding the windows laptop, but I always connect **_without_** using OTIST on the windows laptop - I actually dont know how to activate it even on windows. 

I have tried the option where I change the SSID and the password, and then I do manual config (again without OTIST), and it connects straight away (still the windows laptop). Thats why I think OTIST is not activated on the router.

---

### Post by Favux on 2009-01-07
Hi chr75,

I admit to not having read the whole thread.  If you are still having trouble connecting via WPA2 with Intrepid (NM 0.7) you might want to check out:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I hope this work-a-round is helpful and I'm not stepping on this thread.

---

### Post by meastwood on 2009-01-08
If you're happy that OTIST isn't being used then I guess that rules the router out (pity :-( ).

I have an idea that may or may not shed more light on the problem though have to check it out first. It will generate a lot of output and I need to see if I'm able to understand enough of it and if so, whether or not it would be any use.

---

### Post by meastwood on 2009-01-12
You may not like or agree with this but as I pointed out some time back I thought that your wireless card did not support WPA2.
It is upgradeable to support AES along with enabling software implementation.

If you have upgraded it then ignore this.....

First link is the cards support page, second is its technical spec. doc
[http://support.intel.com/support/wireless/wlan/pro2200bg/sb/cs-009093.htm](http://support.intel.com/support/wireless/wlan/pro2200bg/sb/cs-009093.htm)
[http://download.intel.com/support/wireless/wlan/pro2200bg/sb/2200bgprodbrief.pdf](http://download.intel.com/support/wireless/wlan/pro2200bg/sb/2200bgprodbrief.pdf)

WPA is basically WEP but uses TKIP .  It is an intermediate protocol between WEP and WPA2
WPA2 supports more robust encryption using AES (in counter mode with CBC-MAC) aka. CCMP

Your router does support WPA2.
You should be able to use WPA. This is more secure than WEP.

Enable/check WPA compatibility on the router
In wpa_supplicant.conf set 
network={
.....
key_mgmt=WPA-PSK
proto=WPA
scan_ssid=1			# use if BSSID is hidden
pairwise=TKIP
group=TKIP
.....
}

Alternatively, configure all within /etc/network/interfaces as demonstrated in various posts.

---

