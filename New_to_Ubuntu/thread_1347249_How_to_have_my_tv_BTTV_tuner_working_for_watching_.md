---
title: "How to have my tv BTTV tuner working for watching TV under linux?"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by frenchn00b on 2009-12-06
LinuxQuestions

```
109e036e	Yes	Brooktree Corporation	Bt878 Video Capture	bttv	v2.6.26-
109e0878	Yes	Brooktree Corporation	Bt878 Audio Capture	bt878,snd-bt87x	v2.6.25-
```

 

```
 
10de00e1	Yes	nVidia Corporation	nForce3 250Gb Host Bridge	amd64-agp	v2.6.25-
10de00e0		nVidia Corporation	nForce3 250Gb LPC Bridge		
10de00e4	Yes	nVidia Corporation	nForce 250Gb PCI System Management	i2c-nforce2	v2.6.25-
10de00e7	Yes	nVidia Corporation	CK8S USB Controller	usb-ohci,ohci-hcd	
10de00e7	Yes	nVidia Corporation	CK8S USB Controller	usb-ohci,ohci-hcd	
10de00e8	Yes	nVidia Corporation	nForce3 EHCI USB 2.0 Controller	ehci-hcd	
10de00df	Yes	nVidia Corporation	CK8S Ethernet Controller	forcedeth	v2.6.25-
10de00e5	Yes	nVidia Corporation	CK8S Parallel ATA Controller (v2.5)	amd74xx	v2.6.25-
10de00e3	Yes	nVidia Corporation	nForce3 Serial ATA Controller	sata_nv	v2.6.25-
10de00e2		nVidia Corporation	nForce3 250Gb AGP Host to PCI Bridge		
10de00ed		nVidia Corporation	nForce3 250Gb PCI-to-PCI Bridge		
10221100		Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] HyperTransport Technology Configuration		
10221101		Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] Address Map		
10221102		Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] DRAM Controller		
10221103	Yes	Advanced Micro Devices [AMD]	K8 [Athlon64/Opteron] Miscellaneous Control	k8temp	v2.6.25-
10de0253	Yes	nVidia Corporation	NV25 [GeForce4 Ti 4200]	nv	
109e036e	Yes	Brooktree Corporation	Bt878 Video Capture	bttv	v2.6.26-
109e0878	Yes	Brooktree Corporation	Bt878 Audio Capture	bt878,snd-bt87x	v2.6.25-
```

lspci -n 
```
00:00.0 0600: 10de:00e1 (rev a1)
00:01.0 0601: 10de:00e0 (rev a2)
00:01.1 0c05: 10de:00e4 (rev a1)
00:02.0 0c03: 10de:00e7 (rev a1)
00:02.1 0c03: 10de:00e7 (rev a1)
00:02.2 0c03: 10de:00e8 (rev a2)
00:05.0 0680: 10de:00df (rev a2)
00:08.0 0101: 10de:00e5 (rev a2)
00:0a.0 0101: 10de:00e3 (rev a2)
00:0b.0 0604: 10de:00e2 (rev a2)
00:0e.0 0604: 10de:00ed (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:0253 (rev a3)
02:09.0 0400: 109e:036e (rev 02)
02:09.1 0480: 109e:0878 (rev 02)
```

my super working kernel:
```

 2.6.30-1-686 #1 SMP Sun Jun 14 16:11:32 UTC 2009 i686 GNU/Linux

```

```

dmesg |grep  btt
[    9.224899] bttv: driver version 0.9.18 loaded
[    9.224902] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.224935] bttv: Bt8xx card found (0).
[    9.225183] bttv 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    9.225191] bttv0: Bt878 (rev 2) at 0000:02:09.0, irq: 19, latency: 32, mmio: 0xfbffe000
[    9.225213] bttv0: detected: FlyVideo 98 (LR50)/ Chronos Video Shuttle II [card=35], PCI subsystem ID is 1851:1850
[    9.225216] bttv0: using: Lifeview FlyVideo 98 LR50 / Chronos Video Shuttle II [card=35,autodetected]
[    9.225219] IRQ 19/bttv0: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.225251] bttv0: gpio: en=00000000, out=00000000 in=008dff00 [init]
[    9.225296] bttv0: FlyVideo_gpio: unknown tuner type.
[    9.225299] bttv0: FlyVideo Radio=no  RemoteControl=yes Tuner=-1 gpio=0x8dff00
[    9.225301] bttv0: FlyVideo  LR90=no  tda9821/tda9820=no  capture_only=no 
[    9.225304] bttv0: tuner type unset
[    9.225337] bttv0: registered device video0
[    9.225355] bttv0: registered device vbi0
[    9.225371] bttv0: PLL: 28636363 => 35468950 .. okdmesg |grep  driver
[    0.000000] Using APIC driver default
[    0.453144] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.248985] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.489226] usbcore: registered new interface driver usbfs
[    1.489258] usbcore: registered new interface driver hub
[    1.489292] usbcore: registered new device driver usb
[    1.534012] Uniform Multi-Platform E-IDE driver
[    1.560243] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    2.667752] usbcore: registered new interface driver hiddev
[    2.667800] usbcore: registered new interface driver usbhid
[    2.667803] usbhid: v2.6:USB HID core driver
[    5.193027] ide-gd driver 1.18
[    5.196419] ide-cd driver 5.00
[    5.266307] Uniform CD-ROM driver Revision: 3.20
[    9.169166] usbcore: registered new interface driver snd-usb-audio
[    9.224899] bttv: driver version 0.9.18 loaded






```


