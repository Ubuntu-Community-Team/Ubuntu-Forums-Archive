---
title: "Problems Seeing Linksys AC1200 Wi-Fi Adapter"
date: 2022-10-24
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2022-10-24
I just upgraded to Ubuntu 22.04.1 LTS and I cannot see my wi-fi in Settings.  I ran a sudo lshw -C network and got this 

```
sudo lshw -C network  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 0c
       serial: 64:00:6a:2e:06:88
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-52-generic duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.1.186 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff



```

My problem is I cannot see it in Settings so I reinstalled network-manager and was told I already had the newset version.  Any idea how to reinstall the drivers and how to get the wi-fi to show in settings?

---

### Post by mIk3_08 on 2022-10-25
Please run the command in your terminal and paste the results here in thread wrap with code. Regards and cheers.
```
hostnamectl
```

---

### Post by shane_faulkinbury2 on 2022-10-25
Here you[ATTACH=CONFIG]291180[/ATTACH] go.

---

### Post by #&amp;thj^% on 2022-10-25
shane will you also post this:
```
rfkill list all
```

---

### Post by shane_faulkinbury2 on 2022-10-25
[ATTACH=CONFIG]291181[/ATTACH]

---

### Post by shane_faulkinbury2 on 2022-10-25
[ATTACH=CONFIG]291182[/ATTACH]
Is there anyway to turn WiFi on?

---

### Post by #&amp;thj^% on 2022-10-25
If your machine had a WiFi device it could use, then yes.
It's hard to turn something that isn't there>> on.
Did you upgrade to 22.04 or was it a clean install?

---

### Post by shane_faulkinbury2 on 2022-10-25
Clean install after running dBan..

---

### Post by mIk3_08 on 2022-10-26
> **1fallen said:**
> It's hard to turn something that isn't there>> on.

I agree with 1fallen.

> **shane_faulkinbury2 said:**
> 
Is there anyway to turn WiFi on?

Please run the command below and paste the results here and thread. Regards and cheers
```
lsusb
``` 
I  think you need to reinstall your Linksys AC1200 Wi-Fi Adapter driver. I don't  know if their are available Linux driver for this. Always remember that Linux is not MS Windows of what you think. Regards and cheers.

---

### Post by shane_faulkinbury2 on 2022-10-26
```
$ lsusb[
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 046d:c315 Logitech, Inc. Classic Keyboard 200
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 13b1:0045 Linksys WUSB6300 V2
Bus 003 De[CODE]
```vice 002: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/CODE]

---

### Post by shane_faulkinbury2 on 2022-10-26
Device 5

---

### Post by shane_faulkinbury2 on 2022-10-26
If I run this will it work?```
 sudo apt-get install git dkms
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
cd rtl8812AU_8821AU_linux
make
sudo make install 
```

---

### Post by shane_faulkinbury2 on 2022-10-26
I went ahead and ran that I didn't get all the way done.

[CODE]# makemake ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/5.15.0-52-generic/build M=/home/oem/rtl8812AU_8821AU_linux  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-52-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: gcc (Ubuntu 11.2.0-19ubuntu1) 11.2.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_cmd.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_security.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_debug.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_io.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_ioctl_query.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_ioctl_set.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_ieee80211.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_mlme.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_mlme_ext.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_wlan_util.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_vht.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_pwrctrl.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_rf.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_recv.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_sta_mgt.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_ap.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_xmit.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_p2p.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_tdls.o
  CC [M]  /home/oem/rtl8812AU_8821AU_linux/core/rtw_br_ext.o
/home/oem/rtl8812AU_8821AU_linux/core/rtw_br_ext.c:25:10: fatal error: net/ipx.h: No such file or directory
   25 | #include <net/ipx.h>
      |          ^~~~~~~~~~~
