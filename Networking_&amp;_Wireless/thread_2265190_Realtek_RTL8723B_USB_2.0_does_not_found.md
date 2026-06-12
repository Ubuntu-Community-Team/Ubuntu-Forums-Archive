---
title: "Realtek RTL8723B USB 2.0 does not found"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by Teemu_Kuronen on 2015-02-13
I have a Cube i7 -tablet which is currently running on Ubuntu 14.10, but the device does not detect the wireless network card. I managed to find out (from the Windows 8.1 Device Control) that the actual module is Realtek RTL8723B Wireless LAN 802.11n USB 2.0 Network Adapter.

Does anyone know how I can get the tablet connected to my WLAN? I would be grateful for any helping advices... I'm a bit stuck with this issue right now.

---

### Post by kurt18947 on 2015-02-14
I don't have this adapter but this might provide a place to begin:

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by Teemu_Kuronen on 2015-02-16
I have read that thread, and it didn't help me with this issue... I was not able to compile the source of the driver; apparently Kernel has changed after the source of the driver has released, and it uses some outdated methods. I also managed to find new source for the adapter ([https://github.com/lwfinger](https://github.com/lwfinger)) while I was trying to find out the reason why the compiling always failed. I was able to compile the driver, but my adapter is not working...Currently I don't have the foggiest clue what to do next... Except to continue the Googling.

---

### Post by bench2004 on 2015-07-14
Hi,

I too own a Cube I7 and want to run linux on it. Any luck on your search so far?

Bench

---

### Post by Orditeck on 2015-08-18
Any luck with any driver? I'd like to use the built-in Wi-Fi (& bluetooth if possible!) of my Cube i7 Stylus with Ubuntu :)

