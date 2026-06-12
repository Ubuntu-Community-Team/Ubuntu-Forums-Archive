---
title: "Very choppy music playback on bluetooth headset (a2dp)"
date: 2014-10-18
forum: Networking &amp; Wireless
---

### Post by New00Folder on 2014-10-18
Hi,

I am running Ubuntu 14.04 (64 bit) on Lenovo B480 laptop. I have a "bluetooth to 3.5 mm audio output adapter" (simply a bluetooth headset with a 3.5 mm audio output instead of speakers) that I want to use for A2DP music streaming. (Said device works perfectly with my smartphones.)

The trouble is that music playback is very choppy. Long breaks occur and even the headset disconnects very frequently.

I am able to turn on bluetooth, pair the headset and connect to it for HFP & A2DP. This process too isn't free of glitches. I'll describe with logs.

First I tried to turn on bluetooth from the Settings application. The first time I try to do that, UI displays bluetooth turning on and then off quickly. But bluetooth icon now appears on the topmost bar. I tried turning bluetooth on twice from the Settings UI in these logs but that is not necessary. Once bluetooth is available in the topmost bar, I can turn bluetooth on & off from there. It is not possible to turn on bluetooth from the Settings UI though, however many times I try.

```
Oct 18 19:35:52 kernel: [13223.136008] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
Oct 18 19:35:52 kernel: [13223.232581] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21f4
Oct 18 19:35:52 kernel: [13223.232593] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 18 19:35:52 kernel: [13223.232599] usb 1-1.4: Product: BCM20702A0
Oct 18 19:35:52 kernel: [13223.232604] usb 1-1.4: Manufacturer: Broadcom Corp
Oct 18 19:35:52 kernel: [13223.232608] usb 1-1.4: SerialNumber: 446D57C1EF66
Oct 18 19:35:52 mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Oct 18 19:35:52 mtp-probe: bus: 1, device: 5 was not an MTP device
Oct 18 19:35:53 kernel: [13223.693091] usbcore: registered new interface driver btusb
Oct 18 19:35:53 kernel: [13223.706330] usb 1-1.4: Direct firmware load failed with error -2
Oct 18 19:35:53 kernel: [13223.706347] usb 1-1.4: Falling back to user helper
Oct 18 19:35:53 kernel: [13223.707236] Bluetooth: can't load firmware, may not work correctly
Oct 18 19:35:53 bluetoothd[894]: Unknown command complete for opcode 19
Oct 18 19:35:53 bluetoothd[894]: Adapter /org/bluez/894/hci0 has been enabled
Oct 18 19:35:53 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPAG
Oct 18 19:35:53 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPHS
Oct 18 19:35:53 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSource
Oct 18 19:35:53 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSink
Oct 18 19:35:53 bluetoothd[894]: hci0: Add UUID (0x0010) failed: Not Powered (0x0f)
Oct 18 19:35:53 bluetoothd[894]: Adapter /org/bluez/894/hci0 has been disabled
Oct 18 19:35:53 bluetoothd[894]: hci0: Set Powered (0x0005) failed: <unknown status> (0x12)
Oct 18 19:35:53 bluetoothd[894]: Unregister path: /org/bluez/894/hci0
Oct 18 19:35:53 kernel: [13224.218678] usb 1-1.4: USB disconnect, device number 5
Oct 18 19:35:53 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/A2DPSink
Oct 18 19:35:53 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/A2DPSource
Oct 18 19:35:53 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/HFPAG
Oct 18 19:35:53 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/HFPHS
Oct 18 19:35:56 kernel: [13226.723701] usb 1-1.4: new full-speed USB device number 6 using ehci-pci
Oct 18 19:35:56 kernel: [13226.819910] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21f4
Oct 18 19:35:56 kernel: [13226.819922] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 18 19:35:56 kernel: [13226.819928] usb 1-1.4: Product: BCM20702A0
Oct 18 19:35:56 kernel: [13226.819933] usb 1-1.4: Manufacturer: Broadcom Corp
Oct 18 19:35:56 kernel: [13226.819937] usb 1-1.4: SerialNumber: 446D57C1EF66
Oct 18 19:35:56 kernel: [13226.821039] usb 1-1.4: Direct firmware load failed with error -2
Oct 18 19:35:56 kernel: [13226.821050] usb 1-1.4: Falling back to user helper
Oct 18 19:35:56 kernel: [13226.822689] Bluetooth: can't load firmware, may not work correctly
Oct 18 19:35:56 mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Oct 18 19:35:56 mtp-probe: bus: 1, device: 6 was not an MTP device
Oct 18 19:35:56 bluetoothd[894]: Unknown command complete for opcode 19
Oct 18 19:35:56 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPAG
Oct 18 19:35:56 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPHS
Oct 18 19:35:56 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSource
Oct 18 19:35:56 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSink
Oct 18 19:35:56 bluetoothd[894]: Unregister path: /org/bluez/894/hci0
Oct 18 19:35:56 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/A2DPSink
Oct 18 19:35:56 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/A2DPSource
Oct 18 19:35:56 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/HFPAG
Oct 18 19:35:56 bluetoothd[894]: Endpoint unregistered: sender=:1.62 path=/MediaEndpoint/HFPHS
Oct 18 19:35:56 kernel: [13227.037625] usb 1-1.4: USB disconnect, device number 6


```

