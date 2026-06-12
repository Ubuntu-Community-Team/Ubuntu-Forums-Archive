---
title: "Intel 7260 bluetooth device (usb-device-8087-07dc) at 100% energy usage"
date: 2016-07-12
forum: Networking &amp; Wireless
---

### Post by adlerhn on 2016-07-12
Hi,

I posted this the other day in [http://askubuntu.com/questions/797344/intel-7260-bluetooth-device-usb-device-8087-07dc-at-100-usage](http://askubuntu.com/questions/797344/intel-7260-bluetooth-device-usb-device-8087-07dc-at-100-usage), but did not get a solution. So, I am posting it here as well, in case anyone can lend a hand.

My Intel 7260 bluetooth device is constanly draining battery. As per powertop:

> 13.9 W    100.0%                      Device         USB device: usb-device-8087-07dc

I have both bluetooth and NFC disabled in /etc/rc.local:

> rfkill block bluetooth
rfkill block nfc
/etc/init.d/bluetooth stop

And the suspend options are set as "Good" in powertop:

> /sys/bus/usb/devices/3-9/power/autosuspend = 2
/sys/bus/usb/devices/3-9/power/autosuspend_delay_ms = 2000
/sys/bus/usb/devices/3-9/power/control = auto

I am using Ubuntu 16.04, kernel 4.4.0-28.

This device did not use to use so much energy before. This behaviour has only started in the last one or two months.

I have tested with a live USB Ubuntu 16.04 image and the issue does not occur in there. So, it does not seem to be a hardware issue, but a software/configuration issue.

Also, I have another computer (with the same hardware), also with Ubuntu 16.04 and kernel 4.4.0-28, which is not showing this issue.

I have tried everything I can think of: disabling bluetooth in the bluetooth applet,  going back from GNOME 3.20 to GNOME 3.18 just in case, uninstalling the Nvidia proprietary driver, disabling the wifi, and upgrading to kernel 4.6.4.

How can I get this device to stop using power at 100%?

---

### Post by adlerhn on 2016-07-14
I have tested putting the SSD in another computer with the same specs where this issue does not occur, and the same behaviour appears in the other laptop. So, it's not a hardware issue.

---

### Post by adlerhn on 2016-07-16
```
echo "3-9" | sudo tee /sys/bus/usb/drivers/usb/unbind
``` does not stop the device from using energy as well.

---

### Post by jeremy31 on 2016-07-16
Been thinking about this too much, so let's try some simple
```
bluetoothctl
power off
exit
```

Hopefully that will be persistent with suspend and reboot

---

### Post by adlerhn on 2016-07-18
> **jeremy31 said:**
> Been thinking about this too much, so let's try some simple
```
bluetoothctl
power off
exit
```

Hopefully that will be persistent with suspend and reboot

Thanks for your response. I did that; no change. I have also ran the show sub-command:

> # show 5C:51:4F:D0:A5:24
Controller 5C:51:4F:D0:A5:24
	Name: Donald
	Alias: ChromeLinux_7441
	Class: 0x000000
	Powered: no
	Discoverable: no
	Pairable: yes
	UUID: Headset AG                (00001112-0000-1000-8000-00805f9b34fb)
	UUID: Generic Attribute Profile (00001801-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
	UUID: OBEX File Transfer        (00001106-0000-1000-8000-00805f9b34fb)
	UUID: Generic Access Profile    (00001800-0000-1000-8000-00805f9b34fb)
	UUID: OBEX Object Push          (00001105-0000-1000-8000-00805f9b34fb)
	UUID: PnP Information           (00001200-0000-1000-8000-00805f9b34fb)
	UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
	UUID: IrMC Sync                 (00001104-0000-1000-8000-00805f9b34fb)
	UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
	UUID: Audio Source              (0000110a-0000-1000-8000-00805f9b34fb)
	UUID: Vendor specific           (00005005-0000-1000-8000-0002ee000001)
	UUID: Message Notification Se.. (00001133-0000-1000-8000-00805f9b34fb)
	UUID: Phonebook Access Server   (0000112f-0000-1000-8000-00805f9b34fb)
	UUID: Message Access Server     (00001132-0000-1000-8000-00805f9b34fb)
	Modalias: usb:v1D6Bp0246d0525
	Discovering: no

The device seems to be powered off > Powered: no, but it still seems to be using a lot of energy as per powertop.

> Power est.              Usage       Events/s    Category       Description
  13.7 W    100.0%                      Device         USB device: usb-device-8087-07dc


---

### Post by adlerhn on 2016-07-19
After trying everything I've been able to think of, the only thing I have left to try is to format the "/" partition and reinstall everything from scratch. I will do that one of the next few days.

---

