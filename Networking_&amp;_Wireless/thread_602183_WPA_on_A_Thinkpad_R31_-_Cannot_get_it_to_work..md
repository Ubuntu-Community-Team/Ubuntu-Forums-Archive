---
title: "WPA on A Thinkpad R31 - Cannot get it to work."
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by ruggy on 2007-11-04
I've been trying to setup WPA on my Thinkpad R31, but have had no luck whatsoever.  I cannot use WEP, because it screws up my Mac on the network.  I am following these setups:

[http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html](http://www.ubuntugeek.com/enable-wpa-wireless-access-point-in-ubuntu.html)

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

Reboot your system or use the following command

sudo /etc/init.d/dbus restart

However, I keep on going over them, but it just does not work.  The WPA option does not show.  Can anyone recommend another way of setting up WPA on Ubuntu?

Much thanks in advance.

---

### Post by Lambert on 2007-11-04
What version of ubuntu do you have installed?
What is the wireless device you have?

To find your device type this command.

```

sudo lshw -C network

```

---

### Post by ruggy on 2007-11-04
Hi, I am using the latest version of 7.04 with all updated packages installed.  For the network, I have the following listed:

sudo lshw -class  network
  *-network:0 DISABLED    
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 5
       bus info: pci@01:05.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 latency=32 link=no multicast=yes
       resources: iomemory:80300000-80300fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 42
       serial: 00:0a:e4:41:d8:01
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: iomemory:80100000-80100fff ioport:7000-703f irq:11

---

### Post by ruggy on 2007-11-05
Anyone?  Help please??

---

### Post by wieman01 on 2007-11-05
It says "Disabled":
> *-network:0 DISABLED 
Is there a button or something to turn it on? Could you please boot into Windows, enable the wireless device (through network connections), then restart and boot into Ubuntu? The device isn't turned on.

---

### Post by ruggy on 2007-11-05
Hi, 

I only have Linux on the thinkpad, nothing else.  Is there a code I can use to turn the port on?  Its built into the thinkpad, no button to turn it on.

---

### Post by wieman01 on 2007-11-05
> **ruggy said:**
> Hi, 

I only have Linux on the thinkpad, nothing else.  Is there a code I can use to turn the port on?  Its built into the thinkpad, no button to turn it on.
Mmm... the BIOS perhaps? Or is there any button you key combination that you can press?

---

### Post by ruggy on 2007-11-05
Nope, everything is open.  I can reset the bios though.

---

### Post by ruggy on 2007-11-06
No other recommendations?

---

### Post by Lambert on 2007-11-06
> **ruggy said:**
> No other recommendations?

Install the package linux-wlan-ng

---

### Post by wieman01 on 2007-11-06
> **Lambert said:**
> Install the package linux-wlan-ng
Can you let us know what it does?

---

### Post by Lambert on 2007-11-06
> **wieman01 said:**
> Can you let us know what it does?

linux-wlan-ng is a set of drivers and utilities that is intended to
provide the full range of IEEE 802.11 MAC management capabilities for use
in user-mode utilities and scripts.  The package currently supports the
Intersil 802.11b Prism2, Prism2.5, and Prism3 reference designs for
PCMCIA, PCI, and USB. Additionally, the package includes support for the
PLX9052 based PCI to PCMCIA adapter with a few different PCMCIA cards.

The standard Ubuntu kernel already contains all necessary drivers. This
package ships utilities and integration scripts to make above cards work
seamlessly with the Ubuntu network infrastructure.

---

### Post by wieman01 on 2007-11-06
> **Lambert said:**
> linux-wlan-ng is a set of drivers and utilities that is intended to
provide the full range of IEEE 802.11 MAC management capabilities for use
in user-mode utilities and scripts.  The package currently supports the
Intersil 802.11b Prism2, Prism2.5, and Prism3 reference designs for
PCMCIA, PCI, and USB. Additionally, the package includes support for the
PLX9052 based PCI to PCMCIA adapter with a few different PCMCIA cards.

The standard Ubuntu kernel already contains all necessary drivers. This
package ships utilities and integration scripts to make above cards work
seamlessly with the Ubuntu network infrastructure.
Wow, great! Did not know that. Good to know indeed.

---

### Post by ruggy on 2007-11-08
Much appreciated response.  Can you tell me the exact command I should use in terminal?

---

### Post by wieman01 on 2007-11-08
According to Lambert it would be:
> sudo apt-get install linux-wlan-ng
Then restart the PC.

---

### Post by ruggy on 2007-11-09
Hi, 

Thanks again for the help.  It sees the other non-WPA wireless networks now (live in a apt building), but not my WPA.  Is there something else I need to do to have Ubuntu see my WPA network?

---

### Post by ruggy on 2007-11-09
I upgraded to 7.10 and it sees my network adapter finally, but it is asking me for a WEP password and not a WPA password.  The network is setup on WPA2 Personal.  Works fine on the mac, just not sure why it thinks it is WEP instead of a WPA2 Personal security.

---

### Post by wieman01 on 2007-11-09
> **ruggy said:**
> I upgraded to 7.10 and it sees my network adapter finally, but it is asking me for a WEP password and not a WPA password.  The network is setup on WPA2 Personal.  Works fine on the mac, just not sure why it thinks it is WEP instead of a WPA2 Personal security.
Then the current driver does not support WPA / WPA2. You might have to upgrade it to a more recent version or install "ndiswrapper" and use the Windows driver.

---

### Post by ruggy on 2007-11-09
Hi, 

I can do that.  How do I install ndiswrapper and have it use the Windows driver instead of the one within Ubuntu?

---

### Post by wieman01 on 2007-11-10
> **ruggy said:**
> Hi, 

I can do that.  How do I install ndiswrapper and have it use the Windows driver instead of the one within Ubuntu?
You could try the tutorial in my signature. Post there if you need support.

---

