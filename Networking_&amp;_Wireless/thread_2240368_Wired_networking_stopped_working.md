---
title: "Wired networking stopped working"
date: 2014-08-19
forum: Networking &amp; Wireless
---

### Post by Tania_Petsouka on 2014-08-19
Hi all,

i am on ubuntu trusty 14.04, and i recently lost my wired ethernet connection for uknown reason.
I get eth0 no such device and other related errors.
I tried many solutions from other posts, and i probably messed up things more.
I also removed /etc/udev/rules.d/70-persistent-net.rules and i tried to regenerate with no luck
Right now, my networking is always disabled and i am not able to enable.

Notice that is a dual boot, and i do connect perfectly fine in my old windows installation.

Below i attach some outputs i guess will be useful.

Any help will be highly appreciated.

```


tania@tania:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15228 (15.2 KB)  TX bytes:15228 (15.2 KB)
```


```
tania@tania:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

```
tania@tania:~$ sudo lshw -C network
[sudo] password for tania: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:de00(size=256) memory:fbcff000-fbcfffff memory:fbcf8000-fbcfbfff


```

---

### Post by sedawk on 2014-08-19
Please check output of dmesg. E.g. "dmesg |grep eth0" or "dmesg |grep -i realtek" or "dmesg |grep -i rtl". Any warnings or errors related to realtek/rtl or eth0?
Also output of lsmod might be useful (is the module for the realtek card loaded successfully?).

---

### Post by Tania_Petsouka on 2014-08-19
```
tania@tania:~$ dmesg |grep -i realtek
[   15.297671] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[   15.297672] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0889

```

Nothing found for eth0, but | grep eth :

```
tania@tania:~$ dmesg |grep -i eth
[   14.979858] r8168: disagrees about version of symbol alloc_etherdev_mqs
[   14.979859] r8168: Unknown symbol alloc_etherdev_mqs (err -22)
[   14.979903] r8168: disagrees about version of symbol eth_type_trans
[   14.979904] r8168: Unknown symbol eth_type_trans (err -22)
[   14.979969] r8168: disagrees about version of symbol ethtool_op_get_ts_info
[   14.979970] r8168: Unknown symbol ethtool_op_get_ts_info (err -22)

```

---

### Post by Tania_Petsouka on 2014-08-19
Solved by enabling driver

```
sudo modprobe r8169
```

---

### Post by chili555 on 2014-08-19
>   [14.979858] r8168: disagrees about version of symbol alloc_etherdev_mqs
[   14.979859] r8168: Unknown symbol alloc_etherdev_mqs (err -22)
[   14.979903] r8168: disagrees about version of symbol eth_type_trans
[   14.979904] r8168: Unknown symbol eth_type_trans (err -22)
[   14.979969] r8168: disagrees about version of symbol ethtool_op_get_ts_info
[   14.979970] r8168: Unknown symbol ethtool_op_get_ts_info (err -22)Wow! It appears that you compiled r816[COLOR="#FF0000"]8 [/COLOR]from source and it's not working. You probably need to uninstall it.

Also, if you blacklisted r816[COLOR="#FF0000"]9[/COLOR], you need to undo it, since we know it works; check:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```

---

### Post by Tania_Petsouka on 2014-08-19
I had speed  issues with my old driver and i installed a new one, as it's shown here: [B][http://ubuntuforums.org/showthread.php?t=2227323](http://ubuntuforums.org/showthread.php?t=2227323) .

[/B]Btw i'm the [http://askubuntu.com/questions/513541/wired-connection-cannot-be-established-no-eth0](http://askubuntu.com/questions/513541/wired-connection-cannot-be-established-no-eth0), so issue is solved but these weird "disagreements" still appear in dmesg.
Should i be concerned?

---

### Post by chili555 on 2014-08-19
I am aware that each thread, authored by Tania, is the same issue and the same person.

You solved the issue by modprobeing r816[COLOR="#FF0000"]9[/COLOR], yes? At the same time, r816[COLOR="#FF0000"]8[/COLOR], that you compiled from source code, doesn't load correctly and throws up errors aplenty to *dmesg*. If you are still having issues with r816[COLOR="#FF0000"]9[/COLOR], then we ought to troubleshoot them. If r816[COLOR="#FF0000"]9[/COLOR] still can't be coaxed into working as expected, then we ought to go back to r816[COLOR="#FF0000"]8[/COLOR] and try to compile a trouble-free version.

Yes? No??

---

### Post by Tania_Petsouka on 2014-08-19
Yes,
 I'm not experienced in such issues though.
If you could guide me through it'd be great.

Last dmesg:

