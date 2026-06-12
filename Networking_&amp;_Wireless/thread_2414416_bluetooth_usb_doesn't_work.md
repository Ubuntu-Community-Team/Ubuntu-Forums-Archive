---
title: "bluetooth usb doesn't work"
date: 2019-03-10
forum: Networking &amp; Wireless
---

### Post by jasoncowboy on 2019-03-10
Hi guys, I've been searching for a solution to my bluetooth dongle, result in lsusb showned as this:
```
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


```
I can't turn the bluetooth on and blueman just doesn't detect this adapter.

---

### Post by ChuckFromEugene on 2019-03-16
Tell me about it!  

I've got several of those and they all work on Windows 7.   I've tried them on 18.04 LTS, 16.04 and 14.04, in both AMD64 and X32 distros and I get the same response from hciconfig:

```

hci0:    Type: Primary  Bus: USB
    BD Address: 33:03:30:0A:C4:A3  ACL MTU: 360:4  SCO MTU: 0:0
    DOWN 
    RX bytes:553 acl:0 sco:0 events:28 errors:0
    TX bytes:368 acl:0 sco:0 commands:30 errors:0
    Features: 0xff 0xff 0xcd 0xfa 0xdb 0xbf 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 

```

And if I try to "sudo hciconfig hci0 up", I get this:
```
Can't init device hci0: Operation not supported (95)
```

Now, here's the funny thing:  if I take the same USB dongle and try it on an Orange Pi PC or Raspberry Pi running Armbian Ubuntu 16.04, I get this:

```

hci0:    Type: BR/EDR  Bus: USB
    BD Address: 33:03:30:0A:CC:7D  ACL MTU: 360:4  SCO MTU: 0:0
    UP RUNNING PSCAN ISCAN 
    RX bytes:587 acl:0 sco:0 events:38 errors:0
    TX bytes:3777 acl:0 sco:0 commands:38 errors:0
    Features: 0xff 0xff 0xcd 0xfa 0xdb 0xbf 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 
    Name: 'orangepipc'
    Class: 0x1c0000
    Service Classes: Rendering, Capturing, Object Transfer
    Device Class: Miscellaneous, 
    HCI Version: 4.0 (0x6)  Revision: 0x709
    LMP Version: 4.0 (0x6)  Subversion: 0x709
    Manufacturer: Cambridge Silicon Radio (10)
```

And it works!  I've run into situations where the Armbian version of Ubuntu didn't work right, while the X32 and AMD64 version did, but this is the first one where the reverse is true.

Does this give anyone some additional data?

---

### Post by ChuckFromEugene on 2019-03-17
I think I've got it figured out.   The Chinese CSR USB dongles say that they implement a certain command.  The failure is evidently due to the CSR clones not implementing the DELETE_STORED_LINK_KEY command as evidenced by bltmon:

```
HCI Event: Command Complete (0x0e) plen 6     
    Delete Stored Link Key (0x03|0x0012) ncmd 5
    status 0x11 deleted 0
    Error: Unsupported Feature or Parameter Value
```

But the dongle claims that it does:

```

> HCI Event: Command Complete (0x0e) plen 68               #31 [hci0] 10.207958
      Read Local Supported Commands (0x04|0x0002) ncmd 5
        Status: Success (0x00)
        Commands: 165 entries
          Inquiry (Octet 0 - Bit 0)
          Inquiry Cancel (Octet 0 - Bit 1)
...
          Reset (Octet 5 - Bit 7)
          Set Event Filter (Octet 6 - Bit 0)
          Flush (Octet 6 - Bit 1)
          Read PIN Type (Octet 6 - Bit 2)
          Write PIN Type (Octet 6 - Bit 3)
          Create New Unit Key (Octet 6 - Bit 4)
          Read Stored Link Key (Octet 6 - Bit 5)
          Write Stored Link Key (Octet 6 - Bit 6)
          Delete Stored Link Key (Octet 6 - Bit 7)
          Write Local Name (Octet 7 - Bit 0)
          Read Local Name (Octet 7 - Bit 1)
```

Evidently, the Armbian code ignores the illegal command and just soldiers on, where the i386 version aborts because of an error (the relevant file is hci_core.c).

The obvious "right" solution is to use a conforming dongle.  But a quick view on eBay for "USB bluetooth dongle" shows that these things are all over the place and not likely to go away.

Any input from more knowledgeable folks here?

---

### Post by jeremy31 on 2019-03-17
There is some code in btusb.c that should deal with 
```
	/* Detect controllers which aren't real CSR ones. */
	if (le16_to_cpu(rp->manufacturer) != 10 ||
	    le16_to_cpu(rp->lmp_subver) == 0x0c5c) {
		/* Clear the reset quirk since this is not an actual
		 * early Bluetooth 1.1 device from CSR.
		 */
		clear_bit(HCI_QUIRK_RESET_ON_CLOSE, &hdev->quirks);

		/* These fake CSR controllers have all a broken
		 * stored link key handling and so just disable it.
		 */
		set_bit(HCI_QUIRK_BROKEN_STORED_LINK_KEY, &hdev->quirks);
	}

	kfree_skb(skb);

	return 0;
}
```

---

### Post by ChuckFromEugene on 2019-03-21
Something's not working then. I've got the 4.15.0-46 kernel btusb.ko and the bug persists.
Curiously, the thing works with Arbian Ubuntu 16.04.

I'll have to do some investigation to see what the difference is.  FWIW, the dongle works fine on Win7.

---

### Post by ChuckFromEugene on 2019-03-21
I can see how the code snippet above won't work.  The vendor ID is in fact 10, but the subversion is 0x0709, not 0x0c5c!

So we have the case of yet another counterfeit.

This is info from btmon:

[ATTACH=CONFIG]282829[/ATTACH]


FWIW, here's the lsusb detail on the thing.  I don't know if it'll help.  Could it be that the code in btusb.c is missing this special case?

[ATTACH]282828[/ATTACH]

---

### Post by ChuckFromEugene on 2019-03-21
Why not simply modify the code to ignore the return from the DELETE_STORED_LINK_KEY on initialization?  Would that break anything?

---

### Post by ChuckFromEugene on 2019-03-22
Comparing the 16.04 Armhf source for hci_core.c with the x86 18.04 version shows the two, while they resemble one another, are quite different in many respects.   The Armhf version works with the dongle and yet doesn't have a check nor the definition of QUIRK_BROKEN_STORED_LINK_KEY--and it works with the dongle.

So, how did two versions of the BT kernel code get so different?

---

