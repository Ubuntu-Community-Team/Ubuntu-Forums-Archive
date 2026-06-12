---
title: "ndispwrapper and INPROC IPN2220 - OK in Dapper, no go in Edgy"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by TheFifth on 2006-10-27
Hi,

I'm having a problem with my WiFi card.  It's an Inproc ipn2220 which I install using ndiswrapper.

It worked fine in Dapper and appears to be installed perfectly in Edgy but it refuses to connect to any access points.

```
ndiswrapper -l
```

gives:

```
Installed drivers:
neti2220	driver installed, hardware present
```

```
iwconfig
```

gives:

```
wlan0		IEEE 802.11g	ESSID:off/any
		Mode:Managed	Frequency:2.412 GHz	Access Point: Not-Associated
		Bit Rate:1 Mb/s	Tx-Power:0 dBm
		RTS thr:2347 B	Fragment thr:2346 B
		Power Management:off
		Link Quality:0	Signal level:0	Noise level:0
		Rx invalid nwid:0	RX invalid crypt:0	Rx invalid frag:0
		Tx excessive retries:0	Invalid misc:0	Missed beacon:0
```

```
iwlist wlan0 scanning
```

Lists all of the available access points in my area, so the card must be working to a degree or it wouldn't list the access points.

The problem seems to be when I try to connect to any of the access points.  If I try:

```
ifup wlan0
```

I get:

```
Listening on	LPF/wlan0/00:11:e2:02:54:ed
Sending on	LPF/wlan0/00:11:e2:02:54:ed
Sending on	Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DCHPOFFERS received.
No working leases in persistent database – sleeping.
```

Should this be trying to send requests to 255.255.255.255?  I've no idea, but it looks odd to me!

The strange thing is that this card worked perfectly in Hoary and Dapper with ndiswrapper.  However, I had this identical problem with Breezy.  The driver appeared to be installed and the card seemed to scan OK, but I just couldn't get a connection up.  In the end I gave up with Breezy completely and went back to Hoary until Dapper was released. I hope I don't have to give up on Edgy!

Any help greatly appreciated.

Cheers,

Rich

---

### Post by TheFifth on 2006-10-27
A little update....

When I set a static IP and explicitly tell it what the gateway is and the DNS servers are, I can use the internet!

So it appears to be the DHCP client that isn't working right.  It worked perfectly with Dapper with the same access point and also works when I boot into windows.

Ideas anyone?

---

### Post by TheFifth on 2006-10-27
Ok... Think I've fixed it, but I don't know how!

I installed Network Manager from the Repos by using the static IP.  Then I added:

ndiswrapper

to the file /etc/modules, so that NM could see the wlan card.

Rebooted and all is well!  Using NM the wifi card seems to now be able to pick up an IP via DHCP.  I really don't know why NM made the difference, but it seems to have sorted it, so whatever! :D

---

