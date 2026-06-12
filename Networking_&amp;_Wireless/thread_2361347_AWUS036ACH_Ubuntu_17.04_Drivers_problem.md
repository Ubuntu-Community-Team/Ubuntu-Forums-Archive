---
title: "AWUS036ACH Ubuntu 17.04 Drivers problem"
date: 2017-05-15
forum: Networking &amp; Wireless
---

### Post by lksjfnvljnfdv on 2017-05-15
Can someone please help me with getting the drivers and wifi working for this device please. Without getting it working on my Ubuntu 17.04 host I can't pass it to virtualbox.

When i do lsusb i get

```

$ lsusbBus 002 Device 004: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac WLAN Adapter

```

but it still cant recognise the device, i assume this is due to the drivers

sudo lshw show me

```

                 *-usb:2 UNCLAIMED
                      description: Generic USB device
                      product: 802.11n NIC
                      vendor: Realtek
                      physical id: 3
                      bus info: usb@2:1.3
                      version: 0.00
                      serial: 123456
                      capabilities: usb-2.00
                      configuration: maxpower=500mA speed=480Mbit/s

```

i have downloaded the drivers that are meant to be used and when i goto the directory and type make

i get the following

```



xxxx@Ubuntu:~/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902$ sudo make
[sudo] password for xxxx: 
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.10.0-20-generic/build M=/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902  modules
make[1]: Entering directory '/usr/src/linux-headers-4.10.0-20-generic'
  CC [M]  /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/core/rtw_cmd.o
In file included from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/include/drv_types.h:95:0,
                 from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/core/rtw_cmd.c:22:
/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/include/hal_com.h:384:13: error: ‘file_path’ redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^~~~~~~~~
In file included from ./include/linux/seq_file.h:10:0,
                 from ./include/linux/pinctrl/consumer.h:17,
                 from ./include/linux/pinctrl/devinfo.h:21,
                 from ./include/linux/device.h:24,
                 from ./include/linux/dmaengine.h:20,
                 from ./include/linux/netdevice.h:38,
                 from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/include/osdep_service_linux.h:35,
                 from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/include/osdep_service.h:41,
                 from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/include/drv_types.h:32,
                 from /home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/core/rtw_cmd.c:22:
./include/linux/fs.h:2680:14: note: previous declaration of ‘file_path’ was here
 extern char *file_path(struct file *, char *, int);
              ^~~~~~~~~
scripts/Makefile.build:294: recipe for target '/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/core/rtw_cmd.o' failed
make[2]: *** [/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902/core/rtw_cmd.o] Error 1
Makefile:1524: recipe for target '_module_/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902' failed
make[1]: *** [_module_/home/xxxx/Downloads/AWUS036AC_036EAC_ACH_linux_v4.3.8_12175.20140902/driver/rtl8812AU_linux_v4.3.8_12175.20140902] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-20-generic'
Makefile:1456: recipe for target 'modules' failed
make: *** [modules] Error 2


```

Can someone please let me know how i am able to get this working please?

---

### Post by lksjfnvljnfdv on 2017-05-15
i have managed to get this to work on kali linux rolling with a simple

sudo apt-get update
sudo apt-get install realtek-rtl88xxau-dkms

but cant get this working on ubuntu 17.04

---

### Post by jeremy31 on 2017-05-15
See if this works in Ubuntu 17.04
```
sudo apt-get update && sudo apt-get install rtl8812au-dkms
```

Then reboot

---

### Post by lksjfnvljnfdv on 2017-05-15
this worked. thank you very much, resolved

---

### Post by jeremy31 on 2017-05-16
Great use the thread tools menu near the top right of the page to mark as solved

---

### Post by lksjfnvljnfdv on 2017-05-27
it was working fine until today its stopped working again

sudo lshw show me it's unclaimed again?

```
*-usb:1 UNCLAIMED
                      description: Generic USB device
                      product: 802.11n NIC
                      vendor: Realtek
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 0.00
                      serial: 123456
                      capabilities: usb-2.00
                      configuration: maxpower=500mA speed=480Mbit/s
```

if i try to install the driver again i get the alert to say its already installed, any ideas?
```
rtl8812au-dkms is already the newest version (4.3.8.12175.20140902+dfsg-0ubuntu5).




```

---

### Post by lksjfnvljnfdv on 2017-05-28
any idea where i can start to fix this?

---

### Post by jeremy31 on 2017-05-28
Please post results for ```
modinfo 8812au | egrep 'filename|vermagic'
```

---

### Post by lksjfnvljnfdv on 2017-05-28
> **jeremy31 said:**
> Please post results for ```
modinfo 8812au | egrep 'filename|vermagic'
```

```

filename:       /lib/modules/4.10.0-21-generic/updates/dkms/8812au.ko

vermagic:       4.10.0-20-generic SMP mod_unload 



```

---

