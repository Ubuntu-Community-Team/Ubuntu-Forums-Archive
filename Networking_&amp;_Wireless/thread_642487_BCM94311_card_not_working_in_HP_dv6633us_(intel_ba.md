---
title: "BCM94311 card not working in HP dv6633us (intel based)"
date: 2007-12-16
forum: Networking &amp; Wireless
---

### Post by gfd_2 on 2007-12-16
Sorry for the double post - mods if you could delete my other post under hardware/ laptop...

I have an HP 6633us with 120 Gig drive, 2 Gig memory. I've gone through Fedora 8, Mandriva 2007 adn 2008, Puppy 3.1 and Ubuntu 6.06, 7.04, 7.10 (32 bit) and now 7.10 (64 bit). 

I like the Ubuntu system so I'm going to keep banging around until everything is up and running... out of the box there was no sound or wireless.

I ran the two scripts that Anthony Williams (site's down ?) had and I now have sound.

The biggest issue I have is with the wireless.  I've done the Restricted Driver thing, ndiswrappered in at least 5 methods offered here, unintalled Network Manager, tried wifi-radar... no luck.  The blue light for wifi is on and I can see the network but I can't connect... when i open Network Manager and try to connect to the network it times out.  I have zero security on the router so there should be no problems there. 

below are the results of some testing... any/ all suggestions would be greatlyh appreciated... even if it means installing a different distro of Ubuntu.

Thanks in advance!

---

### Post by gfd_2 on 2007-12-16
here's DMESG...

---

### Post by gfd_2 on 2007-12-17
bump

---

### Post by ChuckFoy on 2007-12-17
Hi there,

I have the same machine and the same problems. Would you please link to the solution for the sound?  

I cannot make the wireless work either.  I tried ndiswrapper as well as extracting the f/w with the cutter and loading that via restricted drivers manager but no love.

Thanks!

Chuck

---

### Post by mukul_d on 2007-12-17
Hi,

When I was starting to seriously work on Linux, I came against the same issue. I had always found Ubuntu to be a better distro to work with drivers though I had my share of issues.

I tried the same on Fedora and I finally managed to make it work. Here's the post I put on my website. It is for fedora, but the underlying principle is the same.

[http://www.dharwadkar.com/weblog/linux_wlan_02](http://www.dharwadkar.com/weblog/linux_wlan_02)

---

### Post by gfd_2 on 2007-12-17
> **ChuckFoy said:**
> Hi there,

I have the same machine and the same problems. Would you please link to the solution for the sound?  

I cannot make the wireless work either.  I tried ndiswrapper as well as extracting the f/w with the cutter and loading that via restricted drivers manager but no love.

Thanks!

Chuck

dudemanChuck... sorry, it appears the guy who posted the fix is off-line and his site's not around... and sorry but I can't recall his name... but THANKS TO YOU!

1.) Save the alsa_1.sh file (see below) to whatever directory you'd like.
2.) Save the alsa_2.sh (see below) to the same directory.
2.) Open terminal and sudo chmod a+x alsa_1.sh
3) In terminal  run 'sudo sh alsa_1.sh' (without quotes)  and sit back... it takes about 6 minutes for the script to run. When its done close down terminal and reboot.
4.) Open terminal and run 'sudo sh alsa_2.sh.' (again without quotes) Reboot.
5.) You should have sound.


Good luck! and please let me know if this works... I believe what he did was take the instructions that  number of folks have created and wrote a script to run them... in the correct order and with the correct syntax.

---

### Post by gfd_2 on 2007-12-18
bump - reinstalled 7.10

Any suggestions?

---

### Post by mmichalik on 2007-12-18
Try this post:

[http://ubuntuforums.org/showthread.php?t=640890](http://ubuntuforums.org/showthread.php?t=640890)

I posted it the other day.  I bought a Compaq Presario C700 with that card in it and I posted what I did to get it to work.

The wireless works great now.

---

### Post by ChuckFoy on 2007-12-18
It works!  It works!  It works!

The uname shenanigans were a little sketchy but it works!

Thank you thank you.  

Now I go after the sound problem.

Chuck

---

### Post by ChuckFoy on 2007-12-18
The first script ran okay but the second one returned:

chuck@esposito:~/Documents/sound$ sudo sh alsa_2.sh
cp: cannot stat `/lib/modules/2.6.22-*/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory
'epmod: malformed/unrecognized option '-a
depmod 3.3-pre2 -- part of module-init-tools
depmod -[aA] [-n -e -v -q -V -r -u]
      [-b basedirectory] [forced_version]
depmod [-n -e -v -q -r -u] [-F kernelsyms] module1.ko module2.ko ...
If no arguments (except options) are given, "depmod -a" is assumed

depmod will output a dependancy list suitable for the modprobe utility.


Options:
        -a, --all            Probe all modules
        -A, --quick          Only does the work if there's a new module
        -n, --show           Write the dependency file on stdout only
        -e, --errsyms        Report not supplied symbols
        -V, --version        Print the release version
        -v, --verbose        Enable verbose mode
        -h, --help           Print this usage message

The following options are useful for people managing distributions:
        -b basedirectory
            --basedir basedirectory    Use an image of a module tree.
        -F kernelsyms
            --filesyms kernelsyms      Use the file instead of the
                                       current kernel symbols.
: not found7: 
chuck@esposito:~/Documents/sound$

---

### Post by gfd_2 on 2007-12-18
hmmm... interesting.  I've run it on an Acer 7720 and am currently running it on an HP dv6633us with no problems.  both files run and sound is fully enabled on the headphone and speakers. 

What kind of system are you installing on?

---

### Post by gfd_2 on 2007-12-18
Here's where I am now:
First step, you must uninstall ndiswrapper & bcm43xx-fwcutter 
1.sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get remove bcm43xx-fwcutter 
Add bcm43xx to the /etc/modprobe.d/blacklist file 
2.sudo vim /etc/modprobe.d/blacklist
add this line “blacklist bcm43xx” (without “”) 
3.Reboot 
4.Download driver for BCM94311MCG wlan mini-PCI here ( if this link expire or not found, you can contact me ) 
5.tar -xzvf WLANBroadcom.tar.gz
6.move the folder WLANBroadcom to your home directory
7.mv WLANBroadcom/ /home/yourname/ 
8.Install ndiswrapper from source : 
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz)
tar xvzf ndiswrapper-1.49.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install 
9.Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper 
10.cd /home/yourname/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l 
11.sudo gedit  /etc/modules
add this line “ndiswrapper” (without “”) 
12.sudo modprobe ndiswrapper
13.sudo ndiswrapper -m 
This is what I see now when running a couple of commands:
dcb@dcb-laptop:~$ ndiswrapper -l

bcmwl5 : driver installed

        device (14E4:4311) present (alternate driver: bcm43xx)


dcb@dcb-laptop:~$ lshw -C network

WARNING: you should run this program as super-user.

  *-network               

       description: Wireless interface

       product: BCM94311MCG wlan mini-PCI

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wlan0

       version: 02

       serial: 00:1a:73:d7:d6:fe

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical wireless

       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

  *-network

       description: Ethernet interface

       product: RTL8101E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:06:00.0

       logical name: eth0

       version: 01

       serial: 00:1b:24:e5:4f:dc

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list ethernet physical

       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.46 latency=0 module=r8169 multicast=yes

dcb@dcb-laptop:~$ 


So it looks like the system is seeing my card... when I first boot up the wireless light is flashing away but once the desktop loads the wireless dies out... I can see my network but can't connect.  I also installed WICD was perscribed... it removed Network Manager but even now when I click on the Connect to Wireless it times out after about 30 seconds with no connection.  I setup the wired connection and hit the network with no issues.

Any suggestions?  Thanks in advance... Doug

---

### Post by gfd_2 on 2007-12-19
bump ... any suggestions?

---

### Post by ChuckFoy on 2007-12-20
Both wireless and sound are now working splendidly on my HP dv6633us.  Solutions in this post worked as long as you are sober while performing them.

Chuck

---

### Post by gfd_2 on 2007-12-21
Fresh reinstall today... ran through the install of ndiswrapper and the HP windows driver; all seemed to go well.  Here are the results:

dcb@dcb-laptop:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:d7:d6:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:e5:4f:dc
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.46 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

Now this appears to show that the wifi is disabled... why would that be?  And more importantly... how do I enable it?

Here are the results of some additional commands:

IWCONFIG:
dcb@dcb-laptop:~$ iwconfig 
lo        no wireless extensions. 
eth0      no wireless extensions. 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

IWLIST SCAN:
dcb@dcb-laptop:~$ iwconfig 
lo        no wireless extensions. 
eth0      no wireless extensions. 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

lLSHW -C NETWORK:
dcb@dcb-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 02 
       serial: 00:1a:73:d7:d6:fe 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g 
  *-network 
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1b:24:e5:4f:dc 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 

CAT /ETC/MODPROBE.D/BLACKLIST
dcb@dcb-laptop:~$ cat /etc/modprobe.d/blacklist 
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
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) 
blacklist i2c_i801 
blacklist bcm43xx 
LSMOD:
dcb@dcb-laptop:~$  lsmod 
Module                  Size  Used by 
i915                   30976  2 
drm                   106408  3 i915 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm 
bluetooth              63876  4 rfcomm,l2cap 
ppdev                  11272  0 
acpi_cpufreq           10632  1 
cpufreq_userspace       6048  0 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  1 
cpufreq_stats           8160  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats 
video                  21140  0 
sbs                    21520  0 
container               6400  0 
ac                      7304  0 
battery                12424  0 
button                 10400  0 
dock                   12264  0 
ndiswrapper           233632  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp 
joydev                 13440  0 
snd_hda_intel         378536  1 
snd_pcm_oss            48000  0 
snd_mixer_oss          20352  1 snd_pcm_oss 
snd_pcm                94600  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         13584  2 snd_hda_intel,snd_pcm 
snd_hwdep              12552  1 snd_hda_intel 
snd_seq_oss            39040  0 
snd_seq_midi_event     10240  1 snd_seq_oss 
snd_seq                63776  4 snd_seq_oss,snd_seq_midi_event 
sr_mod                 19876  0 
cdrom                  41768  1 sr_mod 
snd_timer              27656  2 snd_pcm,snd_seq 
snd_seq_device         10772  2 snd_seq_oss,snd_seq 
sdhci                  21004  0 
mmc_core               33416  1 sdhci 
ata_generic             9988  0 
snd                    71720  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device 
serio_raw               9092  0 
psmouse                45596  0 
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp 
intel_agp              30624  1 
soundcore              10272  1 snd 
evdev                  13056  6 
ext3                  146576  1 
jbd                    69360  1 ext3 
mbcache                11272  1 ext3 
sg                     41384  0 
sd_mod                 32512  3 
usbhid                 32576  0 
hid                    33408  1 usbhid 
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394 
ahci                   27012  2 
ata_piix               20996  0 
libata                138928  3 ata_generic,ahci,ata_piix 
scsi_mod              172856  5 sbp2,sr_mod,sg,sd_mod,libata 
r8169                  36100  0 
ehci_hcd               40076  0 
uhci_hcd               29600  0 
usbcore               161584  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd 
thermal                16528  0 
processor              36232  2 acpi_cpufreq,thermal 
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor 

DMESG:
....
[   31.275344] ndiswrapper version 1.45 loaded (smp=yes) 
[   31.364993] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver 
[   31.367016] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[   31.367299] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[   31.367342] PCI: Setting latency timer of device 0000:02:00.0 to 64 
[   31.374292] ndiswrapper: using IRQ 16 
[   31.727984] wlan0: ethernet device 00:1a:73:d7:d6:fe using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf 
[   31.728038] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[   31.732803] usbcore: registered new interface driver ndiswrapper 
...

CAT /ETC/RESOLV.CONF
cb@dcb-laptop:~$ cat /etc/resolv.conf 
# generated by NetworkManager, do not edit! 
search <my router name> 
nameserver 192.x.x.x 
nameserver 192.x.x.x <same IP as previous>

---

