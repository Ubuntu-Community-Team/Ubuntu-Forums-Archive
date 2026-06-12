---
title: "programming bluetooth with java jsr 82"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by jay|rookie on 2007-08-02
Hi,

i've got problems to get my bluetooth device working using sun jsr 82 classes.

what i have:
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
what i've done:
First i installed bluez components and tested them by pairing my PC with my mobile phone.
It works fine.
Then I plugged the packages javax.bluetooth and javax.obex into my project.
Sun's documentation contains a code snippet that should produce an objectinstance of my bluetooth device.
The Snippet is:
//		 retrieve the local Bluetooth device object
		LocalDevice local = LocalDevice.getLocalDevice();
//		 retrieve the Bluetooth address of the local device
		String address = local.getBluetoothAddress();
//		 retrieve the name of the local Bluetooth device
		String name = local.getFriendlyName();

Now I get the Exception of Type -BluetoothStateException- just when running the first line.
Where's my problem? I think something basic is missing here ..

Thank you for any help...

---

