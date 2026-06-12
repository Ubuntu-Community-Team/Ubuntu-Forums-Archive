---
title: "Fully Restart an Interface or Networking"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by MaindotC on 2008-10-14
I'm using the [Belkin F5D7050](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211) wireless USB adapter with the [b43](http://linuxwireless.org/en/users/Drivers/b43) driver installed.  Sometimes, very rarely, this interface will no longer function and the LED remains illuminated to indicate it is not sending or receiving traffic.  I would like to know how to properly restart an interface if there is a method other than rebooting.  I've used the following to no avail:
```

sudo /etc/init.d/networking restart

```

Whenever I execute this command it definitely doesn't seem to take any effect.  For example, my wireless adapter does not disconnect from the access point and then reconnect.  What is the proper way to restart an interface - perhaps to have it recycle its power but not my entire machine?  Thanks!

---

### Post by hyper_ch on 2008-10-14
if that happens, can you run this command:

```

iwconfig

```

and post the output?

---

### Post by rlzyoner on 2008-10-14
Why don't you try 

Stop the interface
[PHP]sudo ifconfig interface down [/PHP]

Then start it again
[PHP]sudo ifconfig interface up[/PHP]

---

### Post by intel17 on 2008-10-14
I have the same problem with my laptop using the b43 driver.  I thought it was the wifi adapter dieing or something.  I have tried:

```
sudo ifconfig wlan0 down; sudo ifconfig wlan0 up
```

But that did not help, also the strength level meter vanished and turned into the normal wired network logo of two computers.

---

### Post by MaindotC on 2008-10-14
hyper_ch - it only happens once a week or so but I'll try and remember to post the output once that happens.  I should have thought of that myself.

intel17 - ha that happens to me too!  All the wireless networks disappear from the drop-down menu and I get the wired network icon.  Hilarious!

rlzyoner - I tried that command on a different machine and at the time it didn't seem to do the trick but I just tested on my laptop and it definitely brought the interface down but it doesn't seem to go back up with the "up" command.  What I did, though, is re-select the same network from the wireless drop-down menu and that reconnected everything.  This helps.

What I'm looking for is something to turn off the interfaces LED and then turn it back on :)  I think this is as close as I'll get w/o rebooting the machine.

This is very helpful, though, and thank you all.  I'm going to try reconnecting my N adapter (noted in [this thread](http://ubuntuforums.org/showpost.php?p=5901100&postcount=7)) and seeing if I can do anything to keep it running after about an hour.  Thanks!

---

### Post by MaindotC on 2008-10-14
Eh - had this problem so here's some troubleshooting I did right as the LED on the interface went solid.  Hope this can help you help me:
```

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"MSCt61"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:E6:E3:7E:02   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

amd64@amd64-desktop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:50:8d:d1:65:b4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:7077 (6.9 KB)
          Interrupt:22 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1954 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103900 (101.4 KB)  TX bytes:103900 (101.4 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1e:e5:dc:f8:e7  
          inet addr:136.204.225.125  Bcast:136.204.239.255  Mask:255.255.240.0
          inet6 addr: fe80::21e:e5ff:fedc:f8e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68459 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166575588 (158.8 MB)  TX bytes:5656203 (5.3 MB)

sudo ifconfig wlan1 down
sudo ifconfig wlan1 down up (this was a mistake)
sudo /etc/init.d/networking restart
sudo ifconfig wlan1 up (corrected my mistake)
sudo /etc/init.d/networking restart
sudo ifconfig wlan1 down

```

Removed WUSB600N
Network-Manager icon settled on wired network
Plugged WUSB600N back in - no light

```

sudo ifconfig wlan1 up
sudo /etc/init.d/networking restart
ifconfig
amd64@amd64-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:d1:65:b4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12764 (12.4 KB)
          Interrupt:22 Base address:0xd000 

eth0:avahi Link encap:Ethernet  HWaddr 00:50:8d:d1:65:b4  
          inet addr:169.254.8.246  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107981 (105.4 KB)  TX bytes:107981 (105.4 KB)

sudo ifconfig eth0 up

```

Still no light.

lsusb yields a blinking cursor and no output.  Logged in as root on tty2 and did lsusb - still blinking cursor and no output.  Logged in as root on tty3, did /etc/init.d/networking restart, ifconfig showed eth0 this time (no avahi this time), but no wireless extensions.

