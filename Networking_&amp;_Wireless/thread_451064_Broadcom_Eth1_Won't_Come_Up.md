---
title: "Broadcom Eth1 Won't Come Up"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by transkinetic on 2007-05-21
What is it doing down there?

I just installed Feisty on a PowerBook G4. The Wireless does not work. I tried following [COLOR="Blue"][HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=202834")[/COLOR]with no success. I'm trying to connect with wpa1, dhcp, and essid broadcast. Am I missing some preliminary step? Do I need extra drivers/firmwares/onions?

entropy@skeletor:~$ sudo ifconfig eth1 up   
SIOCSIFFLAGS: No such file or directory

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

entropy@skeletor:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:24:8e:bd:83
Sending on   LPF/eth1/00:11:24:8e:bd:83
Sending on   Socket/fallback
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Could not set interface 'eth1' UP
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:11:24:8e:bd:83
Sending on   LPF/eth1/00:11:24:8e:bd:83
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down

...

---

### Post by thantos on 2007-05-22
post the output of:

```
sudo iwlist eth1 scan
```

and post your /etc/network/interfaces file (with minor editing of sensitive information).

if you want after a restart try:

```
sudo dhclient
```

although I don't think this will work, it is worth a shot.

---

### Post by transkinetic on 2007-05-22
entropy@skeletor:~$ sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : No such device

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wpa-driver wext
wpa-ssid u67i
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ******
wireless-essid u67i

---

### Post by thantos on 2007-05-22
Ok, the ubuntu website has support for trying to get wireless with a broadcom 43xx (in your case broadcom 4306).  

[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless")
[http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+broadcom]("http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+broadcom")

should help.

A couple things you can do:

```

sudo cp /etc/network/interfaces /etc/network/interfaces.original
sudo "favorite text editor" /etc/network/interfaces

```
then make your /etc/interfaces file look like this
```


auto lo
iface lo inet loopback

auto eth1                <-- Added line
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid u67i
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk ******
wireless-essid u67i
client dhclient            <-- Added line

```
Reboot (or restart network) and see if that helps.
If you don't use dhcp make the line:

```
iface eth1 inet dhcp
```

into

```
iface eth1 inet static
```

and then add the lines (I think you can put them in place of "client dhclient" at the end)

```

address "your ip address"
netmask "your netmask" (good bet 255.255.255.0)
gateway "your default gateway"

```

If that doesn't work read up on the interfaces file (man interfaces(5))

If that doesn't work search the forums for "broadcom 4306" Also if you can do the same for the ubuntu wiki.  There is a site that works on bcm43xx drivers and I believe there is full support for your model.  I think that feisty automatically installs these though.  To see if you have it:

```
sudo aptitude
```
then do a search for bcm (press "/" then "bcm") (or "bcm43")

What is the output of:

```
sudo lspci -v | less
```

For feisty I guess there is an error that Avahi has that causes this.  (Avahi configures your
device in the case that it cannot find a dhcp server  to a standard ip scheme to connect with other devices that can't find a dhcp server (I guess it is known as zeroconf as well)).

Hopefully this helps.

---

### Post by whitetrash on 2007-05-22
I also have a broadcom card in my computer. I had the same sort of problem when I first installed, Ubuntu found my wireless card and I could try and use it (I setup my wireless I don't know how many times to no avail). I tried everything possible to get WPA to work. It turned out that even though Ubuntu could see the card, without the firmware it couldn't do anything with it (hens no WPA for me).

I followed this guide to getting the firmware installed: [http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)

Worked like a charm for me.

---

### Post by transkinetic on 2007-05-22
it works. The BCMXXX cutter dealy enabled the card and the security howto let me connect with wpa
yays
thankyouthankyouthankyou

---

