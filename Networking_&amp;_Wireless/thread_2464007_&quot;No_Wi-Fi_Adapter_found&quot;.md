---
title: "&quot;No Wi-Fi Adapter found&quot;?"
date: 2021-06-22
forum: Networking &amp; Wireless
---

### Post by thatrius on 2021-06-22
Hi all,

I've recently switched from Windows 10 to Ubuntu 20.04 LTS on my desktop, with ***very*** little prior experience.


 Anyways I can't seem to figure out how to connect to internet via any  means whatsoever. The wifi icon isn't visible anywhere in the top bar, and the "Wi-Fi" tab in Settings just reads "No Wi-Fi  Adapter Found". I've tried using a wired connection to install  possibly-missing drivers for the aforementioned wifi adapter; but plugging in an ethernet  cable freezes the whole system for some reason, and the only way to unfreeze  is by pulling the plug and restarting.


 I don't think it's a hardware issue, as everything worked perfectly fine on Windows (both wired and wireless).


 here's the log output from wireless-info.txt:
[ATTACH]288716[/ATTACH]

I've been at this nonstop for days, and at this point I think it's safe  to say this is the single most frustrating and utterly infuriating  problem I've ever had the turmoil of trying to solve. If anyone can possibly help me fix the issue, you will have my eternal gratitude.

thanks

---

### Post by chili555 on 2021-06-23
> I think it's safe to say this is the single most frustrating and utterly infuriating problem I've ever had the turmoil of trying to solve. Don't be hard on yourself. Wireless is a black art that looks easy if you have a couple of decades of experience, luck and ingenuity. If not, it is, as you've seen, almost impossible.

Please hook up the ethernet temporarily and open a terminal and do:

```
sudo apt update
sudo apt install rtl8812au-dkms
```

The process takes a few moments, so please be patient. When it's finished, detach the ethernet and reboot.

Then post to tell us if your wireless is working as expected.

--------------------------------------------------------------

Note to searchers: The key is the usb.id here:

```
[COLOR="#FF0000"]0bda:0811[/COLOR] Realtek Semiconductor Corp. 802.11ac WLAN Adapter 
```Google "0bda:0811" and Ubuntu and you will find the answer. Be sure to pick the newest result that is solved.

---

### Post by thatrius on 2021-06-23
Thanks for the reply!

I was able to plug in the ethernet and  paste the commands into the terminal before the screen froze; but they  still both threw internet-failure errors. 

I guess the freezing  issue is the one I should try and resolve first then, if an internet  connection is mandatory. Any idea why plugging in an ethernet cable  might cause a crash?

---

### Post by chili555 on 2021-06-23
> **thatrius said:**
> Thanks for the reply!

I was able to plug in the ethernet and  paste the commands into the terminal before the screen froze; but they  still both threw internet-failure errors. 

I guess the freezing  issue is the one I should try and resolve first then, if an internet  connection is mandatory. Any idea why plugging in an ethernet cable  might cause a crash?Let's see if the log tells us:

```
tail -f /var/log/syslog
```Plug in the ethernet cable and watch and carefully note the resulting output. Post it and we'll take a look.

You might also check, after a reboot following a freeze:

```
less /var/log/dmesg.1.gz

```The last few lines might help us.

---

### Post by thatrius on 2021-06-23
the first log didn't print anything before the crash, but here are the last few lines of the dmesg one:
```

kernel:  Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic  FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
kernel: r8169 0000:05:00.0 enp5s0: Link is Down
kernel: rfkill: input handler disabled
```

---

### Post by chili555 on 2021-06-23
> **thatrius said:**
> the first log didn't print anything before the crash, but here are the last few lines of the dmesg one:
```

kernel:  Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic  FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
kernel: r8169 0000:05:00.0 enp5s0: Link is Down
kernel: rfkill: input handler disabled
```Let's dig deeper:

```
sudo dmesg | grep -ie warn -ie error
sudo dmesg | grep r8169 -e enp

```

---