I found this one, tested it and it doesn't work: [https://github.com/hadess/rtl8723bs](https://github.com/hadess/rtl8723bs)
Also found this: [https://github.com/psaintlaurent/amped-wireless-aca1-linux](https://github.com/psaintlaurent/amped-wireless-aca1-linux) there is a reference to rtl8723b here [https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h](https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h) but "make" returns lot of errors.

---

### Post by chili555 on 2015-08-18
Did you try it? It compiles perfectly on my 15.04 system but I haven't the device so I can test no further.

The usual process is:```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/hadess/rtl8723bs.git
make
sudo make install
sudo modprobe  r8723bs 
```

---

### Post by Orditeck on 2015-08-19
Yeah I tried hadess/rtl8723bs, it compiles just fine on 15.04. But Wi-Fi still doesn't work with this driver. Maybe it's because of the "s" at the end of RTL8723B. Mine is just RTL8723B (full name Realtek RTL8723B USB 2.0)

The one that I can't compile is this one: [https://github.com/psaintlaurent/amped-wireless-aca1-linux](https://github.com/psaintlaurent/amped-wireless-aca1-linux)
There is a reference about RTL8723B in this file so I thought it may work: [https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h](https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h)

---

### Post by chili555 on 2015-08-19
The file that you referenced says:> the device is really just generic hardware manufactured in taiwan using the [COLOR="#FF0000"]rtl8812au[/COLOR] chipset and re-branded as LoopComm, Edimax, Amped, etc.That's a very different thing than a rtl8723b or bs or b-whatever.

Before we proceed, let's identify the device in question:```
lsusb
uname -r
```Until we're sure we have the right driver for the right device, we're spinning our wheels.

---

### Post by jicha on 2015-09-02
Any news regarding the WiFi problem? Would be a workaround with USB WiFi adapter possible?

I would like to get this tablet but I want Ubuntu on it. Is at least the stylus working correctly? Did anyone try Krita on it?

Also there is a version called Cube i7 CM which should come with Ubuntu out of the box. Which BT/WiFi chipset it has?

---

### Post by bbaker6212 on 2015-09-08
Maybe this helps... [http://forum.xda-developers.com/windows-8-rt/general/cube-i7-stylus-t3151563/page74](http://forum.xda-developers.com/windows-8-rt/general/cube-i7-stylus-t3151563/page74)

**Linux on Cube i7 Stylus:**[INDENT]Cube refers to Lubuntu 15.04 as installed from a x64 live desktop iso with 3.19.0-15 kernel.
[LIST]
[*]You will need a USB keyboard, a USB hub and a spare USB stick 4GB or more formatted to FAT 32.
[*]Use "Startup Disk Creator" to make your USB stick bootable and load your ubuntu ISO (i use Lubuntu).
[/LIST]
[/INDENT]**Install from USB:**
[INDENT]Cube USB seems to fail config on bus powered device if your USB key and keyboard draws over 200mA, to resolve this:
[LIST]
[*] use powered hub, or
[*] manuall configure USB ie. "echo -n 1 /sys/bus/usb/devices/[usbdevnum]/bConfigurationValue" or
[*] hub that does not comply with USB spec may also work as it reports less current than it draws
[/LIST]
[/INDENT]**WiFi Driver:**[INDENT]Use driver for the RTL8723BU from lwfinger on Github ([https://github.com/lwfinger/rtl8723bu)and]("https://github.com/lwfinger/rtl8723bu%29and") compile it on a pc that has the same kernel as the lubuntu you are installing.
To compile this you will need Git and build-essential from the repo (sudo apt-get install git build-essential)
[LIST]
[*]Get the driver (git clone [https://github.com/lwfinger/rtl8723bu.git](https://github.com/lwfinger/rtl8723bu.git))
[*]Compile it (sudo make)
[*]copy the compiled 8723bu.ko file to the Cube and put it in /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless
[*]make it root owned (sudo chown root:root 8723bu.ko)
[*]run a "depmod -a" to refresh the module list
[*]then "modprobe 8723bu" to load the driver and your wifi should come up.
[/LIST]

As soon as you have WiFi running, update all your software (sudo apt-get update&& sudo apt-get upgrade)[/INDENT]**Sound card:**The sound card is an Intel PCH (Realtek ACL283 chip)
[LIST]
[*]Open Audacious and go into the settings
[*]Audio - ALSA Output settings
[*]Select ALC283 Analog (at bottom of list)
[*]Mixer Device - HDA Intel PCH
[/LIST]

Other software:
install "onboard" for an onscreen keyboard (sudo apt-get install onboard)
I found that i could not get the on-screen keyboard to work for logging into the cube.

---

### Post by jicha on 2015-10-27
I'm now running Kubuntu 15.10 on my Cube i7 Stylus. The WiFi driver compiled and installed without any problems. Everything works except of bluetooth. Do you have any idea where can I get bluetooth driver and how to install it?

---

### Post by chili555 on 2015-10-27
> **jicha said:**
> I'm now running Kubuntu 15.10 on my Cube i7 Stylus. The WiFi driver compiled and installed without any problems. Everything works except of bluetooth. Do you have any idea where can I get bluetooth driver and how to install it?Is the bluetooth a part of the Realtek USB dongle? If not, I suggest you start a new thread and include:```
lsusb
dmesg | grep -i blue
```

---

### Post by jicha on 2015-10-30
BT is part of the same chip AFAIK. I found this guide on compiling the driver:

> 
lwfinger on github has a bluetooth driver for the RTL8723BU (USB ID 0bda:b720)
[LIST]
[*]  Use the "new" branch of the RTL8723AU_BT repository ("git clone  https://github.com/lwfinger/rtl8723au_bt.git", then "git checkout new") 
[*] Compile (make) and install the driver ("sudo make install") 
[*] Enable the driver on the kernel (modprobe btusb) 
[*] Run the bluetooth manager 
[/LIST]


But it doesn't work for me in Kubuntu 15.10. I get these errors when running "make":

```
/home/kubuntu/driver/rtl8723au_bt/btusb.c: In function &#8216;hci_reassembly&#8217;:
/home/kubuntu/driver/rtl8723au_bt/btusb.c:376:15: error: &#8216;NUM_REASSEMBLY&#8217; undeclared (first use in this function)
      index >= NUM_REASSEMBLY)
               ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:376:15: note: each undeclared identifier is reported only once for each function it appears in
