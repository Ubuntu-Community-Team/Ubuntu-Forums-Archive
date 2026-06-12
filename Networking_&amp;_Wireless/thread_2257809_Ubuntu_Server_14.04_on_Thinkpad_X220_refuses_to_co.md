---
title: "Ubuntu Server 14.04 on Thinkpad X220 refuses to connect to my WLAN"
date: 2014-12-22
forum: Networking &amp; Wireless
---

### Post by mark183 on 2014-12-22
Dear community, trying to turn a ThinkPad X220 into a headless music server/player running Ubuntu Server 14.04. All fine so far but now I am stuck with the WiFi configuration. Granted, it may be not the best idea to attach a server over WLAN, but fact is that I cannot cable it to my home NW. 


I have followed the thread "Before posting in Networking & Wireless". I.e. updated the system, downloaded the wireless diagnosis script, changed /etc/network/interfaces so that the box would/should connect to my access point:


```

auto wlan0
iface wlan0 inet static
address 192.168.1.41
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 195.186.4.162 195.186.1.162
wpa-ssid t7r9kkjz
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <key>

```


(The SSID is not broadcast, therefore wpa-ap-scan 2).


Whereby wpa-psk was generated with:


```

mark@x220:~$ wpa_passphrase t7r9kkjz "<ascii key>"
network={
[INDENT]ssid="t7r9kkjz"[/INDENT]
[INDENT]#psk="<ascii key>"[/INDENT]
[INDENT]psk=...[/INDENT]
}

```


Then I ran the script, put back the /etc/network/interfaces to wired configuration and fetched the wireless-info.txt (attached). Browsing through it does not reveal any hint - well, to me at least. As can be seen the command ```
iwlist scan
``` brings up the SSIDs in my neighborhood (but not mine, as it is not broadcast).



Just for the fun of it I configured /etc/network/interfaces for connecting to the portable hotspot on my mobile phone:


```

auto wlan0
iface wlan0 inet dhcp
wpa-ssid XperiaZ1Compact
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <key>

```



(wpa-psk generated as above, with input data appropriate for the hot spot)


Then:


```


mark@x220:~$ **sudo ifdown wlan0 && sudo ifup -v wlan0**

ifdown: interface wlan0 not configured
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan0.pid": 0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 1 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "XperiaZ1Compact" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-pairwise CCMP -- OK
wpa_supplicant: wpa-group CCMP -- OK
wpa_supplicant: wpa-key-mgmt WPA-PSK -- OK
wpa_supplicant: wpa-proto RSN -- OK
wpa_supplicant: enabling network block 0 -- OK
dhclient -1 -v -pf /run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases wlan0
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Listening on LPF/wlan0/a0:88:b4:7e:ac:00
Sending on LPF/wlan0/a0:88:b4:7e:ac:00
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x5f045dd0)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11 (xid=0x5f045dd0)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

mark@x220:~$

```



I.e. same result with dhcp and an SSID that is broadcast.


Any hint??


Thanks a million & BR

Mark

---

### Post by chili555 on 2014-12-22
> auto wlan0
iface wlan0 inet static
address 192.168.1.41
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 195.186.4.162 195.186.1.162
wpa-ssid t7r9kkjz
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <key>Wow! That is one busy file! In /etc/network/interfaces, wpa-psk expects to see the key in clear text, not a scrambled encrypted version. I suggest you amend the file to:```
auto wlan0
iface wlan0 inet static
address 192.168.1.41
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 195.186.4.162 195.186.1.162
wpa-ssid t7r9kkjz
wpa-psk <key>
```...where <key> is the key in clear text. Restart the interface:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```And test:```
ping -c3 www.ubuntu.com
```

---

### Post by mark183 on 2014-12-23
Chili555, thanks for your swift reply. Yes that file is bloated, it got that way during my trouble shooting efforts! I had started off precisely with your suggested configuration, incl. the key in clear text. Well, back to square one, then:


 /etc/network/interfaces:
 ```

  auto wlan0
 iface wlan0 inet static
 address 192.168.1.41
 netmask 255.255.255.0
 gateway 192.168.1.1
 dns-nameservers 195.186.4.162 195.186.1.162
 
wpa-ssid t7r9kkjz
wpa-psk <key>

```


There's one more small thing I changed: the key used for connecting to the access point used to contain spaces. Therefore I had quotes in this line: wpa-psk " ….. ". I have now removed the spaces (in the access point, and in a dozen devices connecting to it …).


Reboot, then I ran the wireless-script again. Now the result is slightly different (wireless-info.txt attached): I find this line:


```


