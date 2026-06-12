---
title: "wifi doesnt work"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by madaxeslasher on 2015-05-26
Ive been using Ubuntu for a while now and can not find a solution to my issue...
My wifi will not work.. I have a dell studio 15 dual boot... windows 7 on one side and my goto OS Ubuntu... 
Ive looked and searched the web and tried all kinds of recommendations on how to to fix this problem with out any success..
Can someone please help me so I can get back to enjoying this OS as I always have... 

First.... My connection works with ethernet...
Ive checked for and installed all updates... installed kernal 4.??...
 
```
lspci -nnk | grep -iA2 net    shows the following info

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
    Kernel driver in use: iwlwifi
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Dell Device [1028:0413]
    Kernel driver in use: r8169
the wireless icon shows up in the top bar but remains empty with out signal bars.. nor do i have an option to (enable wireless) in the drop down

every time i reboot Network tools shows that my wifi is inactive.. so i run 

sudo ifconfig wlan0 up

then it shows my wifi is active.. but still no wifi.....

ive tried rfkill unblock all.. still nothing..

 sudo lshw -class network    

*-network               
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 35
       serial: 00:23:14:99:74:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.0.3-040003-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:28 memory:f0500000-f0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: b8:ac:6f:70:c4:2d
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.254.27 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:25 ioport:4000(size=256) memory:f0b04000-f0b04fff memory:f0b00000-f0b03fff memory:a0600000-a061ffff



sudo /etc/init.d/networking restart    ... still nothing


iwconfig      

eth0      no wireless extensions.


wlan0 IEEE 802.11abgn ESSIDff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=15 dBm 
Retry short limit:7 RTS thrff Fragment thrff
Power Managementff
          
lo        no wireless extensions.
```


there is a function to turn the wifi off and on by pressing the F2 button but that has never worked on the ubuntu side.. only on the windows.... regardless ive tried pressing it.. Fn+F2, Alt+F2, Ctrl+F2..... nothing

Ive even removed the wireless device on the windows side and rebotted to reinstall the drivers for them because at one point when I used the F2 button the pop up on the sceen said wifi off but the program said it was on and vice versa... but now thats sorted out I still have no wifi with my ubuntu..15.04  any help would be greatly appreciated....

---

### Post by chili555 on 2015-05-27
Please run and post:```
lsmod
rfkill list all
dmesg | grep iwl
```For what it's worth, mine is the exact same wireless device!

---

### Post by madaxeslasher on 2015-05-27
```
lsmod

Module                  Size  Used by
binfmt_misc            20480  1 
uvcvideo               94208  0 
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         53248  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              163840  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
arc4                   16384  2 
iwldvm                245760  0 
mac80211              774144  1 iwldvm
dell_wmi               16384  0 
dell_laptop            16384  0 
dcdbas                 16384  1 dell_laptop
snd_hda_codec_hdmi     53248  1 
snd_hda_codec_idt      61440  1 
i915                 1126400  9 
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
snd_hda_intel          32768  3 
snd_hda_controller     36864  1 snd_hda_intel
snd_hda_codec         147456  5 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
iwlwifi               208896  1 iwldvm
sparse_keymap          16384  1 dell_wmi
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               110592  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
drm_kms_helper        126976  1 i915
snd_timer              32768  1 snd_pcm
snd                    86016  14 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
drm                   352256  6 i915,drm_kms_helper
i8k                    16384  0 
intel_powerclamp       20480  0 
joydev                 20480  0 
serio_raw              16384  0 
soundcore              16384  2 snd,snd_hda_codec
kvm_intel             159744  0 
cfg80211              581632  3 iwlwifi,mac80211,iwldvm
kvm                   512000  1 kvm_intel
i2c_algo_bit           16384  1 i915
mei_me                 20480  0 
mei                    90112  1 mei_me
dell_smo8800           16384  0 
intel_ips              20480  0 
wmi                    20480  1 dell_wmi
video                  28672  1 i915
shpchp                 40960  0 
lpc_ich                24576  0 
mac_hid                16384  0 
coretemp               16384  0 
parport_pc             36864  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
sdhci_pci              24576  0 
psmouse               126976  0 
sdhci                  45056  1 sdhci_pci
firewire_ohci          49152  0 
ahci                   36864  3 
r8169                  90112  0 
firewire_core          69632  1 firewire_ohci
libahci                32768  1 ahci
mii                    16384  1 r8169
crc_itu_t              16384  1 firewire_core

rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



dmesg | grep iwl

[   11.582156] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   11.907362] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   11.907591] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   12.001407] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   12.381875] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.381876] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.381878] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.381879] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[   12.381997] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[   12.497847] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```

I love Ubuntu and I am frustrated... Thank you for looking into this for me

---

### Post by chili555 on 2015-05-27
So far, so good! Let's dig deeper:```
cat /etc/network/interfaces
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```Off for a couple of hours; I'll check in later.

---

### Post by madaxeslasher on 2015-05-27
cat /etc/network/interfaces

auto lo
iface lo inet loopback


cat/var/log/syslog | grep -e etwork -e wlan | tail -n20

bash: cat/var/log/syslog: No such file or directory


Thank You

---

### Post by wildmanne39 on 2015-05-27
Please try this command with a space between cat and /.
```
cat /var/log/syslog | grep -e etwork -e wlan | tail -n20
```
Please use code tags when posting code by clicking on the # and putting the code in between the brackets.
Thanks

---

### Post by madaxeslasher on 2015-05-27
```
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <warn> DNS: plugin dnsmasq update failed
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <info> Writing DNS information to /sbin/resolvconf
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <info> Activation (eth0) successful, device activated.
May 27 10:46:38 chris-Studio-1558 systemd[1]: Starting Network Manager Script Dispatcher Service...
May 27 10:46:38 chris-Studio-1558 systemd[1]: Started Network Manager Script Dispatcher Service.
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: <warn> dnsmasq appeared on DBus: :1.23
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: <info> Writing DNS information to /sbin/resolvconf
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:42 chris-Studio-1558 NetworkManager[528]: <info> startup complete
May 27 10:46:42 chris-Studio-1558 systemd[1]: Started Network Manager Wait Online.
May 27 10:46:42 chris-Studio-1558 systemd[1]: Reached target Network is Online.
May 27 10:46:42 chris-Studio-1558 systemd[1]: Starting Network is Online.
May 27 10:46:44 chris-Studio-1558 NetworkManager[528]: <info> WiFi hardware radio set enabled
May 27 10:46:44 chris-Studio-1558 NetworkManager[528]: <info> WWAN hardware radio set enabled
May 27 10:47:51 chris-Studio-1558 gnome-session[1386]: INFO  2015-05-27 10:47:51.014 [main] Using address /192.168.254.27 found on network interface: name:eth0 (eth0)
May 27 11:43:46 chris-Studio-1558 gnome-session[1386]: INFO  2015-05-27 11:43:46.676 [pool-5-thread-1] Address /192.168.254.34 has an estimated network speed of: 21 Mb/s
```

---

### Post by QIII on 2015-05-27
Again:  Please use code tags.

---

### Post by madaxeslasher on 2015-05-27
```

May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <warn> DNS: plugin dnsmasq update failed
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <info> Writing DNS information to /sbin/resolvconf
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf
May 27 10:46:38 chris-Studio-1558 NetworkManager[528]: <info> Activation (eth0) successful, device activated.
May 27 10:46:38 chris-Studio-1558 systemd[1]: Starting Network Manager Script Dispatcher Service...
May 27 10:46:38 chris-Studio-1558 systemd[1]: Started Network Manager Script Dispatcher Service.
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: <warn> dnsmasq appeared on DBus: :1.23
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: <info> Writing DNS information to /sbin/resolvconf
May 27 10:46:39 chris-Studio-1558 NetworkManager[528]: /etc/resolvconf/update.d/libc: Warning: /etc/resolv.conf is not a symbolic link to /etc/resolvconf/run/resolv.conf
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:39 chris-Studio-1558 whoopsie[525]: [10:46:39] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
May 27 10:46:42 chris-Studio-1558 NetworkManager[528]: <info> startup complete
May 27 10:46:42 chris-Studio-1558 systemd[1]: Started Network Manager Wait Online.
May 27 10:46:42 chris-Studio-1558 systemd[1]: Reached target Network is Online.
May 27 10:46:42 chris-Studio-1558 systemd[1]: Starting Network is Online.
May 27 10:46:44 chris-Studio-1558 NetworkManager[528]: <info> WiFi hardware radio set enabled
May 27 10:46:44 chris-Studio-1558 NetworkManager[528]: <info> WWAN hardware radio set enabled
May 27 10:47:51 chris-Studio-1558 gnome-session[1386]: INFO  2015-05-27 10:47:51.014 [main] Using address /192.168.254.27 found on network interface: name:eth0 (eth0)
May 27 11:43:46 chris-Studio-1558 gnome-session[1386]: INFO  2015-05-27 11:43:46.676 [pool-5-thread-1] Address /192.168.254.34 has an estimated network speed of: 21 Mb/s

