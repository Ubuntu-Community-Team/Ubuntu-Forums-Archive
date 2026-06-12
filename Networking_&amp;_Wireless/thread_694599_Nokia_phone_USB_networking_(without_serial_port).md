---
title: "Nokia phone USB networking (without serial port)"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by lunar_shuttle on 2008-02-12
Hi all!

I'm wondering if there is anyone out there who has knowledge about later Nokia phones (N73 and N95 in particular) and network connection **without** using  the serial port (cdc-acm port usually registered as /dev/ttyACMX)?

I want to do stuff with the phone via the serial interface, /dev/ttyACMX - that is send regular AT-commands and such, while I'm still connected to the internet via these other devices that the Nokia phones appear to expose via USB. I've read about the RNDIS standard, which appears to be what Nokia has chosen to use instead of cdc-ether. If I understand everything correct RNDIS is a Microsoft "embrace-and-extend-and-lock-in" attempt which wraps wraps parts of the cdc-ether spec and mixes in the NDIS protocol to a badly documented half-secret standard instead of actually using cdc-ether. So RNDIS and cdc-ether appears to be common standards that are used in order to let the computer use the phone as a network card. RNDIS appears to be Microsoft-only (or mainly) and I've managed to get cdc-ether to work with a phone of another brand. 

But still, there's an RNDIS-driver in the Linux kernel, and it appears there exists stuff that uses RNDIS to sync with Windows CE-devices so I'm worrying that I'm missing something crucial here.... :confused: Thus my question: Has anyone managed to use their Nokia N73, N95 etc, via USB cable as a network interface with Ubuntu - **without** using the cdc-acm serial port and pppd? Does anyone know if it should be possible at all? Bluetooth or N95:s wlan interface is unfortunately not an option I can use in this case... :(

---

