---
title: "trouble getting my 14.04 Ubuntu system back on the network (driver issue?)"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by xigen on 2014-08-14
I am about to reinstall ubuntu 14.04.

Mint 14 works right out of the box.  Leading me to believe:  my wiring is good, I am directly connected to the router, and my NIC is good.

IP 192.168.2.139
Netmask  255.255.255.0
Gateway 192.168.2.1
DNS 192.168.2.1

Upon install.. networking on 14.04 ubuntu does not work

I go to the Network Manager (upper right next to [En] language indicator) and try to give my system a static IP... and .. no luck

..
How do I diagnose what is up?
What do I try next?

---

### Post by varunendra on 2014-08-15
Assuming it is an Ethernet connection you are talking about, please post back the outputs of -
```
sudo lshw -C network
nm-tool
```
..while the cable is connected and is supposed to work.

---

### Post by xigen on 2014-08-18
Here is my best attempt to type what I see on the system

$sudo lshw -C network
description: Etnernet Interface
Product: RTL8111 / 8168 / 8411 PCI Experess Gigabit ...
Vendor: Realtek
Physical Id: 0
Bus info: pci@0000:02:00.o
logical name: eth0
version:06
Serial: 74:... ... ... ..
Size: 100Mbit/s
Capacity: 1Gbit/s
width:64bits
clock: 33MHz
capabilities: pm msi pciexpress msix vdp bus_master cap_list ethernet physical tp mii 10bt ...... ... .. augonegotiation
resources: irq:73 ...ioport: memory: 

$nm-tool
State: connected (global)
Device: eth0 --------------------------
Type: Wired
Driver: r8169
State: unmanaged
Default: no
HW Address: 74:D4:35:5E:C7:63

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s
Wired Properties:
Carrier:  on

Thoughts?

---

### Post by varunendra on 2014-08-18
> **xigen said:**
> Thoughts?
No thoughts, only complains -

**1)** You didn't use 'Code' tags to post the outputs (probably my mistake not having asked that, but your profile dodged me :p). Please follow the "Use Code Tags" link in my signature if you really don't know what it is or how to use it. :)

**2)** You omitted the parts that I was interested in -
```
$sudo lshw -C network
....
capabilities: pm msi pciexpress msix vdp bus_master cap_list ethernet physical tp mii 10bt ...... ... .. augonegotiation
resources: irq:73 ...ioport: memory: 
....
```
Although again my mistake since I didn't tell you which parts I wanted to see. It was the "**configuration**" line (besides the "Size" and "Capacity" lines which you did post) which is printed just below the last line (capabilities) quoted above. Feel free to delete/obscure the IP address if it is there (although it is not a sensitive info, since it is only your LAN side IP).


Although the output of nm-tool tells most part of it, but I just don't feel confident without taking a look at the lshw parts mentioned above.

This time, please also post the output of (along with the full output of "lshw..." command again) -
```
sudo ethtool eth0
```

**PS:**
Okay, the 'complain' part was just a joke. But I do need to see the parts mentioned. So, on a more serious note, you can redirect all output to a file by adding a " > (filename)" part after any command. For example -
```
sudo lshw -C network > Desktop/lshw.txt
```
..will put all the output in a file named "lshw.txt" on your Desktop instead of printing it on the terminal.

---

### Post by xigen on 2014-08-19
Code tags are very cool.  

Thank you for the heads up ...  I will make it part of future postings.



```


  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:5e:c7:63
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:73 ioport:e000(size=256) memory:fe100000-fe100fff memory:d2100000-d2103fff


```

```





NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        74:D4:35:5E:C7:63

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


```

---

