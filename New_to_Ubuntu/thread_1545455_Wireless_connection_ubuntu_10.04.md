---
title: "Wireless connection ubuntu 10.04"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by Dr.JakeDaSnake on 2010-08-03
Hi guys,
I just finished installing Ubuntu 10.04 onto my usb flashdrive (do not want to install onto computer). I made it to where the USB is first on my BIOS so it's running very well on my computer. Although everything seemed to work well, my internet connection is really getting to me. Right now it is saying that, although i've enabled everything, there are no internet/wifi locations anywhere (even though i'm literally five feet from my router). I then get a weird icon saying that i need to download some wireless driver software (2 to be exact). I tried downloading them but they both say that they cannot finish the process. I'm becoming quite disturbed and wondering if anybody can help out. Thanks!
 
 
p.s. i heard 9.10 was better... but i can't find it on the website! AND idk if i should just uninstall and delete everything and start all over (but i really don't want to do that because it took me the entire day to download ubuntu)

---

### Post by ubunterooster on 2010-08-03
You need to connect via wired ethernet and then install the drivers 

as for 9.10: [http://releases.ubuntu.com/9.10/](http://releases.ubuntu.com/9.10/)

---

### Post by jtarin on 2010-08-03
In a terminal issue the command ```
lspci
``` post results.
In a terminal issue the command ```
lsmod
``` post results.
In a terminal issue the command ```
ifconfig
``` 
post results.

What is your router make and model? Can you connect to your router through your web browser?

> I'm becoming quite disturbedM-m-m-m....how disturbed?:-k

---

### Post by Dr.JakeDaSnake on 2010-08-04
Before i put in the code... i just wanted to answer the last part of ur question: my router's brand is cisco and under it there is "linksys" i don't know much about it... anyway i will soon reply with the results... 
 
and i am really disturbed :P haha

---

### Post by Dr.JakeDaSnake on 2010-08-04
ALRIGHT  i got the results and here they are: 
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.1 IDE interface: ATI Technologies Inc SB600 IDE[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ lsmod[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Module                  Size  Used by[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]binfmt_misc             6587  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ppdev                   5259  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lp                      7028  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]parport                32635  2 ppdev,lp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dm_crypt               11331  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_codec_idt      51914  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]joydev                  8708  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_intel          21877  2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_hwdep               5412  1 snd_hda_codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_pcm_oss            35308  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_mixer_oss          13746  1 snd_pcm_oss[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_dummy           1338  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_oss            26726  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_midi            4557  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_rawmidi            19056  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]arc4                    1153  2 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_timer              19098  2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]b43                   157218  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mac80211              204922  1 b43[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]b44                    25542  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]cfg80211              126485  2 b43,mac80211[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dell_wmi                1793  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]psmouse                63245  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]sdhci_pci               5470  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]sdhci                  15462  1 sdhci_pci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]soundcore               6620  1 snd[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dell_laptop             6856  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]led_class               2864  2 b43,sdhci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ricoh_mmc               2923  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mii                     4381  1 b44[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]serio_raw               3978  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dcdbas                  5422  1 dell_laptop[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]i2c_piix4               8335  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]snd_page_alloc          7076  2 snd_hda_intel,snd_pcm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ssb                    37336  2 b43,b44[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]shpchp                 28820  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]k8temp                  3024  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]squashfs               20680  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]aufs                  149050  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]nls_iso8859_1           3249  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]nls_cp437               4919  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]vfat                    8901  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]fat                    47767  1 vfat[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dm_raid45              81647  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]xor                    15028  1 dm_raid45[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]fbcon                  35102  71 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]tileblit                2031  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]font                    7557  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]bitblit                 4707  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]softcursor              1189  1 bitblit[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]vga16fb                11385  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]vgastate                8961  1 vga16fb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]radeon                674135  3 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ttm                    49943  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]drm_kms_helper         29297  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]usb_storage            39425  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ati_agp                 5094  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]drm                   162471  5 radeon,ttm,drm_kms_helper[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]i2c_algo_bit            5028  1 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]pata_atiixp             3148  0 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]agpgart                31724  3 ttm,ati_agp,drm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ahci                   32008  1 [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ ifconfig[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:15:c5:c5:ac:db  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          Interrupt:21 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:92 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:7072 (7.0 KB)  TX bytes:7072 (7.0 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]idk what ANY of this means so if u can decipher plz help haha[/SIZE][/FONT]

---

### Post by jtarin on 2010-08-04
OK it appears that you have modules for your cards, but you need to download updated ones to get your wireless working so you need a hard-wire connection.Your "ifconfig" shows your ethernet card recognized so lets see if we can get that up.How do you connect through Ethernet? Modem? Router?

Try the first command and then run ifconfig to see if eth0 has an IP address.

Start the network interface eth0:
```
ifup eth0
```


Stop the network interface eth0:
```
ifdown eth0 
```

---

### Post by Dr.JakeDaSnake on 2010-08-04
I know this sounds ignorant buy i do not know the difference between a modem, ethernet, and router. I just know that i have this little thing in my house that we all connect to through wifi. Anyway, i performed the commands and these were my results:
 
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ ifup eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ifup: failed to open statefile /var/run/network/ifstate: Permission denied[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:15:c5:c5:ac:db  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:21 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:28 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ ifdown eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ifdown: failed to open statefile /var/run/network/ifstate: Permission denied[/SIZE][/FONT]

---

### Post by jtarin on 2010-08-05
I neglected to tell you to preface those commands as "sudo"

```
sudo  ifup eth0
```

---

### Post by yifangt on 2010-10-11
I believe Ubuntu 10.04 is of problem for the wireless connection, which disturbed me for more than 2 months now and I tried all the methods I could find. Some worked, some did not! Sometimes some worked, sometimes no! I am waiting for a new update Ubuntu 11. Another 6~10 months? Not sure! I started to suspect if Linux is on the right track, at least Ubuntu. Or free softwares are only a dream? 

Ivan

---

### Post by yifangt on 2010-10-11
I believe Ubuntu 10.04 is of problem for the wireless connection, which disturbed me for more than 2 months now. The problem arose from my updating from 9.10 to 10.04. The network was fine before the updating. After that the wireless connection never worked well but all the hardware is for sure fine and the driver seems right too. I tried all the methods I could find, especially the one from this forum. Some worked, some did not! Sometimes some worked, sometimes no! I am waiting for a new update Ubuntu 11. Another 6~10 months? Not sure! I started to suspect if Linux is on the right track, at least Ubuntu. Or free softwares are only a dream? 

Ivan

---

### Post by anewguy on 2010-10-11
There are a few ways to get this working, but since it sounds like you don't have a lot of knowledge (and that's OK!!!) the easiest method has already been suggested:

- hard-wire your computer to your router
- in a terminal window type sudo apt-get update
- check in System/Administration/Drivers for the driver(s) for your wireless and enable them
- physically disconnect the hard-wire connection

If this is something you don't understand or are not comfortable with, it would do you well to find a friend, neighbor, etc., who is a little more knowledgable and understands what we are saying.  To have someone physically there with you to see the equipment at hand would be the best for you.

There are other ways to get this working that do not require any type of connection to the internet.  If you are so inclined, please locate the Windows XP driver files (.inf and .sys) for your wireless adapter (they are probably something similar to bcml5a.inf and .sys).  Once you have those files, post back and I can walk you through installing them very easily.

Dave ;)

---

