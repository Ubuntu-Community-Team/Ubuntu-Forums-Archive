---
title: "WLAN problem"
date: 2006-12-27
forum: Networking &amp; Wireless
---

### Post by Jeeks on 2006-12-27
I've been on Edgy since the day it was released and I never had any problem with my wireless adapter which is of the rt2500 type.

Today I noticed some slowness in transfer and all of a sudden everything died. I couldn't figure out where the problem was coming from.

I am pasting now the system logs during the problem

```

28/12/06 01:28:46	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:46	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:46	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:46	acer	kernel	[17181351.308000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:46	acer	kernel	[17181352.064000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:28:46	acer	kernel	[17181352.064000] pccard: CardBus card inserted into slot 0

28/12/06 01:28:46	acer	kernel	[17181352.064000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:28:46	acer	kernel	[17181352.064000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:28:46	acer	kernel	[17181352.064000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:28:46	acer	kernel	[17181352.064000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:28:47	acer	dhclient	

28/12/06 01:28:47	acer	dhclient	All rights reserved.

28/12/06 01:28:47	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:47	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:47	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:47	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:47	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:47	acer	kernel	[17181352.192000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:28:47	acer	kernel	[17181352.192000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:28:47	acer	kernel	[17181352.204000] pccard: card ejected from slot 0

28/12/06 01:28:47	acer	kernel	[17181352.264000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:28:48	acer	dhclient	

28/12/06 01:28:48	acer	dhclient	

28/12/06 01:28:48	acer	dhclient	All rights reserved.

28/12/06 01:28:48	acer	dhclient	All rights reserved.

28/12/06 01:28:48	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:48	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:48	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:48	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:48	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:48	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:48	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:48	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:48	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:48	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:48	acer	kernel	[17181353.232000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:28:48	acer	kernel	[17181353.232000] pccard: CardBus card inserted into slot 0

28/12/06 01:28:48	acer	kernel	[17181353.232000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:28:48	acer	kernel	[17181353.232000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:28:48	acer	kernel	[17181353.232000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:28:48	acer	kernel	[17181353.232000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:28:48	acer	kernel	[17181353.360000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:28:48	acer	kernel	[17181353.360000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:28:48	acer	kernel	[17181353.940000] pccard: card ejected from slot 0

28/12/06 01:28:48	acer	kernel	[17181354.000000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:28:49	acer	dhclient	

28/12/06 01:28:49	acer	dhclient	All rights reserved.

28/12/06 01:28:49	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:49	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:49	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:28:49	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:49	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:49	acer	dhclient	send_packet: No such device

28/12/06 01:28:49	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:49	acer	kernel	[17181354.908000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:28:49	acer	kernel	[17181354.908000] pccard: CardBus card inserted into slot 0

28/12/06 01:28:49	acer	kernel	[17181354.908000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:28:49	acer	kernel	[17181354.908000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:28:49	acer	kernel	[17181354.908000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:28:49	acer	kernel	[17181354.908000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:28:49	acer	kernel	[17181355.040000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:28:49	acer	kernel	[17181355.040000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:28:50	acer	dhclient	Listening on LPF/ra0/00:11:50:a8:df:71

28/12/06 01:28:50	acer	dhclient	Sending on   LPF/ra0/00:11:50:a8:df:71

28/12/06 01:28:50	acer	dhclient	Sending on   Socket/fallback

28/12/06 01:28:51	acer	dhclient	

28/12/06 01:28:51	acer	dhclient	All rights reserved.

28/12/06 01:28:51	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:51	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:51	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:51	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:51	acer	dhclient	receive_packet failed on ra0: Network is down

28/12/06 01:28:51	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

```

---

### Post by Jeeks on 2006-12-27
And more

