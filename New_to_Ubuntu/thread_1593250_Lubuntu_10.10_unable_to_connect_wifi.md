---
title: "Lubuntu 10.10 unable to connect wifi?"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by John Phang on 2010-10-11
Lately i've move from xubuntu 9.10 to lubuntu 10.10, and i found out that my laptop unable to connect wifi. But it works fine on xubuntu 9.10. Why it is like this? and is there any way to downgrade the NetworkManager Applet back to NetworkManager Applet  0.7.996 in lubuntu 10.10? or is there a way to make it to work back? anyone please help me out? :confused:

---

### Post by celticbhoy on 2010-10-11
First things first, is wireless enabled?

right click on network manager to see

---

### Post by John Phang on 2010-10-11
I've enable and the network manager enable to sense the wireless but it unable to connect to the wireless network.

---

### Post by Hippytaff on 2010-10-11
Whats the output of
```

iwconfig

```

---

### Post by John Phang on 2010-10-12
after i key in the code you gave me it shows something like this:
john@john-Portable-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"aztech"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


what should i do next?

---

### Post by Hippytaff on 2010-10-12
post the output of the following
 
```

lspci

```
or
```

lsusb

```
if it's a usb wireless
 
```

lshw -c network

```

---

### Post by anewguy on 2010-10-12
[QUOTE=John Phang]after i key in the code you gave me it shows something like this:
john@john-Portable-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"aztech"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


what should i do next?[/QUOTE]

Looks to me like eth1 is an 801.b connection already connected to a router with a network id of "aztech".  No access point is listed.  Is the router connected to the net?

Now we have to wonder - is it connected with a flaky or incomplete driver, so a driver install or module load or blacklist is needed, or is it something from the router on out?

Dave ;)

---

### Post by anewguy on 2010-10-12
> **Hippytaff said:**
> post the output of the following
 
```

lspci

```
or
```

lsusb

```
if it's a usb wireless
 
```

lshw -c network

```

Just a little FYI I learned a while back:  Some laptops actually have the internal wireless connected via USB, so the lsusb is pretty much a requirement anymore as you've noted.  I would change the list of things requested when there is a problem like this to:

lspci

lsusb

lshw -C network

ifconfig

iwconfig

That way I seem to get a lot of information at once.  Don't get me wrong - sometimes I don't know what the heck it all means, but at least the info is there for all to see all in one shot.

I only mention this because due to the spacing on your post if makes it look like to only do the lshw if it's USB when in reality it's good to get all of that information right up front.

Please understand I'm not knocking you at all!!  I'm glad you're in here trying to help the OP as well!!

Thanks!
Dave ;)

---

### Post by John Phang on 2010-10-12
Happytaff: When i type in the code (lspci) it shows something like this:


john@john-Portable-PC:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

when i type in lshw -c network it shows:


john@john-Portable-PC:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:8b:e8:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.2 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:f7efd000-f7efdfff ioport:eb40(size=64) memory:f7ec0000-f7edffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:45:49:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-22-generic firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b


anewguy: when i type in the codes (one by one) you gave me it shows:

> john@john-Portable-PC:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
john@john-Portable-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-Portable-PC:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 0d
       serial: 00:00:39:8b:e8:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.1.2 latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:f7efd000-f7efdfff ioport:eb40(size=64) memory:f7ec0000-f7edffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:45:49:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-22-generic firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
john@john-Portable-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:8b:e8:ec  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe8b:e8ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1135346 (1.1 MB)  TX bytes:79845 (79.8 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:45:49:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-Portable-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b  ESSID:"aztech"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

john@john-Portable-PC:~$ 


Hope these info will help. By the way i've check my router it is working fine. But the problem is i just cant connect to the wireless network after i move from xubuntu 9.10 to lubuntu 10.10.

---

### Post by Hippytaff on 2010-10-12
> **anewguy said:**
> Just a little FYI I learned a while back: Some laptops actually have the internal wireless connected via USB, so the lsusb is pretty much a requirement anymore as you've noted. I would change the list of things requested when there is a problem like this to:
 
lspci
 
lsusb
 
lshw -C network
 
ifconfig
 
iwconfig
 
That way I seem to get a lot of information at once. Don't get me wrong - sometimes I don't know what the heck it all means, but at least the info is there for all to see all in one shot.
 
I only mention this because due to the spacing on your post if makes it look like to only do the lshw if it's USB when in reality it's good to get all of that information right up front.
 
Please understand I'm not knocking you at all!! I'm glad you're in here trying to help the OP as well!!
 
Thanks!
Dave ;)
 
