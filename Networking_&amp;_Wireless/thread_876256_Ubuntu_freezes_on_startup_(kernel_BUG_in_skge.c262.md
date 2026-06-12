---
title: "Ubuntu freezes on startup (kernel BUG in skge.c:2628?)"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by jlindbergh on 2008-07-31
Hi!
When starting my computer I get to the ubuntu splash screen, then to a light brown screen and then it becomes a hint darker and locks up. I can't get to TTY1-6 but it's possible to do a Ctrl-Alt-Bkspace though it won't get me to the login screen. It just tries to shutdown but hangs up, forcing me to do a reset. After that it boots into the desktop just fine!
It's a Core2Duo on an ASUS P5B Deluxe and the network adapter I'm using is a Marvell 88E8001 Gigabit controller.
uname -a says:
```
Linux jlindbergh-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
```

Of course I don't like having to boot my computer twice to get it usable, so I'm trying to do some research... I found this in the syslog:
```
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.982375] skge eth0: enabling interface
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985216] ------------[ cut here ]------------
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985219] kernel BUG at /build/buildd/linux-2.6.24/drivers/net/skge.c:2628!
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985222] invalid opcode: 0000 [#1] SMP 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985224] Modules linked in: af_packet rfcomm l2cap bluetooth ppdev snd_usb_audio snd_usb_lib ipv6 acpi_cpufreq cpufreq_conservative cpufreq_stats cpufreq_ondemand freq_table cpufreq_userspace cpufreq_powersave video output sbs sbshc dock container battery nls_utf8 cifs iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport joydev sr_mod cdrom snd_hda_intel snd_hwdep snd_pcm_oss snd_pcm snd_page_alloc snd_mixer_oss sky2 fglrx(P) snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd button intel_agp soundcore agpgart evdev iTCO_wdt iTCO_vendor_support shpchp pci_hotplug pcspkr ext3 jbd mbcache pata_jmicron sg sd_mod usb_storage libusual usbhid hid ata_generic floppy ohci1394 skge ieee1394 pata_acpi ahci libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985277] 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985279] Pid: 6160, comm: ifconfig Tainted: P        (2.6.24-19-generic #1)
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985281] EIP: 0060:[<f889bd09>] EFLAGS: 00010206 CPU: 1
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985288] EIP is at skge_up+0x7e9/0x820 [skge]
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985290] EAX: dfeda000 EBX: 00000000 ECX: 00000300 EDX: f88e8420
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985292] ESI: f74c5b40 EDI: f7492480 EBP: 00008000 ESP: f75bbe50
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985294]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985296] Process ifconfig (pid: 6160, ti=f75ba000 task=f71b4000 task.ti=f75ba000)
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985297] Stack: 00008000 f7492000 00000082 00000001 f7492480 00000000 f88e8000 f74c5b6c 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985303]        00000000 00000000 37100000 00000000 00000000 00000000 00000000 00000000 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985307]        00000000 f7104000 f7100000 f7492500 f7492480 00000000 00002888 00002800 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985312] Call Trace:
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985324]  [<f889d605>] skge_change_mtu+0x55/0x70 [skge]
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985331]  [dev_set_mtu+0x31/0x60] dev_set_mtu+0x31/0x60
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985336]  [dev_ioctl+0x246/0x500] dev_ioctl+0x246/0x500
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985348]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985353]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985359]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985364]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985368]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985377]  =======================
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985378] Code: ff 0f 0b eb fe 80 7e 19 06 0f 86 69 fb ff ff 8b 16 8b 82 5c 01 00 00 0d 00 02 00 02 89 82 5c 01 00 00 e9 51 fb ff ff 0f 0b eb fe <0f> 0b eb fe 8b 06 8b 88 20 01 00 00 c6 80 23 01 00 00 ff 8b 06 
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985405] EIP: [<f889bd09>] skge_up+0x7e9/0x820 [skge] SS:ESP 0068:f75bbe50
Jul 31 20:35:29 jlindbergh-desktop kernel: [   65.985412] ---[ end trace 6ad020d14b743723 ]---
```

It also seems that it tries to enable the interface a bit earlier:
```
Jul 31 20:35:24 jlindbergh-desktop kernel: [   60.804285] skge eth0: enabling interface
Jul 31 20:35:24 jlindbergh-desktop kernel: [   60.809617] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 31 20:35:24 jlindbergh-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'skge'. 
Jul 31 20:35:24 jlindbergh-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jul 31 20:35:24 jlindbergh-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jul 31 20:35:24 jlindbergh-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jul 31 20:35:24 jlindbergh-desktop NetworkManager: <info>  Deactivating device eth0.
``` ...but as you can see above it fails miserably.

This is what happens when I hit reset after it locks up - when all is good, and I get to the desktop. :)
```
Jul 31 20:40:03 jlindbergh-desktop kernel: [   58.568058] skge eth0: enabling interface
Jul 31 20:40:03 jlindbergh-desktop avahi-daemon[5318]: New relevant interface eth0.IPv4 for mDNS.
Jul 31 20:40:03 jlindbergh-desktop avahi-daemon[5318]: Registering new address record for 192.168.1.108 on eth0.IPv4.
Jul 31 20:40:03 jlindbergh-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Jul 31 20:40:03 jlindbergh-desktop NetworkManager: <info>  Deactivating device eth0. 
Jul 31 20:40:03 jlindbergh-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Jul 31 20:40:03 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Jul 31 20:40:03 jlindbergh-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Jul 31 20:40:03 jlindbergh-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6027
Jul 31 20:40:03 jlindbergh-desktop dhclient: killed old client process, removed PID file
Jul 31 20:40:03 jlindbergh-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Jul 31 20:40:03 jlindbergh-desktop avahi-daemon[5318]: Withdrawing address record for 192.168.1.108 on eth0.
Jul 31 20:40:03 jlindbergh-desktop avahi-daemon[5318]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.108.
Jul 31 20:40:03 jlindbergh-desktop avahi-daemon[5318]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 31 20:40:04 jlindbergh-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Jul 31 20:40:04 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Jul 31 20:40:04 jlindbergh-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Jul 31 20:40:04 jlindbergh-desktop avahi-daemon[5318]: Withdrawing address record for fe80::218:f3ff:fe4a:eab8 on eth0.
Jul 31 20:40:04 jlindbergh-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Jul 31 20:40:04 jlindbergh-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Jul 31 20:40:06 jlindbergh-desktop kernel: [   61.604833] skge eth0: Link is up at 1000 Mbps, full duplex, flow control both
Jul 31 20:40:06 jlindbergh-desktop kernel: [   61.606445] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) started... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Jul 31 20:40:06 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Jul 31 20:40:07 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Jul 31 20:40:07 jlindbergh-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Jul 31 20:40:07 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Jul 31 20:40:07 jlindbergh-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Jul 31 20:40:07 jlindbergh-desktop avahi-daemon[5318]: Registering new address record for fe80::218:f3ff:fe4a:eab8 on eth0.*.
Jul 31 20:40:08 jlindbergh-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Jul 31 20:40:12 jlindbergh-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jul 31 20:40:12 jlindbergh-desktop dhclient: DHCPOFFER of 192.168.1.108 from 192.168.1.1
Jul 31 20:40:12 jlindbergh-desktop dhclient: DHCPREQUEST of 192.168.1.108 on eth0 to 255.255.255.255 port 67
Jul 31 20:40:12 jlindbergh-desktop dhclient: DHCPACK of 192.168.1.108 from 192.168.1.1
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.108.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: New relevant interface eth0.IPv4 for mDNS.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Registering new address record for 192.168.1.108 on eth0.IPv4.
Jul 31 20:40:12 jlindbergh-desktop dhclient: bound to 192.168.1.108 -- renewal in 42618 seconds.
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Jul 31 20:40:12 jlindbergh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 31 20:40:12 jlindbergh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 31 20:40:12 jlindbergh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 31 20:40:12 jlindbergh-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    address 192.168.1.108 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    netmask 255.255.255.0 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    gateway 192.168.1.1 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    nameserver 81.26.227.3 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    nameserver 195.54.122.204 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>    nameserver 81.26.228.3 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Jul 31 20:40:12 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Withdrawing address record for 192.168.1.108 on eth0.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.108.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Interface eth0.IPv4 no longer relevant for mDNS.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Withdrawing address record for fe80::218:f3ff:fe4a:eab8 on eth0.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.108.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: New relevant interface eth0.IPv4 for mDNS.
Jul 31 20:40:12 jlindbergh-desktop avahi-daemon[5318]: Registering new address record for 192.168.1.108 on eth0.IPv4.
Jul 31 20:40:13 jlindbergh-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Jul 31 20:40:13 jlindbergh-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Jul 31 20:40:13 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Jul 31 20:40:13 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Jul 31 20:40:13 jlindbergh-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
```