### Post by thatrius on 2021-06-24
ran the commands:
```
sudo dmesg | grep -ie warn -ie error
[    0.479692] pcieport 0000:00:1c.6: DPC: error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+
[    0.479922] pcieport 0000:00:1d.0: DPC: error containment capabilities: Int Msg #0, RPExt+ PoisonedTLP+ SwTrigger+ RP PIO Log 4, DL_ActiveErr+
[    0.600659] RAS: Correctable Errors collector initialized.
[    4.384197] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro

sudo dmesg | grep r8169 -e enp
grep: r8169: No such file or directory
```

---

### Post by chili555 on 2021-06-24
> sudo dmesg | grep r8169 -e enp
grep: r8169: No such file or directorySorry, I made a mistake. Please try again:

```
sudo dmesg | grep -e r8169 -e enp
```I see nothing alarming so far; let's keep looking.

---

### Post by thatrius on 2021-06-24
Okay got it,
```
sudo dmesg | grep -e r8169 -e enp
[    0.831873] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.831882] r8169 0000:05:00.0: enabling device (0000 -> 0003)
[    0.847794] libphy: r8169: probed
[    0.847918] r8169 0000:05:00.0 eth0: RTL8168h/8111h, 4c:ed:fb:6b:f4:6c, XID 541, IRQ 126
[    0.847919] r8169 0000:05:00.0 eth0: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.848430] r8169 0000:05:00.0 enp5s0: renamed from eth0
[    6.862561] Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
[    7.054682] r8169 0000:05:00.0 enp5s0: Link is Down

```

---

### Post by thatrius on 2021-06-25
Could it possibly be a driver issue? Not sure whether or not wired connections need drivers, but at least then I might be able to install one from a flash drive

---

### Post by chili555 on 2021-06-25
> **thatrius said:**
> Could it possibly be a driver issue? Not sure whether or not wired connections need drivers, but at least then I might be able to install one from a flash driveWired connections do require a driver and you have one, r8169:
> [    0.831873] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.831882] r8169 0000:05:00.0: enabling device (0000 -> 0003)
[    0.847794] libphy: r8169: probed
[    0.847918] r8169 0000:05:00.0 eth0: RTL8168h/8111h, 4c:ed:fb:6b:f4:6c, XID 541, IRQ 126
[    0.847919] r8169 0000:05:00.0 eth0: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    0.848430] r8169 0000:05:00.0 enp5s0: renamed from eth0
[    6.862561] Generic FE-GE Realtek PHY r8169-500:00: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-500:00, irq=IGNORE)
[    7.054682] r8169 0000:05:00.0 enp5s0: Link is Down
Other than the link being down, which we expect because the cable is not yet attached, we see nothing alarming here.

Please plug in the ethernet cable and let the system freeze. If you wait long enough, say five minutes, does it eventually recover?

After you force reboot, please let us see:
```
ls -al /var/crash
```Let's see if there is a recent addition that helps us.

Will the system boot with the ethernet cable plugged in.

Based on what I've seen so far. the freeze is not likely related to the driver. It could be Network Manager, systemd, or elsewhere.

---

### Post by thatrius on 2021-06-26
Left it frozen for a few hours, no recovery unfortunately :/

Rebooted and ran 
```

~$ ls -al /var/crash
total 8
drwxrwsrwt  2 root whoopsie 4096 Feb  9 13:52 .
drwxr-xr-x 14 root root     4096 Feb  9 13:56 ..

```

---

### Post by thatrius on 2021-06-26
I just tried booting with the ethernet in. Oddly enough, it booted fine and isn't crashing, even when the cable is taken out and then re-inserted.

Still no internet though

---

### Post by thatrius on 2021-06-26
Plugged the ethernet cable into my laptop with a shared connection, and for whatever reason, wired works now.

Ran these again:
```

sudo apt update 
sudo apt install rtl8812au-dkms

```[FONT=arial]
Both executed fine, but still no wifi after reboot[/FONT]

---

### Post by chili555 on 2021-06-26
Is the module loaded?

```
lsmod | grep 8812
```

If not, load it and see if there are any interesting clues:

```
sudo modprobe 8812au
```

Are there any clues in the log:

```
sudo dmesg | grep 8812
```

