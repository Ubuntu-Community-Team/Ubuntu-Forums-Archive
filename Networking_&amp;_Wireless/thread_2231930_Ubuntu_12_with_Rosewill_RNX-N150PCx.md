---
title: "Ubuntu 12 with Rosewill RNX-N150PCx"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by skater40165 on 2014-06-28
Ok, so I have tried a number of things to get this working. Including following the readme that came with the driver and the instructions listed [here]("http://ubuntuforums.org/showthread.php?t=1803136&page=2"). The first issue I run into is while preforming make I get the following error. 

```
/home/landon/Desktop/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux/../../os/linux/rt_linux.c:1646:10: error: unknown field ‘ndo_set_multicast_list’ specified in initializer
make[2]: *** [/home/landon/Desktop/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/landon/Desktop/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-65-generic-pae'
make: *** [LINUX] Error 2


```

I was able to get around this by commenting out the line 
```
.ndo_set_multicast_list = NULL,
```
in the file os/linux/rt_linux.c

But that is just not enough. If I comment that out and change the lines 
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR=Red]y[/COLOR]

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR=Red]y[/COLOR]
```

in os/linux/config.mk I can get it to build, and I can see the device in iwconfig. But It doesnt see any networks.

---

### Post by chili555 on 2014-06-29
It is doubtful you'll get this antique to compile on any recent version of Ubuntu. Before we propose a solution, let's gather a bit more information:```
lspci -nn | grep 0280
uname -r
lsmod | grep rt2
```Thanks.

---

### Post by skater40165 on 2014-06-29
I did just relize that I had downloaded the drive for the rnx-n150pc not the rnx-n150pcx. But it diesnt appear there is a linux driver for it. So this might be hopeless. Here is the output for the commmands. 

```
 lspci -nn | grep 0280
01:06.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]

```

```
uname -r
3.2.0-65-generic-pae
```

```
lsmod | grep rt2
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14237  1 rt2800pci
rt2x00lib              48923  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci

```

---

### Post by chili555 on 2014-06-29
> lsmod | grep rt2
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pciThe system already has loaded a native driver for you. Is it not working as expected?```
iwconfig
sudo iwlist wlan0 scan
dmesg | grep -e rt2 -e wlan
```

---

### Post by skater40165 on 2014-06-29
No, some of that maybe there from previous steps I took to get it working. Also after doing the steps in the post I mentioned I can generally get ra0 to list in iwconfig but network manager doesnt see it, nor do the scan results from iwlist find anything. 

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

```
sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.


```

```
dmesg | grep -e rt2 -e wlan
[   15.022473] rt2800pci 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   15.032634] rt2x00pci_regbusy_read() Indirect register access failed: offset=0x00000580, value=0xffffffff
[   15.361681] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[   15.361721] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   15.361836] rt2800pci 0000:01:06.0: PCI INT A disabled
[   15.513258] rt2860 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   18.959683] !!! rt28xx Initialized fail !!!
[   19.590695] !!! rt28xx Initialized fail !!!
[   20.017748] !!! rt28xx Initialized fail !!!
[   20.441251] !!! rt28xx Initialized fail !!!
[  255.688644] !!! rt28xx Initialized fail !!!
[  256.121832] !!! rt28xx Initialized fail !!!
[  256.546460] !!! rt28xx Initialized fail !!!
[  256.969505] !!! rt28xx Initialized fail !!!


```

---

### Post by chili555 on 2014-06-29
It won't work to have whatever driver you built above *AND* the native rt2800pci loading at the same time. We can see that rt2800pci, in its present form, won't work:> [   15.361681] phy0 -> rt2800_init_eeprom: Error - Invalid RT chipset detected.
[   15.361721] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   15.361836] rt2800pci 0000:01:06.0: PCI INT A disabledLet's blacklist it and see if the driver you compiled will work, which I doubt:```
sudo -i
echo "blacklist rt2800pci"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and post again:```
lsmod | grep rt2
iwconfig
```Thanks.

---

### Post by skater40165 on 2014-06-29
Ok so we are now gettign ra0 to show up but the scan returns 0 results. 

```
$ lsmod | grep rt2

```

```

landon@landon-PC:~$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```

```
sudo iwlist ra0 scan
ra0       No scan results


```

---

