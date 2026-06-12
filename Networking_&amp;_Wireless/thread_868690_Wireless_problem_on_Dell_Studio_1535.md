---
title: "Wireless problem on Dell Studio 1535"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by dubbeld88 on 2008-07-24
**Problem:**
I can't connect to a wireless network. Drivers are installed. I can see the wireless networks though.

**What did I tried:**
When I try to connect to a Wireless network using the Automatic Network configuration, the system will crash. (mouse/keyboard input still working, but I can't execute anything)

When I use the manual configuration, the system won't crash directly, but never connects to the wireless network (it's not in the Device list of my router). And when I wait a couple of minutes, this will also hang my PC. When I reboot, Ubuntu will stop working (I have to remove ndiswrapper (rmmod it)).

**How is my Wireless card installed:**
Using ndiswrapper, with the BCMWL5 driver from HP. (See also [this thread](http://ubuntuforums.org/showthread.php?p=5419638).)

**Are there any error's:**
dmesg is filled with "error's",
Call Trace:
[<fffffffffff882b64db>] :ndiswrapper:win2lin3+0x11/0x14

but non are very usefull if you ask me... It will detect wlan0 (it's also in ifconfig).

and that every 3 seconds.

**Used versions:**
ndiswrapper: 1.52
ubuntu: 8.04 x64
driver: BCMWL5
chip: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

I hope someone has a solution to this problem...

---

### Post by Ayuthia on 2008-07-24
> **dubbeld88 said:**
> **Problem:**
I can't connect to a wireless network. Drivers are installed. I can see the wireless networks though.

**What did I tried:**
When I try to connect to a Wireless network using the Automatic Network configuration, the system will crash. (mouse/keyboard input still working, but I can't execute anything)

When I use the manual configuration, the system won't crash directly, but never connects to the wireless network (it's not in the Device list of my router). And when I wait a couple of minutes, this will also hang my PC. When I reboot, Ubuntu will stop working (I have to remove ndiswrapper (rmmod it)).

**How is my Wireless card installed:**
Using ndiswrapper, with the BCMWL5 driver from HP. (See also [this thread](http://ubuntuforums.org/showthread.php?p=5419638).)

**Are there any error's:**
dmesg is filled with "error's",
Call Trace:
[<fffffffffff882b64db>] :ndiswrapper:win2lin3+0x11/0x14

but non are very usefull if you ask me... It will detect wlan0 (it's also in ifconfig).

and that every 3 seconds.

**Used versions:**
ndiswrapper: 1.52
ubuntu: 8.04 x64
driver: BCMWL5
chip: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

I hope someone has a solution to this problem...

If you look through the dmesg results a little more, do you see anything about bad magic?  I am thinking that you are trying to use a 32-bit driver on a 64-bit system.  I could be wrong though.  If you are not for sure, please try and attach your dmesg results:
```
dmesg > $HOME/Desktop/forumdmesg.txt
```
This will create a file that contains the results of dmesg on your desktop.  Just take that file and attach it to your post.  Hopefully there is some information that might help in figuring out what is happening.

---

### Post by dubbeld88 on 2008-07-24
Everything stops working after the driver crashes, I only see it on display, but it won't be written to the HardDisk anymore (guess the whole HD stops working, because I also can't run any programs).

Can't find much in dmesg, but kern.log has more information: 

```
[   97.209601] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   97.222825] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   97.227658] ndiswrapper: driver bcmwl5 (Broadcom,03/21/2008, 4.170.77.3) loaded
[   97.228031] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   97.228170] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   97.242460] ndiswrapper: using IRQ 17
[   97.277866] wlan0: ethernet device 00:1f:e1:c6:d5:b3 using NDIS driver: bcmwl5, version: 0x4aa4d03, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:432B.5.conf
[   97.277952] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   97.290672] usbcore: registered new interface driver ndiswrapper
[   97.306902] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  124.076675] NET: Registered protocol family 17
[  124.451022] general protection fault: 0000 [1] SMP 
[  124.451030] CPU 1 
[  124.451032] Modules linked in: af_packet ndiswrapper ipv6 binfmt_misc hci_usb rfcomm l2cap bluetooth ppdev acpi_cpufreq cpufreq_powersave cpufreq_ondemand cpufreq_stats freq_table cpufreq_userspace cpufreq_conservative container dock sbs sbshc iptable_filter ip_tables x_tables sbp2 parport_pc lp parport joydev uvcvideo serio_raw dcdbas pcspkr psmouse compat_ioctl32 videodev v4l1_compat v4l2_common evdev fglrx(P) sdhci mmc_core snd_hda_intel snd_pcm_oss snd_mixer_oss snd_seq_dummy ricoh_mmc snd_seq_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_midi snd_rawmidi snd_seq_midi_event video snd_seq output snd_timer snd_seq_device wmi_acer snd soundcore button battery ac shpchp pci_hotplug iTCO_wdt iTCO_vendor_support intel_agp ext3 jbd mbcache sg sr_mod cdrom sd_mod usbhid hid ohci1394 ieee1394 ahci libata scsi_mod tg3 ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  124.451120] Pid: 6583, comm: ntos_wq Tainted: P        2.6.24-19-generic #1
[  124.451123] RIP: 0010:[ip_tables:__mod_vermagic5+0x1078dbb/0x7f09cc10]  [ip_tables:__mod_vermagic5+0x1078dbb/0x7f09cc10]
[  124.451129] RSP: 0018:ffff8100c77d5a78  EFLAGS: 00010286
[  124.451132] RAX: ffff8100c77d5b80 RBX: ffffc20002028000 RCX: ffffc20002028000
[  124.451135] RDX: 0000000000000001 RSI: 0000000000000001 RDI: ffff8100d0ac2b00
[  124.451138] RBP: ffff8100d0ac5f00 R08: 0000000000000003 R09: 000000000000000c
[  124.451141] R10: ffffc200022c8840 R11: ffffc20001313af0 R12: ffffc20001313af0
[  124.451143] R13: 0000000000000000 R14: 0000000000000000 R15: 00000000000000ff
[  124.451147] FS:  0000000000000000(0000) GS:ffff81011bc01800(0000) knlGS:0000000000000000
[  124.451150] CS:  0010 DS: 0018 ES: 0018 CR0: 0000000080050033
[  124.451153] CR2: 0000000000670800 CR3: 0000000118d7a000 CR4: 00000000000006e0
[  124.451156] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  124.451159] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  124.451162] Process ntos_wq (pid: 6583, threadinfo ffff8100c77d4000, task ffff8100dc1a8fc0)
[  124.451164] Stack:  ffffc200020281e3 ffffc200ffffffff ffff810084020402 ffffc20002028000
[  124.451171]  0000000000000008 ffffc200020281e3 ffff8100c776703e ffffc2000220c0b5
[  124.451176]  ffffc20002028101 0000000000000000 000000000000002d ffffc20002028000
[  124.451181] Call Trace:
[  124.451275]  [<ffffffff885fb4db>] :ndiswrapper:win2lin3+0x11/0x14
[  124.451309]  [<ffffffff885fb4db>] :ndiswrapper:win2lin3+0x11/0x14
[  124.451342]  [default_idle+0x0/0x40] default_idle+0x0/0x40
[  124.451380]  [<ffffffff885ec7a1>] :ndiswrapper:kdpc_worker+0xc1/0x140
[  124.451390]  [snd_pcm:mutex_lock+0x9/0x350] mutex_lock+0x9/0x20
[  124.451416]  [<ffffffff885ec788>] :ndiswrapper:kdpc_worker+0xa8/0x140
[  124.451443]  [<ffffffff885ec6e0>] :ndiswrapper:kdpc_worker+0x0/0x140
[  124.451449]  [run_workqueue+0xcc/0x170] run_workqueue+0xcc/0x170
[  124.451453]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
[  124.451460]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
[  124.451465]  [worker_thread+0xa3/0x110] worker_thread+0xa3/0x110
[  124.451472]  [<ffffffff80253a00>] autoremove_wake_function+0x0/0x30
[  124.451479]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
[  124.451485]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
[  124.451490]  [kthread+0x4b/0x80] kthread+0x4b/0x80
[  124.451496]  [child_rip+0xa/0x12] child_rip+0xa/0x12
[  124.451513]  [kthread+0x0/0x80] kthread+0x0/0x80
[  124.451518]  [child_rip+0x0/0x12] child_rip+0x0/0x12
[  124.451523] 
[  124.451525] 
[  124.451525] Code: 0f 29 70 c8 48 8b 05 fa ae 0f 00 48 33 c4 48 89 84 24 c0 00 
[  124.451538] RIP  [ip_tables:__mod_vermagic5+0x1078dbb/0x7f09cc10]
[  124.451542]  RSP <ffff8100c77d5a78>
[  124.451546] ---[ end trace e24d5241c1f1b0f9 ]---
```
After the [ end trace ] there isn't data been written to this file (on screen it will repeat the call trace). PC is still listening to input, but I can't access anything from the harddrive (commands and programs also don't work anymore).

This is only when I activate ndiswrapper and connect to a network. ndiswrapper is able to see networks though... Btw, bcmwl564.sys is also in the package... I hope it will autoselect it... (don't know for sure).

Edit: [I know for sure](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=616801), here it is working on a x64bit system, only thing is, he is using revision 0, which won't work on my laptop, only rev3 and up.

I'm using the hp driver (sp39243) which is working on other dell studio's (see link in my first post).

---

### Post by Ayuthia on 2008-07-24
You might try the driver in this link:
[http://ubuntuforums.org/showthread.php?t=850913](http://ubuntuforums.org/showthread.php?t=850913)
You also might want to try and compile 1.53.  The information in dmesg is showing that ndiswrapper crashed.  I am guessing that is because there was some incompatibility with the driver.  Hopefully a newer version of ndiswrapper will fix the problem or you might try a different driver.

Another thing that might cause the issue is if you are using any kernel boot parameters (noapic, apic=off, etc).  Sometimes that can cause the issue also.

---

### Post by dubbeld88 on 2008-07-24
Tnx I'm going to try and compile version 1.53 (already tried it, but then also had the idea to update to the development version of ubuntu (which wasn't a good idea (X11 didn't reconize my screen)).

Will try it again, and will continue in the other topic (since they are having the same problem)

Thanks for helping! (didn't saw that topic)

---

### Post by Kevin Aylesworth on 2008-08-12
I have a Dell 1535 with the Dell Wireless 1397 802.11b/g Half Mini Card. I had success with the instructons at this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Use option 2e.

Right after a fresh install of Ubuntu, the wireless model is listed as BCM4310 XXXXXXX (rev 01).  I applied all updates then rebooted. 
When the computer came back up, the wl driver took control of the wireless and 

lspci | grep Broadcom returns: 
Broadcom Corporation BCM4312 802.11b/g (rev 01). I disabled the wl driver and rebooted. All has been fine since.

---

