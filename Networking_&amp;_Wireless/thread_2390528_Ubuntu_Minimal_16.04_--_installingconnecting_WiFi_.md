---
title: "Ubuntu Minimal 16.04 -- installing/connecting WiFi using WPA2"
date: 2018-04-29
forum: Networking &amp; Wireless
---

### Post by bobsuncle on 2018-04-29
I've done an Ubuntu minimal install using the instruction for the minimal iso found here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

The installation went smoothly and it booted normally.  I've installed packages wireless-tools and wpasupplicant but I suspect I am still missing a required package.

I can run iwconfig and see the interface.  I've created /etc/wpa_supplicant.conf using the command wpa_passphrase.  However, after running wpa_supplicant, the interface does not appear to be connected to the ESSID.  The wpa_supplicant command returns normally, saying only that initialization was completed normally.  I am unable to get an IP using dhclient as a result.

I know I am missing something, but not sure what.

Thank You!

P.S. and even though I did not type all of those sudo's in this post above, I did use them when entering the commands on the command line.

---

### Post by chili555 on 2018-04-30
Please run and post:```
cat /etc/network/interfaces
iwconfig
ps aux | grep -i network
```Thanks.

---

### Post by bobsuncle on 2018-04-30
I assume you wanted that after running wpa_supplicant ....

```
blg@U1:~$ sudo ifconfig wlp2s0 up
[sudo] password for blg: 
blg@U1:~$ sudo wpa_supplicant -B -i wlp2s0 -c /etc/wpa_supplicant.conf
Successfully initialized wpa_supplicant
blg@U1:~$ iwconfig
lo        no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=3 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
blg@U1:~$ cat /etc/wpa_supplicant.conf
network={
    ssid="redacted"
    psk=redacted
}
blg@U1:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

blg@U1:~$ ps aux | grep -i network
blg        824  0.0  0.0  14224   964 pts/0    S+   14:32   0:00 grep --color=auto -i network
blg@U1:~$ 
```

After running wpa_supplicant, the SSID is still not associated with the interface.  I have verified the SSID and password are correct in the conf file.

---

### Post by bobsuncle on 2018-04-30
and just for good measure
```
blg@U1:~$ lspci | grep -i ath
02:00.0 Network controller: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
blg@U1:~$ lsmod | grep -i ath
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              479232  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211

```

---

### Post by chili555 on 2018-04-30
> I assume you wanted that after running wpa_supplicant ....Nope. If I did, I would have clearly requested it.

Please open a terminal and do:```
sudo nano /etc/network/interfaces
```Edit the file to read:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

auto wlp2s0
iface wlp2s0 inet dhcp
wpa-ssid <your_ssid>
wpa-psk <your_key_in_clear_text>

```Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.

Reboot.

Please be certain that the key is clear text and *not* this:> using the command wpa_passphrase. 

---

### Post by bobsuncle on 2018-05-01
Thank you for your suggestion.

It still does not connect after rebooting.  The output from iwconfig is unchanged.  The SSID is still not associated with the interface.

---

### Post by chili555 on 2018-05-01
> **bobsuncle said:**
> Thank you for your suggestion.

It still does not connect after rebooting.  The output from iwconfig is unchanged.  The SSID is still not associated with the interface.Are there any interesting clues if you do:```
sudo ifdown wlp2s0 && sudo ifup -v wlp2s0
```The -v for verbose should produce some hopefully helpful output.

Does the interface scan and see your network?```
sudo iwlist wlp2s0 scan
```

---

### Post by bobsuncle on 2018-05-01
Yes, the network shows up in the iwlist scan results ....

```
blg@U1:~$ sudo ifdown wlp2s0 && sudo ifup -v wlp2s0
[sudo] password for blg: 
ifdown: waiting for lock on /run/network/ifstate.wlp2s0
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/4c:0f:6f:5e:c1:32
Sending on   LPF/wlp2s0/4c:0f:6f:5e:c1:32
Sending on   Socket/fallback
Configuring interface wlp2s0=wlp2s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /run/wpa_supplicant.wlp2s0.pid -i wlp2s0 -D nl80211,wext -C /run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlp2s0.pid
wpa_supplicant: ctrl_interface socket located at /run/wpa_supplicant/wlp2s0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "redacted" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

