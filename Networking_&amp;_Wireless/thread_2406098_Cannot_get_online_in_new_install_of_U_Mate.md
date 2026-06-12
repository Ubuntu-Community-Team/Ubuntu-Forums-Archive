---
title: "Cannot get online in new install of U Mate"
date: 2018-11-15
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2018-11-15
After reading through several posts in this forum, decided to repost in Newbie. Hope this is OK way to do so?


(Dell XPS 8700 Desktop i7-4790)

---

### Post by TheFu on 2018-11-15
Troubleshooting networking begins by determining where the issue lies.  Some simple tests, run in the correct order, will narrow down what the issue might be quickly.

Step 1 - can you ping the router using the router's IP?
ping 192.168.x.x   # <--- you need to put in the correct IP address for the router. I have no idea what it is.

Step 2 - can you ping a "well-known" public internet IP?
ping 8.8.8.8   # <---- this is the google public DNS

Step 3 - can you lookup google.com using the name? This is a DNS check
ping google.com

Often, things that appear to be networking issues are just DNS issues.  To end users, DNS issues might seem like "all networking is broken", but really it isn't.

So, do those steps in order.  Stop at the first that fails and report back.  If the first one fails, run these 3 commands and post the output using *code tags*:
* ifconfig
* route -n
* sudo lshw -C network

Please.
Also, we need to know exactly which version of Ubuntu you are using.  Desktop or server, and the version number.  Network configuration has changed over time, so how to fix is dependent on the release.

---

### Post by Odyssey1942 on 2018-11-15
I have just installed UM into a SSD which dual boots with Win 10 on a HDD. The install seems to have gone OK for the most part, but I am unable to get online.

I have done all the poking, proding, changing, I can find to try but no cigar.

Can ping router OK from another computer, but not from the problem new install.

from the new install:

output from ifconfig:
enp3s0: flags=4099<UP,BROADCAST,MULTICAST> mtu 1500
        ether XY:AB:XY:AB:XY:AB   txqueuelen 1000 (Ethernet)
        RX packets 0 bytes 0 (0.0 B)
        RX errors  dropped 0 overruns 0 frame 0
        TX packets 0 bytes 0 (0.0 B)
        TX errors  dropped 0 overruns 0 carrier 0 collisions 0

lo: flags=73<UP,LOOPBACK, RUNNING: mtu 65536
        inet 127.0.0.1 netmask 255.0.0.0
        inet6 ::1   prefixlen 128   scopeid 0x10<host>
        loop  txqueuelen 1000   (Local Loopback)
        RX packets 52355 bytes 3197498   (3.1 MB)
        RX errors  dropped 0 overruns 0 frame 0
        TX packets 52355   bytes 3197498   (3.1 MB)
        TX errors  dropped 0 overruns 0 carrier 0 collisions 0

Where is the best place to start to get a wired internet connection established? Thanks

(Dell XPS 8700 i7-4790)

---

### Post by ajgreeny on 2018-11-15
Threads merged.

Please do not create duplicate posts; it is confusing for everybody including you and dilutes the responses you get and your ability to understand answers properly.

---

### Post by Odyssey1942 on 2018-11-15
> Step 1 - can you ping the router using the router's IP? 

NO

