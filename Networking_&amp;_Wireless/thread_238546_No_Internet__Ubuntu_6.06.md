---
title: "No Internet / Ubuntu 6.06"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by Captain Strobelight on 2006-08-17
Hello

lspci -v shows my ethernet connection is there, but I cannot access the internet.  I have tried both DHCP and Static IP Address, using the numbers I get from Windows x64.  Nothing so far has worked.

Here is the info on this motherboard.

Intel 845GL chipset
Memory Controller Hub (MCH)
I/O Controller Hub (ICH4) for PCI 2.2 bus
Integrated 10/100 Mbit LAN controller
SMBUS device support

When I run the command "sudo lspci -v" the ethernet area shows this info. 

0000:02:08.0 Ethernet Controller: Intel Corporation 82801DB PRO/100 VE (LOM) 
Ethernet Controller (rev 81) 
Subsystem: IBM NetVista A30p
Flags: bus master, medium devsel, Latency 66, IRQ 217
Memory at c0100000 (32-bit, non-prefetchable) [size=4k]
I/O ports at 2000 [size=64]
Capabilities: [dc] Power Management version 2

I tried a few of the tricks on these forums ( and others, all with no success.  The internet is there, I am on it now with my x64 rig.  But, Ubuntu hasn't been recognizing it.  

Any help would be appreciated.  Sorry if it has been resolved before, I have been searching for the fix for 4 hours now and didn't come across anything that worked.

Forgot to add, it's an onboard ethernet adapter.  I don't have access to a ethernet card, currently.

---

### Post by gnutech on 2006-08-18
What other information does ubuntu have on your interface?

Try these commands:

sudo -i
<password>

lsmod
<do you see your interface module loaded?  I think in your case it is either e100 or eepro100>

cat /proc/interrupts
<do you see an irq associated with your interface?>

ifconfig
<does this show your ethx with ip and netmask?  You may need to use the -a option.  does it have the irq and base address listed at the bottom of your ethx?>

route
<do you have a default route for your ethx?>

Post the information you find and read through this:

[http://www.tldp.org/HOWTO/Ethernet-HOWTO.html](http://www.tldp.org/HOWTO/Ethernet-HOWTO.html)

Respectfully,


Gary

---

