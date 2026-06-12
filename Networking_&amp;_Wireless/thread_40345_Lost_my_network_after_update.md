---
title: "Lost my network after update"
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by 8oluf7 on 2005-06-08
System Specification:

Antec Aria SFF case and PSU
MSI K8NM FISRB motherboard (MATX with nForce3/250 chipset and RTL-8129 Gigabit Ethernet)
Athlon 64 3200+ CPU
2 x 512MB Kingston PC3200 RAM (on MSI approved list)
160GB Seagate ST3160827AS SATA hard drive
NEC ND3500A CD-RW/DVD-RW
Connect3D 256MB ATI Radeon 9550 8xAGP graphics card (passive cooling)
NEC 1970NX 19" TFT monitor (connected via DVI and running at the default 1280x1024 resolution)

I was having problems with the system failing to find the network (the first symptom was that it couldn't synchronise the hardware clock to the one at the ubuntu address). Adding 'noapic' after 'boot' in the Grub menu appeared to fix the problem.

Today I've installed the latest kernel update. Grub was rewritten and the 'noapic' switch removed; the network connection disappeared at a most inconvenient time in a work session. Now, **although I've reinstated the 'noapic' switch**  I can't connect to my local network so - no shared files, no printer, and no internet.  ](*,)

I have tried the third item in the grub menu, which I thought 'rolled-back to the previous kernel, with noapic - no success. 

Is there a problem with the latest kernel update, or was I wrong in thinking that I had solved the problem?

---

### Post by alastair on 2005-06-08
Look in your system logs for ethernet/network stuff - all of it i.e. module load e.g. 

e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
....

Look for warnings, errors etc. related to networking.

Look through /var/log/syslog (or "dmesg" output).

Then, when logged in :

ifconfig -a
route -n

---

### Post by gasparov on 2005-06-09
[QUOTE=alastair]Look in your system logs for ethernet/network stuff - all of it i.e. module load e.g. 

e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
....

Look for warnings, errors etc. related to networking.

Look through /var/log/syslog (or "dmesg" output).

Then, when logged in :

ifconfig -a
route -n[/QUOTE]
 Same problem here with realtech and NF3 chipset as well,everything seems recognized and loaded ifconfig -a and route -n are as usual .Switching from static to dhcp brings to no DHCP get discovered,using another nic doesn't solve the problem.2 kernel updates and 2 network problems..is there anyway to swith back?I'll try the noapic nolapic thing and the 386 kernel but the computer is remote:remote comnputer + no net=impotence

---

### Post by gasparov on 2005-06-09
[QUOTE=gasparov]Same problem here with realtech and NF3 chipset as well,everything seems recognized and loaded ifconfig -a and route -n are as usual .Switching from static to dhcp brings to no DHCP get discovered,using another nic doesn't solve the problem.2 kernel updates and 2 network problems..is there anyway to swith back?I'll try the noapic nolapic thing and the 386 kernel but the computer is remote:remote comnputer + no net=impotence[/QUOTE]
 ok..i solved it but in "widows style" that is there are not evident reasons why things should work now,in any case I did the following:
-switch off every network hardware ( unwire it)--->CHECK HARDWARE!!!!
-switched back to linux image not security ,that is .34 and not .34-2 ( Synaptic-->Packet-->Force Version)

---

### Post by 8oluf7 on 2005-06-13
[QUOTE=gasparov]ok..i solved it but in "widows style" that is there are not evident reasons why things should work now,in any case I did the following:
-switch off every network hardware ( unwire it)--->CHECK HARDWARE!!!!
-switched back to linux image not security ,that is .34 and not .34-2 ( Synaptic-->Packet-->Force Version)[/QUOTE]
Sorry I've appeared to be uninterested in the helpful advice on this thread. Two reasons:
[list]
[*]I had a deadline to meet, so had to leave the machine festering and use another one
[*]The machine now won't boot as the EXT3 file check (forced after 30 starts) is failing (I'll raise this in the appropriate forum).
[/list] 
Many thanks gasparov - I think that the 'Force Version' route is what I was looking for.

---

