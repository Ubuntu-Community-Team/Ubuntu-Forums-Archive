---
title: "Qualcomm Atheros AR242x / AR542x Wireless not working"
date: 2013-10-24
forum: Networking &amp; Wireless
---

### Post by Bryan55 on 2013-10-24
Hi

I have never been able to get the wireless network to work under Ubuntu though it does under Limpus Lite (dual boot)
I have read lot of similar threads but have not found one that is the same as my problem. So I have started with this post in the hope of getting it to work. I could give lots of read out but there are so many and I'm not sure which are relevant. Please ask.
Thanks for any help.


Just upgraded to 12.4

The netbook is a Acer Aspire one ZG5

There is a hardware switch for wifi.

I have tried the search for additional drivers = nothing comes up.

Wifi card is =[FONT=arial]Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

Bryan.[/FONT]

---

### Post by Bryan55 on 2013-10-24
Just noticed the sticky. Now I know what read outs are needed.

lspci
03:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

$ lspci -nn | grep 'Wireless Brand'
no read out

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:e8:00:0a  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fee8:a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2056 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1272491 (1.2 MB)  TX bytes:276932 (276.9 KB)
          Interrupt:44 Base address:0xe000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31109 (31.1 KB)  TX bytes:31109 (31.1 KB)




$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.



$ lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252229  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22528  0 
binfmt_misc            17292  1 
ext2                   67987  1 
joydev                 17393  0 
sparse_keymap          13658  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
acerhdf                14140  0 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
psmouse                96744  0 
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  428092  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
r8169                  56396  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
wmi                    18744  0

$ lsmod | grep "wlan_module_name"
nothing

$ dmesg
This read out is very large but I could not see anything to do with wifi. What should I have seen?

$ sudo lshw -C network
[sudo] password for mhgc: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:e8:00:0a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:51010000-51010fff memory:51000000-5100ffff memory:51020000-5103ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:55200000-5520ffff

$ iwlist scan
lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.

$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

$ lsb_release -d
Description:	Ubuntu 12.04.3 LTS

$ uname -mr
3.2.0-55-generic i686

$ sudo service networking restart
stop: Unknown instance: 
networking stop/waiting

Hope that helps.

Bryan

---

### Post by Bryan55 on 2013-10-29
I'v just tried using a USB stick with 12.04 on and the wifi worked. :p I notice that the kernel was 3.8.0.29(a much later one)
So I updated the netbook one to that but it made no difference.:mad:

Well at lest I know now there must be a way to fix this but how??

I've kept a record of all the readouts while using the USB stick if anyone wants to see them.

One of the pairs of readouts I thought was strange was for  lspci
Why are the different??
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
[COLOR=#000000]03:00.0 Ethernet controller: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)    

Bryan.[/COLOR]

---

### Post by Bryan55 on 2013-11-01
After not get any suggestions from here I went to:
[https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

After using the diagnostic command and placing a question here.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/238420](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/238420)

Found out the ath5k drivers had been blacklisted.

Bryan

---

### Post by cavalier90 on 2014-09-04
Thanks for the pointers. This has just cured the same problem with a friend's Aspire that I've just installed Lubuntu onto.

---

### Post by kieths on 2015-02-18
Thank you very much, Bryan.  Saved a lot of time finding you with the same wireless card I have, with the same problem.  With your info, the fix was as simple as:

   1) Open a terminal
   2) Type:  sudo modprobe ath5k
   3) Enter the admin password
   4) Smile like a Cheshire cat! 

Again, thanks!

---

