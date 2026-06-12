---
title: "Airport (atheros) not detected"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by zpon on 2006-11-26
Hey
I have installed ubuntu edgy on my macbook (the core 2 duo version), following this guide [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook), it all worked out great, except my wireless card (atheros) is not detected.
I have tried almost everything, i have even managed to compile madwifi(-ng) by removing linux-restricted-modules and installing libc6-dev first.

My lspci
```
$ lspci
...
02:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
...

```  

My iwconfig
```
$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Can anybody help me out?

EDIT:
I have found a temporary solution using ndiswrapper, see post #5 ([http://ubuntuforums.org/showpost.php?p=1822454&postcount=5](http://ubuntuforums.org/showpost.php?p=1822454&postcount=5))

---

### Post by Rob2687 on 2006-11-26
try doing 
sudo update-pciids

---

### Post by zpon on 2006-11-26
Okay, how is that supposed to help?

EDIT: oh i now i see :), it didn't help

---

### Post by zpon on 2006-11-28
Isn't there anybody who can help me? :confused:

---

### Post by zpon on 2006-11-29
I found a temporary solution on [http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001).
This description should be very easy to follow, even for new users, so the more advanced users will have to bare with me.
You has to install a version of ndiswrapper >= 1.29, so download it from [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148), then it is basicaly just to install the it. 
(You might need libgc-dev)
```
$ sudo make uninstall
$ make
$ sudo make install

```
When you have installed it, you need to download the windows driver from from [www.dlink.com/products/support.asp?pid=489&sec=0](www.dlink.com/products/support.asp?pid=489&sec=0), in the zip file, there is a folder called Driver and in that one there is a file called net5416.inf, this is the one you need, unzip it and go to the directory.
Do
```
$ ndiswrapper -i net5416.inf
$ cp net5416.inf /etc/ndiswrapper
$ sudo modprobe ndiswrapper
```
now
```
$ iwconfig
```
should show wlan0
If you don't know how to use ndiswrapper you can use ndisgtk like i did :).

Hope this will help you, it worked for me :D

---

### Post by trubblemaker on 2006-11-29
ndiswrapper method will work but you should remove the installed drivers (madwifi) first.  ath0 (atheros) comes installed in edgy unless for some reason you  aren't using the restricted drivers, although in an earlier post it appears you removed them.

what are you now getting from 
```

iwlist scan

```
does dmesg contain anything interesting pertaining to your card?
```
 dmesg 
```
also can you post 
```
 cat /etc/network/interfaces 
```

lets not forget K.I.S.S. so you should turn off encrtyption until we can connect to your network, then turn it back on.

---

### Post by zpon on 2006-11-29
> **trubblemaker said:**
> ndiswrapper method will work but you should remove the installed drivers (madwifi) first.  ath0 (atheros) comes installed in edgy unless for some reason you  aren't using the restricted drivers, although in an earlier post it appears you removed them.

what are you now getting from 
```

iwlist scan

```
does dmesg contain anything interesting pertaining to your card?
```
 dmesg 
```
also can you post 
```
 cat /etc/network/interfaces 
```

lets not forget K.I.S.S. so you should turn off encrtyption until we can connect to your network, then turn it back on.

If you read the link i posted before you will see that the new airport chip (atheros) is not added to hal, and there for it does not work yet, it is not the same as the previous card, which works right out-of-the-box

---

### Post by PIC18F452 on 2006-12-04
> **zpon said:**
> If you read the link i posted before you will see that the new airport chip (atheros) is not added to hal, and there for it does not work yet, it is not the same as the previous card, which works right out-of-the-box

Yeah, I was having the exact same problem with my Core 2 Duo MacBook Pro, glad to see I am no the only one having this problem.:twisted:

---

### Post by trubblemaker on 2006-12-05
then why don't you try out [madwifi, ]("http://madwifi.org/")it's made for aethors and claims to have new support, let me know if it works for you/

---

### Post by PIC18F452 on 2006-12-07
Yah, madwifi didn't work, it was installed, but the card didn't show up.
```
andrew@ADD-Machine:~/Desktop/madwifi-0.9.2.1$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```I'm not sure what else to do, I am used to dell laptops were everything works outta the box.

---

### Post by trubblemaker on 2006-12-07
so you did the 
```
make 
make install
```
and it said it was already installed?
try:
```