### Post by xigen on 2014-08-19
```
  $dmesg | grep -e eth0 -e r8169
[    1.362481] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.362491] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.362701] r8169 0000:02:00.0: irq 73 for MSI/MSI-X
[    1.362877] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c5c000, 74:d4:35:5e:c7:63, XID 0c900800 IRQ 73
[    1.362880] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.342342] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.145728] r8169 0000:02:00.0 eth0: link down
[    3.145805] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.145848] r8169 0000:02:00.0 eth0: link down
[    3.146078] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.785466] r8169 0000:02:00.0 eth0: link up
[    4.785473] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.794716] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   64.794718] Modules linked in: snd_hda_codec_hdmi rfcomm bnep bluetooth nls_iso8859_1 snd_ice1712 snd_cs8427 snd_i2c snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_mpu401_uart snd_ac97_codec ac97_bus kvm_amd snd_seq_midi snd_hda_intel kvm snd_seq_midi_event snd_hda_codec snd_hwdep snd_rawmidi snd_pcm crct10dif_pclmul crc32_pclmul snd_page_alloc ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd nouveau snd_seq mxm_wmi snd_seq_device wmi psmouse snd_timer video ttm serio_raw drm_kms_helper snd edac_core k10temp edac_mce_amd fam15h_power drm i2c_algo_bit soundcore sp5100_tco i2c_piix4 parport_pc mac_hid ppdev lp parport hid_generic usbhid hid pata_acpi r8169 ahci pata_atiixp libahci mii
[   64.801003] r8169 0000:02:00.0 eth0: link up
[  112.763016] r8169 0000:02:00.0 eth0: link up
[  160.724919] r8169 0000:02:00.0 eth0: link up
[  502.469903] r8169 0000:02:00.0 eth0: link up
[  556.411075] r8169 0000:02:00.0 eth0: link up
[  610.384210] r8169 0000:02:00.0 eth0: link up
[  664.325458] r8169 0000:02:00.0 eth0: link up
[  994.079897] r8169 0000:02:00.0 eth0: link up
[ 1048.025127] r8169 0000:02:00.0 eth0: link up
[ 1119.972031] r8169 0000:02:00.0 eth0: link up
[ 1179.916483] r8169 0000:02:00.0 eth0: link up
[ 1485.693938] r8169 0000:02:00.0 eth0: link up
[ 1533.651915] r8169 0000:02:00.0 eth0: link up
[ 1581.613802] r8169 0000:02:00.0 eth0: link up
[ 1629.575752] r8169 0000:02:00.0 eth0: link up
[ 1971.288691] r8169 0000:02:00.0 eth0: link up
[ 2019.250606] r8169 0000:02:00.0 eth0: link up
[ 2067.212605] r8169 0000:02:00.0 eth0: link up
[ 2115.174546] r8169 0000:02:00.0 eth0: link up
[ 2456.919517] r8169 0000:02:00.0 eth0: link up
[ 2504.881483] r8169 0000:02:00.0 eth0: link up
[ 2558.822647] r8169 0000:02:00.0 eth0: link up
[ 2606.784552] r8169 0000:02:00.0 eth0: link up
[ 2948.529546] r8169 0000:02:00.0 eth0: link up
[ 2996.491511] r8169 0000:02:00.0 eth0: link up
[ 3044.453444] r8169 0000:02:00.0 eth0: link up
[ 3092.415438] r8169 0000:02:00.0 eth0: link up
[ 3434.128380] r8169 0000:02:00.0 eth0: link up
[ 3482.090263] r8169 0000:02:00.0 eth0: link up
[ 3530.052305] r8169 0000:02:00.0 eth0: link up
[ 3584.025455] r8169 0000:02:00.0 eth0: link up
[ 3925.738470] r8169 0000:02:00.0 eth0: link up
[ 3973.700370] r8169 0000:02:00.0 eth0: link up
[ 4021.662242] r8169 0000:02:00.0 eth0: link up
[ 4069.624184] r8169 0000:02:00.0 eth0: link up
[ 4411.369150] r8169 0000:02:00.0 eth0: link up


```

---

### Post by xigen on 2014-08-19
I tried blacklisting r8169 and installing r8168.