```
[   15.322504] r8168: disagrees about version of symbol alloc_etherdev_mqs
[   15.322506] r8168: Unknown symbol alloc_etherdev_mqs (err -22)
[   15.322550] r8168: disagrees about version of symbol eth_type_trans
[   15.322551] r8168: Unknown symbol eth_type_trans (err -22)
[   15.322615] r8168: disagrees about version of symbol ethtool_op_get_ts_info
[   15.322616] r8168: Unknown symbol ethtool_op_get_ts_info (err -22)
[   15.383282] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc90004742000, 50:e5:49:3f:c4:30, XID 0c900800 IRQ 46
[   15.383284] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   16.423557] r8169 0000:06:00.0 eth0: link down
[   16.423573] r8169 0000:06:00.0 eth0: link down
[   16.423600] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.061732] r8169 0000:06:00.0 eth0: link up
[   18.061739] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1144.316786] r8168: disagrees about version of symbol alloc_etherdev_mqs
[ 1144.316792] r8168: Unknown symbol alloc_etherdev_mqs (err -22)
[ 1144.316872] r8168: disagrees about version of symbol eth_type_trans
[ 1144.316874] r8168: Unknown symbol eth_type_trans (err -22)
[ 1144.316999] r8168: disagrees about version of symbol ethtool_op_get_ts_info
[ 1144.317001] r8168: Unknown symbol ethtool_op_get_ts_info (err -22)
```

---

### Post by chili555 on 2014-08-19
> **Tania_Petsouka said:**
> Yes,
 I'm not experienced in such issues though.
If you could guide me through it'd be great.Please find the files you used to compile r8168. Downloads? Desktop?? Open a terminal and do:```
cd ~/Desktop/r8168-8.038.00  [COLOR="#FF0000"]<--or whatever version you downloaded[/COLOR]
sudo make uninstall
```Now check to see if r8169 is blacklisted:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```If it is blacklisted, edit the file to remove it:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Remove the line, if it exists:```
blacklist r8169
```Proofread carefully, save and close the text editor.

Reboot and let us hear your report.

---

### Post by Tania_Petsouka on 2014-08-19
About  sudo make uninstall in r8168-8.038.00, there's no rule for uninstal in make file.
Only 'clean' and 'install'. You think that 'clean' will work for that?

---

### Post by chili555 on 2014-08-19
> **Tania_Petsouka said:**
> About  sudo make uninstall in r8168-8.038.00, there's no rule for uninstal in make file.
Only 'clean' and 'install'. You think that 'clean' will work for that?Nope. Please try:```
sudo updatedb
```This will take a few moments; please be patient.```
locate r8168.ko
```You will find a copy in /lib/modules and we are going to remove it:```
sudo rm /lib/modules/[COLOR="#FF0000"]3.13.0-34-generic[/COLOR]/kernel/drivers/net/ethernet/realtek/r8168.ko
sudo depmod -a

```Your version may differ; remove the copy you found in /lib/modules/whatever/wherever.

Reboot and let us hear your report.

---

### Post by Tania_Petsouka on 2014-08-19
Nothinh in dmesg for r8168, sounds good.

```
tania@tania:~$ dmesg | grep r8169
[   14.766091] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   14.766099] r8169 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.766312] r8169 0000:06:00.0: irq 45 for MSI/MSI-X
[   14.766448] r8169 0000:06:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000472c000, 50:e5:49:3f:c4:30, XID 0c900800 IRQ 45
[   14.766450] r8169 0000:06:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   15.843683] r8169 0000:06:00.0 eth0: link down
[   15.843700] r8169 0000:06:00.0 eth0: link down
[   17.482235] r8169 0000:06:00.0 eth0: link up
```

Above looks ok to me, to you??

I remember having slownes with r8169, which doesn't appear right now.
I'll be checking next days for that and maybe come back.

---

### Post by Tania_Petsouka on 2014-08-19
I'm actually talking about that issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161)

---

### Post by chili555 on 2014-08-19
Please post back if you still have slow ethernet. As I suggested above, we'll troubleshoot from there.

---

### Post by Tania_Petsouka on 2014-08-19
Thank you again, your help is precious.

---

### Post by Tania_Petsouka on 2014-09-06
Hi again,

unfortunately i have serious speed issues now that i use r8169.
Probably because of that [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161).

Could you give me a hand on this?

---

### Post by chili555 on 2014-09-07
> **Tania_Petsouka said:**
> Hi again,

unfortunately i have serious speed issues now that i use r8169.
Probably because of that [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161).

Could you give me a hand on this?I see but one post that claims to have fixed the issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1275161/comments/27)> I decided to switch the existing CAT 5 cables between these lanports and the Dlink. Plugging in the first of the [COLOR="#FF0000"]5e cables [/COLOR]resulted in immediate resolution of the internet connection problem (I even noticed the activity lights on the lanport flickering more quickly on the one with the 5e than the one without). It's been up and running fabulously for about 48 hours so, with no small amount of trepidation, I'm calling my particular iteration of this problem solved. I hope this helps others.Did you have something else in mind?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812106327&cm_re=cat5e_cable-_-12-106-327-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16812106327&cm_re=cat5e_cable-_-12-106-327-_-Product)

---

