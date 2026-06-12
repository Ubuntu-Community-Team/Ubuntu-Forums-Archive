---
title: "Almost there with wireless, need a little direction..."
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by whobuntu on 2006-09-16
I am having problems with my wireless Linux installation.

I had it running once, but cannot get it going again. It stopped working a couple of days ago without warning.

Hardware:

Dell Inspiron 1100, 3Com OfficeConnect Pro Wireless card, 3CRGPC10075

First I installed Ubuntu Dapper 6.06. I then installed the wireless installer from [http://www.ubuntuforums.org/showthread.php?t=144820](http://www.ubuntuforums.org/showthread.php?t=144820) This is how I got it working first time.

However, this time not even NetworkManager worked. The scripts etc were there for it, but nothing showed up when I ran ps aux...

So I installed NetworkManager and it all seems to offer me the correct tools now, just cannot get it to connect.

OK, here are the gory details:

$ lspci # after having removed extraneous info
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

This line promted me to follow the instructions from [https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k?highlight=%28WifiDocs%2FDriver%29)

Then, running lspci -n I get:

0000:03:00.0 0200: 11ab:1faa (rev 03)

.. which means (I presume) to use the drivers from the 3com site. I have tried this, to no avail.

So I ran

sudo modprobe ndiswrapper
sudo modprobe mrv8k

... and then

sudo  ndiswrapper -l
Installed ndis drivers:
mrv8335         driver present, hardware present

(Before I continue: I tried sudo ndiswrapper -i /path/to/w29n51.inf (because the 11ab:1faa dictated I use the w28n51.inf), but then ndiswrapper -l reports that the driver is present, but with no hardware present I thought I was onto a no-brainer and started using the mrv8335 driver)

and dmesg reported:

[17180528.384000]  <3>ndiswrapper (IoCreateUnprotectedSymbolicLink:744): --UNIMPLEMENTED--
[17180529.412000] wlan0: vendor: ''
[17180529.412000] wlan0: ndiswrapper ethernet device 00:12:b9:54:cb:1f using driver mrv8335, 11AB:1FAA.5.conf
[17180529.412000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180535.288000] ieee80211_crypt: registered algorithm 'NULL'
[17180535.292000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17180535.292000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17180535.336000] mrv8k: Marvel 8xxx Wireless driver, 0.0.2
[17180535.336000] mrv8k: Copyright(c) 2005 Luc Saillard <luc@saillard.org>

Next step - iwlist:

$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:12:2E:B3:BF:81
                    ESSID:"myhouse"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:0/100  Signal level:-84 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202

So it can see the AP. This is good. So far so good...

Then, check out iwconfig:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

OK - so it does not seem to be bound to my AP. So try and take care of that:

rich@howard:~$ sudo iwconfig wlan0 essid myhouse
rich@howard:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

... which does not appear to work (note the ESSID:off/any section).

OK, so I tried to down/up my wlan0 interface with sudo if[down|up] wlan0 but with no luck.

So here are the contents of my wpa_supplicant file:

#ap_scan=2
ap_scan=0

network={
        ssid="myhouse"
        #scan_ssid=1
        mode=0
        key_mgmt=WPA-PSK
        #pairwise=TKIP
        #group=TKIP
        psk=56e764767e51351e2c8d0073cc6392bae791066f5136798505923e36fbf3977c
}

My AP was initially hidden (ie I did not broadcast, but I then changed that so that the AP broadcast its existence). Here is the output of me running

sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -Dwext  -dd

Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=0
Line: 6 - start of a new network block
ssid - hexdump_ascii(len=6):
     74 61 6d 6d 75 7a                                 myhouse
mode=0 (0x0)
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='myhouse'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:12:b9:54:cb:1f
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added


... and then, nothing. It just hangs. And my LED keeps flashing on the card, unlike when I had it working before and it stopped flashing and connected. dmesg then reports:


[17179953.928000] wlan0: no IPv6 routers present
[17180018.176000] wlan0: no IPv6 routers present
[17180418.600000] wlan0: no IPv6 routers present

My /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.17.55
netmask 255.255.255.0
gateway 192.168.17.1


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


#iface wlan0 inet dhcp
iface wlan0 inet static
address 192.168.32.55
netmask 255.255.255.0
gateway 192.168.32.1
wireless-essid myhouse

auto wlan0

I read in a post that it helps to comment out the wlan0 stuff in interfaces, but this did no good either.

I would appreciate any help. I am not quite sure what to do next. If i have not supplied enough output please say.

Thanks in advance chaps and chapettes...

---

### Post by Sporkman on 2007-07-17
> **whobuntu said:**
> Then, check out iwconfig:

...

wlan0     IEEE 802.11FH  ESSID:off/any


So why does it report "802.11FH" instead of "802.11g"??

BTW I, too, am having problems with this very same wireless card. I'll start a more detailed thread on it when I get home.

---

### Post by kevdog on 2007-07-17
Why do you need both of these statements???

> sudo modprobe ndiswrapper
sudo modprobe mrv8k

What does 
lshw -C network 
show.  Lets try first to determine what driver you are actually using?  From the above your card will either use the ndiswrapper driver or the mrv8k driver.  You cant use both.

---

