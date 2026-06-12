---
title: "Bluetooth support in Ubuntu by version"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by Degenko on 2008-01-28
A question about support of Bluetooth USB adapters and other devices: how are they supported by the Bluetooth version they're using?

According to Wikipedia ([link]("http://en.wikipedia.org/wiki/Bluetooth#Bluetooth_1.2")):

```
Bluetooth 1.2

This version is backward-compatible with 1.1 and the major enhancements include the following:

    * Faster Connection and Discovery
    * Adaptive frequency-hopping spread spectrum (AFH), which improves resistance to radio frequency interference by avoiding the use of crowded frequencies in the hopping sequence.
    * Higher transmission speeds in practice, up to 721 kbit/s, as in 1.1.
    * Extended Synchronous Connections (eSCO), which improve voice quality of audio links by allowing retransmissions of corrupted packets.
    *** Host Controller Interface (HCI) support for three-wire UART.**
    * Ratified as IEEE Standard 802.15.1-2005.

```

So, as far as I understand, any device with Bluetooth 1.2 or later, has the HCI feature, which is the requirement for the device to work under Ubuntu, according to the documentation ([link]("https://help.ubuntu.com/community/BluetoothSetup#head-82b6734db30571f54da4ceaa7254b1b464640156")):

```
If your device has an HCI version listed, it should work under Linux.
```

Am I right, and if so, would [this adapter]("http://uk.giga-byte.com/Products/Communication/Products_Spec.aspx?ProductID=2205") work in Ubuntu?

Thanks! :)

---