Good point...noted :-)
 
I'm foxed though...the wireless is on eth1, looks fine, I don't know if its worth looking into the driver - orinoco_cs (firmware number)...maybe there is a conflict?
 
try
 
```

lsmod

```
 
to list the modules (drivers)...maybe that will shed some light!?

---

### Post by SteveDee on 2010-10-12
Please post the output from:-
```

sudo iwlist scanning

```

...and also the contents of your /etc/network/interfaces file.

---

### Post by John Phang on 2010-10-12
anewguy: here is what i get when i enter the code you gave me
> john@john-Portable-PC:~$ lsmod
Module                  Size  Used by
dm_crypt               11385  0 
snd_atiixp_modem        9147  0 
snd_via82xx_modem       8498  0 
snd_intel8x0m          10731  0 
michael_mic             1744  4 
snd_ali5451            15875  1 
snd_ac97_codec         99227  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec
orinoco_cs              5050  1 
orinoco                64558  1 orinoco_cs
snd_seq_midi            4588  0 
cfg80211              144470  1 orinoco
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
smsc_ircc2             16989  0 
ppdev                   5556  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 35973  1 orinoco_cs
irda                  178906  1 smsc_ircc2
psmouse                59033  0 
serio_raw               4022  0 
parport_pc             26058  1 
snd                    49006  12 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               1351  1 irda
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
toshiba_acpi            8454  0 
soundcore                880  1 snd
pcmcia_core            14657  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali15x3             5190  0 
snd_page_alloc          7120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
shpchp                 29886  0 
i2c_ali1535             4865  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
ali_agp                 3729  1 
e100                   30356  0 
video                  18712  0 
pata_ali                7976  2 
output                  1883  1 video
mii                     4425  1 e100
agpgart                32011  1 ali_agp



Steve dee: this is what i get when i enter the code you gave me:

> john@john-Portable-PC:~$ sudo iwlist scanning
[sudo] password for john: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:0E:7F:F8:62
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"aztech"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b87bed9be
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 0006617A74656368
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0A0800280101000200FF0F



---

### Post by Hippytaff on 2010-10-12
There are two orinoco modules...might this be causing a conflict? might need to blacklist one of them? not sure wihch one though :-)

orinoco_cs              5050  1 
orinoco                64558  1 orinoco_cs

---

### Post by anewguy on 2010-10-12
From what I've seen in net searching, having the orinoco_cs and orinoco modules both is common.  Some sites mention a "hermes" helper module which I don't see listed.

What is odd to me is that it IS connected to a wireless network named "aztech".  SO,I'd like to know what indications you have that the wireless isn't working?  What exactly is happening?

Perhaps the router isn't getting DNS info, gateways, etc.

If you open a terminal window and ping [www.yahoo.com](www.yahoo.com), what happens?  (you can use ctrl-z or ctrl-c to kill it).

Dave ;)

---

### Post by cavalier911 on 2010-10-12
Firmware was added after Ubuntu 9.10 to add WPA to the hermes chip