### Post by chili555 on 2014-06-29
What is the driver that loaded?```
lsmod
```Any clues in the message log?```
dmesg | grep ra0
```

---

### Post by skater40165 on 2014-06-29
I would really like to thank you for your time btw. 
```
 lsmod
Module                  Size  Used by
nls_utf8               12493  1 
nls_iso8859_1          12617  1 
isofs                  39553  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
dm_crypt               22528  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd_hda_codec_realtek   174347  1 
nvidia              10304303  40 
rt3562sta             819720  0 
psmouse                86982  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
wmi                    18744  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
joydev                 17393  0 
k10temp                12990  0 
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    81731  1 usbhid
usb_storage            39646  1 
sata_nv                23360  2 
forcedeth              58096  0 
pata_amd               13750  1 

```

```
 dmesg | grep ra0
[   18.684696] ADDRCONF(NETDEV_UP): ra0: link is not ready


```

---

### Post by chili555 on 2014-06-29
> rt3562sta             819720  0 There we go. 

With reference to the interface ra0, the log was not helpful. Let's see what the driver says:```
dmesg | grep rt35
```

---

### Post by skater40165 on 2014-06-29
No results with that. 


```
$ dmesg | grep rt35
$ 

```

---

### Post by chili555 on 2014-06-29
Wonderful. It doesn't work and it won't tell us why. Beautiful. Please do:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use leafpad or kate or nano or any text editor if tou don't have gedit. Change the last line to:```
blacklist rt3562sta
```Proofread, save and close the text editor. Now do:```
sudo apt-get install linux-backports-modules-cw-3.12-precise-generic-pae
```After it's finished, reboot and let us see:```
dmesg | grep -e rt2 -e wlan
```

---

### Post by skater40165 on 2014-06-29
lol this thing has been a nightmare. 

```
$ dmesg | grep -e rt2 -e wlan
[   15.988425] rt2800pci 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   15.988465] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[   15.988505] ieee80211 phy0: rt2x00lib_probe_dev: Error - Failed to allocate device
[   15.988535] rt2800pci 0000:01:06.0: PCI INT A disabled


```

---

### Post by chili555 on 2014-06-29
> this thing has been a nightmare. Yes, indeed! Let's keep trying harder! Please change the blacklist back to rt2800pci as above. Next:```
sudo apt-get install git
git clone https://github.com/mtorromeo/rt3562sta-linux.git
cd rt3562sta-linux
make
sudo make install
```Reboot and let me see:```
iwconfig
dmesg | greo rt3
```

---

### Post by skater40165 on 2014-06-29
Ok so I get this error when running make 

```
WARNING: modpost: missing MODULE_LICENSE() in /home/landon/rt3562sta-linux/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/landon/rt3562sta-linux/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-65-generic-pae'
cp -f /home/landon/rt3562sta-linux/os/linux/rt3562sta.ko /tftpboot
cp: cannot remove `/tftpboot': Permission denied


```

So I tried sudo make which seemed to work 

```
sudo make
make -C tools
make[1]: Entering directory `/home/landon/rt3562sta-linux/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/landon/rt3562sta-linux/tools'
/home/landon/rt3562sta-linux/tools/bin2h
cp -f os/linux/Makefile.6 /home/landon/rt3562sta-linux/os/linux/Makefile
make -C /lib/modules/3.2.0-65-generic-pae/build SUBDIRS=/home/landon/rt3562sta-linux/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-65-generic-pae'
  CC [M]  /home/landon/rt3562sta-linux/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/landon/rt3562sta-linux/os/linux/rt3562sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/landon/rt3562sta-linux/os/linux/rt3562sta.o
see include/linux/module.h for more information
  LD [M]  /home/landon/rt3562sta-linux/os/linux/rt3562sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-65-generic-pae'
cp -f /home/landon/rt3562sta-linux/os/linux/rt3562sta.ko /tftpboot

```

But then make install fails with this. 

```
$ sudo make install 
make -C /home/landon/rt3562sta-linux/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/landon/rt3562sta-linux/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/landon/rt3562sta-linux/RT2860STA.dat /etc/Wireless/RT2860STA/.
cp: cannot stat `/home/landon/rt3562sta-linux/RT2860STA.dat': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/landon/rt3562sta-linux/os/linux'
make: *** [install] Error 2


```

I have not rebooted yet as the make didnt seem to go so well., do you still want the reboot and me to run the other commands?