### Post by gasparov on 2005-06-14
[QUOTE=8oluf7]Sorry I've appeared to be uninterested in the helpful advice on this thread. Two reasons:
[list]
[*]I had a deadline to meet, so had to leave the machine festering and use another one
[*]The machine now won't boot as the EXT3 file check (forced after 30 starts) is failing (I'll raise this in the appropriate forum).
[/list] 
Many thanks gasparov - I think that the 'Force Version' route is what I was looking for.[/QUOTE]

It seems we do have two twins machines:[http://ubuntuforums.org/showthread.php?t=37041](http://ubuntuforums.org/showthread.php?t=37041)

Well no answear cause few people like this kind of problems I think.In my case it was a "download" partition and even if there were many errors it was still a read-only mountable partition and with lots of patience and few dvd I was able to keep my data....Good luck

---

### Post by 8oluf7 on 2005-07-08
[QUOTE=alastair]Look in your system logs for ethernet/network stuff - all of it i.e. module load e.g. 

e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
....

Look for warnings, errors etc. related to networking.

Look through /var/log/syslog (or "dmesg" output).

Then, when logged in :

ifconfig -a
route -n[/QUOTE]
Did a complete reinstall to clear another problem (self-inflicted). Reboot at the end of the install was normal, and I was able to extend the sources list, do updates and install the other stuff I needed. 

The next day - no network found during startup! I fiddled around, restarting several times, unsuccessfully, and then ran the mem86 test, just to do something different - and the reboot from this test found the network. 

The following day, I tried to boot - no network. Before shutting down, I saved the results of running 'dmesg'. Hours later, I tried again - and the boot was successful. Again, I saved the output from 'dmesg'. Comparing the two, I can find no extra warnings and few differences. The differences I found were:

[INDENT][I]ehci_hcd 0000:00:02.2: USB 2.0 initialized, EHCI 1.00, driver 26 October 2004
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected[/I] 
**usb 2-2: new full speed usb device using ohci_hcd and address 2**
*usb 3-4: new high speed USB device using ehci_hcd and address 2* 
[/INDENT]
The line in bold did not appear in the unsuccessful boot dmesg log.

Further down:
[INDENT]
*r8169: eth0: link up*
[B]NET: Registered protocol family 10
Disabled Privacy Extensions on device ffffffff80350fc0(lo)
IPv6 over IPv4 tunnelling driver[/B]
[I]Vendor: USB2.0     Model: CF   CardReader     Rev:
(followed by a lot of cardreader stuff)
usb-storage: device scan complete
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
(followed by several lines of powernow-k8 stuff)[/I]
[/INDENT]

The three lines in bold appeared as above in the successful boot, but at the end of this quote in the unsuccessful one.

**Questions**: Are these differences significant? If so, what can I do to fix them? If not, what else do I look at? Is the fact that all other devices on the network were switched on for the latest (successful) boot, but not for the earlier, unsucessful one, significant?

---

### Post by 8oluf7 on 2005-09-24
An update to this continuing saga.

The system will work for a while, sometimes through multiple re-starts. Very occasionally the network has been lost during a session. Then, for no discernable reason, the system will decide not to play, failing to connect during a start/re-start, sometimes several times. Then, although nothing has been altered, it starts working properly when I try again a few hours later. (When the system fails, all of the activity lights on my 8-way ethernet switch flash in unison.) 

I use Synaptic frequently to keep the system right up to date (legacy of a past littered with Windows problems?). Last night I updated libnspr4 and libss3. This morning - boot up, no network. I tried forcing the old versions of these libraries - no network. I even tried forcing the old version of the kernel - still no network.

So, I restored the latest versions and took a break, during which I remembered Gasparov's posting. Returned to the machine, switched it and the US Robotics ethernet switch off at the mains to force the ethernet circuitry to take a complete break. Switched them back on (ethernet switch first), went for a boot and - bingo! normal network connection.

Can anyone explain this behaviour?

Will this problem be fixed in the 64-bit version of Breezy?

Would installing the 32-bit version be a better bet?

---

### Post by 8oluf7 on 2005-11-25
**Status Update**
A few weeks ago I permanently mounted the shared area on my Windoze machine on my Linux machines. (Yes, I know that I should be using a Linux machine to serve the others - but, for historical reasons ...) Since then, provided that the Windoze machine is fully running before I start up the Linux machine - no network problems. During start-up, the remote drive is mounted before the machine tries to synchronise its clock with the Ubuntu website. 

I don't understand what's going on - but I'll take it.:D

---

