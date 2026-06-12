---
title: "Acer Aspire 5520 wireless"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Aerotha on 2009-03-12
Hey,
I just recently got ubuntu, and I have an issue all my drivers work except my wireless one...I have looked around and there were some guides of it but it required weird tools and was very complex...is there a way to do get my wireless back easily?

---

### Post by Aerotha on 2009-03-14
Nobody has any Idea?

---

### Post by mikewhatever on 2009-03-14
What's the problem exactly? What's your wireless card model?

---

### Post by Aerotha on 2009-03-14
> **mikewhatever said:**
> What's the problem exactly? What's your wireless card model?

How do I check?

---

### Post by mikewhatever on 2009-03-14
Applications->Accessories->Terminal

type in **sudo lshw -C network**, enter the password and post the output here.

---

### Post by Aerotha on 2009-03-15
Okay it said
> 
      description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:4e:dd:8c
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:95:78:f2:4a:45
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

So I think it's the AR242x?

---

### Post by mikewhatever on 2009-03-16
It looks like whenever there is an undetected wireless, the hardware involved is almost always from Atheros or Broadcom.
[http://www.google.co.il/search?q=ubuntu+AR242x+802.11abg+Wireless+PCI+Express+Adapter&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.co.il/search?q=ubuntu+AR242x+802.11abg+Wireless+PCI+Express+Adapter&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by acreech on 2009-03-16
I also have that wireless card if you go to your synaptic package manager (system>admin>synaptic package Manager) install the linux-backports-modules-intrepid-generic 

This is how I have gotten my card to work. 

You may need to log out then back in after installing the package.

---

### Post by Aerotha on 2009-03-16
> **acreech said:**
> I also have that wireless card if you go to your synaptic package manager (system>admin>synaptic package Manager) install the linux-backports-modules-intrepid-generic 

This is how I have gotten my card to work. 

You may need to log out then back in after installing the package.

I guess I did it wrong :S
I installed that and my wireless doesn't work still and my graphics card went on the fritz.

---

### Post by acreech on 2009-03-16
> **Aerotha said:**
> I guess I did it wrong :S
I installed that and my wireless doesn't work still and my graphics card went on the fritz.

On a 32 bit system the following method worked for me with the wireless. This method did not work on my 64 bit system. Enter these commands into the terminal:


 > sudo -s

Then
 > echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist 

then
> apt-get install ndiswrapper* 

then
> wget ftp ://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip 

(remove the space between ftp & :, i.e. [ftp://)](ftp://))

then
 > unzip Wireless* 

Then
 > cd Atheros 

then
 > unzip HR* 

then
>  ndiswrapper -i net5211.inf

Then
 > echo 'ndiswrapper' >> /etc/modules 

If this don't work for you then the problem is out of my league. 

Good Luck

acreech

---

### Post by Aerotha on 2009-03-16
Thank you, I got it working!
Can A mod please close this?

---

