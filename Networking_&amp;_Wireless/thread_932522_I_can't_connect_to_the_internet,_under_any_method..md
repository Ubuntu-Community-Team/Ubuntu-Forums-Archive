---
title: "I can't connect to the internet, under any method."
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by Vaughands on 2008-09-28
Ethernet, or Wireless. It simply... won't work! I've tried everything... Ubuntu community any ideas on what to do?

Wireless: NDISWRAPPER, proprietary drivers are installed madwifi even... sure it picks it up on as on and all but I just can't see any access points, as for wired... I plug it in straight from the modem.. and just nothing...

 Same thing with a Ethernet cable from the router... 

Hardware: Atheroes 802.11g

---

### Post by alastair on 2008-09-28
Stick with the simpler mechanism first - wired ethernet. Once this works, try wireless.

So, is the router set up to give you an IP address? DHCP?

Ethernet cable unplugged.
In one terminal : sudo tail -f /var/log/syslog

Plug in ethernet cable.

Anything in syslog?

Another terminal :
What about output of : ifconfig -a

Cheers,
Alastair

---

### Post by Vaughands on 2008-09-28
Alright, I'm not too computer savvy.. so let me explain to you how this crap is setup. Theres a modem, and out of the modem is a blue wire... the blue wire goes into my D-Link router. Then theres this random black cable... what one am I inserting into the laptop?

---

### Post by Another Monkey on 2008-09-28
> **Vaughands said:**
> Alright, I'm not too computer savvy.. so let me explain to you how this crap is setup. Theres a modem, and out of the modem is a blue wire... the blue wire goes into my D-Link router. Then theres this random black cable... what one am I inserting into the laptop?
I am not being cheeky, but the one that fits!  You need a cable from the Ubuntu box to the router.  This will be an ethernet cable (one may have come with the router).  It should have two ends that loo a bit like this:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/20/Ethernet_plug_grey.svg/180px-Ethernet_plug_grey.svg.png[/IMG]

Plug it in (both ends) wait about 15 seconds (lights may come on on the router) and then try.

