---
title: "SMC USB Wireless with Ethernet already running"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by mdavidjohnson on 2011-02-26
I have my internal network running over wired ethernet and my external connection to the internet running through a wireless router. My Windows machines are all working properly with this.

I have my newly set-up Ubuntu 10.04 properly connected to the internal ethernet network and able to access my Windows 2003 Servers and my Windows XP and 7 Pro Workstations correctly.

But it will not recognize my SMC2862W-G USB wireless connection (which works properly on my Windows XP laptop).

After investigating various threads on this forum, I installed ndisgtk and its dependencies (ndiswrapper-common and ndiswrapper-utils-1.9) and tried to install the SMC Windows driver from its Install CD. The first try reported "Error while installing". The second try reported "Driver already installed". But there was no driver listed when I tried to do a "Remove".

System|Administration|Network Tools only shows the loopback lo and the ethernet eth0; no wireless, no ath0.

iwconfig shows lo = no wireless extensions, eth0 = no wireless extensions, and ath0 = no such device.

Any suggestions?

---

### Post by josephmills on 2011-02-26
> **mdavidjohnson said:**
> I have my internal network running over wired ethernet and my external connection to the internet running through a wireless router. My Windows machines are all working properly with this.

I have my newly set-up Ubuntu 10.04 properly connected to the internal ethernet network and able to access my Windows 2003 Servers and my Windows XP and 7 Pro Workstations correctly.

But it will not recognize my SMC2862W-G USB wireless connection (which works properly on my Windows XP laptop).

After investigating various threads on this forum, I installed ndisgtk and its dependencies (ndiswrapper-common and ndiswrapper-utils-1.9) and tried to install the SMC Windows driver from its Install CD. The first try reported "Error while installing". The second try reported "Driver already installed". But there was no driver listed when I tried to do a "Remove".

System|Administration|Network Tools only shows the loopback lo and the ethernet eth0; no wireless, no ath0.

iwconfig shows lo = no wireless extensions, eth0 = no wireless extensions, and ath0 = no such device.

Any suggestions?

ok so I know that this may sound silly but did you try to pull the ethernet cable out and put it back in well ubuntu was running? also try to post this in your terminal  ifconfig  copy and past that to us and also lspci  make sure that everything that you want to work is plugged in.

---

### Post by wep940 on 2011-02-26
It's a USB device that according to what I have found on the net so far does not look very promising to get working.  I am curious - when you tried ndiswrapper via ndisgtk (a smart move, by the way - it's way easier), did you point it to the .inf file for your driver?  Was the .sys and any other files associated with your driver in the same directory/folder?  And remember the architechure must match - if you are using 32-bit Ubuntu, you *MUST* use 32-bit Windows XP (only!) drivers, if you are using 64-bit Ubuntu, you *MUST* use 64-bit Windows XP (only!) drivers.
 
If you search the web with ubuntu SMC2862W-G USB you'll see others have also had problems with this device even when just using the Windows drivers and ndiswrapper.

---

### Post by mdavidjohnson on 2011-03-04
I've experimented some more with no success.

I installed ubuntu 10.04 (Lucid Lynx) on an old Pentium D with 384 MB RAM and 10 GB HDD. It's a direct boot to ubuntu - no other OS is on the machine.

I can't get my SMC EZ Connect g 802.11g Wireless USB 2.0 Adapter to work on it.

I run a wired network for communication between servers and workstations (Windows Server 2003, Windows XP Pro, and Windows 7 Pro up til now). For those workstations which I want to allow external access to the internet, I run wireless through my Comcast provided wireless router.

The wired internal network connection is working fine with ubuntu and samba.

I have double-checked the SMC wireless adapter in my older HP Windows XP Pro laptop and it's working correctly there.

I used the CD that came with the SMC and installed the driver to ndiswrapper on ubuntu.

sudo lshw -C network gives:
description: Wireless Interface
physical id: 1
logical name: wlan0
serial: (the hardware address, i.e. in form "xx xx xx xx xx xx")
capabilities: ethernet physical wireless
configuration\ broadcast=yes driver=ndiswrapper+smc2862w driver version=1.55+smc, 10/14/2004, 3.0.22.1 link=no multicast=yes wireless=IEEE 802.11g

iwlist scan gives:
Cell 01 - Address: (my access point address in form "xx xx xx xx xx xx")
essid: (my access point name)
protoco\: IEEE 802.11g
mode: managed
frequency: 2.412 GHz (Channel 1)
encryption key: on
extra: bcn_int=100
extra: atim=1

I then did:
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
	listening on LPF/wlan0/(the hardware address, i.e. in form "xx xx xx xx xx xx")
	sending on LPF/wlan0/(the hardware address, i.e. in form "xx xx xx xx xx xx")
	sending on Socket/Fallback
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "(my access point name)"
sudo iwconfig wlan0 key (my wep key)
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 channel 1
sudo dhclient wlan0
	listening on LPF/wlan0/(the hardware address, i.e. in form "xx xx xx xx xx xx")
	sending on LPF/wlan0/(the hardware address, i.e. in form "xx xx xx xx xx xx")
	sending on Socket/Fallback
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
	DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
	No DHCPOFFERS received
	No working leases in persistent database - sleeping
	
ping -c 4 google.com
	ping: unknown host google.com
ping -c 4 74.125.225.17
	... 100% packet loss
	
I added the following to /etc/network/interfaces\:
# The SMC Thumb usb Wireless Interface
auto wlan0
iface wlan0 inet dhcp
wireless-essid (my access point name)
wireless-key (my wep key)
wireless-channel 1
wireless-mode managed

ping -c 4 google.com
	ping: unknown host google.com
ping -c 4 74.125.225.17
	... 100% packet loss
	
nm-tool gives for wlan0:
Type: 802.11 WiFi
Driver: ndiswrapper
State: disconnected
Default: no
HW Address: (the address, i.e. in form "xx xx xx xx xx xx")
capabilities: wep encryption - yes, wpa encryption - yes
wireless access points:
(my access point name): Infra, (my access point address in form "xx xx xx xx xx xx"), Freq. 2412 MHz, Rate 54 Mb/s, Strength 81 wep
(another nearby access point): Infra, (access point address in form "xx xx xx xx xx xx"), Freq. 2437 MHz, Rate 54 Mb/s, Strength 17 wpa

I tried sudo iwconfig wlan0 essid (my access point name) ap (my access point address) key (my wep key) mode managed commit

nm-tool still reports State: disconnected

sudo invoke-re.d networking restart --> ... - sleeping
sudo dhclient wlan0 --> ... - sleeping
nm-tool --> State: disconnected

ping -c 4 google.com
	ping: unknown host google.com
ping -c 4 74.125.225.17
	... 100% packet loss
	
So am I just going to have to buy some other wireless usb device instead of the SMC?

Or is there some other solution you might recommend?

---

