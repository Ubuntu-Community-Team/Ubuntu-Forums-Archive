---
title: "Can not install driver for intel netword adaptor 82562v-2 10/100"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by zhangsan on 2007-07-16
Hi,

I installed Ubuntu Desktop 7.04 on a dell computer (inspiron 530), but system could not find my network adaptor, it is intel 82562v-2 10/100 and the main board is intel g33.

I downloaded the driver(e100-3.5.17.tar.gz) for linux from intel.com, but it could not be compiled:
e100.c:2676:49: error: macro "INIT_WORK" passed 3 arguments, but takes just 2

Could anybody help? Thanks very very much!!

---

### Post by atomictoast on 2007-07-18
I also bought a desktop Dell Inspiron 530 from Dell Japan, and the live CD of 7.04 does not detect the onboard ethernet card. Please let me know if you find a solution for this.

---

### Post by zhangsan on 2007-07-19
One of my friends helped me to solve this problem, could you please leave an email so that I can asked him to send the solution to you?

---

### Post by Hiweed on 2007-07-20
Hi there,

Easy. All you have to do is download the right driver.It's 825xx based network adapter, you should go to
[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=983&DwnldID=9180&lang=eng) and download the[COLOR="Red"]** e1000-7.6.5.tar.gz **[/COLOR]driver.

