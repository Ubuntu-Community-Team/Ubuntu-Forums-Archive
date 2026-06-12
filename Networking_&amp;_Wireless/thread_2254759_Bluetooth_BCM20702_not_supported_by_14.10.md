---
title: "Bluetooth BCM20702 not supported by 14.10"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by lisai9093 on 2014-11-29
Running lsusb gives me:
```
peter@Ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1532:0037 Razer USA, Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04ca:200b Lite-On Technology Corp. 
Bus 003 Device 002: ID 13d3:5163 IMC Networks 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The vendor/device ID of the bluetooth card should be 04ca:200b. Any idea how to install driver for this card?

p.s. This is BCM94352 combo card, which has BCM4352 + BCM20702. BCM4352 wifi card works perfectly fine.

---

### Post by jeremy31 on 2014-11-30
This might work ```
[COLOR=#333333][FONT=monospace]wget [/FONT][/COLOR][http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb](http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb)
```
```
[COLOR=#333333][FONT=monospace]dpkg-deb -x bt-bcm43142-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]onereic_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0.0+20111116som[/FONT][/COLOR][COLOR=#333333][FONT=monospace]erville2_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb bt-bcm43142
```
```
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]sudo cp bt-bcm43142/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]lib/firmware/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]BCM43142A0_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]001.001.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]011.0028.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0036.hcd /lib/firmware/
```
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```[/FONT][/COLOR]

---

### Post by lisai9093 on 2014-11-30
> **jeremy31 said:**
> This might work ```
[COLOR=#333333][FONT=monospace]wget [/FONT][/COLOR][http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb](http://wielki.tk/vostro/debs/bt-bcm43142-onereic_0.0+20111116somerville2_amd64.deb)
```
```
[COLOR=#333333][FONT=monospace]dpkg-deb -x bt-bcm43142-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]onereic_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0.0+20111116som[/FONT][/COLOR][COLOR=#333333][FONT=monospace]erville2_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb bt-bcm43142[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]
[/FONT][/COLOR]```
[COLOR=#333333][FONT=monospace]sudo cp bt-bcm43142/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]lib/firmware/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]BCM43142A0_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]001.001.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]011.0028.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0036.hcd /lib/firmware/[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]
```
sudo modprobe -r btusb
```
```
sudo modprobe btusb
```[/FONT][/COLOR]

Thanks for the help. Unfortunately it does not work for my card. I found another thread which give the general solution: [http://ubuntuforums.org/showthread.php?t=2231813](http://ubuntuforums.org/showthread.php?t=2231813)

I haven't tried the method yet. Will do it in my spare time later.

---

### Post by jeremy31 on 2014-11-30
> **lisai9093 said:**
> Thanks for the help. Unfortunately it does not work for my card. I found another thread which give the general solution: [http://ubuntuforums.org/showthread.php?t=2231813](http://ubuntuforums.org/showthread.php?t=2231813)

I haven't tried the method yet. Will do it in my spare time later.

It might take one more step for it to work ```
gksudo gedit /etc/modprobe.d/bcm43142.conf
```
The file should look like this ```
# Load firmware of BCM43142install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e1' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e3' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```

Change it to this and try ```
# Load firmware of BCM43142
install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '04ca 200b' > /sys/bus/usb/drivers/btusb/new_id && echo '04ca 200b' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```
Save and exit program, then ```
sudo modprobe -r btusb
``````
sudo modprobe btusb
```

---

### Post by lisai9093 on 2014-12-16
> **jeremy31 said:**
> It might take one more step for it to work ```
gksudo gedit /etc/modprobe.d/bcm43142.conf
```
The file should look like this ```
# Load firmware of BCM43142install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e1' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21e3' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```

Change it to this and try ```
# Load firmware of BCM43142
install btusb /sbin/modprobe --ignore-install btusb && echo '0a5c 21d3' > /sys/bus/usb/drivers/btusb/new_id && echo '0a5c 21d7' > /sys/bus/usb/drivers/btusb/new_id && echo '04ca 200b' > /sys/bus/usb/drivers/btusb/new_id && echo '04ca 200b' > /sys/bus/usb/drivers/btusb/new_id && hciconfig hci0 up && /usr/bin/brcm_patchram_plus_usb --patchram /lib/firmware/BCM43142A0_001.001.011.0028.0036.hcd hci0 &
```
Save and exit program, then ```
sudo modprobe -r btusb
``````
sudo modprobe btusb
```

I solved the problem by re-compile kernel with customized patch. But it won't stay after kernel update.

---

### Post by GlenH on 2014-12-17
I solved the same problem with my BCM4352 + BCM20702 with the method described here: [http://ubuntuforums.org/showthread.php?t=2197717&page=2](http://ubuntuforums.org/showthread.php?t=2197717&page=2)

---

### Post by lisai9093 on 2014-12-20
> **GlenH said:**
> I solved the same problem with my BCM4352 + BCM20702 with the method described here: [http://ubuntuforums.org/showthread.php?t=2197717&page=2](http://ubuntuforums.org/showthread.php?t=2197717&page=2)

Yes, I also solved by rebuilding kernel. But it is painful to do the process after kernel update.

---