---

### Post by skater40165 on 2014-06-29
I went ahead and rebooted. dmesg returned nothing and iwconfig returned. 

```

lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


```

---

### Post by chili555 on 2014-06-29
> cp: cannot stat `/home/landon/rt3562sta-linux/RT2860STA.dat': No such file or directoryAgain...wonderful. Please do:```
cp RT3562STA.dat RT2860STA.dat
```And try 'sudo make install' again. Then:```
dmesg | grep rt3
```

---

### Post by skater40165 on 2014-06-29
Ok so make install worked this time. 

```

dmesg | grep rt3
[   15.071465] rt3562sta: module license 'unspecified' taints kernel.


```

```

iwconfig
lo        no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```

```

lspci -nn | grep 0280
01:06.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]


```

---

### Post by chili555 on 2014-06-29
How about:```
dmesg | grep -e rt2 -e ra0 -e RT
sudo iwlist ra0 scan
```

---

### Post by skater40165 on 2014-06-29
Ok so I made a change to the os/linux/config.mk to HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT to y and did make / make install again. Neetwork manager no sees the card and it shows in iwconfig. But still no scan results. 


```

$ dmesg | grep -e rt2 -e ra0 -e RT
[    0.000000] ACPI: WDRT affc05d0 00047 (v01 121009 NV-WDRT  20091210 MSFT 00000097)
[    0.148924] RTC time: 16:26:34, date: 06/29/14
[    0.160919] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.161016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.161042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.161064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.161085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.161290]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0c
[    0.779056] rtc_cmos 00:02: RTC can wake from S4
[   15.024769] ===> rt2860_probe
[   15.024945] rt2860 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   15.024974] --> RTMPAllocAdapterBlock
[   15.025124] --> RTMPAllocTxRxRingMemory
[   15.025156] <-- RTMPAllocTxRxRingMemory, Status=0
[   15.025214] <-- RTMPAllocAdapterBlock, Status=0
[   15.027330] The name of the new ra interface is ra0...
[   15.035006] @rt2860_probe MAC address: ff:ff:ff:ff:ff:ff
[   15.035008] <=== rt2860_probe
[   20.750269] RTMPSetLED::Mode=0,HighByte=0x00,LowByte=0x00
[   20.755269] <---RTPCICmdThread
[   20.755335] !!! rt28xx Initialized fail !!!
[   20.755344] rt28xx_open return fail!
[   20.755576] ADDRCONF(NETDEV_UP): ra0: link is not ready
[   21.237558] RTMPSetLED::Mode=0,HighByte=0x00,LowByte=0x00
[   21.242557] <---RTPCICmdThread
[   21.242673] !!! rt28xx Initialized fail !!!
[   21.242689] rt28xx_open return fail!
[   48.860245] rt28xx_get_wireless_stats --->
[   48.860247] <--- rt28xx_get_wireless_stats

```
```

$ sudo iwlist ra0 scan
[sudo] password for landon: 
ra0       No scan results


```

```

$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.



```

```

~/rt3562sta-linux$ dmesg | grep rt3
[   15.020914] rt3562sta: module license 'unspecified' taints kernel.

```

Please let me know if you would like for me to revert the changes and redo the make process.

---

### Post by chili555 on 2014-06-29
Let's see:```
ls /etc/Wireless
```If there is a directory within, let's see what it is and its contents:```
ls /etc/Wireless/<whatever_you_found>
```Also:```
cat /var/log/syslog | grep dat
```

---

### Post by skater40165 on 2014-06-29
Ok, found one idrectory in /etc/Wireless. Also greping for "dat" returns a lot more than I expected it would lol. 

```
$ ls /etc/Wireless
RT2860STA
$ ls /etc/Wireless/RT2860STA/
RT2860STA.dat

