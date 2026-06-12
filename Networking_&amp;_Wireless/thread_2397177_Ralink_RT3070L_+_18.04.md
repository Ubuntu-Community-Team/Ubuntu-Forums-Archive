---
title: "Ralink RT3070L + 18.04"
date: 2018-07-26
forum: Networking &amp; Wireless
---

### Post by Mrhihat on 2018-07-26
The short story.

I am pretty damn green when it comes to using the terminal and with only the most basic compiling skills.
I am trying to get a directed wifi antenna to work on my asus machine running lubuntu 18.04. 

I have been looking around for a solution but it either does not work or simply is beyond what I can follow.
So I was hoping someone in here could assist me and have the patience to attempt to walk me through it. 

When I try to compile the 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.bz2  I eventually run into an error when I run Sudo Make: 

cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/dman/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o' failed
make[2]: *** [/home/dman/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux/../../sta/sta_cfg.o] Error 1
Makefile:1552: recipe for target '_module_/home/dman/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux' failed
make[1]: *** [_module_/home/dman/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-23-generic'
Makefile:356: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2


Anyone able and willing to give me a few pointers?

---

### Post by chili555 on 2018-07-26
> Anyone able and willing to give me a few pointers?I'm happy to do so. First, please check here:> [COLOR="#FF0000"]2011[/COLOR]_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPOYou will not solve any problem that you have by installing and older, less-developed driver, even if you could compile it, which you can't as there have been many changes in Ubuntu and the Linux kernel since 2011, which is 100 years ago in Linux years!

I doubt that you lack a driver for your device, You can check from the terminal:```
lsmod | grep rt2
```Please tell us what your wireless problem reaallllly is. Please include the results of:```
lsusb
rfkill list all
dmesg | grep rt2
```

---

### Post by Mrhihat on 2018-07-26
Hello.

Thank you for taking the time.

***lsmod | grep rt2*** gives me no info in return

***lsusb*** returns the following:

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b404 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***rfkill list all  ***returns:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***dmesg | grep rt2 ***returns nothing.


I was given a link to a 2012 drive here [https://askubuntu.com/questions/1059321/trying-to-get-my-ralink-rt3070l-to-work-on-my-18-04](https://askubuntu.com/questions/1059321/trying-to-get-my-ralink-rt3070l-to-work-on-my-18-04)
but it seems to fail in the same way as the 2011 drive.

---

### Post by chili555 on 2018-07-26
Let's have a look at:```
lspci -nnk | grep 0280 -A3
```

---

### Post by Mrhihat on 2018-07-26
*lspci -nnk | grep 0280 -A3*  returns:

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave RTL8821AE 802.11ac PCIe Wireless Network Adapter [1a3b:2161]
	Kernel driver in use: rtl8821ae
	Kernel modules: rtl8821ae, wl

---

### Post by chili555 on 2018-07-26
We see no Ralink device. Your internal device, a Realtek, appears to have a working driver (or two!). Where is the Ralink?

We are confused.

---

### Post by Mrhihat on 2018-07-26
Well, that is another thing, It seems it does not register when I plug it in the usb port. (It is a external directed wifi antenna)
I was thinking it might pop up if I install the driver, but then again...

---

### Post by chili555 on 2018-07-26
Is the result of:```
lsusb
```...the same with it plugged in as with it unplugged? If not, show us the difference. If it is the same, show us:```
tail -f /var/log/syslog
```...as you plug it in. Get out of 'tail' with Ctrl+c.

What do you hope to do that the internal wireless can't do better?

---

### Post by Mrhihat on 2018-07-26
tail -f /var/log/syslog

Jul 26 21:22:48 dman-X551MA kernel: [ 9470.182193] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 26 21:22:49 dman-X551MA kernel: [ 9471.154533] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 26 21:22:49 dman-X551MA kernel: [ 9471.154754] usb usb1-port1: attempt power cycle
Jul 26 21:22:51 dman-X551MA kernel: [ 9472.439100] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 26 21:22:52 dman-X551MA kernel: [ 9473.407525] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 26 21:22:52 dman-X551MA kernel: [ 9473.407746] usb usb1-port1: unable to enumerate USB device
tail -f /var/log/syslog

the reason I want the antenna to work is to get wifi from my wife's grandma across the street. I am in a mountain village on vacation and surfing on mobile is not feasible for moving large amounts of data.

---

### Post by chili555 on 2018-07-26
> Jul 26 21:22:49 dman-X551MA kernel: [ 9471.154754] usb usb1-port1: attempt power cycle
Jul 26 21:22:51 dman-X551MA kernel: [ 9472.439100] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?It looks as if the device is defective or the USB port is defective. Is the result the same with all the USB ports on the computer?

If the result is the same, I think the Ralink USB is defective.

---

### Post by Mrhihat on 2018-07-26
Other usb units works on all ports.
I will return the unit to the store tomorrow, see if it works on another computer (ehrmm.. windows machine).
I will report back when the results are in.

Thanks for all the help this far!

---

### Post by Mrhihat on 2018-07-27
update after visit to electronics shop:

The unit works fine (on a windows machine). As far as I understand it, you need to install the driver for the usb to recognize something useful at all is plugged into the port.

---

### Post by chili555 on 2018-07-27
If the device won't identify itself in Linux, I'm not sure what driver to load. The name, RT3070L, suggests the driver rt2800usb. Try loading it:```
sudo modprobe rt2800usb
```Now insert the device and watch the log:```
tail -f /var/log/syslog
```Any change?

If not, I haven't any other suggestion aside from getting a different device.

---

### Post by Mrhihat on 2018-07-27
sudo modprobe rt2800usb resulting in asking for pw, like all sudo commands, but it did not return any messages (normal perhaps?)

tail -f /var/log/syslog returned the same old (or at least similar answer)

dman@dman-X551MA:~$ tail -f /var/log/syslog
Jul 27 17:57:20 dman-X551MA wpa_supplicant[483]: WEXT: Could not set interface 'wlx40a5efda291b' UP
Jul 27 17:57:20 dman-X551MA upowerd[794]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0
Jul 27 17:57:20 dman-X551MA wpa_supplicant[483]: wlx40a5efda291b: Failed to initialize driver interface
Jul 27 17:57:20 dman-X551MA upowerd[794]: unhandled action 'unbind' on /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1
Jul 27 17:57:21 dman-X551MA kernel: [  126.208549] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 27 17:57:22 dman-X551MA kernel: [  127.176527] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 27 17:57:22 dman-X551MA kernel: [  127.176748] usb usb1-port1: attempt power cycle
Jul 27 17:57:23 dman-X551MA kernel: [  128.460552] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 27 17:57:24 dman-X551MA kernel: [  129.428524] usb usb1-port1: Cannot enable. Maybe the USB cable is bad?
Jul 27 17:57:24 dman-X551MA kernel: [  129.428660] usb usb1-port1: unable to enumerate USB device

Weird that there just is not a simple driver available for this chipset. Apparently really simple to install and run on windows.
Is trying to install and run it on wine an option?

---

