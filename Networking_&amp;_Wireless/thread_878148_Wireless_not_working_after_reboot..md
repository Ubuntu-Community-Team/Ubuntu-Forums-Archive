---
title: "Wireless not working after reboot."
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by apostledeets on 2008-08-02
i need help with wireless in ubuntu 8.04. i have an internal atheros 5006/7 card. It works with Windows Wireless Drivers using the net5211.inf driver until i reboot. Upon reboot, it sees the wireless router,  but does not connect to it. I've found that if I uninstall the driver, restart, and reinstall the driver again it works. This is not a long term solution. I shouldn't have to uninstall / reinstall the driver everytime i reboot or shut down the computer. Any suggestions would be greatly appreciated.

Thank you.

---

### Post by monsag on 2008-08-02
> **apostledeets said:**
> i need help with wireless in ubuntu 8.04. i have an internal atheros 5006/7 card. It works with Windows Wireless Drivers using the net5211.inf driver until i reboot. Upon reboot, it sees the wireless router,  but does not connect to it. I've found that if I uninstall the driver, restart, and reinstall the driver again it works. This is not a long term solution. I shouldn't have to uninstall / reinstall the driver everytime i reboot or shut down the computer. Any suggestions would be greatly appreciated.

Thank you.
I do not have an Atheros 5006/7 wireles card, but I had a similar problem before. Though I need not reinstalll any driver for the installed wireless card for my laptop, I had to do Manual Configuration with the Hardy-supplied Network Manager, and re-type my keyphrase afer each reboot.

You may want to try downloading Wicd:

