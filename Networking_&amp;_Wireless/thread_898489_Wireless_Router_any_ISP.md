---
title: "Wireless Router any ISP"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Golden Blunder on 2008-08-23
At the moment I connect through my mobile phone and bluetooth (very easy but slow) and would like to connect via phone line and wireless router.Can I  use the  ISPs router or do I need my own ? Any advice welcome

---

### Post by Golden Blunder on 2008-08-23
At the moment I connect through my mobile phone and bluetooth (very easy but slow) and would like to connect via phone line and wireless router.Can I  use the  ISPs router or do I need my own ? Any advice welcome

---

### Post by karlw on 2008-08-23
You question is a little vague.  Maybe be you've posted someplace before, but what exactly are you using to get online?  Is it a PC?  If this is correct and the device have a wireless network interface, then you can use this to get to the internet.  I can only assume that if you PC has Bluetooth is has wireless card.  If your ISP provided you with a router, then you should be all set.  There are tons of tutorials out there for getting Ubuntu online ([here]("http://www.linux.com/feature/56946")).  



My question is, how did you bridge your cell phone to get online, but didn't try to use your wireless router, seems like your running before you can crawl.

---

### Post by Golden Blunder on 2008-08-23
I use a old Tiny pc Here is my setup 
	#Bluetooth Setup
gedit /etc/bluetooth/hcid.conf

#pin_helper /usr/bin/bluez-pin;
        pin_helper /usr/bin/bluepin;

	#Ubuntu 7.10 (from here).

gedit /etc/bluetooth/rfcomm.conf

rfcomm0 {
        bind yes;
        device 00:12:D2:65:0E:6E;
        channel 1;
        comment "BluetoothDialup";
}
gedit /etc/chatscripts/BluetoothDialup

TIMEOUT         15
ECHO            ON
HANGUP          ON
''              AT
OK              ATZ
OK              ATD*99#

gedit /etc/ppp/peers/BluetoothDialup

debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"
usepeerdns
/dev/rfcomm0 115200
defaultroute
crtscts
lcp-echo-failure 65535

/etc/init.d/bluez-utils restart
pon BluetoothDialup

Find your mac address with hcitool scan
Put two icons in usr/share/pixmaps called stop and go as root,set up on desktop as launchers with command pon Blutooth Dialup/poff Bluetooth Dialup and place on panel .Works with all Versions of Ubuntu

---

