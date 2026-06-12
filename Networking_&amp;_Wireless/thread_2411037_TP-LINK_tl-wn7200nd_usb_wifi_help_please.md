---
title: "TP-LINK tl-wn7200nd usb wifi help please"
date: 2019-01-23
forum: Networking &amp; Wireless
---

### Post by macprox86 on 2019-01-23
Hello everbody
Iam new in ubuntu
please show me the way how to install my usb wifi  tl-wn7200nd PLEASE
Iam using Ubuntu 18.04.1 LTS
Thank you very much !!

---

### Post by macprox86 on 2019-01-24
Any help Please

---

### Post by chili555 on 2019-01-24
Please open a terminal and run and post:```
lsusb
```Thanks.

---

### Post by macprox86 on 2019-01-24
result
```
 lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 025: ID 1bcf:0005 Sunplus Innovation Technology Inc. Optical Mouse
Bus 001 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mani@mani-H61H2-M13:~$ 

```

i think iam the same as this one
[https://ubuntuforums.org/showthread.php?t=1892606&page=2](https://ubuntuforums.org/showthread.php?t=1892606&page=2)
because the usb dongle wifi is not even detected 
but i dont know how to start

---

### Post by chili555 on 2019-01-24
You are quite correct. We see no USB wireless in your readings.> 
i think iam the same as this one
[https://ubuntuforums.org/showthread....1892606&page=2](https://ubuntuforums.org/showthread....1892606&page=2)
because the usb dongle wifi is not even detected 
I wouldn't rely on any posting more than 2 years old and, most especially, any post from 2011 that mentions kernel version 2.6.xx. No matter what you read there, it is no longer valid. 

Please remove the device, open a terminal and run:```
tail -f /var/log/syslog
```Insert the device and watch the terminal output until it stops. Capture the output and post it here.

Get out of 'tail' with Ctrl+c.

For comparison, here is the similar output from my machine when I insert a USB wireless:

```
Jan 24 10:38:34 T440p kernel: [23480.498220] usb 3-3: new high-speed USB device number 7 using xhci_hcd
Jan 24 10:38:34 T440p kernel: [23480.663033] usb 3-3: New USB device found, idVendor=0cf3, idProduct=9271, bcdDevice= 1.08
Jan 24 10:38:34 T440p kernel: [23480.663039] usb 3-3: New USB device strings: Mfr=16, Product=32, SerialNumber=48
Jan 24 10:38:34 T440p kernel: [23480.663043] usb 3-3: Product: USB2.0 WLAN
Jan 24 10:38:34 T440p kernel: [23480.663046] usb 3-3: Manufacturer: ATHEROS
Jan 24 10:38:34 T440p kernel: [23480.663049] usb 3-3: SerialNumber: 12345
Jan 24 10:38:34 T440p kernel: [23480.706220] usb 3-3: ath9k_htc: Firmware ath9k_htc/htc_9271-1.4.0.fw requested
Jan 24 10:38:34 T440p kernel: [23480.706335] usbcore: registered new interface driver ath9k_htc
Jan 24 10:38:35 T440p kernel: [23481.008351] usb 3-3: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
Jan 24 10:38:35 T440p kernel: [23481.260086] ath9k_htc 3-3:1.0: ath9k_htc: HTC initialized with 33 credits

```

---

### Post by macprox86 on 2019-01-24
thanks for beeing here
here's the result

```
mani@mani-H61H2-M13:~$ tail -f /var/log/syslog
Jan 24 16:44:29 mani-H61H2-M13 gnome-shell[1148]: message repeated 2 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
Jan 24 16:44:31 mani-H61H2-M13 gnome-shell[1148]: JS ERROR: Exception in callback for signal: activate: Error: Error invoking IBus.set_global_engine_async: Expected function for callback argument callback, got undefined#012setEngine@resource:///org/gnome/shell/misc/ibusManager.js:207:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012activateInputSource@resource:///org/gnome/shell/ui/status/keyboard.js:490:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012activate@resource:///org/gnome/shell/ui/status/keyboard.js:65:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_inputSourcesChanged@resource:///org/gnome/shell/ui/status/keyboard.js:620:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012reload@resource:///org/gnome/shell/ui/status/keyboard.js:369:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ibusSetContentType@resource:///org/gnome/shell/ui/status/keyboard.js:691:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012_setContentType@resource:///org/gnome/shell/misc/ibusManager.js:183:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Jan 24 16:44:31 mani-H61H2-M13 gnome-shell[1148]: JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13
Jan 24 16:44:32 mani-H61H2-M13 gnome-shell[1148]: message repeated 2 times: [ JS ERROR: TypeError: this._currentWindow is null#012_setCurrentRect@resource:///org/gnome/shell/ui/keyboard.js:536:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init/<@resource:///org/gnome/shell/ui/keyboard.js:503:13]
Jan 24 16:44:34 mani-H61H2-M13 snapd[615]: api.go:1063: Installing snap "inkscape" revision unset
Jan 24 16:45:15 mani-H61H2-M13 gnome-shell[1148]: JS ERROR: Exception in callback for signal: activate: Error: Error invoking IBus.set_global_engine_async: Expected function for callback argument callback, got undefined#012setEngine@resource:///org/gnome/shell/misc/ibusManager.js:207:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012activateInputSource@resource:///org/gnome/shell/ui/status/keyboard.js:490:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012activate@resource:///org/gnome/shell/ui/status/keyboard.js:65:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_inputSourcesChanged@resource:///org/gnome/shell/ui/status/keyboard.js:620:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012reload@resource:///org/gnome/shell/ui/status/keyboard.js:369:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_ibusSetContentType@resource:///org/gnome/shell/ui/status/keyboard.js:691:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_emit@resource:///org/gnome/gjs/modules/signals.js:128:27#012_setContentType@resource:///org/gnome/shell/misc/ibusManager.js:183:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Jan 24 16:45:45 mani-H61H2-M13 dbus-daemon[1024]: [session uid=1000 pid=1024] Activating via systemd: service name='org.gnome.Terminal' unit='gnome-terminal-server.service' requested by ':1.123' (uid=1000 pid=17951 comm="/usr/bin/gnome-terminal.real " label="unconfined")
Jan 24 16:45:45 mani-H61H2-M13 systemd[998]: Starting GNOME Terminal Server...
Jan 24 16:45:45 mani-H61H2-M13 dbus-daemon[1024]: [session uid=1000 pid=1024] Successfully activated service 'org.gnome.Terminal'
Jan 24 16:45:45 mani-H61H2-M13 systemd[998]: Started GNOME Terminal Server.
Jan 24 16:46:15 mani-H61H2-M13 kernel: [ 4874.684338] usb 1-1-port4: Cannot enable. Maybe the USB cable is bad?
Jan 24 16:46:16 mani-H61H2-M13 kernel: [ 4875.536298] usb 1-1-port4: Cannot enable. Maybe the USB cable is bad?
Jan 24 16:46:16 mani-H61H2-M13 kernel: [ 4875.536423] usb 1-1-port4: attempt power cycle
Jan 24 16:46:17 mani-H61H2-M13 kernel: [ 4876.704326] usb 1-1-port4: Cannot enable. Maybe the USB cable is bad?
Jan 24 16:46:18 mani-H61H2-M13 kernel: [ 4877.556278] usb 1-1-port4: Cannot enable. Maybe the USB cable is bad?
Jan 24 16:46:18 mani-H61H2-M13 kernel: [ 4877.556407] usb 1-1-port4: unable to enumerate USB device

```

---

### Post by chili555 on 2019-01-24
> Jan 24 16:46:18 mani-H61H2-M13 kernel: [ 4877.556278] usb 1-1-port4: Cannot enable. Maybe the USB cable is bad?
Jan 24 16:46:18 mani-H61H2-M13 kernel: [ 4877.556407] usb 1-1-port4: unable to enumerate USB deviceThat strongly suggests that either the USB port is bad (unlikely) or that the USB wireless device is defective (likely).

Have you tried all the different USB ports on your computer?

Does the device work on other computers; Windows et al?

Compiling drivers or installing firmware, etc. will do no good until the computer recognizes what the device actually is; USB wireless? Storage device? Mouse? Keyboard? Printer???

---

### Post by macprox86 on 2019-01-24
Yes.. i tried all usb ports even those how worked with the mouse or the keyboard
the dongle worked with windows and just before i installed ubuntu last night

---

### Post by chili555 on 2019-01-24
> **macprox86 said:**
> Yes.. i tried all usb ports even those how worked with the mouse or the keyboard
the dongle worked with windows and just before i installed ubuntu last nightCan you check it with a friend or neighbor's computer? 

I notice that it uses a small detachable cable. Can you please try a different cable? Are you quite certain that the cable is securely plugged in at both ends?

---

### Post by macprox86 on 2019-01-24
I tried with another usb cable and it gave me the same result

```
mani@mani-H61H2-M13:~$ tail -f /var/log/syslog
Jan 24 17:43:06 mani-H61H2-M13 systemd[1]: Started Save/Restore Sound Card State.
Jan 24 17:43:06 mani-H61H2-M13 systemd[1]: Reloading.
Jan 24 17:43:43 mani-H61H2-M13 systemd[1]: Reloading.
Jan 24 17:43:51 mani-H61H2-M13 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jan 24 17:43:51 mani-H61H2-M13 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Jan 24 17:43:51 mani-H61H2-M13 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 24 17:43:51 mani-H61H2-M13 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jan 24 17:43:51 mani-H61H2-M13 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Jan 24 17:43:51 mani-H61H2-M13 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jan 24 17:43:51 mani-H61H2-M13 systemd[1]: Reloading.
Jan 24 17:43:56 mani-H61H2-M13 dbus-daemon[591]: Unknown group "power" in message bus configuration file
Jan 24 17:43:56 mani-H61H2-M13 dbus-daemon[591]: [system] Reloaded configuration
Jan 24 17:43:56 mani-H61H2-M13 systemd[1]: Reloading.
Jan 24 17:43:56 mani-H61H2-M13 systemd[1]: Reloading D-Bus System Message Bus.
Jan 24 17:43:56 mani-H61H2-M13 dbus-daemon[591]: Unknown group "power" in message bus configuration file
Jan 24 17:43:56 mani-H61H2-M13 dbus-daemon[591]: [system] Reloaded configuration
Jan 24 17:43:56 mani-H61H2-M13 dbus-send[20919]: method return time=1548348236.842960 sender=org.freedesktop.DBus -> destination=:1.261 serial=3 reply_serial=2
Jan 24 17:43:56 mani-H61H2-M13 systemd[1]: Reloaded D-Bus System Message Bus.
Jan 24 17:43:56 mani-H61H2-M13 PackageKit: daemon quit
Jan 24 17:43:58 mani-H61H2-M13 kernel: [ 8337.828798] usb 1-1-port2: Cannot enable. Maybe the USB cable is bad?
Jan 24 17:43:59 mani-H61H2-M13 kernel: [ 8338.684834] usb 1-1-port2: Cannot enable. Maybe the USB cable is bad?
Jan 24 17:43:59 mani-H61H2-M13 kernel: [ 8338.684957] usb 1-1-port2: attempt power cycle
Jan 24 17:44:00 mani-H61H2-M13 kernel: [ 8339.852827] usb 1-1-port2: Cannot enable. Maybe the USB cable is bad?
Jan 24 17:44:01 mani-H61H2-M13 kernel: [ 8340.704823] usb 1-1-port2: Cannot enable. Maybe the USB cable is bad?
Jan 24 17:44:01 mani-H61H2-M13 kernel: [ 8340.704906] usb 1-1-port2: unable to enumerate USB device
^C
mani@mani-H61H2-M13:~$ 

```

---

### Post by chili555 on 2019-01-24
I regret that I have no other suggestions. I think the device is defective.

---

### Post by macprox86 on 2019-01-24
I recently upgraded to 18.10
i got the error message attached

---

### Post by chili555 on 2019-01-24
> **macprox86 said:**
> I recently upgraded to 18.10
i got the error message attachedYou encountered an error while building the driver. Without examining the build log, it is useless to speculate as to the cause or the fix. Even if we fixed it, as I said previously:> 
Compiling drivers or installing firmware, etc. will do no good until the computer recognizes what the device actually is; USB wireless? Storage device? Mouse? Keyboard? Printer???


---