```
output from ifconfig:
enp3s0: flags=4099<UP,BROADCAST,MULTICAST> mtu 1500
ether XY:AB:XY:AB:XY:AB txqueuelen 1000 (Ethernet)
RX packets 0 bytes 0 (0.0 B)
RX errors dropped 0 overruns 0 frame 0
TX packets 0 bytes 0 (0.0 B)
TX errors dropped 0 overruns 0 carrier 0 collisions 0

lo: flags=73<UP,LOOPBACK, RUNNING: mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 ::1 prefixlen 128 scopeid 0x10<host>
loop txqueuelen 1000 (Local Loopback)
RX packets 52355 bytes 3197498 (3.1 MB)
RX errors dropped 0 overruns 0 frame 0
TX packets 52355 bytes 3197498 (3.1 MB)
TX errors dropped 0 overruns 0 carrier 0 collisions 0
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

```
sudo lshw -C network
 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: XY:AB:XY:AB:XY:AB
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7100000-f7107fff
```

Bit of a challenge via sneakernet, but hope this is what you need. Apology for the confusion when I "moved" the thread. Nada mas!

---

### Post by TheFu on 2018-11-15
Don't forget to try a different switch port and a different ethernet cable.  Also, do other wired devices work on the cable and switch port that isn't working with this computer?

Assuming that works, 
driver=**r8169**
I'd search for solutions around that driver and the specific card in the machine, RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller.  I remember there being issues with some cards and that driver.

---

### Post by Odyssey1942 on 2018-11-15
Thanks for your quick response. I am replying from the Windows boot on the same dualboot computer, so the connection from the computer to the router/internet is working well.

So it isn't the connection, and I assume it isn't the card and driver, unless the driver needs something for Linux that it doesn't need for Windows.

Does this help narrow down the issue?

Edit: neglected to give Ubuntu info. It is Ubuntu MATE 18.04.1 

found this also:

[https://forums.linuxmint.com/viewtopic.php?t=234367]("https://forums.linuxmint.com/viewtopic.php?t=234367")

---

### Post by TheFu on 2018-11-15
The linux driver has nothing to do with the Windows driver.  

You have this card: RTL8111/8168/8411
But the driver selected is for a r8169.
See the possible problem?  If I google for *RTL8111/8168/8411 ubuntu 18.04* ... there seem to be many issues reported with that card.  I avoid realtek NICs for a number of reasons.

[https://askubuntu.com/questions/1043384/ethernet-not-working-well-in-ubuntu-18-04-on-new-desktop](https://askubuntu.com/questions/1043384/ethernet-not-working-well-in-ubuntu-18-04-on-new-desktop) says that switching to the r8168 driver might be the fix.  You'll need to get some networking on the system (wifi?), then run:

```
sudo apt-get update
sudo apt-get install r8168-dkms
sudo reboot
```
It should work. Be certain to fully patch the system now - 
```
sudo apt upgrade
```

Please let us know if this solves it. If not, someone else should be able to help.

---

### Post by Odyssey1942 on 2018-11-16
Now trying to establish WiFi, but have hit a wall hard!

I put a USB WiFi receiver in and restarted. No automatic connectivity (should the adapter have shown?), so I opened NetWork Connections and clicked on the "+" which opened:

Editing WiFi Connection 1 

and it seems I will need some assistance in selecting the tabs and data points that need to be filled in, AND in finding the necessary information to be supplied. The two that I think seem most relevant are
WiFi tab. and
IPv4 tab

Because I do not have connectivity, I am not posting screen captures, but I assume that anyone who understands this stuff will know which of the boxes need to be filled in, and how to find the data. Or perhaps to guide on a better way to establish WiFi connectivity?

Your assistance is humbly requested. Thanks

---

### Post by Dennis N on 2018-11-16
Comments:

With never-before-used USB adapter, it initially won't connect automatically. If there is no other connection, you probably expect to see a popup message "wireless networks available". In my experience, this will happen as soon as you plug it in and it's detected - no restart necessary. Then, you would have to click on the network panel icon, find the adapter in the "Wireless connections" section, and then "Connect". Then you only need supply the wireless network password. Shouldn't be necessary to edit any network connections, I would think.

Just wondering: Did **r8168-dkms** work for your ethernet?

---

### Post by TheFu on 2018-11-16
> **Dennis N said:**
>  Just wondering: Did **r8168-dkms** work for your ethernet?

Chicken and egg issue. Without networking, the OP can't install anything.

I use wicd-curses to handle wifi connections.  Usually just need to select the SSID and enter the passphrase, but that assumes no 802.11x authentication.

---

### Post by Odyssey1942 on 2018-11-16
Seems like I am going backward here. Dennis mentioned "> you would have to click on the network panel icon and when I plug in the adapter, it does flash a message "WiFi Network Available - Use the NetWork Menu...." 

When I first installed there was an icon in the right hand corner of the upper panel which I somehow managed to remove. Is this the icon that Dennis mentioned, and is it the "Network Menu" of the popup message? 

If so, how do I get it back?

If not, where do I find this "menu'?

I use my wife's UM16.04 often, and there have been a lot of cosmetic changes and relabeling in 18.04 which is really confusing to me.

---

### Post by Dennis N on 2018-11-16
> If so, how do I get it back? If not, where do I find this "menu'?

Looking at my own Ubuntu MATE 18.04, the network icon is in the "Indicator Applet Complete" panel add-on. I can't remove the network icon without removing the whole indicator applet. You can try right-click on panel, and "Add to Panel" > Indicator Applet Complete. 

See attached screenshot showing Network Icon (differs with your icon theme) and the drop-down menu in top-right of panel. I have no wireless adapters here, so it doesn't show that category.

---

### Post by Odyssey1942 on 2018-11-16
Dennis, you nailed it! And that is definitely what was needed, as I am now writing this online on the new UM 18.04 install connected by wifi

Ran the command lines as theFu recommended in post #8, including update. Unfortunately I did not think to try the wired connection before running the update, but the wired connection is still not working at this stage

So I am posting again the steps theFu recommended in post #2.

(The CODE icon has disappeared so will use the QUOTE icon - please advise if this not acceptable as a substitute)

> ping 192.168.1.1
connect: Network is unreachable

> ifconfig
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether XY:AB:XY:AB:XY:AB  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1636  bytes 115102 (115.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1636  bytes 115102 (115.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx00212f30a0d9: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether XY:AB:XY:AB:XY:AB  txqueuelen 1000  (Ethernet)
        RX packets 2599  bytes 1064303 (1.0 MB)
        RX errors 0  dropped 419  overruns 0  frame 0
        TX packets 2065  bytes 424909 (424.9 KB)
        TX errors 0  dropped 1 overruns 0  carrier 0  collisions 0

> oute -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


> udo lshw -C network

  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: XY:AB:XY:AB:XY:AB
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:31 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7100000-f7107fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:11
       logical name: wlx00212f30a0d9
       serial: XY:AB:XY:AB:XY:AB
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

From what I can understand the old driver is still there. Should I rerun all the driver update steps?

Ubuntu release 18.04.1  Kernel Linux 4.15.0-39 generic 86_64  MATE 1.20.1

---

### Post by Dennis N on 2018-11-16
Glad your wireless is working. I hope you can solve the ethernet connectivity as well.

My ethernet adapter is the same as yours, with the same r8169 driver. Aside from the fact that mine works, one  difference I see in the lshw output (not shown here) is my controller is version 15, and yours is 0c. 
```
dmn@Tyana:~$ inxi -n
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp1s0 state: up speed: 1000 Mbps duplex: full