Here is the step-by-step instruction:
1. On an other computer, download the driver e1000-7.6.5.tar.gz by clicking [http://downloadcenter.intel.com/T8Clearance.aspx?sType=&agr=&ProductID=983&DwnldID=9180&url=/9180/eng/e1000-7.6.5.tar.gz&PrdMap=&strOSs=&OSFullName=&lang=eng](http://downloadcenter.intel.com/T8Clearance.aspx?sType=&agr=&ProductID=983&DwnldID=9180&url=/9180/eng/e1000-7.6.5.tar.gz&PrdMap=&strOSs=&OSFullName=&lang=eng)
2. Copy the e1000-7.6.5.tar.gz file to the Dell Inspiron 530 computer.
3. On the Dell, run:
```

tar xfvz e1000-7.6.5.tar.gz
cd e1000-7.6.5/src
sudo make install
sudo modprobe e1000

```
4. OK, your Ubuntu will try to obtain an IP address automatically now. If not, you might want to edit /etc/network/interfaces to configure it manually, then run this command:
```
sudo /etc/init.d/network restart
```
5. If it still not work, reboot your Ubuntu.

---

### Post by Seamus on 2007-07-20
I have a similar problem - looks like the same hardware. My native Ubuntu install works fine, howver I'm trying to run Vista in a VM.

I've tried both  VMware and VirtualBox, but neither of them recognise the network card in the virtual vista installation - I've browsed for the correct driver, and tried to install it but I get the following error:

> This device cannot start. (code 10)

I've attached two screenshots showing Ubuntu recognising the network card, and Vista failing to install the driver.

any help much appreciated.

Cheers

---

### Post by sciurus on 2007-07-22
Seamus,

You ar running a Vista guest inside VMware/Virtualbox on an Ubuntu host?

When you run a guest operating system in most virtual machine software, it does not acess the actual hardware on the host system. Instead, it accesses virtualized hardware presented by the vm software. You should find what hardware your vm software emulates, then try to install the driver for that in Vista.

---

### Post by atomictoast on 2007-07-23
Thanks Hiweed, that dirver worked!

---

### Post by octocore on 2007-07-23
can anyone explain this process with a little more detail? i have the driver (e1000-7.6.5.tar.gz) file on my ubuntu desktop, but i dont really know where to go from there. please help!

---

### Post by Seamus on 2007-07-24
> **sciurus said:**
> Seamus,

You ar running a Vista guest inside VMware/Virtualbox on an Ubuntu host?

When you run a guest operating system in most virtual machine software, it does not acess the actual hardware on the host system. Instead, it accesses virtualized hardware presented by the vm software. You should find what hardware your vm software emulates, then try to install the driver for that in Vista.

Thanks for this - any suggestions on how to find out what hardware NIC VMware or Virtualbox emulates?

---

### Post by diablozx9 on 2007-08-10
I am having the same issue,,,,BUMP.

Please help

---

### Post by Seamus on 2007-08-10
Good timing on the bump! I just got this sorted out last night using VirtualBox, and and I suspect it would work ok with VMware as well.

To achieve this in Virtualbox, download the [User Manual Here]("http://www.virtualbox.org/download/UserManual.pdf")

Look at section 11.2.4 (troubleshooting / Windows Guests / Networking).

It's pretty self explanatory from there.

I've attached a screenshot showing my Vista guest doing an  nslookup and loading a web page.

POst back if you still have trouble.

---

### Post by tttito on 2007-11-09
Sincere thanks to Hiweed for his masterly instructions. It worked great for me.

t

---

### Post by runesvend on 2008-03-06
Thanks for your instructions Hiweed. I tried them on a running LiveCD, I'm not sure if that's the problem but it didn't work. Here's some output from the operation:

```
ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ tar xfvz e1000*
e1000-7.6.15.4/
e1000-7.6.15.4/src/
e1000-7.6.15.4/src/Makefile
e1000-7.6.15.4/src/e1000.h
*[...]*
e1000-7.6.15.4/SUMS
ubuntu@ubuntu:~/Desktop$ cd e1000*/src
ubuntu@ubuntu:~/Desktop/e1000-7.6.15.4/src$ sudo make install
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/ubuntu/Desktop/e1000-7.6.15.4/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_main.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_82540.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_82542.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_82571.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_82541.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_82543.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_ich8lan.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_80003es2lan.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_mac.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_nvm.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_phy.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_manage.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_param.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_ethtool.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/kcompat.o
  CC [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000_api.o
  LD [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000.mod.o
  LD [M]  /home/ubuntu/Desktop/e1000-7.6.15.4/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.22-14-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.22-14-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
[B]man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
[/B]ubuntu@ubuntu:~/Desktop/e1000-7.6.15.4/src$ sudo modprobe e1000
ubuntu@ubuntu:~/Desktop/e1000-7.6.15.4/src$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ubuntu@ubuntu:~/Desktop/e1000-7.6.15.4/src$ sudo /etc/init.d/network restart
sudo: /etc/init.d/network: command not found

```

This is the output of dmesg:
> [  773.862063] Intel(R) PRO/1000 Network Driver - version 7.6.15.4-NAPI
[  773.862067] Copyright (c) 1999-2008 Intel Corporation.
[  773.862092] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 21
[  773.862105] PCI: Setting latency timer of device 0000:00:19.0 to 64
[  773.908572] e1000: 0000:00:19.0: e1000_probe: Invalid MAC Address
[  773.918746] ACPI: PCI interrupt for device 0000:00:19.0 disabled
[  773.918752] e1000: probe of 0000:00:19.0 failed with error -5


```
00:19.0 Ethernet controller [0200]: Intel Corporation 82562V-2 10/100 Network Connection [8086:10c0] (rev 02)
	Subsystem: Dell Unknown device [1028:023d]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fdfc0000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at fdfff000 (32-bit, non-prefetchable) [size=4K]
	Region 2: I/O ports at ff00 [size=32]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Vendor Specific Information
```

Any help is appreciated.

---

### Post by wandalalakers on 2008-03-11
I have an Intel 82557/8/9 Ethernet pro 100 card and I installed the e1000-7.6.5.tar.gz driver.  I'm unable to use my card.  I initially had a 3com 3905tx card but never could get it to work with gutst, so I removed it and installed the Intel 82557/8/9 card.  I followed the instructions from the earlier posts but I still can't get my card to work.  When I went to Intel's website, there was no linux driver for my card so maybe my card isn't supported.  I also tried the e100-3.5.17.tar.gz driver and still can't get my card to work.  I have two nics in my desktop.  One is a Marvell on an Asus board that's on the motherboard and the other is an Intel etherpro 100 card.  I have the marvell card connected to my cable modem and the other nic to a laptop.  I have the desktop and laptop connected via a crossover cable.

---

### Post by wandalalakers on 2008-03-11
I finally got the Intel card to work in my main desktop now I just need to get the Broadcom 5721 card in my Dell D620 to work.

---