/lib/firmware/**agere_ap_fw.bin **
/lib/firmware/**agere_sta_fw.bin**

Move the files in bold out of the firmware folder. Then the hermes agere lucent chip uses it's own flashed firmware like it did in 9.10 and earlier versions of *buntu.
Some users report that installing WICD and removing Network Manager allows you to connect with the new WPA firmware.

---

### Post by anewguy on 2010-10-12
> **cavalier911 said:**
> Firmware was added after Ubuntu 9.10 to add WPA to the hermes chip

/lib/firmware/**agere_ap_fw.bin **
/lib/firmware/**agere_sta_fw.bin**

Move the files in bold out of the firmware folder. Then the hermes agere lucent chip uses it's own flashed firmware like it did in 9.10 and earlier versions of *buntu.
Some users report that installing WICD and removing Network Manager allows you to connect with the new WPA firmware.

Thanks, dude!  I've never seen the "hermes" stuff before so glad to meet someone who knows about this.  Here's hoping the OP tries this and everything works out ok.

Dave ;)

---

### Post by SteveDee on 2010-10-13
> **John Phang said:**
> anewguy: here is what i get when i enter the code you gave me



Steve dee: this is what i get when i enter the code you gave me:

The output from iwlist shows that your pc is communicating with your access point (wifi nodes will "talk" to all access points within range) and that signal strength is good. The problem is probably security (that's why I wanted your /etc/network/interfaces file).

I suggest you temporarily turn off security at your access point and try again...Oh, and post the interfaces file.

By the way, the output from iwconfig shows you are not "connected" (whatever that means) to your access point.

---

### Post by John Phang on 2010-10-13
Sorry about this, but the problem is i don't know how to do it.

> Firmware was added after Ubuntu 9.10 to add WPA to the hermes chip

/lib/firmware/agere_ap_fw.bin 
/lib/firmware/agere_sta_fw.bin

Move the files in bold out of the firmware folder. Then the hermes agere lucent chip uses it's own flashed firmware like it did in 9.10 and earlier versions of *buntu.


can anyone teach me? I'm so sorry, because i'm new to linux.

i've check my wireless network (aztech), it has no problem when i use xubuntu 9.10, and i've try on other laptop too, these laptop also have no problem to connect it... I just don't know why my laptop (that uses lubuntu 10.10) can't connect to wireless network...
and does it means if i install wicd it make it to work?

---

### Post by Hippytaff on 2010-10-13
THe advice is to remove those files from the folder. To do this you can either navigate to the folders and cut and paste the files into a different folder (so they are still there if you need them) or open a terminal and
 
cd /lib/firmware/
 
ls (to list files in the folder)
 
cp agere_ap_fw.bin /home/agere_ap_fw.bin
cp agere_sta_fw.bin /home/gere_sta_fw.bin (to copy them to your home folder (just incase you need them)
 
rm gere_sta_fw.bin
rm agere_ap_fw.bin (to delete them from the folder)
 
Then if this works you can get rid of the copies in your /home folder.

---

### Post by John Phang on 2010-10-13
I've enter the code but i think it doesn't work but why?

> john@john-Portable-PC:/lib/firmware$ ls
2.6.35-22-generic         i2400m-fw-usb-1.4.sbcf  rt2870.bin
3com                      intelliport2.bin        rt3070.bin
acenic                    ipw2100-1.3.fw          rt3071.bin
adaptec                   ipw2100-1.3-i.fw        rt3090.bin
advansys                  ipw2100-1.3-p.fw        rt73.bin
agere_ap_fw.bin           ipw2200-bss.fw          RTL8192E
agere_sta_fw.bin          ipw2200-ibss.fw         RTL8192SE
aic94xx-seq.fw            ipw2200-sniffer.fw      s2250.fw
ar9170-1.fw               iwlwifi-1000-3.ucode    s2250_loader.fw
ar9170-2.fw               iwlwifi-3945-2.ucode    sb16
ar9170.fw                 iwlwifi-4965-2.ucode    scripts
ar9271.fw                 iwlwifi-5000-1.ucode    slicoss
asihpi                    iwlwifi-5000-2.ucode    sun
ath3k-1.fw                iwlwifi-5150-2.ucode    sxg
ath3k-2.fw                iwlwifi-6000-4.ucode    tehuti
atmel_at76c502_3com.bin   iwlwifi-6050-4.ucode    ti_3410.fw
atmel_at76c502.bin        kaweth                  ti_5052.fw
atmel_at76c502d.bin       keyspan                 tigon
atmel_at76c502e.bin       keyspan_pda             tr_smctr.bin
atmel_at76c504_2958.bin   korg                    ttusb-budget
atmel_at76c504a_2958.bin  lgs8g75.fw              ueagle-atm
atmel_at76c504.bin        libertas                usbdux
atmel_at76c506.bin        matrox                  usbduxfast_firmware.bin
atmsar11.fw               mts_cdma.fw             usbdux_firmware.bin
av7110                    mts_edge.fw             v4l-cx231xx-avcore-01.fw
bnx2                      mts_gsm.fw              v4l-cx23418-apu.fw
bnx2x-e1-4.8.53.0.fw      mts_mt9234mu.fw         v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_mt9234zba.fw        v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mwl8k                   v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.7.0.fw      myricom                 v4l-cx2341x-enc.fw
cis                       NPE-B                   v4l-cx2341x-init.mpg
cpia2                     NPE-C                   v4l-cx23885-avcore-01.fw
cxgb3                     ositech                 v4l-cx23885-enc.fw
dabusb                    ql2100_fw.bin           v4l-cx25840.fw
dsp56k                    ql2200_fw.bin           v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2300_fw.bin           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dib0700-1.20.fw   ql2322_fw.bin           vicam
e100                      ql2400_fw.bin           whiteheat.fw
ea                        ql2500_fw.bin           whiteheat_loader.fw
edgeport                  qlogic                  yam
emi26                     r128                    yamaha
emi62                     radeon                  zd1201-ap.fw
ess                       rt2561.bin              zd1201.fw
f2255usb.bin              rt2561s.bin             zd1211
GPL-3                     rt2661.bin
i2400m-fw-usb-1.3.sbcf    rt2860.bin
john@john-Portable-PC:/lib/firmware$ cp agere_ap_fw.bin /home/agere_ap_fw.bin
cp: cannot create regular file `/home/agere_ap_fw.bin': Permission denied
john@john-Portable-PC:/lib/firmware$ cp agere_sta_fw.bin /home/gere_sta_fw.bin
cp: cannot create regular file `/home/gere_sta_fw.bin': Permission denied
john@john-Portable-PC:/lib/firmware$ rm gere_sta_fw.bin
rm: cannot remove `gere_sta_fw.bin': No such file or directory
john@john-Portable-PC:/lib/firmware$ rm agere_ap_fw.bin
rm: remove write-protected regular file `agere_ap_fw.bin'? 


---

### Post by Hippytaff on 2010-10-13
You probably need to prefix the commands with 'sudo'

---

### Post by John Phang on 2010-10-13
am i correct? 
> john@john-Portable-PC:~$ sudo cd /lib/firmware/
[sudo] password for john: 
sudo: cd: command not found
john@john-Portable-PC:~$ cd /lib/firmware/
john@john-Portable-PC:/lib/firmware$ ls
2.6.35-22-generic         i2400m-fw-usb-1.4.sbcf  rt2870.bin
3com                      intelliport2.bin        rt3070.bin
acenic                    ipw2100-1.3.fw          rt3071.bin
adaptec                   ipw2100-1.3-i.fw        rt3090.bin
advansys                  ipw2100-1.3-p.fw        rt73.bin
agere_ap_fw.bin           ipw2200-bss.fw          RTL8192E
agere_sta_fw.bin          ipw2200-ibss.fw         RTL8192SE
aic94xx-seq.fw            ipw2200-sniffer.fw      s2250.fw
ar9170-1.fw               iwlwifi-1000-3.ucode    s2250_loader.fw
ar9170-2.fw               iwlwifi-3945-2.ucode    sb16
ar9170.fw                 iwlwifi-4965-2.ucode    scripts
ar9271.fw                 iwlwifi-5000-1.ucode    slicoss
asihpi                    iwlwifi-5000-2.ucode    sun
ath3k-1.fw                iwlwifi-5150-2.ucode    sxg
ath3k-2.fw                iwlwifi-6000-4.ucode    tehuti
atmel_at76c502_3com.bin   iwlwifi-6050-4.ucode    ti_3410.fw
atmel_at76c502.bin        kaweth                  ti_5052.fw
atmel_at76c502d.bin       keyspan                 tigon
atmel_at76c502e.bin       keyspan_pda             tr_smctr.bin
atmel_at76c504_2958.bin   korg                    ttusb-budget
atmel_at76c504a_2958.bin  lgs8g75.fw              ueagle-atm
atmel_at76c504.bin        libertas                usbdux
atmel_at76c506.bin        matrox                  usbduxfast_firmware.bin
atmsar11.fw               mts_cdma.fw             usbdux_firmware.bin
av7110                    mts_edge.fw             v4l-cx231xx-avcore-01.fw
bnx2                      mts_gsm.fw              v4l-cx23418-apu.fw
bnx2x-e1-4.8.53.0.fw      mts_mt9234mu.fw         v4l-cx23418-cpu.fw
bnx2x-e1-5.2.7.0.fw       mts_mt9234zba.fw        v4l-cx23418-dig.fw
bnx2x-e1h-4.8.53.0.fw     mwl8k                   v4l-cx2341x-dec.fw
bnx2x-e1h-5.2.7.0.fw      myricom                 v4l-cx2341x-enc.fw
cis                       NPE-B                   v4l-cx2341x-init.mpg
cpia2                     NPE-C                   v4l-cx23885-avcore-01.fw
cxgb3                     ositech                 v4l-cx23885-enc.fw
dabusb                    ql2100_fw.bin           v4l-cx25840.fw
dsp56k                    ql2200_fw.bin           v4l-pvrusb2-24xxx-01.fw
dvb-fe-xc5000-1.6.114.fw  ql2300_fw.bin           v4l-pvrusb2-29xxx-01.fw
dvb-usb-dib0700-1.20.fw   ql2322_fw.bin           vicam
e100                      ql2400_fw.bin           whiteheat.fw
ea                        ql2500_fw.bin           whiteheat_loader.fw
edgeport                  qlogic                  yam
emi26                     r128                    yamaha
emi62                     radeon                  zd1201-ap.fw
ess                       rt2561.bin              zd1201.fw
f2255usb.bin              rt2561s.bin             zd1211
GPL-3                     rt2661.bin
i2400m-fw-usb-1.3.sbcf    rt2860.bin
john@john-Portable-PC:/lib/firmware$ sudo cp agere_ap_fw.bin /home/agere_ap_fw.bin
john@john-Portable-PC:/lib/firmware$ sudo cp agere_sta_fw.bin /home/gere_sta_fw.bin
john@john-Portable-PC:/lib/firmware$ sudo rm gere_sta_fw.bin
rm: cannot remove `gere_sta_fw.bin': No such file or directory


---

### Post by Hippytaff on 2010-10-13
Typo
 
sudo rm gere_sta_fw.bin
 
should be - sudo rm agere_sta_fw.bin

---

### Post by John Phang on 2010-10-13
what should i do next?

> john@john-Portable-PC:~$ sudo rm gere_sta_fw.bin
[sudo] password for john: 
rm: cannot remove `gere_sta_fw.bin': No such file or directory
john@john-Portable-PC:~$ sudo rm agere_sta_fw.bin
rm: cannot remove `agere_sta_fw.bin': No such file or directory


---

### Post by Hippytaff on 2010-10-13
> **cavalier911 said:**
> Firmware was added after Ubuntu 9.10 to add WPA to the hermes chip
 
/lib/firmware/**agere_ap_fw.bin **
/lib/firmware/**agere_sta_fw.bin**
 
Move the files in bold out of the firmware folder. Then the hermes agere lucent chip uses it's own flashed firmware like it did in 9.10 and earlier versions of *buntu.
Some users report that installing WICD and removing Network Manager allows you to connect with the new WPA firmware.
 
From these instructions you need to install WICD
 
sudo apt-get WICD
 
and remove network manager
 
Sudo apt-get remove network-manager
 
Though I've never used this method before, but thats what is suggested above.

---

### Post by John Phang on 2010-10-13
should i use synaptic package manager to install wicd? because when i type in sudo apt-get wicd it shows:
> john@john-Portable-PC:~$ sudo apt-get WICD
[sudo] password for john: 
E: Invalid operation WICD
john@john-Portable-PC:~$ 


---

### Post by Hippytaff on 2010-10-13
I'm not familiar with WICD - [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by cavalier911 on 2010-10-13
[B]Please don't install WICD :(
[/B]Network Manager will work if you do the following[B]:
[/B] Open up pcmanfm file manager: menu button(left.bottom.corner)/Accessories/File Manager
Begin to navigate to **/lib/firmware** on the right side by clicking the button with the green arrow pointing up which is called the "Go to Parent Folder" button until you come to root or /
Double click the lib folder.
Double click the firmware folder
The location/address bar in pcmanfm should say **/lib/firmware**
Click Tools menu on pcmanfm,choose Open Current Folder as Root 
You may be prompted for password, a new pcmanfm opens with root privilages in /lib/firmware location
Scroll down to files **agere_ap_fw.bin **and **agere_sta_fw.bin **
Hold the Ctrl key down and click **agere_ap_fw.bin **and **agere_sta_fw.bin ** so they are both highlighted right click,choose Cut from the sub-menu that appears.
Click the green up arrow button twice so your back at root or /
Click the Edit menu on pcmanfm, choose Paste
You have moved **agere_ap_fw.bin** and **agere_sta_fw.bin** from /lib/firmware to /
Now **agere_ap_fw.bin** and **agere_sta_fw.bin** will not be loaded by orinoco_cs driver module


