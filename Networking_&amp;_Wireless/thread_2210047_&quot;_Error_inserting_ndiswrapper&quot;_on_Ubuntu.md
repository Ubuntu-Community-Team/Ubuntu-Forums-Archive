---
title: "&quot; Error inserting ndiswrapper&quot; on Ubuntu 12.04"
date: 2014-03-08
forum: Networking &amp; Wireless
---

### Post by shane15 on 2014-03-08
im bloody sick and tired of getting this message everytime i install updates on ubuntu 12.04 
Module could not be loaded. Error was:


FATAL: Error inserting ndiswrapper (/lib/modules/3.8.0-37-generic/updates/dkms/ndiswrapper.ko): Invalid module format

can somebody please help me

---

### Post by praseodym on 2014-03-08
For which device? Please show
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by shane15 on 2014-03-08
shane@ubuntu:~$ lspci -nnk | grep -iA2 net
02:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff31]
	Kernel modules: 8139too, 8139cp
02:04.0 Ethernet controller [0200]: InProComm Inc. IPN 2220 802.11g [17fe:2220]
	Subsystem: AMBIT Microsystem Corp. Device [1468:0310]
shane@ubuntu:~$ lsusb
Bus 001 Device 005: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
shane@ubuntu:~$ lsmod
Module                  Size  Used by
ppp_deflate            12878  0 
zlib_deflate           26622  1 ppp_deflate
bsd_comp               12842  0 
ppp_async              17307  1 
crc_ccitt              12627  1 ppp_async
option                 33795  1 
usb_wwan               14859  1 option
usbserial              27633  5 option,usb_wwan
usb_storage            48053  0 
bnep                   17919  2 
rfcomm                 38400  0 
snd_intel8x0           33458  2 
bluetooth             211586  10 bnep,rfcomm
snd_ac97_codec        110254  1 snd_intel8x0
parport_pc             27612  0 
ac97_bus               12670  1 snd_ac97_codec
ppdev                  12849  0 
i915                  554804  2 
snd_pcm                85934  2 snd_intel8x0,snd_ac97_codec
lp                     17455  0 
snd_seq_midi           13132  0 
parport                40930  3 parport_pc,ppdev,lp
snd_rawmidi            25157  1 snd_seq_midi
pcmcia                 39854  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         47749  1 i915
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27427  0 
drm                   233935  3 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia_rsrc            18367  1 yenta_socket
joydev                 17329  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                17048  0 
snd                    57014  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                82769  0 
i2c_algo_bit           13316  1 i915
soundcore              12600  1 snd
shpchp                 32265  0 
snd_page_alloc         18398  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
serio_raw              13031  0 
sbs                    13402  0 
video                  19116  1 i915
sbshc                  13575  1 sbs
microcode              18433  0 
binfmt_misc            17292  1 
shane@ubuntu:~$ iwconfig
ppp0      no wireless extensions.


lo        no wireless extensions.

---

### Post by praseodym on 2014-03-09
RUn these commands:
```

echo 8139too | sudo tee -a /etc/modules
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
``` 
Reboot, LAN should work.

Now run
```

sudo apt-get install --reinstall ndiswrapper-dkms ndisgtk linux-headers-generic build-essential
sudo modprobe -v ndiswrapper
dmesg | grep ndis
```

---

