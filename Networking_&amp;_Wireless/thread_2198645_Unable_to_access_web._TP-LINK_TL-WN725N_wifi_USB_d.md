---
title: "Unable to access web. TP-LINK TL-WN725N wifi USB dongle"
date: 2014-01-09
forum: Networking &amp; Wireless
---

### Post by exekutive on 2014-01-09
[SIZE=3][FONT=tahoma][COLOR=#333333]I'm fairly computer savvy, but still super new to Linux so please bear with me.[/COLOR]
[COLOR=#333333]
The adapter info: [http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2](http://wikidevi.com/wiki/TP-LINK_TL-WN725N_v2)
Ubuntu 13[/COLOR]
[COLOR=#333333]
I downloaded the driver zip from [COLOR=#222222]https://github.com/lwfinger/rtl8188eu
[/COLOR][COLOR=#222222]Copied the bin file: sudo cp rtl8188eufw.bin /lib/firmware/rtlwifi/
[/COLOR][COLOR=#222222]"make all", then "make install"[/COLOR][/COLOR]

The installation appeared to work and Ubuntu now recognises the device. I am also able to connect to my home wifi network, and obtain a valid IP address from my ISP. However, if I point my browser to google.com, I just get "This web page is not available". [COLOR=#333333]Punching in google's IP address doesn't work either. [/COLOR]Pinging gets "unknown host google.com". The little status icon shows no reception "bars", even when the computer is right beside router.
[COLOR=#333333]
Any ideas? [/COLOR][COLOR=#333333]Thanks for your attention.[/COLOR][/FONT][/SIZE]

---

### Post by chili555 on 2014-01-09
May we please see the result of these terminal commands?```
iwconfig
dmesg | grep rtl
nm-tool
```Thanks.

---

### Post by exekutive on 2014-01-10
```
joe@bigblackbox:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"ampunchinka"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:63:2C:D0:1E   
          Bit Rate:65 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=2/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.


joe@bigblackbox:~$ dmesg | grep rtl
joe@bigblackbox:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [ampunchinka] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             connected
  Default:           yes
  HW Address:        64:66:B3:08:35:46


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TELUS0982:       Infra, 20:76:00:01:C9:50, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    TELUS2591:       Infra, 20:76:00:06:33:80, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    595484:          Infra, 7C:05:07:CC:11:53, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    TELUS1022:       Infra, 00:26:B8:EF:34:B8, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    Linksys22734:    Infra, C8:D7:19:4D:4B:A0, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA2
    klass-guest:     Infra, 20:AA:4B:D7:BD:4B, Freq 2437 MHz, Rate 16 Mb/s, Strength 0
    Shum:            Infra, 00:26:B8:F5:97:CC, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    TELUS3037:       Infra, A8:39:44:55:06:A0, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    TELUS1514:       Infra, 10:9F:A9:E8:F7:3C, Freq 2437 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
    *ampunchinka:    Infra, 00:1B:63:2C:D0:1E, Freq 2412 MHz, Rate 2 Mb/s, Strength 2
    klass:           Infra, 20:AA:4B:D7:BD:4A, Freq 2437 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2


  IPv4 Settings:
    Address:         154.5.220.92
    Prefix:          22 (255.255.252.0)
    Gateway:         154.5.220.1


    DNS:             75.153.176.9
    DNS:             75.153.176.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:11:D8:11:87:F3


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




joe@bigblackbox:~$ 

```

By the way, the blue status light on the dongle does flash when it's plugged in.

I should also add that the device works perfectly in the Windows XP environment.

Thanks again for your interest.

---

### Post by chili555 on 2014-01-10
It looks pretty solid so far! Are connected to a cable or DSL modem? Is authentication required; i.e. a username and password? Can you ping the gateway?```
ping -c3 154.5.220.1
ping -c3 75.153.176.9
ping -c3 8.8.8.8
```

---

### Post by exekutive on 2014-01-10
Zyxel VSG1432 DSL modem via Apple Airport wifi access point. Both in bridge mode (ie DHCP turned off). No authentication required.

All three "Destination Host Unreachable".

---

### Post by chili555 on 2014-01-10
What addresses, etc. do you get in Windows? Are there any clues here?```
cat /var/log/syslog grep -e wlan -e etwork
```If DHCP is turned off in both devices, where do you get this number?> IPv4 Settings:
    Address:         [COLOR="#FF0000"]154.5.220.92[/COLOR]Is it a static address provided by your ISP?

---

### Post by exekutive on 2014-01-10
It is a dynamic IP assigned by my ISP. I would get a similar one in Windows. The output to your cat command is extremely long. Do you want me to post the entire thing?

---

### Post by chili555 on 2014-01-10
Let's shorten it up:```
cat /var/log/syslog grep -e wlan -e etwork | tail -n20
```> It is a dynamic IP assigned by my ISP. I would get a similar one in Windows.May we see it, please?

---

### Post by exekutive on 2014-01-10
Windows:

---

### Post by exekutive on 2014-01-10
```
joe@bigblackbox:~$ cat /var/log/syslog grep -e wlan -e etwork | tail -n20
cat: grep: No such file or directory
cat: wlan: No such file or directory
cat: etwork: No such file or directory
Jan 10 12:50:14 bigblackbox avahi-daemon[666]: Joining mDNS multicast group on interface wlan0.IPv4 with address 75.157.12.208.$
Jan 10 12:50:14 bigblackbox avahi-daemon[666]: New relevant interface wlan0.IPv4 for mDNS.$
Jan 10 12:50:14 bigblackbox avahi-daemon[666]: Registering new address record for 75.157.12.208 on wlan0.IPv4.$
Jan 10 12:50:15 bigblackbox NetworkManager[832]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]$
Jan 10 12:50:15 bigblackbox NetworkManager[832]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.$
Jan 10 12:50:15 bigblackbox NetworkManager[832]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]$
Jan 10 12:50:15 bigblackbox NetworkManager[832]: <info> Policy set 'ampunchinka' (wlan0) as default for IPv4 routing and DNS.$
Jan 10 12:50:15 bigblackbox NetworkManager[832]: <info> Writing DNS information to /sbin/resolvconf$
Jan 10 12:50:15 bigblackbox dnsmasq[1382]: setting upstream servers from DBus$
Jan 10 12:50:15 bigblackbox dnsmasq[1382]: using nameserver 75.153.176.1#53$
Jan 10 12:50:15 bigblackbox dnsmasq[1382]: using nameserver 75.153.176.9#53$
Jan 10 12:50:16 bigblackbox NetworkManager[832]: <info> Activation (wlan0) successful, device activated.$
Jan 10 12:50:16 bigblackbox avahi-daemon[666]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::6666:b3ff:fe08:3546.$
Jan 10 12:50:16 bigblackbox avahi-daemon[666]: New relevant interface wlan0.IPv6 for mDNS.$
Jan 10 12:50:16 bigblackbox avahi-daemon[666]: Registering new address record for fe80::6666:b3ff:fe08:3546 on wlan0.*.$
Jan 10 12:50:22 bigblackbox ntpdate[2172]: step time server 91.189.94.4 offset -0.513440 sec$
Jan 10 12:50:34 bigblackbox NetworkManager[832]: <info> (wlan0): IP6 addrconf timed out or failed.$
Jan 10 12:50:34 bigblackbox NetworkManager[832]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...$
Jan 10 12:50:34 bigblackbox NetworkManager[832]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...$
Jan 10 12:50:34 bigblackbox NetworkManager[832]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.$
joe@bigblackbox:~$ 



```

---

### Post by chili555 on 2014-01-10
> Joining mDNS multicast group on interface wlan0.IPv4 with address [COLOR="#FF0000"]75.157.12.208[/COLOR]But *nm-tool* says:> Address:         [COLOR="#FF0000"]154.5.220.92[/COLOR]
    Prefix:          22 (255.255.252.0)
    Gateway:         154.5.220.1


    DNS:             75.153.176.9
    DNS:             75.153.176.1Do you have some settings applied in Network Manager? Ideally, it should be blank so that the DHCP server, I assume in the DSL modem, provides all the details. Please see attached.

---

### Post by exekutive on 2014-01-10
I have to reboot the computer every time I switch between Windows and Ubuntu. That is why the IP address is different every time I post some results.

As I said, the DHCP server in the modem is turned off. My dynamic IP's are obtained from the service provider's DHCP servers.

---

### Post by chili555 on 2014-01-10
> That is why the IP address is different every time I post some results.I can see it being 75.157.12.208 versus 75.157.12.212 or something similar, but changing to 154.5.220.92 is unreasonable. What is the answer here?> Do you have some settings applied in Network Manager? Ideally, it should be blank so that the DHCP server, I assume in the DSL modem, provides all the details.> As I said, the DHCP server in the modem is turned off. My dynamic IP's are obtained from the service provider's DHCP servers. I understand. However, the modem gets its IP address by DHCP from your ISP. The modem then hands that same address, *not* using DHCP,  to the Airport and then to the computer.

By the way, isn't it safer to configure the Airport to use a private IP address like 10.0.0.xx or 192.168.0.xx rather than use a public IP address from Telus?

---

### Post by exekutive on 2014-01-10
The different IP ranges are normal. It is a large ISP and they have many addresses. For example, the computer I am using to write this reply (same access point) has IP 64.180...

I have disabled private LAN because it is much simpler to manage and troubleshoot. I am not bothered by security.

---

### Post by chili555 on 2014-01-10
If you get *one* address from the ISP and it is passed through the Airport in bridge mode, I don't see how this is possible. Where is NAT performed?? 

Sorry.

---

### Post by exekutive on 2014-01-10
The ISP seems to provide as many IP addresses as are needed for all my computers to connect. This shouldn't be surprising, though, as this is how it was done when ISPs only gave out modems, before they started building routers into them. Perhaps there is no NAT, but if there was, it would be performed by the ISP.

---

### Post by chili555 on 2014-01-10
I'm sorry. I can be of no further assistance. I don't understand your setup nor why it's set that way. 

I see nothing here indicating that the USB dongle isn't operating correctly.

---

### Post by exekutive on 2014-01-10
The setup is a simple straight-through connection. It would be the same thing if I plugged a computer directly into a "dumb" modem.

I think you are correct that the dongle is working correctly, because it works on the same computer in a different operating system. Therefore the problem lies somewhere in Ubuntu.

If it would make it easier for you to help, I can configure the network any way you ask.

---

### Post by praseodym on 2014-01-11
Are you sure its v2? Lets check
```

lsusb
```

---

### Post by varunendra on 2014-01-11
Can we also see the outputs of -
```
route -n
sudo ufw status
```
..when you seem connected?

---

### Post by exekutive on 2014-01-14
Sorry for the delay.

@ praseodym
Yes, definitely V2
Bus 001 Device 004: ID 0bda:8179 Realtek Semiconductor Corp. 

```
joe@bigblackbox:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         154.5.220.1     0.0.0.0         UG    0      0        0 wlan0
154.5.220.0     0.0.0.0         255.255.252.0   U     9      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
joe@bigblackbox:~$ sudo ufw status
[sudo] password for joe: 
Status: inactive
joe@bigblackbox:~$ 

```

---

### Post by exekutive on 2014-01-18
I tried adding a dedicated route to my gateway host in case there was a routing problem ...
```
sudo route add <mygateway> wlan0
```
... but this did not help.

I am also providing my 'syslog' file, in case there's a problem in the background DHCP activity:
[http://pastebin.ubuntu.com/6775974/](http://pastebin.ubuntu.com/6775974/)

Unfortunately, there are no other open wifi networks available nearby to test. It's a beast of a computer, but I may have to try relocating it somewhere. However, internet via ethernet cable works just fine.

---