compilation terminated.
make[2]: *** [scripts/Makefile.build:297: /home/oem/rtl8812AU_8821AU_linux/core/rtw_br_ext.o] Error 1
make[1]: *** [Makefile:1900: /home/oem/rtl8812AU_8821AU_linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-52-generic'
make: *** [Makefile:1622: modules] Error 2
root@oem-OptiPlex-3020:/home/oem/rtl8812AU_8821AU_linux# sudo make install
install -p -m 644 rtl8812au.ko  /lib/modules/5.15.0-52-generic/kernel/drivers/net/wireless/
install: cannot stat 'rtl8812au.ko': No such file or directory
make: *** [Makefile:1628: install] Error 1
root@oem-OptiPlex-3020:/home/oem/rtl8812AU_8821AU_linux# 


[CODE]

---

### Post by #&amp;thj^% on 2022-10-26
I prefer chili555's way IE:
```
sudo apt update
sudo apt install git dkms
git clone https://github.com/morrownr/8812au-20210629.git
cd 8812au
sudo ./install-driver.sh
```
After a reboot you "should have wifi"

---

### Post by shane_faulkinbury2 on 2022-10-26
```
# git clone https://github.com/morrownr/8812au-20210629.gitCloning into '8812au-20210629'...
remote: Enumerating objects: 1254, done.
remote: Counting objects: 100% (144/144), done.
remote: Compressing objects: 100% (78/78), done.
remote: Total 1254 (delta 92), reused 98 (delta 65), pack-reused 1110
Receiving objects: 100% (1254/1254), 3.46 MiB | 13.66 MiB/s, done.
Resolving deltas: 100% (631/631), done.
root@oem-OptiPlex-3020:/home/oem# cd 8812au
bash: cd: 8812au: No such file or directory
root@oem-OptiPlex-3020:/home/oem# sudo ./install-driver.sh
sudo: ./install-driver.sh: command not found



```

---

### Post by shane_faulkinbury2 on 2022-10-26
Figured it out.  Rebooting!

[CODE]fatal: destination path '8812au-20210629' already exists and is not an empty directory.root@oem-OptiPlex-3020:/home/oem# cd 8812au
bash: cd: 8812au: No such file or directory
root@oem-OptiPlex-3020:/home/oem# cd 8812au-20210629
root@oem-OptiPlex-3020:/home/oem/8812au-20210629# sudo ./install-driver.sh
Running install-driver.sh version 20221018
5.15.0-52-generic
x86_64
Installing 8812au.conf to: /etc/modprobe.d
The dkms installation routines are in use.
Copying source files to: /usr/src/rtl8812au-5.13.6
Creating symlink /var/lib/dkms/rtl8812au/5.13.6/source -> /usr/src/rtl8812au-5.13.6


Kernel preparation unnecessary for this kernel. Skipping...


Building module:
cleaning build area...
'make' -j4 KVER=5.15.0-52-generic KSRC=/lib/modules/5.15.0-52-generic/build................
Signing module:
Generating a new Secure Boot signing key:
Can't load /var/lib/shim-signed/mok/.rnd into RNG
40274C9FAC7F0000:error:12000079:random number generator:RAND_load_file:Cannot open file:../crypto/rand/randfile.c:106:Filename=/var/lib/shim-signed/mok/.rnd
.+......+...+.....+...+...+......+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*........+.......+.........+...+..+......+...+.......+..+.+............+..+.+......+.....+....+..+...+.+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*..+..+.........+...............+.+...+........+...+....+......+.....+.........+.+......+...+...............+.....+...+...+...............................+......+.....+....+.....+....+...........+....+......+.........+.....+.+...+........+...+.........+.............+...+............+.....+..........+.....+.......+..+.+..+.....................+.......+..+.+..+..........+..+............+...+.+..+.......+.................+.............+............+.....+....+..+.......+........+....+...+...+..+............+...+.+.....+....+...+........+......+.............+.....+............+...+..........+.....+......+.+.....+.........+.+......+.....+....+.....+...+..........+..+.........+............+............+.......+...+............+.....+..................+.+..............+......+.+.....+......+............+...+.......+.....+......+.+......+...+......+...+...+...............+..+..........+...............+..+.+........+......+...+.+..+.......+..+......+...+..........+...........+.+........+.......+..+......+.+..............+....+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
..+...........+......+.........+....+.........+...+..+.+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+.....+......+.+...+.....+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+...+...+.....+.......+........+...+.......+.........+...+.....+...+...+....+...........+....+..+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
-----
 - /var/lib/dkms/rtl8812au/5.13.6/5.15.0-52-generic/x86_64/module/8812au.ko
EFI variables are not supported on this system
/sys/firmware/efi/efivars not found, aborting.
cleaning build area...


8812au.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-52-generic/updates/dkms/


depmod.......
The driver was installed successfully.
Do you want to edit the driver options file now? [y/N] n
Do you want to reboot now? (recommended) [y/N] N
root@oem-OptiPlex-3020:/home/oem/8812au-20210629# 
[CODE]

---

### Post by shane_faulkinbury2 on 2022-10-26
Still no WI-FI!

---

### Post by jeremy31 on 2022-10-26
```
git clone https://github.com/morrownr/88x2bu-20210702.git
cd 88x2bu-20210702
sudo ./install-driver.sh
```
Reboot if no issues

---

### Post by shane_faulkinbury2 on 2022-10-26
I said no, but I actually did reboot and it's not working.

---

### Post by jeremy31 on 2022-10-26
Post results from terminal for ```
dkms status
```

---

### Post by shane_faulkinbury2 on 2022-10-26
That says it's installed, but my system still can't see it.

```
 dkms statusrtl8812au/5.13.6, 5.15.0-52-generic, x86_64: installed



```

---

### Post by morrownr on 2022-10-26
.I took a look at the device ID and confirmed the chipset is a rtl8812bu:

[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)

Going to the url is better than typing a few lines because at the site you will get a LOT of information that will help you understand what you are doing. We don't know what you have installed at this point so you might want to start with:

$ sudo ./remove-driver.sh

... per instructions at the above url. You can then start the installation process over and do a little reading. Let us know what happens.

FYI: The Main Menu for the site is shown below and it gives a lot of information about usb wifi adapters and hosts 5 Realtek drivers.

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Nick

---

### Post by shane_faulkinbury2 on 2022-10-27
It's working good this morning guys.  I guess I should have listened when they said sometimes it takes a couple of reboots.  I'll mark this as solved when I move the computer upstairs and it works!

---

### Post by #&amp;thj^% on 2022-10-27
I trusted that shane_faulkinbury2 had the right driver for his device.(lesson learnt)
All is good though, and sometimes it just needs nudge:
```
sudo modprobe 88x2bu
```
Mine without turning on WiFi
```
me on Thu Oct 27 at 09:47 AM in ~ branch: (HEAD) 
>>  lsmod | grep 88x2bu && lsmod |grep iwlwifi 


```
Now turned on:(inxi added this time for my device:
```
lsmod | grep 88x2bu && lsmod |grep iwlwifi 
88x2bu               4579328  0
cfg80211             1105920  4 iwlmvm,88x2bu,iwlwifi,mac80211
usbcore               380928  15 xhci_hcd,usbnet,snd_usb_audio,usbhid,snd_usbmidi_lib,88x2bu,cdc_mbim,cdc_ncm,usb_storage,cdc_wdm,uvcvideo,btusb,xhci_pci,cdc_ether,uas
iwlwifi               413696  1 iwlmvm
cfg80211             1105920  4 iwlmvm,88x2bu,iwlwifi,mac80211


me on Thu Oct 27 at 09:53 AM in ~ branch: (HEAD) 
>> inxi -SN --no-host
System:
  Kernel: 6.0.3-1-default arch: x86_64 bits: 64 Desktop: Xfce v: 4.16.1
    Distro: openSUSE Tumbleweed 20221026
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: Intel Wi-Fi 6 AX200 driver: iwlwifi
  Device-3: Realtek RTL88x2bu [AC1200 Techkey] type: USB driver: rtl88x2bu

```)

---

### Post by mIk3_08 on 2022-10-27
> **shane_faulkinbury2 said:**
> It's working good this morning guys.  I guess I should have listened when they said sometimes it takes a couple of reboots.  I'll mark this as solved when I move the computer upstairs and it works!

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

### Post by shane_faulkinbury2 on 2022-10-28
I know how to mark it solved, but it is not.  I got it working downstairs, moved it upstairs and just like last time it didn't work.  I thought maybe it was the range so thought about getting an extender, but took the cheaper route and installed Windows 10 Pro on my desktop which was the original OS this computer came with on a 250 GB SATA.  I will now install Ubuntu on my 2 TBB HDD to work quicker.  Oh, the range is fine on Windows 10 witch I am currently on.

---

### Post by #&amp;thj^% on 2022-10-28
shane after the move upstairs did you ever try with:
```
sudo modprobe 88x2bu
```

---

### Post by shane_faulkinbury2 on 2022-10-28
No I didn't.  I will after the install though.  Thanks

---

### Post by #&amp;thj^% on 2022-10-28
Also another tip I've learned is to keep it in a USB2 slot, even if it is a USB3 capable device.
Let us know I'm curious now...

---

### Post by shane_faulkinbury2 on 2022-11-07
Sorry getting back to this so late all.  I'm frustrated now.  It works sometimes and other times it doesn't.  I almost know the cost that I can do nothing about.  It's from an outside source I cannot talk about.  Last year I hard wired a [Fenvi PCI-e WiFi 6 Network Card AX3000Mbps Bluetooth 5.1 Wlan Adapter]("https://www.newegg.com/fenvi-fv-ax3000pro-pci-express/p/0XM-00JK-00093?Item=9SIADXZC8S5931") and it worked on and off.  At that time I was close to my router so I just ran an Ethernet cable to it.  I later got a USB wifi adapter which gave me the same problems as this one.  After almost giving up on this one the other day without the USB adapter I went to see if the wireless would work.  To my surprise it did.  It was the Fenvi working with no driver installed.  It worked for 5 days and went out.  This morning I got up and tried again.  No luck that time either.  I let the computer sit for 5 hours untouched and booted it up.  This time it worked.  I have at no time touched anything network related.  I think it is the source I previously talked about.  They can see what I talk about, but is there anyway I could get either method to work permantely?

---

