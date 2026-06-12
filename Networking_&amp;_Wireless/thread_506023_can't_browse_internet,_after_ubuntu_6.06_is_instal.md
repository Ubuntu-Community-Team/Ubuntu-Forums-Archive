---
title: "can't browse internet, after ubuntu 6.06 is installed into vmare"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by figo2476 on 2007-07-21
The eth0 is active & use DHCP. But when using the build-in firefox to browse internet, it won't work
any hint?

regards

---

### Post by figo2476 on 2007-07-21
Correct some typos:

after ubuntu 6.06 is installed into "vmware"

---

### Post by figo2476 on 2007-07-21
Just a little update here. After running lspci:

I got:


0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (r ev 01)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev  01)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
0000:00:0f.0 VGA compatible controller: VMware Inc [VMware SVGA II] PCI Display Adapte r
0000:00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-M PT Dual Ultra320 SCSI (rev 01)
0000:00:11.0 PCI bridge: VMware Inc: Unknown device 0790 (rev 01)
0000:02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
0000:02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
0000:02:02.0 USB Controller: VMware Inc: Unknown device 0770


Does it mean '0000:02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)' - the network card is working??

---

### Post by KiloEleven on 2007-07-21
So you have a Windows host OS, and you installed VMware Server software onto the Windows box. Then, you created a virtual machine for Ubuntu, and installed Ubuntu into the virtual machine? Now, the Windows host can still access the network, but the Ubuntu host (running in the VM environment) cannot access the network? If this is the case, check into the network settings for the virtual machine. IIRC, there are 3 different settings for the network connection of virtual machines in VMware. I have had good luck with "Bridged Network", which I think is the default for all new virtual machines.

---

### Post by figo2476 on 2007-07-22
* Yes, you are right.
* I used the default bridge connection, but I have no luck.
  "0000:00:11.0 PCI bridge: VMware Inc: Unknown device 0790 (rev 01)" - is it because it can't recognize the 
  device?

---

### Post by KiloEleven on 2007-07-24
Not sure. I have run several different Linux distros in VMware, and the network card is always detected. What is the output of ```
ifconfig
``` on the VM?

Also, what is the output of Start --> Run --> cmd --> ```
ipconfig /all
``` on the Windows box?

---

### Post by lawr_rawr on 2007-07-24
Are you using wireless or wired? I'm doing the opposite (Ubuntu host, XP guest) and vmware networking only works with NAT if I am using wireless.

---

### Post by mesocal on 2007-12-20
issue may have been resolved by now, but just incase there are a few others who are having the same issues.  some people who are on 7.10 ( 2.6.22-xx) and use VMware Server or Vmware Workstation may need to install a patch. the file (for me, this is where ubuntu installed it)

/usr/lib/vmware(wmare-server)/modules/sources/vmnet.tar 

needs to be replaced with an updated version.  this one works well 

[http://www.hauke-m.de/fileadmin/vmware/vmnet.tar](http://www.hauke-m.de/fileadmin/vmware/vmnet.tar)

simple stuff:
mv vmnet.tar vmnet.tar.backup
cp  downloadfolder/vmnet.tar /usr/lib/vmware/modules/sources/
run vmware-config.pl 

i used NAT instead of Bridged.  It took a few minutes to initialize ( i also selected my network and clicked on "repair" and then it worked but that may have just been a quincidence).

either way, easy fix.

Note - this is for fixing wireless issues.  ideally, a LAN should work.  dont worry about the term 'virtual' because no matter if you use wired or wireless on the host computer, the Guest OS views the connection as wired.

---

### Post by vek on 2007-12-21
Interesting.  Any idea what changed in that TAR?  Its the source code so I suppose I could go ahead and do a diff, as I am curious as to how this works, but ... of course if you know what changed, that'd save some time

---