sudo make uninstall
make 
sudo make install
```

if you already did that post your dmesg it might give us more info,  well post it regardless, so I can see what's left to checkout.

---

### Post by trubblemaker on 2006-12-07
you could see if the live cd works for wireless. sometimes it does, check it out.

---

### Post by PIC18F452 on 2006-12-07
It did not work on the live disc. Like the original post said, it is a new wireless card, Pre-N one. I'll look around and see what people said it iditifed it's self as in windows.

---

### Post by trubblemaker on 2006-12-07
while your there grab the windows driver, then uninstall aethros and use ndiswrapper to run it.

[check this post]("http://ubuntuforums.org/showpost.php?p=1844068&postcount=113") to see howto get windows to tell you what driver you need and where it is on windows:

---

### Post by PIC18F452 on 2006-12-07
I'm not going to install Windows on my notebook. Some one else had already done it anyways.

[http://www.macobserver.com/article/2006/10/31.8.shtml](http://www.macobserver.com/article/2006/10/31.8.shtml)

It states people got the new card to work with wireless-N within windows using a DLink driver. Can some thing like that be done in ubuntu?

---

### Post by trubblemaker on 2006-12-07
if you know the driver that works in windows use ndiswrapper to install it.  If you know howto get the drivers from windows. you can use ndiswrapper.

There is a howto in my signature that you can use.

you'll need the 

driver.sys and driver.inf files. 

put them in the same directory, That's the only not covered in my howto. 
that is what the howto means when it says:
> /path/to/drivers

---

### Post by trubblemaker on 2006-12-07
and if the wireless card came with a CD it's probably easier to just use the actual windows driver with ndiswrapper. (by getting the drivers' of the CD)

---

### Post by PIC18F452 on 2006-12-07
It's a Mac, it doesn't come with Windows drivers.:-? 

But I'll try again later, there is lots of other issues I am having trouble with and I'll probably make one thread for all the issues.

---

### Post by ipstacks on 2006-12-07
You can build a Windows drivers CD from bootcamp though. If you don't want bootcamp, just don't finish the install or partition your drive. I don't know if the wireless driver is on the CD or is better or worse. I am going to try wait for a cleaner solution than ndiswrapper. So does not having a ExpressCard slot and no flash card reader . . . oh well.

---

### Post by FrodoB on 2006-12-07
Zpon;

How is the performance of the device on ndiswrapper. Does it feel speedy enough?

---

### Post by zpon on 2006-12-13
> **PIC18F452 said:**
> Yah, madwifi didn't work, it was installed, but the card didn't show up.
```
andrew@ADD-Machine:~/Desktop/madwifi-0.9.2.1$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```I'm not sure what else to do, I am used to dell laptops were everything works outta the box.

You can use the ndiswrapper like i wrote in post #5 ([http://ubuntuforums.org/showpost.php?p=1822454&postcount=5](http://ubuntuforums.org/showpost.php?p=1822454&postcount=5))

---

### Post by zpon on 2006-12-13
> **FrodoB said:**
> Zpon;

How is the performance of the device on ndiswrapper. Does it feel speedy enough?

It is okay, but it tends to halt a bit when it has been on for some time (it may just be the hotspot i am connected to), but until it gets included in hal, I guess it's alright :)
EDIT I've just used it fore 12 hours at a friends place, and i worked perfect

---

### Post by Herd on 2007-01-04
I followed your instructions and (finally) got wireless working.  After rebooting it stopped working and wlan0 is no longer visible in iwconfig.  Reinstalling the driver diddnt help.  Any ideas?  Thanks.

---

### Post by trubblemaker on 2007-01-04
If you used the ndiswrapper method don't forget to :
```
 sudo ndiswrapper -m 