Can you go to your router config page?  This is often [http://192.168.0.1](http://192.168.0.1) (but check your documentation).  This should tell you if the router thinks it has a connection to the internet or not (mine tells me in [COLOR="DarkGreen"]green[/COLOR] or [COLOR="Red"]red[/COLOR] text in the upper right).

---

### Post by Vaughands on 2008-09-28
Yeah, I see one. There's one end going into the modem... and the other in the router. And the black one is.. plugged into this PC. Ah I got you, take it out of the PC and try it. And if it works, I'll need to buy myself a another cable. Alright, I'll try as you said now...

---

### Post by Vaughands on 2008-09-28
The power of USB drives....:

Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.269354] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Pattern   7.01 PQ: 0 ANSI: 0 CCS
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.270592] sd 7:0:0:0: [sdb] 3907583 512-byte hardware sectors (2001 MB)
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.271476] sd 7:0:0:0: [sdb] Write Protect is off
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.271482] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.271484] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.273709] sd 7:0:0:0: [sdb] 3907583 512-byte hardware sectors (2001 MB)
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.274335] sd 7:0:0:0: [sdb] Write Protect is off
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.274339] sd 7:0:0:0: [sdb] Mode Sense: 45 00 00 08
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.274342] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.274348]  sdb: sdb1
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.275744] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Sep 28 14:18:00 vaughan-desktop kernel: [ 3778.275784] sd 7:0:0:0: Attached scsi generic sg2 type 0
Sep 28 14:18:00 vaughan-desktop NetworkManager: <debug> [1222633080.315753] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host'). 
Sep 28 14:18:00 vaughan-desktop NetworkManager: <debug> [1222633080.320270] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0'). 
Sep 28 14:18:00 vaughan-desktop NetworkManager: <debug> [1222633080.354108] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 28 14:18:00 vaughan-desktop NetworkManager: <debug> [1222633080.436256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Cruzer_Pattern_1535730C6782537A_0_0'). 
Sep 28 14:18:00 vaughan-desktop NetworkManager: <debug> [1222633080.552242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_7010_64C6'). 
Sep 28 14:18:00 vaughan-desktop hald: mounted /dev/sdb1 on behalf of uid 1000
Sep 28 14:35:34 vaughan-desktop -- MARK --
Sep 28 14:44:41 vaughan-desktop kernel: [ 5376.895601] usb 3-5: USB disconnect, address 5
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.498650] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 28 14:44:41 vaughan-desktop hald[4458]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
Sep 28 14:44:41 vaughan-desktop kernel: [ 5376.925051] scsi 7:0:0:0: rejecting I/O to dead device
Sep 28 14:44:41 vaughan-desktop hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 0
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.590750] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_7010_64C6'). 
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.597397] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Cruzer_Pattern_1535730C6782537A_0_0'). 
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.598537] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0'). 
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.601806] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host'). 
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.613362] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0'). 
Sep 28 14:44:41 vaughan-desktop NetworkManager: <debug> [1222634681.634782] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A'). 
Sep 28 14:46:56 vaughan-desktop kernel: [ 5511.788733] usb 3-5: new high speed USB device using ehci_hcd and address 6
Sep 28 14:46:56 vaughan-desktop kernel: [ 5511.921502] usb 3-5: configuration #1 chosen from 1 choice
Sep 28 14:46:56 vaughan-desktop NetworkManager: <debug> [1222634816.720424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A'). 
Sep 28 14:46:56 vaughan-desktop kernel: [ 5511.956493] scsi8 : SCSI emulation for USB Mass Storage devices
Sep 28 14:46:56 vaughan-desktop kernel: [ 5511.957117] usb-storage: device found at 6
Sep 28 14:46:56 vaughan-desktop kernel: [ 5511.957121] usb-storage: waiting for device to settle before scanning
Sep 28 14:46:56 vaughan-desktop NetworkManager: <debug> [1222634816.830151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0'). 
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.949155] usb-storage: device scan complete
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.950047] scsi 8:0:0:0: Direct-Access     SanDisk  Cruzer Pattern   7.01 PQ: 0 ANSI: 0 CCS
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.956548] sd 8:0:0:0: [sdb] 3907583 512-byte hardware sectors (2001 MB)
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.957539] sd 8:0:0:0: [sdb] Write Protect is off
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.957544] sd 8:0:0:0: [sdb] Mode Sense: 45 00 00 08
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.957546] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.960398] sd 8:0:0:0: [sdb] 3907583 512-byte hardware sectors (2001 MB)
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.961060] sd 8:0:0:0: [sdb] Write Protect is off
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.961063] sd 8:0:0:0: [sdb] Mode Sense: 45 00 00 08
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.961066] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.961072]  sdb: sdb1
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.962435] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Sep 28 14:47:01 vaughan-desktop kernel: [ 5516.962478] sd 8:0:0:0: Attached scsi generic sg2 type 0
Sep 28 14:47:01 vaughan-desktop NetworkManager: <debug> [1222634821.818702] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host'). 
Sep 28 14:47:01 vaughan-desktop NetworkManager: <debug> [1222634821.826458] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0'). 
Sep 28 14:47:01 vaughan-desktop NetworkManager: <debug> [1222634821.865450] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_781_550a_1535730C6782537A_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Sep 28 14:47:01 vaughan-desktop NetworkManager: <debug> [1222634821.957427] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Cruzer_Pattern_1535730C6782537A_0_0'). 
Sep 28 14:47:02 vaughan-desktop NetworkManager: <debug> [1222634822.074366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_7010_64C6'). 
Sep 28 14:47:02 vaughan-desktop hald: mounted /dev/sdb1 on behalf of uid 1000

---

### Post by Vaughands on 2008-09-28
ifconfig -a Output:

[IMG]http://img46.imageshack.us/img46/3465/28413131dy0.png[/IMG]

---

### Post by Another Monkey on 2008-09-28
Apologies, I had misread your first post.  Ignore me.

> **Vaughands said:**
> Yeah, I see one. There's one end going into the modem... and the other in the router. And the black one is.. plugged into this PC. Ah I got you, take it out of the PC and try it. And if it works, I'll need to buy myself a another cable. Alright, I'll try as you said now...

Hang on, your router is connected to a modem?  That's a new one to me, but I am no expert.

I have:
```
Ununtu PC<===(ethernet)===>Router<===(cable)===>Broadband (telephone point with filter)
                             |
                             ---(wire)---mains electricity
```

Looking at your output, you don't seem to be connected to the router.  I can't see any assigned IP.  Are there any networking lghts on?  Is the router plugged into the mains and turned on?  Are there any lights on the router?

Are we really talking about a router and not a hub?  They're not the same thing.

---

### Post by Vaughands on 2008-09-28
Modem > Router > PCs.

I'm pretty sure anyway, the modem is directing from a wire to the router. And then another wire is going out of the router into my PC.  Wireless Router CLEARLY written on it. Although, this isn't my main area to use wireless. It's setup over at my house like this too, I just don't get it...

---

### Post by Vaughands on 2008-09-29
*Bump*

---

### Post by cariboo on 2008-09-29
Once you have your network cable from the router to the computer plugged in it should automagically connect to your router. If it doesn't try in a terminal:

```
sudo dhclient eth0
``` 

Jim

---

### Post by Vaughands on 2008-09-29
[IMG]http://img297.imageshack.us/img297/923/terminaldhclientpa9.png[/IMG]

---

### Post by Vaughands on 2008-09-30
*Bump*

---