Now I'll turn bluetooth on from the icon in topmost bar, connect to the headset and start playing a video (with low quality audio bit rate).


```
Oct 18 19:36:08 kernel: [13239.280890] usb 1-1.4: new full-speed USB device number 7 using ehci-pci
Oct 18 19:36:08 kernel: [13239.377068] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21f4
Oct 18 19:36:08 kernel: [13239.377079] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Oct 18 19:36:08 kernel: [13239.377084] usb 1-1.4: Product: BCM20702A0
Oct 18 19:36:08 kernel: [13239.377089] usb 1-1.4: Manufacturer: Broadcom Corp
Oct 18 19:36:08 kernel: [13239.377094] usb 1-1.4: SerialNumber: 446D57C1EF66
Oct 18 19:36:08 kernel: [13239.377960] usb 1-1.4: Direct firmware load failed with error -2
Oct 18 19:36:08 kernel: [13239.377966] usb 1-1.4: Falling back to user helper
Oct 18 19:36:08 kernel: [13239.379401] Bluetooth: can't load firmware, may not work correctly
Oct 18 19:36:08 mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Oct 18 19:36:08 mtp-probe: bus: 1, device: 7 was not an MTP device
Oct 18 19:36:08 bluetoothd[894]: Unknown command complete for opcode 19
Oct 18 19:36:08 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPAG
Oct 18 19:36:08 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/HFPHS
Oct 18 19:36:08 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSource
Oct 18 19:36:08 bluetoothd[894]: Endpoint registered: sender=:1.62 path=/MediaEndpoint/A2DPSink
Oct 18 19:36:08 bluetoothd[894]: Adapter /org/bluez/894/hci0 has been enabled
Oct 18 19:36:55 bluetoothd[894]: No agent available for request type 0
Oct 18 19:36:55 bluetoothd[894]: btd_event_request_pin: Operation not permitted
Oct 18 19:37:04 bluetoothd[894]: Discovery session 0x7fe5c2583660 with :1.110 activated
Oct 18 19:37:15 bluetoothd[894]: Stopping discovery
Oct 18 19:37:18 bluetoothd[894]: Badly formated or unrecognized command: AT+XEVENT=0,0
Oct 18 19:37:19 kernel: [13309.978741] input: 5A:5A:5B:A7:53:1C as /devices/virtual/input/input13
Oct 18 19:37:20 bluetoothd[894]: /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd1: fd(28) ready
Oct 18 19:37:20 rtkit-daemon[1427]: Successfully made thread 16372 of process 1954 (n/a) owned by '1000' RT at priority 5.
Oct 18 19:37:20 rtkit-daemon[1427]: Supervising 4 threads of 1 processes of 1 users.
Oct 18 19:37:51 pulseaudio[1954]: [alsa-source-ALC269VC Analog] ratelimit.c: 82 events suppressed
Oct 18 19:37:51 pulseaudio[1954]: [alsa-source-ALC269VC Analog] asyncq.c: q overrun, queuing locally
Oct 18 19:37:52 bluetoothd[894]: Start: Connection timed out (110)
Oct 18 19:37:51 pulseaudio[1954]: message repeated 10 times: [ [alsa-source-ALC269VC Analog] asyncq.c: q overrun, queuing locally]
Oct 18 19:37:52 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Failed to acquire transport /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd1
Oct 18 19:37:52 pulseaudio[1954]: [pulseaudio] sink-input.c: Failed to create sink input: sink is suspended.
Oct 18 19:37:54 bluetoothd[894]: Abort: Connection timed out (110)
Oct 18 19:37:54 acpid: input device has been disconnected, fd 17
Oct 18 19:38:00 bluetoothd[894]: Badly formated or unrecognized command: AT+XEVENT=0,0
Oct 18 19:38:04 kernel: [13355.681559] input: 5A:5A:5B:A7:53:1C as /devices/virtual/input/input14
Oct 18 19:38:05 bluetoothd[894]: /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd3: fd(27) ready
Oct 18 19:38:05 rtkit-daemon[1427]: Successfully made thread 16380 of process 1954 (n/a) owned by '1000' RT at priority 5.
Oct 18 19:38:05 rtkit-daemon[1427]: Supervising 4 threads of 1 processes of 1 users.
Oct 18 19:38:55 bluetoothd[894]: Badly formated or unrecognized command: AT+XEVENT=0,0
Oct 18 19:38:57 kernel: [13408.075063] input: 5A:5A:5B:A7:53:1C as /devices/virtual/input/input15
Oct 18 19:38:58 bluetoothd[894]: /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd5: fd(27) ready
Oct 18 19:38:58 rtkit-daemon[1427]: Successfully made thread 16479 of process 1954 (n/a) owned by '1000' RT at priority 5.
Oct 18 19:38:58 rtkit-daemon[1427]: Supervising 4 threads of 1 processes of 1 users.
Oct 18 19:39:51 bluetoothd[894]: No reply to Start request
Oct 18 19:39:51 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Failed to acquire transport /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd5
Oct 18 19:39:51 pulseaudio[1954]: [pulseaudio] sink-input.c: Failed to create sink input: sink is suspended.
Oct 18 19:39:56 bluetoothd[894]: Badly formated or unrecognized command: AT+XEVENT=0,0
Oct 18 19:39:58 kernel: [13469.137635] input: 5A:5A:5B:A7:53:1C as /devices/virtual/input/input16
Oct 18 19:39:59 bluetoothd[894]: /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd7: fd(27) ready
Oct 18 19:39:59 rtkit-daemon[1427]: Successfully made thread 16486 of process 1954 (n/a) owned by '1000' RT at priority 5.
Oct 18 19:39:59 rtkit-daemon[1427]: Supervising 4 threads of 1 processes of 1 users.
Oct 18 19:41:19 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 84838 us (= 14964 bytes) in audio stream
Oct 18 19:41:20 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 625769 us (= 110384 bytes) in audio stream
Oct 18 19:41:20 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 151176 us (= 26664 bytes) in audio stream
Oct 18 19:41:20 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 360304 us (= 63556 bytes) in audio stream
Oct 18 19:41:23 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 2476756 us (= 436896 bytes) in audio stream
Oct 18 19:41:23 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 450574 us (= 79480 bytes) in audio stream
Oct 18 19:42:18 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 158691 us (= 27992 bytes) in audio stream
Oct 18 19:42:18 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 412755 us (= 72808 bytes) in audio stream
Oct 18 19:42:18 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 92573 us (= 16328 bytes) in audio stream
Oct 18 19:42:18 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 20500 us (= 3616 bytes) in audio stream
Oct 18 19:42:19 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 172317 us (= 30396 bytes) in audio stream
Oct 18 19:42:19 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 443779 us (= 78280 bytes) in audio stream
Oct 18 19:42:20 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 41416 us (= 7304 bytes) in audio stream
Oct 18 19:42:20 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 129674 us (= 22872 bytes) in audio stream


```

