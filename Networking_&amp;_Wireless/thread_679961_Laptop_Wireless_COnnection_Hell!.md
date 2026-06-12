---
title: "Laptop Wireless COnnection Hell!"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by MoJoMoGo on 2008-01-27
I have come to the end of my brain capacity... Hopefully someone will be able to help! Thanks in advance!!

- **OS:** Ubuntu 7.10 - I-386

**- Laptop:** Compaq C717NR (C700 Family)

**- Router:** D-Link WBR1310 Rev.B1 - WEP - 64-Bit ASCII Key

**- lpsci output (Relevant):**
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

**- iwconfig output:**
lo no wireless extensions.
eth0 no wireless extensions.
eth1 IEEE 802.11b/g ESSID:ff/any Nickname:"Broadcom 4311"
Mode:Managed Frequency=2.472 GHz Access Point: Invalid
Bit Rate=1 Mb/s Tx-Power=18 dBm
RTS thr: off Fragment thr: off
Encryption key: off
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

**- ifconfig output:**
eth0 Link encap:Ethernet HWaddr 00:1B:38:83:5E:22
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:21 Base address:0xa000

eth1 Link encap:Ethernet HWaddr 00:00:00:1A:73:A7
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:993 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:43458 (42.4 KB)
Interrupt:11 Base address:0x8000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

The laptop has a small button that (normally) enables/disables the wifi. When enabled, the light is blue. Disabled, amber.

**This is what I have tried so far:**

1 - Installed package bcm43xx-fwcutter
2 - Enabled restricted driver (Firmware for Broadcom 43xx chipset family)
3 - Directed the driver to wl_apsta-3.130.20.0.o (downloaded from the bcm43xx development site)

- - Now the restricted driver manager shows that particular driver (Firmware for Broadcom 43xx chipset family) in use.
- - The button is now functional.
- - No wireless networks are visible via the taskbar applet (nm-applet 0.6.5). Another computer (running Win XP) shows mine and 2 other neighbor's networks (I am about 15 feet away from my router).

4 - Tried the taskbar applet "CONNECT TO ANOTHER NETWORK" option and entered all the relevant information (SSID, Security protocol and Security key).
4.1 - The applet displays the "trying to connect" animation and I keep getting a "Network Password Requested" window. I have entered all the different keys, under all the different protocols available to no avail. The same mesage keeps popping up.

This is about the nth installation attempt. I have tried installing SUSE 10.3, Sabayon and Linux Mint. I tried to follow instruction for ndiswrapper on each of those distros, but never even got past the visual display of the WiFi button on the computer.
I cannot remember what I tried before (too many steps to recall), but the steps outlined above were just performed, hence my posting here (Ubuntu seems to be the best, most user friendly distro so far).

Thank you any and all for your input!!

Mojo

---

### Post by Mikecore on 2008-01-28
sometimes wireless can be a pain.

try this I see that your wireless card is there from your iwconfig command. it is called eth1
so it probably mean your driver is loaded. So let try to manually configure your wireless card. disable wep/wap ( router ) for now till we get it talking first then will worry about security.

```

sudo ifconfig eth1 down ( bring it down first )
sudo iwconfig eth1 essid 'your essid here' *do not use the quoations.
sudo iwcondfig eth1 channel 'your wireless channel'
sudo ifconfig eth1 up
sudo dhclient eth1

```

it should get an ip from your router. if it does great try rebooting and see if it will come up on it own now.

---

### Post by SunnyDaze on 2008-01-28
Thje first thing that caught my attention is you have a BCM94311 chipset.  Does that qualify as a BCM43xx or as a BCM943xx?

I have a Broadcom BCM4306 chipset on my wireless cards.  My biggest problem in getting ndiswrapper working was that it wouldn't work at all until I disabled the bcm43xx module that was started at boot.  They appeared to be interfering with each other.

Here's what I have done:

First of all know that the BCM43xx driver that comes with Ubuntu DOES NOT work with my card and it had to be disabled.  You can do this by typing in **sudo modprobe -r bcm43xx** every time you log in, or you can have it disabled at boot automatically by adding **bcm43xx** to the **/etc/modprobe.d/blacklist** file.

Also, disable ndiswrapper for now by typing in **sudo modprobe -r ndiswrapper**

You might also have to uninstall the ndiswrapper version that comes with Ubuntu and install a more current version from another source.  I had to do this in Gutsy, and I can't remember if I had to in Feisty.

Here's a list of my steps, If you need even more detail, let me know:

1.  Disable bcm43xx and ndiswrapper  (see above)
2.  Blacklist bcm43xx in /etc/modprobe.d/blacklist
3.  Download and install latest ndiswrapper-common and ndiswrapper-utils from ndiswrapper website, NOT from Ubuntu
4.  Setup ndiswrapper according to their instructions
5.  Add ndiswrapper to /etc/modules
6.  Reboot  (I do this to make sure the modules are disable and enable correctly after boot)

---

### Post by gdselzer on 2008-01-28
I have the same wireless card in my laptop.  The bcm43xx module does not work with rev 02 of this card.  You must use ndiswrapper.  SunnyDaze's suggestion aside, the ndiswrapper packaged with Gutsy worked just fine for me.  Use the instructions at this site:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It says Feisty, but worked great for me in Gutsy.  You want step 2a.

Good luck!

---