/home/kubuntu/driver/rtl8723au_bt/btusb.c:379:12: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
  skb = hdev->reassembly[index];
            ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:405:7: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
   hdev->reassembly[index] = skb;
       ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:427:10: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
      hdev->reassembly[index] = NULL;
          ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:440:10: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
      hdev->reassembly[index] = NULL;
          ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:453:10: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
      hdev->reassembly[index] = NULL;
          ^
/home/kubuntu/driver/rtl8723au_bt/btusb.c:466:8: error: &#8216;struct hci_dev&#8217; has no member named &#8216;reassembly&#8217;
    hdev->reassembly[index] = NULL;
        ^
scripts/Makefile.build:264: návod pro cíl &#8222;/home/kubuntu/driver/rtl8723au_bt/btusb.o&#8220; selhal
make[2]: *** [/home/kubuntu/driver/rtl8723au_bt/btusb.o] Chyba 1
Makefile:1398: návod pro cíl &#8222;_module_/home/kubuntu/driver/rtl8723au_bt&#8220; selhal
make[1]: *** [_module_/home/kubuntu/driver/rtl8723au_bt] Chyba 2
make[1]: Opou&#353;tí se adresá&#345; &#8222;/usr/src/linux-headers-4.2.0-16-generic&#8220;
Makefile:15: návod pro cíl &#8222;all&#8220; selhal
make: *** [all] Chyba 2
```

---

### Post by chili555 on 2015-10-30
> But it doesn't work for me in Kubuntu 15.10. I get these errors Part of the documentation at github says:> This repo is only for kernels older than 4.1.0. For kernel 4.2, use the btusb driver that is built in.Since you are using 4.2.0-16, I suggest you try the built in version:```
sudo modprobe btusb
```

---

### Post by jicha on 2015-10-31
The command "sudo modprobe btusb" doesn't return anything. But if I run BT settings in KDE, it says that no adapter is available.

What else should I try? Thank you.

---

### Post by chili555 on 2015-10-31
Let's see if the logs have any clues:```
dmesg | grep bt
```> The command "sudo modprobe btusb" doesn't return anything.Perfect! That means that the command was executed as requested and there are no warnings or errors to report.

---

### Post by jicha on 2015-10-31
This is the log:
```
[  224.280908] usbcore: registered new interface driver btusb
```

It seems like the driver is initialized correctly. But why KDE says there are no BT adapters?

---

### Post by jes-sorensen on 2016-01-05
> **Orditeck said:**
> Any luck with any driver? I'd like to use the built-in Wi-Fi (& bluetooth if possible!) of my Cube i7 Stylus with Ubuntu :)

I found this one, tested it and it doesn't work: [https://github.com/hadess/rtl8723bs](https://github.com/hadess/rtl8723bs)
Also found this: [https://github.com/psaintlaurent/amped-wireless-aca1-linux](https://github.com/psaintlaurent/amped-wireless-aca1-linux) there is a reference to rtl8723b here [https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h](https://github.com/psaintlaurent/amped-wireless-aca1-linux/blob/master/include/rtl8723b_hal.h) but "make" returns lot of errors.

You cannot use the 8723bs driver for the 8723bu - the 's' in the name indicates it is for SDIO versions of the chip.

Larry maintains a copy of the Realtek vendor driver as mentioned elsewhere in this thread. I am currently working on adding rtl8723bu support to the rtl8xxxu driver, but it's not quite ready yet and still sitting in my devel branch. It works using the USB dongle that I have, but I have only found one dongle with the rtl8723bu so far, so testing is limited.

Jes

---

### Post by jicha on 2016-04-27
@[**[COLOR=#000000]jes-sorensen[/COLOR]**]("http://ubuntuforums.org/member.php?u=2015626")> Do you have any progress with the integration of rtl8723bu? If you need some testing, I can try it on mine tablet (Cube i7 Stylus).

---

