---
title: "dlink dwl-520 e1 and hostap"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by kkvenkit on 2005-04-18
I'm trying to get my dlink dwl-520 e1 wireless nic to work. In the past (using mandrake) I used hostap to use the nic. But now I'm having serious issues, partly because I'm new to ubuntu.

There are some good instructions at [http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html](http://home.columbus.rr.com/andrewbarr/linux/dwl520e1.html). I followed these in the past with success so I tried to do the same here.

I moved to using the -k7 kernel as my machine is an Athlon. hostap also requires the kernel to be compiled with CONFIG_NET_RADIO=y, which the -k7 kernel satisfies (the -386 does not).

I've tried to use the latest version of hostap-driver and hostap-utils (0.3.7) but the subsequent 'modprobe hostap_pci' hangs my computer. I then tried a version I'd used in the past (with mandrake) -- 0.2.4, and then 0.2.6 -- and am then able to insert the module. But the flashing of the firmware (using hostap_fw_load) then hangs the machine.

So then I installed hostap-source 1:0.2.6-1 and hostap-utils 1:0.2.6-1 (from the universe?). I was able to build hostap-source and insert the module. Flashing the card by hand results in the machine hanging. But, following the instructions in the readme that came with hostap-utils, I edited /etc/network/interfaces and added the following:

auto wlan0
iface wlan0 inet dhcp
    hostname foo
    fw_primary /etc/firmware/pm010102.hex
    fw_secondary /etc/firmware/rf010800.hex

A subsequent reboot makes the wlan0 (and wifi0) devices appear, and iwconfig reports some reasonable info. However, I can't get an IP (using dhcp) for the interface. And setting the IP statically doesn't let any traffic through either. So there's obviously still something wrong here.

I'm out of ideas and growing frustrated. Any help would be greatly appreciated. 

Cheers
kkvenkit

---

### Post by kkvenkit on 2005-04-25
I finally got the card to work. I wrote some documentation on it here: [http://www.ubuntulinux.org/wiki/DLinkDWL520E1](http://www.ubuntulinux.org/wiki/DLinkDWL520E1)

---

### Post by Reality on 2005-05-01
Anyone know if it's possible to do this without an alternate internet connection? The instructions above involve wgetting a few files.

---

### Post by thedead on 2005-06-15
can someone please tell how how I update the kernal, i am looking in synaptic and see nothing!

---

### Post by greenwom on 2005-09-27
[QUOTE=kkvenkit]I finally got the card to work. I wrote some documentation on it here: [http://www.ubuntulinux.org/wiki/DLinkDWL520E1](http://www.ubuntulinux.org/wiki/DLinkDWL520E1)[/QUOTE]

I have the same card and followed the instructions.  The system now identifies the card but I also get a wifi0 and a wlan0 interface.  iwconfig properly identifies the card but when I enter a essid and channel I get nothing "cannot access the network"

Where should I go from there?

---