### Post by jeremy31 on 2017-05-28
There is an issue with the dkms.conf file but it can be fixed
```
sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

You will find a line starting with MAKE and it probably is
```
MAKE[0]="'make' all 
```
or similar, just make it
```
MAKE[0]="'make' all KVER=${kernelver}"
```
Save and exit gedit.  Then
```
sudo dkms remove -m rtl8812au -v 4.3.8.12175.20140902+dfsg -k $(uname -r)
```
It will remove the build for the current kernel, then reinstall with
```
sudo dkms install -m rtl8812au -v 4.3.8.12175.20140902+dfsg -k $(uname -r)
```

Reboot and with any luck it will work with the next kernel update

---

### Post by lksjfnvljnfdv on 2017-05-28
i had no wifi when i did the above, at all not even the onboard wifi on the laptop...

had to do 

[COLOR=#000000]sudo -H gedit /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.confand put it back to 

MAKE[0]="'make' all
rebooted but still noAWUS036ACH wifi on usb


[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by jeremy31 on 2017-05-28
It shouldn't have affected the onboard wifi at all, if nothing else try reinstalling the package again
```
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg
sudo modprobe 8812au
```
Reboot

---

### Post by lksjfnvljnfdv on 2017-05-28
**sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)**
```
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/source/dkms.conf: line 7: unexpected EOF while looking for matching `"'
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/source/dkms.conf: line 8: syntax error: unexpected end of file
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified for record #0.
dkms.conf: Error! Directive 'DEST_MODULE_LOCATION' does not begin with
'/kernel', '/updates', or '/extra' in record #0.
Error! Bad conf file.
File: 
does not represent a valid dkms.conf file.

```

**sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg**
```
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/source/dkms.conf: line 7: unexpected EOF while looking for matching `"'
/var/lib/dkms/rtl8812au/4.3.8.12175.20140902+dfsg/source/dkms.conf: line 8: syntax error: unexpected end of file
dkms.conf: Error! No 'DEST_MODULE_LOCATION' directive specified for record #0.
dkms.conf: Error! Directive 'DEST_MODULE_LOCATION' does not begin with
'/kernel', '/updates', or '/extra' in record #0.
Error! Bad conf file.
File: 
does not represent a valid dkms.conf file.

```


**sudo modprobe 8812au**
```
modprobe: ERROR: could not insert '8812au': Invalid argument


```

---

### Post by jeremy31 on 2017-05-28
Edit the dkms.conf file and add the " to the end of line 7 so it is
```
MAKE[0]="'make' all"
```
Then try the 
```
sudo dkms remove rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg
sudo modprobe 8812au
```

---

### Post by lksjfnvljnfdv on 2017-05-28
the " fixed to commands.]
it now shows the device but i cant seem to scan for or connect to any wifi using the usb device

---

### Post by jeremy31 on 2017-05-28
See the wireless script link in my signature and post results.  Also post results for ```
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by lksjfnvljnfdv on 2017-05-28
[https://pastebin.com/e4XTp2Hf](https://pastebin.com/e4XTp2Hf)

---

### Post by jeremy31 on 2017-05-28
Might as well try a reinstall as it might be the easiest fix ```
sudo apt-get install --reinstall rtl8812au-dkms
```

Reboot and if no improvement, see if disabling the wifi powersave fixes it
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by lksjfnvljnfdv on 2017-05-28
running
[COLOR=#000000]sudo apt-get install --reinstall rtl8812au-dkms[/COLOR]

the wireless device can now be seen, but when you try to look for any wireless networks, nothing shows up.

I can see the blue light flashing on the usb wireless device tho.

---

### Post by jeremy31 on 2017-05-28
Have you tried in terminal?
Unload driver for internal wifi
```
sudo modprobe -r wl
```
Then run a scan
```
iwlist scan
```

---

### Post by lksjfnvljnfdv on 2017-05-28
ok, so the AWUS036ACH is showing wireless networks now in the terminal.and the GUI.

I think it seems to be working now

---

### Post by jeremy31 on 2017-05-28
Can you post results for 
```
cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

You will likely have to do the same reinstall after the next kernel update unless I can see what is wrong in that file.  I have 16.04 installed and the change I recommended for dkms.conf was one I used to fix the same issue in 16.04- module being built using older kernel headers

---

### Post by lksjfnvljnfdv on 2017-05-29
[B]cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf

[/B]
```
PACKAGE_NAME="rtl8812au"
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"

```

---

### Post by jeremy31 on 2017-05-31
I think my fix is the correct one, see [https://askubuntu.com/a/832372/300665](https://askubuntu.com/a/832372/300665) and [https://github.com/Mange/rtl8192eu-linux-driver/commit/00293460e155e5c8c4514065a58f6ac9dccef9db](https://github.com/Mange/rtl8192eu-linux-driver/commit/00293460e155e5c8c4514065a58f6ac9dccef9db)

---

### Post by lksjfnvljnfdv on 2017-05-31
thank you very much for the help you have given, shame it cant be fixed in the main repo ..

---

