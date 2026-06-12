---
title: "usb keyboard does not work on startup"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by irishy on 2009-12-03
Help please after upgrading from hardy heron 8.04 to 8.10 the usb keyboard does not work on start up so I have no choice in which system boots up can anyone help please
I hope my question makes sense
Irishy

---

### Post by ukripper on 2009-12-03
can you plug that keyboard in another usb port and see if that works?

---

### Post by irishy on 2009-12-03
Thanks for responding The keyboard works now after trying 2 other ports 
nobody had moved these round in recent times and I don't understand the situation is there an explanation
thanks 
Irishy

---

### Post by irishy on 2009-12-03
To explain myself a bit better the keboard and mouse did work before when ubuntu had booted up it was just that I had no control of the dual boot at start up
thanks
Irishy

---

### Post by ukripper on 2009-12-03
> **irishy said:**
> To explain myself a bit better the keboard and mouse did work before when ubuntu had booted up it was just that I had no control of the dual boot at start up
thanks
Irishy

control at startup? Do you mean it wasn't working for BIOS like del key wasn't working or at grub keys were not working?

---

### Post by irishy on 2009-12-03
Thanks again
What I mean is the screen that has ubuntu and windows xp in a list of selections at this point the keyboard would not operate but when ubuntu automatically started to boot the keyboard started to operate however with you getting me to change ports the problem seems to have gone away or has it
thanks 
Irishy

---

### Post by ukripper on 2009-12-03
> **irishy said:**
> automatically started to boot the keyboard started to operate however with you getting me to change ports the problem seems to have gone away or has it
thanks 
Irishy

if you plug your keyboard back in same place where it was and boot again. See if it works at the selection screen then I can be sure problem is gone. otherwise i would think problem is with your usb ports

---

### Post by irishy on 2009-12-03
Thanks for your patience the keyboard only works in the the port I had moved it to on your request initially, that is in fact only 1 out of 6, the other ports work with everything else so in my simple terms if I remember this I don,t have a problem or again do I? 
Thanks
Irishy

---

### Post by ukripper on 2009-12-03
ok another test now to identify the problem. Shutdown your computer and connect your keyboard to the port you think is not working. Use any ubuntu cd you got and boot into the live cd. Once running from ubuntu live cd , check whether you can type ok and your keyboard is working?

---

### Post by irishy on 2009-12-04
Sorry for the delay I have done as you ask and the keyboard does not respond could it be  that the usb port that does work is the one I have installed the keyboard on initially
thanks again
Irishy

---

### Post by ukripper on 2009-12-04
which ubuntu version's live cd you tried? ubuntu 8.04, 8.10, 9.04 or 9.10?

---

### Post by irishy on 2009-12-04
ubuntu 8.04

---

### Post by ukripper on 2009-12-04
ok now normally boot into ubuntu 8.10 and when inside ubuntu unplug your keyboard from working usb port and plug it in the nonworking one. Then again plug it in working one so that you can type these commands in terminal:
```
tail -n 50 /var/log/messages
```

```
dmesg | tail
```

and post output here.

---

