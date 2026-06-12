---
title: "bluetooth pairing failed"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by rubing on 2008-08-24
Hi all,

I am using xubuntu 8.04 Hardy with fluxbox window manager and tyring to connect via bluetooth iogear GBU221 usb dongle to my Samsung Sprint phone.


1st I enter hcitool -s
2nd I enter hcitool cc 'my phones address'

there are no error messages, but if I then try hcitool auth, it says i am not connected.  this is confirmed by hcitool con

I have the pincode defined in hcid.conf as well as in a pin file residing in a directory with the phones name in /etc/bluetooth

---

### Post by Golden Blunder on 2008-08-24
This should help ,just adjust for your own dial number and mac.Find your mac with hcitool scan.
	#Bluetooth Setup
gedit /etc/bluetooth/hcid.conf

#pin_helper /usr/bin/bluez-pin;
        pin_helper /usr/bin/bluepin;

	#Ubuntu 7.10 (from here).-----YOU START HERE!

gedit /etc/bluetooth/rfcomm.conf

rfcomm0 {
        bind yes;
        device 00:12:D2:65:0E:6E;-------CHANGE THIS
        channel 1;
        comment "BluetoothDialup";
}
gedit /etc/chatscripts/BluetoothDialup

TIMEOUT         15
ECHO            ON
HANGUP          ON
''              AT
OK              ATZ
OK              ATD*99# ----------AND THIS

gedit /etc/ppp/peers/BluetoothDialup

debug
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/BluetoothDialup"
usepeerdns
/dev/rfcomm0 115200
defaultroute
crtscts
lcp-echo-failure 65535

Reeboot to start everthing !

Open a terminal as root and create all these files then open nautilus stillas root and paste two icons called stop and go in usr/share/pixmaps.
Put these as launchers on the desktop with commands pon BluetoothDialup and poff BluetoothDialup.now connect to the web with your phone browser and click GO ,the phone will ask for accept code ,give it one then do the
same when the pc asks .Sorted from now on just connect your phone and press GO.
IF you don't Know Your dialup  post me.

---

### Post by Crafty Kisses on 2008-08-25
At the bottom of this page Troubleshooting

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by rubing on 2008-08-28
Golden Blunder, thanks so much for the help!!


I have some questions regarding the advice/instructions you gave me.  

1.
Should I add the following lines to the options section (there is also a device section) of the /etc/bluetooth/hcid.conf file?
```

#pin_helper /usr/bin/bluez-pin;
pin_helper /usr/bin/bluepin;

```

Should I also create this file?  should i put anything in it?

2.  
In rfcomm.conf I assume the mac address is for the phone i am trying to connect to?  Also, I don't know what the dial number...what to put here:
```

OK ATD*99# ----------AND THIS
```

3.  

I am using fluxbox window manager and cannot create launcher icons.  I guess I can just type pon BluetoothDialup and poff BluetoothDialup.now at the command line?


Thanks again for the help! :)

---

