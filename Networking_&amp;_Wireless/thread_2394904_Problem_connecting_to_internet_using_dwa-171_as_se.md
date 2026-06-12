---
title: "Problem connecting to internet using dwa-171 as second wireless device"
date: 2018-06-23
forum: Networking &amp; Wireless
---

### Post by peterg17 on 2018-06-23
Hi,
I have a laptop I connect to the internet with using my mobile phones hotspot. I have several wifi devices (printer tv) that currently connect to my mobile, and every time I leave home all these devices disconnect. I decided to set up my laptop as a permanent hotspot host and add a second wireless device that connects to my mobile phone and through that onto the internet.

I ended up getting a d-link DWA-171 usb wireless adapter. I downloaded and compiled the rtl8821au kernel driver. I use wpa_supplicant in a script run by ifup from a systemctl service. My wpa.conf file has nothing more than an ssid and a psk. I had to add a -D option to wpa_supplicant (-D nl80211,wext) to get it to work (from wpa_supplicant log).

When I configure the device, internet does not work. The ping and dig utilities work for a minute or so after changing from the primary wireless device, then stops working. The device is apparently configured ok. There is no difference in the route -n output compared with using the primary device. The file /etc/resolv.conf is identical. The only difference is with the iwconfig output, which is

*enx9cd6435b7223  IEEE 802.11bgn  ESSID:"HTC Portable Hotspot 3E2C"  Nickname:"<WIFI@REALTEK>"*
*           Mode:Managed  Frequency:2.437 GHz  Access Point: 40:4E:36:1A:EF:92*
*           Bit Rate:87 Mb/s   Sensitivity:0/0*
*           Retry : off   RTS thr: off   Fragment thr: off*
*           Encryption key:****-****-****-****-****-****-****-****   Security mode: open*
*           Power Management: off*
*           Link Quality=100/100  Signal level=100/100  Noise level=0/100*
*           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0*
*           Tx excessive retries:0  Invalid misc:0   Missed beacon:0*


With the primary device, which works, the iwconfig output is:
*wlan0     IEEE 802.11bgn  ESSID:"HTC Portable Hotspot 3E2C"  *
*          Mode:Managed  Frequency:2.437 GHz  Access Point: 40:4E:36:1A:EF:92   *
*          Bit Rate=65 Mb/s   Tx-Power=15 dBm   *
*          Retry short limit:7   RTS thr: off   Fragment thr: off*
*          Encryption key: off*
*          Power Management: off*
*          Link Quality=70/70  Signal level=-35 dBm  *
*          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0*
*          Tx excessive retries:1  Invalid misc:235   Missed beacon:0*



and the wpa_supplicant log when connecting with the errant device is:

*Successfully initialized wpa_supplicant*
*nl80211: Could not configure driver mode*
*nl80211: deinit ifname=enx9cd6435b7223 disabled_11b_rates=0*
*ioctl[SIOCSIWAP]: Operation not permitted*
*ioctl[SIOCSIWENCODEEXT]: Invalid argument*
*ioctl[SIOCSIWENCODEEXT]: Invalid argument*
*enx9cd6435b7223: Trying to associate with 40:4e:36:1a:ef:92 (SSID='HTC Portable Hotspot 3E2C' freq=2437 MHz)*
*enx9cd6435b7223: Association request to the driver failed*
*enx9cd6435b7223: Associated with 40:4e:36:1a:ef:92*
*enx9cd6435b7223: WPA: Key negotiation completed with 40:4e:36:1a:ef:92 [PTK=CCMP GTK=CCMP]*
[I]enx9cd6435b7223: CTRL-EVENT-CONNECTED - Connection to 40:4e:36:1a:ef:92 completed [id=0 id_str=]

[/I]So looking forward for ideas on how to solve this. I suspect the problem is something to do with the encryption key setting in the iwconfig output.

---

### Post by peterg17 on 2018-06-23
I have created a more extensive wpa_supplicant output on the failing connection, using the -dd switch.
I tried to upload as an attachment, but kept getting "invalid file" error.
Cannot see any obvious problems in it.

---

### Post by peterg17 on 2018-06-24
The arp tool says the hardware address in incomplete, even though ifconfig for example provides the hardware address. There is also no HWType or Flags data, compared to the normal working wifi setup.

---

### Post by peterg17 on 2018-06-26
I discovered that ifup invokes wpa_supplicant.
So I stopped using any scripts and set up an /etc/network/interfaces entry.
The entry does something like:


[B]iface wifi_client inet dhcp
    wpa-logfile /var/log/wpa_supplicant.log
    wpa-ssid "HTC Portable Hotspot 3E2C"
    wpa-psk [My password psk]
    wpa-maint-debug
[/B]

This works, as it connects to the internet via my mobile, with the command
$ ifup wlan0=wifi_client


but the corresponding command for the usb device fails with behaviour as described above.
However the usb device does connect to the phone and obtains an ip address via dhcp.
The phone says it has the connection. The firewall is diabled. But no internet.
I log into wpa with wpa_cli and get the status. The status with the failing device is:


[B]bssid=40:4e:36:1a:ef:92
freq=0
ssid=HTC Portable Hotspot 3E2C
id=0
mode=station
pairwise_cipher=CCMP
group_cipher=CCMP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
ip_address=192.168.1.136
address=9c:d6:43:5b:72:23
uuid=13fedc65-6913-5f7c-a5c6-e441f1a5f9b8
[/B]

Why the frequency is zero is a bit of a mystery to me.

---

### Post by peterg17 on 2018-07-02
Hi,
I placed my question on linuxquestions and did receive a reply, without resolving the problem so have continued to document the problem there.
I have resolved it to an apparent driver error, where the transmit tasklet has an illegal internal state.
Investigations are continuing.

---

### Post by peterg17 on 2018-07-09
Solution discussed in this thread.
 [https://www.linuxquestions.org/questions/linux-wireless-networking-41/no-internet-with-second-wireless-device-d-link-dwa-171-a-4175632693/](https://www.linuxquestions.org/questions/linux-wireless-networking-41/no-internet-with-second-wireless-device-d-link-dwa-171-a-4175632693/)

Serious bug in the driver. Usable now, but will replace directly.

---

