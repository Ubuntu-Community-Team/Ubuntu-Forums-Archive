---
title: "Network card not working"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by Alun on 2005-05-07
I have installed 5.04 and during the install process I attempted to have my network setup automatically but it didn't work so I proceeded by selecting "do not configure at this time".

Now, once loaded to the desktop, when I go into Network Settings in "Control Center" (Kubuntu) the card shows up but is disabled. Clciking on "enable interface" results in a green tick that only lasts for a fraction of a second before reverting to the Disabled icon.

The machine is (I think) a Compaq Evo D300. The card is an onboard intel chipset.

lspci reports:
Intel Corp. 82801BA/BAM/CA/CAM Ethernet Controller

lsmod shows that the e100 module is loaded

I tried the install before with a realtek 8139 chipset PCI card installed as well and the results were the same which makes me wonder whther the problem lies elsewhere.

If anyone can give me some help to get this card working it would be greatly appreciated.

Thanks,
Alun

---

### Post by defkewl on 2005-05-07
I think that your network card is detected. You have to setup your NIC manually because when it setup automtically it uses DHCP to assign the IP address to your card. CMIIW

---

### Post by kleeman on 2005-05-07
What does ifconfig show?
If eth0 is listed try
sudo ifup eth0 and report output...

---

### Post by Alun on 2005-05-07
I have a DHCP server setup.

Also, the output from ifconfig lists only the local looback, no eth0.

Performing ifconfig eth0 does not show any ip address (v4 or v6).

---

### Post by kleeman on 2005-05-07
What does
sudo ifup eth0 

show?

This is the command that attempts to bring up the interface using dhcp in your case.

---

### Post by Alun on 2005-05-07
sudo ifup eth0
"Ignoring unknown iterface eth0=etho"

btw the only mention of eth0 in /etc/network/interfaces is

mapping hotplug
               script grep
               map eth0

---

### Post by kleeman on 2005-05-07
That looks very different to what I have and what it says you need in the Debian networking manual for dhcp. 

[http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html)         (see 10.6.2)

The manpage for  interfaces explains the syntax of this file but you may need to study it carefully to figure out what is happening for your case. Maybe it has something to do with your install sequence.

My lines are:

# The primary network interface
auto eth0
iface eth0 inet dhcp

Perhaps you could try backing up your file and replacing your lines by mine and then retrying 

sudo ifup eth0

---

### Post by kleeman on 2005-05-07
Looking further into the Debian networking document I quoted above  I found your lines (Section 10.10.2). It appears that the lines are designed to assign a hotplugged device (like a laptop network pcmcia card) to eth0. This does not sound like your setup at all so my advice above stands- change /etc/network/interfaces

---

### Post by Alun on 2005-05-08
I made the changes and on reboot the system paused for a while at "*Configuring network interfaces..." which it didn't before.

The interface still shows up as disabled in Control Center and ifup eth0 says:

ifup: interface eth0 already configured

eth0 now appears in ifconfig though without an ipv4 address.

On a aside note though, when I go to Control Center and hit "Administrator Mode" in order to try and enable the interface I get asked for a password as usual and then after I enter it I get dumped to the main Control Center page, rather than into the network settings. When I navigate to Network Settings it appears as though I have not authenticated for Administrator Mode....

---

### Post by kleeman on 2005-05-08
OK now it looks like dhcp is not assigning an ip address to your nic. To confirm this do
sudo ifdown eth0 (to take the interface down)

then

sudo ifup eth0

