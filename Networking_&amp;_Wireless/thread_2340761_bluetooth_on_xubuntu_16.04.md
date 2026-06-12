---
title: "bluetooth on xubuntu 16.04"
date: 2016-10-21
forum: Networking &amp; Wireless
---

### Post by bigstuff on 2016-10-21
Hey im having trouble with my bluetooth adapter not connecting to anything, all I get is this error:
  Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available

i also did: lspci -knn | grep Net -A2; lsusb
and it gave out this:

```
03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
    Subsystem: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:1020]
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 002: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth**
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


im running xubuntu 16.04
any help would be greatly appreciated

---

### Post by jeremy31 on 2016-10-21
Welcome to the forums

Let's try something in terminal
```
bluetoothctl
power on
scan on
```
See if the same error occurs, use CTRL + d or command exit to leave bluetoothctl.  I am thinking the Dell bluetooth module is more likely to work than the Microsoft one

---

### Post by bigstuff on 2016-10-21
so... I did that and tryed to connect to it using bluetoothctl but then  it connected for about 2 seconds than disconnected and i cant connect to  it again. output:
```
chas@chas-Inspiron-9300:~$ bluetoothctl
[NEW] Controller 00:10:C6:EF:DC:9C chas-Inspiron-9300 [default]
[bluetooth]# power on
Changing power on succeeded
[bluetooth]# scan on
Discovery started
[NEW] Device FC:58:FA:96:E2:83 BLUESYNC BX
[bluetooth]# pair FC:58:FA:96:E2:83
Attempting to pair with FC:58:FA:96:E2:83
[CHG] Device FC:58:FA:96:E2:83 Connected: yes
[CHG] Device FC:58:FA:96:E2:83 UUIDs: 00001101-0000-1000-8000-00805f9b34fb
[CHG] Device FC:58:FA:96:E2:83 UUIDs: 00001108-0000-1000-8000-00805f9b34fb
[CHG] Device FC:58:FA:96:E2:83 UUIDs: 0000110b-0000-1000-8000-00805f9b34fb
[CHG] Device FC:58:FA:96:E2:83 UUIDs: 0000110e-0000-1000-8000-00805f9b34fb
[CHG] Device FC:58:FA:96:E2:83 UUIDs: 0000111e-0000-1000-8000-00805f9b34fb
[CHG] Device FC:58:FA:96:E2:83 Paired: yes
Pairing successful
[CHG] Device FC:58:FA:96:E2:83 Connected: no
[CHG] Device FC:58:FA:96:E2:83 RSSI: -58
[bluetooth]# connect FC:58:FA:96:E2:83
Attempting to connect to FC:58:FA:96:E2:83
Failed to connect: org.bluez.Error.Failed

```

Also I did a test and the **Bus 005 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth, **is not really for bluetooth. i removed my mouse dongle did the hardware scan again and it was not there. I'm not sure why it says *for bluetooth *

---

### Post by jeremy31 on 2016-10-22
What type of device are you trying to connect to?  There is a bug that prevents some people from connecting to bluetooth audio devices
Bus 005 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth  The description comes from a database that anyone can add info to after registering

---

### Post by bigstuff on 2016-10-22
Yeah.. im trying to connect to my bluetooth speaker. so is there a fix or is it a lost cause?

---

### Post by jeremy31 on 2016-10-22
One of the Pulseaudio people were working on it and this has helped some keep connected
```
sudo add-apt-repository ppa:themuso/ppa
sudo apt-get update && sudo apt-get upgrade
```

Reboot

---

### Post by bigstuff on 2016-10-24
No it didn't help but now i cant connect to anything not even my bluetooth keyboard

---

### Post by fenrice on 2016-10-24
I was having some bluetooth problems today, suspected a power management issue and this seems to fix it. The only bluetooth device I am using is a bluetooth mouse and I know it works flawlessly under windows, and lo and behold yesterday was the first time I used bluetooth under ubuntu 16.04.1 . So anyway this page may help, I don't feel like retyping it all :) . [https://pgnunes.blogspot.com/2015/05/linux-bluetooth-mouse-disconnectsnot.html](https://pgnunes.blogspot.com/2015/05/linux-bluetooth-mouse-disconnectsnot.html) check dmesg for the messages mentioned in that article, it's what clued me in.  This fixed my issue.

Here it is for posterity, in case that website ever goes down, please reference webpage for the original. 
[h=3]Linux bluetooth mouse disconnects/not auto-reconnecting[/h][COLOR=#666666][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#666666][FONT=&quot]This was a problem that was bugging me for a while. Once my bluetooth mouse was paired (Microsoft Sculpt Comfort on a Dell XPS 15 9530) I was suffering disconnects. Sometimes randomly and sometimes when I was not using it for a while...


After looking at kernel messages I've found some errors like these:

[FONT=&quot][  305.647268] pci_pm_runtime_suspend(): hcd_pci_runtime_suspend+0x0/0x40 [usbcore] returns -16
[  333.366960] xhci_hcd 0000:00:14.0: xHC is not running.
[  353.538915] xhci_hcd 0000:00:14.0: Port resume took longer than 20000 msec, port status = 0x400603[/FONT]

From the [FONT=&quot]pci_pm_runtime_suspend [FONT=inherit][/FONT][/FONT][FONT=inherit]I thought it was related to power management... And it fact it was. Here's how I've solved this problem:[/FONT]
[FONT=&quot]
[/FONT]

[LIST=1]
[*]Identify the bluetooth device id (which is connected through USB)

[FONT=&quot]$ lsusb -v[/FONT]
This should return a list where you need to identify the bluetooth device. In my case it was this one:

[FONT=&quot](...)
Bus 003 Device 003: ID **8087:07dc** Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  **bDeviceProtocol         1 Bluetooth**
(...)
[/FONT]
[*]Update [FONT=&quot]laptop-mode[/FONT] tool configuration to not manage this device - please note that this will prevent suspending of the bluetooth device - this probably increases battery consumption but should not be enough to be relevant...

[FONT=&quot]$ nano /etc/laptop-mode/conf.d/runtime-pm.conf[/FONT]

Search for the blacklist section and add the device ID:

[FONT=&quot]# The list of Device IDs that should not use autosuspend. Use system commands or
# look into sysfs to find out the IDs of your devices.
# Example: AUTOSUSPEND_DEVID_BLACKLIST="046d:c025 0123:abcd"
AUTOSUSPEND_RUNTIME_DEVID_BLACKLIST="8087:07dc"[/FONT] [FONT=inherit]
[/FONT]
[/LIST]
Save the file, reboot and it the problem should now be solved.

For reference, this was on a Linux Debian 8 but I was facing the same problem with Ubuntu 14/15.
[/FONT][/COLOR]

---

### Post by bigstuff on 2016-10-24
i was looking around and found this:  [http://askubuntu.com/questions/801404/bluetooth-connection-failed-blueman-bluez-errors-dbusfailederror-protocol-no](http://askubuntu.com/questions/801404/bluetooth-connection-failed-blueman-bluez-errors-dbusfailederror-protocol-no)

i did 
                                        "This solution worked for me: [https://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/](https://zach-adams.com/2014/07/bluetooth-audio-sink-stream-setup-failed/)

  
[LIST=1]
[*]sudo apt-get install pulseaudio-module-bluetooth
[*]pactl load-module module-bluetooth-discover
[*]Delete the device from bluetooth devices and pair it again."
[/LIST]

---

