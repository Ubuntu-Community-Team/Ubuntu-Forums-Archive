---
title: "No internet with onboard Realtek RTL8111C"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by AustinMatherne on 2008-09-17
Well... I installed Ubuntu just fine, and I had internet for a few hours afterwards.  But, than I shut the computer down, came back turned it on and now I don't have internet.  The NIC is a Realtek RTL8111C, on a Biostar I45 (Intel P45 platform).

Any ideas?
Thanks,
~ Austin

Edit: If I boot from the Live CD, I don't have internet ether.  Windows works just fine though.

---

### Post by pytheas22 on 2008-09-17
There are some known issues with certain ethernet cards where Windows doesn't power them down in the way it's supposed to, and the Linux driver is unable to power them back up.  This sounds like it might be what's going on in your case.

Try shutting down the computer completely (not hibernating or suspending), then unplug the power cord for thirty seconds (or remove the battery if it's a laptop).  Then reboot, making sure that the ethernet cable is plugged in before you turn on your computer.  Does it work now?  If not, what is the output of:
```

ifconfig
ifconfig -a
lshw -C Network
dmesg | grep -e eth0 -e rtl
lspci -nn
```

---

### Post by AustinMatherne on 2008-09-17
That was the first thing I thought of, since I've actually had that problem before with a different computer.  But, only Ubuntu is installed on the computer, so there's no way Windows could take control over it between reboots :evil:

Here's the output from ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8a:bb:11  
          inet6 addr: fe80::2e0:4dff:fe8a:bb11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:9273402213 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9181 (8.9 KB)  TX bytes:6835 (6.6 KB)
          Interrupt:251 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:4d:8a:bb:11  
          inet addr:169.254.6.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118100 (115.3 KB)  TX bytes:118100 (115.3 KB)


```
Here's the output from ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:8a:bb:11  
          inet6 addr: fe80::2e0:4dff:fe8a:bb11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:13516175294 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9301 (9.0 KB)  TX bytes:6835 (6.6 KB)
          Interrupt:251 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:e0:4d:8a:bb:11  
          inet addr:169.254.6.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118100 (115.3 KB)  TX bytes:118100 (115.3 KB)


```
Here's the output from sudo lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:4d:8a:bb:11
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=1GB/s


```
Here's the output from dmesg | grep -e eth0 -e rtl
```
[   36.304920] eth0: RTL8168c/8111c at 0xffffc2000103e000, 00:e0:4d:8a:bb:11, XID 3c4000c0 IRQ 507
[   49.803267] r8169: eth0: link up
[   49.803273] r8169: eth0: link up
[  104.301458] eth0: no IPv6 routers present


```
Here's the output from lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Eaglelake DRAM Controller [8086:2e20] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Eaglelake PCI Express Root Port [8086:2e21] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation ICH10 USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation ICH10 HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 2 [8086:3a42]
00:1c.3 PCI bridge [0604]: Intel Corporation ICH10 PCI Express Port 4 [8086:3a46]
00:1d.0 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation ICH10 USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation ICH10 USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH10 LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation ICH10 6 port SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation ICH10 SMBus Controller [8086:3a30]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Unknown device [1002:9440]
01:00.1 Audio device [0403]: ATI Technologies Inc Unknown device [1002:aa30]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
04:00.0 IDE interface [0101]: Marvell Technology Group Ltd. 88SE6121 SATA II Controller [11ab:6121] (rev b1)


```

Any help is appreciated.

Thanks,
~ Austin

---

### Post by pytheas22 on 2008-09-18
I found [this thread]("http://ubuntuforums.org/showthread.php?t=773701") which seems to deal with the same issue as yours (exact same ethernet card).  The solution there is to recompile your ethernet driver.  You can do that by running (this is adapted from that thread; don't run the instructions there because some of the links are broken):

```

sudo apt-get install build-essential
wget ftp://66.104.77.130/cn/nic/r8168-8.006.00.tar.bz2
tar -xjvf r8168-8.006.00.tar.bz2
cd r8168-8.006.00/src
wget http://launchpadlibrarian.net/14011806/r8168-8.005.00.hardy.diff.txt
patch < r8168-8.005.00.hardy.diff.txt
make clean
make modules
sudo make install
sudo depmod -a
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
sudo sh -c 'echo "blacklist r8169" >> /etc/modprobe.d/blacklist-network'
echo 'blacklist r8169' | sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -c -k all
```

Then reboot and see if things work.  Three people in that thread say that that did it for them.

---

### Post by AustinMatherne on 2008-09-18
Well...  I feel dumb.  I reset my router, and poof! It magically started working perfectly.

Thanks for all of the help.
~ Austin

---