This was an interesting entry in my syslog:

```

Oct 14 12:39:01 amd64-desktop /USR/SBIN/CRON[6512]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Oct 14 12:39:01 amd64-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.reason
Oct 14 12:39:01 amd64-desktop NetworkManager: <debug> [1224002341.565271] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'MSCt61' 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan1 / MSCt61 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Deactivating device wlan1. 
Oct 14 12:39:01 amd64-desktop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan1: Invalid argument 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Device wlan1 activation scheduled... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 14 12:39:01 amd64-desktop avahi-daemon[5118]: Withdrawing address record for 169.254.8.246 on eth0.
Oct 14 12:39:01 amd64-desktop avahi-daemon[5118]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.8.246.
Oct 14 12:39:01 amd64-desktop avahi-daemon[5118]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) started... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) started... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 1 of 5 (Device Prepare) complete. 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) starting... 
Oct 14 12:39:01 amd64-desktop NetworkManager: <info>  Activation (wlan1/wireless): access point 'MSCt61' is unencrypted, no key needed. 
Oct 14 12:39:02 amd64-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 14 12:39:03 amd64-desktop kernel: [  152.424411] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  kernel_driver for non broadcast check: ndiswrapper (has_scan_capa_ssid=0) 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  Using plain AP_SCAN 2 for ndiswrapper 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was '0' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4d5343743631' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  Activation (wlan1) Stage 2 of 5 (Device Configure) complete. 
Oct 14 12:39:03 amd64-desktop NetworkManager: <info>  Old device 'wlan1' activating, won't change. 
Oct 14 12:39:04 amd64-desktop avahi-daemon[5118]: Registering new address record for fe80::21e:e5ff:fedc:f8e7 on wlan1.*.
Oct 14 12:39:13 amd64-desktop kernel: [  156.718446] wlan1: no IPv6 routers present
Oct 14 12:39:29 amd64-desktop kernel: [  163.221662] Unable to handle kernel NULL pointer dereference at 0000000000000010 RIP: 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221667]  [ndiswrapper:IofCompleteRequest+0xe5/0x180] :ndiswrapper:IofCompleteRequest+0xe5/0x180
Oct 14 12:39:29 amd64-desktop kernel: [  163.221687] PGD 117b64067 PUD 117aef067 PMD 0 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221689] Oops: 0002 [1] SMP 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221691] CPU 0 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221692] Modules linked in: isofs udf binfmt_misc af_packet rfcomm l2cap bluetooth vboxdrv ppdev ipv6 powernow_k8 cpufreq_userspace cpufreq_powersave cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table video output dock container sbs sbshc battery iptable_filter ip_tables x_tables aes_x86_64 dm_crypt dm_mod ac sbp2 lp qcmessenger gspca compat_ioctl32 usbhid parport_pc parport snd_usb_audio videodev hid snd_usb_lib v4l2_common v4l1_compat snd_hwdep ndiswrapper evdev fglrx(P) snd_via82xx gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi serio_raw snd_seq_midi_event psmouse snd_seq snd_timer snd_seq_device button shpchp k8temp i2c_viapro pcspkr pci_hotplug snd i2c_core soundcore ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi floppy pata_via sata_via ehci_hcd uhci_hcd ata_generic usbcore libata scsi_mod via_velocity crc_ccitt ohci1394 ieee1394 thermal processor fan fb
Oct 14 12:39:29 amd64-desktop kernel: on tileblit font bitblit softcursor fuse
Oct 14 12:39:29 amd64-desktop kernel: [  163.221730] Pid: 3216, comm: ntos_wq Tainted: P        2.6.24-19-generic #1
Oct 14 12:39:29 amd64-desktop kernel: [  163.221732] RIP: 0010:[ndiswrapper:IofCompleteRequest+0xe5/0x180]  [ndiswrapper:IofCompleteRequest+0xe5/0x180] :ndiswrapper:IofCompleteRequest+0xe5/0x180
Oct 14 12:39:29 amd64-desktop kernel: [  163.221747] RSP: 0018:ffff810128fcbe40  EFLAGS: 00010202
Oct 14 12:39:29 amd64-desktop kernel: [  163.221748] RAX: 0000000000000000 RBX: ffff810129c23e00 RCX: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221750] RDX: 0000000000000010 RSI: 0000000000000002 RDI: 0000000000000002
Oct 14 12:39:29 amd64-desktop kernel: [  163.221752] RBP: ffff810129c23f60 R08: 0000000000000000 R09: ffff81012feb99c8
Oct 14 12:39:29 amd64-desktop kernel: [  163.221753] R10: ffff810001025fe0 R11: 0000000000000001 R12: ffff810128fcbe4f
Oct 14 12:39:29 amd64-desktop kernel: [  163.221755] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221757] FS:  00007f87f2e236e0(0000) GS:ffffffff805b9000(0000) knlGS:00000000f7e018c0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221758] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Oct 14 12:39:29 amd64-desktop kernel: [  163.221760] CR2: 0000000000000010 CR3: 0000000117b3b000 CR4: 00000000000006e0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221761] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221763] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 14 12:39:29 amd64-desktop kernel: [  163.221765] Process ntos_wq (pid: 3216, threadinfo ffff810128fca000, task ffff8101298107e0)
Oct 14 12:39:29 amd64-desktop kernel: [  163.221766] Stack:  0000000000000000 00ff810128fcd600 ffff810129c23e00 ffff81012a770cc0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221769]  ffff81012a1fb818 ffff81012894a788 0000000000000000 ffffffff88495408
Oct 14 12:39:29 amd64-desktop kernel: [  163.221772]  ffff81012894a780 ffffffff884953c0 ffff81012894a780 ffffffff8024f2bc
Oct 14 12:39:29 amd64-desktop kernel: [  163.221774] Call Trace:
Oct 14 12:39:29 amd64-desktop kernel: [  163.221795]  [ndiswrapper:wrap_urb_complete_worker+0x48/0x120] :ndiswrapper:wrap_urb_complete_worker+0x48/0x120
Oct 14 12:39:29 amd64-desktop kernel: [  163.221810]  [ndiswrapper:wrap_urb_complete_worker+0x0/0x120] :ndiswrapper:wrap_urb_complete_worker+0x0/0x120
Oct 14 12:39:29 amd64-desktop kernel: [  163.221816]  [run_workqueue+0xcc/0x170] run_workqueue+0xcc/0x170
Oct 14 12:39:29 amd64-desktop kernel: [  163.221818]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221821]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221824]  [worker_thread+0xa3/0x110] worker_thread+0xa3/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221828]  [<ffffffff80253a00>] autoremove_wake_function+0x0/0x30
Oct 14 12:39:29 amd64-desktop kernel: [  163.221832]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221836]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221838]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Oct 14 12:39:29 amd64-desktop kernel: [  163.221842]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Oct 14 12:39:29 amd64-desktop kernel: [  163.221853]  [kthread+0x0/0x80] kthread+0x0/0x80
Oct 14 12:39:29 amd64-desktop kernel: [  163.221856]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Oct 14 12:39:29 amd64-desktop kernel: [  163.221860] 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221860] 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221861] Code: 89 02 48 8b 43 38 48 8b 53 48 48 89 42 08 48 8b 7b 50 48 85 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221865] RIP  [ndiswrapper:IofCompleteRequest+0xe5/0x180] :ndiswrapper:IofCompleteRequest+0xe5/0x180
Oct 14 12:39:29 amd64-desktop kernel: [  163.221880]  RSP <ffff810128fcbe40>
Oct 14 12:39:29 amd64-desktop kernel: [  163.221881] CR2: 0000000000000010
Oct 14 12:39:29 amd64-desktop kernel: [  163.221883] ---[ end trace 4b5e77df13797eba ]---

```

