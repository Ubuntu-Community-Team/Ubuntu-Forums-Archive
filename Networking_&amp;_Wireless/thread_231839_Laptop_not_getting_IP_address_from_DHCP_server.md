---
title: "Laptop not getting IP address from DHCP server"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by sessyargc on 2006-08-07
Recently installed Dapper Drake using Xubuntu Alternate. I used the USB HD method since the CDROM of my TP570E has some problems. Got everything to boot properly.

But I noticed that even though my 3Com PCMCIA card was properly detected, it was not getting an IP address from my DHCP server. My DHCP server is a DLINK DI-604. IP address for the laptop/NIC pair is static as configured in the DHCP server. Running Ethereal on my other PC running Windows, I see the packets on the internal network. The laptop issuing a DHCPDISCOVER and the router issuing a DHCPOFFER. I think the packets are correct.

Since last night I have been slowly removing drivers (IrDA, ACPI, APM. etc) on the bootup sequence of the laptop, to no avail.

I have verified that the NIC is working before installing Ubuntu as I was using Windows on the laptop previously. This NIC was also working in other previous Linux distros, even *BSD. I have also verified that the NIC is working when I use the "Rescue" feature from the Ubuntu install CDs! (Now that is really weird)

Hope anyone can provide information.

---

### Post by clint1010 on 2006-08-07
System => Administration => Networking (gnome desktop, not sure about xubuntu)

Make sure your network device is enabled, and then in properties,I have set a static IP address for the machine, and set up static addressing in my dlink router. Gateway address will be the router address. Set the DNS addresses given to you by your ISP on the DNS tab. after this all worked for me

good luck:)

---

### Post by sessyargc on 2006-08-08
thanks <b>clint1010</b>, but i don't want to do it that way. the laptop is roaming from one network to another, not using DHCP will be cumbersome for my purposes. but as a test it is feasible.

reinstalled, using "Server" to minimize clutter. Still NG for my 3C574-TX.

[]   ASIC rev 1,<6>eth0: 3C574-TX Fast EtherLink PC Card at io 0x300, irq 3, hw_addr xx:xx:xx:xx:xx:xx
[]  64K FIFO split 1:1 Rx:Tx, autoselect MII interface.
[] eth0: found link beat
[] eth0: autonegotiation complete: 100baseT-FD selected
[] eth0: interrupt(s) dropped!


hardwired an unused IP to my laptop, pinged a remote pc and got "Destination Host Unreachable". route is valid. network sniff shows that prior to actual ICMP packet, system tries to build up the ARP table. Saw the ARP request and saw the ARP response. "arp -a" on the laptop showed that the h/w address of the remote pc was not received! duh! i decided to hardwire the MAC address of the remote pc via "arp -s". from the laptop pinged the remote pc again. still got nothing. network sniff shows ICMP request packets! this time the remote pc is building its ARP table. saw the ARP request from the remote pc, no ARP response from the laptop. on the remote pc, hardwire the MAC address of the laptop again via "arp -s". from the laptop pinged the remote pc again, got nothing. network sniff showed ICMP request and ICMP reply on the ether! something is really bad here. from the remote pc, pinged the laptop, got no reply. network sniff showed ICMP request only and no ICMP reply from the laptop.

there is no firewall setup on the laptop yet but i flushed it to be sure. all rules are set to accept.

Does anyone have further ideas? Or is this a kernel, or driver issue already?

Is there a way to set the 574 to Half Duplex?

Add: mii-diag and mii-tool does not report any problems with the device.

---

### Post by sessyargc on 2006-08-08
After some searching on the Net I found this old bug report:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=270376](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=270376)

the details in the bug report is consistent to my initial tests.

Add: I just booted up a Knoppix 3.9 livecd, 2.6.11 (Debian) + old pcmcia utilities (not the newer pcmciautils) and my 3C574 is working properly.

---

### Post by RedBoot on 2006-08-08
Interesting posts sessyargc.

I can only suggest basic ideas. Perhaps this bug was fixed in one of the many updates to 6.06. Can you connect to the Inet in some other way and get the laptop updated? Get a more recent CD?

---

### Post by sessyargc on 2006-08-08
the laptop is currently OS-less :) the ISOs were downloaded last July. i'll try to read the securities and devel mailing list later.

i did another check using the kernel and initrd from the CD, used when a user boots the "Rescue" configuration. when i boot to Rescue indeed the card is recognized and works properly. i checked the checksums of the various files (vmlinuz, the kernel modules, etc), and they are different from one another. maybe i'll recompile the kernel and the modules at a later date but i'm thinking that's too much work to get the 3C574 to work.

---

### Post by RedBoot on 2006-08-08
Dude, you're installing alpha level code that's over a year old?

---

### Post by darrenm on 2006-08-08
You mean July 2005 or July 2006?

Try booting without acpi (guess acpi=off as a kernel boot param)

---

### Post by sessyargc on 2006-08-08
**RedBoot** my bad, that should be 07-2006. so it is well within the current release.

**darenm** tried it no change in behaviour. still does not work.

---

### Post by sessyargc on 2006-08-09
FYI. I was not able to resolve the issue thus I've gone back to using my main distro, Slackware. I'm typing this now on the laptop (with the same 3c574) with Slackware installed.

Thanks to all...

---