##### iwlist scan #######################


eth0      Interface doesn't support scanning.



lo        Interface doesn't support scanning.


[COLOR=#0000ff]wlan0     Interface doesn't support scanning : Device or resource busy[/COLOR]


```



In the previous report I had a list of my neighbors' SSIDs; now the device seems to be too busy for scanning. But busy with what? I still do not have a connection with the router.



Meanwhile I also checked the version of the driver for the Centrino Advanced-N 6205 used by the x220:
```

mark@x220:~$ dmesg | grep iwlwifi
[   10.067784] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.067900] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   10.253003] iwlwifi 0000:03:00.0: loaded [COLOR=#0000ff]firmware version 18.168.6.1[/COLOR] op_mode iwldvm

[   10.514414] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.514415] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled

[   10.514416] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.514417] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   10.514513] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   11.670028] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   11.670232] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   11.936791] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   11.937005] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
mark@x220:~$

```


According to [http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi), 18.168.6.1 should be the latest version.


Also, I checked the syslog (excerpt from the last boot attached) for suspicious lines. And here at the very end I find:
```


Dec 23 18:28:46 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:28:52 x220 kernel: [   26.674315] init: plymouth-upstart-bridge main process ended, respawning
Dec 23 18:29:19 x220 ntpdate[844]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Dec 23 18:29:19 x220 ntpdate[844]: no servers can be used, exiting
Dec 23 18:29:19 x220 wpa_supplicant[702]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Dec 23 18:29:22 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:29:27 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:30:12 x220 ntpdate[1439]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Dec 23 18:30:12 x220 ntpdate[1439]: no servers can be used, exiting
Dec 23 18:30:15 x220 wpa_supplicant[702]: message repeated 6 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Dec 23 18:30:18 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:30:23 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:30:56 x220 wpa_supplicant[702]: message repeated 4 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Dec 23 18:30:59 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:31:04 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:31:12 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:31:15 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:31:20 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:31:45 x220 wpa_supplicant[702]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Dec 23 18:31:48 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:31:53 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:32:17 x220 wpa_supplicant[702]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Dec 23 18:32:20 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:32:25 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:32:33 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED
Dec 23 18:32:36 x220 wpa_supplicant[702]: nl80211: send_and_recv->nl_recvmsgs failed: -33
Dec 23 18:32:41 x220 wpa_supplicant[702]: wlan0: CTRL-EVENT-SCAN-STARTED

```


I can't make much sense from this. The message:
```


nl80211: send_and_recv->nl_recvmsgs failed: -33

```
seems to be a known issue. There are a few threads discussing this (e.g. [http://ubuntuforums.org/showthread.php?t=2224450](http://ubuntuforums.org/showthread.php?t=2224450)). But I have no clue if it is relevant in my case.


Still playing around … and happy for every hint!


Thanks & BR
Mark

---

### Post by chili555 on 2014-12-23
>  now the device seems to be too busy for scanning. But busy with what? I still do not have a connection with the router.Indeed! As is often the case, another problem, and one that is not very apparent without some digging, is the real culprit. No amount of fiddling with the interfaces file will likely change things if the interface wlan0 is 'busy.' 

Are there any clues here?```
sudo ifdown wlan0
sudo iwlist wlan0 scan
```Is this the official Ubuntu server installation? Do you have rfkill installed?```
sudo rfkill list all
```I suggest you try resetting the BIOS to defaults and then let us see:```
dmesg  >  wifi.txt
```Paste the file wifi.txt here and let us see the link in your reply: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by mark183 on 2014-12-24
OK, let's go. ```
sudo ifdown wlan0
``` returns an error which does not seem to be related with the issue at hand:

```


no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory


``` 



Apart from that: nothing.



```
sudo iwlist wlan0 scan
``` returns my neighbors SSIDs if issued prior to the ifdown command, and this output after ifdown:

```



wlan0     Interface doesn't support scanning : Network is down


```



Quite normal I suppose?



I could not really figure out how to reset the BIOS, but I suppose what you are after is the page Security => I/O Port Access. I can confirm that all ports are enabled, see the attached pic.


Then the last one: ```
sudo rfkill list all
``` returns:

```




0: hci0: Bluetooth     Soft blocked: no

     Hard blocked: no

1: tpacpi_bluetooth_sw: Bluetooth

     Soft blocked: no

     Hard blocked: no

2: phy0: Wireless LAN

     Soft blocked: no


     Hard blocked: no