Rebooted.

---

### Post by hyper_ch on 2008-10-14
well, the rate is 54M... that's good... here it gets resetted to 1M sometimes and then the whole connection drops dead and I have not found out yet why.

---

### Post by Mazin on 2008-10-14
Hi.  On my laptop, doing
```
sudo ifdown wlan0
```
will disable the adapter and release and DHCP leases,
and ```
sudo ifup wlan0
```
will re-enable the adapter, have it reconnect, and renew its lease.  I don't see why it wouldn't work.

---

### Post by MaindotC on 2008-10-14
hyper_ch - thanks for the heads up and I'll let you know if I ever see that.

Mazin - thank you and next time it happens I'll see if that works.  I'm not using the WUSB600N right now so I can play Brood War without interruptions :)

---

### Post by MaindotC on 2008-10-16
> **hyper_ch said:**
> if that happens, can you run this command:

```

iwconfig

```

and post the output?

It happened again.  When I use iwconfig it says no wireless extensions.  I unplugged the Belkin USB and plugged in the Linksys and it didn't light up.  I'm assuming I'll have to reboot in order to get power to it.  Usually when I plug in a device it's detected and there are like 30 lines of logs, but this is all I get:
```

tail /var/log/syslog

Oct 16 17:57:30 amd64-desktop kernel: [10942.867862] usb 5-4: new high speed USB device using ehci_hcd and address 7

```

