---
title: "rtl8822be bluetooth issue"
date: 2018-01-29
forum: Networking &amp; Wireless
---

### Post by gus_zernial on 2018-01-29
I've installed Kubuntu 17.10 on my Asus ROG STRIX Z370-E mobo system. This mobo has a wifi/bluetooth combo chip, which I believe to be a realtek rtl8822be. The bluetooth/usb device exists, I can start the bluetooth service, but when I try to set the bluetooth device "up", it fails, as follows:

```
$ sudo hciconfig hci0 
hci0:   Type: Primary  Bus: USB
        RX bytes:1803 acl:0 sco:0 events:96 errors:0
        TX bytes:1125 acl:0 sco:0 commands:96 errors:0

```
```
$ sudo hciconfig hci0 up
Can't init device hci0: Invalid request code (56)
```

Also, blueman-applet does not find the device/adapter

Other Data .....

```
$ ps -ef | grep blue
root       761     1  0 12:28 ?        00:00:00 /usr/lib/bluetooth/bluetoothd
rbroman   1179  1005  0 12:28 ?        00:00:00 /usr/bin/python3 /usr/bin/blueman-applet
rbroman   1250     1  0 12:28 ?        00:00:00 /usr/lib/bluetooth/obexd
```

```
$ lsmod | grep rtl
rtl8822be              73728  0
halmac                135168  1 rtl8822be
phydm_mod             401408  1 rtl8822be
btcoexist             184320  1 rtl8822be
rtl_pci                32768  1 rtl8822be
rtlwifi               118784  5 phydm_mod,halmac,rtl_pci,btcoexist,rtl8822be
mac80211              778240  2 rtl_pci,rtlwifi
cfg80211              610304  2 mac80211,rtlwifi
btrtl                  16384  1 btusb
bluetooth             540672  14 btrtl,hci_uart,btintel,btqca,bnep,btbcm,btusb

```
```
$ lsusb -v

bla, bla, bla, .....

Bus 001 Device 002: ID 0b05:185c ASUSTek Computer, Inc. 
Device Descriptor:Data ....

  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0b05 ASUSTek Computer, Inc.
  idProduct          0x185c 
  bcdDevice            1.10
  iManufacturer           1 Realtek 
  iProduct                2 Bluetooth Radio 
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1.
```

Bla, bla, bla ........

---

