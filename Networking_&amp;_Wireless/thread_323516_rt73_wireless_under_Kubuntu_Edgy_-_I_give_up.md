---
title: "rt73 wireless under Kubuntu Edgy - I give up"
date: 2006-12-22
forum: Networking &amp; Wireless
---

### Post by marlowe on 2006-12-22
OK. I've hacked around with this until my eyes bled, but no dice. I'm officially admitting defeat, and throwing myself on the mercy of the court.

I'm trying to get my wireless card to behave under Kubuntu Edgy. The card is internal to the laptop, and is an MSI (Ralink) MS-6877, which is one of the many cards that run the Ralink rt73 chipset. I should stress before we go any further that the card has worked in the past. I've had it running flawlessly under ndiswrapper and SUSE 10.1, and later ran it with the Ralink native drivers under Opensuse 10.2. Kubuntu, though, just doesn't want to know.

The card is detected correctly and assigned to wlan0. If I scan for networks, I can see my local wireless intranet. Not only that, but the encryption protocol, mode, frequency and other gubbins are all detected correctly. When I try to connect to the network, though, it just won't.

My windows box is currently talking to the very same network over wireless, so the network is definitely good. I've disabled all encryption and any MAC address filtering that I had running - still no dice.

The only clue I've managed to pick up is in the result of lshw -C network, which gives this (sorry for the codedump)

```

  *-usb
       description: Wireless interface
       product: 802.11 bg WLAN
       vendor: Ralink
       physical id: 5
       bus info: usb@3:5
       logical name: wmaster0
       version: 0.01
       serial: 00:13:d3:81:81:79
       capabilities: usb-2.00 logical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=CVS firmware=rt
73usb->%s: Error - vendor requ3-5:1.0 link=yes maxpower=300mA multicast=yes spee
d=480.0MB/s wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@08:06.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:52:7c:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                                             00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driververs                                             ion=0.9.27 duplex=full ip=192.168.0.185 link=yes multicast=yes port=MII speed=10                                             0MB/s
       resources: ioport:a000-a0ff iomemory:d0100c00-d0100cff irq:50
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:d3:81:81:79
       capabilities: ethernet physical wireless
       configuration: multicast=yes wireless=IEEE 802.11g



```

Notice the error for wmaster0 (why has it split the card into wlan0 and wmaster0, btw? Is that right?)

I've tried running the card under ndiswrapper, with the ralink native drivers, and with the serialmonkey rt73 drivers - same (lack of) results each time. So, please, take pity on a poor n00b, and help me out here.

---

### Post by marlowe on 2006-12-28
**bump**

Please? Pretty pretty please?

If you fix it, I'll write you a special poem. It'll go something like this:

[I]
I tried and tried, but tried and failed;
Tried every hack to no avail.
I'd almost given up all hope,
Until a post by some great bloke. [*]
So praise to you, <insert name here>,
For you have fixed my wireless gear.
[/I]

* or bloke-ess. Treat this as gender-neutral, for the sake of rhyme.

---

### Post by FrodoB on 2006-12-28
Here is one way to do it, only WEP is documented, but WPA-PSK is possible:
 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by techpeace on 2006-12-29
I found the following post exceedingly helpful:

[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

---

### Post by TheCaptain2000 on 2007-01-21
you can follow the istructions listed here: [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)
forget the fact it is in Italian, just launch the command one ofater the other. Basically they get the driver from the cvs rather than using the one coming from edgy. I have it working, it is stable and i am using it on a production server with no probs since several days.
BR
:guitar:

---