Ever after like 5 minutes that's all that was displayed.

---

### Post by Ayuthia on 2008-10-16
> **strAlan said:**
> 
This was an interesting entry in my syslog:

```

Oct 14 12:39:29 amd64-desktop kernel: on tileblit font bitblit softcursor fuse
Oct 14 12:39:29 amd64-desktop kernel: [  163.221730] Pid: 3216, comm: ntos_wq Tainted: P        2.6.24-19-generic #1
Oct 14 12:39:29 amd64-desktop kernel: [  163.221732] RIP: 0010:[ndiswrapper:IofCompleteRequest+0xe5/0x180]  [ndiswrapper:IofCompleteRequest+0xe5/0x180] :ndiswrapper:IofCompleteRequest+0xe5/0x180
Oct 14 12:39:29 amd64-desktop kernel: [  163.221747] RSP: 0018:ffff810128fcbe40  EFLAGS: 00010202
Oct 14 12:39:29 amd64-desktop kernel: [  163.221748] RAX: 0000000000000000 RBX: ffff810129c23e00 RCX: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221750] RDX: 0000000000000010 RSI: 0000000000000002 RDI: 0000000000000002
Oct 14 12:39:29 amd64-desktop kernel: [  163.221752] RBP: ffff810129c23f60 R08: 0000000000000000 R09: ffff81012feb99c8
Oct 14 12:39:29 amd64-desktop kernel: [  163.221753] R10: ffff810001025fe0 R11: 0000000000000001 R12: ffff810128fcbe4f
Oct 14 12:39:29 amd64-desktop kernel: [  163.221755] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221757] FS:  00007f87f2e236e0(0000) GS:ffffffff805b9000(0000) knlGS:00000000f7e018c0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221758] CS:  0010 DS: 0018 ES: 0018 CR0: 000000008005003b
Oct 14 12:39:29 amd64-desktop kernel: [  163.221760] CR2: 0000000000000010 CR3: 0000000117b3b000 CR4: 00000000000006e0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221761] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 14 12:39:29 amd64-desktop kernel: [  163.221763] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 14 12:39:29 amd64-desktop kernel: [  163.221765] Process ntos_wq (pid: 3216, threadinfo ffff810128fca000, task ffff8101298107e0)
Oct 14 12:39:29 amd64-desktop kernel: [  163.221766] Stack:  0000000000000000 00ff810128fcd600 ffff810129c23e00 ffff81012a770cc0
Oct 14 12:39:29 amd64-desktop kernel: [  163.221769]  ffff81012a1fb818 ffff81012894a788 0000000000000000 ffffffff88495408
Oct 14 12:39:29 amd64-desktop kernel: [  163.221772]  ffff81012894a780 ffffffff884953c0 ffff81012894a780 ffffffff8024f2bc
Oct 14 12:39:29 amd64-desktop kernel: [  163.221774] Call Trace:
Oct 14 12:39:29 amd64-desktop kernel: [  163.221795]  [ndiswrapper:wrap_urb_complete_worker+0x48/0x120] :ndiswrapper:wrap_urb_complete_worker+0x48/0x120
Oct 14 12:39:29 amd64-desktop kernel: [  163.221810]  [ndiswrapper:wrap_urb_complete_worker+0x0/0x120] :ndiswrapper:wrap_urb_complete_worker+0x0/0x120
Oct 14 12:39:29 amd64-desktop kernel: [  163.221816]  [run_workqueue+0xcc/0x170] run_workqueue+0xcc/0x170
Oct 14 12:39:29 amd64-desktop kernel: [  163.221818]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221821]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221824]  [worker_thread+0xa3/0x110] worker_thread+0xa3/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221828]  [<ffffffff80253a00>] autoremove_wake_function+0x0/0x30
Oct 14 12:39:29 amd64-desktop kernel: [  163.221832]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221836]  [worker_thread+0x0/0x110] worker_thread+0x0/0x110
Oct 14 12:39:29 amd64-desktop kernel: [  163.221838]  [kthread+0x4b/0x80] kthread+0x4b/0x80
Oct 14 12:39:29 amd64-desktop kernel: [  163.221842]  [child_rip+0xa/0x12] child_rip+0xa/0x12
Oct 14 12:39:29 amd64-desktop kernel: [  163.221853]  [kthread+0x0/0x80] kthread+0x0/0x80
Oct 14 12:39:29 amd64-desktop kernel: [  163.221856]  [child_rip+0x0/0x12] child_rip+0x0/0x12
Oct 14 12:39:29 amd64-desktop kernel: [  163.221860] 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221860] 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221861] Code: 89 02 48 8b 43 38 48 8b 53 48 48 89 42 08 48 8b 7b 50 48 85 
Oct 14 12:39:29 amd64-desktop kernel: [  163.221865] RIP  [ndiswrapper:IofCompleteRequest+0xe5/0x180] :ndiswrapper:IofCompleteRequest+0xe5/0x180
Oct 14 12:39:29 amd64-desktop kernel: [  163.221880]  RSP <ffff810128fcbe40>
Oct 14 12:39:29 amd64-desktop kernel: [  163.221881] CR2: 0000000000000010
Oct 14 12:39:29 amd64-desktop kernel: [  163.221883] ---[ end trace 4b5e77df13797eba ]---

```

