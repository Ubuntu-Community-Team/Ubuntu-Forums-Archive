---
title: "I hate to say it, but networking problems..."
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by twooften on 2008-03-15
I have been searching and troubleshooting for a week, I can see that (what seems like) EVERYONE, is having issues, but I have run into problems that I have not seen in any posts.
I installed 8.04 on an HP Compaq 6515b laptop. 
I initially tried setting up the wireless, it wouldn't find the AP, so I entered the essid manually and it would continually ask me for a passphrase. So far I have read plenty on this problem. 
So I get out a cable and hook it up to the router (D-Link DI-524), internet worked right away. 
Updates started to come in, I did them all hoping that maybe some update might solve wireless problems. After installing updates and doing a reboot, the wireless option disappears from the "System>Admin>Network" Settings window.
Here are the usual output's from the system.

 lshw -C network (There was more info than this the first time that I ran it)

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:91:95:db
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.0.101 latency=0 module=tg3 multicast=yes

ifconfig  (When I ran this the first time I tried the wireless it had a "wlan0" and "wmaster0")

eth0      Link encap:Ethernet  HWaddr 00:1a:4b:91:95:db  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe91:95db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1029531 (1005.4 KB)  TX bytes:142854 (139.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10500 (10.2 KB)  TX bytes:10500 (10.2 KB)

iwconfig (again, there was wmaster0 and wlan0 with a bit of info for wlan0)

lo        no wireless extensions.

eth0      no wireless extensions.

dmesg

[   33.998007] usb usb3: configuration #1 chosen from 1 choice
[   33.998031] hub 3-0:1.0: USB hub found
[   33.998042] hub 3-0:1.0: 2 ports detected
[   34.101964] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 17 (level, low) -> IRQ 20
[   34.101979] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   34.102005] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[   34.102022] ohci_hcd 0000:00:13.2: irq 20, io mem 0xd0603000
[   34.161961] usb usb4: configuration #1 chosen from 1 choice
[   34.161982] hub 4-0:1.0: USB hub found
[   34.161993] hub 4-0:1.0: 2 ports detected
[   34.207863]  sda1 sda2 < sda5 >
[   34.231346] sd 0:0:0:0: [sda] Attached SCSI disk
[   34.235179] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.285885] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 20
[   34.285901] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   34.285925] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[   34.285940] ohci_hcd 0000:00:13.3: irq 20, io mem 0xd0604000
[   34.345844] usb usb5: configuration #1 chosen from 1 choice
[   34.345867] hub 5-0:1.0: USB hub found
[   34.345879] hub 5-0:1.0: 2 ports detected
[   34.449796] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 17 (level, low) -> IRQ 20
[   34.449812] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   34.449834] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[   34.449848] ohci_hcd 0000:00:13.4: irq 20, io mem 0xd0605000
[   34.486245] Attempting manual resume
[   34.486248] swsusp: Resume From Partition 8:5
[   34.486250] PM: Checking swsusp image.
[   34.486385] PM: Resume from disk failed.
[   34.498500] EXT3-fs: INFO: recovery required on readonly filesystem.
[   34.498504] EXT3-fs: write access will be enabled during recovery.
[   34.509781] usb usb6: configuration #1 chosen from 1 choice
[   34.509807] hub 6-0:1.0: USB hub found
[   34.509818] hub 6-0:1.0: 2 ports detected
[   34.613809] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   34.614899] scsi4 : pata_atiixp
[   34.614961] scsi5 : pata_atiixp
[   34.615388] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x5040 irq 14
[   34.615391] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x5048 irq 15
[   34.757558] usb 4-1: new full speed USB device using ohci_hcd and address 2
[   34.933757] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[   34.974528] usb 4-1: configuration #1 chosen from 1 choice
[   35.105647] ata5.00: configured for MWDMA2
[   35.264896] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[   35.264975] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   35.273746] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   35.273751] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   35.282164] Driver 'sr' needs updating - please use bus_type methods
[   35.299223] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   35.299227] Uniform CD-ROM driver Revision: 3.20
[   35.299269] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   36.590991] kjournald starting.  Commit interval 5 seconds
[   36.591171] EXT3-fs: sda1: orphan cleanup on readonly fs
[   36.626377] ext3_orphan_cleanup: deleting unreferenced inode 458826
[   36.650053] ext3_orphan_cleanup: deleting unreferenced inode 12551028
[   36.658143] ext3_orphan_cleanup: deleting unreferenced inode 12550912
[   36.667557] ext3_orphan_cleanup: deleting unreferenced inode 12550913
[   36.667568] ext3_orphan_cleanup: deleting unreferenced inode 12550918
[   36.667577] ext3_orphan_cleanup: deleting unreferenced inode 12550909
[   36.667587] ext3_orphan_cleanup: deleting unreferenced inode 12550915
[   36.667597] ext3_orphan_cleanup: deleting unreferenced inode 12550917
[   36.667606] ext3_orphan_cleanup: deleting unreferenced inode 12550920
[   36.667615] ext3_orphan_cleanup: deleting unreferenced inode 12550914
[   36.667624] ext3_orphan_cleanup: deleting unreferenced inode 12550910
[   36.692135] ext3_orphan_cleanup: deleting unreferenced inode 12550919
[   36.692145] ext3_orphan_cleanup: deleting unreferenced inode 12550916
[   36.692154] ext3_orphan_cleanup: deleting unreferenced inode 12550911
[   36.716059] ext3_orphan_cleanup: deleting unreferenced inode 12485692
[   36.742705] ext3_orphan_cleanup: deleting unreferenced inode 12551993
[   36.756781] ext3_orphan_cleanup: deleting unreferenced inode 12485532
[   36.756794] ext3_orphan_cleanup: deleting unreferenced inode 12551989
[   36.765571] ext3_orphan_cleanup: deleting unreferenced inode 12486952
[   36.783797] ext3_orphan_cleanup: deleting unreferenced inode 12486348
[   36.815161] ext3_orphan_cleanup: deleting unreferenced inode 12619428
[   36.829444] ext3_orphan_cleanup: deleting unreferenced inode 12551981
[   36.835535] ext3_orphan_cleanup: deleting unreferenced inode 12485285
[   36.839633] ext3_orphan_cleanup: deleting unreferenced inode 12486416
[   36.883117] ext3_orphan_cleanup: deleting unreferenced inode 12485659
[   36.890768] ext3_orphan_cleanup: deleting unreferenced inode 12485654
[   36.890894] ext3_orphan_cleanup: deleting unreferenced inode 12487007
[   36.897328] ext3_orphan_cleanup: deleting unreferenced inode 12489084
[   36.914347] ext3_orphan_cleanup: deleting unreferenced inode 12550464
[   36.929520] ext3_orphan_cleanup: deleting unreferenced inode 12550463
[   36.929785] ext3_orphan_cleanup: deleting unreferenced inode 12489099
[   36.941930] ext3_orphan_cleanup: deleting unreferenced inode 12489085
[   36.952134] ext3_orphan_cleanup: deleting unreferenced inode 12486691
[   36.967790] ext3_orphan_cleanup: deleting unreferenced inode 12485045
[   36.975118] ext3_orphan_cleanup: deleting unreferenced inode 12486526
[   36.980130] ext3_orphan_cleanup: deleting unreferenced inode 12486462
[   36.980144] ext3_orphan_cleanup: deleting unreferenced inode 12489078
[   36.980286] ext3_orphan_cleanup: deleting unreferenced inode 12489045
[   36.980299] ext3_orphan_cleanup: deleting unreferenced inode 12489027
[   36.980440] ext3_orphan_cleanup: deleting unreferenced inode 12489006
[   36.980457] ext3_orphan_cleanup: deleting unreferenced inode 12489049
[   36.991497] ext3_orphan_cleanup: deleting unreferenced inode 12488997
[   36.998201] ext3_orphan_cleanup: deleting unreferenced inode 12551984
[   37.005967] ext3_orphan_cleanup: deleting unreferenced inode 12488468
[   37.019717] ext3_orphan_cleanup: deleting unreferenced inode 12551988
[   37.019841] ext3_orphan_cleanup: deleting unreferenced inode 12486830
[   37.032865] ext3_orphan_cleanup: deleting unreferenced inode 12485037
[   37.057405] ext3_orphan_cleanup: deleting unreferenced inode 12490212
[   37.068023] ext3_orphan_cleanup: deleting unreferenced inode 12551977
[   37.068034] ext3_orphan_cleanup: deleting unreferenced inode 12486430
[   37.081731] ext3_orphan_cleanup: deleting unreferenced inode 12486975
[   37.089183] ext3_orphan_cleanup: deleting unreferenced inode 12486668
[   37.097829] ext3_orphan_cleanup: deleting unreferenced inode 12487003
[   37.110028] ext3_orphan_cleanup: deleting unreferenced inode 12489074
[   37.110039] ext3_orphan_cleanup: deleting unreferenced inode 12489062
[   37.121468] ext3_orphan_cleanup: deleting unreferenced inode 12489047
[   37.130772] ext3_orphan_cleanup: deleting unreferenced inode 12489017
[   37.130784] ext3_orphan_cleanup: deleting unreferenced inode 12489003
[   37.130795] ext3_orphan_cleanup: deleting unreferenced inode 12489000
[   37.130806] ext3_orphan_cleanup: deleting unreferenced inode 12488993
[   37.143420] ext3_orphan_cleanup: deleting unreferenced inode 12487035
[   37.150311] ext3_orphan_cleanup: deleting unreferenced inode 12486693
[   37.160063] ext3_orphan_cleanup: deleting unreferenced inode 12488932
[   37.167438] ext3_orphan_cleanup: deleting unreferenced inode 12488931
[   37.167449] ext3_orphan_cleanup: deleting unreferenced inode 12488929
[   37.178800] ext3_orphan_cleanup: deleting unreferenced inode 12485024
[   37.187747] ext3_orphan_cleanup: deleting unreferenced inode 12486797
[   37.187896] ext3_orphan_cleanup: deleting unreferenced inode 12486777
[   37.201722] ext3_orphan_cleanup: deleting unreferenced inode 12485260
[   37.213508] ext3_orphan_cleanup: deleting unreferenced inode 12486550
[   37.213521] ext3_orphan_cleanup: deleting unreferenced inode 12486844
[   37.223860] ext3_orphan_cleanup: deleting unreferenced inode 12488959
[   37.223871] ext3_orphan_cleanup: deleting unreferenced inode 12488958
[   37.223881] ext3_orphan_cleanup: deleting unreferenced inode 12488957
[   37.223891] ext3_orphan_cleanup: deleting unreferenced inode 12488956
[   37.223901] ext3_orphan_cleanup: deleting unreferenced inode 12488955
[   37.223912] ext3_orphan_cleanup: deleting unreferenced inode 12488954
[   37.223922] ext3_orphan_cleanup: deleting unreferenced inode 12488953
[   37.223933] ext3_orphan_cleanup: deleting unreferenced inode 12488952
[   37.236272] ext3_orphan_cleanup: deleting unreferenced inode 12488951
[   37.236283] ext3_orphan_cleanup: deleting unreferenced inode 12488950
[   37.236293] ext3_orphan_cleanup: deleting unreferenced inode 12488949
[   37.236303] ext3_orphan_cleanup: deleting unreferenced inode 12488947
[   37.236314] ext3_orphan_cleanup: deleting unreferenced inode 12488946
[   37.236324] ext3_orphan_cleanup: deleting unreferenced inode 12488945
[   37.236337] ext3_orphan_cleanup: deleting unreferenced inode 12488937
[   37.236488] ext3_orphan_cleanup: deleting unreferenced inode 12487056
[   37.246517] ext3_orphan_cleanup: deleting unreferenced inode 12486646
[   37.246529] ext3_orphan_cleanup: deleting unreferenced inode 12486644
[   37.251968] ext3_orphan_cleanup: deleting unreferenced inode 12486636
[   37.251979] ext3_orphan_cleanup: deleting unreferenced inode 12486626
[   37.251990] ext3_orphan_cleanup: deleting unreferenced inode 12486632
[   37.252146] ext3_orphan_cleanup: deleting unreferenced inode 12486612
[   37.255485] ext3_orphan_cleanup: deleting unreferenced inode 12486634
[   37.268088] ext3_orphan_cleanup: deleting unreferenced inode 12486620
[   37.278997] ext3_orphan_cleanup: deleting unreferenced inode 12486614
[   37.279162] ext3_orphan_cleanup: deleting unreferenced inode 12489013
[   37.289269] ext3_orphan_cleanup: deleting unreferenced inode 12486540
[   37.299065] ext3_orphan_cleanup: deleting unreferenced inode 12551991
[   37.308714] ext3_orphan_cleanup: deleting unreferenced inode 12551985
[   37.308724] ext3_orphan_cleanup: deleting unreferenced inode 12486548
[   37.331961] ext3_orphan_cleanup: deleting unreferenced inode 12618088
[   37.338081] ext3_orphan_cleanup: deleting unreferenced inode 12618089
[   37.338218] ext3_orphan_cleanup: deleting unreferenced inode 12486942
[   37.351388] ext3_orphan_cleanup: deleting unreferenced inode 12486270
[   37.368625] ext3_orphan_cleanup: deleting unreferenced inode 12402712
[   37.427899] ext3_orphan_cleanup: deleting unreferenced inode 9752216
[   37.432772] ext3_orphan_cleanup: deleting unreferenced inode 9752203
[   37.432782] ext3_orphan_cleanup: deleting unreferenced inode 9752195
[   37.432792] ext3_orphan_cleanup: deleting unreferenced inode 9752185
[   37.432803] ext3_orphan_cleanup: deleting unreferenced inode 9748586
[   37.433644] ext3_orphan_cleanup: deleting unreferenced inode 12486266
[   37.476984] ext3_orphan_cleanup: deleting unreferenced inode 12484625
[   37.497329] ext3_orphan_cleanup: deleting unreferenced inode 12649018
[   37.512604] ext3_orphan_cleanup: deleting unreferenced inode 12649016
[   37.512615] ext3_orphan_cleanup: deleting unreferenced inode 12649015
[   37.517457] ext3_orphan_cleanup: deleting unreferenced inode 12649011
[   37.527362] ext3_orphan_cleanup: deleting unreferenced inode 12649014
[   37.534820] ext3_orphan_cleanup: deleting unreferenced inode 12649013
[   37.534832] ext3_orphan_cleanup: deleting unreferenced inode 12649012
[   37.535434] ext3_orphan_cleanup: deleting unreferenced inode 12648954
[   37.574400] ext3_orphan_cleanup: deleting unreferenced inode 12648952
[   37.574410] ext3_orphan_cleanup: deleting unreferenced inode 12648947
[   37.574758] ext3_orphan_cleanup: deleting unreferenced inode 12648945
[   37.579678] ext3_orphan_cleanup: deleting unreferenced inode 12648944
[   37.596967] ext3_orphan_cleanup: deleting unreferenced inode 12486193
[   37.617790] ext3_orphan_cleanup: deleting unreferenced inode 12913215
[   37.631138] ext3_orphan_cleanup: deleting unreferenced inode 12913176
[   37.631293] ext3_orphan_cleanup: deleting unreferenced inode 12913237
[   37.631305] ext3_orphan_cleanup: deleting unreferenced inode 12913159
[   37.631315] ext3_orphan_cleanup: deleting unreferenced inode 12913222
[   37.631325] ext3_orphan_cleanup: deleting unreferenced inode 12913192
[   37.631334] ext3_orphan_cleanup: deleting unreferenced inode 12913174
[   37.631344] ext3_orphan_cleanup: deleting unreferenced inode 12913193
[   37.631354] ext3_orphan_cleanup: deleting unreferenced inode 12913184
[   37.631510] ext3_orphan_cleanup: deleting unreferenced inode 12913133
[   37.631522] ext3_orphan_cleanup: deleting unreferenced inode 12913137
[   37.631531] ext3_orphan_cleanup: deleting unreferenced inode 12913180
[   37.631677] ext3_orphan_cleanup: deleting unreferenced inode 12913103
[   37.631689] ext3_orphan_cleanup: deleting unreferenced inode 12913116
[   37.631698] ext3_orphan_cleanup: deleting unreferenced inode 12913160
[   37.631708] ext3_orphan_cleanup: deleting unreferenced inode 12913166
[   37.631717] ext3_orphan_cleanup: deleting unreferenced inode 12913139
[   37.631727] ext3_orphan_cleanup: deleting unreferenced inode 12913198
[   37.631736] ext3_orphan_cleanup: deleting unreferenced inode 12913189
[   37.631746] ext3_orphan_cleanup: deleting unreferenced inode 12913218
[   37.631755] ext3_orphan_cleanup: deleting unreferenced inode 12913163
[   37.631765] ext3_orphan_cleanup: deleting unreferenced inode 12913208
[   37.631774] ext3_orphan_cleanup: deleting unreferenced inode 12913245
[   37.631784] ext3_orphan_cleanup: deleting unreferenced inode 12913157
[   37.631794] ext3_orphan_cleanup: deleting unreferenced inode 12913202
[   37.631803] ext3_orphan_cleanup: deleting unreferenced inode 12913203
[   37.631813] ext3_orphan_cleanup: deleting unreferenced inode 12913112
[   37.631970] ext3_orphan_cleanup: deleting unreferenced inode 12913252
[   37.631982] ext3_orphan_cleanup: deleting unreferenced inode 12913220
[   37.631991] ext3_orphan_cleanup: deleting unreferenced inode 12913183
[   37.632001] ext3_orphan_cleanup: deleting unreferenced inode 12913179
[   37.632010] ext3_orphan_cleanup: deleting unreferenced inode 12913255
[   37.632020] ext3_orphan_cleanup: deleting unreferenced inode 12913175
[   37.632029] ext3_orphan_cleanup: deleting unreferenced inode 12913173
[   37.632039] ext3_orphan_cleanup: deleting unreferenced inode 12913141
[   37.632048] ext3_orphan_cleanup: deleting unreferenced inode 12913240
[   37.632058] ext3_orphan_cleanup: deleting unreferenced inode 12913161
[   37.632067] ext3_orphan_cleanup: deleting unreferenced inode 12913251
[   37.632077] ext3_orphan_cleanup: deleting unreferenced inode 12913216
[   37.632086] ext3_orphan_cleanup: deleting unreferenced inode 12913170
[   37.632096] ext3_orphan_cleanup: deleting unreferenced inode 12913129
[   37.632106] ext3_orphan_cleanup: deleting unreferenced inode 12913234
[   37.632116] ext3_orphan_cleanup: deleting unreferenced inode 12913227
[   37.632125] ext3_orphan_cleanup: deleting unreferenced inode 12913155
[   37.632137] ext3_orphan_cleanup: deleting unreferenced inode 12913143
[   37.632147] ext3_orphan_cleanup: deleting unreferenced inode 12913172
[   37.632156] ext3_orphan_cleanup: deleting unreferenced inode 12913152
[   37.632167] ext3_orphan_cleanup: deleting unreferenced inode 12913127
[   37.632177] ext3_orphan_cleanup: deleting unreferenced inode 12913156
[   37.632186] ext3_orphan_cleanup: deleting unreferenced inode 12913146
[   37.632196] ext3_orphan_cleanup: deleting unreferenced inode 12913217
[   37.632205] ext3_orphan_cleanup: deleting unreferenced inode 12913250
[   37.632215] ext3_orphan_cleanup: deleting unreferenced inode 12913241
[   37.632225] ext3_orphan_cleanup: deleting unreferenced inode 12913239
[   37.632234] ext3_orphan_cleanup: deleting unreferenced inode 12913107
[   37.632244] ext3_orphan_cleanup: deleting unreferenced inode 12913190
[   37.639802] ext3_orphan_cleanup: deleting unreferenced inode 12845230
[   37.651528] ext3_orphan_cleanup: deleting unreferenced inode 12486985
[   37.667486] ext3_orphan_cleanup: deleting unreferenced inode 12486969
[   37.684682] ext3_orphan_cleanup: deleting unreferenced inode 12486822
[   37.696339] ext3_orphan_cleanup: deleting unreferenced inode 12486821
[   37.709330] ext3_orphan_cleanup: deleting unreferenced inode 12486882
[   37.709343] ext3_orphan_cleanup: deleting unreferenced inode 12486881
[   37.709352] ext3_orphan_cleanup: deleting unreferenced inode 12486820
[   37.724871] ext3_orphan_cleanup: deleting unreferenced inode 12550690
[   37.724996] ext3_orphan_cleanup: deleting unreferenced inode 12486566
[   37.738572] ext3_orphan_cleanup: deleting unreferenced inode 12550577
[   37.738588] ext3_orphan_cleanup: deleting unreferenced inode 12550570
[   37.738723] ext3_orphan_cleanup: deleting unreferenced inode 12486484
[   37.741540] ext3_orphan_cleanup: deleting unreferenced inode 12486486
[   37.749799] ext3_orphan_cleanup: deleting unreferenced inode 12486652
[   37.771735] ext3_orphan_cleanup: deleting unreferenced inode 12616954
[   37.771886] ext3_orphan_cleanup: deleting unreferenced inode 12486850
[   37.781858] ext3_orphan_cleanup: deleting unreferenced inode 12486852
[   37.781870] ext3_orphan_cleanup: deleting unreferenced inode 12486854
[   37.791943] ext3_orphan_cleanup: deleting unreferenced inode 12486988
[   37.801002] ext3_orphan_cleanup: deleting unreferenced inode 12486195
[   37.807808] ext3_orphan_cleanup: deleting unreferenced inode 12487050
[   37.807819] ext3_orphan_cleanup: deleting unreferenced inode 12487052
[   37.829047] ext3_orphan_cleanup: deleting unreferenced inode 12486276
[   37.843767] ext3_orphan_cleanup: deleting unreferenced inode 12486498
[   37.843780] ext3_orphan_cleanup: deleting unreferenced inode 12486669
[   37.856572] ext3_orphan_cleanup: deleting unreferenced inode 12550492
[   37.863151] ext3_orphan_cleanup: deleting unreferenced inode 12488971
[   37.870697] ext3_orphan_cleanup: deleting unreferenced inode 12486568
[   37.879351] ext3_orphan_cleanup: deleting unreferenced inode 12486538
[   37.883723] ext3_orphan_cleanup: deleting unreferenced inode 12486303
[   37.890518] ext3_orphan_cleanup: deleting unreferenced inode 12486301
[   37.908336] ext3_orphan_cleanup: deleting unreferenced inode 12489179
[   37.916318] ext3_orphan_cleanup: deleting unreferenced inode 12486470
[   37.929047] ext3_orphan_cleanup: deleting unreferenced inode 12487058
[   37.938090] ext3_orphan_cleanup: deleting unreferenced inode 12486516
[   37.952610] ext3_orphan_cleanup: deleting unreferenced inode 12486524
[   37.965669] ext3_orphan_cleanup: deleting unreferenced inode 12486534
[   37.965680] ext3_orphan_cleanup: deleting unreferenced inode 12486576
[   37.975144] ext3_orphan_cleanup: deleting unreferenced inode 12486648
[   37.975264] ext3_orphan_cleanup: deleting unreferenced inode 12550640
[   37.987012] ext3_orphan_cleanup: deleting unreferenced inode 12550639
[   38.007124] ext3_orphan_cleanup: deleting unreferenced inode 12486372
[   38.014085] ext3_orphan_cleanup: deleting unreferenced inode 9748518
[   38.057404] ext3_orphan_cleanup: deleting unreferenced inode 12619026
[   38.057417] ext3_orphan_cleanup: deleting unreferenced inode 12619023
[   38.057428] ext3_orphan_cleanup: deleting unreferenced inode 12619021
[   38.057437] ext3_orphan_cleanup: deleting unreferenced inode 12619014
[   38.057447] ext3_orphan_cleanup: deleting unreferenced inode 12619011
[   38.057570] ext3_orphan_cleanup: deleting unreferenced inode 12619007
[   38.057582] ext3_orphan_cleanup: deleting unreferenced inode 12619004
[   38.057593] ext3_orphan_cleanup: deleting unreferenced inode 12618994
[   38.057603] ext3_orphan_cleanup: deleting unreferenced inode 12618997
[   38.057613] ext3_orphan_cleanup: deleting unreferenced inode 12618989
[   38.057623] ext3_orphan_cleanup: deleting unreferenced inode 12618986
[   38.067923] ext3_orphan_cleanup: deleting unreferenced inode 12618985
[   38.080014] ext3_orphan_cleanup: deleting unreferenced inode 12485466
[   38.094106] ext3_orphan_cleanup: deleting unreferenced inode 12619017
[   38.106880] ext3_orphan_cleanup: deleting unreferenced inode 12618979
[   38.106891] ext3_orphan_cleanup: deleting unreferenced inode 12618988
[   38.106901] ext3_orphan_cleanup: deleting unreferenced inode 12618982
[   38.107056] ext3_orphan_cleanup: deleting unreferenced inode 12618964
[   38.107068] ext3_orphan_cleanup: deleting unreferenced inode 12618999
[   38.107079] ext3_orphan_cleanup: deleting unreferenced inode 12618991
[   38.127883] ext3_orphan_cleanup: deleting unreferenced inode 9752316
[   38.127898] ext3_orphan_cleanup: deleting unreferenced inode 9752312
[   38.127908] ext3_orphan_cleanup: deleting unreferenced inode 9752310
[   38.165463] ext3_orphan_cleanup: deleting unreferenced inode 9752308
[   38.165621] ext3_orphan_cleanup: deleting unreferenced inode 9752303
[   38.165632] ext3_orphan_cleanup: deleting unreferenced inode 9752299
[   38.165643] ext3_orphan_cleanup: deleting unreferenced inode 9752297
[   38.165652] ext3_orphan_cleanup: deleting unreferenced inode 9752295
[   38.165663] ext3_orphan_cleanup: deleting unreferenced inode 9752293
[   38.175825] ext3_orphan_cleanup: deleting unreferenced inode 9752290
[   38.193756] ext3_orphan_cleanup: deleting unreferenced inode 9752288
[   38.193767] ext3_orphan_cleanup: deleting unreferenced inode 9752286
[   38.193778] ext3_orphan_cleanup: deleting unreferenced inode 9752282
[   38.202921] ext3_orphan_cleanup: deleting unreferenced inode 12488890
[   38.203077] ext3_orphan_cleanup: deleting unreferenced inode 12488834
[   38.213996] ext3_orphan_cleanup: deleting unreferenced inode 9748499
[   38.235102] ext3_orphan_cleanup: deleting unreferenced inode 12550553
[   38.245717] ext3_orphan_cleanup: deleting unreferenced inode 12485506
[   38.273067] ext3_orphan_cleanup: deleting unreferenced inode 12648601
[   38.278769] ext3_orphan_cleanup: deleting unreferenced inode 12648597
[   38.287981] ext3_orphan_cleanup: deleting unreferenced inode 12648595
[   38.287992] ext3_orphan_cleanup: deleting unreferenced inode 12486946
[   38.300901] ext3_orphan_cleanup: deleting unreferenced inode 12648600
[   38.310376] ext3_orphan_cleanup: deleting unreferenced inode 12648598
[   38.310546] ext3_orphan_cleanup: deleting unreferenced inode 12648594
[   38.322580] ext3_orphan_cleanup: deleting unreferenced inode 12489991
[   38.327308] ext3_orphan_cleanup: deleting unreferenced inode 12489990
[   38.327319] ext3_orphan_cleanup: deleting unreferenced inode 12489989
[   38.327330] ext3_orphan_cleanup: deleting unreferenced inode 12485305
[   38.338576] ext3_orphan_cleanup: deleting unreferenced inode 12486948
[   38.338586] ext3_orphan_cleanup: deleting unreferenced inode 12486944
[   38.348609] ext3_orphan_cleanup: deleting unreferenced inode 9752190
[   38.348621] ext3_orphan_cleanup: deleting unreferenced inode 12486815
[   38.348632] ext3_orphan_cleanup: deleting unreferenced inode 12486288
[   38.348644] ext3_orphan_cleanup: deleting unreferenced inode 12485017
[   38.353692] ext3_orphan_cleanup: deleting unreferenced inode 12486542
[   38.358445] ext3_orphan_cleanup: deleting unreferenced inode 12486695
[   38.358458] ext3_orphan_cleanup: deleting unreferenced inode 12486412
[   38.372093] ext3_orphan_cleanup: deleting unreferenced inode 12486656
[   38.392272] ext3_orphan_cleanup: deleting unreferenced inode 12488257
[   38.405465] ext3_orphan_cleanup: deleting unreferenced inode 12488300
[   38.405479] ext3_orphan_cleanup: deleting unreferenced inode 12488286
[   38.411145] ext3_orphan_cleanup: deleting unreferenced inode 12488284
[   38.427455] ext3_orphan_cleanup: deleting unreferenced inode 12488280
[   38.427603] ext3_orphan_cleanup: deleting unreferenced inode 12488278
[   38.430449] ext3_orphan_cleanup: deleting unreferenced inode 12488272
[   38.436440] ext3_orphan_cleanup: deleting unreferenced inode 12486404
[   38.446536] ext3_orphan_cleanup: deleting unreferenced inode 12486402
[   38.473337] ext3_orphan_cleanup: deleting unreferenced inode 12486317
[   38.483259] ext3_orphan_cleanup: deleting unreferenced inode 12486315
[   38.492329] ext3_orphan_cleanup: deleting unreferenced inode 12486410
[   38.500531] ext3_orphan_cleanup: deleting unreferenced inode 12486355
[   38.506552] ext3_orphan_cleanup: deleting unreferenced inode 12486282
[   38.517366] ext3_orphan_cleanup: deleting unreferenced inode 12488026
[   38.517380] ext3_orphan_cleanup: deleting unreferenced inode 12486343
[   38.533968] ext3_orphan_cleanup: deleting unreferenced inode 12485107
[   38.542998] ext3_orphan_cleanup: deleting unreferenced inode 12486935
[   38.556099] ext3_orphan_cleanup: deleting unreferenced inode 12550578
[   38.556110] ext3_orphan_cleanup: deleting unreferenced inode 12486382
[   38.556238] ext3_orphan_cleanup: deleting unreferenced inode 12484687
[   38.578826] ext3_orphan_cleanup: deleting unreferenced inode 12655046
[   38.593379] ext3_orphan_cleanup: deleting unreferenced inode 12486284
[   38.593392] ext3_orphan_cleanup: deleting unreferenced inode 12486697
[   38.606556] ext3_orphan_cleanup: deleting unreferenced inode 12486311
[   38.619979] ext3_orphan_cleanup: deleting unreferenced inode 12486989
[   38.629821] ext3_orphan_cleanup: deleting unreferenced inode 12486444
[   38.629833] ext3_orphan_cleanup: deleting unreferenced inode 9748544
[   38.636899] ext3_orphan_cleanup: deleting unreferenced inode 12849451
[   38.651410] ext3_orphan_cleanup: deleting unreferenced inode 12488914
[   38.651424] ext3_orphan_cleanup: deleting unreferenced inode 12488919
[   38.657140] ext3_orphan_cleanup: deleting unreferenced inode 12402732
[   38.668256] ext3_orphan_cleanup: deleting unreferenced inode 11386892
[   38.668264] EXT3-fs: sda1: 318 orphan inodes deleted
[   38.668266] EXT3-fs: recovery complete.
[   38.821643] EXT3-fs: mounted filesystem with ordered data mode.
[   46.579135] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   46.739877] Linux agpgart interface v0.102
[   46.808474] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.833261] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.940127] tpm_inf_pnp 00:03: Found C231 with ID IFX0102
[   46.940178] tpm_inf_pnp 00:03: TPM found: config base 0x520, data base 0x530, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   47.049846] parport_pc 00:02: activated
[   47.049851] parport_pc 00:02: reported by Plug and Play ACPI
[   47.050741] parport_pc 00:02: disabled
[   47.176798] input: Power Button (FF) as /devices/virtual/input/input3
[   47.207256] ACPI: Power Button (FF) [PWRF]
[   47.207474] input: Sleep Button (CM) as /devices/virtual/input/input4
[   47.239242] ACPI: Sleep Button (CM) [C28D]
[   47.239333] input: Lid Switch as /devices/virtual/input/input5
[   47.275524] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   47.415322] ACPI: Lid Switch [C265]
[   47.416137] ACPI: AC Adapter [C1EB] (on-line)
[   47.444293] Yenta: CardBus bridge found at 0000:02:04.0 [103c:30c2]
[   47.457643] ACPI: Battery Slot [C1ED] (battery present)
[   47.457874] ACPI: Battery Slot [C1EC] (battery absent)
[   47.458370] ACPI: WMI-Acer: Mapper loaded
[   47.572048] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   47.572053] Socket status: 30000006
[   47.572055] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   47.572060] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd03fffff
[   47.613570] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   47.671246] ACPI: Video Device [C08D] (multi-head: yes  rom: no  post: no)
[   48.451387] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   48.594319] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   48.594325] serio: Synaptics pass-through port at isa0060/serio4/input0
[   48.634135] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   49.900675] cs: IO port probe 0x100-0x3af: clean.
[   49.902611] cs: IO port probe 0x3e0-0x4ff: clean.
[   49.903418] cs: IO port probe 0x820-0x8ff: clean.
[   49.904087] cs: IO port probe 0xc00-0xcf7: clean.
[   49.904790] cs: IO port probe 0xa00-0xaff: clean.
[   50.460690] lp: driver loaded but no devices found
[   50.578049] Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1 across:2650684k
[   51.207822] EXT3 FS on sda1, internal journal
[   52.562870] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.058365] No dock devices found.
[   53.386337] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[   53.386235] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[   53.386239] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[   53.386241] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   53.386244] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   53.386286] powernow-k8: ph2 null fid transition 0xb
[   54.677545] ppdev: user-space parallel port driver
[   54.986621] audit(1205623861.637:2): operation="inode_permission" request_mask="a::" denied_mask="a::" name="/dev/tty" pid=5195 profile="/usr/sbin/cupsd" namespace="default"
[   55.037009] apm: BIOS not found.
[   55.803053] Clocksource tsc unstable (delta = -280168633 ns)
[   56.186481] Bluetooth: Core ver 2.11
[   56.186959] NET: Registered protocol family 31
[   56.186962] Bluetooth: HCI device and connection manager initialized
[   56.186966] Bluetooth: HCI socket layer initialized
[   56.205272] Bluetooth: L2CAP ver 2.9
[   56.205277] Bluetooth: L2CAP socket layer initialized
[   56.241445] Bluetooth: RFCOMM socket layer initialized
[   56.241459] Bluetooth: RFCOMM TTY layer initialized
[   56.241461] Bluetooth: RFCOMM ver 1.8
[   56.823328] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   56.823334] tg3: eth0: Flow control is off for TX and off for RX.
[   57.567189] [drm] Initialized drm 1.1.0 20060810
[   58.853143] tg3: eth0: Link is down.
[   61.076280] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   61.076287] tg3: eth0: Flow control is off for TX and off for RX.
[   62.733568] hda-intel: Invalid position buffer, using LPIB read method instead.
[   64.597806] tg3: eth0: Link is down.
[   65.296720] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   65.296727] tg3: eth0: Flow control is off for TX and off for RX.
[   67.652161] NET: Registered protocol family 10
[   67.652387] lo: Disabled Privacy Extensions
[   71.862775] eth0: no IPv6 routers present
[   71.900309] CPU0 attaching NULL sched-domain.
[   71.900315] CPU1 attaching NULL sched-domain.
[   71.908234] CPU0 attaching sched-domain:
[   71.908239]  domain 0: span 03
[   71.908241]   groups: 01 02
[   71.908244] CPU1 attaching sched-domain:
[   71.908246]  domain 0: span 03
[   71.908247]   groups: 02 01
[  122.780492] APIC error on CPU0: 00(40)
[  122.780183] APIC error on CPU1: 00(40)
[  157.630427] tg3: eth0: Link is down.
[  158.312139] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  158.312146] tg3: eth0: Flow control is off for TX and off for RX.
[  191.860873] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  191.860879] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  191.860882] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[  281.113524] tg3: eth0: Link is down.
[  283.258088] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  283.258095] tg3: eth0: Flow control is off for TX and off for RX.
[  285.544998] tg3: eth0: Link is down.
[  286.263360] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  286.263367] tg3: eth0: Flow control is off for TX and off for RX.
[  324.803602] tg3: eth0: Link is down.
[  326.899233] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  326.899240] tg3: eth0: Flow control is off for TX and off for RX.
[  329.362945] tg3: eth0: Link is down.
[  330.067556] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  330.067559] tg3: eth0: Flow control is off for TX and off for RX.
[  521.381054] APIC error on CPU0: 40(40)
[  521.380615] APIC error on CPU1: 40(40)
[  697.145000] APIC error on CPU0: 40(40)
[  697.144401] APIC error on CPU1: 40(40)
[ 1240.170872] tg3: eth0: Link is down.
[ 1242.265682] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1242.265688] tg3: eth0: Flow control is off for TX and off for RX.
[ 1244.644695] tg3: eth0: Link is down.
[ 1245.347649] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1245.347655] tg3: eth0: Flow control is off for TX and off for RX.
[ 6060.423564] tg3: eth0: Link is down.
[ 6069.340253] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 6069.340260] tg3: eth0: Flow control is off for TX and off for RX.
[ 6092.652384] APIC error on CPU0: 40(40)
[ 6092.650072] APIC error on CPU1: 40(40)
[ 6227.247984] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6227.503096] NET: Registered protocol family 17
[ 6227.890716] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 6227.890720] tg3: eth0: Flow control is off for TX and off for RX.
[ 6227.891949] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 6233.556077] eth0: no IPv6 routers present


So I am hoping that someone can see something that I am not seeing in all of that.

---

