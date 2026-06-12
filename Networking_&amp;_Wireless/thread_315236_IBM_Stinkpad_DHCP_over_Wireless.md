---
title: "IBM Stinkpad DHCP over Wireless"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by Bingo on 2006-12-08
I am at wits end.

IBM T21 Laptop with a pcmica Cisco Aironet 350

After going thru everything I could find here I am unable to get this thing to grab a dhcp address from my DI-614+ router.

One strange thing is that I have a phantom wifi0 adapter listed...that basically mirrors my eth1.  I dont know what to do next.

I can see my router in lshw eth1 scan.

Please help.
thanks in advance.

---

### Post by Sir_stox on 2006-12-09
I also have an T30 2366-85U with a cisco wireless router. I have just installed 6.10 and was having the same sort of issue. 

I could not figure out which was the right one, Thought that it could be the infared port showing up see attached picture... Here is what I did to resolve the issue, I had to configured both connections to use the wireless network router name, also change the router security to wep - 10 Hex digits and copy and paste the key into both Wifi0 & eth1. 

Not sure if it has anything to do with the router, I am using a Linsys updated with Firmware: DD-WRT v23 SP1 Final (05/16/06) mini.

It did allow me to move to 26 HEx, but disabling either Wifi0 or Eth1 will not allow the connection to the router.

Thanks & good luck 
Sir Stox
[www.stoxservices.com](www.stoxservices.com)

[ATTACH]20764[/ATTACH]

---

### Post by Bingo on 2006-12-09
Thanks, I tried that as well...no luck.

> 
/etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

#auto ath0
#iface ath0 inet dhcp


iface eth1 inet dhcp
wireless-essid funkzilla317
wireless-channel 7
wireless-key xxxxxxxxxx

auto eth1

iface wifi0 inet dhcp
wireless-essid funkzilla317
wireless-channel 7
wireless-key xxxxxxxxxx

auto wifi0


I can scan with eth1 and see my AP but not with the phantom wifi0

I know this topic is beat to death, but I really want to get this thing working.  

Thanks in advance.

---

### Post by FrodoB on 2006-12-09
I believe that you can safely ignore the wifi0 device for the time being.

Wifi0 is used for raw packet capture in tools like Kismet.

---

### Post by nijinsky on 2006-12-09
I had the same problem with 6.10 and vector linux. iwlist scan listed all the routers in my area but I couldn't connect.

I beleive WPA is the problem.

I have WPA here at home so I put xandros on the T30 (linksys pcmcia G card) and it was connected using WPA in 1 minute.

Linux working is better for me than going back to windows again. Well worth the $79

cheers
bob

---

### Post by Bingo on 2006-12-09
Thanks to all...still no go.  I tried to ignore the wifi0 at the start, but it still keeps showing up.

As for the WPA, I am not using it, I do have WEP setup...but it was doing this without it as well.

I went thru all the steps in the troubleshooting guide before I decided to bug the general population with my lack of Linux skill.

Again, I can scan, see my AP, but no dhcp.  I tried static and that does not work either.

---

### Post by neoflight on 2006-12-09
> **Bingo said:**
> Thanks, I tried that as well...no luck.

I can scan with eth1 and see my AP but not with the phantom wifi0

I know this topic is beat to death, but I really want to get this thing working.  

Thanks in advance.

Please try these:

1. install network-manager-gnome if you can connect wired
2. comment out everything from /etc/network/interfaces except instances of 'lo'.
keep just these..

> auto lo
iface lo inet loopback 
3. then restart the network ```
sudo /etc/init.d/networking restart
```
4. see in the sessions (system>preferences>sessions> current tab) and find whether nm-applet is running

---

### Post by Bingo on 2006-12-09
Ok I have installed the network-manager, commented out all interfaces but the lo, restarted networking...checked sessions and I see:

nm-applet --sm disable running

what should I do now?

thanks in advance

---

### Post by neoflight on 2006-12-09
> **Bingo said:**
> Ok I have installed the network-manager, commented out all interfaces but the lo, restarted networking...checked sessions and I see:

nm-applet --sm disable running

what should I do now?

thanks in advance

ok. do u see an icon in the task panel? click on that and see if it shows 'ur' wireless? if yes select that and it will try to connect and will pop up a window to enter wep or wpa key. from ur post, WEP   key is the hexadecimal one. enter that and see if u can connect.

you might be asked to enter a password for the keyring. the key  is stored in the keyring which u are providing a password protection. create one if it asks. you will require to enter this password to let the manager to access the key stored in the keyring. the file is  '.gnome2/keyrings/default.keyring' (invisible folder in the home dir. ctrl+h will show it). if you mess up entering the password then just delete that file and the next time you will be prompted again to create one. 

if the icon doesnt show up in the first place try restarting the machine and see if it comes up. 
hope this helps

---

### Post by Bingo on 2006-12-09
I get the icon, but all it says is "wired network"  my wireless does not show up at all.

---

### Post by neoflight on 2006-12-09
> **Bingo said:**
> I get the icon, but all it says is "wired network"  my wireless does not show up at all.

oh.. i forgot to tell u....just disconnect the ethernet cable and restart the network following the previous post. (not good to try using 2 network devices simultaneously.)

edit: you should set up the router such that it **transmits** the essid.

select system>administration>networking and disable the wireless connection. coz, we are letting the nm-applet to do the work. so it should show ; under wireless network that  " this interface is not configured"....try this and let us know...

---

### Post by Bingo on 2006-12-09
Ok.  Booted sans cat5.  This time the icon lists three access points (mine included). Network-manager icon spins then stops with a little exclaimation icon on it.

I looked at connection information and it says I am connected to:
Wireless internet (eth1)
Speed: 11Mb/s
Driver: airo_cs

other than that everything is coming up zeros.  I am still not getting dhcp to pass me an address.

I really appreciate your help, dont give up on me yet.

any other ideas?

thanks in advance

---

### Post by neoflight on 2006-12-09
make sure that u disabled the wired network too from 
system>admi..>networking

sometimes it happens... 
whats the output of ifconfig?

and iwconfig (here replace ur ESSID: with "xxxxxx" for privacy)

---