```
I'll defer the driver installation question to someone with networking expertise.

---

### Post by Odyssey1942 on 2018-11-16
Hi Dennis, Thanks for yours. Actually it's the WiFi that is working, not the wired. I'm sure that was just a typo/transposition on your part, but just for the sake of avoiding confusion to subsequent readers, thought it best to mention.

---

### Post by Odyssey1942 on 2018-11-16
Something just occurred to me. Thinking about the earlier post suggesting booting from a bootable USB or DVD into a live version to see if the wired connection worked that way. So now I am even more confused than usual.

The wired connection works fine from a Windows boot, but doesn't from an installed Ubuntu boot. I learned that separate drivers are required for each (and that the linux version appeared to be the issue), although I think that previous to that revelation I was under the assumption that this is something controlled down the stack from the OS.

The above (live version) question raises the question: How could it work in the live Ubuntu version and not in the installed?

---

### Post by TheFu on 2018-11-16
Great getting the wifi working!  Nice to have a backup method.

Need to disable the wifi before trying the wired network.  Always.  Do not leave both active.  Should just be a right-click, disable, wifi.

driver=r8169 is still being used. 
 If the r8168 driver is truly installed, then I'd blacklist that r8169 driver in the /etc/modprobe.d/ directory, but only after the -dkms driver has been installed, as that link suggests.  There are manual ways to unload and reload a different driver, but probably just easier to reboot.

If you want to try the "live" version, then use a Live Boot of Ubuntu.  That can be a flash drive or a CDROM/DVD.  Use the one you used to install the desktop OS and pick the "Try Ubuntu" option.  This is a great skill to have, since it is a way to fix a broke OS.  With a little skill, it would probably be possible to boot off the live-boot, mount the installed OS, use the wired networking, and patch everything, install the needed driver, all sorts of things are possible.  THIS is how I fix my mistakes, boot issues, or hardware failures, but pretty much anything can be fixed in this way.

Drivers are the interface between the OS and the hardware.  Every OS has different drivers.

---

### Post by Odyssey1942 on 2018-11-17
TheFu, thanks for yours. I tried re-running all the steps to replace the driver with no success, and have rebooted several times since we last exchanged messages, but the old driver seems to be dug in.

I apologize for asking, but can you or anyone walk me through the steps to replace the r8169 driver with the r8168 one (I have confirmed that r8168.ko exists, if that is what I should be looking for)? I fully expect that this is going to be command line stuff and the extent of my CLI skills is limited to getting the shell interface open. I can remember ping, ifconfig, and a few others, but I even have to look up how to change directories and everything more complicated.

I have been working on this for over a week and, while I don't want to seem impatient, it's wearing me out, and I sure would like to get it put to bed. Any assistance from anyone with "how to" will be much appreciated. Thanks

---

### Post by Dennis N on 2018-11-17
Here is some information I read about the Realtek chips and controller:

> Installation of the r8168-dkms package will disable the in-kernel r8169
module. To re-enable r8169, the r8168-dkms package must be purged.

This package provides the dkms source code for the r8168 kernel modules.
Kernel source or headers are required to compile these modules.

This driver should only be used for devices not yet supported by the
in-kernel driver r8169. Please see the README.Debian for instructions how
to report bugs against r8169 that made it necessary to use r8168-dkms.

Source: [https://packages.debian.org/sid/r8168-dkms](https://packages.debian.org/sid/r8168-dkms)
also with terminal command:
apt show r8168-dkms 


If installation disables the r8169, sounds like you may not need to do anything additional after the install of the new package?

I read that the r8169 is in driver in the Linux kernel. It works with many different Realtek ethernet controller chips. The driver number is not necessarily the same as the controller chips it can work with. The chip in my computer is actually RTL8111H. I had to look into the motherboard specs to find this.

---

### Post by praseodym on 2018-11-17
Hi,

if wifi works run
```

sudo apt-get install r8168-dkms
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and show the output of
```

lsmod
```

---

### Post by Odyssey1942 on 2018-11-17
Dennis, thanks for yours. Whatever changes which may or may not have been made by the steps I have taken have not had the result of connecting via Ethernet.

What can I look at, and provide the output of, that might help move this stalled process along?

---

### Post by Odyssey1942 on 2018-11-17
fraseodym, sorry I missed yours earlier. The thread had started a page three holding yours while I was still at the bottom of page 2 writing my last post. Here are the outputs you requested:

```
sudo apt-get install r8168-dkms
[sudo] password for  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
r8168-dkms is already the newest version (8.045.08-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

and

```
lsmod
Module                  Size  Used by
binfmt_misc            20480  1
cfg80211              622592  0
r8712u                176128  0
rfcomm                 77824  16
cmac                   16384  1
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
snd_hda_codec_realtek   106496  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
dcdbas                 16384  0
irqbypass              16384  1 kvm
snd_hda_intel          40960  2
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
crct10dif_pclmul       16384  0
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
pcbc                   16384  0
snd_seq_midi           16384  0
btusb                  45056  0
snd_seq_midi_event     16384  1 snd_seq_midi
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
aesni_intel           188416  2
btintel                16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
bluetooth             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
aes_x86_64             20480  1 aesni_intel
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
ecdh_generic           24576  2 bluetooth
joydev                 24576  0
input_leds             16384  0
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_timer              32768  2 snd_seq,snd_pcm
intel_cstate           20480  0
intel_rapl_perf        16384  0
snd                    81920  15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
soundcore              16384  1 snd
mei                    90112  1 mei_me
shpchp                 36864  0
lpc_ich                24576  0
mac_hid                16384  0
sch_fq_codel           20480  3
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
uas                    24576  0
usbhid                 49152  0
usb_storage            69632  1 uas
hid                   118784  2 usbhid,hid_generic
nouveau              1716224  2
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
i2c_algo_bit           16384  1 nouveau
ttm                   106496  1 nouveau
drm_kms_helper        172032  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
i2c_i801               28672  0
r8168                 524288  0
drm                   401408  5 drm_kms_helper,ttm,nouveau
ahci                   36864  2
libahci                32768  1 ahci
bcma                   57344  0
video                  45056  1 nouveau

```

---

### Post by praseodym on 2018-11-17
Are you using an USB wifi dongle? If no unload that driver

```
sudo modprobe -rfv r8712u
```

and load the real driver
```

