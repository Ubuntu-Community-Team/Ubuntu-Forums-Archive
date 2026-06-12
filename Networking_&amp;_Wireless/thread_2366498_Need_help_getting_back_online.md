---
title: "Need help getting back online"
date: 2017-07-18
forum: Networking &amp; Wireless
---

### Post by aviator1 on 2017-07-18
Hello All:

I recently had some problems with an SSD that had intermittent problems. I disconnected that drive and did a clean install on my remaining HDD.

Now I have lost all network connectivity.

I will be away from that computer until noon, central time.

If anyone can give me any advice/suggestions/ideas I would appreciate the help.

---

### Post by TheFu on 2017-07-18
wifi or wired?
[http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues](http://blog.jdpfu.com/2013/08/23/common-answers-for-ubuntu-and-linux-issues) has a few links that might be helpful.  Networking 101, especially.

---

### Post by aviator1 on 2017-07-18
Thank you. I looked, but must not have in the right places.

---

### Post by aviator1 on 2017-07-18
Wired

---

### Post by leunam12 on 2017-07-18
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)

---

### Post by TheFu on 2017-07-18
> **aviator1 said:**
> Thank you. I looked, but must not have in the right places.

You looked at what?  Did you run the commands, in order, and post those cmds and output back here?

Sorry, but we cannot read minds. Linux is VERY flexible. I'm not even certain what release you are running or which desktop or server is being used.

---

### Post by aviator1 on 2017-07-18
> **TheFu said:**
> You looked at what?  Did you run the commands, in order, and post those cmds and output back here?

Sorry, but we cannot read minds. Linux is VERY flexible. I'm not even certain what release you are running or which desktop or server is being used.

I apologize for not being clear.

I looked in the forum for some answers, but must not have used the correct search criteria.

I don't know what commands to run, or in what order, which is why I made the post. I'm a long time user, but not well educated in how to run the commands, etc. This is a fresh install of 16.04

The motherboard is an Asus M5A97 R2.0

I appreciate any help.

---

### Post by slickymaster on 2017-07-18
*Thread moved to **Networking & Wireless**.*

---

### Post by aviator1 on 2017-07-18
> **slickymaster said:**
> *Thread moved to **Networking & Wireless**.*

Thanks. Sorry for posting here.

---

### Post by vasa1 on 2017-07-18
Read the sticky here carefully, especially the part about not having internet connectivity: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Then post the required information here.

---

### Post by aviator1 on 2017-07-18
> **vasa1 said:**
> Read the sticky here carefully, especially the part about not having internet connectivity: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Then post the required information here.

Thanks. Will do.

---

### Post by TheFu on 2017-07-18
> **vasa1 said:**
> Read the sticky here carefully, especially the part about not having internet connectivity: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

Then post the required information here.

@Vasa - He isn't doing wifi.  It is wired.  I don't remember the wifi-info script exactly, but I do know it is extremely pointed at wifi issues.

Basically, answer the questions following, in order:
[LIST=1]
[*]Can you ping the router from the machine? Y/N?  If not. Stop.
[*]Can you ping a well-known public IP from the machine? Y/N? If not. Stop.
[*]Can you ping a few well-known websites using names? Y/N If not. Stop.
[*] If those things all work, it isn't a network problem. It is an application problem.  Try a different application. Usually a simpler application would be best.  Simple web browsers : dillo, lynx ; 
[*] Do the simple web browsers work? Y/N?  If yes, stop. Problem solved. 
[*] Try a new userid, which will remove any per-user config issues. Problem solved. remove the config files from the main userid where the issue is happening.
[*] Purge and reload the problem application(s). Problem solved?
[/LIST]

Please show your work. The needed commands are at the 101 Networking link.

Same questions that my link(s) asks, just without detailed commands.  Which distro? We know "16.04" ... which applies to many different releases.  Unity? Gnome? Mate? LXDE? XFCE? Cinnamon? Server? Something else? 

If anything wasn't clear, ask. Happy to help. We all started with next to no knowledge. That isn't an issue at all.
Open a terminal and type the commands.  Select/paste the commands into a file, transfer the file to some other device and post the contents back here inside "code tags" please.  If that is confusing, we have explicit links to explain the process.

---