```




Which I guess is good news!



And here's the [wifi.txt]("http://paste.ubuntu.com/9613342/").


I searched through it (wifi, wlan, 6205, …) and did some googling, but here I am definitely lost.



One of the last lines:

```
 [   12.596922] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```



I guess this is not relevant? I am not trying to set up IPv6.



Thanks & BR

Mark

---

### Post by chili555 on 2014-12-24
> I could not really figure out how to reset the BIOSIn your attachment at the lower right, it shows that F9 resets the BIOS to defaults. Then press F10 to save and close. > One of the last lines:
 ```
[   12.596922] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```
I guess this is not relevant? I am not trying to set up IPv6.Correct; not relevant in this context.

I see a lot of questionable items in dmesg, such as:> [    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!And also:> [    0.153542] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPMAnd also:> [    0.182713] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
[    0.182715] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
[    0.182718] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
[    0.182720] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
[    0.182723] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
[    0.182725] system 00:00: [mem 0x00100000-0xdf9fffff] could not be reserved
[    0.182728] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
[    0.182731] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reservedI don't know if these contribute to your troubles, but they sure sound ominous. I am hoping that resetting the BIOS helps.

I see this:> [   10.942145] type=1400 audit(1419451554.590:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=578 comm="apparmor_parser"
[   10.942150] type=1400 audit(1419451554.590:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/[COLOR="#FF0000"]NetworkManager[/COLOR]/nm-dhcp-client.action" pid=578 comm="apparmor_parser"Is or was Network Manager installed?```
ps aux | grep etwork
```

---

### Post by mark183 on 2014-12-25
```

In your attachment at the lower right, it shows that F9 resets the BIOS to defaults. Then press F10 to save and close. 

```
Oops, sorry for that. Have now reset and saved the BIOS.


All those ominous messages are still around. Here's the new [wifi.txt]("http://paste.ubuntu.com/9618172/").



About the Network Manager: I was briefly running Ubuntu Desktop 14.04 on this X220. BTW, no problem connecting to my hotspot by means of the GUI. However a week ago I did a fresh install of Ubuntu Server 14.04, thereby whipping out all partitions and setting up from scratch. 


```

mark@x220:~$ ps -aux | grep etwork
mark      1937  0.0  0.0  11744   916 pts/0    S+   17:26   0:00 grep --color=auto etwork
mark@x220:~$

```


In wifi.txt:
```