### Post by praseodym on 2018-01-30
[https://ubuntuforums.org/showthread.php?t=2364383&page=3&p=13721914#post13721914](https://ubuntuforums.org/showthread.php?t=2364383&page=3&p=13721914#post13721914)

Maybe this helps with kernel 4.14?!

---

### Post by gus_zernial on 2018-02-03
Per praseodym's suggestion, I followed the link above, installed kernel 4.15.0-041500-generic, and put rtl8822befw.bin in /lib/firmware/rtfwifi. Still no joy. The relevant lines from syslog during boot are below, followed by last part of btmon output when executing "sudo hciconfig hci0 up". Relevant output of btmon seems to be "invalid packet size". How to fix ?????

```
Feb  3 08:50:25 Jboat17 kernel: [    2.759393] r8822be: module is from the staging directory, the quality is unknown, you have been warned.
Feb  3 08:50:25 Jboat17 kernel: [    2.760312] r8822be 0000:03:00.0: enabling device (0000 -> 0003)
Feb  3 08:50:25 Jboat17 kernel: [    2.772600] r8822be: Using firmware rtlwifi/rtl8822befw.bin
Feb  3 08:50:25 Jboat17 kernel: [    2.779180] r8822be: rtlwifi: wireless switch is on
Feb  3 08:50:25 Jboat17 kernel: [    2.780382] r8822be 0000:03:00.0 wlp3s0: renamed from wlan0
Feb  3 08:50:25 Jboat17 NetworkManager[773]: <info>  [1517676625.8989] rfkill1: found WiFi radio killswitch (at invalid packet size/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/ieee80211/phy0/rfkill1) (driver r8822be)invalid packet size
```

```
$ sudo hciconfig hci0 up

.
.
.       Status: Success (0x00)
        TX power: 0 dBm
< HCI Command: LE Read White List Size (0x08|0x000f) plen 0                          #55 [hci0] 90.813520
> HCI Event: Command Complete (0x0e) plen 5                                          #56 [hci0] 90.814482
      LE Read White List Size (0x08|0x000f) ncmd 2
        Status: Success (0x00)
        Size: 32
< HCI Command: LE Clear White List (0x08|0x0010) plen 0                              #57 [hci0] 90.814517
> HCI Event: Command Complete (0x0e) plen 4                                          #58 [hci0] 90.815482
      LE Clear White List (0x08|0x0010) ncmd 2
        Status: Success (0x00)
< HCI Command: Read Local Extended Features (0x04|0x0004) plen 1                     #59 [hci0] 90.815514
        Page: 2
> HCI Event: Command Complete (0x0e) plen 14                                         #60 [hci0] 90.816489
      Read Local Extended Features (0x04|0x0004) ncmd 2
        Status: Success (0x00)
        Page: 2/2
        Features: 0x5f 0x03 0x00 0x00 0x00 0x00 0x00 0x00
          Connectionless Slave Broadcast - Master
          Connectionless Slave Broadcast - Slave
          Synchronization Train
          Synchronization Scan
          Inquiry Response Notification Event
          Coarse Clock Adjustment
          Secure Connections (Controller Support)
          Ping
< HCI Command: Delete Stored Link Key (0x03|0x0012) plen 7                           #61 [hci0] 90.816526
        Address: 00:00:00:00:00:00 (OUI 00-00-00)
        Delete all: 0x01
> HCI Event: Command Complete (0x0e) plen 6                                          #62 [hci0] 90.818483
      Delete Stored Link Key (0x03|0x0012) ncmd 2
        Status: Success (0x00)
        Num keys: 0
< HCI Command: Read Synchronization Train Parameters (0x03|0x0077) plen 0            #63 [hci0] 90.818517
> HCI Event: Command Complete (0x0e) plen 9                                          #64 [hci0] 90.819485
      Read Synchronization Train Parameters (0x03|0x0077) ncmd 2
        invalid packet size
        01 08 69 11 80 01                                ..i...          
= Close Index: 64:6E:69:8F:25:A4                                                         [hci0] 90.819519
@ RAW Close: hciconfig
```

---

### Post by praseodym on 2018-02-03
What about 4.14 as suggested? Thats the stable one

---

### Post by gus_zernial on 2018-02-09
> **praseodym said:**
> What about 4.14 as suggested? Thats the stable one

I'm on kernel 4.14.15, problem continues:

Wifi works, and in my dmesg output I see ....

```
$ dmesg | egrep -i '8822'
.....................
[    3.870314] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    3.876041] r8822be: rtlwifi: wireless switch is on
[    3.877704] Modules linked in: rtlwifi(OE+) ...............
```

What I do *not* see in dmesg is something like this - taken from another post ....

```
38.862067] usb 1-5: Product: Bluetooth Radio 
[   39.028085] Bluetooth: hci0: rtl: examining hci_ver=07 hci_rev=000b lmp_ver=07 lmp_subver=8822
[   39.028087] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_config.bin
[   39.028144] Bluetooth: hci0: rtl: loading rtl_bt/rtl8822b_fw.bin
[   39.029844] Bluetooth: hci0: rom_version status=0 version=2
```

The rtl8822 chip provides both wifii and bluetooth support, and I think that linux support for the bluetooth side happened or is happening after the linux support for the wifi side. The bluetooth firmware files rtl_bt/rtl8822b_config.bin and rtl_bt/rtl8822b_fw.bin are installed on my system. But I don't think they're loading.

At this point I'm in over my head. Modules btusb and btrtl are loaded on my system, and I suspect that one of them is supposed to cause the two firmware bin files above to load, but I'm not sure. If so, kernel 4.14.15 may not have a version of those modules which supports the rtl8822be bluetooth side. I'd appreciate it if someone can confirm or deny my theory, and/or provide recommendations to fix things.

---

### Post by gus_zernial on 2018-02-12
I finally got Bluetooth working for my rtl8822be wifi/bluetooth chip. As others have noted, the chip is supported in kernel 4.14 and beyond, but so far only for the wifi function of the chip. For the bluetooth function there's a patch for the btusb module, to add support for the chip, see: 

[https://gist.github.com/hwchong/8738e100ec4e140bae2cac2894c29d65](https://gist.github.com/hwchong/8738e100ec4e140bae2cac2894c29d65)

You have to download the kernel 4.14 source, apply the patch to /drivers/bluetooth/btusb.c in that source, recompile that module to generate btusb.ko, and replace that module in /lib/modules/....your kernel ID...../kernel/drivers/bluetooth/. There's instructions elsewhere as to how to compile and replace a single module in the kernel.

In addition, I had to add the line "Enable=Source,Sink,Media,Socket" under [General] in /etc/bluetooth/main.conf to get my kubuntu box to play audio through my bluetooth speakers.

---

### Post by jeremy31 on 2018-02-13
Actually you could do the same in 4.4, for the wireless
```
sudo apt-get install git dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Then for bluetooth you can clone the patched 4.4 bluetooth source code
```
git clone https://github.com/jeremyb31/bluetooth-4.4.git
sudo dkms add ./bluetooth-4.4
sudo dkms install bluetooth-4.4/0.1
```
Reboot

---

### Post by praseodym on 2018-03-05
Jeremy: Do you know if this bluetooth manual works for rtl8723de chipsets, too? Mostly, this error occurs:

```
[ 1182.222843] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
```
The file is missing anywhere

---

### Post by jeremy31 on 2018-03-05
Hi, that file doesn't exist for all Realtek bluetooth chipsets, for now all we have is at [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_bt](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/rtl_bt)
That bluetooth should work without the file but if it doesn't, it might be worth filing a bug report about

---

### Post by ttoine on 2018-04-19
hello, ok for the files, but do we put them so it works ?

---

### Post by aznxluvlyguy4u on 2018-08-15
> **gus_zernial said:**
> I finally got Bluetooth working for my rtl8822be wifi/bluetooth chip. As others have noted, the chip is supported in kernel 4.14 and beyond, but so far only for the wifi function of the chip. For the bluetooth function there's a patch for the btusb module, to add support for the chip, see: 

[https://gist.github.com/hwchong/8738e100ec4e140bae2cac2894c29d65](https://gist.github.com/hwchong/8738e100ec4e140bae2cac2894c29d65)

You have to download the kernel 4.14 source, apply the patch to /drivers/bluetooth/btusb.c in that source, recompile that module to generate btusb.ko, and replace that module in /lib/modules/....your kernel ID...../kernel/drivers/bluetooth/. There's instructions elsewhere as to how to compile and replace a single module in the kernel.

In addition, I had to add the line "Enable=Source,Sink,Media,Socket" under [General] in /etc/bluetooth/main.conf to get my kubuntu box to play audio through my bluetooth speakers.

Hi I'm having the exact same problem, I have rtl8822be chip, got wireless working but not bluetooth. Can you please explain step by step how you managed to fix this problem? As your description is a bit vague, thanks in advance!

---

### Post by aznxluvlyguy4u on 2018-09-04
> **jeremy31 said:**
> Actually you could do the same in 4.4, for the wireless
```
sudo apt-get install git dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Then for bluetooth you can clone the patched 4.4 bluetooth source code
```
git clone https://github.com/jeremyb31/bluetooth-4.4.git
sudo dkms add ./bluetooth-4.4
sudo dkms install bluetooth-4.4/0.1
```
Reboot

Hi, I still haven't got it working with the exact same problem on kernel 4.15..

I followed all your steps and still got this error message when:

> 
sudo dkms install bluetooth-4.4/0.1


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....(bad exit status: 2)
make KERNELRELEASE=4.15.0-041500-generic -C /lib/modules/4.15.0-041500-generic/build M=/var/lib/dkms/bluetooth-4.4/0.1/build....(bad exit status: 2)
ERROR (dkms apport): binary package for bluetooth-4.4: 0.1 not found
Error! Bad return status for module build on kernel: 4.15.0-041500-generic (x86_64)
Consult /var/lib/dkms/bluetooth-4.4/0.1/build/make.log for more information.

I'm starting to pull my hairs out... please help? anyone?


FINALLY, apparently this issue has been solved by Jeremy in another post:
[https://ubuntuforums.org/showthread.php?t=2394125&p=13775193#post13775193](https://ubuntuforums.org/showthread.php?t=2394125&p=13775193#post13775193)

thanks!!!

---

### Post by shengyangwei on 2018-10-28
> **aznxluvlyguy4u said:**
> Hi I'm having the exact same problem, I have rtl8822be chip, got wireless working but not bluetooth. Can you please explain step by step how you managed to fix this problem? As your description is a bit vague, thanks in advance!


I got the same bluetooth issue and fixed by following the steps in [https://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module](https://askubuntu.com/questions/515407/how-recipe-to-build-only-one-kernel-module), just replace the scsi/mcsas in his case by bluetooth/btusb, also, make sure you have download matched kernel source.

---

