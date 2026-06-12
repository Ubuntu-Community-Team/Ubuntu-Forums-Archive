---
title: "Belkin F5D7010UK v7000 Wireless Cardbus"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by essexboyracer on 2007-03-15
Hi all, i have an old PIII Tiny laptop with edgy eft that am trying to get a Belkin F5D7010UK v7000 Wireless Cardbus working in.

Having read numerous posts on the F5D7010, it seems belkin change the chipset used in the cards almost with every new version. I havnt found a thread on here specifically for a rev7000 yet, which, from a readme file on the install CD, seems to point to it having a Realtek 818x chipset and from further research on [www.realtek.com.tw](www.realtek.com.tw), it is specifically the 8185 (although I could be wrong).

Realtek do have linux drivers available, but I havnt tried those yet, instead going the ndiswrapper route. I have only tries the inf file from the original install CD, doing it manually as well as through ndisgtk, ndiswrapper reports driver installed and hardware present, but there are no lights on the card. I did see a message i think in dmesg saying the card had no power?

has any one else tried this version or have any pointers?

---

### Post by teaker1s on 2007-03-16
ndisgtk could be your problem, I advise you "cd"  into directory containing driver and all driver related files and use terminal to install driver


first try 
```
sudo modprobe ndiswrapper
```
```
iwconfig
``` can we see wireless running-post output

terminal commands for ndiswrapper
```
sudo ndiswrapper -r nameofdriver
``` removal of driver
```
sudo ndiswrapper -i nameofdriver.inf
``` install driver
```
sudo ndiswrapper -l
``` list installed driver/hardware
you may also want to check and install the latest version of ndiswrapper-utils
```
gksudo synaptic
```

---