Power off the computer and reboot Network Manager should automatically connect your wireless..

---

### Post by John Phang on 2010-10-14
It works!! XD By removing the agere_sta_fw.bin to the / root it really let me connect to the wireless network. Thanks guys for helping me out... Now i can enjoy the internet with wireless... Thank you,Thank you and thank you... :)

and by the way is there any way to make lubuntu to restart? because my laptop can't restart properly after i move from windows to linux... hope you guys can help me out... :)

---

### Post by cavalier911 on 2010-10-14
I'm very happy you could follow my directions. :guitar:

Start a **new thread** with Startup Problem in the title that has **more information** about your start up problem.:popcorn:

---

### Post by John Phang on 2010-10-14
Ok thanks for the advice :) i'll start a new tread now... and i'm so happy that you helped me out. I've nothing to say except Thank you ... :)

---

### Post by sindahir on 2010-11-09
This also did the trick for me. Thank you very much. I allready was thinking about changing to a different linux distribution. I am very happy that I don't need to it.
By the way: OS-ver: 10.10 on a toshiba tecra 9100.
Old stuff I know, but it is good enough for surfing the web by my girlfriend.

---

### Post by HolmerGreen on 2010-11-12
Hi. Read this thread with interest. I am building a PC with Lunbuntu - latest ver. Did initial build with no wifi card installed - maybe that was a mistake! Anyway using wired connection ran all updates. Installed Linksys WM54g Ver2. Installed Wifi Radar. Card working - can see router and signal strength etc using Wifi Radar. Just cannot get it to connect using DHCP. Also put in static IP etc - no luck. Have used wrapper to install win driver but that was after the linux install of non prop driver. My thoughts are should I rebuild with the wifi card installed at start - but that strikes me as the wrong approach. Or is Wifi Radar the problem - I note that wicd is recommended but when I went to install the installation of it and its packages just sat there in a loop for ever.