The logs "Skipping n us ... " occur after the audio breaks. But not all audio breaks cause logs like this.

Now I'll play a music file with higher audio quality bitrate. After a few seconds playback stopped completely and the following was displayed in logs.

```
Oct 18 19:44:12 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Skipping 18674083 us (= 3294108 bytes) in audio stream
Oct 18 19:44:12 pulseaudio[1954]: [bluetooth] module-bluetooth-device.c: Failed to write data to socket: Connection timed out
Oct 18 19:44:12 pulseaudio[1954]: [pulseaudio] bluetooth-util.c: Failed to release transport /org/bluez/894/hci0/dev_5A_5A_5B_A7_53_1C/fd7: Method "Release" with signature "s" on interface "org.bluez.MediaTransport" doesn't exist

```

The headset is now disconnected.

Now I suspected that there was something wrong with the firmware in use as suggested by the kernel logs while turning bluetooth on. I found on many online posts that it is possible to load correct firmware by getting the hex files from windows driver, converting it to .hcd format and saving it as fw-<vendor id>_<product id>.hcd in /lib/firmware/ (fw-0a5c_21f4.hcd in my case). This did not work. Kernel logs showed the USB device being discovered, 0x0c03 (HCI Reset) command getting timed out & USB device getting disconnected. This process would go on in an infinite loop. (I don't have the exact logs right now.) There were a bunch of hex files in broadcom's driver folder in windows and I met with the same failure with all of them.

Now I am totally at loss. If anyone has had any experience in this field, please suggest me how to deal with this.

---

