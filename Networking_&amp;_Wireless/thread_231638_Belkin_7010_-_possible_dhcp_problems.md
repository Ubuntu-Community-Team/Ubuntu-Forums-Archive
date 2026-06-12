---
title: "Belkin 7010 - possible dhcp problems"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by ScotsXB on 2006-08-07
After trying a lot of How-To's to get the card working, nothing seems to work.

Using the bcm43xx-fwcutter has allowed me to scan for network and attempt to connect, but it wont.

It seems to have trobule receiving an IP from DHCP.

$iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Karnage"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.467 GHz  Access Point: 00:14:7F:30:17:9F
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$iwlist eth1 scanning
```
eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:30:17:9F
                    ESSID:"Karnage"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-159 dBm
                    Extra: Last beacon: 80ms ago

```

Also ...

$sudo dhclient eth0
```
Listening on LPF/eth0/00:0f:b0:47:07:3a
Sending on   LPF/eth0/00:0f:b0:47:07:3a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.67 -- renewal in 34060 seconds.

```

$sudo dhclient eth1
```
Listening on LPF/eth1/00:11:50:1d:4d:84
Sending on   LPF/eth1/00:11:50:1d:4d:84
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any ideas?

---

### Post by cantormath on 2006-08-07
> **ScotsXB said:**
> After trying a lot of How-To's to get the card working, nothing seems to work.

Using the bcm43xx-fwcutter has allowed me to scan for network and attempt to connect, but it wont.

It seems to have trobule receiving an IP from DHCP.

$iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Karnage"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.467 GHz  Access Point: 00:14:7F:30:17:9F
          Bit Rate=11 Mb/s   Tx-Power=15 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

$iwlist eth1 scanning
```
eth1      Scan completed :
          Cell 01 - Address: 00:14:7F:30:17:9F
                    ESSID:"Karnage"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-159 dBm
                    Extra: Last beacon: 80ms ago

```

Also ...

$sudo dhclient eth0
```
Listening on LPF/eth0/00:0f:b0:47:07:3a
Sending on   LPF/eth0/00:0f:b0:47:07:3a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.67 -- renewal in 34060 seconds.

```

$sudo dhclient eth1
```
Listening on LPF/eth1/00:11:50:1d:4d:84
Sending on   LPF/eth1/00:11:50:1d:4d:84
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Any ideas?

did you try to set it up through System>Administration>Networking?

I hae network-manager, network-manager-gnome, wifi-radar(which I think is in the universe repo), and waproamd installed.

maybe that might help.

---

### Post by ScotsXB on 2006-08-07
Thanks for the reply.

I have them installed, as I've tried anything I can.

Wifi Radar states that it is connected to the network yet couldnt get an ip.

Going to try and set a static ip in hope that will work.

It never .... ](*,)

---

### Post by orodos on 2006-08-07
I have the exact same problem. DHCPDISCOVER I can't remember when it began, or what i did to cause this calamity unfortunately.
If you look at syslog/kernlog you also get this message: 

Aug  7 21:48:25 localhost kernel: [17181209.764000] TKIP: replay detected: STA=00:11:50:d7:79:00 previous TSC 000000000b33 received TSC 000000000b33

Where the mac addy is the wireless card.
I'm able to connect to the internet and am connected right now, only it is insanely slow... choppy would describe it best. usually have to refresh a few times to get a page to even load. 
Any help would result in ressurection of one to status of god/goddess idol and i will make sacrafices of york peppermint patty klondike bars and other equally awesome things annually in said idol's name.

---

### Post by ScotsXB on 2006-08-10
Ok, I've somehow fixed it. :D 

Firstly I removed wifi-radar

Then downloaded the driver firmware from [http://www.drinus.net/airport/wl_apsta.o ]("http://www.drinus.net/airport/wl_apsta.o")

In the terminal, from the directory where the file was downloaded to (normally the Desktop) I typed
```
sudo bcm43xx-fwcutter -w /lib/firmware wl_apsta.o
```

Re checked my WEP key and network name, then typed
```
sudo modprobe bcm43xx
sudo iwconfig eth1 ap any

```

And reboot.

Let me know if this helps or I need to explain it better.

---

### Post by orodos on 2006-08-10
So you suppose its a problem with the firmware? I used fwcutter, not ndiswrapper, to begin with. Odd, odd, odd. I found a temporary fix in turning off my router's wpa, however, whenever i do a bootup with the system it completely locks if i dont immediately switch to lo while the network manager locates and connects to the wireless network. Then I am able to switch to eth1 and everything is spiffy fine, no disconnections or slow speed...

---

