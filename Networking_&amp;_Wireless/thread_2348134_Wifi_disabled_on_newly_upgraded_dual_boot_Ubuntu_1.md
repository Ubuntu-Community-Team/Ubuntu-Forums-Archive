---
title: "Wifi disabled on newly upgraded dual boot Ubuntu 16.04"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by prashant-bhatia on 2017-01-01
Hello All,

Wishing all of you a happy new year. I have upgraded Ubuntu 16.04 (from 14.04) and have been trying to fix wifi issue since past 4 days without any luck.

1. The reason I upgraded Ubuntu was I wanted to solve wifi issue that I faced while installing 14.04.
2. But on 16.04 as well, I am facing same issue.
3. I have HP Pavilion x360 laptop with dual booting windows 10 which came pre-installed.
4. I have attached the link for output of script (Output link - [http://paste.ubuntu.com/23716873/](http://paste.ubuntu.com/23716873/)) which has been provided in this forum to get important information about Ethernet and Wifi on the system.
5. Script found on [https://raw.githubusercontent.com/Ub.../wireless-info](https://raw.githubusercontent.com/Ub.../wireless-info).
6. Screenshot of my desktop attached for reference depicting wifi disabled on the top right corner of the screen.

Would really appreciate if someone can assist fixing this issue. Thanks in advance.

---

### Post by raju5 on 2017-01-01
I have the same issue. Can someone please look into this matter ?

---

### Post by vasa1 on 2017-01-01
> **raju5 said:**
> I have the same issue. Can someone please look into this matter ?
It's a bit unlikely that you have **exactly** the same issue.

Please take the trouble to start your own thread using this one as a guide if you wish.

---

### Post by jeremy31 on 2017-01-01
> **prashant-bhatia said:**
> Hello All,

Wishing all of you a happy new year. I have upgraded Ubuntu 16.04 (from 14.04) and have been trying to fix wifi issue since past 4 days without any luck.

1. The reason I upgraded Ubuntu was I wanted to solve wifi issue that I faced while installing 14.04.
2. But on 16.04 as well, I am facing same issue.
3. I have HP Pavilion x360 laptop with dual booting windows 10 which came pre-installed.
4. I have attached the link for output of script (Output link - [http://paste.ubuntu.com/23716873/](http://paste.ubuntu.com/23716873/)) which has been provided in this forum to get important information about Ethernet and Wifi on the system.
5. Script found on [https://raw.githubusercontent.com/Ub.../wireless-info](https://raw.githubusercontent.com/Ub.../wireless-info).
6. Screenshot of my desktop attached for reference depicting wifi disabled on the top right corner of the screen.

Would really appreciate if someone can assist fixing this issue. Thanks in advance.

I would delete the one blacklist file because of some warnings
```
sudo rm /etc/modprobe.d/blacklist-acer-wmi.conf
```
And another one contradicts another
```
sudo rm /etc/modprobe.d/iwlwifi-opt.conf
```
You may have installed a broadcom module
```
sudo apt-get remove bcmwl-kernel-source broadcom-sta-dkms broadcom-sta-common
```

Reboot and run the script command again if it still doesn't work

---

### Post by prashant-bhatia on 2017-01-01
Thank You for your prompt response. Tried the scripts however issue still persists. Couple of screenshots that might assist in troubleshooting the issue. One screenshot shows the output of the scripts. The other screenshot shows I have enabled WIFI from status bar however I can't switch it to ON status under Network window.

Ran the wireless script again. Pls find the link for the output. [http://paste.ubuntu.com/23721978/](http://paste.ubuntu.com/23721978/)

---

### Post by jeremy31 on 2017-01-01
Run the wireless script again and post the new results

---

### Post by prashant-bhatia on 2017-01-01
Here you go Jeremy. Pls find the link for the output. [http://paste.ubuntu.com/23721978/](http://paste.ubuntu.com/23721978/)

---

### Post by jeremy31 on 2017-01-01
Have you checked in BIOS to see if wifi is enabled and reset BIOS to defaults?

---

### Post by prashant-bhatia on 2017-01-01
1. Wifi works fine when I work on Win10. 
2. I have done reset defaults in BIOS yesterday I think and I did it from BIOS system configuration but with no luck. 
3. I also opened up the laptop to remove the battery and put it back in. No luck there as well.

To add to what I have mentioned above. There is no physical wifi button on the laptop to turn it off/on.

---

### Post by jeremy31 on 2017-01-01
Does it boot if you remove acpi=off from grub?

---

### Post by prashant-bhatia on 2017-01-01
It would not, it will just give me blank purple window. 

In fact, when I tried installing 16.04 (not upgrading from 14.04), It would not boot no matter what parameters I input. But when I tried installing 14.04 with acpi=off and nomodeset, that's when it booted fine.

Post that, I upgraded it to 16.04 thinking it might resolve the wifi issue.

---

### Post by jeremy31 on 2017-01-01
Post results from ```
dmesg | grep iwl
```

---

### Post by prashant-bhatia on 2017-01-01
Not getting any output from the script you provided. just goes to the next line...

---

### Post by jeremy31 on 2017-01-01
There should be something.  I want to compare your system to some info on linuxmint forums ```
sudo apt-get install inxi
inxi -Fxz
```
Post results

---

### Post by prashant-bhatia on 2017-01-01
Script - 1 output

```
prashant@prashant-HP-Pavilion-13-x360-PC:~$ sudo apt-get install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
inxi is already the newest version (2.2.35-0ubuntu1).
The following packages were automatically installed and are no longer required:
  libcdaudio1 libenca0 libslv2-9
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

Script - 2 output

```
prashant@prashant-HP-Pavilion-13-x360-PC:~$ inxi -Fxz
System:    Host: prashant-HP-Pavilion-13-x360-PC Kernel: 4.4.0-57-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP Pavilion 13 x360 PC v: 0974120002405F00000420180
           Mobo: Hewlett-Packard model: 2341 v: 07.0A
           Bios: Insyde v: F.35 date: 07/29/2016
CPU:       Single core Intel Core i3-5010U (-UP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 4190 speed: 2100 MHz (max)
Graphics:  Card: Intel Broadwell-U Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 1366x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Broadwell-U Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-57-generic
Network:   Card-1: Intel Wireless 3160 driver: iwlwifi bus-ID: 03:00.0
           IF: wlan0 state: down mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 04:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (2.3% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB temp: 37C
Partition: ID-1: / size: 26G used: 9.0G (38%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 2.05GB used: 0.00GB (0%) fs: swap dev: /dev/sda4
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 189 Uptime: 1:36 Memory: 1102.5/3874.5MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35
```

---

### Post by jeremy31 on 2017-01-01
I would try booting once and press e at the grub menu and scroll down to the line with nomodeset and acpi=off and delete them and replace with
```
acpi_osi=!
```
Hopefully it will then boot with wireless enabled

---

### Post by prashant-bhatia on 2017-01-01
It did boot up fine and also started showing bluteooth and battery icons which it wasn't earlier. Thanks for that but now the wifi option doesn't showing up under Settings - Network. Screenshot attached for your reference. Do I need to install any drivers?

Also, do you recommend to do a permanent change to grub and replace nomodeset acpi=off with acpi_osi=! ? 

If Yes, can you pls let me know the script to do so?

---

### Post by wildmanne39 on 2017-01-01
A long time ago I had a laptop that I could only  boot with acpi=off and that parameter did in fact to my wifi off.

---

### Post by jeremy31 on 2017-01-01
We can change it by editing the grub file
```
sudo -H gedit /etc/default/grub
```

Then scroll to the line with nomodeset acpi=off and replace it with acpi_osi=!
Save and exit then do ```
sudo update-grub
```
Reboot, run the wireless-script once again and post the results.  I am still not sure why the dmesg command had no results, hopfully the grub change fixes that

---

### Post by prashant-bhatia on 2017-01-01
sure. Here is the output of wireless-script - [http://paste.ubuntu.com/23722546/](http://paste.ubuntu.com/23722546/)

Also, I tried below code again but no output just like before
dmesg | grep iwl

---

### Post by jeremy31 on 2017-01-01
What about ```
sudo modprobe -r iwlwifi
```
```
sudo modprobe -v iwlwifi
```
```
dmesg | tail
```

---

### Post by prashant-bhatia on 2017-01-01
Here are the output's for the above scripts.

sudo modprobe -r iwlwifi - No Output

prashant@prashant-HP-Pavilion-13-x360-PC:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=8 

prashant@prashant-HP-Pavilion-13-x360-PC:~$ dmesg | tail
[ 1014.180945] evbug: Event. Dev: input7, Type: 0, Code: 0, Value: 0
[ 1014.252950] evbug: Event. Dev: input7, Type: 3, Code: 0, Value: -27
[ 1014.252953] evbug: Event. Dev: input7, Type: 3, Code: 1, Value: 119
[ 1014.252955] evbug: Event. Dev: input7, Type: 0, Code: 0, Value: 0
[ 1014.324952] evbug: Event. Dev: input7, Type: 3, Code: 0, Value: -24
[ 1014.324955] evbug: Event. Dev: input7, Type: 3, Code: 1, Value: 131
[ 1014.324956] evbug: Event. Dev: input7, Type: 0, Code: 0, Value: 0
[ 1014.340819] evbug: Event. Dev: input3, Type: 4, Code: 4, Value: 28
[ 1014.340824] evbug: Event. Dev: input3, Type: 1, Code: 28, Value: 1
[ 1014.340826] evbug: Event. Dev: input3, Type: 0, Code: 0, Value: 0

---

### Post by jeremy31 on 2017-01-01
Strange ```
lsmod | grep evbug; dmesg | grep iwl
```

---

### Post by prashant-bhatia on 2017-01-01
prashant@prashant-HP-Pavilion-13-x360-PC:~$ lsmod | grep evbug; dmesg | grep iwl

Output --> evbug                  16384  0

---

### Post by jeremy31 on 2017-01-01
You still have an old UDEV file that doesn't need to be there
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```

Somehow a file was deleted, so we will put it back
```
sudo -H gedit /etc/modprobe.d/blacklist.conf
```

Add the following
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

Save, exit and reboot

---

### Post by prashant-bhatia on 2017-01-01
The above file opened with your script and it already contains this --- blacklist acer_wmi

Shall I remove the above piece of script from the file and then add the code you have mentioned or shall I just add your code below blacklist acer_wmi ??

---

### Post by praseodym on 2017-01-01
Any key or key combo (as there is no switch)? If yes, press this key (combo) permanently or repeatedly during boot-up

---

### Post by jeremy31 on 2017-01-01
Just add ```
blacklist acer_wmi
```
at the bottom of the file

---

### Post by prashant-bhatia on 2017-01-01
Sure Jeremy, I have added the code, restarted the system. Nothing much has changed...you need me to do anything else?

for whatever reasons, the file name in etc\modprobe.d shows this - blacklist.conf.save is it supposed to be like that? screenshot attached for your reference.

---

### Post by jeremy31 on 2017-01-01
It probably won't cause any issues

---

### Post by prashant-bhatia on 2017-01-01
alright cool. Anything else you want me to try to get this sorted?

---

### Post by jeremy31 on 2017-01-01
Just post results for ```
lspci -nnk | grep -iA2 net; dmesg | grep iwl; lsmod | grep iwl; rfkill list all
```

---

### Post by prashant-bhatia on 2017-01-01
```
prashant@prashant-HP-Pavilion-13-x360-PC:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    DeviceName: Intel Dual Band Wireless-AC 3160 802.11ac 1x1 WiFi + BT 4.0 Combo Adapter
    Subsystem: Intel Corporation Dual Band Wireless-AC 3160 [8086:0070]
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:2341]
    Kernel driver in use: r8169
    Kernel modules: r8169



prashant@prashant-HP-Pavilion-13-x360-PC:~$ dmesg | grep iwl
[   10.680606] iwlwifi 0000:03:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   10.897279] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   10.897431] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   10.897742] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   10.897765] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   15.895147] iwlwifi 0000:03:00.0: Failed to load firmware chunk!
[   15.895152] iwlwifi 0000:03:00.0: Could not load the [0] uCode section
[   15.895161] iwlwifi 0000:03:00.0: Failed to start INIT ucode: -110
[   15.895390] iwlwifi 0000:03:00.0: Failed to run INIT ucode: -110
[   15.895466] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled


prashant@prashant-HP-Pavilion-13-x360-PC:~$ lsmod | grep iwl
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm

prashant@prashant-HP-Pavilion-13-x360-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by jeremy31 on 2017-01-01
Try ```
sudo modprobe -r iwlwifi
```
```
sudo modprobe -v iwlwifi
```
With any luck it will work

---

### Post by prashant-bhatia on 2017-01-01
That absolutely worked....Thank You so much Jeremy!! Would you mind explaining briefly what went wrong and what you did to fix?

Really appreciate you looking into this issue and taking it to resolution.

---

### Post by jeremy31 on 2017-01-01
I think you are suffering from a bug I read about lately.  For some reason rfkill is getting toggled while iwlwifi module is trying to upload the firmware and that causes the upload to fail.

Reboot and see if it works on its own or if you have to run those modprobe commands again

---

### Post by prashant-bhatia on 2017-01-01
You are right. I rebooted and we have the situation back.

can we do a permanent fix for this one?

Forgot to add the output of below script.

prashant@prashant-HP-Pavilion-13-x360-PC:~$ sudo modprobe -v iwlwifi
insmod /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=8

---

### Post by jeremy31 on 2017-01-01
Do you have Secure Boot disabled in BIOS as I do have some patched source code that may work

---

### Post by prashant-bhatia on 2017-01-02
I have disabled the secure boot now. Do let me know what you want me to do next. Thanks!

---

### Post by jeremy31 on 2017-01-02
This will work only for kernel 4.4.0-57
```
wget https://www.dropbox.com/s/ebguegmfg7rueh5/iwl4.4.57.tar.gz
tar -zxvf iwl4.4.57.tar.gz
cd iwl4.4.57
```

Then we backup the current kernel modules
```
 sudo mv /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko.bak
```
```
sudo mv /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko.bak
```
Then copy the patched ones in
```
sudo cp iwlwifi.ko /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
```
```
sudo cp iwlmvm.ko /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
```

Reboot

Patch used is from [here](http://git.kernel.org/cgit/linux/kernel/git/next/linux-next.git/commit/drivers/net/wireless/intel/iwlwifi?id=a6bd005fe92dc1cc808c4c6aa43e3b2a8272bbfa)

---

### Post by prashant-bhatia on 2017-01-02
Thanks Jeremy! That sure fixed the issue. Restarted the system after running above scripts and it straight away picked up my wifi connections. Again really appreciate you looking into this one and sorting this out. Great troubleshooting and Thanks for your assistance!!

---

### Post by jeremy31 on 2017-01-02
If you want to keep using the 4.4 kernels in Ubuntu, I would recommend filing a bug report, a small guide can be found [here](https://ubuntuforums.org/showthread.php?t=1011078)
If you want to switch to the 4.8 kernel you can install with ```
sudo apt-get install linux-generic-hwe-16.04-edge
```
I checked the source code for 4.8 and it has the patch I used, a bug report would be needed to get the patch into 4.4
You could have issues with the 4.8 kernels, I can't know

---

### Post by prashant-bhatia on 2017-01-02
Sure will give it a try. Just to ensure I have clear understanding on the bug, so you want me to file the bug for what you mentioned in your earlier posts yesterday --- "[COLOR=#000000]I think you are suffering from a bug I read about lately. For some reason rfkill is getting toggled while iwlwifi module is trying to upload the firmware and that causes the upload to fail.[/COLOR]"

Do let me know and I think I will stick with 4.4 Kernel as of now as I just want to learn and soak in as much as I can about Shell scripts and Ubuntu. Idea is to make myself comfortable with Ubuntu or shall I say Linux so much so to make this my main operating system in near future and remove Windows 10.

---

### Post by jeremy31 on 2017-01-02
You will likely have to wait for the next kernel update so that the strange behavior occurs again before filing the bug, then after you use the modprobe command you can report the bug against package linux since it is an issue with the kernel

You can get my patched source code with
```
wget https://www.dropbox.com/s/frw4h1y1lp3cfsf/iwlwifi.tar.gz
tar -zxvf iwlwifi.tar.gz
```
I put a file named commands with the commands to use after a kernel update but you will need to install some packages to be able to compile
```
sudo apt-get install build-essential linux-headers-generic
```
You should be able to paste the commands from the file into terminal after using ```
cd ~/iwlwifi
```
Reboot when done

---

### Post by prashant-bhatia on 2017-01-02
Alright, I will wait for the next update to see if I find this recurring behavior and accordingly take the course of action as you have suggested. I guess for now I can sit back and wait until that update comes out.

Any ideas when the next update is expected?

---

