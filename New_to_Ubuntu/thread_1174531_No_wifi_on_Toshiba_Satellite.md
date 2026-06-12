---
title: "No wifi on Toshiba Satellite"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-31
This morning I installed Jaunty Jackalope in this laptop. This went without a hitch. Then I updated, again without any trouble. However, since then it's been nothing but trouble trying to get the (built-in) wifi adapter to connect to my router. 

So far I have followed two troubleshooting procedures found in the Ubuntu documentation, read numerous threads here in the forum that deal with the problem - all to no avail. The only thing I have learned is that it helps if one provides the output of several commands, so here it goes:
```
 lutz@lutz-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:7c:d8:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.106 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 4e:d9:8b:b0:fd:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
``````
lutz@lutz-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
``````
lutz@lutz-laptop:~$ iwconfig
lo        no wireless extensions.lutz@lutz-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```I might mention that I found some Linux drivers [here ]("http://www.intellinuxwireless.org/")but the referenes to kernels scared me off, as a comple newbie (I started using Ubuntu 4 weeks ago) I don't think I am ready to fool around with kernels.

Hopefully some of you great people will come to the rescue. 

TIA.

---

### Post by candtalan on 2009-05-31
Have you used information which has been specific to your actual satellite model, they will be different I guess?

Did wifi get shown and or connected when using the Live CD?

The information you provide may asist others in helping, although I am at the low tech end of this sort of thing. If the driver is in place you should see a wireless connection being attempted. If the driver is not found, then have you considered installing ndiswrapper (using an ethernet cable connection initially) and simply pointing to the windows wireless driver?

good luck

---

### Post by mapes12 on 2009-05-31
I have never had any luck trying to use a windoze driver through ndiswrapper but it may be a solution for you. Alternatively, here are some links that may help you out:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Mark

---

### Post by don_diego on 2009-05-31
> **candtalan said:**
> Have you used information which has been specific to your actual satellite model, they will be different I guess?

Did wifi get shown and or connected when using the Live CD?
Unfortunately I have not been able to find any specific info for this particular model and YES, wifi was operational when I ran JJ from the Livd CD. Weird, eh?

---

### Post by don_diego on 2009-05-31
> **mapes12 said:**
> I have never had any luck trying to use a windoze driver through ndiswrapper but it may be a solution for you. Alternatively, here are some links that may help you out:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

[http://madwifi.org/](http://madwifi.org/)

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

[https://help.ubuntu.com/community/Wi...3d3c3468508d45](https://help.ubuntu.com/community/Wi...3d3c3468508d45)

[https://help.ubuntu.com/community/Wi...eShootingGuide](https://help.ubuntu.com/community/Wi...eShootingGuide)

Mark
Thank you, Mark. I followed the troubleshooting instructions provided in the last 2 of those links explicitly without any luck. Based on the forum thread (4th link in your list) I also installed "wicd" which looks good and runs very nicely but only comes up with "no wireless network found". Since, as I mentioned in my reply to Candtalan, wireless is fine when I run off the LiveCD, I am totally stumped.

---

### Post by superprash2003 on 2009-05-31
ensure that your wireless switch is on [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by don_diego on 2009-05-31
> **superprash2003 said:**
> ensure that your wireless switch is on [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)
Thank you superprash. The switch is ON and wireless was working off the JJ Live CD but not since I installed it. One oddity I noticed is that on booting from the hard drive a message is displayed: "unsupported PM cap regs version (7)". I have no idea what it means or whether it could possibly have anything to do with my wireless problem, all I know is that it causes a delay of several seconds after which the boot continues quite normally.

---