[http://wicd.net/download.php](http://wicd.net/download.php)

I have done the same thing for the wireless Hardy desktops in my office. My laptop has an Intel wireless NIC and the desktops in my workplace have a D-Link PCI wireless cards. Sorry, I do not recall the exact model of the D-Link wireless card.  

It worked for me, and I hope will work for you too.

Mon Sagullo

---

### Post by jualin on 2008-08-02
How did you install your driver?

---

### Post by apostledeets on 2008-08-03
> **monsag said:**
> I do not have an Atheros 5006/7 wireles card, but I had a similar problem before. Though I need not reinstalll any driver for the installed wireless card for my laptop, I had to do Manual Configuration with the Hardy-supplied Network Manager, and re-type my keyphrase afer each reboot.

You may want to try downloading Wicd:

[http://wicd.net/download.php](http://wicd.net/download.php)

I have done the same thing for the wireless Hardy desktops in my office. My laptop has an Intel wireless NIC and the desktops in my workplace have a D-Link PCI wireless cards. Sorry, I do not recall the exact model of the D-Link wireless card.  

It worked for me, and I hope will work for you too.

Mon Sagullo



Thanks, but no go. Installed and couldn't connect at all, so i had to reinstall network manager. Jualin, this is what I used to install the driver.

 For 64-bit Users

1. Blacklist the default driver:

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

2. Download the 64 bit driver

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

3. Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

4. Ensure you have your kernel headers and the build essential package.

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

5. Install ndisgtk

sudo apt-get install ndisgtk

Either use ndisgtk to install the driver or

sudo ndiswrapper -i net5211.inf

6. Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system.

Thank you.

---

### Post by jualin on 2008-08-03
Go to the terminal and run > lsmod and then post the results. This command will list (**ls**) all the modules **(mod)** that your computer is running right now. If you set it up correctly you should have "ndiswrapper" on the list.

---

### Post by jualin on 2008-08-03
> **apostledeets said:**
> 

6. Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system.

Thank you.

I think that step #6 is missing a command since [the community wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Automatically%20loading%20at%20start-up") suggests running an extra command for making it ndiswrapper load the driver when the computer starts. 
And one more question, was the wireless working before restarting the computer? You may also want to check that you installed the driver correctly by running > ndiswrapper -l the "l" is a lower case "L". And then post the results of that too. Good luck!

---

### Post by apostledeets on 2008-08-03
> **jualin said:**
> Go to the terminal and run  and then post the results. This command will list (**ls**) all the modules **(mod)** that your computer is running right now. If you set it up correctly you should have "ndiswrapper" on the list.

apostle@apostlebuntu:~$ lsmod
Module                  Size  Used by
ndiswrapper           243872  0 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ipv6                  311848  12 
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_stats           8416  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
af_packet              27272  2 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
snd_hda_intel         440408  4 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
serio_raw               9092  0 
snd_seq_midi           10688  0 
psmouse                46236  0 
snd_rawmidi            29856  1 snd_seq_midi
video                  23444  8 
output                  5632  1 video
sdhci                  21508  0 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
ricoh_mmc               5120  0 
mmc_core               59272  1 sdhci
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
ac                      8328  0 
wmi_acer               11076  0 
nvidia               8858052  36 
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
snd                    70856  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                16776  0 
i2c_core               28544  1 nvidia
k8temp                  7680  0 
soundcore              10400  1 snd
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
evdev                  14976  7 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
ata_generic             9988  0 
pata_amd               16772  0 
ahci                   33028  2 
ohci1394               36532  0 
ieee1394              106968  2 sbp2,ohci1394
pata_acpi               9856  0 
forcedeth              55564  0 
libata                176432  4 ata_generic,pata_amd,ahci,pata_acpi
scsi_mod              178488  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               41996  0 
ohci_hcd               27524  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  4 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 



apostle@apostlebuntu:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '“blacklist'
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

### Post by jualin on 2008-08-03
Can you post your blacklist file > cat /etc/modprobe.d/blacklist, I think there is something wrong on line 40

---

### Post by jualin on 2008-08-03
And also post the results of > lspci I just want to make sure you installed the correct drivers for your card. I am assuming that your problem is coming from not blacklisting all of the "free drivers" for your card and therefore these are conflicting with ndiswrapper. [This link]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Disable%20Free%20Drivers") says that with Atheros chipsets you have to blacklist 2 modules > If you have an atheros based card, remember to blacklist not only ath_pci, but also ath_hal, since ndiswrapper won't work if ath_hal is still loaded. And since ndiswrapper is complaining of an error in line 40 of the blacklist file maybe there is something there that is supposed to be blacklisted.

---

### Post by apostledeets on 2008-08-03
> **jualin said:**
> Can you post your blacklist file , I think there is something wrong on line 40

apostle@apostlebuntu:~$ cat /etc/modprobe.d/blacklist 
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

“blacklist ath_pci”



apostle@apostlebuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by jualin on 2008-08-03
The error is found on the quotes. You wrote > &#8220;blacklist ath_pci&#8221; and it was supposed to be > blacklist ath_pci, also you need to add the line > blacklist ath_hal at the end of the file. Pretty much make it look like > # This file lists those modules which we don't want to be loaded by
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

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci

blacklist ath_hal Reboot your system and check that it works

---

### Post by apostledeets on 2008-08-03
> **jualin said:**
> The error is found on the quotes. You wrote  and it was supposed to be , also you need to add the line  at the end of the file. Pretty much make it look like  Reboot your system and check that it works

Still not working. Also, since i reinstalled network manager, it no longer shows up on the task bar. any help with that would be greatly appreciated as well.

---

### Post by jualin on 2008-08-03
> **apostledeets said:**
> Still not working. Also, since i reinstalled network manager, it no longer shows up on the task bar. any help with that would be greatly appreciated as well.

> sudo apt-get install gnome-network-manager I am not sure about that command since I am not in my Ubuntu Machine now, but you can also look for "network-manager" in Synaptic Package Manager.

---

### Post by jualin on 2008-08-03
I think you should install Network Manager first and then try again since I am pretty sure that you are almost done with the installation. Just have a little bit more of patience, you almost got it :)

---

### Post by apostledeets on 2008-08-03
> **jualin said:**
> I think you should install Network Manager first and then try again since I am pretty sure that you are almost done with the installation. Just have a little bit more of patience, you almost got it :)

ok. got network manager back to working correctly, but the driver still operates the same, still have to uninstall / restart / reinstall.

---

### Post by jualin on 2008-08-03
Post the results again of > ndiswrapper -l to make sure that the error in line 40 is not there anymore

---

### Post by jualin on 2008-08-03
Can you login in another machine and log in into AIM so I can assist you better and faster? my screen name is jualin289

---

### Post by apostledeets on 2008-08-03
> **jualin said:**
> Post the results again of  to make sure that the error in line 40 is not there anymore

apostle@apostlebuntu:~$ ndiswrapper -l 
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

### Post by mahdisadeghi84 on 2012-10-31
Dear all
I just installed DWA 525(Dlink wireless card) driver on my Ubuntu 12.04 with lots of problem and finally i could connect to the wireless networks.
but after 2 days when i come back to my Ubuntu it was disappear and went back to the time which i didn't install driver!:(
any suggestion?
thank you in advance

---

