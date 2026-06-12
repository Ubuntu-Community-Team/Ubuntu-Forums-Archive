---
title: "Ethernet port doesn't recognize cable"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by DianaRobledo on 2015-04-13
I am trying to connect my ethernet network but the port seems not to recognize that the cable is connected. The port's lights are not blinking at all. But the wifi works correctly.

After I tried lspci -nn|grep 0200
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)

also nm-tool:
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        F0E:F14:61:9E

Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Falone] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        40:25:C2:B9:71:0C

Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

Wireless Access Points (* = current AP)
    UILENZEIK:       Infra, 00:18:E742:53, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Marumaru:        Infra, 30:B5:C2:52:7B:C2, Freq 2447 MHz, Rate 54 Mb/s, Strength 74 WPA2
    Nein Nein Nein!!:Infra, F8:1A:67:F9:5D:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    stine:           Infra, B8:62:1F:51:3F:5A, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    WLAN-WoKo:       Infra, BC:05:43:B2:A5:43, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Vorsicht!:       Infra, 74:EA:3AE:41:94, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SMFNet:          Infra, BC:05:43:3B:CA:FF, Freq 2467 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *Falone:         Infra, 20:C90:B3:2F:E3, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA2
    kimi:            Infra, 28:2C:B2:66:71:12, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    WLAN-JNZ2X9:     Infra, E0:19:1D:26:50:31, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Vitamina:        Infra, E8:94:F6:78:97:74, Freq 2422 MHz, Rate 54 Mb/s, Strength 17 WPA2

  IPv4 Settings:
    Address:         192.168.2.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        64:D4:DA:6B:7E:02

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

and dmesg|grep eth:

[    0.598863] r8169 0000:03:00.0 eth0: RTL8168e/8111e at 0xffffc90000c7c000, f0:de:f1:d4:61:9e, XID 0c200000 IRQ 40
[    0.598866] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   21.438869] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.604480] r8169 0000:03:00.0 eth0: link down
[   32.604526] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.604869] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
diana@jannis:~$ lspci -nn|grep 0200
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)

---

### Post by 1clue on 2015-04-13
Probably you have a bad ethernet cable.

Second possibility, you have a crossover cable and your hardware does not support crossover, not very likely with newer equipment.

