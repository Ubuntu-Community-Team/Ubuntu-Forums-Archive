---
title: "USB wireless WiFi adaptor"
date: 2023-05-19
forum: Networking &amp; Wireless
---

### Post by tinman456 on 2023-05-19
Hi there knowledgeable folks, 

I have a Linux driver  for my USB wireless WiFi adapter and I cannot  install it for love or  money. It came with a shell script that does not  complete and ends with  an error 2 message that I still can't resolve. I  do know the adapter is  compatible because it did work when I first  installed Ubuntu  "alongside" my Windows but now as I have it on a  dedicated HDD no luck.  

Can anybody be of help here?

Thanks in advance

---

### Post by ajgreeny on 2023-05-19
We need to know a lot more about the hardware in question, both the computer itself and the USB wireless WiFi adapter you're trying to get working.
Without that we are simply guessing so as a start with the adapter attached please run commands ```
inxi -Fzx && lsusb
```

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by tinman456 on 2023-05-19
Hi Aj, Thank you very much for your quick response. I'm new to all this and had to install some stuff before I was able to get an output. Is the following acceptable? I really DO appreciate your help - very much...

```
System:
  Kernel: 5.19.0-41-generic x86_64 bits: 64 compiler: N/A Desktop: Unity
    Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Hewlett-Packard product: HP G42 Notebook PC
    v: 0597130000202710010020100 serial: <superuser required>
  Mobo: Hewlett-Packard model: 1425 v: 54.57 serial: <superuser required>
    BIOS: Hewlett-Packard v: F.37 date: 04/07/2011
CPU:
  Info: dual core model: Intel Pentium P6200 bits: 64 type: MCP
    arch: Westmere rev: 5 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 2128 min/max: 933/2133 cores: 1: 2128 2: 2128
    bogomips: 8513
  Flags: ht lm nx pae sse sse2 sse3 ssse3
Graphics:
  Device-1: Intel Core Processor Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: Silicon Motion - Taiwan (formerly Feiya ) HP Webcam-101
    Integrated Camera
    type: USB driver: uvcvideo bus-ID: 2-1.5:4
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 resolution: 1360x768~59Hz
  OpenGL: renderer: Mesa Intel HD Graphics (ILK) v: 2.1 Mesa 22.2.5
    direct render: Yes
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio
    vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Sound Server-1: ALSA v: k5.19.0-41-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Broadcom BCM4313 802.11bgn Wireless Network Adapter
    vendor: Hewlett-Packard driver: wl v: kernel bus-ID: 02:00.0
  IF: wlo1 state: dormant mac: <filter>
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 2000 bus-ID: 03:00.0
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
  Device-3: Realtek 802.11ac NIC type: USB driver: N/A bus-ID: 2-1.2:7
Bluetooth:
  Device-1: Broadcom BCM2070 Bluetooth 2.1 + EDR type: USB driver: btusb
    v: 0.8 bus-ID: 1-1.3:4
  Report: hciconfig ID: hci0 rfk-id: 8 state: down
    bt-service: enabled,running rfk-block: hardware: no software: no
    address: <filter>
Drives:
  Local Storage: total: 298.09 GiB used: 19.97 GiB (6.7%)
  ID-1: /dev/sda vendor: Western Digital model: WD3200BEKT-60F3T1
    size: 298.09 GiB
Partition:
  ID-1: / size: 291.85 GiB used: 19.97 GiB (6.8%) fs: ext4 dev: /dev/sda3
  ID-2: /boot/efi size: 512 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 1.09 GiB (54.5%) file: /swapfile
Sensors:
  System Temperatures: cpu: 57.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 297 Uptime: 1d 3h 10m Memory: 7.56 GiB used: 4.92 GiB (65.0%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.3.0 Packages: 1740 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
Bus 002 Device 004: ID 090c:37bc Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) HP Webcam-101 Integrated Camera
Bus 002 Device 007: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC
Bus 002 Device 006: ID 0000:3825   USB OPTICAL MOUSE
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by jeremy31 on 2023-05-19
If you can connect with USB tethering do
```
sudo apt update
sudo apt install git dkms
git clone https://github.com/morrownr/8821cu-20210916.git
cd 8821cu-20210916
sudo ./install-driver.sh
mokutil --sb
```
If the last command results with "Secure Boot enabled" then Secure Boot will need to be disabled in BIOS settings when you reboot

---

### Post by tinman456 on 2023-05-19
Hey Jeremy! It worked! How do you guys do this?

I ran the commands as you listed and it did its thing and it then, lo and behold, actually DID connect to my 5gz wireless through the USB adapter.

I am forever grateful, thank you and thank you again.

Anthony

---

### Post by ajgreeny on 2023-05-20
**Great news! **

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by morrownr on 2023-05-20
> **tinman456 said:**
> It worked! How do you guys do this?

Anthony

It actually takes a lot of work by several people. You can go to the repo and look at the bottom of the README to see the people that worked on this driver.. The lines of commands may get the driver installed but there is more that you need to know to keep it going:


[https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

The Main Menu of the site where this driver lives is:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

There is a LOT of information for USB WiFi users at that site.

@morrownr

---

### Post by tinman456 on 2023-05-21
> **tinman456 said:**
> Hey Jeremy! It worked! How do you guys do this?

I ran the commands as you listed and it did its thing and it then, lo and behold, actually DID connect to my 5gz wireless through the USB adapter.

I am forever grateful, thank you and thank you again.

Anthony

Hey Jeremy, I don't want to be a nuisance but it's still not working right. Let me try to explain. The USB adapter itself has two modes 2.4ghz and 5ghz and the laptop has a built-in 2.4ghz w/less card. The problem is that ALL of them are connecting at once and I can't figure out how to disable the ones I don't want to use. Once i enable one they all connect and the sum effect is that the connection is very slow as it seems to favor the 2.4ghz above the 5ghz.

Is there anything we can do to fix this?

Thanks in advance

---

### Post by jeremy31 on 2023-05-21
Try ```
sudo modprobe -r wl
```
See if that works better with the internal cards driver unloaded

---

### Post by tinman456 on 2023-05-21
> **jeremy31 said:**
> Try ```
sudo modprobe -r wl
```
See if that works better with the internal cards driver unloaded

Well so far that seems to have done the trick. It's now acceptably fast enough so i can disconnect the Ethernet. I have so so much to learn!

I would eventually like to use Ubuntu in place of my Win10 laptop but without the help of you guys in the forum it would be next to impossible. Besides there is still a lot of functionality that is very challenging to implement. A lot still has to be done to make this OS simpler to use. It's a shame it's not further along because as an alternate to Windows for the masses it really has so much more to offer. I'll read up on the links you sent me earlier and keep on truckin' and hope you guys don't lose patience with me.

I know I can install it for my wife and she would be have little to no problems but she is just a basic user/housewife and it will work just fine for that.

Thanks for all your help and Moribus (I think that's his handle) as well who helped me 100% with the sharing I needed to access my Windows laptop.

So until the next time, cheers to everybody and thanks a whole lot -again.
Anthony

---

### Post by jeremy31 on 2023-05-21
You should go into the Driver Manager in Software & Updates and uninstall the broadcom proprietary module so you don't have to run the sudo modprobe -r wl command after every boot

---

### Post by tinman456 on 2023-05-25
> **morrownr said:**
> It actually takes a lot of work by several people. You can go to the repo and look at the bottom of the README to see the people that worked on this driver.. The lines of commands may get the driver installed but there is more that you need to know to keep it going:


[https://github.com/morrownr/8821cu-20210916](https://github.com/morrownr/8821cu-20210916)

The Main Menu of the site where this driver lives is:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

There is a LOT of information for USB WiFi users at that site.

@morrownr

Thank you morrownr. I was just looking through my posts and realized that it was you who actually sent me those research links. I appreciate it.

Patience, dedication and motivation are the no1 requirements for any potential Linux adopter lol.

---

### Post by tinman456 on 2023-05-25
> **jeremy31 said:**
> You should go into the Driver Manager in Software & Updates and uninstall the broadcom proprietary module so you don't have to run the sudo modprobe -r wl command after every boot

Just saw your suggestion and did just that! A big help really.....thanks

---

