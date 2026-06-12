---
title: "WiMax with Ubuntu 11.04?"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Nickjpost on 2011-05-04
I have a Dell Inspiron, core i5, 8GB RAM with WiMax capability. Can I use WiMax in Ubuntu 11.04? If so, how? I know, obviously, that it works in Windows, but I'm trying to 'phase-out' my use of Windows all together. Any help is much appreciated!

Nick

---

### Post by gandaran on 2011-05-04
> **Nickjpost said:**
> I have a Dell Inspiron, core i5, 8GB RAM with WiMax capability. Can I use WiMax in Ubuntu 11.04? If so, how? I know, obviously, that it works in Windows, but I'm trying to 'phase-out' my use of Windows all together. Any help is much appreciated!

Nick
if the modem is already supported then yes it should work, run the network manager » mobile broadband tab » add, check in the first setup wizard window if the modem is detected then choose your country and internet provider, check that the ISP authentication details are correct (you can compare them with the windows setup), thats all to get connected.

---

### Post by Nickjpost on 2011-05-04
> **gandaran said:**
> if the modem is already supported then yes it should work, run the network manager » mobile broadband tab » add, check in the first setup wizard window if the modem is detected then choose your country and internet provider, check that the ISP authentication details are correct (you can compare them with the windows setup), thats all to get connected.

The Dell model I have has it installed internally, so I would think so also.
Awesome, I think that Clear, a Wireless Internet provider, offers a trial membership, so I'll have to see if that works out. I'll post whether or not I could get it to work along with any necessary info. Thank you!!

---

### Post by Nickjpost on 2011-05-07
So I've had Clearwire activate WiMAX on my laptop. 
Ubuntu sees the Intel Centrino Advanced N WiMAX 6250 installed but is showing disabled when I click on the network GUI and there is no way that I can find to enable it. lscpi shows the driver is present. I was going to make sure it was installed but the driver I installed is not an .inf extension. I'm so baffled!! Any other suggestions? let me know if I need to post other info as well. Also, I have checked the Additional Drivers tool in Ubuntu, but none show.

---

### Post by Nickjpost on 2011-05-07
bump

---

### Post by Nickjpost on 2011-05-07
bump

---

### Post by Nickjpost on 2011-05-07
Here's what lspci displays


00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5f)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by sandyd on 2011-05-07
Download: [http://www.linuxwimax.org/Download](http://www.linuxwimax.org/Download)
Readme: [http://git.kernel.org/?p=linux/kernel/git/inaky/wimax.git;a=blob_plain;f=Documentation/wimax/README.wimax;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/inaky/wimax.git;a=blob_plain;f=Documentation/wimax/README.wimax;hb=HEAD)

---

### Post by Nickjpost on 2011-05-08
> **sandyd said:**
> Download: [http://www.linuxwimax.org/Download](http://www.linuxwimax.org/Download)
Readme: [http://git.kernel.org/?p=linux/kernel/git/inaky/wimax.git;a=blob_plain;f=Documentation/wimax/README.wimax;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/inaky/wimax.git;a=blob_plain;f=Documentation/wimax/README.wimax;hb=HEAD)

Nice!!!!
I can't wait to test! I will post results later!

:KS:KS:KS:KS:KS

---

### Post by Nickjpost on 2011-06-12
I had tried the linux driver link you posted, but to no avail. lpsci shows that there is a driver there for the WiMax card, however it will not 'enable' in network settings or via the toolbar icon. Also, Clearwire's software to enable your WiMax connection on my laptop simply will not work with Linux as of yet. Oh well.

---

### Post by Amantay on 2011-09-01
can't connect to [http://www.linuxwimax.org/](http://www.linuxwimax.org/)

---

### Post by johndoe32102002 on 2011-09-03
same here... I can't connect to that website either.

---