```

28/12/06 01:28:51	acer	kernel	[17181356.276000] pccard: card ejected from slot 0

28/12/06 01:28:51	acer	kernel	[17181356.336000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:28:52	acer	kernel	[17181357.968000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:53	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:28:53	acer	dhclient	send_packet: No such device

28/12/06 01:28:53	acer	kernel	[17181358.536000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:54	acer	kernel	[17181359.272000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:54	acer	kernel	[17181359.996000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:55	acer	dhclient	

28/12/06 01:28:55	acer	dhclient	All rights reserved.

28/12/06 01:28:55	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:55	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:55	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:55	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:55	acer	kernel	[17181360.732000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:28:55	acer	kernel	[17181360.732000] pccard: CardBus card inserted into slot 0

28/12/06 01:28:55	acer	kernel	[17181360.732000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:28:55	acer	kernel	[17181360.732000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:28:55	acer	kernel	[17181360.732000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:28:55	acer	kernel	[17181360.732000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:28:55	acer	kernel	[17181360.924000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:28:55	acer	kernel	[17181360.924000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:28:55	acer	kernel	[17181361.152000] pccard: card ejected from slot 0

28/12/06 01:28:56	acer	dhclient	

28/12/06 01:28:56	acer	dhclient	All rights reserved.

28/12/06 01:28:56	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:56	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:56	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:56	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4

28/12/06 01:28:56	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:56	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:56	acer	dhclient	send_packet: No such device

28/12/06 01:28:56	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:56	acer	kernel	[17181361.212000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:28:57	acer	dhclient	

28/12/06 01:28:57	acer	dhclient	

28/12/06 01:28:57	acer	dhclient	All rights reserved.

28/12/06 01:28:57	acer	dhclient	All rights reserved.

28/12/06 01:28:57	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:57	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:57	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:28:57	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:57	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:28:57	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:57	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:28:57	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:57	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:28:57	acer	kernel	[17181362.228000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:28:57	acer	kernel	[17181362.228000] pccard: CardBus card inserted into slot 0

28/12/06 01:28:57	acer	kernel	[17181362.228000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:28:57	acer	kernel	[17181362.228000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:28:57	acer	kernel	[17181362.228000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:28:57	acer	kernel	[17181362.228000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:28:57	acer	kernel	[17181362.372000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:28:57	acer	kernel	[17181362.372000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:28:57	acer	kernel	[17181362.784000] pccard: card ejected from slot 0

28/12/06 01:28:57	acer	kernel	[17181362.848000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:28:58	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:28:58	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:28:58	acer	dhclient	send_packet: No such device

28/12/06 01:28:58	acer	kernel	[17181364.024000] cs: pcmcia_socket0: unable to apply power.

28/12/06 01:28:59	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6

28/12/06 01:28:59	acer	dhclient	send_packet: No such device

28/12/06 01:29:00	acer	dhclient	

28/12/06 01:29:00	acer	dhclient	

28/12/06 01:29:00	acer	dhclient	All rights reserved.

28/12/06 01:29:00	acer	dhclient	All rights reserved.

28/12/06 01:29:00	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:29:00	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:29:00	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:29:00	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10

28/12/06 01:29:00	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:29:00	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:29:00	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:29:00	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:29:00	acer	dhclient	send_packet: No such device

28/12/06 01:29:00	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:29:00	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:29:00	acer	kernel	[17181365.264000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:29:00	acer	kernel	[17181365.264000] pccard: CardBus card inserted into slot 0

28/12/06 01:29:00	acer	kernel	[17181365.264000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:29:00	acer	kernel	[17181365.264000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:29:00	acer	kernel	[17181365.264000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:29:00	acer	kernel	[17181365.264000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:29:00	acer	kernel	[17181365.392000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:29:00	acer	kernel	[17181365.392000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:29:00	acer	kernel	[17181365.832000] pccard: card ejected from slot 0

28/12/06 01:29:00	acer	kernel	[17181365.892000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

28/12/06 01:29:01	acer	dhclient	

28/12/06 01:29:01	acer	dhclient	All rights reserved.

28/12/06 01:29:01	acer	dhclient	Bind socket to interface: No such device

28/12/06 01:29:01	acer	dhclient	Copyright 2004-2006 Internet Systems Consortium.

28/12/06 01:29:01	acer	dhclient	For info, please visit http://www.isc.org/sw/dhcp/

28/12/06 01:29:01	acer	dhclient	Internet Systems Consortium DHCP Client V3.0.4

28/12/06 01:29:01	acer	dhclient	There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416

28/12/06 01:29:01	acer	kernel	[17181366.544000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

28/12/06 01:29:01	acer	kernel	[17181366.544000] pccard: CardBus card inserted into slot 0

28/12/06 01:29:01	acer	kernel	[17181366.544000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)

28/12/06 01:29:01	acer	kernel	[17181366.544000] PCI: Setting latency timer of device 0000:02:00.0 to 64

28/12/06 01:29:01	acer	kernel	[17181366.544000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com

28/12/06 01:29:01	acer	kernel	[17181366.544000] yenta EnE: chaning testregister 0xC9, 04 -> 04

28/12/06 01:29:01	acer	kernel	[17181366.844000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel

28/12/06 01:29:01	acer	kernel	[17181366.844000] rt2500 EEPROM: 13 13 13 13 13 13 13 13 13 13 12 12 11 11  dBm Maximum

28/12/06 01:29:02	acer	dhclient	Listening on LPF/ra0/00:11:50:a8:df:71

28/12/06 01:29:02	acer	dhclient	Sending on   LPF/ra0/00:11:50:a8:df:71

28/12/06 01:29:02	acer	dhclient	Sending on   Socket/fallback

28/12/06 01:29:03	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:29:05	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15

28/12/06 01:29:07	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:29:10	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11

28/12/06 01:29:12	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3

28/12/06 01:29:12	acer	kernel	[17181377.192000] ra0: no IPv6 routers present

28/12/06 01:29:13	acer	dhclient	DHCPREQUEST on ra0 to 255.255.255.255 port 67

28/12/06 01:29:15	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5

28/12/06 01:29:20	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13

28/12/06 01:29:20	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7

28/12/06 01:29:21	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17

28/12/06 01:29:23	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6

28/12/06 01:29:27	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 16

28/12/06 01:29:29	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9

28/12/06 01:29:33	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20

28/12/06 01:29:38	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15

28/12/06 01:29:38	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 19

28/12/06 01:29:40	acer	kernel	[17181405.772000] usb 4-3: new high speed USB device using ehci_hcd and address 3

28/12/06 01:29:40	acer	kernel	[17181405.904000] usb 4-3: configuration #1 chosen from 1 choice

28/12/06 01:29:43	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8

28/12/06 01:29:43	acer	kernel	[17181408.808000] usb 4-3: USB disconnect, address 3

28/12/06 01:29:44	acer	kernel	[17181409.232000] usb 2-1: new full speed USB device using uhci_hcd and address 2

28/12/06 01:29:44	acer	kernel	[17181409.352000] usb 2-1: device descriptor read/64, error -71

28/12/06 01:29:44	acer	kernel	[17181409.576000] usb 2-1: device descriptor read/64, error -71

28/12/06 01:29:44	acer	kernel	[17181409.792000] usb 2-1: new full speed USB device using uhci_hcd and address 3

28/12/06 01:29:44	acer	kernel	[17181409.912000] usb 2-1: device descriptor read/64, error -71

28/12/06 01:29:44	acer	kernel	[17181410.136000] usb 2-1: device descriptor read/64, error -71

28/12/06 01:29:45	acer	kernel	[17181410.352000] usb 2-1: new full speed USB device using uhci_hcd and address 4

28/12/06 01:29:45	acer	kernel	[17181410.760000] usb 2-1: device not accepting address 4, error -71

28/12/06 01:29:45	acer	kernel	[17181410.872000] usb 2-1: new full speed USB device using uhci_hcd and address 5

28/12/06 01:29:46	acer	kernel	[17181411.280000] usb 2-1: device not accepting address 5, error -71

28/12/06 01:29:47	acer	kernel	[17181413.080000] usb 4-3: new high speed USB device using ehci_hcd and address 5

28/12/06 01:29:48	acer	kernel	[17181413.212000] usb 4-3: configuration #1 chosen from 1 choice

28/12/06 01:29:51	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7

28/12/06 01:29:51	acer	kernel	[17181417.124000] usb 4-3: USB disconnect, address 5

28/12/06 01:29:53	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4

28/12/06 01:29:53	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7

28/12/06 01:29:57	acer	dhclient	bound: renewal in 980217850 seconds.

28/12/06 01:29:57	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 20

28/12/06 01:29:57	acer	dhclient	No DHCPOFFERS received.

28/12/06 01:29:57	acer	dhclient	Trying recorded lease 192.168.1.10

28/12/06 01:29:57	acer	ntpdate[7613]	step time server 82.211.81.145 offset -0.009976 sec

28/12/06 01:29:58	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11

28/12/06 01:30:00	acer	dhclient	bound: renewal in 980217847 seconds.

28/12/06 01:30:00	acer	dhclient	No DHCPOFFERS received.

28/12/06 01:30:00	acer	dhclient	Trying recorded lease 192.168.1.10

28/12/06 01:30:00	acer	ntpdate[7631]	step time server 82.211.81.145 offset -0.000097 sec

28/12/06 01:30:01	acer	kernel	[17181426.688000] usb 4-3: new high speed USB device using ehci_hcd and address 6

28/12/06 01:30:01	acer	kernel	[17181426.820000] usb 4-3: configuration #1 chosen from 1 choice

28/12/06 01:30:09	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4

28/12/06 01:30:11	acer	kernel	[17181437.032000] usb 4-3: USB disconnect, address 6

28/12/06 01:30:13	acer	dhclient	bound: renewal in 980217834 seconds.

28/12/06 01:30:13	acer	dhclient	No DHCPOFFERS received.

28/12/06 01:30:13	acer	dhclient	Trying recorded lease 192.168.1.10

28/12/06 01:30:13	acer	ntpdate[7658]	step time server 82.211.81.145 offset -0.000091 sec

28/12/06 01:30:17	acer	dhclient	DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7

28/12/06 01:30:24	acer	dhclient	bound: renewal in 980217823 seconds.

28/12/06 01:30:24	acer	dhclient	No DHCPOFFERS received.

28/12/06 01:30:24	acer	dhclient	Trying recorded lease 192.168.1.10

28/12/06 01:30:24	acer	ntpdate[7676]	step time server 82.211.81.145 offset 0.000136 sec

28/12/06 01:59:42	acer	none	-- MARK --

28/12/06 02:17:01	acer	/USR/SBIN/CRON[7766]	(root) CMD (   run-parts --report /etc/cron.hourly)

28/12/06 02:39:42	acer	none	-- MARK --
```

---