### Post by Bingo on 2006-12-09
ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:10:A4:78:1D:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1094832 (1.0 MiB)  TX bytes:256979 (250.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:0F:8F:57:5E:F7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:10158 dropped:0 overruns:0 frame:10158
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3294 (3.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

iwconfig:
eth0      Link encap:Ethernet  HWaddr 00:10:A4:78:1D:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1094832 (1.0 MiB)  TX bytes:256979 (250.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:0F:8F:57:5E:F7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:10158 dropped:0 overruns:0 frame:10158
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3294 (3.2 KiB)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


it will not grab an ip, so it looks to be quitting at that...my ap doesnt seem to be showing up in iwconfig after the network-manager stops spinning.

thanks for all your help...I am still stuck.

thanks in advance.

---

### Post by neoflight on 2006-12-09
i think there is some problem here... still hope though.
lets start over.

1. disconnect the ethernet cable

2. make sure that u disable all network from sys > admi..> networking. click the DNS tab and delete if there are any entries.

3. keep only the 'lo' instances in /etc/network/interfaces file.

4. restart the system and see if it automatically start detecting ur wireless.. see if clicking the icon brings up ur wireless.

5. it will and then try connecting...then run iwconfig even if it fails...

6. find out the output of ```
ping 192.168.0.1
```

7. ```
route
```

a typical result of iwconfig is like this...

```

icecube@icecube:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"##############"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:xx:xx:xx:xx:A1   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/100  Signal level=-36 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:9

sit0      no wireless extensions.

```

this is what we are looking for. we want to see if the wireless device is up and running...

---

### Post by Bingo on 2006-12-09
no luck.  On restart network-manager cycles for a while then craps out with the little exclaimation mark. 

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=1/100  Signal level=-91 dBm  Noise level=-89 dBm
          Rx invalid nwid:352  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:22  Invalid misc:3196   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=1/100  Signal level=-91 dBm  Noise level=-89 dBm
          Rx invalid nwid:352  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:22  Invalid misc:3196   Missed beacon:0

**ping 192.168.0.1**
connect: Network is unreachable

**route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


worst of all the phantom wifi0 is back.  without network-manager I was able to get the card to see and associate to my AP, it just would not grab an IP...network-manager sees my AP and asks for all the security info, just wont connect. 

I was really excited to find ubuntu and wish I could get past this one hurdle.  Thanks again for all your help.

I am willing to try anything at this point.

thanks in advance

---

### Post by neoflight on 2006-12-09
i wonder why its not giving anything for the route command..

you are close... just make the router give an ip...

you cannot even ping the router...so its not connected...
can u connect wireless using windows? any other open wireless network around you can connect? just for testing?

look in [_this_](http://ubuntuforums.org/showthread.php?t=309569&highlight=Kernel+IP+routing+table") thread too
and [_here_]("http://ubuntuforums.org/showthread.php?t=312543&highlight=Kernel+IP+routing+table")

i dont know too much beyond this point. mostly this is what i did to solve my problem... it also heavily depends on the router and the wireless card we are using...

edit: there are many threads addressing the network problem [_here_]("http://ubuntuforums.org/forumdisplay.php?f=136") refer this thread in one of those post where some experts will be of more help....

---

### Post by FrodoB on 2006-12-09
Just ignore wifi0, don't worry about it. It is a part of the driver that you will not be using at the moment.

---

### Post by Bingo on 2006-12-09
Yes I have several other Windoze boxes connected wirelessly to this AP...thing spits out ips left and right..just not to this thing.

I will look at those posts...I have been crawln this forum for a week and a half, not wanting to bug anyone and find my own fix..but no luck.

Thanks...if you think of anything else let me know you have been great.

---

### Post by Bingo on 2006-12-09
I guess I am stuck at why I can get dhcp over wire, but not wirelessly.  I like the functionality that network-manager seems to provide (if I can ever get connected)...but this is dhcp thing has me hung.

---

### Post by FrodoB on 2006-12-09
Usually this means that you are not using the exact same WEP keys on the Access Point and the client machine.

---

### Post by FrodoB on 2006-12-09
Go to this WEP key generator and make some 128bit keys and it will give you the same key in both formats. Save these in a text file and paste them into your access point and your computer workstations:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Examples:

ASCII:
a*ozW8Ex3iDq_

HEX:
612a6f7a57384578336944715f

This is the exact same key in the two formats.

Put these in your access point and clients and then re-test.

---

### Post by AgenT on 2006-12-09
This has nothing to do with your Thinkpad being broken or Linux not supporting your card. The network card is buggy. I had the exact same problem and while it is fixable, I decided to just buy a new IBM network card and replace the existing one with it (then sell the old one and break about even). Notice how there are two wireless cards shown. This is because the network card has bad hardware specifications in its BIOS. This confuses Linux into thinking there are two network cards which cause conflicts.

What is the output of these commands:
```
lsmod
lspci
lshw
```(please post each output separately and in code tags)

---

### Post by FrodoB on 2006-12-09
There are two interfaces because that is how the Aironet driver is designed. I am typing this through one now.

---

### Post by Bingo on 2006-12-09
I tried the new keys...still a no-go.  So I went a step further and nuked the WEP altogher.

Network-manager cycles down the wired connection, attempts to connect to the AP then pushes me back down the wire.  It has to be that it is not getting an IP from the router.  

Any ideas why I can get DHCP wired, but not wireless?

This is killing me.  Wife already wants to take a hammer to this laptop (I get kind of crazy when tech gets the best of me)

Thanks in advance

---

### Post by FrodoB on 2006-12-09
You don't have MAC filtering turned on in the router do you?

---

### Post by Bingo on 2006-12-09
No MAC filter on

---

### Post by Bingo on 2006-12-09
What is the output of these commands:
**lsmod**
```
Module                  Size  Used by
af_packet              24584  2 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nvram                  10376  1 
uinput                 10368  1 
savage                 35200  2 
drm                    74644  3 savage
speedstep_smi           7184  0 
speedstep_lib           5764  1 speedstep_smi
cpufreq_userspace       5408  1 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_smi,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
ibm_acpi               28672  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
lp                     12964  0 
aes                    28864  1 
irtty_sir              10112  0 
tsdev                   9152  0 
sir_dev                18308  1 irtty_sir
airo_cs                 7552  1 
airo                   78496  1 airo_cs
nsc_ircc               25100  0 
irda                  214332  3 irtty_sir,sir_dev,nsc_ircc
snd_cs46xx             89448  1 
gameport               17160  2 snd_cs46xx
floppy                 63044  0 
psmouse                41352  0 
serio_raw               8452  0 
snd_rawmidi            27264  1 snd_cs46xx
snd_seq_device          9868  1 snd_rawmidi
crc_ccitt               3200  1 irda
evdev                  11392  2 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_ac97_codec         97696  1 snd_cs46xx
snd_ac97_bus            3456  1 snd_ac97_codec
pcmcia                 40380  1 airo_cs
i2c_piix4              10000  0 
pcspkr                  4352  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_core               23424  2 i2c_ec,i2c_piix4
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
e100                   38020  0 
mii                     6912  1 e100
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
yenta_socket           28812  4 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd                    58372  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_cs46xx,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  2 uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
```

**lspci**
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)
```

**lshw**
```
bingo-laptop              
    description: Notebook
    product: 2648ED7
    vendor: IBM
    version: Not Available
    serial: 78KHN96
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=notebook uuid=FF5B0A81-449A-11CB-BDFC-F2AA7E7C4495
  *-core
       description: Motherboard
       product: 2648ED7
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1HRZ16D1U2
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: KZET26WW (1.07 ) (05/15/2001)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect pcmciaboot edd int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.8.10
          slot: None
          size: 650MHz
          capacity: 800MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 256KB
             capacity: 256KB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 256MB
          capacity: 1GB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 256MB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous [empty]
             physical id: 1
             slot: DIMM 2
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 86C270-294 Savage/IX-MV
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 13
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f0000000-f7ffffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50000000-50000fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1450
             vendor: Texas Instruments
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50100000-50100fff irq:11
           *-network
                description: Cisco Systems
                physical id: 0
                version: 350 Series Wireless LAN Adapter
                slot: Socket 1
                resources: irq:3
        *-network
             description: Ethernet interface
             product: 82557/8/9 [Ethernet Pro 100]
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@00:03.0
             logical name: eth0
             version: 09
             serial: 00:10:a4:78:1d:58
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A ip=192.168.0.100 link=yes multicast=yes port=MII speed=100MB/s
             resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11
        *-communication
             description: Serial controller
             product: Mini-PCI V.90 56k Modem
             vendor: Xircom
             physical id: 3.1
             bus info: pci@00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: 16550 cap_list
             configuration: driver=serial
             resources: ioport:1840-1847 iomemory:e8121000-e8121fff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]
             vendor: Cirrus Logic
             physical id: 5
             bus info: pci@00:05.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Sound Fusion CS46xx
             resources: iomemory:e8122000-e8122fff iomemory:e8000000-e80fffff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1850-185f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IBM-DJSA-220
                   vendor: IBM
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: JS4IAC6A
                   serial: 44T445S0689
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 17GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 729MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: MATSHITADVD-ROM SR-8175
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: G228
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge:1 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:0f:8f:57:5e:f7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
```

hope I did that right...thanks for all your help folks.

thanks in advance

---

### Post by neoflight on 2006-12-09
Man! we want that IBM TP up and running...keep going...:D 

there are many experts out there...

--a Thinkpad owner :d

---

### Post by Bingo on 2006-12-10
I do too...I am about to kill a chicken and do a rain dance to get this thing to grab an IP.  Anything to please the DHCP gods.

---

### Post by FrodoB on 2006-12-10
Remove security from the Access Point and from the interfaces file and retry. I am using this card and it should work.

---

### Post by Bingo on 2006-12-10
They have me using network-manager, my interfaces file only has the loopback active, all others are commented out.

Turned off all security on the AP, network manager reports seeing my AP, but any attempt to connect returns no IP address, thus it craps out.

Before using network-manager and just going thru the admin>networking settings I could activate my card, scan, see my network, associate to the AP, but it would never grab an IP.

DHCP works wired but not wireless...card seems to be functioning fine.  

Any other ideas...really appreciate the help.

thanks in advance

---

### Post by AgenT on 2006-12-10
Notice that in the lspci output, you wireless card is not mentioned! This is bad. Even if you do not have the proper modules loaded, it should still be mentioned in the output. Double check out lspci output and make sure you did not leave something out when you did a copy/paste.

And FrodoB is right that the reason why there are two devices listed is because that is how the driver was designed. However, that is not a good enough reason or answer. As I mentioned previously (and which FrodoB wants to dispute for some strange reason): the real reason why you have two entries, or the reason why the driver was designed this way, is because the wireless card is buggy. I use the term buggy because this is not the place to go into technical details. To sum up quickly, the aironet chipset implementation is a POS. ;) For more information just read the airo driver mailing lists, search the web or search launchpad.

A few things you need to know:
NEVER enable wifiX (where X = 0, 1, etc. depending on your setup) on the aironet card. It will trick you into thinking that it works just like ethX if you check using iwconfig or ifconfig, but it does not and will not work. Always use the ethX entry of the aironet card. Because of the ridiculous two entry "feature", major conflicts can happen at boot when the driver is first initialized (see complaints on this in launchpad). What sometimes will happen is that your card will not initialize at bootup and you have to do this:
```
sudo rmmod airo
sudo modprobe airo
```How often this problem occurs depends on what exact version of the airo card and chipset you have (you never mention that) and what other hardware you have. This problem is not fixable except by replacing the network card. However, there is a workaround. When I had this card I created a small script like this:
```
#/bin/bash

gksudo rmmod airo && gksudo modprobe airo
```After bootup, if the card did not start correctly, I had a link on the panel that activated this script and restarted the wireless card. This made it easy for me as it only required one click on the panel.

Also, default network card settings will enable you to connect. Do not change any hardware settings on the wireless network card unless you really know what you are doing. If you want to reset your settings, just remove and add the airo module as mentioned above. Do not hard code the network settings in a configuration file because then even if you remove/re-add the airo module, the settings will not reset. This does not apply if you know what you are doing and know that the new settings work for you.

Also, do not have more than one network card enabled (at first). Disable your ethernet wired card and just try connecting with the wireless.

Instead of playing around little by little with your router and network card, my suggestion would be this:[LIST=1]
[*]reset your wireless router to default factory settings (I assume this is with WEP disabled and DHCP enabled)
[*]reset your AP to factory defaults, but make sure that the AP can connect to the router! - they need to be on the same submask and sometimes they use different submasks by default.
[*]disable all entries in network manager and close it
[*]using root/sudo clear (make it empty) /etc/networking/interfaces
[*]reboot
[*]run the above script that removes and re-adds the airo module
[*]edit the eth0 wireless card entry in network manager
[*]select "enable this connection"
[*]select dhcp
[*]enable only the wireless ethX entry in networking manager by check marking the wireless ethX entry only[/LIST]When testing, connect to the AP and Router first. If this works, then your network card is working. If your network card is working but you cannot connect to the internet, your router settings need to be changed.

---

### Post by Bingo on 2006-12-10
Ok.  I nuked network-manager, got further without it before.

Did all the above steps, no avail.

when I pull iwconfig it shows that I am seeing my AP, it has it on the wrong channel.

I am going to edit the etc/network/interfaces to correct this and see what happens...

added: wireless-channel 7 to the interface file...rebooting

Now iwconfig is showing the correct channel, but says ESSID:""

I am totally lost...any help?  Network icon says eth1 connection idle signal strenth 100%

thanks in advance.

---

### Post by FrodoB on 2006-12-10
A quick overview of a working Aironet 350 PCMCIA card using WEP encryption to a Linksys Router.

1) Install cardctl for checking pcmcia cards:

sudo apt-get update
sudo apt-get install pcmcia-cs

2) Check to see that device is installed correctly:

cardctl ident

Expected output should be similar to:

Socket 0:
  product info: "Cisco Systems", "350 Series Wireless LAN Adapter"
  manfid: 0x015f, 0x000a
  function: 6 (network)

3) Run dmesg and check output for airo: Just cut and paste this line into a terminal window:

dmesg > test.txt; gedit test.txt &


you should find something similar to this:

[17179590.836000] airo(eth1): cmd= 111
[17179590.836000] 
[17179590.836000] airo(eth1): status= 7f11
[17179590.836000] 
[17179590.836000] airo(eth1): Rsp0= 2
[17179590.836000] 
[17179590.836000] airo(eth1): Rsp1= 0
[17179590.836000] 
[17179590.836000] airo(eth1): Rsp2= 0
[17179590.836000] 
[17179590.836000] airo(eth1): Doing fast bap_reads
[17179590.884000] airo(eth1): MAC enabled 0:d:20:ea:09:11

4) The driver is airo_cs and the lsmod command should show:

airo_cs                 7552  1 
airo                   78496  1 airo_cs
af_packet              24584  6 
pcmcia                 40380  1 airo_cs


5) The wifi0 interface is for capturing raw packets and is used by tools like kismet, you do not need to worry that it exists at all. Several other devices that have prism based chipsets have the same feature. It is just there, but you do not touch it.

6) I took this card to an already working Ubuntu machine that had never seen the device before. I opened the /etc/network/interfaces file and copied by existing record for wlan0 and pasted it and modified it so that everything that was wlan0 has been changed to eth1. I then save the file and inserted the Aironet 350. Checked the device with iwconfig and got this:

eth1      IEEE 802.11-DS  ESSID:"MY_ESSID"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:70:3A:D3:52:21   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/100  Signal level=-50 dBm  Noise level=-91 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:1

wifi0     IEEE 802.11-DS  ESSID:"MY_ESSID"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:70:3A:D3:52:21   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/100  Signal level=-50 dBm  Noise level=-91 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:1


7) Then I can control the device ifdown and ifup:

sudo ifdown eth1

sudo ifup eth1

---

### Post by Bingo on 2006-12-10
Ok...I have completed all of the above and everything looks as described.  Ran iwconfig and my AP, shows up (on the correct channel) but I can still not get an IP from my AP.

after the sudo ifup eth1 it just cycles and end with "No DHCPOFFERS received"

Please dont give up.

thanks in advance

---

### Post by FrodoB on 2006-12-10
iwconfig shows the MAC identifier of you Access Point and not some other one correct? What is the output of iwconfig at this point?

You are sure that your AP is not filtering MAC identifiers?

Have you tried new WEP keys or disabling WEP?

Can we see your present /etc/network/interfaces file?

---

### Post by Bingo on 2006-12-10
**iwconfig**
```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"funkzilla317"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:40:05:24:F2:D3   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-18 dBm  Noise level:-106 dBm
          Rx invalid nwid:11726  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36339   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"funkzilla317"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:40:05:24:F2:D3   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-18 dBm  Noise level:-106 dBm
          Rx invalid nwid:11726  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36339   Missed beacon:0
```

**interface file**
```
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid funkzilla317

auto eth1
```


No MAC filtering and the MAC returned by iwconfig is my AP...WEP disabled.

Please help...thanks in advance

---

### Post by FrodoB on 2006-12-10
That sure looks good, what do you see from:

ifconfig

netstat -rn

---

### Post by Bingo on 2006-12-10
**ifconfig**
```

eth1      Link encap:Ethernet  HWaddr 00:0F:8F:57:5E:F7  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:51 errors:11585 dropped:0 overruns:0 frame:11585
          TX packets:3 errors:10 dropped:0 overruns:7 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16601 (16.2 KiB)  TX bytes:990 (990.0 b)
          Interrupt:3 Base address:0x100 
```


[B]
netstat -rn[/B]
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface

```

---

### Post by FrodoB on 2006-12-10
Just run dhclient:

dhclient eth1

then what happens?

---

### Post by Bingo on 2006-12-10
**dhclient eth1**
```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0f:8f:57:5e:f7
Sending on   LPF/eth1/00:0f:8f:57:5e:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

This is all it has ever done...arrggg

Thanks in advance for all your help.

---

### Post by FrodoB on 2006-12-10
What do you get from scanning for your router?

---

### Post by FrodoB on 2006-12-10
Does your router have the latest firmware upgrade?

The Ubuntu side looks good as you have pointed out.

I do have a wireless router that will not work with one of my Orinoco Gold cards, but if I switch routers the card works fine.

Can you borrow another router to check this out?

---

### Post by FrodoB on 2006-12-10
Or can you take the card to someone who has a working Ubuntu system and just have them copy their settings in interfaces and paste them in with eth1 and then install the card and see if it works with their router?

---

### Post by Bingo on 2006-12-10
I am on an ubuntu island...I know of no others.  My router is a DI-614+ Rev.B.  I have tried three other cards a 3Com and a linksys...those were a total no-go.  

This thing gives IPs left and right to my windoz machines...just no this laptop.  It has very few places to tweak settings for DHCP.  Why is ubuntu lookin on one particular port 67?...is that something to look into?

---

### Post by FrodoB on 2006-12-10
Have you used this Aironet 350 from a Windows machine? Maybe if you used it with a Windows driver it would reset something in the card and then it might work with Ubuntu.

I would still look into router firmware if you have not.  Did you get the same results with the other devices as this one?

---

### Post by FrodoB on 2006-12-10
Also if you have the CD that came with the card, then you could perhaps take it to a Windows machine and reload the card's firmware, that has been know to fix some strange issues.

---

### Post by FrodoB on 2006-12-10
Also, just saw that this wireless router is a 22Mbps router. Go to the configuration and make sure that you set this router to be an 802.11b device if that is possible and make sure in any case that you set the maximum speed to 11Mbps. Restart the router and then restart the Ubuntu machine and run all of the normal checks. 

A router that runs at 22Mbps is one of those non-standard things from a 802.11x point of view and this may be related to your issues perhaps.

Also see router firmware at:

[http://support.dlink.com/downloads/](http://support.dlink.com/downloads/)

---

### Post by FrodoB on 2006-12-10
Here is the download page from Cisco for the Aironet 350. I see firmwares on there as well as Linux and Windows drivers:

[http://tools.cisco.com/support/downloads/go/SoftwareType.x?mdfid=268438202&mdfname=Cisco%20Aironet%20350%20Wireless%20LAN%20Client%20Adapter](http://tools.cisco.com/support/downloads/go/SoftwareType.x?mdfid=268438202&mdfname=Cisco%20Aironet%20350%20Wireless%20LAN%20Client%20Adapter)

You will need to setup an account to get access. 

I don't know if there is anything on there that will help for sure.

---

### Post by Bingo on 2006-12-10
Upgraded to the latest firmware, reset to default settings...nothing.  The wireless tab shows my laptops MAC as being connected.

I pulled this card from a working windoze machine.  Still cant grab an IP.  I am starting to regret the move to Linux...I really wanted an alternative to the world of Gatezilla.

thanks in advance

---

### Post by FrodoB on 2006-12-11
Well it surely seems that you are connected, but there is some sort of DNS problem going on here.

To debug perhaps you can setup your Ubuntu machine with a static address making your wireless router's address the default gateway and getting your DNS servers from the ones that your router picks up from your ISP.

Do you know that your wireless router is correctly logged in to your ISP at this point. It has the classic symptoms  of being connected to the router, but the router is not connected so there is no where to give you a valid DNS route to.

Have you tired to ping the wireless router, it sounds like you should be able to at this point?

If you can ping the router can you ping an IP address like RedHat's:

ping -c3 209.132.177.50

---

### Post by FrodoB on 2006-12-11
I should also add that on LinuxQuestions' hardware wiki there is an entry on the Aironet 350 and ilikejam reports that firmware 4.25.23 works with the rfmon utility, so maybe downgrading to 4.25.23 would be a known good firmware I suppose.

---

### Post by Bingo on 2006-12-11
I have play dumb on this one.  I have tried the static thing too. Could you walk me thru the steps to complete the Static setup with my router as the default gateway.

I know my router is connected, and it is giving all three of my windoze machines an IP via DHCP...and this laptop one via the wired connection.  I am still at a loss why it would see my router, connect to it, but not grab an IP via the DHCP wirelessly.  All signs point to the card functioning properly...just something fishy in how it is addressing the DHCP over the air.

I have two other cards that I had tried:

3Com 3CRWE62092B
Linksys WPC11

The 3com was up for about three minutes on my first install, but soon crapped and started exibiting the same symptoms as this card.

The Linksys hung the machine on inserting it.

I had read on these forums that a fresh install with the card inserted would help some things...so I have tried that with the Aironet card.

That is where I am now.

I would be willing to try one of these cards again, but I dont want to start a conflict.  I read of some folks getting the 3Com to work with some specific drivers (pcmf502r3 Atmel driver)...but I have no clue on how to uninstall the Aironet and install new drivers for the 3Com.

I hate to sound like a basketcase...I am pretty good on the windoze side of ball.

---

### Post by hagan on 2006-12-11
Hello,
I have this problem also all the time. Network-manager thinks somehow that my AP is not using WEP. So he dries to connect without encryption, which does of course not work, he always fails to get an IP address via DHCP. Try to "Connect to Other Wireless Network ..." and give the SSID of your network and the WEP key. Make sure you choose the correct representation (Hex or ASCII).
That works for me, till the next time, you have to do it again. 

I am really tired of this network manager. Especially with the new madwifi drivers. (Everything worked fine in Dapper). Does anyone have some better alternative? Something which does not try to be so clever, that it stumbles over his own feet.

Regards
Hagan

---

### Post by FrodoB on 2006-12-11
Well if your 3COM really has an Atmel driver it is built into Edgy and you just pull out the Aironet and then plug in the 3COM and start debugging without much change.

Refer to this link for chipsets:

[http://linux-wless.passys.nl/query_part.php?brandname=3Com](http://linux-wless.passys.nl/query_part.php?brandname=3Com)

---

### Post by Bingo on 2006-12-11
802.11b 	 3CRWE62092B 	 	 PCMCIA 	 Atmel 	 atmelwlandriver 	 green  	 works with pcmf502r3 Atmel driver; [http://atmelwlandriver.sourceforge.net/news.html](http://atmelwlandriver.sourceforge.net/news.html)


I think I may have blown this thing up...I downloaded the driver, followed some of the install instructions (not having a clue what I was doing) boom.

I am rebuilding the machine with the Linksys card in it during install...seeing what happens.

Please hang in there with me.  I am so in uncharted waters, but learning alot from your help.

Thanks in advance

---

### Post by FrodoB on 2006-12-11
For Edgy you do not have to install any drivers for the Atmel device's they are built-in.

A clean install is probably a good idea.

---

### Post by Bingo on 2006-12-11
ok...it is churn'n now.  Thanks again for all your help.  Stay tuned.

---

### Post by Bingo on 2006-12-11
First build using the Linksys card was a no-go.  Looked good at first, but just would not grab my AP...kept latching on to some other router in the area, but not the one it is four feet from.

I have slapped the 3Com in and I am doing a fresh install of the OS.

---

### Post by FrodoB on 2006-12-11
That really calls your router or its configuration into question. 

To get true compatibility with all devices you sometime have to enter everything in HEX on both ends it that is possible.

I also had to return a nice Netgear WGT624 because it would not work with one of my Linux machines, but Windows XP and two other Linux wireless devices had no issues.

It will be really interesting to get to the root cause of this issue.

---

### Post by FrodoB on 2006-12-11
I will almost bet that if you take your laptop to a coffee shop or some other location that it will work with the Aironet card. 

Unless that card is just somehow damaged it should just work,  which I cannot believe. They are built like a tank and they do work well in Linux.

---

### Post by Bingo on 2006-12-13
Ok well two installs later (one with the linksys, another with the 3Com) and I am back at square one...the Cisco card seems the best pony so far, who wants to help me troubleshoot my router config?...thanks again for all the help so far.

---

### Post by FrodoB on 2006-12-13
Well I am sick tonight, but this information helped another fella get his wireless working after fighting the wireless device for days:

My ViewSonic WAPR-100 Wireless Access Point Settings: (Linksys WRT54GL differences noted)


Authentication Type: Open System

Basic Rate: All  (Linksys only)
      
Transmission Rates: Auto (All for my Linksys)

Frame Burst: Disable  (Only on my Linksys)

RTS/CTS: Disable 

CTS Protection Mode : Disable (Linksys only)

Beacon Interval: 100 ms

RTS Threshold: 2346

Fragmentation Threshold: 2346 (2347 on my Linksys)

DTIM Interval: 3

Xpress mode: Disable   (Maybe this is the same as preamble on this router?)

Access Control: Disable

Wireless Mode 802.11b 11Mbps

Channel: 11

SSID Broadcast: Disable  (You could try enabling this to see if their is any difference.)

SecureEasySetup : Disable    (Linksys only)

If you get connected you can start changing back to the originals until you find out which one is a problem.

---

### Post by Bingo on 2006-12-13
Thanks...feel better.  I will give it a go in the morn and report back.  Thanks a ton for your help.

---

### Post by FrodoB on 2006-12-13
Agree that the Cisco card is the best choice. It does seem to just work with Edgy. The interface to configure is eth1.

---

### Post by Bingo on 2006-12-15
arg...no go again.

What about static dhcp...it allows me to assign a address to a particular mac.  I still wonder about the 255.255.255.255 that the laptop is sniffing for an ip on...

thanks in advance.

---

### Post by FrodoB on 2006-12-15
The 255.255.255.255 just means that it is looking for it on any address, no problem.

I am going a vacation, so I will not be available for some time.

Good luck, it should work.

---

### Post by Bingo on 2006-12-15
Thanks Frodo...you have been great.  Enjoy the time off.

Anyone else out there wish to help a linux noob with my wireless config?

What about creating a local domain name on my router?

thanks in advance.

---

### Post by Joachim Ziegler on 2006-12-30
Hello Bingo,

maybe it consoles you to hear that I have exactly the same configuration as you (IBM Thinkpad T21, Cisco Aironet 350, Ubuntu 6.10) and... guess what... exactly the same problems.

Also my card cannot get an IP. If have read through this whole thread, tried everything - it just does not work. I've given up. Maybe I'll buy another card.

Joachim

PS: Is there a list of cards or USB sticks currently for sale THAT WORK FOR SURE WITH UBUNTU?

---

### Post by jamgramet on 2006-12-30
Hi - I'm in a similar situation : T21 but I'm using a different wireless card: an old Compaq Ipaq card. I see the same symptoms i.e. gets associated with the router but then can't get a DHCP response. I have been able to get it to work as follows: reboot machine without PCMCIA card plugged in, then plug the card in after booting. If I reboot with the card plugged in, then I see your symptoms...

It must be something to do with the wireless side of things on Ubuntu in my opinion...

---

### Post by jamgramet on 2006-12-30
I take it back - I'm full of crap. I cannot predictably get the network to come up. Sometimes it comes up, usually it doesn't. I did set up a static IP address to try and eliminate DHCP assigning an address as the issue, and this seems to work OK when it comes up. In fact, I'm posting this from my T21 Linux right now using a static IP address. Perhaps Bingo could try the same - I assume you know how to do that?

This is very frustrating...

---

### Post by jamgramet on 2006-12-31
For the record and if it helps with debug, with the network working, here is some of my data:

```
$ sudo lshw -businfo
Bus info     Device     Class          Description
==================================================
                        system         26478AU
                        bus            26478AU
                        memory         BIOS
cpu@0                   processor      Pentium III (Coppermine)
                        memory         L1 cache
                        memory         L2 cache
                        memory         System Memory
                        memory         SODIMM SDRAM Synchronous
                        memory         SODIMM SDRAM Synchronous
pci@00:00.0             bridge         440BX/ZX/DX - 82443BX/ZX/DX Host bridge
pci@00:01.0             bridge         440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
pci@01:00.0             display        86C270-294 Savage/IX-MV
pci@00:02.0             bridge         PCI1450
                        network        Version 01.02
pci@00:02.1             bridge         PCI1450
pci@00:03.0  eth0       network        82557/8/9 [Ethernet Pro 100]
pci@00:03.1             communication  Mini-PCI V.90 56k Modem
pci@00:05.0             multimedia     CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator]
pci@00:07.0             bridge         82371AB/EB/MB PIIX4 ISA
pci@00:07.1             storage        82371AB/EB/MB PIIX4 IDE
ide@0        ide0       bus            IDE Channel 0
ide@0.0      /dev/hda   disk           IBM-DJSA-220
ide@0.0,1    /dev/hda1  disk           Linux filesystem partition
ide@0.0,2    /dev/hda2  disk           Extended partition
ide@1        ide1       bus            IDE Channel 1
ide@1.0      /dev/hdc   disk           MATSHITADVD-ROM SR-8175
             /dev/hdc   disk           
pci@00:07.2             bus            82371AB/EB/MB PIIX4 USB
usb@1        usb1       bus            UHCI Host Controller
pci@00:07.3             bridge         82371AB/EB/MB PIIX4 ACPI
             eth1       network        Wireless interface

$ sudo lshw -C network
  *-network               
       description: 11Mbps Wireless PC Card
       product: Version 01.02
       vendor: Compaq
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:8e:b6:bd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:e8120000-e8120fff ioport:1800-183f iomemory:e8100000-e811ffff irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.3.4 ip=192.168.0.184 link=yes multicast=yes wireless=IEEE 802.11b

$ more /etc/network/interfaces     #NOTE: I commented everything out except the wireless
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


iface eth1 inet static
wireless-essid xxxxxx
address 192.168.0.184
netmask 255.255.255.0
gateway 192.168.0.1


$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.0.184  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1865063 (1.7 MiB)  TX bytes:476918 (465.7 KiB)
          Interrupt:3 Base address:0x100 

$ sudo iwconfig eth1
eth1      IEEE 802.11b  ESSID:"xxxxxx"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: yy:yy:yy:yy:yy:yy   
          Bit Rate:11 Mb/s   Sensitivity:1/3  **<=====Note: this was 2Mb/s when network not working**
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=32/92  Signal level=-85 dBm  Noise level=-145 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Joachim Ziegler on 2007-01-03
I've just got a hint from a friend of mine:

I've tried my T21 and my Cisco Aironet 350 with the Knoppix 5.1 Live CD and... EVERYTHING WORKS FINE!!!

I've got an IP, I've got DNS, I can browse the net...

Even WEP works right out of the box.

So the problem must be Ubuntu, not the T21 and the Cisco Aironet. Maybe there is something wrong with the default kernel and/or the modules?

My friend (an experienced Linux networker) also told me that the 350 series is known to have worked with T21's and (Debian) Linux for a long time - that's why our insitute almost exclusively used these cards in the past for Linux notebooks.

He gave me another hint: I should switch to openSuSE 10.2, which I am doing now. Shame on me. Sorry Ubuntu.

J.

---

### Post by jamgramet on 2007-01-04
I have found a solution to my problem which might be of help to you both. There is no mention of this on the Ubuntu forums so I'll add as a HOWTO when I get the time.

The issue comes up if you have more than one ethernet adapter in your machine. I have a built in wired ethernet + a PCMCIA wireless ethernet. The problem is that when Linux boots, it can be arbitrary as to which device is assigned to eth0 or eth1. The info below tells you how to hardwire this - I used the udev method. After doing this, my wireless ethernet has been working reliably (you can see my settings in previous post - I'm still using a static IP address but will go back to see if DHCP will also work).

Cheers!

Here is a link, but I'll also paste below in case the link goes stale. Note this information appears in several forums now so it's quite well known...
[http://www.unixadmintalk.com/f59/controlling-eth0-eth1-assignment-order-133600/](http://www.unixadmintalk.com/f59/controlling-eth0-eth1-assignment-order-133600/)

 Re: Controlling eth0,eth1,... assignment order?
On Fri, 30 Dec 2005 00:52:26 +0100
Svante Signell <svante.signell@telia.com> wrote:

> With the new way of device creation and module loading (udev, discover
> etc) my ethernet modules (3c59x,8139too) are loaded in different order
> with kernels 2.6.12 and 2.6.14. For 2.6.14 3c59x is loaded first
> corresponding to eth0 and then 8139too corresponding to eth1. With
> kernel 2.6.12 they are loaded in reverse order, giving the wrong names
> on my interfaces, and the interfaces defined in /etc/network/interfaces
> becomes wrong. How to bind modules to eth interface numbers? Any hints
> on which of the /etc/modules, /etc/modules.conf etc should be used, and
> which are obsolete?

An explanation I saw in another post explained that with newer kernels
in Debian, hardware is initialized asynchronously so you never know which
card will become eth0 and which eth1 and this matches what I
experienced with my cards.

If all you need to do is apply the correct configuration to the correct
interface and don't have a reason to care which card is designated eth0
and which is designated eth1 then you could copy the script
get-mac-address.sh from /usr/share/doc/ifupdown/examples
into /etc/network and map the configuration to the mac address of each
card with some text in /etc/network/interfaces like:

auto eth0 eth1
mapping eth0 eth1
script /etc/network/get-mac-address.sh
map 00:00:00:00:00:00 wireless
map 11:11:11:11:11:11 ethernet

: In this example you would then create interface entries for wireless
and ethernet the same as you would have otherwise done for eth0 and
eth1:

iface wireless inet static
name Wireless LAN card
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 204.127.198.4 63.240.76.4
wireless_essid your_essid
wireless_key1 your_128_or_64_bit_encryption_key
broadcast 192.168.1.255
network 192.168.1.0
multicast 192.168.1.0 255.255.255.0

iface ethernet inet static
address 192.168.2.1
netmask 255.255.255.0
name Ethernet LAN card
broadcast 192.168.2.255
network 192.168.2.0

: This worked for me. If I booted one time and my wireless interface
was designated eth0 it got the correct configuration and if it got
designated eth1 it still got the correct configuration.

If you need a specific card to be eth0 or eth1 (in my case firestarter
requires this) then instead of the above you would create a udev rule.

Based on previous posts on the list I created a file in /etc/udev/
named static-nic.rules with the contents:

# /etc/udev/static-nic.rules
#
# Set permission to 0644 'chmod 0644 static-nic.rules', then symlink
#'ln -s static-nic.rules rules.d/025_static-nic.rules'
#
# Purpose:
# Mapping specific MAC address to specific device names for cases where
# that is expected.
#
# SYSFS{address}="MAC address" - MAC address should be the machine
# address of the network card the rule is for.
#
# NAME="name" - name is the device name you want used for the interface.
# These could be standard names eth0, wlan0, etc... or if you prefer
# something more descriptive lan, internet, wireless, whatever...

KERNEL="eth*", SYSFS{address}="00:00:00:00:00:00", NAME="eth0"
KERNEL="eth*", SYSFS{address}="11:11:11:11:11:11", NAME="eth1"

#end

: This way eth0 is always mapped to my wireless card and eth1 is always
mapped to my ethernet card.

Later, Seeker

---

### Post by Bingo on 2007-01-07
Ok...well maybe I have been on the dark side too long.  But, I need someone to help me with the above suggestion in english.

I got all hyped up and jumped over to openSuSe 10.2, and after blowing a day downloading five discs, and getting it all installed...bam-o same issue.

I prefer the feel and community here with the ubuntu distro.

I dont have any experience with scripts or working with a static IP in a DHCP eviro (all my windoze boxes need to be dynamic).

thanks in advance
bingo

---

### Post by chili555 on 2007-01-07
I will give it a whirl...answering from a Thinkpad T23 using, quite easily, either a Prism 2 card or a Netgear WG511 under ndiswrapper. Both use WEP.

Are these Windows machines on the network at the same time as the Ubuntu? If so, you may have a problem if your router has assigned DHCP IP's and you boot up a static IP that is already given out via DHCP. I dunno for sure, but just a heads up.

The easy way to set up a static IP in Ubuntu is to drop down System -> Administration -> Networking. Highlight the wireless device and click Properties. Change DHCP to static and put in any IP address in the range allowed in the Setup page of your router, for example, 192.168.1.110. The subnet mask will almost certainly be 255.255.255.0. The gateway will be the IP address of your router, possibly 192.168.1.1. Save and close.

If you have DNS IP addresses in /etc/resolv.conf, you should be set. Ping -c3 [www.google.com](www.google.com) and see if you are connected.

---

### Post by randoker on 2007-01-15
I have been having the same problem on my IBM T41 and Cisco mini-PCI wireless.
It's been driving me nuts all day but I FINALLY FOUND A WORKAROUND AND FIXED IT.

Symptom:
Everything seemed to be working correctly, except the card would not obtain an IP address via DHCP.

All of the following revealed the expected results:
sudo lsmod | grep airo
sudo iwlist eth1 scan
sudo iwconfig eth1
sudo lshw -businfo
sudo lshw -C network

**The only issue was that it would not get an IP from the router, and a static IP did not work either.**

I have a d-link WBR-1310 router.

After tinkering for hours, all I had to do was paste the WEP key into all 4 fields on the router, instead of having it just in the first one.

This is how it was to start with:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 0000000000000000000000000
WEP Key 3: 0000000000000000000000000
WEP Key 4: 0000000000000000000000000

This is what I changed it to:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 613c5e6645787166627e7a395f
WEP Key 3: 613c5e6645787166627e7a395f
WEP Key 4: 613c5e6645787166627e7a395f

Now everything works perfectly. I can get online with no problems at all.
Maybe I'll try WPA now.

---

### Post by s4nt on 2007-08-16
Randoker thaks a lot !!!!
I have an IBM t41 myself w/ airo and this issue was driving me crazy.. (my router is a linksys WTRG54L w/ openwrt)
As you say, the answer is, in fact to configure the router with the 4 keys with the same value, in my case I already had the router configured like that.
BUT i also had to configure the laptop with the 4 keys too... as shown here..

quick test as root: (use sudo if you are a regular user)
(eth1 is the airo card in my install)

```

# ifconfig eth1 up

# iwconfig eth1 key [1] **adsadadasdasdasdas[/B ] key [2] [B]adsadadasdasdasdasd** key [3]  **adsadadasdasdasdasd** key [4] **adsadadasdasdasdasd**  essid **name_of_your_lan** 

# dhclient eth1

```
obvioulsy replace **adsadadasdasdasdasd ** with your actual WEP key and **name_of_your_lan** with the name of your wireless lan (d'oh!)
that should assign you the IP from the router

and to configure the laptop to always use the standard ifup/ifdown network scripts

put the following on the /etc/networking/interfaces
```

# The primary network interface
iface eth1 inet dhcp
wireless-essid **name_of_your_lan**
wireless-key1 **adsadadasdasdasdasd**
wireless-key2 **adsadadasdasdasdasd**
wireless-key3 **adsadadasdasdasdasd**
wireless-key4 **adsadadasdasdasdasd**

```
with that in place, you should make the network come up executing 
```

#  ifup eth1

```

Im not really sure why this workaround makes the laptop finally connect and get an IP from the router, since no error messages were found in the commands output or the system logs.

This "bug" is specially strange since I had a prior installation of ubuntu 7.04 on the same laptop 2 days ago with wireless working PERFECTLY.
But then had to do a reinstall since I had a HD crash, and the new installation has this crazy issue that prevented me from getting an IP from the router.:confused:

Im happy that with your help I could "fix" the problem, or at least make it work.

Thanks to everyone that contributed to this thread and I hope my post can shed some light over this issue

> **randoker said:**
> I have been having the same problem on my IBM T41 and Cisco mini-PCI wireless.
It's been driving me nuts all day but I FINALLY FOUND A WORKAROUND AND FIXED IT.

Symptom:
Everything seemed to be working correctly, except the card would not obtain an IP address via DHCP.

All of the following revealed the expected results:
sudo lsmod | grep airo
sudo iwlist eth1 scan
sudo iwconfig eth1
sudo lshw -businfo
sudo lshw -C network

**The only issue was that it would not get an IP from the router, and a static IP did not work either.**

I have a d-link WBR-1310 router.

After tinkering for hours, all I had to do was paste the WEP key into all 4 fields on the router, instead of having it just in the first one.

This is how it was to start with:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 0000000000000000000000000
WEP Key 3: 0000000000000000000000000
WEP Key 4: 0000000000000000000000000

This is what I changed it to:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 613c5e6645787166627e7a395f
WEP Key 3: 613c5e6645787166627e7a395f
WEP Key 4: 613c5e6645787166627e7a395f

Now everything works perfectly. I can get online with no problems at all.
Maybe I'll try WPA now.

---

### Post by Ichijin on 2007-10-07
has anyone tried this with WPA?

---

### Post by J-Rod on 2007-10-07
I read somewhere else that this was the problem. It seems that for some reason, the card is looking for TX KEY 4 on the router, instead of 1. If I changed the default TX Key on the router to 4, and match that key on the laptop, it works fine. The problem is, when you travel somewhere like a hotel, you don't have that option, they give you a key and you better hope that works. I'd *really* like a solution that lets me change the default TX key on the laptop to look for key 1... Anyone?

---

### Post by plaa on 2007-10-19
Hi,

I'm having a very similar problem on my Thinkpad T23.  The card is recognized, it finds the networks and seems to work fine, but it can't get a DHCP reply with quite erratic behaviour.

I'm using an Orinoco Silver PCMCIA card, which I have used fine on another laptop with an old version of Debian.  The network I'm trying to connect to is my university's wlan.  It's an open network (no WEP or other encryption, only a www-login *after* the DHCP lease has been given).  I've tried it in different locations (different routers) and also in another open wlan.  The symptoms are always the same:

"iwlist eth1 scan" reports all available networks correctly, and it automatically chooses the correct network (I've also tried assigning the ESSID). However, a DHCP lease is almost never received.  If I analyze the traffic with wireshark, I can see all the network traffic normally.

If I run "dhclient eth1" manually, it keeps sending the requests, and the wireshark report shows it sending them.  Sometimes it never gets a reply, other times it gets a reply and dhclient reports the IP assignment but does nothing.  No IP is set, no routing tables, no DNS information.  When analyzing the DHCP reply with wireshark it contains all the info - IP, gateway, DNS, domain name - but it's not used in any way!  I've also tried assigning the IP manually, and in that case I've often been able to ping the router.  One time I even managed to get it working when using pump instead of dhclient, but I have failed to repeat it.  On the whole, the results tend to be quite stochastic.

I originally had the problem in Feisty, and have now upgraded to Gutsy, but with no avail.  I've also tried another PCMCIA wireless card (a no-name 54Mbps card which Ubuntu seemed to autodetect) with exactly the same results.

The only real solution I could find in this thread (assigning the same WEP key to all four alternative keys) doesn't apply in my case since it's an open network!

On Monday I'll test knoppix or some other cd-bootable Linux distro and see whether it works.  In the meanwhile, I'd appreciate any ideas on how to further analyze the problem.  Might some acpi / ipv6 / laptop stuff be interfering with it or something...?  I'm very used to Linux and networking, but this one has me completely baffled.

Thanks for any help!


Below are typical outputs of ifconfig eth1 and iwconfig eth1:

```

eth1      Link encap:Ethernet  HWaddr 00:02:2D:08:D1:D5  
          inet6 addr: fe80::202:2dff:fe08:d1d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54386 (53.1 KB)  TX bytes:7476 (7.3 KB)
          Interrupt:3 Base address:0x2100 


eth1      IEEE 802.11b  ESSID:"aalto"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:05:5D:ED:94:3E   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=43/92  Signal level=-54 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0
```

---

### Post by plaa on 2007-10-22
More information concerning my last post:

Knoppix works directly out-of-the-box.  I boot it up, plug in my PCMCIA wlan card, and in a few seconds the network is configured and working.

The significant point seems to be that Knoppix doesn't use dhclient3, but instead pump.  When I try pump on Ubuntu, it also receives the IP and sets up the network correctly.  The default dhclient3 says it doesn't receive any DHCP reply.

How can I configure which program to use as my DHCP client program?  I haven't been able to find information about that anywhere, and the documentation of pump is all but non-existent.

---

### Post by thegrenade on 2007-11-05
Well almost a year after this thread began, I'm amused to report that I have also lost several hours of my life to the issue of the stinkpad failing to obtain an ip in ubuntu. I'm using Gutsy (7.10) on a t40 with an old school cisco 350 series pcmcia. The bugger works fine under windows but has been a royal pita under Ubuntu. I might add that I don't use any encryption at all - just an open access point. It's worth mentioning that the problems first started when I upgraded to 7.04 but I don't know if it's kernel or driver related because I updated both at the same time.

---

### Post by plaa on 2007-11-05
> **thegrenade said:**
> The bugger works fine under windows but has been a royal pita under Ubuntu. I might add that I don't use any encryption at all - just an open access point. It's worth mentioning that the problems first started when I upgraded to 7.04 but I don't know if it's kernel or driver related because I updated both at the same time.

Try using pump instead of dhclient, to see if that works.  Using some other net connection issue the command "sudo apt-get install pump" (or equivalent with the package manager - it requires packages from universe to be switched on).  Then after inserting the wifi-card (and not getting an IP) try the following from a terminal:

sudo killall dhclient dhclient3
sudo pump -i eth1

(Change eth1 to whatever your wireless network interface is.)

You can check whether things are working using iwconfig (you should see the wifi-card and ESSID it has attached to) and ifconfig (you should see what IP address has been assigned, if any).

That worked for me, and I've now got a few custom scripts set up for different environments.

---

### Post by g0nzo on 2007-11-06
@plaa: Thank you, thank you, thank you! :) After switching to pump I got wifi working on T60. 
Just one question - how to set pump to be used by default for my wifi card instead of dhclient3 after restarting the system?

---

### Post by plaa on 2007-11-06
> **g0nzo said:**
> Just one question - how to set pump to be used by default for my wifi card instead of dhclient3 after restarting the system?

I have no idea - I've been trying to solve that out for myself.

But as I'm not the only one having problems with dhclient, I have added a bug report about the problem:  [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/160594](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/160594)

---

### Post by g0nzo on 2007-11-06
Ubuntu comes with dhclient 3.0.5. There are already versions 3.0.6, 3.1.0 and 4.0.0 beta 2.  However, I'm not sure if the new versions fix this problem  and if there are packages available.

---