```
this will add ndiswrapper as a module to the kernel on boot.  Which may be why it stopped working.

---

### Post by Herd on 2007-01-04
I did that but it diddnt seem to have any effect.  And now its not showing wlan0 at all.  Reinstalling ndiswrapper and the driver are proving futile. :(  Any other ideas?  Thanks a lot guys.

---

### Post by dannyboy79 on 2007-01-04
you shouldn't have to do anything other than install ububtu and that's it!!!! I have xubuntu 6.06 Dapper and it works out of the box with my Atheros Card, it's a netgear WG511T I believe. I thought I would let you know this. you really shouldn't be struggling with this as much as you are.

---

### Post by FrodoB on 2007-01-04
There are new Atheros devices that are not yet in the Atheros HAL so they do not yet work with mAdWiFi in Linux.  

This is documented on the mAdWiFi site bug reports and they are recommending ndiswrapper for those cards until a new HAL is created for mAdWiFi.  

Most Atheros devices work fine with Edgy and Dapper, but some of the newer pre-N devices do not.

---

### Post by dannyboy79 on 2007-01-04
this does make sense I suppose but why would a manufacturer use the same chipset which require different drivers? sounds like they should identify this so people know it's different than the original atheros chipset! oh well, now I know why people have been saying that there atheros chipset wifi card isn't working. Oh I should mention, my card has the AR5212 chipset, is that what yours has?

---

### Post by trubblemaker on 2007-01-05
Herd, what do you get with 
```
 dmesg | grep ndis 
```
also can you post ```

iwlist scan
iwconfig
cat /etc/network/interfaces
```

---

### Post by FrodoB on 2007-01-05
There are more Atheros devices out there than the AR5212. If they were all AR5212 devices then they likely would work.

> **dannyboy79 said:**
> this does make sense I suppose but why would a manufacturer use the same chipset which require different drivers? sounds like they should identify this so people know it's different than the original atheros chipset! oh well, now I know why people have been saying that there atheros chipset wifi card isn't working. Oh I should mention, my card has the AR5212 chipset, is that what yours has?

---

### Post by FrodoB on 2007-01-05
Here is another example of a Atheros device that will not yet work with mAdWiFi:

[http://ubuntuforums.org/showthread.php?t=308455&highlight=restricted-modules](http://ubuntuforums.org/showthread.php?t=308455&highlight=restricted-modules)

Note that post 18 and forward bear this out.

---

### Post by Herd on 2007-01-05
Now Im really confused... After rebooting this time wlan0 showed up and I was able to sucessfully set up my wireless again (posting on it now).  Im afraid to reboot.  Thanks for the responses.

---

### Post by gmatt on 2007-02-28
Hey,

I have a mac and I am trying to get ubuntu (6.10) working with my wireless card. I have it working, that is I can setup the ndiswrapper properly as per instructions earlier in this thread, but it seems to crash (literally lock up need to restart type crash) my system after a few minutes of modprobing it. Here is my cat /var/log/kern.log | grep ndis 

```

