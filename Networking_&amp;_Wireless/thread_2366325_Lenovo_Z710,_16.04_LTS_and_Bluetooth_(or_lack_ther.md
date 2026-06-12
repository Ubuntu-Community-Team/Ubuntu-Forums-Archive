---
title: "Lenovo Z710, 16.04 LTS and Bluetooth (or lack thereof)"
date: 2017-07-16
forum: Networking &amp; Wireless
---

### Post by Roy_Bettle on 2017-07-16
JBL Bluetooth speaker cannot be found by my laptop.  All the Bluetooth apps/drivers seem to be installed correctly (one error that I noticed, below).  Cell phone has Bluetooth turned off as it has a current pairing relationship with the speaker.  Speaker was power cycled as was my laptop, yet the laptop cannot find the speaker.  Output from " lspci -nnk | grep -iA2 net; lsusb; hciconfig -a; dmesg | egrep -i 'blue|firm' " is as follows:

```

01:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: wl
--
02:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:1091]
    Kernel driver in use: alx
    Kernel modules: alx
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:5136 ASMedia Technology Inc. ASM1053 SATA 6Gb/s bridge
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 105b:e065 Foxconn International, Inc. BCM43142A0 Bluetooth module
Bus 003 Device 004: ID 174f:14ad Syntek 
Bus 003 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 80:56:F2:E9:22:52  ACL MTU: 1021:8  SCO MTU: 64:1
    UP RUNNING 
    RX bytes:1854 acl:0 sco:0 events:133 errors:0
    TX bytes:5692 acl:0 sco:0 commands:133 errors:0
    Features: 0xff 0xfe 0xcf 0xfe 0xdb 0xff 0x7b 0x87
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF 
    Link mode: SLAVE ACCEPT 
    Name: 'Z710-Main'
    Class: 0x10010c
    Service Classes: Object Transfer
    Device Class: Computer, Laptop
    HCI Version: 4.0 (0x6)  Revision: 0x0
    LMP Version: 4.0 (0x6)  Subversion: 0x210b
    Manufacturer: Broadcom Corporation (15)


[    0.167816] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    1.583589] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x595f03)
[    7.908472] Bluetooth: Core ver 2.21
[    7.908483] Bluetooth: HCI device and connection manager initialized
[    7.908485] Bluetooth: HCI socket layer initialized
[    7.908487] Bluetooth: L2CAP socket layer initialized
[    7.908491] Bluetooth: SCO socket layer initialized
[    8.032028] Bluetooth: hci0: BCM: chip id 70
[    8.048016] Bluetooth: hci0: BCM43142A
[    8.048018] Bluetooth: hci0: BCM (001.001.011) build 0000
**[    8.048976] bluetooth hci0: Direct firmware load for brcm/BCM.hcd failed with error -2**
[    8.048978] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   10.054456] Bluetooth: hci0 command 0x1003 tx timeout
[   10.154783] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.154784] Bluetooth: BNEP filters: protocol multicast
[   10.154787] Bluetooth: BNEP socket layer initialized
[   52.097045] Bluetooth: RFCOMM TTY layer initialized
[   52.097050] Bluetooth: RFCOMM socket layer initialized
[   52.097055] Bluetooth: RFCOMM ver 1.11
[ 1541.488302] Bluetooth: hci0 command 0x1003 tx timeout

```

Might the boldfaced section be the problem?  I honestly don't know what to do from here.  Thanks!

---

### Post by jeremy31 on 2017-07-16
```
wget https://www.dropbox.com/s/f503f6r686riiow/fw-105b_e065.hcd
sudo cp fw-105b_e065.hcd /lib/firmware/brcm/BCM.hcd
sudo modprobe -r btusb
sudo modprobe btusb
```

Then it should work

---

### Post by Roy_Bettle on 2017-07-16
Thank you!  That got me part of the way home in that I now find the "JBL Charge 2" and can add it.  It appears to pair OK, but when I go to "Connect" I get "Device added successfully, but failed to connect" and I get this whether I try "Headset", "Audio Sink" (?) or "Handsfree".

In this thread here - [https://ubuntuforums.org/showthread.php?t=2170439&highlight=jbl+charge](https://ubuntuforums.org/showthread.php?t=2170439&highlight=jbl+charge) - there is mention of being prompted for the PIN code, which did happen when pairing with my cell, but I have not been prompted for any PIN code thus far.

Is there a conf file somewhere that I can enter the PIN code or something like that?

Thanks!

---

### Post by jeremy31 on 2017-07-16
I have never had to enter a PIN for a headset, post results for ```
pactl list short | grep blue
```

---

### Post by Roy_Bettle on 2017-07-16
By the way, I managed to locate an error code that may help:

```

Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available

```

---

### Post by Roy_Bettle on 2017-07-16
> **jeremy31 said:**
> I have never had to enter a PIN for a headset, post results for ```
pactl list short | grep blue
```

There are no results (hit "Enter" and it just drops to a new line; no response from the system).

---

### Post by Roy_Bettle on 2017-07-16
Got it!  Google'd the error code about "Protocol not available" and found this post:  [https://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/](https://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/)

Didn't work after the first step, but now is working fine after the second.  Thank you!

---

### Post by Roy_Bettle on 2017-07-16
OK, partially solved.  The speaker has been found, paired, and connected ... but no sound comes out.  Not as a headset nor with the high fidelity option.  So, any ideas?  =)

Thanks again!

---

### Post by jeremy31 on 2017-07-16
See [https://askubuntu.com/a/837732/300665](https://askubuntu.com/a/837732/300665) and see if it helps

---

### Post by Roy_Bettle on 2017-07-17
OK, read through the link you gave me and the page it linked to as well.  That looks ... awesomely confusing.  What, exactly, do I do with that script?  Sorry, but I do OK up to a point and digging into scripts is one of those things I've always wanted to understand but, as yet, I do not.  Do I download the ZIP and ...?  Unpack it ... where?  And then what?  Thanks again!

---

### Post by Roy_Bettle on 2017-07-17
> **jeremy31 said:**
> See [https://askubuntu.com/a/837732/300665](https://askubuntu.com/a/837732/300665) and see if it helps

Well, I think I'm almost there.  I figured out how to auto-execute it, where to put it, etc., but now when running it I watch it error out with the following:

```

roy@Z710-Main:~/.local/bin$ python fix-bt.py
Disconnected 0C:A6:94:AC:4F:21
Connected 0C:A6:94:AC:4F:21
Fixing...
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/usr/lib/**python2.7**/dist-packages/dbus/connection.py", line 230, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "fix-bt.py", line 32, in cb
    subprocess.call([A2DP,device_id])
  File "/usr/lib/**python2.7**/subprocess.py", line 523, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/**python2.7**/subprocess.py", line 711, in __init__
    errread, errwrite)
  File "/usr/lib/**python2.7**/subprocess.py", line 1343, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

The "python2.7" bit is obviously a problem as this script needs Python 3.5 (which is installed) but how do I force it to execute using 3.5?  It has the line in the script for 3.5 already so ...?  I'm not sure what to do here.  There is one curious line in the beginning of his script that goes ```
#! /usr/bin/env python3.5
``` and I find that odd as it looks like the script assumes /usr/bin/env is a directory but "env" is an executable ...?  Or am I reading that wrong?

Thanks again!

---

### Post by jeremy31 on 2017-07-17
You should be able to run it using ```
~/.local/bin/fix-bt.py
```
I just put the script in my home folder and called it a2dp.py and use ```
./a2dp.py
```

---

### Post by Roy_Bettle on 2017-07-17
Hah!  That did it!  Thank you.  I guess I over-complicated things a bit, eh?  I appreciate your help.  Thanks!

---