---

### Post by Hippytaff on 2010-11-12
> **HolmerGreen said:**
> Hi. Read this thread with interest. I am building a PC with Lunbuntu - latest ver. Did initial build with no wifi card installed - maybe that was a mistake! Anyway using wired connection ran all updates. Installed Linksys WM54g Ver2. Installed Wifi Radar. Card working - can see router and signal strength etc using Wifi Radar. Just cannot get it to connect using DHCP. Also put in static IP etc - no luck. Have used wrapper to install win driver but that was after the linux install of non prop driver. My thoughts are should I rebuild with the wifi card installed at start - but that strikes me as the wrong approach. Or is Wifi Radar the problem - I note that wicd is recommended but when I went to install the installation of it and its packages just sat there in a loop for ever.
 
You might just need to blecklist or remove the linux driver.
look into modprobe for installing uninstalling dirver (you knew that probably) and blacklisting .
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

---

### Post by HolmerGreen on 2010-11-12
Hi. Thanks for your input. Created blacklist-custom using gedit.
Ran lsmod but did not spot what could be an obvious wifi driver except ndiswrapper.

---

### Post by Hippytaff on 2010-11-12
If its a pci card you can find the chipset and then search for the driver name (google it) by doing
```

lspci

```
if it's usb then
[/code]
```

lsusb

```
:-)