Rebooted.

Are you using ndiswrapper or b43?  From this log, it looks like ndiswrapper crashed.  Can you post your lshw -C network?

I originally was going to suggest that you reload the b43 module, but it does not look like the module that crashed.

---

### Post by MaindotC on 2008-10-16
I was using b43 for my Belkin, which was stuck on a solid LED and thus indicating it was inoperable, and then I unplugged the Belkin and plugged in the Linksys.  Since the Linksys didn't light up, I plugged in the Belkin again just for kicks and it gave me the solid LED and the network-manager applet didn't show any wireless networks.  This lshw -C network is on the machine whose network interface isn't working.  I can, of course, copy the output to a text file, reboot and copy/paste it.  I tried transferring the text file to a jump drive but now my usb devices aren't mounting and I can't move the text file.  Will rebooting affect any future outputs you'd like for the time being?

Edit: using ndiswrapper for the linksys wusb600n

Edit#2: I put a CAT V between my laptop (working) and my desktop (Belkin/Linksys) and sftp'd the text file - didn't reboot.  Here's the ouptut you requested:

```

amd64@amd64-desktop:~$ sudo lshw -C network
[sudo] password for amd64: 
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 11
       serial: 00:50:8d:d1:65:b4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.14 duplex=full latency=32 link=no maxlatency=8 mingnt=3 module=via_velocity multicast=yes port=twisted pair speed=1GB/s
amd64@amd64-desktop:~$

```

---

### Post by Ayuthia on 2008-10-16
I am really not for sure if this will help or not, but you can try and reset the b43 module:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
```The ssb module will load automatically because b43 needs it.  You could then reset the network if needed.  I am not for sure if this will work for you or not though because I am not for sure what crashed.  If it was one of the usb modules, you will need to figure out which one it was and reload it.  However if it is just the wireless locking up, you should just be able to reset the module and hopefully that will get it back up again.

---

### Post by MaindotC on 2008-10-16
I did as you advised and didn't see any results :(  I'm mildly familiar w/ the modprobe command so I'll have to man page that to understand precisely what this is doing.  In the meantime I'm just going to reboot it and live with the consequences.  However, I'm going to use the WUSB600N w/ ndiswrapper to start things off.  When and if it crashes, is there any particular logging that would help understand what problems its having?

---

### Post by MaindotC on 2008-10-27
I'd like to re-open this issue.  My laptop - Lenovo T60 - always uses my wireless connection so I've never had the wired connection in use.  Just now I'm trying to connect to an access point to configure it.  I plugged the cat V cable into an interface on the AP, and on my laptop, and no lights.  Is there some way to kind of *nudge* my wired interface?

---