```

```
$ ls /etc/Wireless/RT2860STA/
RT2860STA.dat
landon@landon-PC:~/rt3562sta-linux$ cat /var/log/syslog | grep dat
Jun 28 12:45:39 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 12:45:39 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 12:45:39 landon-PC kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Jun 28 12:45:39 landon-PC kernel: [    0.000000]  modified: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 12:45:39 landon-PC kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 28 12:45:39 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c07dcfc0, node_mem_map c10dc000
Jun 28 12:45:39 landon-PC kernel: [    0.000000] Memory: 5916928k/7340032k available (4849k kernel code, 110556k reserved, 2220k data, 680k init, 5117704k highmem)
Jun 28 12:45:39 landon-PC kernel: [    0.000000]       .data : 0xc05bc7ff - 0xc07e7948   (2220 kB)
Jun 28 12:45:39 landon-PC kernel: [    0.242710] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 12:45:39 landon-PC kernel: [    0.689093] Write protecting the kernel read-only data: 1884k
Jun 28 12:45:39 landon-PC kernel: [    2.336523] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 28 12:45:45 landon-PC ntpdate[1138]: adjust time server 91.189.89.199 offset 0.013901 sec
Jun 28 12:51:06 landon-PC mysqld[17073]: databases and anonymous user created by default.  This is
Jun 28 12:52:39 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 12:52:39 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 12:52:39 landon-PC kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
Jun 28 12:52:39 landon-PC kernel: [    0.000000]  modified: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 12:52:39 landon-PC kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 28 12:52:39 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c07eb240, node_mem_map c10ed000
Jun 28 12:52:39 landon-PC kernel: [    0.000000] Memory: 5916800k/7340032k available (4893k kernel code, 110624k reserved, 2232k data, 684k init, 5117704k highmem)
Jun 28 12:52:39 landon-PC kernel: [    0.000000]       .data : 0xc05c77fb - 0xc07f5bc8   (2232 kB)
Jun 28 12:52:39 landon-PC kernel: [    0.242715] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 12:52:39 landon-PC kernel: [    0.689298] Write protecting the kernel read-only data: 1896k
Jun 28 12:52:39 landon-PC kernel: [    2.193240] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 28 12:52:47 landon-PC ntpdate[1171]: adjust time server 91.189.89.199 offset 0.091599 sec
Jun 28 13:13:47 landon-PC kernel: [ 1273.331829] <30>udevd[9918]: converting old udev database
Jun 28 13:29:35 landon-PC mysqld_safe[18029]: to connect to the mysql database and look at the grant tables:
Jun 28 13:32:09 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 13:32:09 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 13:32:09 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 13:32:09 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f284a200
Jun 28 13:32:09 landon-PC kernel: [    0.000000] Memory: 5914868k/7340032k available (5849k kernel code, 113736k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 13:32:09 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 13:32:09 landon-PC kernel: [    0.148935] RTC time: 17:31:59, date: 06/28/14
Jun 28 13:32:09 landon-PC kernel: [    0.235421] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 13:32:09 landon-PC kernel: [    0.785891] Write protecting the kernel read-only data: 2388k
Jun 28 13:32:09 landon-PC kernel: [    0.785893] NX-protecting the kernel data: 4388k
Jun 28 13:32:09 landon-PC kernel: [    2.423948] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 13:32:09 landon-PC kernel: [    7.794356] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 13:32:09 landon-PC kernel: [    8.628720] cfg80211: World regulatory domain updated:
Jun 28 13:32:23 landon-PC ntpdate[980]: adjust time server 91.189.89.199 offset -0.419606 sec
Jun 28 14:23:28 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 14:23:28 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 14:23:28 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 14:23:28 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2176200
Jun 28 14:23:28 landon-PC kernel: [    0.000000] Memory: 5911372k/7340032k available (5849k kernel code, 117232k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 14:23:28 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 14:23:28 landon-PC kernel: [    0.148934] RTC time: 18:23:17, date: 06/28/14
Jun 28 14:23:28 landon-PC kernel: [    0.235404] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 14:23:28 landon-PC kernel: [    0.778381] Write protecting the kernel read-only data: 2388k
Jun 28 14:23:28 landon-PC kernel: [    0.778382] NX-protecting the kernel data: 4388k
Jun 28 14:23:28 landon-PC kernel: [    2.830467] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 14:23:28 landon-PC kernel: [   10.870942] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 14:23:28 landon-PC kernel: [   11.607807] cfg80211: World regulatory domain updated:
Jun 28 14:23:36 landon-PC NetworkManager[1186]:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 14:23:36 landon-PC NetworkManager[1186]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 28 14:23:43 landon-PC ntpdate[1139]: adjust time server 91.189.89.199 offset 0.267855 sec
Jun 28 14:25:23 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 28 14:28:37 landon-PC anacron[3572]: Updated timestamp for job `cron.daily' to 2014-06-28
Jun 28 14:38:31 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 14:38:31 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 14:38:31 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 14:38:31 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 28 14:38:31 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 14:38:31 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 14:38:31 landon-PC kernel: [    0.148923] RTC time: 18:38:15, date: 06/28/14
Jun 28 14:38:31 landon-PC kernel: [    0.231064] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 14:38:31 landon-PC kernel: [    0.786386] Write protecting the kernel read-only data: 2388k
Jun 28 14:38:31 landon-PC kernel: [    0.786388] NX-protecting the kernel data: 4388k
Jun 28 14:38:31 landon-PC kernel: [    3.579175] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 14:38:31 landon-PC kernel: [   15.032221] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 14:38:31 landon-PC kernel: [   15.133448] cfg80211: World regulatory domain updated:
Jun 28 14:38:33 landon-PC NetworkManager[1212]:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 14:38:33 landon-PC NetworkManager[1212]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 28 14:38:41 landon-PC ntpdate[1117]: adjust time server 91.189.89.199 offset -0.377069 sec
Jun 28 14:39:50 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 28 14:48:33 landon-PC anacron[2470]: Updated timestamp for job `cron.weekly' to 2014-06-28
Jun 28 14:53:33 landon-PC anacron[3087]: Updated timestamp for job `cron.monthly' to 2014-06-28
Jun 28 19:09:17 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 19:09:17 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 19:09:17 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 19:09:17 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 28 19:09:17 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 19:09:17 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 19:09:17 landon-PC kernel: [    0.148901] RTC time: 23:09:02, date: 06/28/14
Jun 28 19:09:17 landon-PC kernel: [    0.227040] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 19:09:17 landon-PC kernel: [    0.778458] Write protecting the kernel read-only data: 2388k
Jun 28 19:09:17 landon-PC kernel: [    0.778460] NX-protecting the kernel data: 4388k
Jun 28 19:09:17 landon-PC kernel: [    3.606744] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 19:09:17 landon-PC kernel: [   14.965948] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 19:09:17 landon-PC kernel: [   15.238957] cfg80211: World regulatory domain updated:
Jun 28 19:09:20 landon-PC NetworkManager[1192]:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 19:09:20 landon-PC NetworkManager[1192]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 28 19:09:28 landon-PC ntpdate[1105]: step time server 91.189.94.4 offset -0.589943 sec
Jun 28 19:10:39 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 28 19:33:30 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 19:33:30 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 19:33:30 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 19:33:30 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 28 19:33:30 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 19:33:30 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 19:33:30 landon-PC kernel: [    0.148924] RTC time: 23:33:13, date: 06/28/14
Jun 28 19:33:30 landon-PC kernel: [    0.231068] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 19:33:30 landon-PC kernel: [    0.782377] Write protecting the kernel read-only data: 2388k
Jun 28 19:33:30 landon-PC kernel: [    0.782378] NX-protecting the kernel data: 4388k
Jun 28 19:33:30 landon-PC kernel: [    4.098321] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 19:33:30 landon-PC kernel: [   15.902796] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 19:33:30 landon-PC kernel: [   15.921035] cfg80211: World regulatory domain updated:
Jun 28 19:33:33 landon-PC NetworkManager[1245]:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 19:33:33 landon-PC NetworkManager[1245]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 28 19:33:41 landon-PC ntpdate[1158]: adjust time server 91.189.89.199 offset -0.243700 sec
Jun 28 19:34:49 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 28 19:55:21 landon-PC NetworkManager[1245]: <error> [1403999721.643214] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 28 20:02:02 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 28 20:02:02 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 28 20:02:02 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 28 20:02:02 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 28 20:02:02 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 28 20:02:02 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 28 20:02:02 landon-PC kernel: [    0.148898] RTC time:  0:01:47, date: 06/29/14
Jun 28 20:02:02 landon-PC kernel: [    0.227048] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 28 20:02:02 landon-PC kernel: [    0.774437] Write protecting the kernel read-only data: 2388k
Jun 28 20:02:02 landon-PC kernel: [    0.774439] NX-protecting the kernel data: 4388k
Jun 28 20:02:02 landon-PC kernel: [    3.580837] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 28 20:02:02 landon-PC kernel: [   15.008726] cfg80211: Calling CRDA to update world regulatory domain
Jun 28 20:02:02 landon-PC kernel: [   15.324146] cfg80211: World regulatory domain updated:
Jun 28 20:02:05 landon-PC NetworkManager[1183]:    SCPlugin-Ifupdown: update_system_hostname
Jun 28 20:02:05 landon-PC NetworkManager[1183]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 28 20:02:05 landon-PC NetworkManager[1183]: <error> [1404000125.260398] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 28 20:02:14 landon-PC ntpdate[1108]: adjust time server 91.189.89.199 offset 0.282041 sec
Jun 28 20:03:21 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 28 20:06:01 landon-PC NetworkManager[1183]: <error> [1404000361.990242] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 29 07:35:01 landon-PC anacron[4943]: Updated timestamp for job `cron.daily' to 2014-06-29
Jun 29 09:18:49 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 09:18:49 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 09:18:49 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 09:18:49 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 09:18:49 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 09:18:49 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 09:18:49 landon-PC kernel: [    0.148921] RTC time: 13:18:34, date: 06/29/14
Jun 29 09:18:49 landon-PC kernel: [    0.231077] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 09:18:49 landon-PC kernel: [    0.786372] Write protecting the kernel read-only data: 2388k
Jun 29 09:18:49 landon-PC kernel: [    0.786374] NX-protecting the kernel data: 4388k
Jun 29 09:18:49 landon-PC kernel: [    3.648695] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 09:18:51 landon-PC NetworkManager[1227]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 09:18:51 landon-PC NetworkManager[1227]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 09:18:51 landon-PC NetworkManager[1227]: <error> [1404047931.971070] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 29 09:18:58 landon-PC ntpdate[1123]: step time server 91.189.94.4 offset -2.600122 sec
Jun 29 09:20:18 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 09:55:51 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 09:55:51 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 09:55:51 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 09:55:51 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 09:55:51 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 09:55:51 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 09:55:51 landon-PC kernel: [    0.148899] RTC time: 13:55:35, date: 06/29/14
Jun 29 09:55:51 landon-PC kernel: [    0.227044] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 09:55:51 landon-PC kernel: [    0.782565] Write protecting the kernel read-only data: 2388k
Jun 29 09:55:51 landon-PC kernel: [    0.782567] NX-protecting the kernel data: 4388k
Jun 29 09:55:51 landon-PC kernel: [    3.386226] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 09:55:51 landon-PC kernel: [   15.395785] cfg80211: Calling CRDA to update world regulatory domain
Jun 29 09:55:51 landon-PC kernel: [   15.405291] cfg80211: World regulatory domain updated:
Jun 29 09:55:53 landon-PC NetworkManager[1197]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 09:55:53 landon-PC NetworkManager[1197]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 09:56:02 landon-PC ntpdate[1093]: adjust time server 91.189.89.199 offset -0.074396 sec
Jun 29 09:58:20 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 10:49:46 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 10:49:46 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 10:49:46 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 10:49:46 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 10:49:46 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 10:49:46 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 10:49:46 landon-PC kernel: [    0.148923] RTC time: 14:49:30, date: 06/29/14
Jun 29 10:49:46 landon-PC kernel: [    0.231076] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 10:49:46 landon-PC kernel: [    0.782737] Write protecting the kernel read-only data: 2388k
Jun 29 10:49:46 landon-PC kernel: [    0.782738] NX-protecting the kernel data: 4388k
Jun 29 10:49:46 landon-PC kernel: [    4.119307] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 10:49:49 landon-PC NetworkManager[1204]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 10:49:49 landon-PC NetworkManager[1204]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 10:49:49 landon-PC NetworkManager[1204]: <error> [1404053389.624123] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 29 10:49:58 landon-PC ntpdate[1100]: adjust time server 91.189.94.4 offset -0.099304 sec
Jun 29 10:52:35 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 12:17:14 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 12:17:14 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 12:17:14 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 12:17:14 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 12:17:14 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 12:17:14 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 12:17:14 landon-PC kernel: [    0.148922] RTC time: 16:16:58, date: 06/29/14
Jun 29 12:17:14 landon-PC kernel: [    0.231071] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 12:17:14 landon-PC kernel: [    0.782440] Write protecting the kernel read-only data: 2388k
Jun 29 12:17:14 landon-PC kernel: [    0.782441] NX-protecting the kernel data: 4388k
Jun 29 12:17:14 landon-PC kernel: [    3.397571] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 12:17:14 landon-PC kernel: [   15.077540] Allocate a net device with private data size=0!
Jun 29 12:17:17 landon-PC NetworkManager[1218]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 12:17:17 landon-PC NetworkManager[1218]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 12:17:26 landon-PC ntpdate[1111]: adjust time server 91.189.89.199 offset -0.389779 sec
Jun 29 12:18:37 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 12:26:49 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 12:26:49 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 12:26:49 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 12:26:49 landon-PC kernel: [    0.148924] RTC time: 16:26:34, date: 06/29/14
Jun 29 12:26:49 landon-PC kernel: [    0.231074] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 12:26:49 landon-PC kernel: [    0.786435] Write protecting the kernel read-only data: 2388k
Jun 29 12:26:49 landon-PC kernel: [    0.786437] NX-protecting the kernel data: 4388k
Jun 29 12:26:49 landon-PC kernel: [    3.409477] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 12:26:49 landon-PC kernel: [   15.026570] Allocate a net device with private data size=0!
Jun 29 12:26:54 landon-PC NetworkManager[1195]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 12:26:54 landon-PC NetworkManager[1195]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 12:26:54 landon-PC NetworkManager[1195]: <error> [1404059214.45765] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 29 12:27:02 landon-PC ntpdate[1100]: adjust time server 91.189.89.199 offset 0.113300 sec
Jun 29 12:28:11 landon-PC AptDaemon.PackageKit: INFO: Get updates()


```

---

### Post by chili555 on 2014-06-29
We see this:```
<error> [1404059214.45765] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
```Which I firmly believe is related to this:```
!!! rt28xx Initialized fail !!!
```When we used the native driver rt2800pci, we got the somewhat similar:```
[   15.988465] ieee80211 phy0: rt2800_probe_rt: Error - Invalid RT chipset 0xffff, rev ffff detected
[   15.988505] ieee80211 phy0: rt2x00lib_probe_dev: [COLOR="#FF0000"]Error - Failed to allocate device[/COLOR]
```We have tried the native driver, the updated backports version and a compiled driver from github; all with similar results. 

Google shows us dozens of examples where this device 1814:3060 works perfectly with rt2800pci. 

All I can deduce is that perhaps the hardware is defective. Just before I hang my head and admit defeat, let's have a looks at:```
dmesg | grep 01:06
```That's the PCI bus the card is on.

Is the card seated correctly? Does it work better if you try a different PCI slot?

---

### Post by skater40165 on 2014-06-29
Yea card is fully seated and is plugged into the ony PCI slot it haswhich previously contained a know working ethernet NIC. The wireless card is brand new from new egg wso it is not in a known working status. The card may very well have been shipped faulty. 

```

dmesg | grep 01:06
[    0.160734] pci 0000:01:06.0: [1814:3060] type 0 class 0x000280
[    0.160746] pci 0000:01:06.0: reg 10: [mem 0x5fff0000-0x5fffffff]
[    0.182323] pci 0000:01:06.0: no compatible bridge window for [mem 0x5fff0000-0x5fffffff]
[    0.231069] pci 0000:01:06.0: BAR 0: assigned [mem 0xdff00000-0xdff0ffff]
[    0.231074] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
[    0.231077] pci 0000:01:06.0: BAR 0: set to [mem 0xdff00000-0xdff0ffff] (PCI address [0xdff00000-0xdff0ffff])
[   15.024945] rt2860 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   15.024970] 0000:01:06.0: at 0xdff00000, VA 0xf9240000, IRQ 19. 

```

---

### Post by chili555 on 2014-06-29
```
[    0.182323] pci 0000:01:06.0: no compatible bridge window for [mem 0x5fff0000-0x5fffffff]
[    0.231069] pci 0000:01:06.0: BAR 0: assigned [mem 0xdff00000-0xdff0ffff]
[    0.231074] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
```Doesn't look like a happy card to me. Will you try a different slot? A different card?

---

### Post by skater40165 on 2014-06-29
Give me a second I will shut down and reseat the card. I dont have another slot the card will fit in nor do I have another card at the moment. Once I reseat it would you like me to re-run the last command again?

---

### Post by chili555 on 2014-06-29
> **skater40165 said:**
> Give me a second I will shut down and reseat the card. I dont have another slot the card will fit in nor do I have another card at the moment. Once I reseat it would you like me to re-run the last command again?Exactly!

---

### Post by skater40165 on 2014-06-29
Seems we lost the card... 

```
dmesg | grep 01:06
$ 


```

```
Jun 29 12:17:14 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 12:17:14 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 12:17:14 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 12:17:14 landon-PC kernel: [    0.148922] RTC time: 16:16:58, date: 06/29/14
Jun 29 12:17:14 landon-PC kernel: [    0.231071] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 12:17:14 landon-PC kernel: [    0.782440] Write protecting the kernel read-only data: 2388k
Jun 29 12:17:14 landon-PC kernel: [    0.782441] NX-protecting the kernel data: 4388k
Jun 29 12:17:14 landon-PC kernel: [    3.397571] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 12:17:14 landon-PC kernel: [   15.077540] Allocate a net device with private data size=0!
Jun 29 12:17:17 landon-PC NetworkManager[1218]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 12:17:17 landon-PC NetworkManager[1218]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 12:17:26 landon-PC ntpdate[1111]: adjust time server 91.189.89.199 offset -0.389779 sec
Jun 29 12:18:37 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 12:26:49 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 12:26:49 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 12:26:49 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 12:26:49 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 12:26:49 landon-PC kernel: [    0.148924] RTC time: 16:26:34, date: 06/29/14
Jun 29 12:26:49 landon-PC kernel: [    0.231074] pci 0000:01:06.0: BAR 0: error updating (0xdff00000 != 0x5ff00000)
Jun 29 12:26:49 landon-PC kernel: [    0.786435] Write protecting the kernel read-only data: 2388k
Jun 29 12:26:49 landon-PC kernel: [    0.786437] NX-protecting the kernel data: 4388k
Jun 29 12:26:49 landon-PC kernel: [    3.409477] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 12:26:49 landon-PC kernel: [   15.026570] Allocate a net device with private data size=0!
Jun 29 12:26:54 landon-PC NetworkManager[1195]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 12:26:54 landon-PC NetworkManager[1195]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 12:26:54 landon-PC NetworkManager[1195]: <error> [1404059214.45765] [nm-device-wifi.c:2591] real_update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Jun 29 12:27:02 landon-PC ntpdate[1100]: adjust time server 91.189.89.199 offset 0.113300 sec
Jun 29 12:28:11 landon-PC AptDaemon.PackageKit: INFO: Get updates()
Jun 29 14:47:20 landon-PC kernel: [    0.000000]  BIOS-e820: 00000000affc0000 - 00000000affce000 (ACPI data)
Jun 29 14:47:20 landon-PC kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 29 14:47:20 landon-PC kernel: [    0.000000] e820 update range: 00000000b0000000 - 0000000100000000 (usable) ==> (reserved)
Jun 29 14:47:20 landon-PC kernel: [    0.000000] free_area_init_node: node 0, pgdat c1873b80, node_mem_map f2214200
Jun 29 14:47:20 landon-PC kernel: [    0.000000] Memory: 5911688k/7340032k available (5849k kernel code, 116916k reserved, 2859k data, 744k init, 5115656k highmem)
Jun 29 14:47:20 landon-PC kernel: [    0.000000]       .data : 0xc15b657c - 0xc18813c0   (2859 kB)
Jun 29 14:47:20 landon-PC kernel: [    0.148923] RTC time: 18:47:05, date: 06/29/14
Jun 29 14:47:20 landon-PC kernel: [    0.774424] Write protecting the kernel read-only data: 2388k
Jun 29 14:47:20 landon-PC kernel: [    0.774425] NX-protecting the kernel data: 4388k
Jun 29 14:47:20 landon-PC kernel: [    3.878704] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jun 29 14:47:25 landon-PC NetworkManager[1200]:    SCPlugin-Ifupdown: update_system_hostname
Jun 29 14:47:25 landon-PC NetworkManager[1200]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, id:Ifupdown (eth0), uuid: 681b428f-beaf-8932-dce4-687ed5bae28e
Jun 29 14:47:33 landon-PC ntpdate[1098]: adjust time server 91.189.89.199 offset -0.403231 sec


```

```
 iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2014-06-29
It is kind of inconclusive. Let's try to get a better look. Please detach the ethernet, reboot and run:```
dmesg > wifi.txt
```Find the file wifi.txt in your user directory and post it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

