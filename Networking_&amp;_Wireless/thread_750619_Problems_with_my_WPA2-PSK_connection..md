---
title: "Problems with my WPA2-PSK connection."
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Astronaut on 2008-04-09
Hi There, i'm looking for help here since I'm desperate with my network configuration.
First of all, hello to everyone, hope you're all doing fine. I'm writing from Chile, but it happens that forums over there didn't took me too seriously.

Ok then, It happens that recently I installed a wifi connection in my house. There are 2 pcs in the house. My mother's, running Win XP, and mine with Win XP and Ubuntu 7.04. I used to have both computers connected in a wired network, sharing internet and files. When I bought the wifi router, I installed it in my mother's pc and I installed a wireless PCI Card in my PC. Internet works perfectly in both PCs under Windows, but now my Ubuntu doesn't want to connect to anything. I'm using a WPA2-PSK Encryption.

I looked over google and it says that I needed wpa_supplicant, wpa_gui and network-manager gnome. I installed all of them and when I run wpa_gui there's a message "Could not get status from WPA_SUPPLICANT" and I cannot connect to any network available.

The router is a D-Link DIR-300 and my wireless card is a D-Link G DWA-510.

**Here is my lspci:**

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c3
01:00.1 Audio device: ATI Technologies Inc Unknown device aa10
02:00.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169SC Gigabit Ethernet (rev 10)
[B]
my IWCONFIG:[/B]

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**My /etc/network/interfaces:**

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface ra0 inet static
address 192.168.0.102
netmask 255.255.255.0
wireless-essid Herrera Gonzalez Net
wireless-key herrerag1640
gateway 192.168.0.1

And finaly my **ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:19:DB:B7:92:C3  
          ARRIBA BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupción:20 Base address:0xec00 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4406 (4.3 KiB)  TX bytes:4406 (4.3 KiB)

ra0       Link encap:Ethernet  HWaddr 00:1B:11:C8:A1:72  
          inet dirección:192.168.5.234  Bcast:192.168.5.255  Máscara:255.255.255.0
          dirección inet6: fe80::21b:11ff:fec8:a172/64 Alcance:Vínculo
          ARRIBA BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:595085 (581.1 KiB)  TX bytes:0 (0.0 b)
          Interrupción:16 

That's all. Am I lost? Anyway Thanks in advance. I'd love some help.

---

### Post by ibutho on 2008-04-09
Hi. Some wireless drivers have poor WPA support or don't support it at all. Try switching to WEP and see if that helps. The reason I mention this is because I have a ralink rt73 (rt2573) card that won't play along nicely with WPA but works perfectly with WEP.

---

### Post by Astronaut on 2008-04-09
> **ibutho said:**
> Hi. Some wireless drivers have poor WPA support or don't support it at all. Try switching to WEP and see if that helps. The reason I mention this is because I have a ralink rt73 (rt2573) card that won't play along nicely with WPA but works perfectly with WEP.

Well I don't want to change to WEP due to security issues. I've read somewhere that ralink drivers shows lost of problems too. But there must be a way. Am I doomed?

---

### Post by ibutho on 2008-04-10
If you are not willing to use WEP, then you probably have to use your Windows drivers with ndiswrapper or look for a natively supported card that works with WPA (can't be specific here because all cards I have are ralink based).

---

### Post by Astronaut on 2008-04-15
Thanks! I'll try...

---

### Post by Astronaut on 2008-04-15
I solved it!!! with a very strange solution however. I installed the drivers with ndiswrapper like you told me, then I went to the console and initialized the driver:

sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf

the result is a lot of diagnostic errors like:

CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
ioctl[SIOCSIWENCODEEXT]: No such file or directory
No network configuration found for the current AP
WPA: No SSID info found (msg 1 of 4).

...etc

However, when I connect manually through the mn-applet icon in the upper right corner of the desktop with the console running wpa_supplicant (with the bad diagnostic and everything), wpa_supplicant now shows:

WPA: Could not verify EAPOL-Key MIC - dropping packet

And wow! Internet works! Thanks!!

---