sudo modprobe -v wl
```

---

### Post by Odyssey1942 on 2018-11-17
Yes I am using a WiFi dongle. Should I take any action, e.g. run any of the above with wifi disconnected and/or dongle removed?

---

### Post by praseodym on 2018-11-18
Remove the dongle and run those commands

---

### Post by Odyssey1942 on 2018-11-18
After: Disconnect from wifi network / turn off enable wifi / restart without dongle:

```
sudo modprobe -v wl
[sudo] password for
modprobe: FATAL: Module wl not found in directory /lib/modules/4.15.0-39-generic
```

```
sudo modprobe -rfv r8712u
(blank i.e.,no report given)
```

Wasn't sure whether you meant just those codes in your previous post or also the ones in  #23, so JIC ran them again

```
sudo apt-get install r8168-dkms
[sudo] password for 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
r8168-dkms is already the newest version (8.045.08-2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

```
lsmod
Module                  Size  Used by
rfcomm                 77824  16
cmac                   16384  1
bnep                   20480  2
nls_iso8859_1          16384  1
snd_hda_codec_hdmi     49152  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             212992  0
kvm                   598016  1 kvm_intel
irqbypass              16384  1 kvm
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_hda_codec_realtek   106496  1
dcdbas                 16384  0
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_seq_midi           16384  0
aesni_intel           188416  2
btusb                  45056  0
snd_seq_midi_event     16384  1 snd_seq_midi
btrtl                  16384  1 btusb
snd_rawmidi            32768  1 snd_seq_midi
btbcm                  16384  1 btusb
aes_x86_64             20480  1 aesni_intel
snd_hda_intel          40960  2
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
btintel                16384  1 btusb
crypto_simd            16384  1 aesni_intel
snd_hda_codec         126976  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
glue_helper            16384  1 aesni_intel
bluetooth             548864  43 btrtl,btintel,btbcm,bnep,btusb,rfcomm
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
snd_hda_core           81920  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
intel_cstate           20480  0
joydev                 24576  0
ecdh_generic           24576  2 bluetooth
intel_rapl_perf        16384  0
input_leds             16384  0
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  15 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
mei_me                 40960  0
soundcore              16384  1 snd
mei                    90112  1 mei_me
shpchp                 36864  0
lpc_ich                24576  0
mac_hid                16384  0
sch_fq_codel           20480  2
parport_pc             36864  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 parport_pc,lp,ppdev
ip_tables              28672  0
x_tables               40960  1 ip_tables
autofs4                40960  2
hid_generic            16384  0
uas                    24576  0
usbhid                 49152  0
usb_storage            69632  1 uas
hid                   118784  2 usbhid,hid_generic
nouveau              1716224  2
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
i2c_algo_bit           16384  1 nouveau
ttm                   106496  1 nouveau
drm_kms_helper        172032  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
r8168                 524288  0
drm                   401408  5 drm_kms_helper,ttm,nouveau
ahci                   36864  2
libahci                32768  1 ahci
i2c_i801               28672  0
bcma                   57344  0
video                  45056  1 nouveau
```

fingers crossed that something in this reveals the problem. 
Thanks

---

### Post by Dennis N on 2018-11-18
Looks like you made progress. After installing r8168, did you go back to network menu on panel and enable wired connection (ethernet)?

---

### Post by Odyssey1942 on 2018-11-18
Some things, which ought to be obvious to me, just go unnoticed. I clicked on the little internet icon on right side of top panel and the "Ethernet Network" is greyed out, so I clicked on "Edit Connections" at the bottom of that list and it brought up the "Network Connections" popup with 

Ethernet
Wired Connection 1   and
Wi-Fi
(name of my home network here)

so I clicked on the Wired Connection 1 which brought up Editing Wired Connection 1 with the following tabs:

-General which already has "Automatically connect to this network when it is available" ticked

-Ethernet which shows an IP # in Device and Default selected in "Wake on LAN", also Ignore under Link negotiation with most everything else blank or greyed out,

-802.1x Security with Use 802.1x security for this connection NOT ticked  (I'm wondiering if this is the correct setting?). Everything else is consequently greyed out

-DCB with nothing selected

-Proxy with nothing selected

-IPv4 Settings: Automatic (DHCP) showing in the "Method" selection (which seems right to me) but everything else is blank

IPv6 Settings: Automatic (DHCP) showing in the "Method" selection [this probably not so important??]

Do I enable ethernet by changing anything in the above, or by another method?

---

### Post by TheFu on 2018-11-18
In post #6, we started trying to get the different ethernet driver loaded.  That appears to have finally happened.

I expected things to "just work" once the correct driver was loaded, assuming the wifi dongle isn't plugged in and the ethernet cable is connected to the router/switch and the other end is connected to the PC. I don't use GUIs to setup networking, so I cannot help with that. Sorry.

In post #2, we asked for troubleshooting information.  We are back to that point now, if the network isn't working.

---

### Post by Odyssey1942 on 2018-11-18
```
ifconfig
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 12:34:56:78:99:87  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 31  base 0x5000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3940  bytes 300279 (300.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3940  bytes 300279 (300.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

```

```
sudo lshw -C network
[sudo] password for robert: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 12:34:56:78:99:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=off broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:31 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7100000-f7107fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@3:11
       logical name: wlx00212f30a0d9
       serial: XY:AB:XY:AB:XY:AB
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u multicast=yes wireless=unassociated

```

I notice that both controllers have a physical id of "0". Is that significant?

---

### Post by TheFu on 2018-11-18
I don't think the physical ID matters.  They are on different PCI channels.

Is the DHCP server working or do you use static IPs?
If the machine never moves, then you can setup a static IP.
[https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux) is a guide.  
For a laptop, DHCP is better, but the DHCP server (probably in the LAN router) has to be working.

---

### Post by Odyssey1942 on 2018-11-18
I don't understand "Is the DHCP server working or do you use static IPs?" Where or what is the DHCP server? Is it provided by my ISP, or is it in my router?

By "never moves" are you thinking of a desktop? It is. It is in my work area upstairs at the moment while I am trying to get it ready to move to my wife's work area downstairs which is on a different lan (downstream from the main router in my office). It is important to us that she be able to connect via ethernet which I (wrongly or rightly, and I would be interested in your opinion on this, view as a more secure connection than wifi. She occasionally does minor banking on her computer for convenience so security is an important consideration.

So it will move, if and when we get the ethernet connection working, but then it will replace her computer and hers will come  back to my work area and I will start the upgrade to UM 18.04.1 on it.

I have a couple of additional questions. One are you suggesting this because you think DHCP is the problem, or simply that a fixed IP routes around the area that might now be interfering with ethernet connectivity?

Two, can one computer have a fixed IP# and all other devices on that lan be configured DHCP?

Finally, what did you see in my last post that prompted the question? Or should I ask do you see the problem that is preventing eth connectivity?

Thanks

---

### Post by TheFu on 2018-11-18
[https://www.grc.com/sn/past/2006.htm](https://www.grc.com/sn/past/2006.htm)
Episode 25-27 is how the internet and LANs work.  

This is basic IPv4 networking.

Assuming the correct driver is loaded, when the system connects without a static IP setup, it will ask the "network" for an IP using DHCP. You can google that term.  If the DHCP server, which is probably your router in a home environment, doesn't answer, then by providing network configuration information, then the the troubleshooting steps would look like what you have.  A DHCP server could be running on any Linux system, but you would definitely need to set it up and for a simple network, having multiple DHCP servers on the same subnet is a terrible idea.

A desktop PC needs to have
* an IP address - something like 192.168.1.100 (but usually different)
* a netmask - almost always 255.255.255.0 in a home LAN.  Sometimes also known as a /24, pronounced "slash-24"
* a default gateway - usually the router - sometimes 192.168.1.1 (but usually different)
* a DNS server, though 2-3 of them are commonly provided since they are very important. DNS servers must be specified with an IP address.  1.1.1.1, 8.8.8.8, 1.0.0.1, 8.8.4.4 are popular and fast.

If you don't understand these things, google them. The wikipedia articles on each should be good.  But if you start with the Security Now! episodes, you should understand those things.

18.04 changed the networking setup to use netplan.  Prior to that, for 20+ yrs, we used ifup/down.  Netplan is immature (it seems) and a key reason I **haven't moved any systems** here to 18.04.

But start with the SN episodes to get a handle on basic networking. You can read the transcripts or listen.  There might be newer versions with videos. IDK.

---

### Post by Dennis N on 2018-11-18
Wow. This is getting to be a tough problem to solve! You have Dell XPS 8700 (a desktop model) with Intel core i7-4790 (which is gen 4, code named Haswell). You have successfully installed Ubuntu MATE 18.04. Didn't the ethernet connection work when you ran the live media pre-installation? (One requirement Ubuntu states (I think) is that you need an internet connection.)

Assuming that's true, can you still access the internet from a live media session, using your ethernet?

---

### Post by mitesh.agrwl on 2018-11-19
```

sudo lshw -C network
[sudo] password for robert: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 12:34:56:78:99:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: **autonegotiation=off** broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:31 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
```

The card has autonegotiation properties but for some reasons it is disabled. Please turn on the autonegotiation using command 

```
 ~$ ethtool -s enp3s0 autoneg on
~$ sudo service networking restart 
```

Please check if this solves your problem. Also check that the autonegotiation does not turn off again when you reboot the machine. If it happens so, please report back.

---

### Post by TheFu on 2018-11-19
mitesh.agrwl - nice catch.  GigE NICs need auto negotiation on.

---

### Post by Odyssey1942 on 2018-11-19
Apology for the lapse at my end. We had a big family get together for my 76th!

Dennis, unfortunately there is no ethernet connectivity in a live session. Probably would be helpful in tracking down the problem if it would.

mitesh.agrwl, thanks for catching and mentioning this. Ran the commands and autonegotiation is now on. Have restarted several times since running your suggested commands in various states of WiFi, no Wifi, etc but still no ethernet connectivity. Dang! My hopes were high

FWIIW, looking at the Editing Wired Connection 1, General tab, I notice that "connection priority for auto-activation now shows a value of -999 (whereas I am pretty sure it was blank before, so this is probably a consequence of turning autonegotiation on, which remains on after reboots). In any case this appears to be one more step toward the solution

This is probably not important, but l was looking at the information provided by the Active Network Connections screen General Section, and it shows the driver to be r8712u.  ```
lshw -C network
``` still shows "driver=r8168" Unsure how or when the Active Network Connections screen updates that driver information, but this discrepancy is a little strange.

FWIIW:
```
sudo lshw -C network
[sudo] password for 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 12:34:56:78:99:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.045.08-NAPI duplex=half latency=0 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:30 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:19 memory:f7100000-f7107fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@3:11
       logical name: wlx00212f30a0d9
       serial: 00:21:2f:30:a0:d9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.236 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by TheFu on 2018-11-19
Pull the wireless USB device. That uses the r8712u driver.  Best to only give the OS 1 choice for networking.
The wifi having an IP could prevent the wired from getting one.

But .... seeing that the wifi gets an IP of 192.168.1.236, likely proves that the DHCP server is working.

I have just 1 more guess for the core problem, assuming you've checked everything listed previously already.  There have been times when Realtek NICs have retained settings from Windows after a reboot into Linux which prevented the card from working under Linux.  A full, hard, completely, powered off, reboot is needed to clear it.  Let me look for a link.  [https://en.opensuse.org/SDB:Realtek_8169_driver_problem](https://en.opensuse.org/SDB:Realtek_8169_driver_problem) is for SuSE, but the text could describe what you are seeing.

---

### Post by Dennis N on 2018-11-19
> Dennis, unfortunately there is no ethernet connectivity in a live session. Probably would be helpful in tracking down the problem if it would.
Does that include before installing? I'm wondering how did you install without internet connection.

Comments:

If it were me (not suggesting you surrender and do the same), I would at this point try reinstall, and if I got the same failure, I would try another distro (18.10, or some other Linux entirely, like Fedora) and see if anything changes. But the guys making the recent posts here seem to be very knowledgeable on networking and probably will solve this for you. I hope so. 

An anecdote:

When I built my second computer in 2014 (like yours, a Intel gen 4 Haswell), and after installing Ubuntu, I also found I had no ethernet (but it worked with a wifi adapter I had). I assumed some bad hardware. Several days later, I checked the cable, and found I hadn't plugged it in all the way. There are little colored LED lights by the connector that show status, and they came on. Ethernet!

Added remark:

This may mean nothing, but In your output, I noticed this:
size: 10Mbit/s
capacity: 1Gbit/s 

by comparison, on my computer, **size: 1Gbit/s**. Why is that? Is size the bandwith of the connection we have?

---

### Post by TheFu on 2018-11-19
The _size: 10Mbit/s_ just means it isn't seeing a fast or gigabit ethernet connection on the wire. 10base-tx is the lowest speed today, so if the card is powered, nothing slower is possible.  The 100 and 1000 base-tx protocols report their speeds. 10 base-tx does not.

---

### Post by mitesh.agrwl on 2018-11-19
```
sudo lshw -C network
[sudo] password for 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: 12:34:56:78:99:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: **autonegotiation=on** broadcast=yes driver=r8168 driverversion=8.045.08-NAPI ***duplex=half*** latency=0 link=no multicast=yes port=twisted pair **speed=10Mbit/s**
       resources: irq:30 ioport:d000(size=256) memory:f7200000-f7200fff memory:f2100000-f2103fff
```

Though the autonegotiation has been turned on but the card is still stuck with **duplex=half** and of course the speed to 10Mb/s. As itr had been mentioned earlier that the card is working fine with windows, hence it is safe to assume there is no issue with the hardware (with router, ether card and the wire).

With autonegotitation on, I was hoping for duplex=full and speed=100Mbit/sec or 1Gbit/sec. As these values does not change, this shows the interface is not able to auto-negotiate for full duplex and the required speed. Please paste the output of the code:
```
~$ ethtool enp3s0  
```

---

### Post by Odyssey1942 on 2018-11-20
Well, I managed to pull the pin on a grenade. I was following the post #39 [https://en.opensuse.org/SDB:Realtek_8169_driver_problem]("https://en.opensuse.org/SDB:Realtek_8169_driver_problem") and had done #2, then restarted. The power turned on (fans spun), but no video output.

This confounds me as I would not expect the change I made (enabled wake on LAN in BIOS) to brick the mobo, and hopefully there is some way to recover. I will post separately on this subject and return to this thread if and when it restarts. Please keep one eye out for a new post here.

Dell XPS 8700 Desktop i7-4790 16GB RAM dual boot Win 10 home on HDD / Ubuntu MATE 18.04.1 on SSD

---

### Post by Odyssey1942 on 2018-11-21
Here is the output requested by mitesh.agrwl:
```
ethtool enp3s0
Settings for enp3s0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: 10Mb/s
	Duplex: Half
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: no

```

---

### Post by mitesh.agrwl on 2018-11-21
The above output is stating the same, auto-negotiation is supported and on. Can you please check the LAN cable/wire, how many pairs of wire (2 pair/4 pair or 4 wire/8 wire) in it and what is the category of cable, should be mention like CAT 5 or CAT 5e or CAT 6.  If it is mentioned as CAT 5e or CAT 6, it should be able to negotiate 1000 Mb/s and if cable is CAT 5 will support only 100Mb/s. A 2 pair cable support 100Mb/s only.To set the speed and duplex manually use code

```
ethtool -s enp3s0 speed 1000 duplex full
sudo service networking restart
```

If above code does not work try 

```
ethtool -s enp3s0 speed 100 duplex full
sudo service networking restart
```

In both cases post the output of **dmesg | tail**

---

### Post by Odyssey1942 on 2018-11-21
mitesh.agrwl, thanks for yours. Before addressing the content, I want to mention  that when this computer (dual) boots into Win 10, the ethernet works fine with the existing cable. Also I have tried other ethernet cables with same results (Win works, Ubuntu doesn't).

Surely this is not a cable issue?

---

### Post by TheFu on 2018-11-21
When you boot into win10, what are the connection parameters?  What speed?  Full/half duplex?  Linux drivers will do what they are told. 
Actually, it would be helpful to know the IP, netmask, gateway and DNS settings too. ** ipconfig /all **will provide those on Windows, I think.

And "working fine" doesn't mean the same as working optimally.  Right now, we'd be happy to get something working, but if you have a GigE network, then we should make certain we are asking to use it properly.

---

### Post by Odyssey1942 on 2018-11-21
Here is output:
```
C:\Users\xyz>ipconfig /all
Windows IP Configuration
   Host Name . . . . . . . . . . . . : Dell-Desktop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Ethernet:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Local Area Connection* 1:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Wi-Fi:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Dell Wireless 1704 802.11b/g/n (2.4GHz)
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 12-34-56-78-98-76(Preferred)
   Temporary IPv6 Address. . . . . . : 12-34-56-78-98-76
(Preferred)
   Link-local IPv6 Address . . . . . : 12-34-56-78-98-76(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.176(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Wednesday, November 21, 2018 4:09:14 PM
   Lease Expires . . . . . . . . . . : Thursday, November 22, 2018 4:09:14 PM
   Default Gateway . . . . . . . . . : 12-34-56-78-98-76
                                       192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 123456789
   DHCPv6 Client DUID. . . . . . . . : 12-34-56-78-98-76
   DNS Servers . . . . . . . . . . . : 12-34-56-78-98-76
                                       192.168.1.1
   Primary WINS Server . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Ethernet adapter Bluetooth Network Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
```

---

### Post by TheFu on 2018-11-21
So .... I thought we were working on the wired connection.  Did that change?  Is wifi the issue now?

I ask because we need to see the wired connection on Windows, not the wifi, if we are still trying to fix the wired ethernet on Linux.

---

### Post by Odyssey1942 on 2018-11-21
No, ethernet is still the issue, thanks.

Did you see the second section: "Ethernet adapter Ethernet"?

> Ethernet adapter Ethernet:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Is this not the relevant bit? Or are you referring to something else?

---

### Post by TheFu on 2018-11-21
You've claimed that the ethernet works under Windows all this time, but you posted a wifi connection with Windows, not the ethernet one. 

Boot into windows, disable the wifi, enable the wired ethernet, run the ipconfig command and please post the results.

Specifically, I asked for:
> what are the connection parameters? What speed? Full/half duplex? Linux drivers will do what they are told.
Actually, it would be helpful to know the IP, netmask, gateway and DNS settings too. 

---

### Post by Odyssey1942 on 2018-11-21
I think I now understand that I should have done that without the Wifi adapter in place, and I will certainly do that just as soon as I get past my next possible self-administered shot in the foot.

I kept wondering what would happen if I took out the existing HDD and the SSD, put in a spare HDD and installed 18.04.1 on that using my USB installer, i.e., would it find ethernet connectivity. And I tried to do just that, but am now concerned whether that was a bit too experimental.

The live disk was not able to install on the new HDD. Lots of errors. 

I suddenly realized that this might have royally corrupted the boot loader? I will not know until I try to replace the SSD and the HDD, unless you already know that I have, or suspect that I have. Any opinions/guidance you can share with me before I try to replace the drives will be much appreciated.

---

### Post by TheFu on 2018-11-21
The windows OS needs to be **connected** using the wired ethernet port.  I hope we aren't 53 posts into troubleshooting a NIC that never worked on Windows either.

No advice around a dual-boot setup. I don't do that and haven't in over a decade and even then it was only a few times.  The last time I seriously dual-booted was in the mid-1990s - and that was Windows and OS/2 and MS-DOS and DR-DOS using a 240MB HDD.

---

### Post by mitesh.agrwl on 2018-11-22
> **Odyssey1942 said:**
> No, ethernet is still the issue, thanks.

Did you see the second section: "Ethernet adapter Ethernet"?

```
Ethernet adapter Ethernet:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
```

Is this not the relevant bit? Or are you referring to something else?

If the above output is from 'Win' as claimed, I am not able to see a 'working' wired Ethernet connection. 

> mitesh.agrwl, thanks for yours. Before addressing the content, I want to  mention  that when this computer (dual) boots into Win 10, the ethernet  works fine with the existing cable. Also I have tried other ethernet  cables with same results (Win works, Ubuntu doesn't).


As it already had been mentioned the wired Ethernet connection is 'working perfectly' with Win, please post the 'working' settings and details for the same for further assistance!

---

### Post by Odyssey1942 on 2018-11-22
Sometimes it is good to sleep on a problem. It occurred to me that there was an older version of Ubuntu (maybe 12.04 or possibly even earlier) on this 500GB HDD (not the previous 1TB HDD), anyway most likely done on a BIOS install. In yesterday's exercise, I had done a something else install and the computer was probably trying to install with UEFI and that might be the problem with this attempt at installing. So this morning, I ran it again doing a complete format and simple install. All seems to have gone well with the exception of still no wired ethernet.

So I am about to shut down, remove this older 500GB HDD and hook up the previous HDD and SDD to post the Windows connectivity results, but before I do, and while there is only the one brand new fresh install of Ubuntu Mate 18.04.1 running at the moment, is there anything that you would suggest I test now (can only use WiFi if connectivity is desired for any tests) as this might be an opportunity to obtain unique results?

---

### Post by Odyssey1942 on 2018-11-22
OK, here is output with Wifi disabled

```
ipconfig /all
Windows IP Configuration
   Host Name . . . . . . . . . . . . : Dell-Desktop
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
Ethernet adapter Ethernet:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek PCIe GBE Family Controller
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 12-34-56-78-98-76Preferred)
   Temporary IPv6 Address. . . . . . : 12-34-56-78-98-76Preferred)
   Link-local IPv6 Address . . . . . : 12-34-56-78-98-76(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.194(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, November 22, 2018 4:47:43 PM
   Lease Expires . . . . . . . . . . : Friday, November 23, 2018 4:47:40 PM
   Default Gateway . . . . . . . . . : 12-34-56-78-98-76
                                       192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 43552918
   DHCPv6 Client DUID. . . . . . . . : 12-34-56-78-98-76
   DNS Servers . . . . . . . . . . . : 12-34-56-78-98-76
                                       192.168.1.1
   Primary WINS Server . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
Wireless LAN adapter Local Area Connection* 1:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Local Area Connection* 2:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Wi-Fi Direct Virtual Adapter #2
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Wireless LAN adapter Wi-Fi:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Dell Wireless 1704 802.11b/g/n (2.4GHz)
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Ethernet adapter Bluetooth Network Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 12-34-56-78-98-76
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

```

With my sincere thanks to all, I think that I am wearing you all out on this. I know that i am exhausted. Maybe I should just buy a new compatible controller card and get on with all the stuff that has been stacking up. Unless someone has an idea that seems worth a try, I will do that.

---

