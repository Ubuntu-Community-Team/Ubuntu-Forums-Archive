---
title: "Wireless working, how to start it on boot?"
date: 2005-07-15
forum: Networking &amp; Wireless
---

### Post by sd5867 on 2005-07-15
Ok, first let me say that I am not running ubuntu, I am running Debian 3.1 (Sarge).  I have tried 4 other forums to try to get this answer, but I am having no luck.  I am a linux novice, and can get around a system enough, however I am self taught and probably don't know everything that I should know. So, here's the problem.  I have my wireless card working, however I have to go Root and start it everytime I start the computer. This is how I start it:

Login Root
Ifconfig wlan0 up
iwconfig wlan0 essid "Router SSID"
dhcpcd wlan0

and the wireless is working.
What I am trying to figure out, is how do I get the system to automatically start up the wireless card on startup.
Where do I store the SSID, so it automatically used it by default? and...
How to set up automatic DHCP address retrieval.

Thank You.

---

### Post by TheOtherShoe on 2005-07-15
If you can get gnome-system-tools it makes things pretty easy. That is what I use along with netapplet and it connects to a wireless network when Gnome starts up.

Using the boot scripts for activating a wireless card is trickier because the network initialization script runs before PCMCIA services are started, which most wireless cards require.

---

### Post by spd106 on 2005-07-15
Hi, you might try looking in the /et/networking/interfaces file. I think this is where the network configuration settings are stored.  You should have an auto line plus a stanza for each network interface like this

```

auto eth0

iface eth0 inet dhcp
wireless-key xxxxxxxxxx
wireless-essid your_essid

```

Different distros have other methods. In xandros it only has the first line and the encryption key is strored elsewhere. It's usually best to use whatever gui tool is installed as default.

Also if you using ndiswrapper make sure the kernel module is loaded during startup. ie ndiswrapper -m.

Good luck

---

### Post by gruepig on 2005-07-15
Edit the file /etc/network/interfaces to contain one of the following (in addition to whatever it has for lo and other interfaces):

auto wlan0
iface wlan0 inet dhcp
wireless-essid "Router SSID"

- or -

auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 essid "Router SSID"

The auto line specifies that the interface should be brought up on boot, the next line says to use dhcp, and the third line says to set to SSID.  The difference between the two examples is that the first works because there are specific hooks between wireless-tools (iwconfig) and interfaces (ifup), whereas the second is the more general way to execute arbitrary commands before bringing up an interface.

Test by running 'ifdown wlan0' to bring the interface down and 'iwup wlan0' to bring it back up.  If that works, reboot.

---

### Post by b4k4 on 2005-08-02
My interfaces contains this:

> iface eth1 inet dhcp
wireless-essid HIS
wireless-key s:*keyhere*
auto eth1

However, when I boot up and login, the connection is not up. I have to go into system/admin/networking to get it to work (or use a terminal)

---

### Post by kleeman on 2005-08-02
First checkout what went wrong on the boot with
dmesg | grep eth1

---

### Post by andyjenkins on 2005-08-03
Nearly all linux distributions come with a "miscellaneous" startup file where simple stuff that doesn't fit anywhere else is put.  On Debian, this is in /etc/init.d/bootmisc.sh.  You could edit that file as root, and append your wireless networking commands to the end.  This is not an elegant solution, kinda like duct tape, but it'll work.

---

