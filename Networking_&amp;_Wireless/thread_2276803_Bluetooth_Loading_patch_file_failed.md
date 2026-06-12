---
title: "Bluetooth: Loading patch file failed"
date: 2015-05-05
forum: Networking &amp; Wireless
---

### Post by tycho-z on 2015-05-05
Bluetooth firmware is not loaded. I did some research and found that it _should_ be the kernel version. So upgraded to new kernel 3.19.5 but still no joy. 
Cant find the file it needs anywhere on the web..  what is going wrong?

lsusb
```

0cf3:3004 Atheros Communications

```

dmesg
```

[    8.411052] usb 3-1.3: Direct firmware load for ar3k/AthrBT_0x00000200.dfu failed with error -2
[    8.411058] Bluetooth: Patch file not found ar3k/AthrBT_0x00000200.dfu
[    8.411060] Bluetooth: Loading patch file failed
[    8.411066] ath3k: probe of 3-1.3:1.0 failed with error -2
[    8.411274] usbcore: registered new interface driver ath3k

```

ll  /lib/firmware/ar3k/
```

-rw-r--r--  1 root root 55244 nov 24 16:42 AthrBT_0x01020001.dfu
-rw-r--r--  1 root root 40724 nov 24 16:42 AthrBT_0x01020200.dfu
-rw-r--r--  1 root root 19164 dec  1 16:16 AthrBT_0x01020201.dfu
-rw-r--r--  1 root root 36828 nov 24 16:42 AthrBT_0x11020000.dfu
-rw-r--r--  1 root root 40652 nov 24 16:42 AthrBT_0x31010000.dfu
-rw-r--r--  1 root root 31500 dec  1 16:16 AthrBT_0x41020000.dfu
-rw-r--r--  1 root root  1224 nov 24 16:42 ramps_0x01020001_26.dfu
-rw-r--r--  1 root root  1274 nov 24 16:42 ramps_0x01020200_26.dfu
-rw-r--r--  1 root root  1204 nov 24 16:42 ramps_0x01020200_40.dfu
-rw-r--r--  1 root root   264 dec  1 16:16 ramps_0x01020201_26.dfu
-rw-r--r--  1 root root   264 dec  1 16:16 ramps_0x01020201_40.dfu
-rw-r--r--  1 root root  1796 nov 24 16:42 ramps_0x11020000_40.dfu
-rw-r--r--  1 root root  1926 nov 24 16:42 ramps_0x31010000_40.dfu
-rw-r--r--  1 root root  1820 dec  1 16:16 ramps_0x41020000_40.dfu

```

---

### Post by Pilot6 on 2015-05-05
This must be fixed upstream. Something has changed  in this chip, so file versions are wrong.
The chip does not give the data for firmware versions.  [COLOR=#000000][FONT=Ubuntu Mono]AthrBT_0x01020200.dfu is supposed.
But ath3k module maust be patched.[/FONT][/COLOR]

---

### Post by tycho-z on 2015-05-05
ok, thats to bad. so symlink wont work. 
so in short, it is a waiting game. 

does it main the linux-firmware package needs to be updated? or kernel?
And what is the proper way to push this request upstream?

---

### Post by Pilot6 on 2015-05-05
I already sent this link to kernel maintainers.

But you can try to symlink too. It may work.

---

### Post by notify-8 on 2015-05-10
I've got the same issue on my MSI WS-60. The ar3k drivers are looking for AthrBT_0x00000200.dfu:

```

[    1.365695] usb 3-1.3: Direct firmware load for ar3k/AthrBT_0x00000200.dfu failed with error -2
[    1.365696] Bluetooth: Patch file not found ar3k/AthrBT_0x00000200.dfu
[    1.365697] Bluetooth: Loading patch file failed
[    1.365700] ath3k: probe of 3-1.3:1.0 failed with error -2

```

Is there a link to the kernel mailing list discussion thread that deals with this?

---

