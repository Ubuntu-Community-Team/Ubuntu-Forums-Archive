---
title: "Belkin Card on Gutsy 64bit"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Irondayz on 2008-04-19
Hi,

I am installing a Belkin Wireless G Desktop card (F5D7000 ver 7000) and cannot get my network card to appear under System->Administration->Network.  I am running the Gutsy Gibbon 64bit version.  

I followed the tutorial here: [https://help.ubuntu.com/community/WifiDocs/Device/F5D7000#head-74fc39c78e5ff5412c06b619827729e272bdf9e8]("https://help.ubuntu.com/community/WifiDocs/Device/F5D7000#head-74fc39c78e5ff5412c06b619827729e272bdf9e8")

I was successful up until I had to to manually select the broadcast/receive frequency.  I do not know why the interface is not listed when I run the command "sudo lshw -C network"  

Here are the results of that command:
**sudo lshw -C network**
 *-network
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ndiswrapper latency=64 maxlatency=64 mingnt=32

**lspci**
05:02.0 Ethernet controller: Belkin Unknown device 700f (rev 20)

**sudo ndiswrapper -l**
driver installed
        device (1799:700F) present

**iwconfig**
lo        no wireless extensions.
eth0      no wireless extensions.

**sudo iwlist scan**
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

I also checked Ubuntu support for this driver here (I used ndiswrapper, with the driver I found on the cd that came in the box.)
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

Any ideas on why this is not appearing in my System->Administrator->Network? Or why my card does not have an interface listed?

Thanks for any help!

---

### Post by lanceros217 on 2008-04-20
Perhaps this could help...

I had the hardest time trying to get my belking 54g f5f7011 wireless card working on ubuntu 8.04 untill i gave up and had to downgrade to ubuntu 7.10 (I literally spent weeks trying all of the guides found here on the forums which used ndiswrapper and obviously the windows drivers). So anyways, after I installed 7.10, the card was still not recognized but, I noticed that "bcm43xx" (which is the chipset used in the card) was listed under the restricted drivers managers, so somehow I came up with the solution of installing a the   bcm43xx-fwcutter package from the synaptic package manager, and that did it for me. I don't even have to use ndiswrapper and ubuntu automatically recognizes my card. In fact it also even recognizes my linksys WPC54GS wireless card (because it also has the bcm43xx chipset). 

All without a hitch and without having to use the command terminal.

---