---

### Post by HolmerGreen on 2010-11-13
Hi - Hippytaff. Thanks for your replies. I have decided to start with a fresh install of lunbuntu but this time with the wifi card installed. I know from years of building Win PCs (as an PC technician) sometimes it's better to start from fresh! I have tinkered with Linux over the years. But this is the first PC I am building to give to someone - my brother! First question I am unclear on - as Network manager installs as default do you need to also then install an application to scan for and connect to wifi networks. The one I used in the first build was Wifi radar but I did note people also recommended wicd. The wifi card is a WM54G Ver2 which is listed in the unbuntu directory as working with the broadcom driver. Thanks

---

### Post by Hippytaff on 2010-11-13
I agree, sometimes it's easier to do a fresh install if you've got nothing to loose. I've never needed anything additional to network manager to scan for wifi, though I'm not sure what comes with Lubuntu, but I'm almost positive you don't need additional software to scan for wireless networks, though you can if you want to :-)

---

### Post by SteveDee on 2010-11-13
> **HolmerGreen said:**
> ...First question I am unclear on - as Network manager installs as default do you need to also then install an application to scan for and connect to wifi networks...

No you don't need to install any other app if you are installing Lubuntu 10.10 with Network Manager, as long as your hardware is supported.

Some additional apps can be useful for determining other local access point channels and relative strengths, thereby allowing you to chose the best channel for your own use.

