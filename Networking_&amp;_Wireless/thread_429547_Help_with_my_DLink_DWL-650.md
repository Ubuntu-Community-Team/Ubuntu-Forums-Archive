---
title: "Help with my DLink DWL-650"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by m0u53m4t on 2007-05-01
Ok, on the supported cards page ( [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink) ) it says that it will detect it and work fine, but nothing happens. I've just installed feisty and nothing popped up, so I'm running on wired connection atm.

I have also installed ndiswrapper and wine, and have installed the windows drivers with no luck.

Help?

Edit: It recognises my card anyway! I don't understand :p
```
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:40:05:ae:f1:a2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.3.5 multicast=yes wireless=IEEE 802.11b

```
```
owen@Owen-laptop-lin:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "D", "Link DWL-650 11Mbps WLAN Card", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

```

---

### Post by kjkrum on 2007-05-31
Same problem here.  The card is listed in the Device Manager, but not in the output of lspci.

```
kevin@lappy:~$ sudo pccardctl ident
Socket 0:
  no product info available
Socket 1:
  product info: "D-Link", "DWL-650 Wireless PC Card RevP", "ISL37101P-10", "A3"
  manfid: 0x000b, 0x7110
  function: 6 (network)
```

The Restricted Drivers Manager says my hardware does not need any restricted drivers.

---

### Post by soulglo83 on 2007-06-02
I'm installing feisty on a friends laptop (a Dell Latitude D800) and have until now had no problems.  i installed ubuntu 7.04, and was literally putting it back in the bag when i saw that he owned a D-Link DWL-650 Wireless NIC.  I assumed what any good Linux converter would assume; he wants this to work in linux.  So I pop the wireless card in, it lights, and everything appeared honky dory.  

So i issue an ifconfig to make sure I have 2 eth interfaces, and only saw one.  The wired interface I'm using right now.

So next I executed : sudo lshw -C network 
[I]  *-network
       description: DWL-650 Wireless PC Card RevP
       product: ISL37101P-10
       vendor: D-Link
       physical id: 0
       version: A3
       slot: Socket 0
[/I]

So from what I can tell I am in the same or at least a similar boat to you fellas.  The device is recognized, its just not bound to an eth interface.

Has anyone figured out how to get this (supposedly supported) card to work?  Really once we can figure out how to bind it to its own ethx interface, ubuntu can take it from there.  Thanks in advance for any responses, you ubuntu folks (and your distro) rock my sox!

---

### Post by soulglo83 on 2007-06-19
Okay, the problem has been solved (kind of).  

If you upgrade to kernel 2.6.22 you can skip the hostap.ko hex editing from step 3 #the kernel can be found @ [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=99d3184ac7b4e91c88073f474ebe758540b3ad82](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=99d3184ac7b4e91c88073f474ebe758540b3ad82)


The DWL-650 CAN work in Ubuntu, but, because the card does not possess its own firmware (its a software nic!) it needs to be loaded with its firmware which can be found @

1. [http://www.red-bean.com/~proski/firmware/](http://www.red-bean.com/~proski/firmware/)  (download the primary.tar.bz2 and the 1.8.2.tar.bz2 files, then extract the pm010102.hex from the primary.tar.bz2 and the rf010802.hex from the 1.8.2.tar.bz2 archive, extract them to /etc/firmware and then 'sudo chown your_username /etc/firmware/*' and 'sudo chmod 644 /etc/firmware/*').  

2. Add orinoco_cs to your /etc/modprobe.d/blacklist.  Then add hostap and hostap_cs to /etc/modules if they aren't there already.

3. Additionally, you will need to hexedit 2 values in your 'hostap_cs.ko' (back it up first!) so that the card will be recognized (search for the ascii/text string "m000Bc7100" and change it to "m000Bc7110", then search for the hex value "0B000071" and change it to "0B001071" save and exit).  

4. sudo modprobe hostap 

5. sudo modprobe hostap_cs

6. edit your /etc/network/interfaces as follows:

auto wlan0
iface wlan0 inet dhcp
fw_primary /etc/firmware/pm010102.hex
fw_secondary /etc/firmware/rf010802.hex
wireless-essid
wireless-key

7. Reboot! (praying while rebooting might help a lot;))

I finally got the card to work, but after carelessly upgrading my kernel (still think my cat/or a burglar did it, I'm generally not that dumb) I can no longer repeat my success.  It was fun while it lasted, but I recently sprung for a NetGear WG511T V5 (I think) and it rox my sox, no problems whatsoever and great signal strength.  Needless to say, my D-Link DWL-650 Rev P has a new home... in the garbage.

---