```

no internet connection at all.... after update and restart I'm with out connection ... wired or wireless


Please help

never mind after additional reboot i now have Ethernet connection..  
so, just the original problem.....

---

### Post by chili555 on 2015-05-28
I suspect, from the syslog readings, that the ethernet cable may be attached and the we are seeing some information related to ethernet and some from wireless, It's hard for us to see what's going wrong with either or both! For now, let's concentrate on wireless and please detach the ethernet for now.

I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by ericschopper on 2015-05-28
Make sure you have the correct drivers for your wifi, I had the same problem, but after installing the drivers it works. Go to settings>software and updates>additional drivers, then search for drivers and download the one you need.

Cheers-eric

---

### Post by chili555 on 2015-05-28
> **ericschopper said:**
> Make sure you have the correct drivers for your wifi, I had the same problem, but after installing the drivers it works. Go to settings>software and updates>additional drivers, then search for drivers and download the one you need.

Cheers-ericAdditional Drivers only installs wireless drivers for Broadcom devices. madaxeslasher has an Intel. Your suggestion will be ineffective.

---

### Post by madaxeslasher on 2015-05-28
didnt work...

---

### Post by chili555 on 2015-05-28
> **madaxeslasher said:**
> didnt work...Which?

---

### Post by madaxeslasher on 2015-05-28
the instructions posted.. ignoring ipv6... 
changing my country code to US   etc.. 

additional drivers has nothing for me

---

### Post by ericschopper on 2015-05-28
I found this from this thread. [http://askubuntu.com/questions/489157/intel-wireless-7260-card-doesnt-connect-to-wifi-sometimes](http://askubuntu.com/questions/489157/intel-wireless-7260-card-doesnt-connect-to-wifi-sometimes)

Try Disabling 802.11n by

```
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1

```

Then reboot and see if that helps. You can also try turning off wifi power management by doing

```
sudo iwconfig
```


Then find the name of the wireless device (usually wlan0) and do

```
sudo iwconfig wlan0 power off
```

Hope that helps

---

### Post by chili555 on 2015-05-28
> Code:
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1
Then reboot and see if that helps. If you reboot, the temporary module parameter will disappear.

---

### Post by madaxeslasher on 2015-05-28
sudo rmmod iwlwifi

```
rmmod: ERROR: Module iwlwifi is in use by: iwldvm
```

---

### Post by madaxeslasher on 2015-05-28
sudo iwconfig wlan0 power off

```
Error for wireless request "Set Power Management" (8B2C) :    SET failed on device wlan0 ; No such device.



```

 sudo rmmod iwlwifi

```
rmmod: ERROR: Module iwlwifi is in use by: iwldvm
```

 sudo rmmod iwldvn

```
rmmod: ERROR: Module iwldvn is not currently loaded
```

sudo iwconfig

```
eth0      no wireless extensions.