---

### Post by wkhasintha on 2010-11-13
You might just need to blecklist or remove the linux driver.

---

### Post by HolmerGreen on 2010-11-13
Hi. Thanks for your input. New install and fully patched.Wifi not working. Green light on card. Lunbuntu detected that the broadcom driver was the driver to use. Downloaded and installed. Using lspci can see card listed as network controller broadcom wifi. Network manager with wired network not plugged in will not attempt to connect to wifi network. Welcome pointers for next steps - thanks

---

### Post by HolmerGreen on 2010-11-13
Hi. Now working. Here is the solution "hey jay i have the same card with ubuntu it took me like a week* but can do it like a champ now all you need is the ndisgtk.deb package from the ubuntu web site but first you have to install the ndiswrapper-utils from repository don't worry it is default in synaptic after install the ndisgtk.deb and under administration u should see wireless drivers put in cd and open driver folder and use wmp54gsa.inf then configure and activate*" found at [http://www.computing.net/answers/linux/ubuntu-amp-linksys-pci-wmp54g/28880.html](http://www.computing.net/answers/linux/ubuntu-amp-linksys-pci-wmp54g/28880.html) [COLOR="Red"]helpinghand56[/COLOR] May 28, 2006 at 00:49:36 Pacific

My description. Install ndiswrapper-utils, install ndisgtk. Go to Linksys website. Download driver to USB stick - and extract. Plug into Linux PC. Launch windows driver shortcut navigate to drivers folder on USB and install. Reboot and Network Manager does the rest. Thanks for all your help. I have to say though if we are to convert Windows users then there must be an easier way.

---

### Post by SteveDee on 2010-11-14
> **HolmerGreen said:**
> ...I have to say though if we are to convert Windows users then there must be an easier way....

I agree with you, but I don't think driver problems are just a Linux issue (my son can't get his laptop wifi working on Windows 7, but its fine on XP & Ubuntu).

It seems to me that wifi support is much better on 10.10 than previous versions. Not only does my laptop work with the internal wifi, but I can plug in any of the wifi dongles we have, select them from the panel icon and they all work fine.

---