[   10.169210] type=1400 audit(1419522091.881:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=599 comm="apparmor_parser"
[   10.169216] type=1400 audit(1419522091.881:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"
[   10.169219] type=1400 audit(1419522091.881:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=599 comm="apparmor_parser"
[   10.169392] type=1400 audit(1419522091.881:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=591 comm="apparmor_parser"
[   10.169398] type=1400 audit(1419522091.881:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=591 comm="apparmor_parser"
[   10.169403] type=1400 audit(1419522091.881:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=591 comm="apparmor_parser"
[   10.169409] type=1400 audit(1419522091.881:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=622 comm="apparmor_parser"
[   10.169414] type=1400 audit(1419522091.881:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=622 comm="apparmor_parser"
[   10.169418] type=1400 audit(1419522091.881:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=622 comm="apparmor_parser"
[   10.169554] type=1400 audit(1419522091.881:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=599 comm="apparmor_parser"

```



As I understand the Server edition should not by default install the NetworkManager? I certainly have not installed it manually afterwards.


mark@x220:~$ ll /etc/NetworkManager
ls: cannot access /etc/NetworkManager: No such file or directory
mark@x220:~$


And: 


```

mark@x220:~$ nmcli help
The program 'nmcli' is currently not installed. You can install it by typing:
sudo apt-get install network-manager
mark@x220:~$

```


On [this]("https://help.ubuntu.com/community/NetworkManager") page I found:



```

Using NetworkManager on the command line


NetworkManager now ships with nmcli, a simple interface to allow users to connect to particular networks, and even create connections to new wireless networks they have never connected to.


nmcli help


Provides all the information about how to use the nmcli utility. 

```



Could that be of any help?


Thanks & BR
Mark

---

### Post by chili555 on 2014-12-25
How about?```
sudo updatedb
locate NetworkManager
locate network-manager
```

---

### Post by mark183 on 2014-12-25
Sure:
```

mark@x220:~$ sudo updatedb
[sudo] password for mark:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
mark@x220:~$ locate NetworkManager
/usr/share/locale-langpack/en_AU/LC_MESSAGES/NetworkManager.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/NetworkManager.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/NetworkManager.mo
mark@x220:~$ locate network-manager
mark@x220:~$

```

---

### Post by mark183 on 2014-12-30
Is there a way to examine more closely what is going on between the X220 and my access point? 
When bringing up the interface I see many OKs etc. but in the end there's no connection:

```

mark@x220:~$ [COLOR=#0000ff]sudo ifdown wlan0 && sudo ifup -v wlan0[/COLOR]
[sudo] password for mark:
Configuring interface wlan0=wlan0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/ethtool
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan0.pid -i wlan0 -D nl80211,wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan0.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan0
wpa_supplicant: wpa-ap-scan 2 -- OK
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "t7r9kkjz" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK
ip addr add 192.168.1.41/255.255.255.0 broadcast 192.168.1.255    dev wlan0 label wlan0
ip link set dev wlan0   up
 ip route add default via 192.168.1.1  dev wlan0
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
mark@x220:~$

```

Is there a way to show more details? Was tha key actually accepted or not?

Thanks & BR
Mark

---

### Post by chili555 on 2014-12-30
What is the result if you temporarily change to DHCP? Does it connect?```
auto wlan0
 #iface wlan0 inet static
 #address 192.168.1.41
 #netmask 255.255.255.0
 #gateway 192.168.1.1
 #dns-nameservers 195.186.4.162 195.186.1.162
iface wlan0 inet dhcp
 
wpa-ssid t7r9kkjz
wpa-psk <key>
```And then:```
sudo ifdown wlan0 && sudo ifup -v wlan0
```And then:```
ifconfig
route -n
```

---

### Post by mark183 on 2014-12-30
I tried earlier with a separate access point, using dhcp and without security - no success.

Just tried again with my "normal" access point. Then re-boot, then sudo ifdown wlan0, then sudo ifup -v wlan0 &> ifup.txt.
ifup.txt then contains this:

```

OK

dhclient -1 -v -pf /run/dhclient.wlan0.pid -lf /var/lib/dhcp/dhclient.wlan0.leases wlan0     
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/a0:88:b4:7e:ac:00
Sending on   LPF/wlan0/a0:88:b4:7e:ac:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16 (xid=0x600f62f1)
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0x600f62f1)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ethtool
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

ifconfig:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8416 (8.4 KB)  TX bytes:8416 (8.4 KB)

wlan0     Link encap:Ethernet  HWaddr a0:88:b4:7e:ac:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Is there no way to examine what is going on between the X220 and my access point? 
I'd like to see what we receive from the AP; some sort of "reject", or noting at all?

Thanks & BR
Mark

---

### Post by mark183 on 2014-12-30
Just to give it a try I have switched on SSID broadcast on my access point and what do I see: my X220 finally connects to the WLAN!


Now ifconfig returns:
```

lo        Link encap:Local Loopback            inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3493 (3.4 KB)  TX bytes:3493 (3.4 KB)


wlan0     Link encap:Ethernet  HWaddr a0:88:b4:7e:ac:00  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fe7e:ac00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 

          RX bytes:44913 (44.9 KB)  TX bytes:17900 (17.9 KB)

```



Strange thing now: when I turn off SSID broadcast again, with all my devices connected, the X220 is instantly lost, while all the others (a MAC Book Air, an old notebook running Fedora Linux, and an Android phone) remain connected. When I turn back on SSID broadcast, the connection to the X220 is up again. I turned on and off half a dozen times, with consistent results: Ubuntu looses connection when SSID broadcast is turned off, all other devices remain connected. What makes Ubuntu loose the connection while the others do not seem to care?


Now I also tried this: added this line in /etc/network/interfaces:
```


wpa-ap-scan 2

```
And what happens? The box does not connect to the AP, with or without SSID broadcast.


BR
Mark

---

### Post by chili555 on 2014-12-30
Please try:```
auto wlan0
 iface wlan0 inet static
 address 192.168.1.41
 netmask 255.255.255.0
 gateway 192.168.1.1
 dns-nameservers 195.186.4.162 195.186.1.162
wpa-scan-ssid 1
wpa-ssid t7r9kkjz
wpa-psk <key>
```From here: [http://unix.stackexchange.com/questions/48431/connect-to-hidden-wifi-ap-with-wpa-supplicant](http://unix.stackexchange.com/questions/48431/connect-to-hidden-wifi-ap-with-wpa-supplicant)

---

### Post by mark183 on 2014-12-30
That's the trick. With "wpa-scan-ssid 1" the X220 connects to the hidden WLAN!

Thanks & BR
Mark

---

### Post by chili555 on 2014-12-30
Awesome! Please mark the thread Solved using thread tools at the top. Many a searcher will appreciate the solution.

Glad it's working.

---