Feb 28 00:51:41 matt-laptop kernel: [17180024.260000] ndiswrapper version 1.37 loaded (preempt=no,smp=yes)
Feb 28 00:51:41 matt-laptop kernel: [17180024.380000] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
Feb 28 00:51:41 matt-laptop kernel: [17180024.528000] ndiswrapper: using IRQ 177
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ec71fb> wrap_miniport_timer+0x2b/0x80 [ndiswrapper]  <c01172c8> hpet_readl+0x8/0x10
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ecb2a0> timer_proc+0x50/0x70 [ndiswrapper]  <c012be69> run_timer_softirq+0x159/0x1a0
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ecb250> timer_proc+0x0/0x70 [ndiswrapper]  <c0127842> __do_softirq+0x72/0xe0
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ec9af0> ExAllocatePoolWithTag+0x30/0x160 [ndiswrapper]  <f8ec9b38> ExAllocatePoolWithTag+0x78/0x160 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ec61bf> NdisAllocateMemoryWithTag+0x1f/0x40 [ndiswrapper]  <f8ec61bf> NdisAllocateMemoryWithTag+0x1f/0x40 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ebfc99> KeStallExecutionProcessor+0x9/0x10 [ndiswrapper]  <c011b8e7> activate_task+0x67/0xb0
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ed3cb1> miniport_set_info+0xe1/0x290 [ndiswrapper]  <f8ec0259> set_essid+0x59/0xd0 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ed4f9d> NdisDispatchPnp+0xabd/0xd80 [ndiswrapper]  <f8ece122> IoAllocateIrp+0x62/0x90 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ecddca> IofCallDriver+0x3a/0xa0 [ndiswrapper]  <f8ed064b> IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ed0993> pnp_start_device+0x53/0xb0 [ndiswrapper]  <f8ed0bc3> wrap_pnp_start_device+0x1d3/0x2b0 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8ed0ce5> wrap_pnp_start_pci_device+0x45/0x50 [ndiswrapper]  <c0286498> netlink_broadcast+0x208/0x320
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <c01ee107> __pci_register_driver+0x47/0x70  <f8ec37b8> loader_init+0x138/0x260 [ndiswrapper]
Feb 28 00:51:51 matt-laptop kernel: [17180034.280000]  <f8dee0c7> wrapper_init+0xc7/0xd2 [ndiswrapper]  <c013cda8> sys_init_module+0x148/0x19c0
Feb 28 08:17:18 matt-laptop kernel: [17180459.240000] ndiswrapper: disagrees about version of symbol struct_module
Feb 28 17:28:31 matt-laptop kernel: [17213529.376000] ndiswrapper: disagrees about version of symbol struct_module
Feb 28 17:43:48 matt-laptop kernel: [17179849.488000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
Feb 28 17:43:48 matt-laptop kernel: [17179849.496000] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
Feb 28 17:43:49 matt-laptop kernel: [17179849.644000] ndiswrapper: using IRQ 177
Feb 28 17:43:49 matt-laptop kernel: [17179850.224000] usbcore: registered new driver ndiswrapper
Feb 28 17:56:58 matt-laptop kernel: [17179798.564000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
Feb 28 17:56:58 matt-laptop kernel: [17179798.652000] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
Feb 28 17:56:59 matt-laptop kernel: [17179798.800000] ndiswrapper: using IRQ 177
Feb 28 17:56:59 matt-laptop kernel: [17179799.384000] usbcore: registered new driver ndiswrapper
Feb 28 18:07:25 matt-laptop kernel: [17180039.236000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
Feb 28 18:07:25 matt-laptop kernel: [17180039.472000] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
Feb 28 18:07:26 matt-laptop kernel: [17180039.620000] ndiswrapper: using IRQ 177
Feb 28 18:07:26 matt-laptop kernel: [17180040.204000] usbcore: registered new driver ndiswrapper
Feb 28 19:14:23 matt-laptop kernel: [17179978.188000] ndiswrapper version 1.37 loaded (preempt=no,smp=no)
Feb 28 19:14:23 matt-laptop kernel: [17179978.408000] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
Feb 28 19:14:24 matt-laptop kernel: [17179978.564000] ndiswrapper: using IRQ 177
Feb 28 19:14:24 matt-laptop kernel: [17179979.148000] usbcore: registered new driver ndiswrapper

```

dmesg doesn't have anything usefull in it. Also, when I did the ndiswrapper -i *.inf step I get the following output:

```
sudo ndiswrapper -i net5416.inf 
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
```

which I find suspicious. Anyways any input is appreciated, otherwise I might have to go back to slow old OS X.

Here is my lspci ```
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
03:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
0c:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)

```

So does the message ```
Feb 28 08:17:18 matt-laptop kernel: [17180459.240000] ndiswrapper: disagrees about version of symbol struct_module
Feb 28 17:28:31 matt-laptop kernel: [17213529.376000] ndiswrapper: disagrees about version of symbol struct_module
``` mean that I am using the wrong windows driver? Im not sure how to check which driver i have as the lspci says unknown... Hmmm. I figured I had the same card as the poster but it may be different. Its weird though because the driver works fine for the few minutes that it does not lock up.

---

### Post by trubblemaker on 2007-03-01
hmm, do you have mad wifi setup aswell? it doesn't play nice with ndiswrapper. Just a thought

---

### Post by roadrash on 2008-02-05
All the info regarding the Atheros AR500G chipset is now out of date as there is now an offical native driver for this chipset in MadWiFI drivers.   Go here for instructions on how to install .


[http://ubuntuforums.org/showthread.php?t=683919]("http://ubuntuforums.org/showthread.php?t=683919")

---