### Post by vasa1 on 2017-07-18
> **TheFu said:**
> @Vasa - He isn't doing wifi.  It is wired.  I don't remember the wifi-info script exactly, but I do know it is extremely pointed at wifi issues.
...
You're absolutely right! *Mea culpa*. It's all about wireless :(

---

### Post by Hadaka on 2017-07-18
Hi, you state...
"I disconnected that drive and did a clean install on my remaining HDD. 
  * Now I have lost all network connectivity."

May we assume Ubuntu boots normally , but you simply have no wired network ??

*If yes..then open a terminal..ctrl/alt/t..and Copy and paste one line at a time.
```
lsb_release -a | sed -n 2p
uname -r
arch
rfkill list all | awk '/yes/'
lspci -n|awk '/0200|0280/{print$3}'
```
*The out put of theses commands are intentionally simple.
Please post EVERY command output..or state no output.
Thanks

---

### Post by aviator1 on 2017-07-18
> **TheFu said:**
> @Vasa - He isn't doing wifi.  It is wired.  I don't remember the wifi-info script exactly, but I do know it is extremely pointed at wifi issues.

Basically, answer the questions following, in order:
[LIST=1]
[*]Can you ping the router from the machine? Y/N?  If not. Stop.
[*]Can you ping a well-known public IP from the machine? Y/N? If not. Stop.
[*]Can you ping a few well-known websites using names? Y/N If not. Stop.
[*] If those things all work, it isn't a network problem. It is an application problem.  Try a different application. Usually a simpler application would be best.  Simple web browsers : dillo, lynx ;
[*] Do the simple web browsers work? Y/N?  If yes, stop. Problem solved.
[*] Try a new userid, which will remove any per-user config issues. Problem solved. remove the config files from the main userid where the issue is happening.
[*] Purge and reload the problem application(s). Problem solved?
[/LIST]

Please show your work. The needed commands are at the 101 Networking link.

Same questions that my link(s) asks, just without detailed commands.  Which distro? We know "16.04" ... which applies to many different releases.  Unity? Gnome? Mate? LXDE? XFCE? Cinnamon? Server? Something else? 

If anything wasn't clear, ask. Happy to help. We all started with next to no knowledge. That isn't an issue at all.
Open a terminal and type the commands.  Select/paste the commands into a file, transfer the file to some other device and post the contents back here inside "code tags" please.  If that is confusing, we have explicit links to explain the process.
Thanks for your reply.

I do not know how to ping.

No browser works. 

It appears that the Realtek on the motherboard is just not doing anything. 

I have options ions on the desktop to configure VPN Connections, Enable Networking ( it is checked), or Edit Connections. 

All I know about the distro is that it is 16.04.2 LTS Xenial Xerus. 

Thanks very much for your responses.

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> Hi, you state...
"I disconnected that drive and did a clean install on my remaining HDD. 
  * Now I have lost all network connectivity."

May we assume Ubuntu boots normally , but you simply have no wired network ??

*If yes..then open a terminal..ctrl/alt/t..and Copy and paste one line at a time.
```
lsb_release -a | sed -n 2p
uname -r
arch
rfkill list all | awk '/yes/'
lspci -n|awk '/0200|0280/{print$3}'
```
*The out put of theses commands are intentionally simple.
Please post EVERY command output..or state no output.
Thanks
Boots normal. No network. 
lsb_release -a | seed -n  2p
No lsb modules are available
Description Ubuntu 16.04.2
uname -r 
4.8.0-36 Generic
arch
x86_64
rfkill list all | awk '/yes/'
no output
lspci -n|awk '/0200|0280/{print$3}'
No output
Thanks

---

### Post by Hadaka on 2017-07-18
Hi you have a typo in this command..
"lsb_release -a | seed -n  2p"
please try again and a couple more..
```
lsb_release -a | sed -n  2p
lspci -n | awk '/0200|0280/{print$3}'
lsmod | grep wl
```
Thanks

---

### Post by aviator1 on 2017-07-18
Stand by. Working on it.

---

### Post by Hadaka on 2017-07-18
My apologies..i had a typo in the last post..it is now correct..
please post the output of..
```
lspci -n | awk '/0200|0280/{print$3}'
```
Thanks.

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> Hi you have a typo in this command..
"lsb_release -a | seed -n  2p"
please try again and a couple more..
```
lsb_release -a | sed -n  2p
lspci -n | awk '/0200|0280{print$3}'
lsmod | grep wl
```
Thanks
lsb_release -a |seed-n 2p
No lsb modules are available
seed-n command not found I tried it with and without a space after seed
lspci -n | ask '/0200|0280{print$3}
bash: awk/0200|0280{print$3}: no such file or directory

---

### Post by aviator1 on 2017-07-18
Oops typo working on it

---

### Post by aviator1 on 2017-07-18
lspc -n | ask '/0200|0280{print$3}'
awk: line 1: runaway regular expression /0200|0280{ ...
lsmod | grew wl
no output

---

### Post by TheFu on 2017-07-18
@Hadaka - please help the OP with **ping** troubleshooting.  I've been unable to accomplish that for some reason. [http://www.wikihow.com/Ping-in-Linux](http://www.wikihow.com/Ping-in-Linux)

It appears that folks are jumping ahead to other troubleshooting when 3 trivial commands would determine exactly where the problem lies.

---

### Post by praseodym on 2017-07-18
Lets check the outputs without filtering the results:
```

lspci -nnk
lsmod
rfkill list
dmesg | grep wl
```

---

### Post by aviator1 on 2017-07-18
> **TheFu said:**
> @Hadaka - please help the OP with **ping** troubleshooting.  I've been unable to accomplish that for some reason. [http://www.wikihow.com/Ping-in-Linux](http://www.wikihow.com/Ping-in-Linux)

It appears that folks are jumping ahead to other troubleshooting when 3 trivial commands would determine exactly where the problem lies.
I have not gone to the instructions. Have been trying to follow suggestions here.

---

### Post by aviator1 on 2017-07-18
> **praseodym said:**
> Lets check the outputs without filtering the results:
```

lspci -nnk
lsmod
rfkill list
dmesg | grep wl
```
There is no way I can post all the info that showed up from lspci -nnk. Too many lines to type. 


I am am running terminal on the machine with the problem and having to manually type the lines here. 

rfkill list and dmesg | grep wl had no output.

---

### Post by aviator1 on 2017-07-18
> **aviator1 said:**
> I have not gone to the instructions. Have been trying to follow suggestions here.
When I type ping and enter, I get 16 items within brackets [-c count] as an example.

Ping and the space bar does nothing.

adding an address gives the error connect: network is unreachable

---

### Post by Hadaka on 2017-07-18
Hi, you still have a typo..
*" lspc -n | ask '/0200|0280{print$3}' "

please triple check your typing..the correct command is..
```
lspci -n | awk '/0200|0280/{print$3}'
```
*Ping Commands..
```
ping -c2 $(route -n | awk 'FNR==3{print$2}')
ping -c2 localhost
ping -c2 8.8.8.8
ping -c2 google.com
```
* Just post the IP that was pinged and it's packet loss 
*Example..
--- **[COLOR=#ff0000]192.168.1.1[/COLOR]** ping statistics ---
2 packets transmitted, 2 received, **[COLOR=#ff0000]0%[/COLOR]** packet loss, time 1001ms
Thanks

---

### Post by aviator1 on 2017-07-18
I ran all the terminal instructions that I have seen so far, and copied them to a flash drive, and have gone to another computer to post.

Here are the results of this so far:

```
                         avid@david-desktop:~$ lsb_release -a | sed -n 2p
 No LSB modules are available.
 Description:    Ubuntu 16.04.2 LTS
 david@david-desktop:~$ lspci -n | awk'/0200|0280{print$3}'
 bash: awk/0200|0280{print$3}: No such file or directory
 david@david-desktop:~$ lsmod |grep wl
 david@david-desktop:~$ lspci -nnk
 00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14]
 00:02.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port B) [1002:5a16]
     DeviceName:  Onboard IGD
     Kernel driver in use: pcieport
     Kernel modules: shpchp
 00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18]
     Kernel driver in use: pcieport
     Kernel modules: shpchp
 00:05.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port E) [1002:5a19]
     Kernel driver in use: pcieport
     Kernel modules: shpchp
 00:07.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port G) [1002:5a1b]
     Kernel driver in use: pcieport
     Kernel modules: shpchp
 00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] (rev 40)
     Subsystem: ASUSTeK Computer Inc. SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1043:84dd]
     Kernel driver in use: ahci
     Kernel modules: ahci
 00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Kernel driver in use: ohci-pci
 00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Kernel driver in use: ehci-pci
 00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Kernel driver in use: ohci-pci
 00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Kernel driver in use: ehci-pci
 00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385]
     Kernel driver in use: piix4_smbus
     Kernel modules: i2c_piix4, sp5100_tco
 00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
     Subsystem: ASUSTeK Computer Inc. SBx00 Azalia (Intel HDA) [1043:8444]
     Kernel driver in use: snd_hda_intel
     Kernel modules: snd_hda_intel
 00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
 00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
 00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
     Kernel driver in use: ohci-pci
 00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
     Kernel driver in use: ohci-pci
 00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
     Kernel driver in use: ehci-pci
 00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
 00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
 00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
 00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
     Kernel driver in use: k10temp
     Kernel modules: k10temp
 00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
     Kernel driver in use: fam15h_power
     Kernel modules: fam15h_power
 00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 730] [10de:0f02] (rev a1)
     Subsystem: NVIDIA Corporation GF108 [GeForce GT 730] [10de:1117]
     Kernel driver in use: nouveau
     Kernel modules: nvidiafb, nouveau
 01:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)
     Subsystem: NVIDIA Corporation GF108 High Definition Audio Controller [10de:1117]
     Kernel driver in use: snd_hda_intel
     Kernel modules: snd_hda_intel
 03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
     Subsystem: ASUSTeK Computer Inc. P8B WS Motherboard [1043:8488]
     Kernel driver in use: xhci_hcd
 04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
     Subsystem: ASUSTeK Computer Inc. P8B WS Motherboard [1043:8488]
     Kernel driver in use: xhci_hcd
 david@david-desktop:~$ lsmod
 Module                  Size  Used by
 nls_iso8859_1          16384  1
 uas                    24576  0
 usb_storage            73728  2 uas
 nls_utf8               16384  1
 isofs                  40960  1
 eeepc_wmi              16384  0
 asus_wmi               28672  1 eeepc_wmi
 sparse_keymap          16384  1 asus_wmi
 snd_hda_codec_hdmi     45056  4
 kvm_amd                73728  0
 kvm                   598016  1 kvm_amd
 joydev                 20480  0
 input_leds             16384  0
 snd_hda_codec_realtek    86016  1
 snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
 snd_hda_intel          36864  5
 snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 irqbypass              16384  1 kvm
 crct10dif_pclmul       16384  0
 snd_hda_core           86016  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
 crc32_pclmul           16384  0
 ghash_clmulni_intel    16384  0
 aesni_intel           167936  0
 snd_hwdep              16384  1 snd_hda_codec
 aes_x86_64             20480  1 aesni_intel
 snd_pcm               110592  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
 shpchp                 36864  0
 snd_seq_midi           16384  0
 snd_seq_midi_event     16384  1 snd_seq_midi
 snd_rawmidi            32768  1 snd_seq_midi
 snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
 snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
 lrw                    16384  1 aesni_intel
 tpm_infineon           20480  0
 i2c_piix4              24576  0
 snd_timer              32768  2 snd_seq,snd_pcm
 snd                    86016  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
 soundcore              16384  1 snd
 glue_helper            16384  1 aesni_intel
 serio_raw              16384  0
 ablk_helper            16384  1 aesni_intel
 cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
 k10temp                16384  0
 fam15h_power           16384  0
 mac_hid                16384  0
 parport_pc             32768  0
 ppdev                  20480  0
 lp                     20480  0
 parport                49152  3 lp,parport_pc,ppdev
 autofs4                40960  2
 hid_logitech_hidpp     28672  0
 hid_logitech_dj        20480  0
 usbhid                 53248  0
 hid                   122880  5 usbhid,hid_logitech_dj,hid_logitech_hidpp
 nouveau              1572864  3
 mxm_wmi                16384  1 nouveau
 video                  40960  2 asus_wmi,nouveau
 i2c_algo_bit           16384  1 nouveau
 ttm                   102400  1 nouveau
 psmouse               139264  0
 drm_kms_helper        167936  1 nouveau
 ahci                   36864  3
 syscopyarea            16384  1 drm_kms_helper
 sysfillrect            16384  1 drm_kms_helper
 libahci                32768  1 ahci
 sysimgblt              16384  1 drm_kms_helper
 fb_sys_fops            16384  1 drm_kms_helper
 drm                   368640  6 nouveau,ttm,drm_kms_helper
 wmi                    16384  3 asus_wmi,mxm_wmi,nouveau
 fjes                   28672  0
 david@david-desktop:~$ rfkill list
 david@david-desktop:~$ dmesg | grep wl
 david@david-desktop:~$ lspci -n | awk '/0200|0280/{print$3}'
 david@david-desktop:~$ 
```

---

### Post by aviator1 on 2017-07-18
Re-checked lspci -n | awk '/0200|0280/{print$3}' No output

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> Hi, you still have a typo..
*" lspc -n | ask '/0200|0280{print$3}' "

please triple check your typing..the correct command is..
```
lspci -n | awk '/0200|0280/{print$3}'
```
*Ping Commands..
```
ping -c2 $(route -n | awk 'FNR==3{print$2}')
ping -c2 localhost
ping -c2 8.8.8.8
ping -c2 google.com
```
* Just post the IP that was pinged and it's packet loss 
*Example..
--- **[COLOR=#ff0000]192.168.1.1[/COLOR]** ping statistics ---
2 packets transmitted, 2 received, **[COLOR=#ff0000]0%[/COLOR]** packet loss, time 1001ms
Thanks
  Doing Ping commands now. BRB

---

### Post by aviator1 on 2017-07-18
> **aviator1 said:**
> Doing Ping commands now. BRB

```
   david@david-desktop:~$ ping -c2 $(route -n | awk 'FNR==3{print$2}')
 Usage: ping [-aAbBdDfhLnOqrRUvV] [-c count] [-i interval] [-I interface]
             [-m mark] [-M pmtudisc_option] [-l preload] [-p pattern] [-Q tos]
             [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp_option]
             [-w deadline] [-W timeout] [hop1 ...] destination
 david@david-desktop:~$ ping -c2 localhost
 PING localhost (127.0.0.1) 56(84) bytes of data.
 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.028 ms
 64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.028 ms
 

 --- localhost ping statistics ---
 2 packets transmitted, 2 received, 0% packet loss, time 1014ms
 rtt min/avg/max/mdev = 0.028/0.028/0.028/0.000 ms
 david@david-desktop:~$ ping -c2 8.8.8.8
 connect: Network is unreachable
 david@david-desktop:~$ ping -c2 google.com
 ping: unknown host google.com
 david@david-desktop:~$ 
```

---

### Post by Hadaka on 2017-07-18
That lspci command "should have output the pci-id's for your network cards.

Please post the output of..
```
lsusb
route -n
```
*That is lowercase  "LSUSB"
Thanks.

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> That lspci command "should have output the pci-id's for your network cards.

Please post the output of..
```
lsusb
```
*That is lowercase  "LSUSB"
Thanks.

```
   david@david-desktop:~$ lsusb
 Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 005: ID 05dc:c75c Lexar Media, Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 david@david-desktop:~$ 
```

---

### Post by Hadaka on 2017-07-18
Did this ... ever work??
```
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
```
The Logitech, Unifying Receiver ??

Thus far NONE of your command outputs show ANY type of network card or usb.
and you are not even able to ping your router..

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> Did this ... ever work??
```
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
```
The Logitech, Unifying Receiver ??

Thus far NONE of your command outputs show ANY type of network card or usb.
and you are not even able to ping your router..

What do you mean by "does this ever work"? Are those some commands I should type into terminal?

---

### Post by Hadaka on 2017-07-18
No, those are not commands..that is the output from the 
command " lsusb"
The logitec unifying receiver "i think" is a usb you plug in to
run things like wireless mice and keyboards, was this something
you added?

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> No, those are not commands..that is the output from the 
command " lsusb"
The logitec unifying receiver "i think" is a usb you plug in to
run things like wireless mice and keyboards, was this something
you added?

The Logitec stuff is a wireless  keyboard and mouse. They work.

The network "card" is on the motherboard, and I believe it is a Realtek of some type.

---

### Post by aviator1 on 2017-07-18
I think the simplest thing would be for me to install a network card. 

Maybe the onboard network card has failed.

---

### Post by Hadaka on 2017-07-18
This looks to me like a fairly new computer..
"AMD 8530 4.0Ghz, 8 Core, 16GB RAM, 256GB SSD, 2 TB HDD, NVIDIA GT 640, Ubuntu 16.04 LTS"

I suppose it is possible the onboard Realtech  network card has failed, but i doubt it. How old/new
 is this computer and what make and model ?
and are you dual booting with Windows ?

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> This looks to me like a fairly new computer..
"AMD 8530 4.0Ghz, 8 Core, 16GB RAM, 256GB SSD, 2 TB HDD, NVIDIA GT 640, Ubuntu 16.04 LTS"

I suppose it is possible the onboard Realtech  network card has failed, but i doubt it. How old/new
 is this computer and what make and model ?
and are you dual booting with Windows ?

It's about 3 years old. The only OS is Ubuntu 16.04.2.

I got it from Magic Micro. AMD FX AM3+ Eight Core

I originally had a 256GB SSD and the 2 TB HDD. The SSD was having intermittent failures and causing boot issues.

I wouldn't lose anything if I did another clean install if you think that might help.

I eliminated the SSD and did a clean install on the 2 TB HDD.

It worked for a day or so, and the network problem popped up.

I shut down night before last, and the next boot up, in the morning, there was no network access.

---

### Post by Hadaka on 2017-07-18
Reloading the os might be a good idea..but first..
i see this doing some research..
**ASUS M5A97* LE *R2*.*0* AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS *
Figure out how to get into BIOS and reset to default,disable secure boot, and look  for anything that
might show the status of the network card. I know nothing about your computer so you are on your own
but that does need to be done.
*If after you reset bios..turn off secureboot UEFI..and verify the network is enabled in bios and it still
wont connect then perhaps another 10/100 ethernet card might help. Last resort reload 16.04

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> Reloading the os might be a good idea..but first..
i see this doing some research..
**ASUS M5A97* LE *R2*.*0* AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS *
Figure out how to get into BIOS and reset to derfault,disable secure boot, and look  for anything that
might show the status of the network card. I know nothing about your computer so you are on your own
but that does need to be done.
*If after you reset bios..turn off secureboot UEFI..and verify the network is enabled in bios and it still
wont connect then perhaps another 10/100 ethernet card might help. Last resort reload 16.04


I'll get to work on it and report back what turns up.

Thanks very much for your time and help.

Regards

---

### Post by Hadaka on 2017-07-18
You are welcome,sometimes it takes awhile to determine what
is causing the problem, thanks for your understanding..just to satisfy
my curiosity..please post the output of..
```
route -n
```
Thanks.

---

### Post by aviator1 on 2017-07-18
Maybe off thread..... here is what I see at boot up. I selected default, but no help. 

I did another clean install. Boot up is normal. 

Could this his be in the boot process?

thanks for your time.

---

### Post by aviator1 on 2017-07-18
> **Hadaka said:**
> You are welcome,sometimes it takes awhile to determine what
is causing the problem, thanks for your understanding..just to satisfy
my curiosity..please post the output of..
```
route -n
```
Thanks.
Route -n
Kernel IP routing table
Destination    Gateway     Genmask    Flags Metric Ref    Use Iface

---

### Post by aviator1 on 2017-07-18
Just for info. 

I decided to to do another clean install. When I get to the page to select install software, the box for download updates while installing is not available. 

It it must know at that point there is no way to get udates. 

As a guess, whatever is wrong must be in the boot up sequence. 

I saw saw nothing that related to networks in the uefi/bios area.

---

### Post by Hadaka on 2017-07-18
Hi, this is what a normal "route -n " command produces..
```
hadaka:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

You have  zero data on yours..the network card isnt even attempting to communicate.

Since you have done a new install, all we have done is void. I would suggest you open a
new thread in "New Installations" and ask how to remove UEFI from your drive and verify
that networking and the card are enabled.
Thanks.

---

### Post by TheFu on 2017-07-19
No network device is being seen by the kernel. This is very odd.  Even with a bad cable, the NIC (fancy abbreviation for any network adapter connected to the system) should be seen.

I would create a live-boot USB flash drive and boot off it. "Try Ubuntu" from the boot screen and see if the networking works.  

That motherboard claims to have a GigE Realtek® 8111F network adapter.

If it doesn't work, buy an Intel PRO/1000 NIC (PCIe 2.0 x1) for about $25 and install it.  It is possible to manually do all sorts of things to manually side-load the motherboard NIC driver, but $25 and 5 minutes to physically install a new, well-supported, network card makes this issue go away.
Something like this: [https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G/](https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G/)
I'm assuming you have an open PCIe slot on the motherboard.

---

### Post by aviator1 on 2017-07-19
> **TheFu said:**
> No network device is being seen by the kernel. This is very odd.  Even with a bad cable, the NIC (fancy abbreviation for any network adapter connected to the system) should be seen.

I would create a live-boot USB flash drive and boot off it. "Try Ubuntu" from the boot screen and see if the networking works.  

That motherboard claims to have a GigE Realtek® 8111F network adapter.

If it doesn't work, buy an Intel PRO/1000 NIC (PCIe 2.0 x1) for about $25 and install it.  It is possible to manually do all sorts of things to manually side-load the motherboard NIC driver, but $25 and 5 minutes to physically install a new, well-supported, network card makes this issue go away.
Something like this: [https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G/](https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G/)
I'm assuming you have an open PCIe slot on the motherboard.

Thanks very much.

I did use the "Try Ubuntu" and there was still no access.

I had already ordered a Star Tech card. Just installed and everything is working fine. I am on the computer that had all the problems now.

I appreciate the help.

Regards.

---

### Post by aviator1 on 2017-07-19
> **Hadaka said:**
> Hi, this is what a normal "route -n " command produces..
```
hadaka:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

You have  zero data on yours..the network card isnt even attempting to communicate.

Since you have done a new install, all we have done is void. I would suggest you open a
new thread in "New Installations" and ask how to remove UEFI from your drive and verify
that networking and the card are enabled.
Thanks.
I really appreciate the time you took to help troubleshoot this issue.

I just received and installed a Star Tech card, and the computer booted right up and recognized it. I am on the computer that had the problems now.

I think I will follow your advice regarding the New Install thread.

This is a great forum, and I have been helped by some great folks. I'm simply a user, and thankfully, rarely have problems.

Thanks again.

Regards.

---

### Post by Hadaka on 2017-07-19
That is GREAT ! Glad to hear you resolved the problem.
Please mark you thread Solved, by logging into your thread
and in the upper right area click **Thread Tools** then choose
**Solved**.
If it is working to your satisfafction, it might be best to just leave it
alone as  "messin about", as you have seen..can cause issues.
Enjoy !

*I'm going to cheat here a little because TheFu doesnt do  pm's and I have a ping script for him.
Mods..please dont beat me..
@TheFu
#!/bin/bash
gwy=`route -n | awk 'FNR==3{print$2}'`
ping -c2 "$gwy" | awk '/ping/,/2 /' > ping.tst
ping -c2 localhost | awk '/ping/,/2 /' >> ping.tst
ping -c2 8.8.8.8 | awk '/ping/,/2 /' >> ping.tst
ping -c2 google.com | awk '/ping/,/2 /' >> ping.tst
cat ping.tst | awk '{print$2,$6,$8}'
exit

@Aviator1, if you want to give your new Star Tech card a little work out 
copy and paste one line at a time in the above script starting with the * gwy= line
and ending with the * cat line. You will see NO output untill you do the last cat line.
enjoy !

---

### Post by aviator1 on 2017-07-19
> **Hadaka said:**
> That is GREAT ! Glad to hear you resolved the problem.
Please mark you thread Solved, by logging into your thread
and in the upper right area click **Thread Tools** then choose
**Solved**.
If it is working to your satisfafction, it might be best to just leave it
alone as  "messin about", as you have seen..can cause issues.
Enjoy !

*I'm going to cheat here a little because TheFu doesnt do  pm's and I have a ping script for him.
Mods..please dont beat me..
@TheFu
#!/bin/bash
gwy=`route -n | awk 'FNR==3{print$2}'`
ping -c2 "$gwy" | awk '/ping/,/2 /' > ping.tst
ping -c2 localhost | awk '/ping/,/2 /' >> ping.tst
ping -c2 8.8.8.8 | awk '/ping/,/2 /' >> ping.tst
ping -c2 google.com | awk '/ping/,/2 /' >> ping.tst
cat ping.tst | awk '{print$2,$6,$8}'
exit

@Aviator1, if you want to give your new Star Tech card a little work out 
copy and paste one line at a time in the above script starting with the * gwy= line
and ending with the * cat line. You will see NO output untill you do the last cat line.
enjoy !

Appreciate your help. I have posted in the install thred to make sure the UEFI stuff is correct.

Have a great day.

Regards,

---

