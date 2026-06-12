---
title: "Wireless card recognized  by installer but not by network manager"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by rossd on 2007-02-03
I installed Edgy Eft on an old Pentium III laptop (Toshiba Satellite Pro 4300).
The wireless card (Netgear- Atheros driver) was recognized and the installer could see my ESSID.

However after booting up, network manager could not see the wireless connection.

Can anyone suggest why?

---

### Post by Floppyjoe on 2007-02-03
Network Manager has problems with some cards. I'm not sure though if yours is one of them.

---

### Post by jml on 2007-02-03
Precisely what NetGear Wireless card do you have?  Model number, Version?  I have a WG511T that is working right now as I type and it is also based on the Atheros chipset.  Another question, what installer are yoou referring to?  Also, are you trying to connect to an encrypted network?  Does your cars support that particular type of encryption.  (for example, older 802.11 b cards do not support WPA encryption.

Joe

---

### Post by rossd on 2007-02-04
Thanks guys for your prompt replies. 

The card is a Netgear WG511T. The router uses WEP. The installation process understood the WEP encryption (it asks once it finds the ESSID) (and the card supports it) so I'm not sure why this matters.  

I'm referring to the edgy Eft iso image downloaded off the AU mirror.
What info do you need?
The kernel at the time (from grub) was
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic

The lshw info is (since I installed the alternate kernel) is
     *-network
          description: Wireless interface
          product: AR5212 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@02:00.0
          logical name: wifi0
          version: 01
          serial: 00:0f:b5:e8:b4:19
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci ip=10.1.1.7 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:22000000-2200ffff irq:11

I have sorted the problem. I'm using the machine now for this bit of banter. What I cannot fathom is how the UBUNTU installer can recognize a device and connect to the router but the OS's primary application for establishing network connection can't. I love the fact UBUNTU can be installed using 1CD and relies on internet connections for installing other applications so one would think that establishing internet connectivity is high on the list of "things that should work". 

Cheers

---

### Post by stavaroti on 2007-02-07
Hi,

I am a noob, so please forgive me for any errors.  I just installed network manager and it installed fine.  However network manager only displays the wired connection but no wireless connection.  Any help would be appreciated.

---

### Post by rossd on 2007-02-07
Hi

You could try 

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

or in synaptic package manager search for  atheros wireless and install the restricted package (this worked for me)

Cheers

---

### Post by stavaroti on 2007-02-07
Hi,

Okay so I tried to reset everything as mentioned in this forum and others, but network manager still does not show my wireless connections.  The funny thing is that wifi radar will, but i can not use wifi radar because it does not allow me to to use wpa.  I have a dell 700m with a broadcom wireless chip in it, i think 1390, and here are somemore details from *-network:

*-network:0 UNCLAIMED
                description: Network controller
                product: BCM4309 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@02:01.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:e0204000-e0205fff irq:10

Any help will be appreciated

Thanks.

---

### Post by tdhombre on 2007-02-07
I have found that there are conflicts between WiFi-Radar and NM.  Suggest you COMPLETELY uninstall wifi-radar and try again with nm.

Good luck.

---

### Post by dannyboy79 on 2007-02-08
the problem is the madwifi-ng version that comes with edgy I beleive. madwifi has solved this issue per this link, [http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016).  read the post dated 2-06-07. you need madwifi-ng r2081.

---