BTTV, how to make tv working? what to install
xawtv gives : NOTHING

---

### Post by blazemore on 2009-12-06
Run the command
```
xawtv -hwscan
```It should give something like this
```
[COLOR=#000000]This is xawtv-3.94, running on Linux/i686 (2.6.8)
 looking for available devices
 port 139-139
     type : Xvideo, image scaler
     name : NV17 Video Overlay

 port 140-140
     type : Xvideo, image scaler
     name : NV17 Video Texture

 port 141-172
     type : Xvideo, image scaler
     name : NV05 Video Blitter

 port 173-173                            [ -xvport 173 ]
     type : Xvideo, video overlay
     name : NVIDIA Video Interface Port

 /dev/video0: OK                         [ -device /dev/video0 ]
     type : v4l2
     name : BT878 video (Hauppauge (bt878))[/COLOR]
```[COLOR=#000000]

Now that you know your Bt8x8 device is available, try starting Xawtv:

```
[COLOR=#000000]xawtv -device /dev/video0[/COLOR]
```[COLOR=#000000]
[/COLOR][/COLOR] Note that some Nvidia cards may confuse xawtv, so if you have one of  these be  sure to use the **-device** switch as above.

---

### Post by frenchn00b on 2009-12-07
# xawtv -hwscan
> This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.30-1-686)
looking for available devices
port 65-65
    type : Xvideo, image scaler
    name : NV Video Overlay

port 66-97
    type : Xvideo, image scaler
    name : NV Video Blitter

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Lifeview FlyVideo 
    flags: overlay capture


xawtv -device /dev/video0
gives blue :( 
in pal or ntsc, it does not change.

---

### Post by frenchn00b on 2009-12-07
here is my mega script

```
 seq 1  1 45  |  while read i ; do rmmod bttv ; rmmod tuner ; echo $i ; modprobe bttv card=35 tuner=$i ; echo $i ; xterm -e tvtime  ; done
```

---

### Post by frenchn00b on 2009-12-08
kind of working. i get 2 channels, wow
with sound even
```
rmmod  bttv ; rmmod tuner ; modprobe bttv card=35 tuner=7 
```

works with tvtime, I get 2channels and the config is as that:

it is a fly video II , temic , pal 

into .tvtime
```
 <?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="DefaultBrightness" value="-1"/>
  <option name="DefaultContrast" value="-1"/>
  <option name="DefaultSaturation" value="-1"/>
  <option name="DefaultHue" value="-1"/>
  <option name="PrevChannel" value="111"/>
  <option name="Channel" value="127"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="3.5"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="-1"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="-1"/>
  <option name="Muted" value="0"/>
<option name="V4LInput" value="0"/><option name="AudioMode" value="mono"/><option name="PalDKMode" value="0"/><option name="Frequencies" value="europe"/><option name="Norm" value="PAL-Nc"/><option name="FullScreen" value="0"/></tvtime>
```

---

### Post by steveneddy on 2009-12-08
I can only use Kaffeine.

Other TV tunes apps only gave a blue screen for me.

---

### Post by stefcep on 2009-12-08
> **steveneddy said:**
> I can only use Kaffeine.

Other TV tunes apps only gave a blue screen for me.

x2.

i would try kaffeine.  In fact its become my default media player.

---

### Post by frenchn00b on 2009-12-08
> **stefcep said:**
> x2.

i would try kaffeine.  In fact its become my default media player.

well, I do not know how to use it ... I put  a picture to show you

---