[http://www.dividebyzero.co.za/blog/2012/02/how-to-fix-rtl8168b-ethernet-connectivity-issues-in-linux/](http://www.dividebyzero.co.za/blog/2012/02/how-to-fix-rtl8168b-ethernet-connectivity-issues-in-linux/)

** I went to the Realtek website and got a newer r8168 driver.

```

Firstly, confirm you actually have the r8168 controller.  (I recommend running all commands as root).

lshw -short
If so, you’ll need to download the latest driver from the Realtek driver website. Alternatively, run the following command in your Home directory:

wget http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2
Next we need to remove the r8169 drivers from the kernel.

rmmod r8169
Now we get to the good bit – compile and install the Realtek r8168 drivers:

tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
sudo modprobe -rfv r8169
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
sudo depmod -a
sudo modprobe -v r8168
Confirm everything went as planned and the driver is installed.

lsmod | grep r8168
You now have to blacklist the r8169 driver by editing /etc/modprobe.d/blacklist.conf and inserting

blacklist r8169
Test the success by rebooting your server and pinging it from another machine.  This is how I tested it and after updating the driver my ping returned a consistent response.  In fact, the response was much quicker as the r8169 driver also capped the ethernet controller at 100MBits.




```



No luck.  No networking so far.

Suggestions?

---

### Post by xigen on 2014-08-20
Looking into  RealTek r8168 driver.

```

meow@MeowBatunde:~/Downloads/r8169-6.018.00$ sudo dmesg | grep eth0
[sudo] password for meow: 
[    1.561923] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c5c000, 74:d4:35:5e:c7:63, XID 0c900800 IRQ 73
[    1.561925] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.417754] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.353512] r8169 0000:02:00.0 eth0: link down
[    3.353592] r8169 0000:02:00.0 eth0: link down
[    3.353598] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.353945] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.977780] r8169 0000:02:00.0 eth0: link up
[    4.977788] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.862633] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   64.872936] r8169 0000:02:00.0 eth0: link up
[  112.834981] r8169 0000:02:00.0 eth0: link up
[  160.792795] r8169 0000:02:00.0 eth0: link up
[  502.624734] r8169 0000:02:00.0 eth0: link up
[  550.587804] r8169 0000:02:00.0 eth0: link up
[  604.616642] r8169 0000:02:00.0 eth0: link up
[  652.451897] r8169 0000:02:00.0 eth0: link up
[  994.172285] r8169 0000:02:00.0 eth0: link up
[ 1042.188033] r8169 0000:02:00.0 eth0: link up
[ 1090.183680] r8169 0000:02:00.0 eth0: link up
[ 1138.076383] r8169 0000:02:00.0 eth0: link up
[ 1363.327898] r8169 0000:02:00.0 eth0: link down
[ 1365.140416] r8169 0000:02:00.0 eth0: link up
[ 1377.874603] r8169 0000:02:00.0 eth0: link up
[ 1425.842300] r8169 0000:02:00.0 eth0: link up
[ 1473.787951] r8169 0000:02:00.0 eth0: link up
[ 1521.793642] r8169 0000:02:00.0 eth0: link up
[ 1569.745095] r8169 0000:02:00.0 eth0: link up
[ 1617.710109] r8169 0000:02:00.0 eth0: link up
meow@MeowBatunde:~/Downloads/r8169-6.018.00$ ping 192.168.2.1
connect: Network is unreachable
meow@MeowBatunde:~/Downloads/r8169-6.018.00$ dmesg | grep -i realtek
meow@MeowBatunde:~/Downloads/r8169-6.018.00$ dmesg | grep -i rtl
[    1.561923] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c5c000, 74:d4:35:5e:c7:63, XID 0c900800 IRQ 73
meow@MeowBatunde:~/Downloads/r8169-6.018.00$ 



```

---

### Post by Mark_Shapiro on 2014-08-20
I've had the same problem installing Ubuntu 14.04.1 where the system loses ethernet and WiFi connectivity just as installation completes.  I've tried installing from a DVD and also from a USB drive.  If I select "Run from the Disk" everything works OK, including both WiFi and ethernet.  When I do a full install from either media, all is nominal and the normal "Up Arrow/Down Arrow" icon for network connectivity is displayed until just before the completion of the install.  At that time a "Network Disconnected" message flashes briefly and the icon changes to the little "windshield" symbol for no network found.  Apparently the drivers and hardware are OK since it does work in the "run from media" mode.  I've tried re-installing several times and even burned a new image from the ISO file.  I'm installing on a Dell Inspiron laptop with 160Gb disk, 2Gb RAM, and a dual core processor.  At this point I'm ready to declare 14.04.1 "blitzed" and look for another release. Ideas?  Suggestions?

---

### Post by xigen on 2014-08-21
Wow!  What an epic journey.   My networking is back.

[http://ubuntuforums.org/showthread.php?t=2240533](http://ubuntuforums.org/showthread.php?t=2240533)
... and a big thank you goes out to Chili555

Issues:  
gigabyte 970A-UD3P  has boot loader issues with Ubuntu 14.04 64 bit
gigabyte 970A-UD3P uses the RealTek 8169 driver.   Ubuntu 14.04 works best with the 8168 driver

---

### Post by varunendra on 2014-08-21
Glad you got two of the best people (chili555 and praseodym) working towards a solution to your problem. I also see that you seem to have problems again on that thread you linked above. Please note that modern Gigabyte motherboards come with a feature called "IOMMU" which can cause problems with some I/O devices including network adapters (internal or external).

If you haven't already, you should try toggling its state from "disabled" to "enabled" or vice-versa. If it works, perhaps a better way to deal with this feature is to use "iommu=soft" kernel parameter. Links to wiki pages on how to use kernel parameters temporarily/permanently can be found on this wiki page : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Since you have marked this thread as [SOLVED], and are dealing with further issues on a different thread, I suggest you post questions/updates on that one instead of here. Please do post an update here when the problem gets finally solved.

**PS:**
My availability on the forums is very very uncertain these days, so I'm glad you are now being assisted by two other wifi-masters who are not only the bests, but are also very consistent on the forums. Before trying anything else than what they ask you to do (including what I suggested here), make sure to post there and confirm it with them.

---

