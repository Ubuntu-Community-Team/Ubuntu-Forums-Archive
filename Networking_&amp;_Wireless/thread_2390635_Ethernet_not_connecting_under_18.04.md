---
title: "Ethernet not connecting under 18.04"
date: 2018-04-30
forum: Networking &amp; Wireless
---

### Post by jdbx on 2018-04-30
Hello,
I upgraded from 16.04 last week-end on my Dell Inspiron 1545 (Intel® Core™2 Duo CPU T9800 @ 2.93GHz × 2). Since then, I can only use the Wifi to connect to the Internet, my Ethernet connection doesn't work. My Ethernet controler is:
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
Here is what I get with some command lines:
```
jide@jide-Inspiron-1545:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Advertised FEC modes: Not reported
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: no

```
And:
```
jide@jide-Inspiron-1545:~$ sudo ifconfig eth0
eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:25:64:3e:c7:1e  txqueuelen 1000  (Ethernet)
        RX packets 1195  bytes 111332 (111.3 KB)
        RX errors 0  dropped 13  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 18  
```

I have tried the following Command "sudo apt-get install ethtool" (with my version being more recent) and being told to use "sudo apt autoremove" to delete unnecessary packets.
As you may expect, I am at a loss here. If anyone can help, it will be very much welcome!

---

### Post by TheFu on 2018-04-30
**sudo lshw -C network** would be helpful, but I don't see anything wrong at this point.
Please use 'code tags' whenever posting command output.  Also, editing the first post and wrapping the output in code tags will help others with readability.  Adv Reply (#).

As for connection stiff, I'd like to see **route -n** output and the **resolv.conf** file.

---

### Post by jdbx on 2018-05-01
Hello TheFu,
Sorry for the "excecrable" formatting, hope this is better:
```

jide@jide-Inspiron-1545:~$ sudo lshw -C network
[sudo] Mot de passe de jide : 
  *-network                 
       description: Interface réseau sans fil
       produit: BCM4322 802.11a/b/g/n Wireless LAN Controller
       fabriquant: Broadcom Limited
       identifiant matériel: 0
       information bus: pci@0000:0c:00.0
       nom logique: wlan0
       version: 01
       numéro de série: 00:24:2b:e0:ef:ea
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=192.168.1.118 latency=0 multicast=yes wireless=IEEE 802.11
       ressources: irq:17 mémoire:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       produit: 88E8040 PCI-E Fast Ethernet Controller
       fabriquant: Marvell Technology Group Ltd.
       identifiant matériel: 0
       information bus: pci@0000:09:00.0
       nom logique: eth0
       version: 13
       numéro de série: 00:25:64:3e:c7:1e
       taille: 100Mbit/s
       capacité: 100Mbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=sky2 driverversion=1.30 duplex=full latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       ressources: irq:24 mémoire:f68fc000-f68fffff portE/S:de00(taille=256)
jide@jide-Inspiron-1545:~$ 

```
then:
```

jide@jide-Inspiron-1545:~$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0
jide@jide-Inspiron-1545:~$ 

```

That last command, **resolv.conf** gives confusing results. Initially it gives:
```

jide@jide-Inspiron-1545:~$ resolv.conf

La commande « resolv.conf » n'a pas été trouvée, voulez-vous dire :

  commande « resolvconf » du deb openresolv
  commande « resolvconf » du deb resolvconf

Essayez : sudo apt install <nom du deb>

jide@jide-Inspiron-1545:~$

```
If I try **sudo apt install**, the installed file is more up-to-date than the download (and still dives no result). If I type **resolvconfig**, I get:
```

jide@jide-Inspiron-1545:~$ resolvconf
resolvconf: Error: Command not recognized
Usage: resolvconf (-d IFACE|-a IFACE|-u|--enable-updates|--disable-updates|--updates-are-enabled)
jide@jide-Inspiron-1545:~$ 

```

Since I am learning this as I go, can you tell what exactly you're looking for with these comamnds?
Thanks a lot for your help,

---

### Post by jdbx on 2018-05-01
Well, I guess the code tags were not properly used. Sorry 'bout that.

---

### Post by jeremy31 on 2018-05-01
jdbx the code tags here are [noparse]```
 
```[/noparse] Not <code></code>
In advanced reply you can use the # icon

---

### Post by TheFu on 2018-05-01
sudo apt autoremove will clean up old packages. This is a good thing, almost always.

Do you want wifi or ethernet?   Disable the wifi card if you want ethernet to work.  Having 2 NICs on the same subnet is not a beginner task.  You may need to logout and login to get the ethernet connection working if you used a GUI to configure it.

The **lshw** shows the driver used with all network adapters.  sky2, for the 100-base-tx NIC.
**route -n** shows that there is a connection to the router, somehow. It is on the 192.168.1.0/24 subnet.  That would be normal. So the router seems to be providing data over DHCP. But this is wifi stuff, not ethernet.

So, at this point, I think you don't actually have any network issue, just have wifi instead of ethernet.  It is a priority problem, I suppose.

The **resolv.conf** file ... is a file, not a command.  It controls name resolution - the lookups for internet, and maybe for local servers.  Linux distros have been screwing with name resolution the last 6+ yrs and can't seem to get it right.  In the old days, we could just manually edit the /etc/resolv.conf with IP addresses for nameservers to be used.  Then they tried to _make it easier_ by overwriting that file based on what was inside the *interfaces* file. I think the resolvconf package/command was supposed to deal with that, it normally isn't used directly by any users or admins. resolvconf is configured in text files. For normal network setups, there isn't any need to touch those. Then someone decided everything was too complex and put in a new system called netplan which connects to resolvconf somehow.  I miss the old days.  I've never used netplan.

Oh ... and if you use a GUI to setup the network, an extra layer is involved to get fowled up. 18.04 is the first LTS with netplan.

So ... just to be positive that networking is actually working and it truly is just a DNS issue, please use IP addresses and 
* ping 192.168.1.1 # the router
* ping 8.8.8.8  # google's DNS
* ping google.com   # force a DNS lookup
I bet the first 2 work perfect and the last one fails.

If all this works as I expect, then you know it is a DNS issue and should head down that path for a solution.  I don't have 18.04 (and won't for a few months), so how to deal with DNS is something you'll need to google.   Looks like there was a bug reported [https://bugs.launchpad.net/cloud-init/+bug/1750884](https://bugs.launchpad.net/cloud-init/+bug/1750884) against the MAAS release related to this a few months ago.  That shouldn't impact you on a typical desktop install, but who knows? I'd assume it doesn't at this point.

