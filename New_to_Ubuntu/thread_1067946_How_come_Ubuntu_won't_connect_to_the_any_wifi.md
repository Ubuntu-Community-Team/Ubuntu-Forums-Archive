---
title: "How come Ubuntu won't connect to the any wifi?"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by cheese123 on 2009-02-12
I am currently multibooting Xp and Ubuntu. I cannot connect to my Universities Public and Private wifi. The private is secure, but I have the info to access it. I've notice I can only connect to the wifi on XP, but when I run Ubuntu I'm getting nothing. If it helps I have a Intel Pro/Wireless 3945ABG wireless card.

---

### Post by prometheus1981 on 2009-02-12
You need to make sure to install the drivers for the wireless card. Does you computer have a Wi-Fi indicator "light"? If so, can you turn it on or off while in Ubuntu?

Also, please post as much hardware information that you can and version of Ubuntu you are using.

---

### Post by BDNiner on 2009-02-12
Can you post the output of
```

lshw -C Network

```
when run from a terminal in ubuntu? This will display what networking hardware you have installed and may give a clue as to what the problem is.

---

### Post by cheese123 on 2009-02-12
I'm using Ubuntu 8.10 II, here is some of my hardware info.

Acer Aspire 5930
Intel Core Duo T5750 @ 2.00 Ghz
3 GB
Intel 965 Chipset
Realtek HD Audio
320 HDD

---

### Post by gn2 on 2009-02-12
I have the same wireless adapter and just couldn't get it to work with Network Manager.

The cure for me was to remove the network-manager package with Synaptic and install [Wicd]("http://wicd.sourceforge.net/").

---

### Post by cheese123 on 2009-02-12
> **gn2 said:**
> I have the same wireless adapter and just couldn't get it to work with Network Manager.

The cure for me was to remove the network-manager package with Synaptic and install [Wicd]("http://wicd.sourceforge.net/").

Could you give me steps on how to do this?

---

### Post by mc4100 on 2009-02-12
> **cheese123 said:**
> I have a Intel Pro/Wireless 3945ABG wireless card.
That card should work fine, you might be affected by this:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues)

A few questions:
Have updated since you installed?
Is there a light that's on when using Windows but not Ubuntu?
What's the output of BDNiner's command?

Wicd might be a good solution, but I'd say that's a last resort since it **should** work.

---

### Post by cheese123 on 2009-02-12
> **BDNiner said:**
> Can you post the output of
```

lshw -C Network

```
when run from a terminal in ubuntu? This will display what networking hardware you have installed and may give a clue as to what the problem is.

```

 *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:96:33:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:bd:56:de
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5787m-v3.23 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 76:17:7c:1b:a5:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by |{urse on 2009-02-12
+1 to the poster who suggested wicd. NetworkManager did the same thing with my atheros5k and my enlwig2 (rtl8185 based) card. The networks were there but would never connect to them. Now i use wicd instead and both cards work fine.

---

### Post by cheese123 on 2009-02-12
> **mc4100 said:**
> That card should work fine, you might be affected by this:
[http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/810#Other%20known%20issues)

A few questions:
Have updated since you installed?
Is there a light that's on when using Windows but not Ubuntu?
What's the output of BDNiner's command?

Wicd might be a good solution, but I'd say that's a last resort since it **should** work.

The light is on when I use both Ubuntu and Windows, how do I uninstall network manager and install wicd? I've already updated. Sorry I just install this yesterday. I am still a noob. :(

---

### Post by tarps87 on 2009-02-12
Probably the easiest suggestion is the Ubuntu section of their site:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Administration > Synaptic Packages
add this to the third party tab:
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

Now in a terminal window type:
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

Now in add remove programs search for wicd

If you have any problems just post back

---

### Post by prometheus1981 on 2009-02-12
To remove the Network Manager, go to "Applications", and then select "Add/Remove...", type "network" in the search bar and un-check "Network Manager", finish by clicking on "Apply Changes".

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103054&d=1234463070[/IMG]

---

### Post by BDNiner on 2009-02-12
Ubuntu is detecting your card fine. I am not sure about installing wicd so someone with experience should chime in this issue.

---

### Post by |{urse on 2009-02-12
the post above the screenshot explained that

---

### Post by cheese123 on 2009-02-12
> **tarps87 said:**
> Probably the easiest suggestion is the Ubuntu section of their site:
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Administration > Synaptic Packages
add this to the third party tab:
deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras

Now in a terminal window type:
wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

Now in add remove programs search for wicd

If you have any problems just post back

I'm getting this error when I reload the synaptics package

```

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by cheese123 on 2009-02-12
Okay well I just going to blow my head off with my Desert Eagle ](*,) Thanks for the help guys.

---

### Post by gn2 on 2009-02-12
To stop the error, click: System > Administration > Synaptic Package Manager > Settings > Repositories > Third Party Software and un-tick the CD Rom entry. 

Then reload.

---