If you have a tester, then check connectivity across all the pins.  It should match to this:  [http://www.bb-elec.com/Images/EthernetRJ45B.aspx](http://www.bb-elec.com/Images/EthernetRJ45B.aspx)

You can google 'ethernet rj45 pinout' and get that and many other images.  It doesn't matter if the colors match exactly, but they must be the same on both ends of any cable.  Meaning you might have solid brown when the diagram says striped green, but the same pin must have the same color on both ends of the cable for a standard patch cable.

---

### Post by DianaRobledo on 2015-04-13
Sorry, I modified the results because I am not sure I copied them correctly. But actually I was using this cable before, this is happening after I came from holidays. I also tried my cable with my roomie's laptop and it recognized it correctly. I have a Lenovo V570.

---

### Post by chili555 on 2015-04-13
> [COLOR="#FF0000"]Nein Nein Nein!![/COLOR]:Infra, F8:1A:67:F9:5D:16, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2LOL!! Somebody has a great sense of humor.

Please turn the wireless off, open a terminal and do:```
sudo ethtool -s eth0 autoneg off speed 100
```Are the lights blinking? Does it connect? If so, we can make it persistent.

---

### Post by DianaRobledo on 2015-04-13
I tried and the light never turned on.

---

### Post by chili555 on 2015-04-13
Let's also see:```
dmesg | grep r8169
```This driver is always a bit tricky.

---

### Post by DianaRobledo on 2015-04-13
It gives:

[    0.594774] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.594784] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.595104] r8169 0000:03:00.0: irq 40 for MSI/MSI-X
[    0.595278] r8169 0000:03:00.0 eth0: RTL8168e/8111e at 0xffffc90000ce0000, f0:de:f1:d4:61:9e, XID 0c200000 IRQ 40
[    0.595280] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   33.361390] r8169 0000:03:00.0 eth0: link down
[ 1777.626726] r8169 0000:03:00.0 eth0: link down

---

### Post by chili555 on 2015-04-13
There is nothing remarkable there. The usual procedure is to compile the alternate r8168 driver. Before we proceed, please tell me your kernel version:```
uname -r
```I'll compile the driver myself as a proof before I write the process for you.

---

### Post by DianaRobledo on 2015-04-13
3.13.0-49-generic

---

### Post by chili555 on 2015-04-13
Please download the file from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false) You want this file: *LINUX driver for kernel 3.x and 2.6.x and 2.4.x* Select a mirror close to you. I picked US2.

Downloads usually go to the directory Downloads. Open it, find the r8168-xx compressed file, right-click it and select 'Extract Here.' Now open a terminal and, temporarily using wireless, do:```
sudo -i
apt-get update
apt-get install linux-headers-generic build-essential
cd /home/diana(or whatever your user name is)/Downloads/r8168-8.039.00
./autorun.sh
exit
```The process is a bit lengthy so please be patient.

After it finishes, check to see if r8168, the new one, or r8169, the old one, is loaded:```
lsmod | grep r816
```I believe the new driver module r8168 will be loaded. Turn off the wireless and tell me if it connects.

It may take a reboot.

---

### Post by DianaRobledo on 2015-04-13
It loaded r8168, but it is still not working. I did reboot it. No lights in the port, nothing :?

---

### Post by DianaRobledo on 2015-04-13
It loaded r8168, but it is still not working. I did reboot it. The lights of the port are not on either.

---

### Post by chili555 on 2015-04-13
Before we start to suspect hardware failure, let's have another look:```
dmesg | grep -e r816 -e 03:00
```Have you tried a different port on the router?

---

### Post by DianaRobledo on 2015-04-13
I got this:

[    0.158378] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.158447] pci 0000:03:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.158567] pci 0000:03:00.0: reg 0x18: [mem 0xd0404000-0xd0404fff 64bit pref]
[    0.158641] pci 0000:03:00.0: reg 0x20: [mem 0xd0400000-0xd0403fff 64bit pref]
[    0.158968] pci 0000:03:00.0: supports D1 D2
[    0.158970] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.159084] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.605237] r8168: module verification failed: signature and/or  required key missing - tainting kernel
[    0.605721] r8168 Gigabit Ethernet driver 8.039.00-NAPI loaded
[    0.605981] r8168 0000:03:00.0: irq 41 for MSI/MSI-X
[    0.607004] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    0.607012] r8168  Copyright (C) 2014  Realtek NIC software team <nicfae@realtek.com> 
[ 1839.549599] r8168 0000:03:00.0: no hotplug settings from platform

No, I live in an student residence and the only thing I have is a ethernet port attached to the wall. When I cnfigured it, I had to change it from DHCP to Manual and enter the internet data myself. it worked perfectly. I don't know what changed.

---

### Post by chili555 on 2015-04-13
>  I had to change it from DHCP to Manual In Network Manager? Are there any clues here?```
cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```Off for the evening; I'll check back later.

---

### Post by DianaRobledo on 2015-04-14
Got this:

Apr 14 03:48:04 jannis NetworkManager[1220]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 14 03:48:04 jannis NetworkManager[1220]: <error> [1429001284.642065] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 14 03:48:04 jannis NetworkManager[1220]: <warn> DNS: plugin dnsmasq update failed
Apr 14 03:48:04 jannis NetworkManager[1220]: <info> Writing DNS information to /sbin/resolvconf
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> (wlan0): roamed from BSSID 00:03:52:A6:4C:D3 (eduroam) to 00:03:52:A6:53:A3 (eduroam)
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Activation (wlan0) successful, device activated.
Apr 14 03:48:06 jannis NetworkManager[1220]: <warn> dnsmasq appeared on DBus: :1.88
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Writing DNS information to /sbin/resolvconf
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Activation (wlan0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> dhclient started with pid 2950
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> (wlan0): DHCPv6 state changed nbi -> renew6
Apr 14 03:48:06 jannis NetworkManager[1220]: <info>   nameserver '2001:4ca0::53:1'
Apr 14 03:48:06 jannis NetworkManager[1220]: <info>   nameserver '2001:4ca0::53:2'
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) scheduled...
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> (wlan0): DHCPv6 client pid 2950 exited with status 0
Apr 14 03:48:06 jannis NetworkManager[1220]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) started...
Apr 14 03:48:07 jannis NetworkManager[1220]: <info> Policy set 'eduroam' (wlan0) as default for IPv6 routing and DNS.
Apr 14 03:48:07 jannis NetworkManager[1220]: <info> Writing DNS information to /sbin/resolvconf
Apr 14 03:48:08 jannis NetworkManager[1220]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) complete.

---

### Post by chili555 on 2015-04-14
Wonderful. We got a perfect log showing the wireless connecting! Please turn off the wireless with the switch or key combination, reboot and run the command once again so that we, ideally, see only Network Manager and eth0.

---

### Post by DianaRobledo on 2015-04-14
Now:

Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (wlan0): bringing up device.
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (wlan0): deactivating device (reason 'managed') [2]
Apr 14 08:32:44 jannis NetworkManager[1185]: <warn> failed to allocate link cache: (-12) Object not found
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (eth0): carrier is OFF
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (eth0): new Ethernet device (driver: 'r8168' ifindex: 2)
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/2
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 14 08:32:44 jannis NetworkManager[1185]: <info> (eth0): bringing up device.
Apr 14 08:32:44 jannis kernel: [   32.973043] eth0: 0xffffc90000c7c000, f0:de:f1:d4:61:9e, IRQ 40
Apr 14 08:32:45 jannis NetworkManager[1185]: <info> (eth0): preparing device.
Apr 14 08:32:45 jannis NetworkManager[1185]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 14 08:32:45 jannis NetworkManager[1185]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 14 08:32:45 jannis NetworkManager[1185]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 14 08:32:45 jannis NetworkManager[1185]: <info> urfkill disappeared from the bus
Apr 14 08:32:45 jannis kernel: [   33.129151] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 14 08:32:45 jannis kernel: [   33.129418] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 14 08:32:45 jannis NetworkManager[1185]: <info> ModemManager available in the bus
Apr 14 08:32:53 jannis NetworkManager[1185]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.21': no such name
Apr 14 08:32:53 jannis NetworkManager[1185]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.21': no such name
Apr 14 08:32:54 jannis NetworkManager[1185]: <info> WiFi hardware radio set enabled

---

### Post by chili555 on 2015-04-14
>  <info> (eth0): deactivating device (reason 'managed') [2]Hello! 

When you set your static IP address, did you set it in Network Manager or in /etc/network/interfaces? If the latter, as I strongly suspect, there may be an error. May we please check it?```
cat /etc/network/interfaces
```If there are any secret passwords, etc. there, please disguise them: xxxxx or similar.

---

### Post by DianaRobledo on 2015-04-14
This is all I get:

auto lo
iface lo inet loopback

---

### Post by chili555 on 2015-04-14
Let's see:```
cat /etc/NetworkManager/NetworkManager.conf
```These commands may fail, but I'd love to know the error messages anyway. Please turn off the wireless and do:```
sudo ifconfig eth0 up
sudo dhclient eth0
```If it tries and repeatedly fails, which we expect, stop the sequence with Ctrl+c.

EDIT: Off for a few hours; back a bit later today.

---

### Post by DianaRobledo on 2015-04-14
With > cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=F0:DE:F1:D4:61:9E,

[ifupdown]
managed=false

With > sudo ifconfig eth0 up
nothing happened in the terminal.

And with 
> sudo dhclient eth0
it tried for some minutes but nothing happened. I didn't have to stop it.

---

### Post by michi1983 on 2015-04-14
Then post again the output of ```
sudo ifconfig
``` your eth0 might have drawn an IP address correctly from your DHCP server.

---

### Post by 1clue on 2015-04-14
I'm at a bit of a loss.  I have several of these cards, they always come up easily for me but they cause a lot of interrupts on the CPU so I've stopped buying them.  The tiny bit extra to get a decent Intel card is well worth it.  But I've never had to debug one of the realtek cards.

---

### Post by DianaRobledo on 2015-04-14
Something weird happened. When I came back from lunch I saw the lights and they were blinking correctly and the tramission icon in the bar appeared. But because I was trying to connect in a network that is not mine, I couldn't really connect to internet. So I changed to wifi to answer, but when I tried to go back to ethernet, the port was again off and I couldn't see the ethernet ico anymore (again). I came back home and plugged in my ethernet network cable. I tried to reboot the laptop, turned off the wifi and typed again the three codes "[COLOR=#000000][FONT=Ubuntu Mono]cat /etc/NetworkManager/NetworkManager.conf",[/FONT][/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo ifconfig eth0 up" and "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dhclient eth0". [/FONT][/COLOR]Now I am getting this error message only when running the last code:

 PING 10.153.175.254 (10.153.175.254) 56(84) bytes of data.

--- 10.153.175.254 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

I don't know what happened or what changed. When typing "[COLOR=#000000][FONT=Ubuntu Mono]sudo ifconfig" [/FONT][/COLOR]with the wifi off I get:

[sudo] password for diana: 
eth0      Link encap:Ethernet  direcciónHW f0:de:f1:d4:61:9e  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:40 Dirección base: 0xc000 

eth0:avahi Link encap:Ethernet  direcciónHW f0:de:f1:d4:61:9e  
          Direc. inet:169.254.10.215  Difus.:169.254.255.255  Másc:255.255.0.0
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Interrupción:40 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:5574 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5574 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:435368 (435.3 KB)  TX bytes:435368 (435.3 KB)

wmx0      Link encap:Ethernet  direcciónHW 64:d4:da:6b:7e:02  
          ACTIVO NOARP  MTU:1400  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:20 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2015-04-14
> eth0:avahi Link encap:Ethernet direcciónHW f0:de:f1:d4:61:9e
Direc. inet:[COLOR="#FF0000"]169.254.[/COLOR]10.215 Difus.:169.254.255.255 Másc:255.255.0.0
ACTIVO DIFUSIÓN MULTICAST MTU:1500 Métrica:1
Interrupción:40 Dirección base: 0xc000 This just means that the system asked for an IP address and one was not offered. A placeholder was written instead.

You said earlier:> When I cnfigured it, I had to change it from DHCP to Manual and enter the internet data myself. it worked perfectly. I assume you set it in Network Manager. We've already looked at /etc/network/interfaces and it isn't there.

I suspect there is something faulty with your static IP settings.  I suggest you check back with the University to confirm the proper settings and verify and correct Network manager as needed.

[ATTACH=CONFIG]261301[/ATTACH]

---

### Post by DianaRobledo on 2015-04-14
Well, I thought that maybe because one update might had done something to this, a new update might have had corrected it already. So I installed the newest update, rebooted the laptop and the connection worked perfectly. For half an hour I used it. After that, I unplugged it, but when I came back and plugged it again it didn't work anymore.

Yes, I used the Netwrok manager to configure the IP settings and they are correct, according to the form they gave me. And this same data were those that were working before I went on holidays.

I just tried typing [COLOR=#000000][FONT=Ubuntu Mono]sudo "ifconfig eth0 up" and "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dhclient eth0" t[/FONT][/COLOR]he connection works again. But I tried it before and didn't work.

---

### Post by chili555 on 2015-04-14
So, if you boot with the ethernet plugged in, it works?

---

### Post by DianaRobledo on 2015-04-14
Yes, exactly. I just tried it and I am still connected.

---

### Post by chili555 on 2015-04-14
> **DianaRobledo said:**
> Yes, exactly. I just tried it and I am still connected.Was the update by chance a newer linux-image? You were running:> 3.13.0-49-generic What are you running now?```
uname -r
```If you got a newer linux-image, also known as kernel version, and you didn't recompile, you are back to a now working r8169. Confirm:```
lsmod | grep r816
```Maybe it healed itself!

---

### Post by DianaRobledo on 2015-04-14
Still running 3.13.0-49-generic

And i got:
r8168                 434402  0 
r8169                  67581  0 
mii                    13934  1 r8169

But I don't know wtf is happening. The ethernet connection is gone again and I didn't unplugg it or turned it off.

---

### Post by chili555 on 2015-04-14
Let's blacklist r8169:```
sudo -i
echo "blacklist r8169"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r r8169
exit
```It may take a reboot for the change to take effect.

---

### Post by DianaRobledo on 2015-04-14
I did it and it showed:

r8168                 434402  0 

But when I rebooted, it showed me again:

r8168                 434402  0 
r8169                  67581  0 
mii                    13934  1 r8169

So I had to blacklist it again. Ethernet still not working.

---

