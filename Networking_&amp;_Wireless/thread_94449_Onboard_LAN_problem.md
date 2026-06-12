---
title: "Onboard LAN problem"
date: 2005-11-24
forum: Networking &amp; Wireless
---

### Post by ambo on 2005-11-24
Did a bit of a search on the forums to see if anyone else had the same problem as me - but it seems they haven't...

I have an onboard EtherExpress pro100 NIC and a clean install of Breezy 5.10.
The system appears to have detected the device - and the problem that some others mentioned of having 2 modules loaded for the one does not appear to be a problem on my system.
There is a link light on both the NIC and the hub and "sudo mii-tool" returns: "eth0: negotiated 100baseTx-FD flow-control, link ok"

However, the box was unable to connect to the DHCP to obtain a lease. So I set static IP, gw and DNS.
Despite this i cannot ping in or out and theres no sign of the box connecting to the internet gateway and it can't connect to any external resources.

Now this is where it really gets weird - i opened "Network Servers" and the firewall on my doz box began detecting samba packets coming in.
And yet "ifconfig eth0" indicates "RX packets:0..... TX packets:0"

This is my first Ubuntu installation - and i have no idea what is going on...

Any ideas??

---

### Post by mips on 2005-11-24
Lets see your **/etc/network/interfaces** file
Lets see output of **ifconfig -a** command
Lets see output of **mii-diag** command
Lets see output of **mii-tool** command
Lets see output of **route -n** command

What firewall are you running ?
Is it configured correctly ?

You mention you connect to a hub and that is it. 
What does the hub connect to ? 
Where are you attemping to get the DHCP lease from ?
Give us a little sketch/diagram of your network, devices and model numbers might be handy.
Please provide IP addresses/masks for the LAN side equipment all the way from the PC to the Gateway. These addresses should be private so no security risk.

It's easier to troubleshoot something when you have a mental picture in your mind as to what the network looks like.

---

### Post by ambo on 2005-11-24
I'll just retype relevant parts - i'm not a typist :???: 
[QUOTE=mips]Lets see your **/etc/network/interfaces** file[/quote]```
...
mapping hotplug
       script grep
       map eth0

iface eth0 inet static
       address 192.168.0.22
       netmask 255.255.255.0
       ...
       gateway 192.168.0.2
       dns-nameservers 192.168.0.2

auto eth0
```
[QUOTE=mips]Lets see output of **ifconfig -a** command[/quote]```
eth0   Link encap:Ethernet HWaddr...
          inet addr:192.168.0.22....
          inet6....
          UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 tsqueuelen:1000
          RX bytes:0 ... TX bytes:0

lo ....

sit0 ....
```
[QUOTE=mips]Lets see output of **mii-diag** command[/quote]```
Using the default interface 'eth0'
Basic registers of MII PHY #1  3100 782d 02a8 0330 05e1 45e1 0001 0000
 The autonegotiation capability is 01e0
The autonegotiation media type is 100baseTx-FD
 Basic mode control register 0x3100: Auto-negotiation enabled
 You have link beat, and everything is working OK.
 Your link partner advertised 14e1: Flow-control 100baseTx-FD 100baseTx 10baseT-FD 10baseT, w/ 802.3X flow control
     End of transceiver information.
```
[QUOTE=mips]Lets see output of **mii-tool** command[/quote]```
eth0: negotiated 100baseTx-FD flow-control, link ok
```
[QUOTE=mips]Lets see output of **route -n** command[/quote]```
Dest.....
192.168.0.0    0.0.0.0    255.255.255.0   U   0   0   0    eth0
0.0.0.0       192.168.0.2    0.0.0.0    UG    0    0   0    eth0
```

[QUOTE=mips]What firewall are you running ?
Is it configured correctly ?[/QUOTE]The firewall is on the doz2k box - Tiny Personal Firewall - but i'm not really wanting to connect the ubuntu to the doz right now, i just noticed that the firewall detected UDP packets on port 137 from the IP address i set on ubuntu when i opened the network browse window and yet TX and RX packets remained at 0.

[QUOTE=mips]You mention you connect to a hub and that is it. 
What does the hub connect to ? 
Where are you attemping to get the DHCP lease from ?
Give us a little sketch/diagram of your network, devices and model numbers might be handy.
Please provide IP addresses/masks for the LAN side equipment all the way from the PC to the Gateway. These addresses should be private so no security risk.[/QUOTE]Yeah ok sorry - let me elaborate:
10/100 CNet switch with various doz and linux boxes
There is an IPcop gateway that provides DHCP, DNS and routing at 192.168.0.2 and that is fully up as far as i can see... this machine is currently connected through it.
The doz2k box at 192.168.0.20 (255.255.255.0)
And the ubuntu box at 192.168.0.22 (255.255.255.0)
Thats whats on my desk - the others don't really feature in the equation i don't think.

---

### Post by mips on 2005-11-24
Things look ok.

What are the results if you ping your local Ethernet & Loopback interfaces ?

---

### Post by ambo on 2005-11-24
[QUOTE=mips]Things look ok.[/QUOTE]Thats what i thought - thats why i'm confused

Ping to LO is fine, ping to local IP is also fine but "destination host unreachable" to any of the other boxes...

---

