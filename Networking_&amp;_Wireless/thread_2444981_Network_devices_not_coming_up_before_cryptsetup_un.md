---
title: "Network devices not coming up before cryptsetup unlock - can't dropbear"
date: 2020-06-07
forum: Networking &amp; Wireless
---

### Post by flipbrad on 2020-06-07
Hi all,

I have a [Lenovo Thinkpad 13]("https://www.lenovo.com/gb/en/laptops/thinkpad/13-series/ThinkPad-13-Windows-2nd-Gen/p/22TP2TX133E") running Ubuntu Server 20.04 (focal fossa).  
I have configured it to have FDE (only /boot is unencrypted) via LVM + LUKS.
I have now followed these steps in order to put dropbear in the initramfs so that I can remotely unlock it over SSH - using the instructions [here]("https://paste.ubuntu.com/p/XJMxqQJwnT/"). 

The device doesn't have an RJ45 port - only a wireless AC card and something that *registers* as an ethernet port on PCI, which I think is something on the motherboard that can serve as an Ethernet device if I connected a proprietary dongle to the device's proprietary "Onelink+" port.  Lspci as follows:

```
lspci | grep -i net
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection I219-V (rev 21)
03:00.0 Network controller: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth (rev 99)

```

I also connect a Dell USB-C -to- RJ45 adapter: [https://www.dell.com/en-uk/shop/dell-network-adapter/apd/470-abbt/networking]("http://The Dell Adaptor- USB-C to Ethernet contains a built-in driver for easy set-up, eliminating the need to install drivers from a CD or download them from another source. The adaptor saves you time by automatically prompting you to install the driver when you plug it in for the first time.") 
To save the USB-C port and use the (probably more robust) USB-A port, I use the USB-C to USB-A adapter (supplied with the Dell adapter) to actually connect this dongle to the laptop.

Both the Wifi card and USB-C-RJ45 adapter work fine (obviously, this being the Server edition of ubuntu, I had to install wpa-supplicant for wifi to work).  
Since the USB works, I've turned off the Wifi by not provisioning it in Netplan configs.  My device connects to the Internet fine over USB-C

[COLOR=#800080]_**PROBLEM**_: Unfortunately, neither Wifi nor the USB-C adapter seem to work before I unlock the encrypted parts of my hard drive during boot.  This means my device can't get an IP via DHCP when dropbear is loading, because it's only trying the weird onboard ethernet adapter - which I don't have a connector for.  This means I can't remote into the box in order to unlock it on boot/reboot.
[/COLOR][COLOR=#800080]
From the dm-crypt password prompt, if I enter the wrong password repeatedly, I drop to an initramfs/busybox prompt.  Running "ip addr list" while in busybox returns just the loopback and internal ethernet device - the machine just appears to be unaware at that point of my Wifi card or the USB ethernet adapter.

[/COLOR]Once I enter the cryptsetup command dm-crypt password, as prompted, the device proceeds to boot; and the Wifi and USB-C ethernet become usable as you'd expect (and now show up in ip addr list).  
Is there a way to make them available earlier in the boot process, e.g. do I have to enable anything for the initramfs?

My journalctl -b output - omitting bits which I guess are irrelevant - can be found here: [https://paste.ubuntu.com/p/XJMxqQJwnT/](https://paste.ubuntu.com/p/XJMxqQJwnT/)
In the log, the first command after I have unlocked the encrypted drive is (...) "kernel: Btrfs loaded, crc32c=crc32c-intel"

Once systemd has renamed the devices,
[LIST]
[*]The USB-C adapter is named enx9cebe8837133 
[*]The wifi card is named wlp3s0.  The driver is iwlwifi. 
[*]The onboard ethernet is named enp0s31f6.  The driver is e1001e 
[/LIST]

If I try to specify an interface name that the initramfs should try and get an IP for, I get an error, "'Error getting hardware address for " enx9cebe8837133": No such device' " (and the same for "wlp3s0" and "wlan0").  The fix suggested here doesn't work: [https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5755653.html](https://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg5755653.html)

For some reason, updating the BIOS using the tools from Lenovo (and a USB key) fails - but with a completely generic error message, so I can't diagnost the issue.  I will in future try different means of flashing an updated BIOS (e.g. burning a CD and using a USB cd drive).  I don't know if the problem lies with the BIOS, though.

Very grateful for any help diagnosing - and ideally, fixing! - the issue!
Thanks in advance.

---

### Post by TheFu on 2020-06-07
Golf clap for even attempting this.  You are braver than me.
Perhaps just having the unlock come from a USB key file would be easier when the system is in a secure location, then using a 2FA - challenge/response solution when away from the box?  LUKS has 8 slots, use a few of them for different conditions.

If the intent is to leave this laptop with someone else, outside your physical control, I suppose you'll need to trust them with the USB key?

BTW, the I219-V should be a fairly new Intel GigE NIC using the igb driver.  I have a router with i210 and a ryzen with i211 NICs. Very compatible, very fast, few interrupts, unlike some, cough, "other" NIC vendors.  Too bad Lenovo didn't provide a port for it. Makes me want to cry when they obviously created the motherboard with the capability, but no port? Ouch.

---

### Post by flipbrad on 2020-06-07
Hi theFu

The onboard ethernet seems to be using e1000e not igb driver.  And where do you see it's an I219-V?

---

### Post by TheFu on 2020-06-07
From the lspci output.  i didn't look up the correct driver, just assumed that all i21x series would use the same one.
[https://www.intel.com/content/www/us/en/support/articles/000005480/network-and-i-o/ethernet-products.html](https://www.intel.com/content/www/us/en/support/articles/000005480/network-and-i-o/ethernet-products.html) says my assumption is wrong.  e1000e is what that link says.
> 
There are three Linux* base drivers for Intel® Gigabit Network Connections:
[LIST]
[*]    igb-x.x.x.tar.gz driver: Supports all 82575/6, 82580, I350, I354, and I210/I211 based gigabit network connections.
[*]    e1000e-x.x.x.x.tar.gz driver: Supports the Intel® PRO/1000 PCI-E (82563/6/7, 82571/2/3/4/7/8/9, or 82583) I217/I218/**I219** based gigabit network adapters.
[*]    e1000-x.x.x.tar.gz driver: Supports Intel® PRO/1000 PCI and PCI-X family of gigabit network connections.
[/LIST]

My i210/i211 are exceptions, it seems.

---