### Post by irishy on 2009-12-04
tony@tony-desktop:~$ tail -n 50 /var/log/messages
Dec  4 13:17:54 tony-desktop kernel: [   24.655074] Bluetooth: HCI device and connection manager initialized
Dec  4 13:17:54 tony-desktop kernel: [   24.655082] Bluetooth: HCI socket layer initialized
Dec  4 13:17:54 tony-desktop kernel: [   24.694933] Bluetooth: L2CAP ver 2.11
Dec  4 13:17:54 tony-desktop kernel: [   24.694945] Bluetooth: L2CAP socket layer initialized
Dec  4 13:17:54 tony-desktop kernel: [   24.706955] Bluetooth: RFCOMM socket layer initialized
Dec  4 13:17:54 tony-desktop kernel: [   24.706988] Bluetooth: RFCOMM TTY layer initialized
Dec  4 13:17:54 tony-desktop kernel: [   24.706993] Bluetooth: RFCOMM ver 1.10
Dec  4 13:17:54 tony-desktop kernel: [   24.753722] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Dec  4 13:17:54 tony-desktop kernel: [   24.753735] Bluetooth: BNEP filters: protocol multicast
Dec  4 13:17:54 tony-desktop kernel: [   24.816936] Bridge firewalling registered
Dec  4 13:17:54 tony-desktop kernel: [   24.886493] Bluetooth: SCO (Voice Link) ver 0.6
Dec  4 13:17:54 tony-desktop kernel: [   24.886506] Bluetooth: SCO socket layer initialized
Dec  4 13:17:59 tony-desktop kernel: [   29.257574] NET: Registered protocol family 17
Dec  4 13:18:12 tony-desktop pulseaudio[5554]: ltdl-bind-now.c: Failed to find original dlopen loader.
Dec  4 13:18:12 tony-desktop pulseaudio[5556]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Dec  4 13:18:12 tony-desktop pulseaudio[5556]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Dec  4 13:20:37 tony-desktop kernel: [  187.267115] usb 2-5: USB disconnect, address 2
Dec  4 13:20:49 tony-desktop kernel: [  199.832041] usb 1-5: new high speed USB device using ehci_hcd and address 9
Dec  4 13:20:50 tony-desktop kernel: [  200.182159] usb 1-5: configuration #1 chosen from 1 choice
Dec  4 13:20:51 tony-desktop kernel: [  201.824305] usbcore: registered new interface driver libusual
Dec  4 13:20:51 tony-desktop kernel: [  201.849190] Initializing USB Mass Storage driver...
Dec  4 13:20:52 tony-desktop kernel: [  202.320651] scsi6 : SCSI emulation for USB Mass Storage devices
Dec  4 13:20:52 tony-desktop kernel: [  202.321767] usbcore: registered new interface driver usb-storage
Dec  4 13:20:52 tony-desktop kernel: [  202.321780] USB Mass Storage support registered.
Dec  4 13:20:57 tony-desktop kernel: [  207.320820] scsi 6:0:0:0: Direct-Access     Maxtor   OneTouch         0125 PQ: 0 ANSI: 4
Dec  4 13:20:57 tony-desktop kernel: [  207.323170] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec  4 13:20:57 tony-desktop kernel: [  207.323790] sd 6:0:0:0: [sdb] Write Protect is off
Dec  4 13:20:57 tony-desktop kernel: [  207.324542] sd 6:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Dec  4 13:20:57 tony-desktop kernel: [  207.325167] sd 6:0:0:0: [sdb] Write Protect is off
Dec  4 13:20:57 tony-desktop kernel: [  207.325184]  sdb: sdb1
Dec  4 13:20:57 tony-desktop kernel: [  207.348755] sd 6:0:0:0: [sdb] Attached SCSI disk
Dec  4 13:20:57 tony-desktop kernel: [  207.349062] sd 6:0:0:0: Attached scsi generic sg2 type 0
Dec  4 13:20:58 tony-desktop kernel: [  208.504113] usb 1-5: USB disconnect, address 9
Dec  4 13:20:58 tony-desktop kernel: [  208.948042] usb 2-6: new full speed USB device using ohci_hcd and address 24
Dec  4 13:20:59 tony-desktop kernel: [  209.696041] usb 2-6: new full speed USB device using ohci_hcd and address 25
Dec  4 13:21:00 tony-desktop kernel: [  210.440038] usb 2-6: new full speed USB device using ohci_hcd and address 26
Dec  4 13:21:00 tony-desktop kernel: [  211.024037] usb 2-6: new full speed USB device using ohci_hcd and address 27
Dec  4 13:21:04 tony-desktop kernel: [  214.656043] usb 2-5: new low speed USB device using ohci_hcd and address 28
Dec  4 13:21:04 tony-desktop kernel: [  214.877299] usb 2-5: configuration #1 chosen from 1 choice
Dec  4 13:21:04 tony-desktop kernel: [  214.892992] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input9
Dec  4 13:21:04 tony-desktop kernel: [  214.941297] input,hidraw0: USB HID v1.10 Keyboard [PATEN USB HID Device        ] on usb-0000:00:02.0-5
Dec  4 13:21:04 tony-desktop kernel: [  214.957993] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.1/input/input10
Dec  4 13:21:04 tony-desktop kernel: [  215.009298] input,hidraw1: USB HID v1.10 Device [PATEN USB HID Device        ] on usb-0000:00:02.0-5
Dec  4 13:21:04 tony-desktop kernel: [  215.021594] input: PATEN USB HID Device         as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.2/input/input11
Dec  4 13:21:04 tony-desktop kernel: [  215.081305] input,hidraw2: USB HID v1.10 Mouse [PATEN USB HID Device        ] on usb-0000:00:02.0-5
Dec  4 13:21:05 tony-desktop kernel: [  215.257068] usb 2-6: new full speed USB device using ohci_hcd and address 29
Dec  4 13:21:05 tony-desktop kernel: [  215.988088] usb 2-6: new full speed USB device using ohci_hcd and address 30
Dec  4 13:21:06 tony-desktop kernel: [  216.736035] usb 2-6: new full speed USB device using ohci_hcd and address 31
Dec  4 13:21:07 tony-desktop kernel: [  217.320033] usb 2-6: new full speed USB device using ohci_hcd and address 32
Dec  4 13:21:07 tony-desktop kernel: [  218.052037] usb 2-5: reset low speed USB device using ohci_hcd and address 28
tony@tony-desktop:~$ dmesg | tail
[  215.709033] usb 2-6: device descriptor read/64, error -62
[  215.988088] usb 2-6: new full speed USB device using ohci_hcd and address 30
[  216.168035] usb 2-6: device descriptor read/64, error -62
[  216.456062] usb 2-6: device descriptor read/64, error -62
[  216.736035] usb 2-6: new full speed USB device using ohci_hcd and address 31
[  217.144031] usb 2-6: device not accepting address 31, error -62
[  217.320033] usb 2-6: new full speed USB device using ohci_hcd and address 32
[  217.728030] usb 2-6: device not accepting address 32, error -62
[  217.728408] hub 2-0:1.0: unable to enumerate USB device on port 6
[  218.052037] usb 2-5: reset low speed USB device using ohci_hcd and address 28
I hope I have done this right

