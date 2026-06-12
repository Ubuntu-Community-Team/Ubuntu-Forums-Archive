---
title: "solved: bluetooth pairing problem in edgy"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by jts88 on 2007-04-07
I read a lot of threads about people having trouble getting edgy to pair with bluetooth devices, some with solutions but none of them seemed to work with the onboard bluetooth on my laptop, and my motorola v550 phone. The problem was that whenever i tried to use the OBEX file transfer utility on the phone, the computer would try to pair with the phone, but any pin i entered on the phone would be immediately rejected. The way i solved it was as follows:

Firstly i had already installed these packages:
bluetooth
kdebluetooth
bluez-utils

I kept /etc/bluetooth/hcid.conf to the default settings.

I started kbluetoothd from the command line, waited till the icon appeared in the taskbar. I then put the phone in discoverable mode, and used 'hcitool scan' to find out it's address. Once it was started, i opened a terminal, and ran this command:

passkey-agent /usr/bin/bluez-pin <phone's hardware address here>

I left it running in the terminal, then opened konqueror by clicking on the kbluetoothd icon. I clicked on the phone's icon, then the OBEX File transfer icon from the list that came up. The phone then came up with a message asking me if i wanted to bond with the laptop. I entered the standard pin (this is where it usually failed) but it waited and then the bluez-pin window opened on the laptop and it paired successfully when i entered the same code. I'm not sure this is the right way to do it or if i've missed anything important out, but having spent ages failing to get the devices to pair i thought i should post my solution.

---

### Post by Mike_Longbow on 2007-04-22
Man, you rock.
This helped me a lot with my SE k700. :)

---

### Post by volkswagner on 2007-07-10
I cannot connect my nokia 6126 via bluetooth with my msi starkey usb device, known as broadcom.  I can scan on laptop and get my id of phone.  I can scan on my phone and see my laptop.  if i just try and pair on the phone i get rejected after entering the "1234"

when i follow 

> 
I started kbluetoothd from the command line, waited till the icon appeared in the taskbar. I then put the phone in discoverable mode, and used 'hcitool scan' to find out it's address. Once it was started, i opened a terminal, and ran this command:

passkey-agent /usr/bin/bluez-pin <phone's hardware address here>
 I get prompted to enter pin on laptop and phone, they seem to pair, but then i need to hit 

"connect" on my phone and i get denied here is what i see in the open terminal

```
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
```

any ideas?  I feel so close i can taste it!

also here is output after starting kbluetoothd

eric@vista:~$ kbluetoothd
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0

---