### Post by mips on 2005-11-24
[QUOTE=ambo]Thats what i thought - thats why i'm confused[/QUOTE]

lol, that makes two of us.

What is the Linux Device & Vendor ID of that card, what chipset does it use ? There are many versions of this card.

Not to insult you by asking a stupid question but does the card work under windows or another distro ?

---

### Post by mips on 2005-11-24
Or pick your card from this list:
[http://www.intel.com/support/network/sb/cs-008441.htm](http://www.intel.com/support/network/sb/cs-008441.htm)

---

### Post by ambo on 2005-11-24
[QUOTE=mips]Not to insult you by asking a stupid question but does the card work under windows or another distro ?[/QUOTE]Not a stupid question at all - i did think of that to. Got the MB last week and first thing i tested on it was a Asterisk@home installation and that worked fine. Asterisk@home is based on CentOS which is a relative of RedHat.

---

### Post by ambo on 2005-11-24
[QUOTE=mips]What is the Linux Device & Vendor ID of that card, what chipset does it use ? There are many versions of this card.[/QUOTE]The device manager reports the following for the card:
info.linux.driver - e100
info.product - 82801BA/BAM/CA/CAM Ethernet Controller
info.vendor - Intel Corp.
pci.product - ditto info.product
pci.subsys_product - EtherExpress PRO/100 VE
pci.subsys_product_id - 12307
pci.vendor_id - 32902

anything else you need?

---

### Post by mips on 2005-11-24
Nah, I'll try and search the net with that a bit later, going for lunch first...

---

### Post by mips on 2005-11-24
What version of the driver is Ubuntu using ?

I see Intel has version 3.4.14 (7Jul05) available at:
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?strState=LIVE&ProductID=1641&DwnldID=2896&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?strState=LIVE&ProductID=1641&DwnldID=2896&lang=eng)
[ftp://aiedownload.intel.com/df-support/2896/ENG/README.txt](ftp://aiedownload.intel.com/df-support/2896/ENG/README.txt)

Maybe try and build your own and see what gives seeing it doesnt work for you on Hoary or Breezy.

You can also try and play around by turning ACPI & APIC off.

---

### Post by mips on 2005-11-24
Just found this,  [http://www.intel.com/support/network/adapter/pro100/pro100ve/sb/cs-008339.htm](http://www.intel.com/support/network/adapter/pro100/pro100ve/sb/cs-008339.htm)

> **Intel(R) PRO/100 VE Desktop Adapter loads, but doesn't browse the network**
If you install the Intel&#174; PRO/100 VE desktop adapter into a CNR (Communications and Network Riser) slot while the power cord is still attached to the computer, you may create a condition in which the adapter cannot communicate with the network. The link light will light if a network connection is active and the adapter will appear to be fully functional to the system, but you will not be able to send or receive packets.

I tried searching on the vendor & device ID but found nothing. What brand & model motherboard is it ?

---

### Post by ambo on 2005-11-24
> This problem description only applies to the removable Intel PRO/100 VE desktop adapter that plugs into a CNR slot on the motherboard and is sold separately. For Intel adapters that are built into the computer, please contact the computer or motherboard manufacturer for adapter related networking issues.And unfortunately i fall into the second category...

I found this [http://ubuntuforums.org/showthread.php?t=58840&page=2]("http://ubuntuforums.org/showthread.php?t=58840&page=2") Note post #17 - and tried something along those lines with the Asterisk@home distro that had been working - but no luck.

Then i choose a last resort that i had to do on a RedHat server previously:
"After fighting with an onboard LAN adapter for many hours - i popped in a PCI LAN adapter..."
So i went and stole a PCI adaptor out of another box... and hey presto - DHCP lease in less than a second and now it seems to be working like a charm!

Can anyone explain why Linux is soooo anti onboard LAN (in my experience)

---

### Post by mips on 2005-11-24
[QUOTE=ambo]Can anyone explain why Linux is soooo anti onboard LAN (in my experience)[/QUOTE]
No idea, what motherboard do you have ???

Is your card removable ? If not then it might be the VM version.

Strange thing is I have two onboard LAN adapders, Marvell 8053 10/100/1000 (PCI-E bus) & Vitesse 8201 10/100/1000 (PCI bus) and both of them work fine.

---

### Post by mips on 2005-11-24
Have you tried disabling ACPI & APIC in the grub config ?

---

### Post by ambo on 2005-11-24
[QUOTE=mips]Is your card removable ? If not then it might be the VM version.[/QUOTE]Nope the port is completely integrated into the motherboard. My Linux knowledge is sometimes a little patchy - what is "the VM version"?
[QUOTE=mips]Have you tried disabling ACPI & APIC in the grub config ?[/QUOTE]No - never attempted to tweak a grub config. What are ACPI & APIC? Rings a bell as power management systems...

---

### Post by mips on 2005-11-24
[QUOTE=ambo]Nope the port is completely integrated into the motherboard. My Linux knowledge is sometimes a little patchy - what is "the VM version"?
No - never attempted to tweak a grub config. What are ACPI & APIC? Rings a bell as power management systems...[/QUOTE]

VM version is basically the same as the VE version except it is not a removable card from what I understand, onboard integrated.

Yes ACPI & APIC has something to do with power management, not something I'm very clued up on but it seems to solves some peoples problems.

---