If there still is an issue, try a different cable and a different port on the switch/router.

After you get an internet connection working, you should 
* sudo apt update
* sudo apt upgrade
and do that weekly, probably just after you do system backups.

Lastly, ethtool should NOT be needed, unless specifically required.  I haven't needed it in about 10 yrs. Driver defaults for all common NICs - like you have - are fine.

---

### Post by jdbx on 2018-05-03
Thanks for all these explanations TheFu, useful!
I do have  connectivity to Internet (I am using the laptop to post answers), but it  is with the Wifi. I do not think the cable or router are faulty: if I  disconnect the cable, the led on the router turns off and it turns back  on when I re-connect the cable.

So I am going with the netplan  issue, but I will reconfigure the router (it needs to get done anyways)  alas. And thanks again for the lead on the bug!
cheers!

---

### Post by jdbx on 2018-05-03
Ok, something odd here. I tried **cat** command, but got nothing (as shown below).
```
jide@jide-Inspiron-1545:~$ cat /etc/netplan/50-cloud-init.yaml
cat: /etc/netplan/50-cloud-init.yaml: Aucun fichier ou dossier de ce type
jide@jide-Inspiron-1545:~$ cat /etc/network/interfaces.d/50-cloud-init.cfg
cat: /etc/network/interfaces.d/50-cloud-init.cfg: Aucun fichier ou dossier de ce type
jide@jide-Inspiron-1545:~$ 

```
How can I have a Wifi connection, if there is no config/netplan file??

---

### Post by TheFu on 2018-05-03
If you don't disable wifi,  logout,login, and only use the ethernet, then there isn't any assurance anything is working.
I would assume the cable **is** faulty - mainly because it is so easy to check.  Same for the switch/router port.  Blinking lights aren't exactly useful.

network-manager is dealing with your connectivity.

---

### Post by jdbx on 2018-05-03
Well... I tried looking into the Networkmanager.conf file, with hopes of using suggestions found in [http://www.ubuntugeek.com/how-to-fix-dns-problems-after-upgrading-ubuntu-17-10-from-ubuntu-17-04-16-10-16-04.html](http://www.ubuntugeek.com/how-to-fix-dns-problems-after-upgrading-ubuntu-17-10-from-ubuntu-17-04-16-10-16-04.html) (namely solution 2, changing "dns=dnsmasq" to "dns=systemd-resolved")
 and here is what I have:
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

```

Does anyone know what to make of this?

---

### Post by ptosis on 2018-09-17
I have same problem, tried different known good cable, tried different port on router.  This 18.04.1 is buggy as hell and I want to downgrade so I can get back to work. Wifi is slower.

What command do I use to fix this. It keeps trying andtrying and trying to  connecting and over an over  and over again is says activation fail!@

---

### Post by chili555 on 2018-09-17
> **ptosis said:**
> I have same problem, tried different known good cable, tried different port on router.  This 18.04.1 is buggy as hell and I want to downgrade so I can get back to work. Wifi is slower.

What command do I use to fix this. It keeps trying andtrying and trying to  connecting and over an over  and over again is says activation fail!@I doubt that your question that is tacked on to the end of a six-month-old thread will get much attention. Please start your own new question.

---

### Post by TheFu on 2018-09-17
Networking in 16.04 is completely different than in 18.04.  Following any non-18.04 guides won't help.

ptosis - thread-jacking isn't good in these forums.

---

### Post by thewordmonk on 2018-09-30
Hi, i also have Marvell 88E8040 on my laptop & it is not connecting to both wifi & through ethernet. How do i make it functional?

---

### Post by chili555 on 2018-09-30
> **thewordmonk said:**
> Hi, i also have Marvell 88E8040 on my laptop & it is not connecting to both wifi & through ethernet. How do i make it functional?Please see my post #12 above.

---

### Post by ericjmcd on 2018-10-01
I just upgraded from 16.04 to 18.04 and lots of the networking stuff was broken - all interfaces were down and unmanaged

This is what worked for me to get the interfaces/DHCP back up:
```
sudo mv /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf_orig # backup orig
sudo touch /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf # create empty one
sudo systemctl restart NetworkManager # restart service
```

Then DNS was broken.  The complaint in the 17.10 post was actually what fixed it for me:
[https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10](https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10)

The /etc/resolv.conf original soft link pointed to /run/resolvconf/resolv.conf which was apparently wrong.
```
sudo rm /etc/resolv.conf # rm the soft link
sudo ln -s /run/NetworkManager/resolv.conf /etc/resolv.conf # create new soft link to correct resolv.conf
sudo systemctl restart resolvconf # restart service
```

---