Is the Airplane Mode switch set to enable wireless?

```
rfkill list all
```

---

### Post by thatrius on 2021-06-26
It's showing up, so I assume that means it's loaded:
```
~$ lsmod | grep 8812
8812au               1290240  0
cfg80211              778240  1 8812au

```
Ran *sudo modprobe 8812au* just in case, it didn't return anything though, just made a new line.

*sudo dmesg | grep 8812* returned:
```

[    0.798812] hub 2-0:1.0: USB hub found
[    3.656220] 8812au: loading out-of-tree module taints kernel.
[    3.667522] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[    3.706622] RTL871X: rtl8812au v4.3.8_12175.20140902
[    3.706688] Modules linked in: 8812au(OE+) snd_seq fjes(-) crypto_simd cec snd_seq_device cryptd rc_core snd_timer glue_helper fb_sys_fops eeepc_wmi mei_me cfg80211 snd syscopyarea asus_wmi rapl sysfillrect joydev input_leds intel_cstate sysimgblt soundcore sparse_keymap wmi_bmof efi_pstore ee1004 mei mac_hid acpi_pad sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_generic usbhid hid crc32_pclmul r8169 i2c_i801 ahci i2c_smbus realtek xhci_pci libahci xhci_pci_renesas wmi video
[    3.706746]  ? _rtw_malloc+0x2d/0x2f [8812au]
[    3.706762]  ? _rtw_memcpy+0x10/0x12 [8812au]
[    3.706779]  ? rtw_5g_rates_init+0x1a/0x1c [8812au]
[    3.706795]  ? rtw_spt_band_alloc+0xb0/0xb2 [8812au]
[    3.706812]  rtw_wdev_alloc+0xf6/0x29c [8812au]
[    3.706829]  rtw_usb_if1_init+0xf0/0x20c [8812au]
[    3.706845]  rtw_drv_init+0x246/0x2d3 [8812au]
[    3.706875]  rtw_drv_entry+0x65/0x1000 [8812au]
[    3.979794] usbcore: registered new interface driver rtl8812au
```

---

### Post by chili555 on 2021-06-26
> [3.706688] Modules linked in: 8812au(OE+) snd_seq fjes(-) crypto_simd cec snd_seq_device cryptd rc_core snd_timer glue_helper fb_sys_fops eeepc_wmi mei_me cfg80211 snd syscopyarea asus_wmi rapl sysfillrect joydev 
[    3.706812]  rtw_wdev_alloc+0xf6/0x29c [8812au]
<snip>

That is a very unhappy driver and hardware combo! Let's try somthing newer. With a working internet connection:

```
sudo apt purge rtl8812au-dkms
sudo apt update
sudo apt install git
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo ./dkms-install.sh
sudo modprobe 88XXau
```

Reboot. Your wireless should now be working.

---

### Post by thatrius on 2021-06-26
[FONT=arial]I am overjoyed to say that I'm writing this from wifi.

I ran your code - the *sudo ./dkms-install.sh *line returned an error, but I tried *sudo make dkms_install* (from the instructions on the git clone page) instead, and that seemed to work just as well.

Thanks again for the help![/FONT]

---

### Post by morrownr on 2021-06-27
> **thatrius said:**
> [FONT=arial]I am overjoyed to say that I'm writing this from wifi.

[/FONT]

Glad you are online with wifi. I am going to recommend you do some reading at the following link:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

That link contains a LOT of information regarding usb wifi on Linux. One thing that I and others have found to be very handy is to have at least one adapter that uses in-kernel drivers. Adapters that use in-kernel drivers are plug and play. The site currently has 69 links to adapters that use in-kernel drivers.

Regards

---

### Post by thatrius on 2021-06-27
> **morrownr said:**
> Glad you are online with wifi. I am going to recommend you do some reading at the following link:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

That link contains a LOT of information regarding usb wifi on Linux. One thing that I and others have found to be very handy is to have at least one adapter that uses in-kernel drivers. Adapters that use in-kernel drivers are plug and play. The site currently has 69 links to adapters that use in-kernel drivers.

Regards

Thanks, good to know!

---

