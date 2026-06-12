---
title: "WPA: How to get it working?"
date: 2005-12-06
forum: Networking &amp; Wireless
---

### Post by starfire1983 on 2005-12-06
I can get my broadcom wireless adpater working and scanning for networks but the odd thing is, I can't find where to configure it to work with a WPA-PSK (for my home wireless network) and WEP (school and anywhere else) encryption. I haven't been able to get it to really connect to even an unsecured network. I've got it setup in NDIS wrapper.

---

### Post by jafenske on 2005-12-06
Here are some links to pages that do a good job explaining how to get WPA working. 

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto) 

[http://www.fmepnet.org/debian_wpa.html](http://www.fmepnet.org/debian_wpa.html)

Good Luck'

---

### Post by starfire1983 on 2005-12-06
I've decided getting WPA is too much of a pain to get working so I switched my network over to 128-bit encryption WEP. Not the best and easily hacked, but man WPA is such a pain. I did everything on those pages and still nothing. Given, there's 3 secure networks here (including mine) and 1 unsecure network. But even when explicitly naming the network to connect to, it wouldn't go.

Also, I read about something called "wpa_gui" but I can't find it anywhere. The #1 page on Google doesn't load. This is -definately- something that should be worked on for not just Ubuntu, but Linux all around. Better secured networks are a good thing.

Edit: The URL of the #1 result for wpa_gui on Google is [http://hostap.epitest.fi/wpa_supplicant/wpa_gui.html](http://hostap.epitest.fi/wpa_supplicant/wpa_gui.html)

---

### Post by jafenske on 2005-12-06
It's realy not that bad... You just need to configure two files and those two links lay it out for you.  The benefit from WPA is well worth the time spent.  I have read that a WEP network can be cracked in about an hour with the right tools and a experienced user.  I'm willing to help you get it up and running.

I agree with you that a gui would be very nice.  Until then... seeing as I'm a engineer and not a programmer all I can do is help you.

Joe

---

### Post by jafenske on 2005-12-06
On my machine at home I've got some better links, I will post them later.

---

### Post by starfire1983 on 2005-12-06
Well I'll be damned, if decided to work after I rebooted.

When I switch my router over to WPA-PSK, wpa_supplicant outputs this when I run it w/ sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper

ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
Trying to associate with 00:13:46:a3:ed:d0 (SSID='Apt207' freq=2437 MHz)
Associated with 00:13:46:a3:ed:d0
WPA: Key negotiation completed with 00:13:46:a3:ed:d0 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:13:46:a3:ed:d0 completed (auth)

All I can decipher from that is that it successfully authenticated the WPA-PSK key with my AP. But what concerns me the "No such device" line. I've got everything working now. The second link ([http://www.fmepnet.org/debian_wpa.html](http://www.fmepnet.org/debian_wpa.html)) is a far superior resource than the Wiki, sadly. My only conundrum is...will I have to go through this on each reboot or will wpa_supplicant be running in the background without me needing a terminal window open to run it and to send the command to bring up wlan0?

---

### Post by jafenske on 2005-12-06
I have this problem with a gentoo box of mine and sadly I think it is a bug.  But the good news is that is hasn't effected my wireless connection.  If you add wpa supplicant to start on boot and your config file is correct (which it sounds like it is) it will just run in the background.

---

### Post by starfire1983 on 2005-12-06
Odd thing after I just rebooted. I had to run sudo ifdown wlan0 then sudo ifup wlan0 to get my wireless working. wpa_supplicant was already ready in the background, but somehow my wireless wasn't working or something. It should be set to start up at boot time but seems not. This is what's in my /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
pre-up /etc/init.d/wpasupplicant start
pre-up sleep 5

---

### Post by jafenske on 2005-12-06
Try adding

```
wireless-essid [COLOR="Red"]your essid[/COLOR]
```

to /etc/network/interfaces after iface wlan0 inet dhcp

---

### Post by pr0fess0r on 2005-12-09
Hi
I'm running Ubuntu 5.10 on a dual PIII 500 and I'm having no luck with a Prism card that shows up in the Network Settings as eth1 (which I cant activate) so I'm using a standard NIC as eth0. I've been through the wiki and as many resources as I can find. I get this error:

sudo /etc/init.d/wpasupplicant restart
Restarting wpa_supplicant: ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCSIFFLAGS: Timer expired
Could not set interface 'eth1' UP
wpa_driver_prism54_set_countermeasures - not yet implemented
done.

I tried the windows drivers and ndiswrapper

ndiswrapper -l
Installed ndis drivers:
o4i01a  driver present, hardware present

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dndiswrapper
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCSIFFLAGS: Timer expired
Could not set interface 'eth1' UP
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/eth1' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

my config files are:

/etc/default/wpasupplicant
ENABLED=1
OPTIONS="-w"
OPTIONS="-i eth1 -D prism54 -c /etc/wpa_supplicant.conf"

/etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="MyNETWORK"
	scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
      psk=(psk)
}

/etc/network/interfaces
auto lo
iface lo inet loopback
mapping hotplug
	script grep
	map eth0

iface eth0 inet static
	address 192.168.x.x
	netmask 255.255.255.0
	network 192.168.x.x
	broadcast 192.168.0.255
	gateway 192.168.x.x
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 210.xxx.xxx.xxx

auto eth0

iface eth1 inet static
address 192.168.xxx.xxx
netmask 255.255.255.0
gateway 192.168.xxx.xxx
wireless-essid MyNETWORK
wireless-key s:xxxxxxxxxx

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:xx:xx:xx:xx
          inet addr:192.168.xxx.xxx  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:xxxx:5cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2295246 (2.1 MiB)  TX bytes:372483 (363.7 KiB)
          Interrupt:18 Base address:0xb000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1012 (1012.0 b)  TX bytes:1012 (1012.0 b)

Is there anything I can check to whether the problem is the card, the driver or just the configuration? My network uses WPA-PSK TKIP
Thanks in advance for any helps or tips

---

### Post by mgor on 2005-12-29
[QUOTE=pr0fess0r]wpa_driver_prism54_set_countermeasures - not yet implemented[/QUOTE]

the prism54 driver dosen't support wpa ... yet.

---