---

### Post by ukripper on 2009-12-04
> **irishy said:**
> 
tony@tony-desktop:~$ dmesg | tail
[  215.709033] usb 2-6: device descriptor read/64, error -62
[  215.988088] usb 2-6: new full speed USB device using ohci_hcd and address 30
[  216.168035] usb 2-6: device descriptor read/64, error -62
[  216.456062] usb 2-6: device descriptor read/64, error -62
[  216.736035] usb 2-6: new full speed USB device using ohci_hcd and address 31
[  217.144031] usb 2-6: device not accepting address 31, error -62
[  217.320033] usb 2-6: new full speed USB device using ohci_hcd and address 32
[  217.728030] usb 2-6: device not accepting address 32, error -62
[  217.728408] hub 2-0:1.0: unable to enumerate USB device on port 6
[  218.052037] usb 2-5: reset low speed USB device using ohci_hcd and address 28
I hope I have done this right

you have done it very well. i was looking for this kind of output with errors. There was a bug reported on launchpad after upgrade it usb keyboard didn't work. [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/395568](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/395568)

Can you try following and see if your keyboard starts working again on that usb port:

```
sudo mv /lib/udev/rules.d/70-hid2hci.rules{,.disabled}
```
```
  sudo update-initramfs -u
```

reboot and let your keyboard be connected to that faulty usb port.

If it doesn't work then switch it back :

 ```
sudo mv /lib/udev/rules.d/70-hid2hci.rules{.disabled,}
```
  ```
sudo update-initramfs -u
```

---

### Post by irishy on 2009-12-04
Thanks again
I tried the first instruction but after copying and pasting the first command I pressed enter and it asked for password but I could not type anything in 
I also have an old keyboard not wireless that
 I also could not type in with
Irishy

---

### Post by mgmiller on 2009-12-04
Take a look in your BIOS and make sure you have legacy USB enabled for the keyboard.  This option will be in different places in different BIOS's so you will have to look around a bit to find it.

What this does is enable USB keyboard to work before the OS loads any USB drivers.  You may need to use a USB to atx adapter so the keyboard works to get you into BIOS.

---

### Post by ukripper on 2009-12-04
> **irishy said:**
> Thanks again
I tried the first instruction but after copying and pasting the first command I pressed enter and it asked for password but I could not type anything in 
I also have an old keyboard not wireless that
 I also could not type in with
Irishy

ok you can follow the above commands even with working usb port.

---

### Post by irishy on 2009-12-05
Thanks for all suggestions the the usb is enabled.
when I copy and paste the commands and press enter the request for password comes up but I cannot type it in either with usb keyboard or wired one 
thanks 
Irishy

---

### Post by irishy on 2009-12-05
Tried it again after restart and this is what I've got> tony@tony-desktop:~$ sudo mv /lib/udev/rules.d/70-hid2hci.rules{,.disabled}
[sudo] password for tony: 
mv: cannot stat `/lib/udev/rules.d/70-hid2hci.rules': No such file or directory
tony@tony-desktop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.27-15-generic
tony@tony-desktop:~$ 


---

