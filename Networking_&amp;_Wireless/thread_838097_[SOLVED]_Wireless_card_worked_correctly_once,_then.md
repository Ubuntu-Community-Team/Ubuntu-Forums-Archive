---
title: "[SOLVED] Wireless card worked correctly once, then stopped"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by sandyscott on 2008-06-23
Hi,

I've just put Ubuntu Hardy on a slightly older system of mine, which has got a D-Link DWL-G520+ (acx111) in it.

Immediately after installation, the card seemed to be working just about acceptably (had to enter the network key quite a few times before it accepted it, gave up trying to make DHCP work), but I did get it connected to our wireless network with a manual configuration, complete with internet access.

However, this morning, after the first reboot since installation, the card is no longer recognised properly by the network manager, and a little probing with lshw reveals that the driver hasn't been loaded:

```

*-network:1 UNCLAIMED
     description: Network Controller
     product: ACX 111 54Mbps Wireless Interface
     vendor: Texas Instruments
     physical id: 8
     bus info: pci@0000:00:08:0
     version: 00
     width: 32 bits
     clock 33MHz
     capabilities: pm cap_list
     configuration: latency=32

```

"pccardctl ident" outputs nothing

Can anybody help me with this?

Thanks

Sandy

---

### Post by chili555 on 2008-06-23
Does it work if you load the module manually:```
sudo modprobe acx
```If so, make it permanent with *sudo gedit /etc/modules* and add, on its own line:```
acx
```If not, it may be having trouble loading the firmware. Let's check with:```
sudo cat /var/log/messages | grep firmware
```

---

### Post by sandyscott on 2008-06-23
Thanks,

I tried the modprobe command, didn't appear to do anything as far as I could tell (no change in the network manager or the output of lshw).

However, checking the logs for firmware appears to have been a good idea, the firmware appears to have loaded correctly the first couple of times, but not after that, what do I do next?

```

Jun 23 01:18:30 beaker kernel: [   31.619591] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun 23 01:18:30 beaker kernel: [   31.619597] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun 23 01:18:30 beaker kernel: [   31.620793] acx: loading firmware for acx1111 chipset with radio ID 16
Jun 23 01:18:30 beaker kernel: [   37.771690] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Jun 23 01:36:33 beaker kernel: [   30.433570] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun 23 01:36:33 beaker kernel: [   30.433577] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun 23 01:36:33 beaker kernel: [   30.434774] acx: loading firmware for acx1111 chipset with radio ID 16
Jun 23 01:36:33 beaker kernel: [   36.709454] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
Jun 23 11:00:51 beaker kernel: [   29.038968] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun 23 11:00:51 beaker kernel: [   29.038975] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun 23 11:00:51 beaker kernel: [   29.040170] acx: loading firmware for acx1111 chipset with radio ID 16
Jun 23 11:00:51 beaker kernel: [   34.524863] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
Jun 23 11:00:51 beaker kernel: [   34.953711] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts
Jun 23 11:07:55 beaker kernel: [   29.687346] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun 23 11:07:55 beaker kernel: [   29.687352] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun 23 11:07:55 beaker kernel: [   29.688555] acx: loading firmware for acx1111 chipset with radio ID 16
Jun 23 11:07:55 beaker kernel: [   35.168702] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
Jun 23 11:07:55 beaker kernel: [   35.601494] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts
Jun 23 15:12:16 beaker kernel: [   29.601881] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun 23 15:12:16 beaker kernel: [   29.601887] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun 23 15:12:16 beaker kernel: [   29.603085] acx: loading firmware for acx1111 chipset with radio ID 16
Jun 23 15:12:16 beaker kernel: [   35.165870] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
Jun 23 15:12:16 beaker kernel: [   35.722762] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts

```

---

### Post by chili555 on 2008-06-23
> acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scriptsHmmm! It's on my machine:```
/lib/firmware/2.6.24-19-generic/acx/1.2.1.34/tiacx111
```Check yours with:```
sudo updatedb
locate acx/1.2.1.34/tiacx111
```*updatedb* will take a few moments; please be patient. It is possible that it later locates and loads. Please let us see:```
dmesg | grep acx
```Since this:```
Jun 23 15:12:16
```is the time after which it didn't work, you can pare down the copy and paste to that time and later.

---

### Post by sandyscott on 2008-06-23
When searching for the firmware, I get:
```

/lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111
/lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111c16
/lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111c17
/lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111r16
/lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111r17

```

and the dmesg command returns this after a reboot:

```

[   29.653148] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   29.653154] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   29.653344] acx: found ACX111-based wireless network card at 0000:00:08.0, irq:17, phymem1:0xE4800000, phymem2:0xE4000000, mem1:0xe0944000, mem1_size:8192, mem2:0xe0a00000, mem2_size:131072
[   29.654350] acx: loading firmware for acx1111 chipset with radio ID 16
[   34.955921] acx: firmware image 'acx/1.2.1.34/tiacx111c16' was not provided. Check your hotplug scripts
[   35.388594] acx: firmware image 'acx/1.2.1.34/tiacx111' was not provided. Check your hotplug scripts
[   35.388602] acx: reset_dev() FAILED
[   35.402077] acx_pci: probe of 0000:00:08.0 failed with error -5
[   35.402167] usbcore: registered new interface driver acx_usb


```

---

### Post by chili555 on 2008-06-24
When you installed, did you do a lot of updates? One of the updates was probably a new kernel. Please check with the terminal command *uname -r*. If you are running a kernel other than 2.6.24-16-generic, then you have the firmware for your old kernel but not the new one.

The firmware is included in *linux-restricted-modules-generic*, which you should install. 

We can cheat this up a bit by copying the firmware to the running kernel location:```
sudo cp /lib/firmware/2.6.24-16-generic/acx/1.2.1.34/tiacx111 /lib/firmware/`uname -r`/acx/1.2.1.34/tiacx111
```Those tickmarks around *uname -r* are found, on my keyboard, on the same key with ~. Reboot and see if it works.

Please let us know.

---

### Post by sandyscott on 2008-06-24
Thanks very much

Turns out I had started an update, but didn't have enough time to complete it, so that must have screwed up the version numbers.

In any case, your fix sorted it, and with the help of the manual configuration sticky I'm back up and running.

Thanks again

Sandy Scott

---

