---
title: "Ubuntu freezing after 10.04 distribution upgrade"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by sodra on 2010-05-02
Hi, again

When I upgraded to 10.04, I was impressed, but one little thing make me a little frustrated
Applications kept freezing!
when I was on 9.10, Nothing ever froze, and I loved it!

Can anyone tell me how to fix this?
Ask me and I will provide information (if it has to do with the terminal, please add the code for what you need)

Thanks!

---

### Post by davidmohammed on 2010-05-02
would be useful to see your specs - start a terminal and type 

lspci

post the contents here.

---

### Post by sodra on 2010-05-02
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

```

Anything else?

---

### Post by sodra on 2010-05-02
Anyone? Please?
I really need help! I cant stand Windows!

---

### Post by uRock on 2010-05-02
> **sodra said:**
> Anyone? Please?
I really need help! I cant stand Windows!

Please be patient.

---

### Post by davidmohammed on 2010-05-02
OK, nvidia graphics - are you using the correct nvidia graphics restricted driver? (administration - hardware drivers).

Have you tried deactivating the driver to use the default "nouveau" driver instead of the proprietary driver?

---

### Post by sodra on 2010-05-02
Im using NVIDIA accelerated graphics driver )version current) [Recommended]
The other 2 It says I can use are 96 or 173

I will try the nouveau driver

---

### Post by davidmohammed on 2010-05-02
> **sodra said:**
> Hi, again

When I upgraded to 10.04, I was impressed, but one little thing make me a little frustrated
Applications kept freezing!
when I was on 9.10, Nothing ever froze, and I loved it!

Can anyone tell me how to fix this?
Ask me and I will provide information (if it has to do with the terminal, please add the code for what you need)

Thanks!

Is it individual applications that freeze or the entire desktop?

If the former, is it any application or one particular application?

---

### Post by sodra on 2010-05-02
I tried the nouveau driver and same thing, still freezing applications

---

### Post by sodra on 2010-05-02
> **davidmohammed said:**
> Is it individual applications that freeze or the entire desktop?

If the former, is it any application or one particular application?
individual applications like Firefox freeze,

I found that Firefox and Pidgin freeze the most
when I go on Nexuiz/ other 3D Graphics games, they are laggy (even on lowest setting)

---

### Post by davidmohammed on 2010-05-02
did you have a custom nvidia driver installed during karmic or the one from the repository?

May be this [link]("http://lushchick.blogspot.com/2010/05/lucid-lynx-and-nvidia-video-cards.html") will help

---

### Post by cgroza on 2010-05-02
Did you installed fresh or upgraded? If you upgraded back up and try a fresh install ... sometimes it works.

---

### Post by sodra on 2010-05-02
> **davidmohammed said:**
> did you have a custom nvidia driver installed during karmic or the one from the repository?

May be this [link]("http://lushchick.blogspot.com/2010/05/lucid-lynx-and-nvidia-video-cards.html") will help
Tried instructions, didnt work

cgroza~ Im afraid I cant do that, I tried that once, and it took 3 days to get it working again

---

### Post by davidmohammed on 2010-05-02
the laggy graphics is because noveau doesnt do 3D acceleration.

Do you still get application freezes with nouveau?

if so can you see if anything has been outputted to the system logs (administration - log file viewer) at about the same time as the freeze.

---

### Post by GnuSense on 2010-05-05
I'm getting random freezing as well using the Ubuntu Gnome desktop, seems to be related to moving the mouse, but that may be coincidental.  Incidently, I have Intel onboard graphics, this was a fresh Kubuntu install with Gnome added from apt-get.

---

### Post by FBARRENA on 2010-05-05
I am having the same trouble. My Dell Inspiron 6400 is freezing after upgrading to 10.04. I have had 8.04, 8.10, 9.04 and 9.10 in this same machine and never had such a problem. 

It is not an application is the whole machine, the mouse does not respond neither the keyboard, I had to turn it off with button twice today. 

I have noticed the fan is making more noise than usual. May it be overheat? What has it to do with the upgrade?

I found the following text in the message log: 

May  5 19:40:26 fbarrena-ubuntu kernel: [   28.047190] [drm] set up 7M of stolen space
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.067741] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.067746] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.179801] composite sync not supported
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.180858] [drm] initialized overlay support
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.287523] Linux video capture interface: v2.00
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.312644] type=1505 audit(1273106426.332:5):  operation="profile_load" pid=793 name="/usr/share/gdm/guest-session/Xsession"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.314429] type=1505 audit(1273106426.332:6):  operation="profile_replace" pid=794 name="/sbin/dhclient3"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.315167] type=1505 audit(1273106426.332:7):  operation="profile_replace" pid=794 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.315592] type=1505 audit(1273106426.332:8):  operation="profile_replace" pid=794 name="/usr/lib/connman/scripts/dhclient-script"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.320386] type=1505 audit(1273106426.340:9):  operation="profile_load" pid=795 name="/usr/bin/evince"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.333715] type=1505 audit(1273106426.352:10):  operation="profile_load" pid=795 name="/usr/bin/evince-previewer"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.342933] type=1505 audit(1273106426.360:11):  operation="profile_load" pid=795 name="/usr/bin/evince-thumbnailer"
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.385983] pwc: Philips webcam module version 10.0.13 loaded.
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.385988] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.385991] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.385993] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.386025] pwc: Logitech QuickCam 4000 Pro USB webcam detected.
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.386199] pwc: Registered as /dev/video0.
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.389078] input: PWC snapshot button as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/input/input9
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.389172] usbcore: registered new interface driver Philips webcam
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.466701] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-2.ucode
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.560727] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.596561] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.671881] composite sync not supported
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.742024] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.809900] Registered led device: iwl-phy0::radio
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.809927] Registered led device: iwl-phy0::assoc
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.810002] Registered led device: iwl-phy0::RX
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.810024] Registered led device: iwl-phy0::TX
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.824076] fb0: inteldrmfb frame buffer device
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.824080] registered panic notifier
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.824102] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.824170] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.825425] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.829106] vga16fb: mapped to 0xc00a0000
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.829111] vga16fb: not registering due to another framebuffer present
May  5 19:40:26 fbarrena-ubuntu kernel: [   28.831400] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  5 19:40:27 fbarrena-ubuntu kernel: [   28.957974] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
May  5 19:40:27 fbarrena-ubuntu kernel: [   28.958167] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
May  5 19:40:27 fbarrena-ubuntu kernel: [   28.990446] vboxdrv: fAsync=1 offMin=0xe4991316 offMax=0xe4991316
May  5 19:40:27 fbarrena-ubuntu kernel: [   28.990949] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.005392] Console: switching to colour frame buffer device 210x65
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.031493] usbcore: registered new interface driver snd-usb-audio
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.264599] composite sync not supported
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.277897] vboxnetflt: no symbol version for SUPDrvLinuxIDC
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.277902] vboxnetflt: Unknown symbol SUPDrvLinuxIDC
May  5 19:40:27 fbarrena-ubuntu kernel: [   29.365372] ppdev: user-space parallel port driver
May  5 19:40:28 fbarrena-ubuntu kernel: [   30.231914] composite sync not supported
May  5 19:40:28 fbarrena-ubuntu kernel: [   30.456254] composite sync not supported
May  5 19:40:29 fbarrena-ubuntu kernel: [   31.527084] composite sync not supported
May  5 19:40:29 fbarrena-ubuntu kernel: [   31.738981] composite sync not supported
May  5 19:40:30 fbarrena-ubuntu kernel: [   31.991066] composite sync not supported
May  5 19:47:10 fbarrena-ubuntu kernel: [  432.384593] composite sync not supported
May  5 19:47:10 fbarrena-ubuntu kernel: [  432.600533] composite sync not supported
May  5 19:47:10 fbarrena-ubuntu kernel: [  432.820690] composite sync not supported
May  5 19:47:12 fbarrena-ubuntu kernel: [  434.687461] composite sync not supported
May  5 19:47:13 fbarrena-ubuntu kernel: [  435.975970] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  5 19:47:16 fbarrena-ubuntu kernel: [  438.016140] composite sync not supported
May  5 19:47:50 fbarrena-ubuntu kernel: [  472.945764] __ratelimit: 12 callbacks suppressed
May  5 19:47:50 fbarrena-ubuntu kernel: [  472.945774] operapluginwrap[1667]: segfault at 0 ip (null) sp bfdff72c error 4 in libXt.so.6.0.0[110000+4f000]
May  5 19:47:51 fbarrena-ubuntu kernel: [  473.174353] operapluginwrap[1689]: segfault at 0 ip (null) sp bfd4966c error 4 in libuuid.so.1.3.0[110000+3000]
May  5 19:47:51 fbarrena-ubuntu kernel: [  473.340625] operapluginwrap[1711]: segfault at 0 ip (null) sp bfb032ac error 4 in libm-2.11.1.so[110000+24000]
May  5 19:47:51 fbarrena-ubuntu kernel: [  473.869162] operapluginwrap[1744]: segfault at 0 ip (null) sp bfb49aac error 4 in libX11.so.6.3.0[110000+119000]
May  5 19:50:59 fbarrena-ubuntu kernel: [  661.972569] composite sync not supported

---

### Post by dirk_k on 2010-05-12
I maybe have the same problem on a Dell Latitude D830.
It would help if you would add the system monitor to a panel or just run 
'top' from within a terminal. I think you will probably see high iowait levels at ~100%. This is visible in the system monitor as a dark blue (see preferences) or in top as %wa.

---

### Post by radu.c on 2010-05-13
I just saw a similar effect on my Dell X1.

My Dell X1 sports an Intel 915 video card, so no nVidia here.

I noticed that my screen saver was slow and the CPU usage went through the roof when the screen saver was running. I run the "Atlantis" screen saver, and until this morning it was running just fine. Thing is I didn't change anything. I just used my computer as I usually do (terminal, firefox, pidgin). No updates came in today.

---

### Post by ezsit on 2010-05-13
My systems would randomly freeze at boot, then randomly freeze during the day when left for long periods of non-use. I eventually went back to Karmic (and it runs perfectly fine). I'll run Ubuntu 9.10 and try again when 10.10 comes out. The differences between 9.10 and 10.04 are so minimal that I couldn't care less.

---