Any suggestions on what to do to get it to successfully boot on the first try? What's up with the *"kernel BUG at /build/buildd/linux-2.6.24/drivers/net/skge.c:2628!"*? 
Btw, the interface is connected to a D-Link DGS 1005D (greenline). Don't know if that's relevant or not, but now you know! :)

Thanks in advance!
/jl

PS. saw this related too: [http://ubuntuforums.org/showthread.php?p=4714891](http://ubuntuforums.org/showthread.php?p=4714891)

---

### Post by jlindbergh on 2008-08-04
Excuse the bump. 
I still haven't had any luck getting the computer to startup properly. Last time it didn't even start after I hit reset the first time and I thought I was screwed. Luckily it started ok the third time i resetted it..

---

### Post by warpuck on 2008-08-24
I dont know if this is a kernal freeze or Xwindows freeze.

To take control of the GUI

Try using control, alt and plus on keypad, wait till the screen flashes (you may not notice this on a LCD screen)if no change repeat two or three times. I believe this askes the kernal to switch video modes. You may end up with low res (800 x 600) but it will get you online and give you some thing to work with. If that doesnt work,(this command appears to shutsdown the gui) Control, Alt and Backspace will bring you back to command line. (unless the kernal froozed)((now that I reread this you dood this before already))

It should put you back to keybord only land. You Know. That place you start the OS from, that happens before you or the system do the startx command. 
and u shoulds see this 

$
or
#
startx
(this may bring up the gui) 
on other systems try 
xwin

note you need to be root or sudo to make video changes.

Note for jlindstrom:
Take two aspirin and fumble around with apt-get and gedit on the conf files. There is lots of help with that in this forum.
As long as you can get the recovery to boot there is hope (the second line in grub boot loader)

   I had the same thing happen after I replaced a Nvidia 6200 with a ATI radeon X1800 dual head without removing the Nvidia driver first (big WHOOPSEY)

Note the GUI crashed hard twice on me because I wanted the dual head thing to work, for now I get double vision, aka same thing on both monitors. That doesnt stop from searching. If winders kin doit Linux kin doit betterer

Mote: I am not knocking your ability, but someone who has strayed from the Redmond Borg Hive reading this may not understand what is obvious to a Linux Shellback.
_________________________________________________________________
There is more than one way to skin a cat. Dont be suprised if the cat isnt happy to see you after the second or third try. I never said cats were smart.

---

