---
title: "(k)Ubuntu 14.04 RTL8111/8168/8411"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by raiden2332 on 2014-05-15
Hi Guys,

i got no connection in my network manager
Maybe you can help me

```

raiden@Raiden-Notebook:~/Downloads$ sudo lshw -C network
  *-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Logischer Name: eth0
       Version: 0c
       Seriennummer: a4:5d:36:ce:95:a4
       Größe: 10Mbit/s
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.038.00-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       Ressourcen: irq:62 ioport:3000(Größe=256) memory:d0600000-d0600fff memory:d0400000-d0403fff
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: QCA9565 / AR9565 Wireless Network Adapter
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:04:00.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: a4:db:30:da:7b:9e
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A ip=192.168.125.229 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:19 memory:d0500000-d057ffff memory:bf500000-bf50ffff


```

---

### Post by varunendra on 2014-05-17
Welcome to the forums raiden2332!

It seems you are connected via wireless. So is the problem only with the Ethernet port as your thread title suggests? Some description of the problem is always good. :)

If it is indeed just the Ethernet, please tell us what all you have tried so far to fix it.

Have you checked the cable? Tried replacing it with a different, working one?

On software front, initially you may try this -

**1)** Install 'ethtool' -
```
sudo apt-get install ethtool
```

**2)** Try forcing 100 Mbps/full-duplex mode using ethtool -
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
This change will be temporary, will be lost at next boot, so try the connection without rebooting after running the above command.

If it doesn't help, please post the details of the problem and whatever you have tried so far, along with the output of -
```
sudo ethtool eth0
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by raiden2332 on 2014-06-13
thanks for the answers in the german forum there is the solution

```

sudo apt-get install linux-headers-generic build-essential dkms
wget http://ftp.de.debian.org/debian/pool/main/r/r8168/r8168-dkms_8.038.00-1_all.deb
sudo dpkg -i r8168*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-r8169.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo service network-manager restart


```

---

### Post by varunendra on 2014-06-14
Thanks for sharing the solution! Please mark the thread as [SOLVED] (using "Thread Tools" link above the top post) to make the thread more helpful to others. Thanks! :)

---

### Post by family-sklenar-wildcat on 2014-07-08
Hello, thank You!.
 I had recently the same problem using Asrock J1900-ITX board and Trusty. 
It WAS perfect until some recent update, around a day or a few days ago.

Using gigabil lan I know my file sharing DID run at cca 100MB/s (not megabit, real file transfer in megabytes).
I noticed today (8/7/14), that vnc connect is very poor, pausing..  But no link down or any other signs. 
At first I did fight with pstate powertop and so,.. Well at last I came here, and the solution worked perfectly.
I woud bet that new kernel is suspect:
Linux xxxx 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Just a note - do not try that steps using VNC or so at a distant machine, as it breaks the link after modprobe -r 
And do not panic when nothing changes after service restart command, my machine started normal link only past real reboot.

btw, before applying this solution, IPerf  results was cca 57kilobites, up to 100kbit/s,  instead of cca 940 that is normal.
I think some internet-only users would think their internet provider went poor, instead of real reason of damaged drivers.

---

### Post by andrea-costa on 2014-07-14
it works like a charms 
Thank you

---

### Post by 2010-s on 2014-08-30
The [dkms 8.038 changelog]("https://launchpad.net/ubuntu/+source/r8168/8.038.00-1") lists "Use module aliases for PCI IDs supported by r8168 instead of blacklisting     r8169.  (Closes: #739394)".

Instead of:
```
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-r8169.conf
```

You might want to:
```
echo "# map the specific PCI IDs instead of blacklisting the whole r8169 module" | sudo tee -a /etc/modprobe.d/r8168-dkms.conf
echo -e "alias\tpci:v00001186d00004300sv00001186sd00004B10bc*sc*i*\tr8168" | sudo tee -a /etc/modprobe.d/r8168-dkms.conf
echo -e "alias\tpci:v000010ECd00008168sv*sd*bc*sc*i*\t\t\tr8168" | sudo tee -a /etc/modprobe.d/r8168-dkms.conf
```

And for the users of Ubuntu without network manager, instead of: "sudo service network-manager restart" you can use ```
ifconfig p5p1 down;ifconfig p5p1 up
```.

---

### Post by pegngary on 2014-10-18
wget [http://ftp.de.debian.org/debian/pool/main/r/r8168/r8168-dkms_8.038.00-1_all.deb](http://ftp.de.debian.org/debian/pool/main/r/r8168/r8168-dkms_8.038.00-1_all.deb)

This returned a 404 error Not Found.

DOes this solution need an update?

---

### Post by talajic on 2014-11-03
> **raiden2332 said:**
> thanks for the answers in the german forum there is the solution

```

sudo apt-get install linux-headers-generic build-essential dkms
wget http://ftp.de.debian.org/debian/pool/main/r/r8168/r8168-dkms_8.038.00-1_all.deb
sudo dpkg -i r8168*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-r8169.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo service network-manager restart


```

The ftp-link is down. I changed it and used this instead:
```
sudo apt-get install linux-headers-generic build-essential dkms
wget http://launchpadlibrarian.net/173890469/r8168-dkms_8.038.00-1_all.deb
sudo dpkg -i r8168*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist-r8169.conf
sudo modprobe -rfv r8169
sudo modprobe -v r8168
sudo service network-manager restart
```

For some reason the four last lines didn't execute so I ran them again separately.

Then I got a wired connection in the network manager but internet didn't work. 
Then I did what [MariusMatutiae]("http://superuser.com/users/255732/mariusmatutiae") suggestes in [this]("http://superuser.com/questions/756145/ubuntu-14-04-wired-connection-detected-but-no-internet-access") thread, now everything works!

---

### Post by peter_lustig2 on 2015-03-21
[http://ftp.debian.org/debian/pool/main/r/r8168/](http://ftp.debian.org/debian/pool/main/r/r8168/)

Check the version of xxx.deb and change it if necessary

---

### Post by loongseng-kok on 2015-08-08
I have similar issue happened to my Ethernet. 

I am able to connect to my lan, but I have found error message from dmesg "vpd r/w failed. This is likely a firmware bug on this device.....". Based on the pci port number it is referring to Realtek Ethernet Controller.

Checked with lsmod and r8169 is running but not r8168, so I did the steps above and this issue disappeared!

By the way, I did not go to ftp.debian.org to get the required .deb, instead I use "sudo apt-get install r8168-dkms".

Hope this will help if anyone faced the same issue like mine.

---

