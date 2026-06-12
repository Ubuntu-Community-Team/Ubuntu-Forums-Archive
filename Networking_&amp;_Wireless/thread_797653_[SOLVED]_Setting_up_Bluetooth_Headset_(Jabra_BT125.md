---
title: "[SOLVED] Setting up Bluetooth Headset (Jabra BT125)"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by slackerwarenative on 2008-05-17
Hi.
I need help setting up a Bluetooth headset, since I have never done it before.

My hardware is:
Kensington USB Bluetooth 2.0 adapter
[http://us.kensington.com/html/9403.html]("http://us.kensington.com/html/9403.html")

Jabra BT125 Headset
[http://www.jabra.com/Sites/Jabra/NA-US/products/Pages/JabraBT125Black.aspx]("http://www.jabra.com/Sites/Jabra/NA-US/products/Pages/JabraBT125Black.aspx")

I am running:
Ubuntu 7.10 (gutsy)
Kernel Linux 2.6.22-14-generic
GNOME 2.20.1
Compiled all for x86, since this box is a 32bit x86 (P4 cpu)

Bluez-utils are install and all that. When I plug in the USB adapter, my computer instantly recognizes it and the daemons are enabled. I see the Bluetooth symbol at the top, and it detects some local bluetooth devices. I understand I need to pair the headset and computer, and when I try to connect it says:
> "obex://[00:11:22:33:44:55]" is not a valid location.

I checked in terminal to make sure the USB adapter is working, and it is:

```

$ sudo hciconfig hci0 revision
hci0:   Type: USB
        BD Address: 00:11:22:33:44:55 ACL MTU: 1017:8 SCO MTU: 64:0
        Firmware 0.67 / 14

```
Then I scanned for the headset.
```
$ hcitool scan
Scanning ...
        00:11:22:33:44:55       Jabra BT125
```

Which was found.

How do I set this up? I just want to use it for VoIP, such as skype.

Thank your for you help.

---

### Post by slackerwarenative on 2008-05-18
This thread may be closed. Problem was solved, and my headset now works. For others to use as a reference, this is what I did:


To know what the address of the headset is, type:
```
sudo hitool scan
```

It should say something like:

```
00:00:00:00:00:00 DeviceName
```
Use the 00:00:00:00:00:00 where I say "[whatever the scan said of a MAC]".

I changed the configuration files. To start, add your device to:
```
gksu gedit /etc/bluetooth/rfcomm.conf
```
then type something like:
```
#
# RFCOMM configuration file.
#

rfcomm0 {
#	# Automatically bind the device at startup
	bind no;
#
#	# Bluetooth address of the device
	device [whatever the scan said of a MAC];
#
#	# RFCOMM channel for the connection
	channel	1;
#
#	# Description of the connection
	comment "Blutooth Headset device";
}
```

Depending on your computers settings, you may have to change other settings.

Make sure that your Bluetooth headset is in Pairing Mode. This must be done every time the computer is rebooted. I wrote a BASH script, which I execute when I need to Pair the headset. This should be done in a terminal that can stay open, since btsco must remain open during the entire time you use the headset. Therefore, you might want to run it as a background process.

```
sudo modprobe snd-bt-sco
sudo hcitool cc [whatever the scan said of a MAC]
sudo btsco -v [whatever the scan said of a MAC]
```

If the connection to the Channel is lost (it will say if you did - usually because of distance or power loss), then you must restart the bluetooth stack like so:
```
sudo /etc/init.d/bluetooth restart
```

To test the headset I used Audacious. When that worked, I used it on skype (non-opensource VoIP), which worked great. BT125 does run loud, so you might also want to lower the volume on the headset.

I hope this helps those who need it. Cheers.


Someone might want to make this or an edited version of this a STICKY, so others can see it.

---

### Post by meoblast001 on 2009-03-19
I tried that and I get
```
speaker volume: 13 mic volume: 13
i/o needed: connecting sco...
Can't connect SCO audio channel
: Address already in use
speaker volume: 13 mic volume: 13
```
when I start Skype.

---

### Post by mcdavey on 2009-04-04
I have a Jabra BT125, and could not get it to work with Hardy 8.04.
When running "bt-sco -v [mac address]" the sco module
complained "Error: btsco open (1-0): No such device or address"

Then I came across bug #222922, and tried downgrading to kernel 2.6.22.
My headset now works flawlessly.

I'm pretty staggered that support for plain old SCO headsets broke in 2.6.24 and is still broken (apparently) in current 2.6.28.

---