and report output (this may show why dhcp isn't working)

---

### Post by bigbangbigbigbang on 2005-05-08
[QUOTE=Alun]sudo ifup eth0
"Ignoring unknown iterface eth0=etho"

btw the only mention of eth0 in /etc/network/interfaces is

mapping hotplug
               script grep
               map eth0[/QUOTE]

Hi

you have to disable these lines (all three of them) and let it only with the good old:

# The primary network interface
auto eth0
iface eth0 inet dhcp

These two definitions do not work together, either you use hotplug configuration (which sometimes does not work) or let the initscript configure  it for you (2nd definition)

cheers

---

### Post by Alun on 2005-05-09
[QUOTE=kleeman]
sudo ifup eth0

and report output (this may show why dhcp isn't working)[/QUOTE]

ifup: interface eth0 already configured

---

### Post by Alun on 2005-05-09
[QUOTE=bigbangbigbigbang]Hi

you have to disable these lines (all three of them) and let it only with the good old:

# The primary network interface
auto eth0
iface eth0 inet dhcp

These two definitions do not work together, either you use hotplug configuration (which sometimes does not work) or let the initscript configure  it for you (2nd definition)

cheers[/QUOTE]

Yeah, thanks. I had already done that. Sorry that I didn't make that clear before.

---

### Post by kleeman on 2005-05-09
Did you bring the interface down first with ifdown (see above)? The bootup starts it up but fails for some reason so that's why you need to bring it down and then up to get the error messages... (you migh also want to chack dmesg for messages as well...)

---

### Post by Gandalf on 2005-05-09
your network interface is already up, you need only to run DHCP on it
sudo dhclient eth0

---

### Post by Alun on 2005-05-09
[QUOTE=kleeman]Did you bring the interface down first with ifdown[/QUOTE]

no :(

ifdown eth0:

cp: cannot stat '/etc/resolv.conf': No such file or directory
run-parts: etc/network/if-down.d/postfix exited with return code 1
Internet Systems Consortium DHCP Client v3.01
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit heep://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on   LPF/eth0/00:02:a5:fd:4e:2b
Sending on     LPF/eth0/00:02:a5:fd:4e:2b
Sending on     Socket/fallback

followed by ifup eth0:

Internet Systems Consortium DHCP Client v3.01
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit heep://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on   LPF/eth0/00:02:a5:fd:4e:2b
Sending on     LPF/eth0/00:02:a5:fd:4e:2b
Sending on     Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
no DHCPOFFERS received.
No working offers in persisten database - sleeping.
cp: cannot stat '/etc/resolv.conf': No such file or directory
run-parts: etc/network/if-down.d/postfix exited with return code 1

"sudo dhclient eth0" gives same results as above...

Anything in particular I should be looking for in dmesg?

---

### Post by Gandalf on 2005-05-09
[QUOTE=Alun]no :(

ifdown eth0:

cp: cannot stat '/etc/resolv.conf': No such file or directory
run-parts: etc/network/if-down.d/postfix exited with return code 1
Internet Systems Consortium DHCP Client v3.01
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit heep://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on   LPF/eth0/00:02:a5:fd:4e:2b
Sending on     LPF/eth0/00:02:a5:fd:4e:2b
Sending on     Socket/fallback

followed by ifup eth0:

Internet Systems Consortium DHCP Client v3.01
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit heep://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on   LPF/eth0/00:02:a5:fd:4e:2b
Sending on     LPF/eth0/00:02:a5:fd:4e:2b
Sending on     Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
no DHCPOFFERS received.
No working offers in persisten database - sleeping.
cp: cannot stat '/etc/resolv.conf': No such file or directory
run-parts: etc/network/if-down.d/postfix exited with return code 1

Anything in particular I should be looking for in dmesg?[/QUOTE]
 your /etc/resolv.conf isn't there
sudo gedit /etc/resolv.conf
put in it
nameserver ISP_DNS_CACHE_IP_ADDRESS

---

### Post by Alun on 2005-05-09
Same as before but without the two error lines above "Internet Systems Consortium..."

---

### Post by Gandalf on 2005-05-09
[QUOTE=Alun]Same as before but without the two error lines above "Internet Systems Consortium..."[/QUOTE]
 then your dhcp system is not working properly,
what is the output of arp -a

---

### Post by Alun on 2005-05-09
[QUOTE=Gandalf]then your dhcp system is not working properly,
what is the output of arp -a[/QUOTE]

nothing at all.

what does the "unknown hardware address type 776" message mean?

Should I try setting an IP manually then?

---

### Post by Gandalf on 2005-05-09
[QUOTE=Alun]nothing at all.

what does the "unknown hardware address type 776" message mean?

Should I try setting an IP manually then?[/QUOTE]
 well apparently your DHCP server is not working or just refusing your MAC address try setting up the ip manually
edit /etc/network/interfaces
replace the
iface eth1 inet dhcp

with

iface eth1 inet static
	address YOUR_DESIRED_IP_ADDRESS
	netmask YOUR_NET_MASK
	gateway YOUR_GATEWAY
	dns-nameservers SAME_NAMESERVERS_ENTERED_IN_/etc/resolv.conf


and then

sudo ifdown -a && sudo ifup -a

---

### Post by Alun on 2005-05-09
No errors this time but I can't ping other computers on the network.
"Destination Host Unreachable"

If I unplug the cable from the machine and stick it in my powerbook and assign a manual address (or use DHCP) it works straight away with internet browsing and eveything...

---

### Post by Gandalf on 2005-05-09
[QUOTE=Alun]No errors this time but I can't ping other computers on the network.
"Destination Host Unreachable"[/QUOTE]
 can i ask you a question, did you ever get internet on this box?? i mean on XP for example,
because this isuue can be from serval reason,
bad cable is used (straight instead of cross-over)
bad router port
NIC not correctly identified (i doubt this one, because ifup eth0 is not wrong)
bad IP address, bad NETMASK, bad GATEWAY

---

### Post by Alun on 2005-05-09
I have had internet with FreeBSD. Not tried with XP or other windows though.
The (crossover) cable is connected to a windows XP machine and is part of a network bridge. 
As I said (in my edited post above), this configuration works fine from the powerbook. (using same IP, gateway, netmask, dns etc) 
I had a second network card in the machine before and was getting the same error so I removed it and reinstalled ubuntu with just the one card but the behaviour did not seem to change. Perhaps the card isn't getting recognised, though as you said this doesn't seem to be the case.

Thanks for your help with this issue.

---

### Post by Gandalf on 2005-05-09
[QUOTE=Alun]I have had internet with FreeBSD. Not tried with XP or other windows though.
The (crossover) cable is connected to a windows XP machine and is part of a network bridge. 
As I said (in my edited post above), this configuration works fine from the powerbook. (using same IP, gateway, netmask, dns etc) 
I had a second network card in the machine before and was getting the same error so I removed it and reinstalled ubuntu with just the one card but the behaviour did not seem to change. Perhaps the card isn't getting recognised, though as you said this doesn't seem to be the case.

Thanks for your help with this issue.[/QUOTE]
 ok if it's possible, plug your NIC in another windows box to see if the card itself is defected

---

### Post by Alun on 2005-05-09
[QUOTE=Gandalf]ok if it's possible, plug your NIC in another windows box to see if the card itself is defected[/QUOTE]
 The card I am currently trying to configure (on the ubuntu box) is an onboard intel chipset.
The secondary card that would not work before (that I removed before reinstalling) is currently in the windows box, with a crossover cable linking it to the ubuntu machine :)

This card now seems to be working fine under windows (and has done so before).

---

### Post by Gandalf on 2005-05-09
well i stop here then, try borrow a card, or buy a cheap card, because i don' think the problem is from ubuntu :(

---

### Post by Alun on 2005-05-09
Wouldn't the fact that the card works in FreeBSD mean that the problem, if not specifically ubuntu is at least related to the driver rather than a physical card problem?

Thanks again for helping me try and diagnose this problem.

I will try putting the secondary card back in (a Realtek 8139 chipset) and configuring it as has been suggested above and see waht happens this time.

---

### Post by hansdezwart on 2005-05-10
I seem the have a near exact copy as Alun. I also chose not to configure the network during installation (I was doing it in the train).
My network card works perfectly fine when I boot in WinXP, so does the DHCP server. I have tried in two different locations now and have the same problem and error messages.

It must have something to do with the installer. I think I will try to install Ubuntu again (can that be done? Ubuntu over Ubuntu) with a network cable plugged in. Maybe that will solve the problem. If so, I will write that down here.

Regards,

Hans de Zwart

---

### Post by Alun on 2005-05-11
[QUOTE=hansdezwart]I seem the have a near exact copy as Alun. I also chose not to configure the network during installation (I was doing it in the train).
My network card works perfectly fine when I boot in WinXP, so does the DHCP server. I have tried in two different locations now and have the same problem and error messages.

It must have something to do with the installer. I think I will try to install Ubuntu again (can that be done? Ubuntu over Ubuntu) with a network cable plugged in. Maybe that will solve the problem. If so, I will write that down here.

Regards,

Hans de Zwart[/QUOTE]
 Be interested to hear how you get on Hans. Keep this thread updated with your findings.

---

### Post by mkeller on 2005-05-11
Hi!

Same problem here... 

Try to add the kernel parameter "noapic", which should fix some buggy IRQ handling on your hardware... (I found that here: [http://ubuntuforums.org/showthread.php?t=30714](http://ubuntuforums.org/showthread.php?t=30714) )

It worked for me! 


HTH

Michael

---

### Post by Alun on 2005-05-13
[QUOTE=mkeller]Hi!

Same problem here... 

Try to add the kernel parameter "noapic", which should fix some buggy IRQ handling on your hardware... (I found that here: [http://ubuntuforums.org/showthread.php?t=30714](http://ubuntuforums.org/showthread.php?t=30714) )

It worked for me! 


HTH

Michael[/QUOTE]
 hmmm. I added the noapic optiopnto menu.lst and ran update-grub and restarted.
There is a message saying something about 'Skipping IOAPIC probe due to 'noapic' option.' but there are still a lot of references to APIC in dmesg...

And of course, the NIC still refuses to work. Exact behaviour as before.

---

### Post by brannala on 2005-05-20
I was having similar problems with a broadcom ethernet card on a Acer Ferrari 3400. I already added apm=off and acpi=noirq to the kernal commands in menu.lst and that fixed the problem.

---

### Post by rubixDead on 2005-06-03
I am having the same exact problem as you guys, but I have an integrated SiS900 nic. 
Alun, I am wondering if you were able to get yours working, I have tried all the suggestions made on this thread (all the kernel paramenters) still to no avail, the only thing I have left to do is find another NIC and try that.

---

### Post by angst7 on 2005-07-08
[QUOTE=brannala]I was having similar problems with a broadcom ethernet card on a Acer Ferrari 3400. I already added apm=off and acpi=noirq to the kernal commands in menu.lst and that fixed the problem.[/QUOTE]

Howdy.  Just ran into this problem (identical symptoms) on a older Dell Latitude CPt (330 Mhz Celeron) with a Cabletron Wireless PCMCIA card (oronco drivers).  Those two kernel options fixed the network problem, and got the sound working.  

Thanks!

---

