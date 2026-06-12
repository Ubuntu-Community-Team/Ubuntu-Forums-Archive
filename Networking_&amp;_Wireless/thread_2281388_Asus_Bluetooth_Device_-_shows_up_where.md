---
title: "Asus Bluetooth Device - shows up where?"
date: 2015-06-06
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2015-06-06
lsusb:

```
Bus 001 Device 009: ID 0b05:17cb ASUSTek Computer, Inc.
```

Under System Settings / Sound /  Output / Play Sound Through

there is no Asus or Bluetooth device showing (see attached screenshot for clarity).

Is this where I would see a bluetooth device? The various (I'm confused about some of this) Panel mgrs, e.g. - Blueman applet 1.23 and Bluetooth Manager and a third in the upper panel with no name. for BT devices show the Asus and I've named it after this 'puter: Lexington-0 (zero).

I can received files (pix) from my Android phone just fine. What I cannot do is set the usb-400bt to network with a Belkin SongStream. The belkin is a bluetooth receiver, only. It's sole function is to receive music and pass it to a 3.5mm plug. 

The usb-bt400 connects (or so it says), but cannot stream. Where would I look for a Ubuntu 14.04 LTS driver for the usb-400bt device? I've been at the 'net for 2 hours now and am lost and confused. Linux-drivers.org shows nothing for the usb-400bt, but it is obviously working somewhat. The "Local Services" function of the un-named panel applet, greys out before I can even enter my password.

This is Trusty Tahr ver. 14.04 LTS

---

### Post by Aidan_St.Louis on 2015-06-06
What is the bluetooth device

---

### Post by Mark_in_Hollywood on 2015-06-06
The usb-bt400 connects (or so it says), but cannot stream. As per my OP

---

### Post by jeremy31 on 2015-06-07
You might just need the firmware to get the audio to stream, but I don't know exactly what it expects the name to be
```
dmesg | grep -i bluetooth; dmesg | grep firmware
```
That should reveal what it needs to be named

There is also a chance that you don't have the correct module loaded so you could try```
sudo pactl load-module module-bluetooth-discover
```
You will either see a number returned in terminal or possibly an error message, the error could be that it was already loaded
Then delete the device from the paired/trusted list and then add it again

---

### Post by Mark_in_Hollywood on 2015-06-09
It is difficult for me to believe that "Core ver 2.17" is the name . But this is what was returned in the terminal:

```
mark@Lexington:~$ dmesg | grep -i bluetooth; dmesg | grep firmware

[   12.753746] Bluetooth: Core ver 2.17
[   12.753779] Bluetooth: HCI device and connection manager initialized
[   12.753795] Bluetooth: HCI socket layer initialized
[   12.753797] Bluetooth: L2CAP socket layer initialized
[   12.753801] Bluetooth: SCO socket layer initialized
[   14.565110] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.565116] Bluetooth: BNEP filters: protocol multicast
[   14.565127] Bluetooth: BNEP socket layer initialized
[   14.570365] Bluetooth: RFCOMM TTY layer initialized
[   14.570382] Bluetooth: RFCOMM socket layer initialized
[   14.570391] Bluetooth: RFCOMM ver 1.11


mark@Lexington:~$ sudo pactl load-module module-bluetooth-discover
[sudo] password for mark: 
25

```

---

### Post by jeremy31 on 2015-06-09
Now delete the pairing with the audio device and add it again and see if it appears in Sound Settings, depending on blueman version, you may have to use the pactl load-module module-bluetooth-discover command after every restart

---

### Post by Mark_in_Hollywood on 2015-06-11
For other readers of this post: 

IT IS NOT: pactl load-modules module-bluetooth-discover

but it IS:

pactl load-module module-bluetooth-discover

Thanks, jeremy31 and to all who read this with or without comment/reply.

---