lo        no wireless extensions.
```

---

### Post by ctgcwiqc on 2015-05-28
FWIW make certain that WiFi is not disabled in Windoze.  If I disable WiFi in Windoze and reboot into Ubuntu, WiFi will not work unless I boot back to Windozzzze and re-enable WiFi no matter what commands I put into terminal or which hotkeys I press.  Hopefully that helps.

---

### Post by chili555 on 2015-05-29
Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
echo iwlwifi  >>  /etc/modules
exit
```Detach the ethernet, reboot and run:```
dmesg >  wifi.txt
```Find the file wifi.txt in your user direstory and post it here:  [http://paste.ubuntu.com](http://paste.ubuntu.com)

Please give me the link in your reply.

---

### Post by madaxeslasher on 2015-05-30
```
[    0.000000] CPU0 microcode updated early to revision 0xe, date = 2013-06-26[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.0.3-040003-generic (kernel@tangerine) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201505131441 SMP Wed May 13 13:43:16 UTC 2015
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.0.3-040003-generic root=UUID=dd0f9cec-379f-47e9-83f5-1790ce51c8be ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009c3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009c400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000d2000-0x00000000000d3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009b27bfff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b27c000-0x000000009b281fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b282000-0x000000009b3e5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b3e6000-0x000000009b40efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b40f000-0x000000009b46efff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b46f000-0x000000009b46ffff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b470000-0x000000009b4f0fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b4f1000-0x000000009b70efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b70f000-0x000000009b716fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b717000-0x000000009b71efff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009b71f000-0x000000009b77dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b77e000-0x000000009b79efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009b79f000-0x000000009b7e1fff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b7e2000-0x000000009b7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009b7ff000-0x000000009b7fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009b800000-0x000000009fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f0a04000-0x00000000f0a04fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feaff000-0x00000000feafffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x0000000157ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Dell Inc. Studio 1558/0G939P, BIOS A12 03/30/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x158000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DBFFF uncachable
[    0.000000]   DC000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask FC0000000 write-back
[    0.000000]   4 base 140000000 mask FE0000000 write-back
[    0.000000]   5 base 158000000 mask FF8000000 uncachable
[    0.000000]   6 base 09C000000 mask FFC000000 uncachable
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] e820: last_pfn = 0x9b800 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f7050-0x000f705f] mapped at [ffff8800000f7050]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fcd000, 0x01fcdfff] PGTABLE
[    0.000000] BRK [0x01fce000, 0x01fcefff] PGTABLE
[    0.000000] BRK [0x01fcf000, 0x01fcffff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x157e00000-0x157ffffff]
[    0.000000]  [mem 0x157e00000-0x157ffffff] page 2M
[    0.000000] BRK [0x01fd0000, 0x01fd0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x140000000-0x157dfffff]
[    0.000000]  [mem 0x140000000-0x157dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x120000000-0x13fffffff]
[    0.000000]  [mem 0x120000000-0x13fffffff] page 2M
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x00100000-0x9b27bfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x9b1fffff] page 2M
[    0.000000]  [mem 0x9b200000-0x9b27bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b282000-0x9b3e5fff]
[    0.000000]  [mem 0x9b282000-0x9b3e5fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b40f000-0x9b46efff]
[    0.000000]  [mem 0x9b40f000-0x9b46efff] page 4k
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9b70f000-0x9b716fff]
[    0.000000]  [mem 0x9b70f000-0x9b716fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b71f000-0x9b77dfff]
[    0.000000]  [mem 0x9b71f000-0x9b77dfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b79f000-0x9b7e1fff]
[    0.000000]  [mem 0x9b79f000-0x9b7e1fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9b7ff000-0x9b7fffff]
[    0.000000]  [mem 0x9b7ff000-0x9b7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x11fffffff]
[    0.000000]  [mem 0x100000000-0x11fffffff] page 2M
[    0.000000] RAMDISK: [mem 0x3595c000-0x36ca5fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F6F70 000024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 0x000000009B7F403E 000074 (v01 DELL   QA09     06040000  LTP 00000000)
[    0.000000] ACPI: FACP 0x000000009B7E4000 0000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 0x000000009B7E5000 00A9B8 (v02 Intel  CALPELLA 06040000 INTL 20060912)
[    0.000000] ACPI: FACS 0x000000009B79BFC0 000040
[    0.000000] ACPI: HPET 0x000000009B7FEC0A 000038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 0x000000009B7FEC42 00003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 0x000000009B7FEC7E 000084 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 0x000000009B7FED02 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SPCR 0x000000009B7FED2A 000050 (v01 PTLTD  $UCRTBL$ 06040000 PTL  00000001)
[    0.000000] ACPI: SLIC 0x000000009B7FED7A 000176 (v01 DELL   QA09     06040000  LTP 00000000)
[    0.000000] ACPI: OSFR 0x000000009B7FEEF0 000070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: ASF! 0x000000009B7FEF60 0000A0 (v16   CETP     CETP 06040000 PTL  00000001)
[    0.000000] ACPI: SSDT 0x000000009B7E3000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20060912)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x0000000157ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x157ff7000-0x157ffbfff]
[    0.000000]  [ffffea0000000000-ffffea00055fffff] PMD -> [ffff880153800000-ffff8801575fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x0000000157ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009bfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000009b27bfff]
[    0.000000]   node   0: [mem 0x000000009b282000-0x000000009b3e5fff]
[    0.000000]   node   0: [mem 0x000000009b40f000-0x000000009b46efff]
[    0.000000]   node   0: [mem 0x000000009b70f000-0x000000009b716fff]
[    0.000000]   node   0: [mem 0x000000009b71f000-0x000000009b77dfff]
[    0.000000]   node   0: [mem 0x000000009b79f000-0x000000009b7e1fff]
[    0.000000]   node   0: [mem 0x000000009b7ff000-0x000000009b7fffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x0000000157ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x0000000157ffffff]
[    0.000000] On node 0 totalpages: 996486
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 9876 pages used for memmap
[    0.000000]   DMA32 zone: 632043 pages, LIFO batch:31
[    0.000000]   Normal zone: 5632 pages used for memmap
[    0.000000]   Normal zone: 360448 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x9e000000-0x9fffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000d1fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d2000-0x000d3fff]
[    0.000000] PM: Registered nosave memory: [mem 0x000d4000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b27c000-0x9b281fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b3e6000-0x9b40efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b46f000-0x9b46ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b470000-0x9b4f0fff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b4f1000-0x9b70efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b717000-0x9b71efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b77e000-0x9b79efff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b7e2000-0x9b7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9b800000-0x9fffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xa0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf0a03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0a04000-0xf0a04fff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0a05000-0xfeafefff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeaff000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xa0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 32 pages/cpu @ffff880157c00000 s91032 r8192 d31848 u524288
[    0.000000] pcpu-alloc: s91032 r8192 d31848 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 980893
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.0.3-040003-generic root=UUID=dd0f9cec-379f-47e9-83f5-1790ce51c8be ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3819564K/3985944K available (8150K kernel code, 1137K rwdata, 3920K rodata, 1420K init, 1292K bss, 166380K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2260.767 MHz processor
[    0.000038] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.53 BogoMIPS (lpj=9043068)
[    0.000041] pid_max: default: 32768 minimum: 301
[    0.000048] ACPI: Core revision 20150204
[    0.008739] ACPI: All ACPI Tables successfully acquired
[    0.023011] Security Framework initialized
[    0.023028] AppArmor: AppArmor initialized
[    0.023029] Yama: becoming mindful.
[    0.023384] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.024370] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.024804] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.024816] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.025055] Initializing cgroup subsys blkio
[    0.025060] Initializing cgroup subsys memory
[    0.025068] Initializing cgroup subsys devices
[    0.025071] Initializing cgroup subsys freezer
[    0.025073] Initializing cgroup subsys net_cls
[    0.025076] Initializing cgroup subsys perf_event
[    0.025078] Initializing cgroup subsys net_prio
[    0.025081] Initializing cgroup subsys hugetlb
[    0.025108] CPU: Physical Processor ID: 0
[    0.025109] CPU: Processor Core ID: 0
[    0.025115] mce: CPU supports 9 MCE banks
[    0.025125] CPU0: Thermal monitoring handled by SMI
[    0.025132] process: using mwait in idle threads
[    0.025136] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.025137] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.025253] Freeing SMP alternatives memory: 28K (ffffffff81e81000 - ffffffff81e88000)
[    0.026819] ftrace: allocating 33165 entries in 130 pages
[    0.046172] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.192681] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz (fam: 06, model: 25, stepping: 02)
[    0.192715] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.192735] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.192738] ... version:                3
[    0.192739] ... bit width:              48
[    0.192740] ... generic registers:      4
[    0.192741] ... value mask:             0000ffffffffffff
[    0.192742] ... max period:             000000007fffffff
[    0.192743] ... fixed-purpose events:   3
[    0.192745] ... event mask:             000000070000000f
[    0.193686] x86: Booting SMP configuration:
[    0.193689] .... node  #0, CPUs:      #1
[    0.205029] CPU1 microcode updated early to revision 0xe, date = 2013-06-26
[    0.205071] CPU1: Thermal monitoring handled by SMI
[    0.207222] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.207359]  #2
[    0.218331] CPU2: Thermal monitoring handled by SMI
[    0.220566]  #3
[    0.231635] CPU3: Thermal monitoring handled by SMI
[    0.233745] x86: Booted up 1 node, 4 CPUs
[    0.233750] smpboot: Total of 4 processors activated (18086.13 BogoMIPS)
[    0.236611] devtmpfs: initialized
[    0.242373] evm: security.selinux
[    0.242375] evm: security.SMACK64
[    0.242376] evm: security.SMACK64EXEC
[    0.242377] evm: security.SMACK64TRANSMUTE
[    0.242378] evm: security.SMACK64MMAP
[    0.242379] evm: security.ima
[    0.242380] evm: security.capability
[    0.242453] PM: Registering ACPI NVS region [mem 0x9b470000-0x9b4f0fff] (528384 bytes)
[    0.242464] PM: Registering ACPI NVS region [mem 0x9b77e000-0x9b79efff] (135168 bytes)
[    0.242641] pinctrl core: initialized pinctrl subsystem
[    0.242773] RTC time:  2:18:03, date: 05/31/15
[    0.242906] NET: Registered protocol family 16
[    0.244719] cpuidle: using governor ladder
[    0.248713] cpuidle: using governor menu
[    0.248819] ACPI: bus type PCI registered
[    0.248822] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.248913] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.248917] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.249493] PCI: Using configuration type 1 for base access
[    0.249702] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.249703] mtrr: probably your BIOS does not setup all CPUs.
[    0.249704] mtrr: corrected configuration.
[    0.253201] ACPI: Added _OSI(Module Device)
[    0.253204] ACPI: Added _OSI(Processor Device)
[    0.253205] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.253207] ACPI: Added _OSI(Processor Aggregator Device)
[    0.259298] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.260032] ACPI: Dynamic OEM Table Load:
[    0.260040] ACPI: SSDT 0xFFFF880152B20C00 0003F0 (v01 PmRef  Cpu0Ist  00003000 INTL 20060912)
[    0.260491] ACPI: Dynamic OEM Table Load:
[    0.260498] ACPI: SSDT 0xFFFF880152B19000 0008B0 (v01 PmRef  Cpu0Cst  00003001 INTL 20060912)
[    0.261215] ACPI: Dynamic OEM Table Load:
[    0.261220] ACPI: SSDT 0xFFFF880152B21400 000303 (v01 PmRef  ApIst    00003000 INTL 20060912)
[    0.261670] ACPI: Dynamic OEM Table Load:
[    0.261675] ACPI: SSDT 0xFFFF880152AEDE00 000119 (v01 PmRef  ApCst    00003000 INTL 20060912)
[    0.262622] ACPI: Interpreter enabled
[    0.262630] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150204/hwxface-580)
[    0.262635] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150204/hwxface-580)
[    0.262650] ACPI: (supports S0 S3 S4 S5)
[    0.262652] ACPI: Using IOAPIC for interrupt routing
[    0.262684] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.263190] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.263345] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.269426] ACPI: Power Resource [FN00] (off)
[    0.269524] ACPI: Power Resource [FN01] (off)
[    0.270230] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.270237] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.270274] \_SB_.PCI0:_OSC invalid UUID
[    0.270275] _OSC request data:1 1f 0 
[    0.270279] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.270811] PCI host bridge to bus 0000:00
[    0.270814] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.270817] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.270819] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.270821] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.270823] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.270825] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.270827] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.270829] pci_bus 0000:00: root bus resource [mem 0xa0000000-0xdfffffff window]
[    0.270831] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff window]
[    0.270841] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.270863] DMAR: BIOS has allocated no shadow GTT; disabling IOMMU for graphics
[    0.270962] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.270975] pci 0000:00:02.0: reg 0x10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.270982] pci 0000:00:02.0: reg 0x18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.270987] pci 0000:00:02.0: reg 0x20: [io  0x1800-0x1807]
[    0.271135] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.271167] pci 0000:00:16.0: reg 0x10: [mem 0xf0a05800-0xf0a0580f 64bit]
[    0.271268] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.271391] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.271419] pci 0000:00:1a.0: reg 0x10: [mem 0xf0a06000-0xf0a063ff]
[    0.271533] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.271648] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.271674] pci 0000:00:1b.0: reg 0x10: [mem 0xf0a00000-0xf0a03fff 64bit]
[    0.271788] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.271899] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.272011] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.272081] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.272129] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.272241] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.272309] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.272360] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    0.272471] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.272540] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.272591] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.272702] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.272772] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.272820] pci 0000:00:1c.5: [8086:3b4c] type 01 class 0x060400
[    0.272931] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.272998] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.273054] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.273080] pci 0000:00:1d.0: reg 0x10: [mem 0xf0a06400-0xf0a067ff]
[    0.273194] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.273270] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.273318] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.273446] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.273495] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.273703] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.273737] pci 0000:00:1f.2: reg 0x10: [io  0x1818-0x181f]
[    0.273748] pci 0000:00:1f.2: reg 0x14: [io  0x180c-0x180f]
[    0.273759] pci 0000:00:1f.2: reg 0x18: [io  0x1810-0x1817]
[    0.273771] pci 0000:00:1f.2: reg 0x1c: [io  0x1808-0x180b]
[    0.273782] pci 0000:00:1f.2: reg 0x20: [io  0x1820-0x183f]
[    0.273793] pci 0000:00:1f.2: reg 0x24: [mem 0xf0a05000-0xf0a057ff]
[    0.273865] pci 0000:00:1f.2: PME# supported from D3hot
[    0.273971] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.273994] pci 0000:00:1f.3: reg 0x10: [mem 0xf0a06800-0xf0a068ff 64bit]
[    0.274024] pci 0000:00:1f.3: reg 0x20: [io  0x1840-0x185f]
[    0.274152] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.274181] pci 0000:00:1f.6: reg 0x10: [mem 0xf0a04000-0xf0a04fff 64bit]
[    0.274440] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.274674] pci 0000:03:00.0: [8086:422c] type 00 class 0x028000
[    0.274743] pci 0000:03:00.0: reg 0x10: [mem 0xf0500000-0xf0501fff 64bit]
[    0.275489] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.275570] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.281827] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.281835] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.281929] pci 0000:00:1c.3: PCI bridge to [bus 04-05]
[    0.281934] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.281939] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.281947] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.282054] pci 0000:06:00.0: [1180:e822] type 00 class 0x080500
[    0.282076] pci 0000:06:00.0: MMC controller base frequency changed to 50Mhz.
[    0.282099] pci 0000:06:00.0: reg 0x10: [mem 0xf0600000-0xf06000ff]
[    0.282283] pci 0000:06:00.0: supports D1 D2
[    0.282285] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.282321] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.282383] pci 0000:06:00.1: [1180:e230] type 00 class 0x088000
[    0.282410] pci 0000:06:00.1: reg 0x10: [mem 0xf0700800-0xf07008ff]
[    0.282582] pci 0000:06:00.1: supports D1 D2
[    0.282584] pci 0000:06:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.282673] pci 0000:06:00.3: [1180:e832] type 00 class 0x0c0010
[    0.282701] pci 0000:06:00.3: reg 0x10: [mem 0xf0700000-0xf07007ff]
[    0.282873] pci 0000:06:00.3: supports D1 D2
[    0.282875] pci 0000:06:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.289785] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.289796] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.289805] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf07fffff]
[    0.289818] pci 0000:00:1c.4:   bridge window [mem 0xf0e00000-0xf0ffffff 64bit pref]
[    0.289925] pci 0000:08:00.0: [10ec:8168] type 00 class 0x020000
[    0.289946] pci 0000:08:00.0: reg 0x10: [io  0x4000-0x40ff]
[    0.289974] pci 0000:08:00.0: reg 0x18: [mem 0xf0b04000-0xf0b04fff 64bit pref]
[    0.289994] pci 0000:08:00.0: reg 0x20: [mem 0xf0b00000-0xf0b03fff 64bit pref]
[    0.290006] pci 0000:08:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.290091] pci 0000:08:00.0: supports D1 D2
[    0.290093] pci 0000:08:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.290129] pci 0000:08:00.0: System wakeup disabled by ACPI
[    0.297765] pci 0000:00:1c.5: PCI bridge to [bus 08]
[    0.297775] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.297793] pci 0000:00:1c.5:   bridge window [mem 0xf0b00000-0xf0bfffff 64bit pref]
[    0.297899] pci 0000:00:1e.0: PCI bridge to [bus 09] (subtractive decode)
[    0.297913] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.297915] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.297917] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.297919] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
[    0.297921] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
[    0.297923] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff window] (subtractive decode)
[    0.297925] pci 0000:00:1e.0:   bridge window [mem 0xa0000000-0xdfffffff window] (subtractive decode)
[    0.297927] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff window] (subtractive decode)
[    0.298450] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.298507] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.298561] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.298615] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.298669] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.298723] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.298777] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.298832] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.299749] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.299754] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.299759] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.299835] PCI host bridge to bus 0000:ff
[    0.299838] pci_bus 0000:ff: root bus resource [bus ff]
[    0.299844] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.299897] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.299954] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.300004] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.300053] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.300102] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.300291] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.300369] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.300517] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.300520] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.300525] vgaarb: loaded
[    0.300526] vgaarb: bridge control possible 0000:00:02.0
[    0.300793] SCSI subsystem initialized
[    0.300843] libata version 3.00 loaded.
[    0.300871] ACPI: bus type USB registered
[    0.300896] usbcore: registered new interface driver usbfs
[    0.300905] usbcore: registered new interface driver hub
[    0.300923] usbcore: registered new device driver usb
[    0.301075] PCI: Using ACPI for IRQ routing
[    0.310947] PCI: pci_cache_line_size set to 64 bytes
[    0.311073] e820: reserve RAM buffer [mem 0x0009c400-0x0009ffff]
[    0.311075] e820: reserve RAM buffer [mem 0x9b27c000-0x9bffffff]
[    0.311077] e820: reserve RAM buffer [mem 0x9b3e6000-0x9bffffff]
[    0.311080] e820: reserve RAM buffer [mem 0x9b46f000-0x9bffffff]
[    0.311082] e820: reserve RAM buffer [mem 0x9b717000-0x9bffffff]
[    0.311084] e820: reserve RAM buffer [mem 0x9b77e000-0x9bffffff]
[    0.311085] e820: reserve RAM buffer [mem 0x9b7e2000-0x9bffffff]
[    0.311087] e820: reserve RAM buffer [mem 0x9b800000-0x9bffffff]
[    0.311228] NetLabel: Initializing
[    0.311230] NetLabel:  domain hash size = 128
[    0.311231] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.311246] NetLabel:  unlabeled traffic allowed by default
[    0.311342] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.311348] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.313393] Switched to clocksource hpet
[    0.319823] AppArmor: AppArmor Filesystem Enabled
[    0.319920] pnp: PnP ACPI init
[    0.320139] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.320142] system 00:00: [io  0x0500-0x050f] has been reserved
[    0.320144] system 00:00: [io  0x0600-0x0603] has been reserved
[    0.320147] system 00:00: [io  0xffff] has been reserved
[    0.320149] system 00:00: [io  0x0400-0x047f] could not be reserved
[    0.320151] system 00:00: [io  0x1180-0x11ff] has been reserved
[    0.320154] system 00:00: [io  0x164e-0x164f] has been reserved
[    0.320156] system 00:00: [io  0xfe00] has been reserved
[    0.320160] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.320211] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.320253] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.320282] pnp 00:03: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.320586] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.320589] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.320592] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.320594] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.320596] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.320599] system 00:04: [mem 0xfeaff000-0xfeafffff] has been reserved
[    0.320601] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.320603] system 00:04: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.320605] system 00:04: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.320608] system 00:04: [mem 0xff000000-0xffffffff] has been reserved
[    0.320610] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.320613] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.321449] pnp: PnP ACPI: found 5 devices
[    0.328511] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.328516] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.328518] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.328529] pci 0000:00:1c.1: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[    0.328532] pci 0000:00:1c.1: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[    0.328561] pci 0000:00:1c.5: bridge window [mem 0x00100000-0x001fffff] to [bus 08] add_size 400000
[    0.328578] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.328580] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.328582] pci 0000:00:1c.1: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.328584] pci 0000:00:1c.5: res[14]=[mem 0x00100000-0x001fffff] get_res_add_size add_size 400000
[    0.328587] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.328589] pci 0000:00:1c.1: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.328596] pci 0000:00:1c.0: BAR 14: assigned [mem 0xa0000000-0xa01fffff]
[    0.328602] pci 0000:00:1c.0: BAR 15: assigned [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.328608] pci 0000:00:1c.1: BAR 15: assigned [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.328611] pci 0000:00:1c.5: BAR 14: assigned [mem 0xa0600000-0xa0afffff]
[    0.328614] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.328617] pci 0000:00:1c.1: BAR 13: assigned [io  0x6000-0x6fff]
[    0.328621] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.328625] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.328631] pci 0000:00:1c.0:   bridge window [mem 0xa0000000-0xa01fffff]
[    0.328636] pci 0000:00:1c.0:   bridge window [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.328644] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.328648] pci 0000:00:1c.1:   bridge window [io  0x6000-0x6fff]
[    0.328654] pci 0000:00:1c.1:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.328659] pci 0000:00:1c.1:   bridge window [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.328667] pci 0000:00:1c.3: PCI bridge to [bus 04-05]
[    0.328671] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.328677] pci 0000:00:1c.3:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.328682] pci 0000:00:1c.3:   bridge window [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.328690] pci 0000:00:1c.4: PCI bridge to [bus 06-07]
[    0.328694] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.328700] pci 0000:00:1c.4:   bridge window [mem 0xf0600000-0xf07fffff]
[    0.328706] pci 0000:00:1c.4:   bridge window [mem 0xf0e00000-0xf0ffffff 64bit pref]
[    0.328715] pci 0000:08:00.0: BAR 6: assigned [mem 0xa0600000-0xa061ffff pref]
[    0.328717] pci 0000:00:1c.5: PCI bridge to [bus 08]
[    0.328721] pci 0000:00:1c.5:   bridge window [io  0x4000-0x4fff]
[    0.328727] pci 0000:00:1c.5:   bridge window [mem 0xa0600000-0xa0afffff]
[    0.328732] pci 0000:00:1c.5:   bridge window [mem 0xf0b00000-0xf0bfffff 64bit pref]
[    0.328740] pci 0000:00:1e.0: PCI bridge to [bus 09]
[    0.328756] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.328758] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.328760] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.328762] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff window]
[    0.328764] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff window]
[    0.328766] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff window]
[    0.328768] pci_bus 0000:00: resource 10 [mem 0xa0000000-0xdfffffff window]
[    0.328770] pci_bus 0000:00: resource 11 [mem 0xf0000000-0xfebfffff window]
[    0.328773] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.328775] pci_bus 0000:02: resource 1 [mem 0xa0000000-0xa01fffff]
[    0.328777] pci_bus 0000:02: resource 2 [mem 0xa0200000-0xa03fffff 64bit pref]
[    0.328779] pci_bus 0000:03: resource 0 [io  0x6000-0x6fff]
[    0.328781] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.328783] pci_bus 0000:03: resource 2 [mem 0xa0400000-0xa05fffff 64bit pref]
[    0.328785] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.328787] pci_bus 0000:04: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.328789] pci_bus 0000:04: resource 2 [mem 0xf0c00000-0xf0dfffff 64bit pref]
[    0.328791] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
[    0.328793] pci_bus 0000:06: resource 1 [mem 0xf0600000-0xf07fffff]
[    0.328795] pci_bus 0000:06: resource 2 [mem 0xf0e00000-0xf0ffffff 64bit pref]
[    0.328797] pci_bus 0000:08: resource 0 [io  0x4000-0x4fff]
[    0.328799] pci_bus 0000:08: resource 1 [mem 0xa0600000-0xa0afffff]
[    0.328801] pci_bus 0000:08: resource 2 [mem 0xf0b00000-0xf0bfffff 64bit pref]
[    0.328803] pci_bus 0000:09: resource 4 [io  0x0000-0x0cf7 window]
[    0.328805] pci_bus 0000:09: resource 5 [io  0x0d00-0xffff window]
[    0.328807] pci_bus 0000:09: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.328809] pci_bus 0000:09: resource 7 [mem 0x000d4000-0x000d7fff window]
[    0.328811] pci_bus 0000:09: resource 8 [mem 0x000d8000-0x000dbfff window]
[    0.328813] pci_bus 0000:09: resource 9 [mem 0x000dc000-0x000dffff window]
[    0.328815] pci_bus 0000:09: resource 10 [mem 0xa0000000-0xdfffffff window]
[    0.328817] pci_bus 0000:09: resource 11 [mem 0xf0000000-0xfebfffff window]
[    0.328857] NET: Registered protocol family 2
[    0.329066] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.329194] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.329360] TCP: Hash tables configured (established 32768 bind 32768)
[    0.329392] TCP: reno registered
[    0.329413] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.329448] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.329522] NET: Registered protocol family 1
[    0.329539] pci 0000:00:02.0: Video device with shadowed ROM
[    0.330092] PCI: CLS 64 bytes, default 64
[    0.330163] Trying to unpack rootfs image as initramfs...
[    0.711283] Freeing initrd memory: 19752K (ffff88003595c000 - ffff880036ca6000)
[    0.711315] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.711318] software IO TLB [mem 0x9727c000-0x9b27c000] (64MB) mapped at [ffff88009727c000-ffff88009b27bfff]
[    0.711373] Simple Boot Flag at 0x36 set to 0x1
[    0.711638] microcode: CPU0 sig=0x20652, pf=0x10, revision=0xe
[    0.711648] microcode: CPU1 sig=0x20652, pf=0x10, revision=0xe
[    0.711653] microcode: CPU2 sig=0x20652, pf=0x10, revision=0xe
[    0.711660] microcode: CPU3 sig=0x20652, pf=0x10, revision=0xe
[    0.711741] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.711772] Scanning for low memory corruption every 60 seconds
[    0.712194] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.712218] Initialise system trusted keyring
[    0.712244] audit: initializing netlink subsys (disabled)
[    0.712270] audit: type=2000 audit(1433038682.596:1): initialized
[    0.712628] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.714391] zpool: loaded
[    0.714393] zbud: loaded
[    0.714586] VFS: Disk quotas dquot_6.5.2
[    0.714627] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.715179] fuse init (API version 7.23)
[    0.715341] Key type big_key registered
[    0.715982] Key type asymmetric registered
[    0.715987] Asymmetric key parser 'x509' registered
[    0.716032] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 251)
[    0.716098] io scheduler noop registered
[    0.716103] io scheduler deadline registered (default)
[    0.716140] io scheduler cfq registered
[    0.717086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.717105] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.717140] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.717142] vesafb: scrolling: redraw
[    0.717144] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.717166] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc90010780000, using 3072k, total 3072k
[    0.843724] Console: switching to colour frame buffer device 128x48
[    0.970239] fb0: VESA VGA frame buffer device
[    0.970260] intel_idle: MWAIT substates: 0x1120
[    0.970262] intel_idle: v0.4 model 0x25
[    0.970263] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.970536] ACPI: AC Adapter [ADP1] (on-line)
[    0.970638] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.970643] ACPI: Power Button [PWRB]
[    0.970684] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.970687] ACPI: Sleep Button [SLPB]
[    0.970728] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.971480] ACPI: Lid Switch [LID0]
[    0.971531] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.971534] ACPI: Power Button [PWRF]
[    0.972428] thermal LNXTHERM:00: registered as thermal_zone0
[    0.972431] ACPI: Thermal Zone [TZ00] (27 C)
[    0.972753] thermal LNXTHERM:01: registered as thermal_zone1
[    0.972755] ACPI: Thermal Zone [TZ01] (0 C)
[    0.972788] GHES: HEST is not enabled!
[    0.972909] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.982005] Linux agpgart interface v0.103
[    0.982209] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    0.982336] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    0.982897] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    0.983095] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.988108] ACPI: Battery Slot [BAT0] (battery present)
[    0.988804] brd: module loaded
[    0.991565] loop: module loaded
[    0.992103] libphy: Fixed MDIO Bus: probed
[    0.992113] tun: Universal TUN/TAP device driver, 1.6
[    0.992116] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.992250] PPP generic driver version 2.4.2
[    0.992458] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.992471] ehci-pci: EHCI PCI platform driver
[    0.992828] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.992844] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.992870] ehci-pci 0000:00:1a.0: debug port 2
[    0.996907] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.996949] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf0a06000
[    1.005594] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.005716] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.005722] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.005727] usb usb1: Product: EHCI Host Controller
[    1.005732] usb usb1: Manufacturer: Linux 4.0.3-040003-generic ehci_hcd
[    1.005736] usb usb1: SerialNumber: 0000:00:1a.0
[    1.006111] hub 1-0:1.0: USB hub found
[    1.006128] hub 1-0:1.0: 3 ports detected
[    1.006695] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.006710] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.006733] ehci-pci 0000:00:1d.0: debug port 2
[    1.010781] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.010809] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0a06400
[    1.021587] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.021673] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.021678] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.021683] usb usb2: Product: EHCI Host Controller
[    1.021687] usb usb2: Manufacturer: Linux 4.0.3-040003-generic ehci_hcd
[    1.021692] usb usb2: SerialNumber: 0000:00:1d.0
[    1.022054] hub 2-0:1.0: USB hub found
[    1.022070] hub 2-0:1.0: 3 ports detected
[    1.022353] ehci-platform: EHCI generic platform driver
[    1.022380] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.022393] ohci-pci: OHCI PCI platform driver
[    1.022425] ohci-platform: OHCI generic platform driver
[    1.022448] uhci_hcd: USB Universal Host Controller Interface driver
[    1.022574] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.030714] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.030720] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.031298] mousedev: PS/2 mouse device common for all mice
[    1.031872] rtc_cmos 00:01: RTC can wake from S4
[    1.032051] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.032085] rtc_cmos 00:01: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.032106] i2c /dev entries driver
[    1.032174] device-mapper: uevent: version 1.0.3
[    1.032280] device-mapper: ioctl: 4.30.0-ioctl (2014-12-22) initialised: dm-devel@redhat.com
[    1.032302] ledtrig-cpu: registered to indicate activity on CPUs
[    1.032531] PCCT header not found.
[    1.032653] TCP: cubic registered
[    1.032773] NET: Registered protocol family 10
[    1.033022] NET: Registered protocol family 17
[    1.033038] Key type dns_resolver registered
[    1.033488] Loading compiled-in X.509 certificates
[    1.034518] Loaded X.509 cert 'Magrathea: Glacier signing key: e1c36deb3cdc4da7ed2de308728a46a50ab6d32b'
[    1.034537] registered taskstats version 1
[    1.037597] Key type trusted registered
[    1.037755] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.047225] Key type encrypted registered
[    1.047242] AppArmor: AppArmor sha1 policy hashing enabled
[    1.047250] ima: No TPM chip found, activating TPM-bypass!
[    1.047293] evm: HMAC attrs: 0x1
[    1.048236]   Magic number: 15:802:309
[    1.048295] tty tty38: hash matches
[    1.048445] rtc_cmos 00:01: setting system clock to 2015-05-31 02:18:03 UTC (1433038683)
[    1.049594] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.049596] EDD information not available.
[    1.049716] PM: Hibernation image not present or could not be loaded.
[    1.050191] Freeing unused kernel memory: 1420K (ffffffff81d1e000 - ffffffff81e81000)
[    1.050194] Write protecting the kernel read-only data: 12288k
[    1.050451] Freeing unused kernel memory: 32K (ffff8800017f8000 - ffff880001800000)
[    1.050548] Freeing unused kernel memory: 176K (ffff880001bd4000 - ffff880001c00000)
[    1.062696] random: systemd-udevd urandom read with 5 bits of entropy available
[    1.089106] sdhci: Secure Digital Host Controller Interface driver
[    1.089110] sdhci: Copyright(c) Pierre Ossman
[    1.091469] sdhci-pci 0000:06:00.0: SDHCI controller found [1180:e822] (rev 1)
[    1.092638] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.092685] sdhci-pci 0000:06:00.0: No vmmc regulator found
[    1.092688] sdhci-pci 0000:06:00.0: No vqmmc regulator found
[    1.092850] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.092861] r8169 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.093333] r8169 0000:08:00.0 eth0: RTL8168d/8111d at 0xffffc9001076c000, b8:ac:6f:70:c4:2d, XID 081000c0 IRQ 24
[    1.093338] r8169 0000:08:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.093694] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.095048] sdhci-pci 0000:06:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.096061] mmc0: SDHCI controller on PCI [0000:06:00.0] using DMA
[    1.097832] ahci 0000:00:1f.2: version 3.0
[    1.098239] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.098293] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    1.098298] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems sxs apst 
[    1.114497] scsi host0: ahci
[    1.114714] scsi host1: ahci
[    1.114911] scsi host2: ahci
[    1.115117] scsi host3: ahci
[    1.115303] scsi host4: ahci
[    1.115391] ata1: SATA max UDMA/133 abar m2048@0xf0a05000 port 0xf0a05100 irq 25
[    1.115396] ata2: SATA max UDMA/133 abar m2048@0xf0a05000 port 0xf0a05180 irq 25
[    1.115398] ata3: DUMMY
[    1.115400] ata4: DUMMY
[    1.115404] ata5: SATA max UDMA/133 abar m2048@0xf0a05000 port 0xf0a05300 irq 25
[    1.149706] firewire_ohci 0000:06:00.3: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.208798] mmc0: new high speed SD card at address f3d3
[    1.211268] Driver 'mmcblk' needs updating - please use bus_type methods
[    1.211413] mmcblk0: mmc0:f3d3 SD02G 1.83 GiB 
[    1.212436]  mmcblk0: p1
[    1.317739] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.333723] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.433816] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.450437] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.450442] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.450853] hub 1-1:1.0: USB hub found
[    1.451044] hub 1-1:1.0: 6 ports detected
[    1.466539] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.466545] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.467008] hub 2-1:1.0: USB hub found
[    1.467156] hub 2-1:1.0: 8 ports detected
[    1.479296] ata1.00: ATA-8: TOSHIBA MK5056GSY, LH003D, max UDMA/100
[    1.479301] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.480575] ata1.00: configured for UDMA/100
[    1.481000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK5056GS 3D   PQ: 0 ANSI: 5
[    1.481531] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.481571] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.481635] sd 0:0:0:0: [sda] Write Protect is off
[    1.481641] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.481704] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.553574]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.554603] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.650082] firewire_core 0000:06:00.3: created device fw0: GUID 344fc0002b502a61, S400
[    1.709847] tsc: Refined TSC clocksource calibration: 2260.999 MHz
[    1.722045] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.801840] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.820882] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-T633C, D800, max UDMA/100
[    1.820892] ata2.00: applying bridge limits
[    1.839297] ata2.00: configured for UDMA/100
[    1.842298] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-T633C D800 PQ: 0 ANSI: 5
[    1.852830] psmouse serio1: synaptics: queried max coordinates: x [..5836], y [..4908]
[    1.863597] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.863605] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.863844] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.863931] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.913920] usb 1-1.4: New USB device found, idVendor=0c45, idProduct=6417
[    1.913928] usb 1-1.4: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    1.913934] usb 1-1.4: Product: Laptop_Integrated_Webcam_2M
[    1.913938] usb 1-1.4: Manufacturer: CN07RGXF7248704M06BDA01
[    1.922449] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000, board id: 0, fw id: 552693
[    1.967093] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.181924] ata5: SATA link down (SStatus 0 SControl 300)
[    2.665969] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.710284] Switched to clocksource tsc
[    3.300335] random: nonblocking pool is initialized
[    3.947171] systemd[1]: Inserted module 'autofs4'
[    4.089607] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    4.089776] systemd[1]: Detected architecture x86-64.
[    4.104295] systemd[1]: Set hostname to <chris-Studio-1558>.
[    6.119631] systemd[1]: Found ordering cycle on firestarter.service/start
[    6.119638] systemd[1]: Found dependency on network-online.target/start
[    6.119641] systemd[1]: Found dependency on network.target/start
[    6.119644] systemd[1]: Found dependency on NetworkManager.service/start
[    6.119646] systemd[1]: Found dependency on basic.target/start
[    6.119649] systemd[1]: Found dependency on sockets.target/start
[    6.119651] systemd[1]: Found dependency on dbus.socket/start
[    6.119654] systemd[1]: Found dependency on sysinit.target/start
[    6.119656] systemd[1]: Found dependency on firestarter.service/start
[    6.119659] systemd[1]: Breaking ordering cycle by deleting job network-online.target/start
[    6.119662] systemd[1]: Job network-online.target/start deleted to break ordering cycle starting with firestarter.service/start
[    6.122930] systemd[1]: Created slice Root Slice.
[    6.122943] systemd[1]: Starting Root Slice.
[    6.122977] systemd[1]: Listening on Delayed Shutdown Socket.
[    6.122986] systemd[1]: Starting Delayed Shutdown Socket.
[    6.123091] systemd[1]: Created slice System Slice.
[    6.123108] systemd[1]: Starting System Slice.
[    6.123726] systemd[1]: Starting Increase datagram queue length...
[    6.123784] systemd[1]: Listening on udev Control Socket.
[    6.123799] systemd[1]: Starting udev Control Socket.
[    6.123832] systemd[1]: Reached target Remote File Systems (Pre).
[    6.123845] systemd[1]: Starting Remote File Systems (Pre).
[    6.123916] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    6.123926] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    6.123984] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.123994] systemd[1]: Starting Journal Socket (/dev/log).
[    6.124092] systemd[1]: Created slice User and Session Slice.
[    6.124102] systemd[1]: Starting User and Session Slice.
[    6.124135] systemd[1]: Listening on fsck to fsckd communication Socket.
[    6.124149] systemd[1]: Starting fsck to fsckd communication Socket.
[    6.124361] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.124375] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[    6.124415] systemd[1]: Listening on udev Kernel Socket.
[    6.124424] systemd[1]: Starting udev Kernel Socket.
[    6.124529] systemd[1]: Created slice system-getty.slice.
[    6.124539] systemd[1]: Starting system-getty.slice.
[    6.124561] systemd[1]: Reached target Encrypted Volumes.
[    6.124569] systemd[1]: Starting Encrypted Volumes.
[    6.124613] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.124622] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    6.124636] systemd[1]: Reached target Slices.
[    6.124643] systemd[1]: Starting Slices.
[    6.124677] systemd[1]: Listening on Journal Audit Socket.
[    6.124686] systemd[1]: Starting Journal Audit Socket.
[    6.124742] systemd[1]: Listening on Journal Socket.
[    6.124759] systemd[1]: Starting Journal Socket.
[    6.125296] systemd[1]: Starting Uncomplicated firewall...
[    6.125897] systemd[1]: Mounting POSIX Message Queue File System...
[    6.310397] systemd[1]: Started Set Up Additional Binary Formats.
[    6.311097] systemd[1]: Mounting Huge Pages File System...
[    6.311725] systemd[1]: Starting Nameserver information manager...
[    6.312587] systemd[1]: Started Braille Device Support.
[    6.312799] systemd[1]: Starting Braille Device Support...
[    6.313411] systemd[1]: Starting Setup Virtual Console...
[    6.314058] systemd[1]: Mounting Debug File System...
[    6.314910] systemd[1]: Starting LSB: controls configuration of serial ports...
[    6.436806] systemd[1]: Starting Load Kernel Modules...
[    6.437492] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.438125] systemd[1]: Starting udev Coldplug all Devices...
[    6.438772] systemd[1]: Started Read required files in advance.
[    6.438869] systemd[1]: Starting Read required files in advance...
[    6.439940] systemd[1]: Started Setup Virtual Console.
[    6.678997] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    6.679880] systemd[1]: Starting Create Static Device Nodes in /dev...
[    6.733118] systemd[1]: Started udev Coldplug all Devices.
[    6.734004] systemd[1]: Starting udev Wait for Complete Device Initialization...
[    6.794642] systemd[1]: Started Increase datagram queue length.
[    6.797795] systemd[1]: Listening on Syslog Socket.
[    6.797840] systemd[1]: Starting Syslog Socket.
[    6.798454] systemd[1]: Starting Journal Service...
[    6.820821] systemd[1]: Started Uncomplicated firewall.
[    6.830197] systemd[1]: Mounted POSIX Message Queue File System.
[    6.830244] systemd[1]: Mounted Huge Pages File System.
[    6.830269] systemd[1]: Mounted Debug File System.
[    6.977592] systemd[1]: Started Nameserver information manager.
[    7.418625] systemd[1]: Started Journal Service.
[    7.859765] lp: driver loaded but no devices found
[    7.905189] ppdev: user-space parallel port driver
[    8.296302] cfg80211: Calling CRDA to update world regulatory domain
[    8.516731] Intel(R) Wireless WiFi driver for Linux
[    8.516734] Copyright(c) 2003- 2014 Intel Corporation
[    8.516938] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    8.725172] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[    8.808382] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[    8.969183] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[    9.699346] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    9.699351] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    9.699353] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    9.699356] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    9.699471] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    9.832792] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   10.988691] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20150204/utaddress-258)
[   10.988702] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.988707] ACPI Warning: SystemIO range 0x00000000000011c0-0x00000000000011cf conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20150204/utaddress-258)
[   10.988712] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.988714] ACPI Warning: SystemIO range 0x00000000000011b0-0x00000000000011bf conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20150204/utaddress-258)
[   10.988719] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.988721] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011e3 (\GPIO) (20150204/utaddress-258)
[   10.988725] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.988727] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.033114] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.375208] wmi: Mapper loaded
[   11.378314] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   11.378587] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   11.380167] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   11.594572] [drm] Initialized drm 1.1.0 20060810
[   11.748806] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   11.753415] [drm] Memory usable by graphics device = 2048M
[   11.753421] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[   11.753423] fb: switching to inteldrmfb from VESA VGA
[   11.753451] Console: switching to colour dummy device 80x25
[   11.753540] [drm] Replacing VGA console driver
[   11.780147] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   11.780153] [drm] Driver supports precise vblank timestamp query.
[   11.780258] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.798645] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   11.799566] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.799624] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   11.800057] acpi device:05: registered as cooling_device6
[   11.800148] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   11.800400] [drm] Initialized i915 1.6.0 20150130 for 0000:00:02.0 on minor 0
[   11.814152] fbcon: inteldrmfb (fb0) is primary device
[   12.100606] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.180422] sound hdaudioC0D0: autoconfig for 92HD73C1X5: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   12.180423] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.180425] sound hdaudioC0D0:    hp_outs=2 (0xf/0xa/0x0/0x0/0x0)
[   12.180426] sound hdaudioC0D0:    mono: mono_out=0x0
[   12.180427] sound hdaudioC0D0:    inputs:
[   12.180429] sound hdaudioC0D0:      Internal Mic=0x13
[   12.180430] sound hdaudioC0D0:      Mic=0xe
[   12.311794] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   12.311915] input: HDA Intel MID Headphone Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   12.312024] input: HDA Intel MID Headphone Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.312151] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.368244] input: Dell WMI hotkeys as /devices/virtual/input/input12
[   12.573288] Console: switching to colour frame buffer device 170x48
[   12.576410] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.576411] i915 0000:00:02.0: registered panic notifier
[   12.581678] cfg80211: Calling CRDA to update world regulatory domain
[   13.060311] media: Linux media interface: v0.10
[   13.098840] Linux video capture interface: v2.00
[   13.346135] Adding 3984380k swap on /dev/sda5.  Priority:-1 extents:1 across:3984380k FS
[   13.440569] cfg80211: World regulatory domain updated:
[   13.440574] cfg80211:  DFS Master region: unset
[   13.440575] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.440579] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.440581] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.440583] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.440585] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.440587] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.440599] cfg80211: Calling CRDA for country: US
[   13.446529] cfg80211: Regulatory domain changed to country: US
[   13.446534] cfg80211:  DFS Master region: FCC
[   13.446535] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.446538] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[   13.446540] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[   13.446542] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   13.446544] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   13.446546] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   13.446548] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[   13.446550] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   13.524381] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:6417)
[   13.533673] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input13
[   13.533776] usbcore: registered new interface driver uvcvideo
[   13.533778] USB Video Class driver (1.1.1)
[   15.090412] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   15.321045] systemd-journald[243]: Received request to flush runtime journal from PID 1
[   16.531715] audit: type=1400 audit(1433038698.977:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=517 comm="apparmor_parser"
[   16.531724] audit: type=1400 audit(1433038698.977:3): apparmor="STATUS" operation="profile_load" name="chromium" pid=517 comm="apparmor_parser"
[   16.576099] audit: type=1400 audit(1433038699.017:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=517 comm="apparmor_parser"
[   16.576107] audit: type=1400 audit(1433038699.017:5): apparmor="STATUS" operation="profile_load" name="chromium" pid=517 comm="apparmor_parser"
[   16.581251] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   16.587055] audit: type=1400 audit(1433038699.029:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=517 comm="apparmor_parser"
[   16.587064] audit: type=1400 audit(1433038699.029:7): apparmor="STATUS" operation="profile_load" name="chromium" pid=517 comm="apparmor_parser"
[   16.762592] audit: type=1400 audit(1433038699.205:8): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=517 comm="apparmor_parser"
[   16.762599] audit: type=1400 audit(1433038699.205:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=517 comm="apparmor_parser"
[   16.762603] audit: type=1400 audit(1433038699.205:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=517 comm="apparmor_parser"
[   16.762608] audit: type=1400 audit(1433038699.205:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=517 comm="apparmor_parser"
[   27.540385] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   27.544173] vboxdrv: Found 4 processor cores.
[   27.544682] vboxdrv: fAsync=0 offMin=0x21d offMax=0x2459
[   27.544820] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.544822] vboxdrv: Successfully loaded version 4.1.26 (interface 0x00190000).
[   29.893527] r8169 0000:08:00.0 eth0: link down
[   68.207569] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
```

---

### Post by chili555 on 2015-05-31
> [   27.540385] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
        [   27.544173] vboxdrv: Found 4 processor cores.
        [   27.544682] vboxdrv: fAsync=0 offMin=0x21d offMax=0x2459
        [   27.544820] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
        [   27.544822] vboxdrv: Successfully loaded version 4.1.26 (interface 0x00190000).Is this a virtual machine? Guest or host??

---

### Post by madaxeslasher on 2015-05-31
No.. I have oracle vm ware installed... but I have had it on there since I first installed ubuntu

---

### Post by chili555 on 2015-06-02
Please be certain that at the Network Manager icon, Networking and WiFi are both checked off as enabled.

We have tried just about everything in the playbook except a newer driver.  Please download this to your desktop: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.0.1/backports-4.0.1-1.tar.gz](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.0.1/backports-4.0.1-1.tar.gz) Right-click it and select 'Extract here.' Now, in a terminal:```
sudo apt-get install linux-headers-generic build-essential
```If one or the other or both is already installed, that's fine, just continue.```
cd ~/Desktop/backports-4.0.1-1
make defconfig-iwlwifi
make
sudo make install
```Reboot and let us know how it's working.

---

### Post by madaxeslasher on 2015-06-18
sorry for the delay... going through a home renovation and havent had the time to do this but im going for it now... there is no longer an option to check "enable wireless" in my network manager

---

### Post by madaxeslasher on 2015-06-18
im a sorry to say, that did not work...I dont know what the problem is with this thing any more....  I know I see text during load up after grub that says something about firestarter..Dont know what that is...    i did however save all the info from the terminal during install in case it didnt work and you wanted to see...

```
chris@chris-Studio-1558:~$ sudo apt-get install linux-headers-generic build-essential[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
chris@chris-Studio-1558:~$ cd ~/Desktop/backports-4.0.1-1
chris@chris-Studio-1558:~/Desktop/backports-4.0.1-1$ make defconfig-iwlwifi
Generating local configuration database from kernel ... done.
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o conf.o conf.c
cc -Wall -Wmissing-prototypes -Wstrict-prototypes -O2 -fomit-frame-pointer   -c -o zconf.tab.o zconf.tab.c
In file included from zconf.tab.c:2503:0:
menu.c: In function ‘get_symbol_str’:
menu.c:561:18: warning: ‘jump’ may be used uninitialized in this function [-Wmaybe-uninitialized]
     jump->offset = r->len - 1;
                  ^
menu.c:515:19: note: ‘jump’ was declared here
  struct jump_key *jump;
                   ^
cc   conf.o zconf.tab.o   -o conf
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
chris@chris-Studio-1558:~/Desktop/backports-4.0.1-1$ make
make[5]: 'conf' is up to date.
boolean symbol HWMON tested for 'm'? test forced to 'n'
boolean symbol HWMON tested for 'm'? test forced to 'n'
#
# configuration written to .config
#
Building backport-include/backport/autoconf.h ... done.
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/compat/main.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/compat/compat.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-io.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-drv.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-debug.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-notif-wait.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-eeprom-read.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-eeprom-parse.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-phy-db.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-nvm-parse.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/pcie/drv.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/pcie/rx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/pcie/tx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/pcie/trans.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-1000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-2000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-5000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-6000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-7000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-8000.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwl-devtrace.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwlwifi.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/main.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/rs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/mac80211.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/ucode.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/tx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/lib.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/calib.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/tt.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/sta.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/rx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/power.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/scan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/rxon.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/devices.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/led.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/debugfs.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/fw.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/mac80211.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/nvm.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/ops.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/phy-ctxt.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/mac-ctxt.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/utils.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/rx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/tx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/binding.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/quota.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/sta.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/sf.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/scan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/time-event.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/rs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/power.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/coex.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/coex_legacy.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/tt.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/offloading.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/tdls.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/debugfs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/debugfs-vif.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/led.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/d3.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/main.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/status.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/sta_info.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/wep.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/wpa.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/scan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/offchannel.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/ht.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/agg-tx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/agg-rx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/vht.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/ibss.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/iface.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/rate.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/michael.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/tkip.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/aes_ccm.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/aes_gcm.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/aes_cmac.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/aes_gmac.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/cfg.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/ethtool.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/rx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/spectmgmt.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/tx.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/key.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/util.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/wme.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/event.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/chan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/trace.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/mlme.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/tdls.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/ocb.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/led.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/debugfs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/debugfs_sta.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/debugfs_netdev.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/debugfs_key.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/pm.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/mac80211.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/core.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/sysfs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/radiotap.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/util.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/reg.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/scan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/nl80211.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/mlme.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/ibss.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/sme.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/chan.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/ethtool.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/mesh.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/ap.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/trace.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/ocb.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/debugfs.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/wext-compat.o
  CC [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/wext-sme.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/cfg80211.o
  Building modules, stage 2.
  MODPOST 6 modules
  CC      /home/chris/Desktop/backports-4.0.1-1/compat/compat.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/compat/compat.ko
  CC      /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
  CC      /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwlwifi.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwlwifi.ko
  CC      /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
  CC      /home/chris/Desktop/backports-4.0.1-1/net/mac80211/mac80211.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/net/mac80211/mac80211.ko
  CC      /home/chris/Desktop/backports-4.0.1-1/net/wireless/cfg80211.mod.o
  LD [M]  /home/chris/Desktop/backports-4.0.1-1/net/wireless/cfg80211.ko
chris@chris-Studio-1558:~/Desktop/backports-4.0.1-1$ sudo make install
  Building modules, stage 2.
  MODPOST 6 modules
  INSTALL /home/chris/Desktop/backports-4.0.1-1/compat/compat.ko
Can't read private key
  INSTALL /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
Can't read private key
  INSTALL /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/iwlwifi.ko
Can't read private key
  INSTALL /home/chris/Desktop/backports-4.0.1-1/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
Can't read private key
  INSTALL /home/chris/Desktop/backports-4.0.1-1/net/mac80211/mac80211.ko
Can't read private key
  INSTALL /home/chris/Desktop/backports-4.0.1-1/net/wireless/cfg80211.ko
Can't read private key
  DEPMOD  4.0.3-040003-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Debian GNU/Linux") tag for your distribution to avoid this warning.


Your backported driver modules should be installed now.
Reboot.


chris@chris-Studio-1558:~/Desktop/backports-4.0.1-1$ 



```

i see at the end there it has problems reading "private key"????


i was also able to get a screen shot showing,, or not showing the option to enable wireless..

[https://drive.google.com/file/d/0B1ssTH8sEKElY0VUYld6bno5S2M/view?usp=sharing](https://drive.google.com/file/d/0B1ssTH8sEKElY0VUYld6bno5S2M/view?usp=sharing)




i really appreciate you helping me..

---

### Post by madaxeslasher on 2015-06-18
also.. after running software updater... it says the software on this computer is up to date however, Ubuntu 15.04 is available (you have 14.10)

thats not right because i installed 15.04... it shows it when at login screen,,,, also on "About this computer"  at the very top it says 15.04....


im at wits end

---