### Post by essexboyracer on 2007-03-17
I also found another thread on here trying the same chipset, but in the PCI version, [http://www.ubuntuforums.org/showthread.php?t=381878&highlight=realtek]("http://www.ubuntuforums.org/showthread.php?t=381878&highlight=realtek") here is some output from sudo dmesg....

[17180563.836000] CPU:    0
[17180563.836000] EIP:    0060:[<d04a5239>]    Tainted: P      VLI
[17180563.836000] EFLAGS: 00010202   (2.6.17-11-386 #2) 
[17180563.836000] EIP is at 0xd04a5239
[17180563.836000] eax: 00000000   ebx: 00000000   ecx: 0000003d   edx: d04cfe52
[17180563.836000] esi: d057681a   edi: d04e003d   ebp: c8bc7c98   esp: c8bc7c8c
[17180563.836000] ds: 007b   es: 007b   ss: 0068
[17180563.836000] Process pccardd (pid: 2687, threadinfo=c8bc6000 task=c8b8d540)
[17180563.836000] Stack: d057681a d04eb000 d04d6271 c8bc7d00 d04a560f d057681a d04d4980 0000003d 
[17180563.836000]        00000000 00000000 cc018680 c01056fe c0103e8a d04eb000 c8063e60 cc018680 
[17180563.836000]        00000000 000000c7 00000003 c0000001 d037ffdf d0380c40 d04ebaac c8bc7d1c 
[17180563.836000] Call Trace:
[17180563.836000]  <c01056fe> do_IRQ+0x1e/0x30  <c0103e8a> common_interrupt+0x1a/0x20
[17180563.836000]  <d037ffdf> NdisInitializeEvent+0x1f/0x30 [ndiswrapper]  <d0380c40> NdisAllocateSpinLock+0x10/0x20 [ndiswrapper]
[17180563.836000]  <d0390c94> miniport_init+0xa4/0x150 [ndiswrapper]  <d0390e06> NdisDispatchPnp+0xa6/0x8c0 [ndiswrapper]
[17180563.836000]  <d03849dd> get_current_nt_thread+0xad/0x130 [ndiswrapper]  <d038a05a> IoAllocateIrp+0x5a/0x90 [ndiswrapper]
[17180563.836000]  <d038ad4c> IoQueueThreadIrp+0x1c/0x140 [ndiswrapper]  <d0389d36> IofCallDriver+0x36/0x70 [ndiswrapper]
[17180563.836000]  <d038f42b> IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]  <d038f710> pnp_start_device+0x50/0xb0 [ndiswrapper]
[17180563.836000]  <d038f92a> wrap_pnp_start_device+0x1ba/0x290 [ndiswrapper]  <c01d5ac6> pci_device_probe+0x56/0x80
[17180563.836000]  <c022acb4> driver_probe_device+0x44/0xc0  <c02c50f1> klist_next+0x31/0x50
[17180563.836000]  <c022a544> bus_for_each_drv+0x44/0x70  <c022ada6> device_attach+0x66/0x70
[17180563.836000]  <c022ad30> __device_attach+0x0/0x10  <c022a418> bus_add_device+0x28/0x110
[17180563.836000]  <c02295f4> device_add+0xf4/0x150  <c01d1c4b> pci_bus_add_device+0xb/0x30
[17180563.836000]  <c01d1caf> pci_bus_add_devices+0x3f/0xc0  <d00d51a8> cb_alloc+0x98/0xd0 [pcmcia_core]
[17180563.836000]  <d00d17e7> socket_insert+0x97/0xe0 [pcmcia_core]  <d00d1c51> pccardd+0x221/0x240 [pcmcia_core]
[17180563.836000]  <c0115da0> default_wake_function+0x0/0x10  <d00d1a30> pccardd+0x0/0x240 [pcmcia_core]
[17180563.836000]  <c0101005> kernel_thread_helper+0x5/0x10 
[17180563.836000] Code: 04 00 cc cc cc cc cc cc 8b ff 55 8b ec 56 8b 75 08 57 66 8b 7d 10 0f b7 cf 33 c0 85 c9 7e 15 53 8b 55 0c 8b 52 04 8a 14 42 8b 1e <88> 14 18 40 3b c1 7c ed 5b 66 89 7e 04 5f 33 c0 5e 5d c2 0c 00 
[17180563.836000] EIP: [<d04a5239>] 0xd04a5239 SS:ESP 0068:c8bc7c8c
[17180563.836000]

---

### Post by teaker1s on 2007-03-17
okay I see that the device is trying to start, but we need to see output of
iwconfig so 
```
sudo modprobe ndiswrapper
```
```
iwconfig
```

---

### Post by essexboyracer on 2007-03-17
```
oliver@ubuntu610:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

---

### Post by teaker1s on 2007-03-17
if the output of this gives you harware present :driver present then It may still be possible to get it working with ndiswrapper
```
sudo ndiswrapper -l 
```
thats a small L not i

---

### Post by essexboyracer on 2007-03-17
```
oliver@ubuntu610:~$ sudo ndiswrapper -l
Installed drivers:
blkwgnv7                driver installed 

```

---

### Post by teaker1s on 2007-03-17
okay well we have driver present-generally a better sign than invalid driver:) 

I'm taking a leap at this as normally we hope to see hardware present as well-my prior experience tells me that it could be just that you are missing " ndiswrapper-utils" latest version.

**if you have ethernet internet**
```
gksudo synaptic
```
hit reload tab
search "ndiswrapper" you want to tick and install related ndiswrapper packages including latest ndiswrapper-utils-1.8 (you may find it's now 1.9)
[B]
without internet access[/B]
```
gksudo synaptic
```
hit edit tab and select add cdrom (you want your ubuntu install cd, place in drive and allow ubuntu to read it)
hit reload tab
search "ndiswrapper" you want to tick and install related ndiswrapper packages including latest ndiswrapper-utils-1.8 (you may find it's now 1.9)



reboot

```
sudo modprobe ndiswrapper
``` hopefully we get no errors
```
sudo ndiswrapper -l
``` if you see hardware present and driver present then
```
iwconfig 
``` post output

If you can't see driver and hardware present, either a driver known to work(look on ndiswrapper sourceforge wiki) generally unless anyone viewing the tread has more idea's with ndiswrapper
:- you will possibly need linux drivers

---

### Post by essexboyracer on 2007-03-17
thank you teaker, i already had 1.8 ndis installed and have previously tried the chipset vendors drivers, no joy. I think i am going to leave this one now. I have a SAFECOM branded zd1211b USB adaptor which at least shows up in the network settings gui :) on this default edgy install. Haven't got it connected yet, but with the help of google and (may i say) these excellent forums i am sure i can discover it. 

Whilst I dont fully understand linux filesystem makeup in the same general way as windows, i have 'flirted' with various distros over the years (FC3/4, slax (which is lovely I have to say), slackware 10, various livecd's (recommed the gparted livecd) ubuntu hoary, dapper and now edgy) and am building some good knowledge. I have a fairly good grip on using linux in a shared hosting environment.

Thank you all for your help, out of the limited distros I have tried ubuntu i would say is by far the best, not sure why, the whole thing seems simpler/uncluttered in some way. Just wish I could get gnome running a bit faster on my ageing TINY PIII laptop (hoary speed was good)

---

### Post by GS2 on 2007-04-04
[http://ubuntuforums.org/showpost.php?p=2402378&postcount=16](http://ubuntuforums.org/showpost.php?p=2402378&postcount=16)

Worked like a treat for me - send me a message if you need more help

---