/sbin/dhclient -1 -v -pf /run/dhclient.wlp2s0.pid -lf /var/lib/dhcp/dhclient.wlp2s0.leases -I -df /var/lib/dhcp/dhclient6.wlp2s0.leases wlp2s0     
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/4c:0f:6f:5e:c1:32
Sending on   LPF/wlp2s0/4c:0f:6f:5e:c1:32
Sending on   Socket/fallback
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 15 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 17 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 18 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 20 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 15 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 7 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 13 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 7 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 19 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 20 (xid=0x43d65515)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 18 (xid=0x43d65515)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
```

no errors from wpa_supplicant, but the SSID is still not assigned to the interface.

---

### Post by chili555 on 2018-05-01
I wonder if your faulty wpa_supplicant.conf file may be interfering. Let's temporarily rename it and try again:```
sudo mv /etc/wpa_supplicant.conf /etc/wpa_supplicant.bak 
```Please carefully proofread the /etc/network/interfaces file for typos, case, etc. Next, try again:```
sudo ifdown wlp2s0 && sudo ifup -v wlp2s0
```Any improvement? May we see the scan result?```
sudo iwlist wlp2s0 scan
```Omit all but your own SSID and redact the MAC address, please.

---

### Post by bobsuncle on 2018-05-01
```
blg@U1:~$ sudo mv /etc/wpa_supplicant.conf /eetc/wpa_supplicant.bak
[sudo] password for blg: 
mv: cannot move '/etc/wpa_supplicant.conf' to '/eetc/wpa_supplicant.bak': No such file or directory
blg@U1:~$ sudo mv /etc/wpa_supplicant.conf /etc/wpa_supplicant.bak
blg@U1:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# wifi
auto wlp2s0
iface wlp2s0 inet dhcp
wpa-ssid redacted 
wpa-psk redacted
blg@U1:~$ sudo ifdown wlp2s0 && sudo ifup -v wlp2s0
ifdown: waiting for lock on /run/network/ifstate.wlp2s0
Killed old client process
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/redacted
Sending on   LPF/wlp2s0/redacted
Sending on   Socket/fallback
Configuring interface wlp2s0=wlp2s0 (inet)
/bin/run-parts --exit-on-error --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver nl80211,wext (default)
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /run/wpa_supplicant.wlp2s0.pid -i wlp2s0 -D nl80211,wext -C /run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: creating sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlp2s0.pid
wpa_supplicant: ctrl_interface socket located at /run/wpa_supplicant/wlp2s0
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "redacted" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: enabling network block 0 -- OK

/sbin/dhclient -1 -v -pf /run/dhclient.wlp2s0.pid -lf /var/lib/dhcp/dhclient.wlp2s0.leases -I -df /var/lib/dhcp/dhclient6.wlp2s0.leases wlp2s0     
Internet Systems Consortium DHCP Client 4.3.3
Copyright 2004-2015 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/redacted
Sending on   LPF/wlp2s0/redacted
Sending on   Socket/fallback
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 5 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 14 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 19 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 18 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 12 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 15 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 11 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 21 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 16 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 18 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 7 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 8 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 9 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 10 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 11 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 13 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 21 (xid=0x684fd530)
DHCPDISCOVER on wlp2s0 to 255.255.255.255 port 67 interval 3 (xid=0x684fd530)
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
/bin/run-parts --exit-on-error --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant
blg@U1:~$ sudo iwlist wlp2s0 scan
wlp2s0    Scan completed :
          Cell 03 - Address: redacted
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"redacted"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018caeca2c55
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0004486F6D65
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F02C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
```

---

### Post by chili555 on 2018-05-01
> blg@U1:~$ sudo mv /etc/wpa_supplicant.conf /[COLOR="#FF0000"]eetc[/COLOR]/wpa_supplicant.bak
[sudo] password for blg: 
mv: cannot move '/etc/wpa_supplicant.conf' to '/eetc/wpa_supplicant.bak': No such file or directoryPlease try again:```


sudo mv /etc/wpa_supplicant.conf  /etc/wpa_supplicant.bak



```

---

### Post by bobsuncle on 2018-05-01
I did, it is the next line.  I didn't realize that I grabbed my typo when I pasted it here.

---

### Post by bobsuncle on 2018-05-02
In fiddling with this some more, I booted up with a live USB distro.  It connects to the AP with no issues.  But then it is also using the just released 18.04 version.  It looks like it also uses network manager, which I do not have installed on my minimal version.

Of course, the minimal install ISO also connected to the wireless network during installation.  What and/or how does it connect?

Both of these lead me back to my original supposition that there is something not installed.  Looking at lsmod between the 2 versions seems to have loaded the same drivers.

At this point, I'm a bit out of ideas.  Is the answer to just install Network Manager?  I'm not sure how to do that via USB.  And would that come with a large amount of bloat-ware?

Any help would be appreciated.

Thanks!

---

### Post by chili555 on 2018-05-02
> What and/or how does it connect?That's the trick! If it connected during installation, then I doubt that something crucial is not installed.

Let's dive deep:```
uname -r
lsb_release -a
cat /etc/netplan/*.yaml
dmesg | grep -e wlp -e ath
```May I assume that you have double- and triple-checked the SSID and password in /etc/network/interfaces? MySSID vs. myssid, etc., etc.

---

### Post by bobsuncle on 2018-05-02
> May I assume that you have double- and triple-checked the SSID and password in /etc/network/interfaces? MySSID vs. myssid, etc., etc.Just checked again and they are correct .... truth be told, I had my fingers crossed, hoping that was the problem :P

```
blg@U1:~$ uname -r
4.4.0-122-generic
blg@U1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial
blg@U1:~$ cat /etc/netplan/*.yaml
cat: '/etc/netplan/*.yaml': No such file or directory
blg@U1:~$ dmesg | grep -e wlp -e ath
[    8.742433] systemd[1]: Reached target Paths.
[   12.039362] ath: phy0: ASPM enabled: 0x43
[   12.039368] ath: EEPROM regdomain: 0x65
[   12.039370] ath: EEPROM indicates we should expect a direct regpair map
[   12.039373] ath: Country alpha2 being used: 00
[   12.039374] ath: Regpair used: 0x65
[   12.046808] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[   15.988709] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
```

---

