---
title: "ActiveSync on Vbox"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-02-10
This is the closest I've managed to get a full syncing and program installation system going for my HTC Touch Pro.

I'm running Vbox 2.1.2 on Intrepid with XP as guest.
After managing to get Vbox to recognise my device, I added this line to /etc/init.d/mountkernfs.sh

```
domount usbfs "" /proc/bus/usb usbdevfs -onoexec,nosuid,nodev,devgid=<gid>,devmode=664
```

Now I can activate my device in Vbox and get it to load in XP. When I have the Advanced Networking turned off in Windows mobile Vbox recognises my device as HTC Generic Serial. If I use the Advanced Network options, it shows up as HTC Generic RNDIS. The USB 2.0 option has to effect so far on or off.

When I load HTC Generic Serial, Windows seems to detect it just fine and install the drivers. It shows up in it's own category in Device Manager with no errors.

If I try to load the HTC Generic RNDIS device (with the advanced network functionality turned on) Windows seems to detect a Windows Mobile based device fine but it says there were problems installing my hardware. In device manager, this one is listed as "Windows Mobile-based Device #2" with a "This device cannot start. Code 10" error

I realised I was running an older version of ActiveSync and after upgrading to 4.5 I get this message whenever I start up my XP install.
"Microsoft ActiveSync cannot open the COM port."

I didn't think this was an issue as I'm using USB and when I Googled the error it seems to be more related to bluetooth issues, and I don't have BT on my desktop.

Here's my lsusb output with it pluged in,
```
Bus 002 Device 003: ID 1532:0101 Razer USA, Ltd 
Bus 002 Device 002: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 0bb4:0a2c High Tech Computer Corp. PocketPC Sync
Bus 001 Device 003: ID 03f0:5911 Hewlett-Packard PhotoSmart C6180
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And this is what is reported in the system log when I plug it in.
```
Feb 10 14:07:02 chris-desktop kernel: [ 4788.878020] usb 1-6: new high speed USB device using ehci_hcd and address 18
Feb 10 14:07:02 chris-desktop kernel: [ 4789.018274] usb 1-6: configuration #1 chosen from 1 choice
Feb 10 14:07:02 chris-desktop kernel: [ 4789.021063] ipaq 1-6:1.0: PocketPC PDA converter detected
Feb 10 14:07:02 chris-desktop kernel: [ 4789.022635] usb 1-6: PocketPC PDA converter now attached to ttyUSB0
```

So, this is what I've tried and I cant find any information to get further other than disabling the Advanced Network which I've tried. Anyone know why Windows would recognise my device but not ActiveSync?

---

### Post by OldTimeTech on 2009-02-10
You should really take this down to Virtualization, they are really good with Vbox.

---

### Post by HittingSmoke on 2009-02-10
> **OldTimeTech said:**
> You should really take this down to Virtualization, they are really good with Vbox.

Would a mod mind moving it for me so I don't double post the same issue?

---

### Post by HittingSmoke on 2009-02-11
I know people have made it work, and I know I'm close because it's at least recognised properly under the XP system.

No one knows the step to take to get ActiveSync to see it?

---

