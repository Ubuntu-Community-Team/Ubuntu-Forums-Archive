---
title: "Ethernet randomly stops receiving anything."
date: 2020-10-31
forum: Networking &amp; Wireless
---

### Post by avgjoetx on 2020-10-31
I originally posted this on askubuntu, but received no replies.  So I will try again here.  This problem has now persisted through two installs and two versions.....

[COLOR=#242729][FONT=Arial]I started with an Ubuntu 18.04.5 LTS, system on an AMD 64bit system with 16 GB of ram. Recent Zoneminder install has cranked up traffic. But I did not use this system much prior to the ZM install.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After a while (minutes to hours), the system stops communicating. When this happens, the ARP cache is mostly showing incomplete in the mac entries, and the only way to reset is to reboot or unplug the Ethernet. Eventually it happens again.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have tried 3 different drivers up to and including the latest from Realtek. Currently, using the r8168, 8.045.08, 4.15.0-118-generic, x86_64 driver per dkms. No real diff between them. The systems I am trying to ping are all in the same local subnet and same GigE switch. I have tried 3 different cables including a cat6 one.  All are 4-6ft patch cables going directly to the switch. Everything works great....for a while.   Then it stops.   Interestingly, the default router, and other IPs that are not sending or receiving traffic, retain their MACs in the ARP cache UNTIL I try to ping them or otherwise communicate with them. So once this problem starts, every ARP entry will move to &#8220;incomplete&#8221; as soon as I attempt to ping them. To be clear, all IP and ping traffic immediately fails, but the ARP cache doesn't start to show Incompletes until I try to send or receive to each one. It makes sense to me why I can't communicate. The system does not know the MAC!  Or so I thought.  It turns out, the system is not RECEIVING any packets.  It is transmitting fine.  But no receive.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Multiple other systems on the same local IP subnet have no issues communicating with each other all on the same local switch. I have tried different switch ports for this system, but after correcting itself for a while, it just happens again. I have no duplicate IP's. ARP fails because ARP replies arre not received.. I am not sure what to look at next.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas why it keeps dropping? I see similar questions like mine here, but none say it was ever resolved and trying some of the suggestions did not help me.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]
*******UPDATE[/B]******[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After many failures. I decided on a complete reinstall of Lubuntu 20.04 LTS. I removed the old partition and started over.  Sadly, I have the EXACT same problem. It looks like it uses the same driver also. tcpdump shows my system is constantly trying to ARP to refill the incompletes in the table. I can also see those broadcasts hitting the network on another machine. Once the problem starts, the problem box never sees any replies (in tcpdump), and all of the ARP entries age out . And just as before, simply unplugging the ethernet cable for a second, or a reboot fixes the issue, for a while. Using the gui to disable/enable the interface does NOT fix the issue. And by "fix", I mean temporarily. Eventually the problem always comes back. So essentially the "receive" on this systems goes to sleep until I physically reset the interface somehow. Transmit is working fine.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Ethtool shows nearly the same driver of 8.048.00-NAPI for the r8168. My bios says the chip is 8111G. Based on what I found, the driver is the same for 8168 and 8111.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I have ruled out at least one rev of the OS. That leaves the driver or Ethernet hardware? Or perhaps a config issue the crosses these to versions of the OS??[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]*********Update********[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After seeing another post where they had a similar issue, which was solved by a bios update, I checked mine again. I am on the latest bios for the MSI AM1I MB, which is V10.2. It is from 2014 but no updates have been made available since.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][B]
*****Update 10-30-20[/B]******[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After reading another post, I tried forcing the interface to 100Mb FD. That just created another issue, a periodic full system freeze requiring a reset button or power cycle. Not even a sysrq worked.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Fortunately, My USB Ethernet hardware arrived today. So I tried the new hardware and it's automatically downloaded driver. Sadly the "packet receive stop" happened again!! Exact same symptoms. After running fine for 5min to an hour, suddenly and randomly, no packets are received per tcpdump. Outbound (transmit), is working as before. ARP packets are being broadcast, other machines are responding, but this system "sees" NO packets coming in. In all these tests and versions, the ethernet maintains link and the activity LED flashes as if nothing is wrong.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Now keep in mind that my "load" on this machine is 5 IP cameras feeding the Zoneminder app. It keeps a fairly high receive load on the ethernet interface.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]That leaves just a few things in common, the fact that I have installed Zoneminder on both versions of Linux, and some of the hardware, not including the Ethernet components.
[/FONT][/COLOR]

Help!

---

### Post by TheFu on 2020-10-31
excellent troubleshooting. You've done good isolation. Along the way, I had ideas for problem, then your next step would isolated that away.  We assume there is a single issue, when there could be 2 or more issues.

So, all I have are guesses for things to try.
[LIST]
[*]disable all realtek network stuff.
[*]install an Intel PRO/1000 or i210/i211 NIC.
[*]Consider swapping in a cheap $15 unmanaged switch.
[/LIST]

Realtek has hw and driver issues, hence why to disable and use proven e1000e or igb based intel hw. Avoid any too new Intel, as the 2.5 Gbps stuff has some issues still.

Having a spare switch is never a bad idea.

I've had a realtek NIC partially fail. My solution was to install a cheap Intel NIC I had laying around. I've installed some even cheaper Marvell Gbps NICs too, but they had terrible performance with the skye driver, usually in the 250Mbps range. OTOH, $10 for a NIC in 2006 was a great deal.

---

### Post by avgjoetx on 2020-11-01
Sadly, I have no option to add anything other than a USB device.  This micro itx board has no expansion slots other than the AGP for video.  That is why I ordered and tried the USB Eth dongle, which it turns out also uses a realtek chip, but a completely different one and a different driver.  Does someone know of a different dongle that uses Intel hardware?  I am hoping to have another switch soon.  Not that I believe mine has an issue, since over a dozen other devices are working on it fine, and I have swapped this box onto known good ports.  I mainly ordered the new switch because it has more ports and also supports port mirroring.

---

### Post by TheFu on 2020-11-01
I have this USB3 to GigE+3 USB3 port device. Use it with laptops that don't have ethernet and gain a few other USB3 ports.

```
$ sudo lsusb -v  |egrep 'Ether|Network'
Bus 002 Device 003: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
  idProduct          0x1790 AX88179 Gigabit Ethernet
      iInterface              4 Network_Interface

$ lsmod|grep ax88
ax88179_178a           24576  0
usbnet                 45056  1 ax88179_178a
mii                    16384  2 usbnet,ax88179_178a
```

Not Intel either. "Ubuntu Server" didn't come with drivers for it last time I checked. All the 'desktop' variants appear to come with the drivers - 100% plug-n-play. Sorry, I don't know if it is still made.  I usually see about 920 Mbps from it.
```
$ iperf3 -c hadar
Connecting to host hadar, port 5201
[  4] local 172.22.22.13 port 42840 connected to 172.22.22.6 port 5201
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec   110 MBytes   921 Mbits/sec    0    120 KBytes       
[  4]   1.00-2.00   sec   110 MBytes   921 Mbits/sec    0    120 KBytes       
[  4]   2.00-3.00   sec   110 MBytes   921 Mbits/sec    0    120 KBytes    
```

Hadar has an i211 using igb driver. The laptop is going through 2 GigE switches to get to hadar.

I had an old AMD e-350 APU device that only had 1 slot. I'd planned to use it as a router when the GPU couldn't handle FHD video. That plan failed mainly because I didn't want any important stuff dependent on USB connections. I've been burned too many times.

---

### Post by avgjoetx on 2020-11-01
That dongle is very similar to the one I just received.  GigE plus 3 USB ports.  I am hesitant to keep buying hardware.  It just seems unlikely to me that I would have the same exact issue with two different ethernet devices, and different drivers, and still be facing a hardware issue.  

I read another post about "dmesg" which is something I had not heard of before.  I hoped it would give me some indication of what was happening with the drivers.  Sadly, I see no messages related to network before or after the problem starts.  I do see what appears to be normal info at startup, but nothing after.  Another bust.

---

### Post by avgjoetx on 2020-11-02
I decided to return the realtek USB adapter, and order one based on [COLOR=#000000][FONT=&quot]AX88179.  It seems like a longshot to me, but perhaps realtek just makes bad drivers for Linux.[/FONT][/COLOR][COLOR=#000000][FONT=&quot] I have used their products with Windows for years.  It seems odd that they would be so bad a Linux.[/FONT][/COLOR]

---

### Post by TheFu on 2020-11-02
> **avgjoetx said:**
> I decided to return the realtek USB adapter, and order one based on AX88179.  It seems like a longshot to me, but perhaps realtek just makes bad drivers for Linux. I have used their products with Windows for years.  It seems odd that they would be so bad a Linux.

Realtek works sometimes, often, but the second there's an issue and configuration is ruled out, then it is either the driver or the hardware. They use the CPU more than Intel NICs do. There is a difference.  Plus, Intel has been supporting BSD for decades. In my book, even if I don't run BSD directly on the HW, having a vendor who supports BSD is a good sign for the portability of their drivers.

Things working on Windows means nothing.  Anyone making hardware will spend 99.99999% of their time ensuring that Windows10 works for clear reasons.  Other drivers are 'good enough' quality to claim Linux support, even when it isn't quality code..  We've seen some drivers that didn't properly initialize registers over the years.  The workaround was to always boot into Windows first, then, without a power cycle, reboot into Linux.  That happened about 10 yrs ago - I don't recall if realtek was part of that specific issue or not - best to assume not.  OTOH, I've got a few realtek on-the-motherboard GigE NICs that either are bad hardware or bad drivers.  Regardless, the fix for my sanity was to disable them in the BIOS and use a NIC from Intel. Perhaps I'm overly quick to dislike Realtek stuff? We all have different experiences.  These forums have lots of people with GigE NICs from Realtek that are traced back to the drivers.  In my book, bad drivers or bad hardware cause the exact same result means I need to avoid them. If $25 saves me 1 hr of hassles, then it is worth the replacement to never have issues again. That's how I think on this.  YMMV.

---

### Post by avgjoetx on 2020-11-02
I wish I had and easy way to add a different NIC in this box.  All it has is one "Mini" PCI-E slot.  Talk about obscure.  If I had not already invested in this system, I would have given up long ago. 

 I just loaded the the identical config on a different system that ALSO uses the rtl8111 but it is the "E" rev and Lubuntu automatically put an 8169 driver on it.   That is what other forums have said you should NOT do.  But so far, and I do mean "so far".  The ethernet is more stable!  It looks like MANY MB makers use this 8111 chip, or they did just a few years ago.

So I am questioning the other post now.  It would be great to understand why Lubuntu loads the 8169 driver on this board, and if that is really a problem now.  Perhaps it was a problem a few years ago, but it has been corrected???? Or perhaps the different revs of this chip need different drivers??  What a mess.

---

### Post by TheFu on 2020-11-03
There are 20 different versions of the rtl8111.  I have a rev "0C" in 1 box, but it isn't used.

Would be helpful if someone would make a chart or a DB that has the revision, kernel, and driver in a huge table.  The kernel shouldn't need to be 3-level accurate, but 2-level is needed as 4.4.x and 4.15.x are both still supported on Ubuntu systems.  It gets worse with RHEL versions. They have very long support.  There is also certain network setups which have incorrect support and break things that we all have in our cheap home networks (and some expensive enterprise gear too).

---

### Post by avgjoetx on 2020-11-03
Well I received my new USB dongle based on he [COLOR=#000000][FONT=&quot]AX88179.  Same issue!!. That makes 3 different pieces of hardware and 3 different drivers, all the same issue. I think I can safely rule out Ethernet hardware and ethernet drivers.  My new switch should arrive in a few days.  While I do not believe my existing switch has an issue, the new one supports port mirroring.  That will allow me to verify that this Lubuntu system is, or is not, actually receiving packets when this problem starts. 

But considering that ethernet PC hardware is now highly unlikely, I am unsure of what to look at next.  Since tcpdump sees NO packets being received other than those to and from localhost, I am left to wonder what software sits between the driver and the rest of the OS. [/FONT][/COLOR]

---

### Post by TheFu on 2020-11-03
Try booting from a "Try Ubuntu" flash environment or using a different ISO from 20.04, 18.04 and/or 16.04 releases?
Also, try booting from an older kernel on the system if it did work previously. There should be a list under "Advance" in the grub menu.

---

### Post by avgjoetx on 2020-11-03
I decided to do a fresh install and do some testing w/o Zoneminder installed.  However, the high zm load is also what seems to trigger this issue.  I if I recall correctly, it takes MUCH longer for the issue to appear without a significant load, if at all.

---

### Post by avgjoetx on 2020-11-04
Reinstall complete.  Everything seemed fine for a day under light network load.  So I decided to install Zoneminder and as usual, it worked for a while before the Ethernet stopped receiving again.  ZM requires install of LAMP.  I followed the instructions here using the script.  [https://wiki.zoneminder.com/Ubuntu_Server_or_Desktop_Zoneminder_1.34.x](https://wiki.zoneminder.com/Ubuntu_Server_or_Desktop_Zoneminder_1.34.x)   This seems to be the common denominator, well that and the MB/CPU/RAM.  

Any thoughts?

---

### Post by avgjoetx on 2020-11-06
Beyond crazy.  My new switch came in and I also decided to try Centos.  Neither made any difference!  I can now see that this system is definitely ignoring incoming packets.  For example, after the problem starts, this system keeps ARPing for it's default router and everything else it is attempting to communicate with.  I can see the ARP replies using a span port and Wireshark.  The replies ARE getting to the ethernet port, but this PC does not count the incoming packets in ifconfig stats or see any replies in tcpdump.  It appears that the system tells the ethernet to ignore incoming packets for some reason.  The pc keeps transmitting and attempting to recover.  But because it can't "see" the replies, it just keeps trying to ARP.

I am stumped.  I have ruled out all of the Ethernet hardware.  Yet this "looks" like an ethernet problem.

---

### Post by TheFu on 2020-11-06
Did you try 20.04 and 16.04 yet - under load?
Have you tried using a static IP or using a DHCP reservation, which ever you aren't using today?
Have you tried using different network management - not network-manager, but static files?

In theory, these shouldn't matter, but we never know.  I've seen a cracked motherboard do strange things to ethernet packets.

---

### Post by avgjoetx on 2020-11-06
I have tried 18.04 Ubuntu and 20.04 Lubuntu, as well as Centos 8.  All were fresh installs including a repartition.  I have used both static IP's and DHCP with reservation.  Network-manager is default for ubuntu and lubuntu I believe.  I have NOT tried anything different.  I would not know how to change it.  I did see a post about it fighting with something else when used together, but I forgot where I saw that.  It was one of the reasons I decided to wipe and start over about 4 tries ago.

My installs go the same.  Fresh/default install, check operation (light load), install LAMP, install ZM.  Configure 5 IP cameras to load up ZM.  This causes a large constant load on the Eth receive.  Eventually the Eth stops receiving properly....fail.

I am inclined to believe the LAMP, ZM or the constant high load are the problem.  Perhaps one, or all 3.   What I know for sure now is that the system transmits fine, the replies make it to the ethernet port fine, but replies are lost on the motherboard or in the software.  Remember that my brand new AX based USB Eth had the same problem.

Something goes wrong "inside" this box. I really wish someone could tell me how to check operation at the driver software level and all levels between that and what ever runs arp OR tcpdump.  That is where things go wrong.

---

