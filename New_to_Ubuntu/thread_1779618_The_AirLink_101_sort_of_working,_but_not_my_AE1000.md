---
title: "The AirLink 101 sort of working, but not my AE1000"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by Acrosby on 2011-06-10
The computer boots up, the keyring thing happens(BTW, I think I got rid of that, or at least stopped it from popping up), I choose my network and enter my password, it tries to connect , but doesn't.

---

### Post by jtarin on 2011-06-10
Are you talking about your internet connection? If yes post the output from the terminal command ```
lspci
```

---

### Post by Acrosby on 2011-06-10
ashley@ashley-GA-MA790XT-UD4P:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:04.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port A)
00:0a.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port F)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:06.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
ashley@ashley-GA-MA790XT-UD4P:~$

---

### Post by jtarin on 2011-06-10
How do you connect to the internet? Cable,ADSL or other. Do you use a router?

---

### Post by chili555 on 2011-06-10
I'm sure he meant:```
lsusb
```Are you trying to get the Airlink working or the AE1000? I seriously hope not both at the same time!

---

### Post by Acrosby on 2011-06-10
I am connected with a wire to my Bell wi fi box, I want to be able to move my computer to another room that doesn't have a bell outlet and installing one there would be very difficult. I want to connect with one or the other, not both.



ashley@ashley-GA-MA790XT-UD4P:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ashley@ashley-GA-MA790XT-UD4P:~$


I think we have exhausted the AE1000 doctor, lets try for the AirLink101

---

### Post by chili555 on 2011-06-10
This device works with r8712u in Ubuntu Natty 11.04. Is that your version? Any interesting messages here?```
dmesg | grep 8712
```

---

### Post by Acrosby on 2011-06-10
Nothing, I am stuck on 10.10 Meerkat, I tried to update the machine to 11.04, but it didn't play nice with compiz, so I reinstalled Meerkat

---

### Post by chili555 on 2011-06-10
I wonder what in the wide world of sports is uh drivin' it then. I wasn't aware that r8712u was in Meerkat. May we see:```
lsmod
```You didn't get real brave and compile it from scratch, did ya?

---

### Post by Acrosby on 2011-06-10
> **Acrosby said:**
> Nothing, I am stuck on 10.10 Meerkat, I tried to update the machine to 11.04, but it didn't play nice with compiz, so I reinstalled MeerkatStuck is a harsh word, prefer would have been better

---

### Post by Acrosby on 2011-06-10
ashley@ashley-GA-MA790XT-UD4P:~$ lsmod
Module                  Size  Used by
arc4                    1165  0 
nls_utf8                1069  1 
udf                    79366  1 
binfmt_misc             6599  1 
parport_pc             26378  0 
ppdev                   5556  0 
dm_crypt               11385  0 
r8192s_usb            287308  0 
rt3572sta             619883  0 
snd_hda_codec_atihdmi     2411  1 
snd_hda_codec_realtek   218492  1 
eeprom_93cx6            1345  1 r8192s_usb
snd_hda_intel          22299  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2252898  91 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                  8767  0 
serio_raw               4022  0 
soundcore                880  1 snd
i2c_piix4               8795  0 
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
k10temp                 2607  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
hid_logitech            8971  0 
ff_memless              4393  1 hid_logitech
usbhid                 36978  1 hid_logitech
hid                    67742  2 hid_logitech,usbhid
firewire_ohci          21554  0 
firewire_core          46675  1 firewire_ohci
ati_agp                 5202  0 
floppy                 54343  0 
r8169                  36777  0 
crc_itu_t               1383  2 udf,firewire_core
mii                     4425  1 r8169
ahci                   19198  3 
pata_atiixp             3288  0 
pata_jmicron            1855  0 
agpgart                32075  2 fglrx,ati_agp
libahci                21792  1 ahci
ashley@ashley-GA-MA790XT-UD4P:~$ 

no doctor, I am to green to do something like that, I am used to windows, where everything is in a nice package for you

---

### Post by chili555 on 2011-06-10
> where everything is in a nice package for youThat's fine for some people, just not for me, my wife, my sister and my old racin' buddy. 

It looks like r8192s_usb has grabbed the Airlink. I wonder if having both that and rt3572sta loaded is causing a conflict. Please do, as a temporary experiment:```
sudo gedit /etc/modules
```Change this:

rt3572sta

to this:

#rt3572sta

Proofread carefully, save and close gedit. Reboot. Is the Airlink working better now? If not, we can dig deeper.

---

### Post by Acrosby on 2011-06-10
I have to disconnect the ethernet now, be right back

---

### Post by Acrosby on 2011-06-10
no luck, I received this "attached" I wonder if I shut off my security, if it'll connect?

---

### Post by chili555 on 2011-06-10
I assume you mean it asks, you provide the key, it asks, etc.

I am at a little disadvantage here. I do not have r8192s_usb on my Natty system, so I have to depend on you. Do you have linux-firmware installed?```
sudo dpkg -s linux-firmware
```If not, please install it:```
sudo apt-get install linux-firmware
```Then unload and reload the module:```
sudo ifconfig wlan0 down
sudo rmmod -f r8192s_usb
sudo modprobe r8192s_usb
sudo ifconfig wlan0 up
```Any improvement?

See you tomorrow.

---

### Post by Acrosby on 2011-06-10
Nothing

---

### Post by Acrosby on 2011-06-11
Hey Doctor,

Fooling around this morning I decided to try the AE1000 again, first on Windows 7 then on Ubuntu 10.10. The connection was established in windows, so then I rebooted into Ubuntu. low and behold, there it was. the wireless networks. I tried to establish connection but security wouldn't let me pass, so I hard wired my machine and entered my bell box through Firefox and suspended the security. I rebooted the bell box, and Ubuntu and a connection was made. After confirming my connection with Chrome/You tube, I reinstated the security on the bell box, I don't know what we did, but we did it. Now just to get passed that security thing. While in the Bell box, I noticed that the security was on WEP, in Ubuntu, it tries to connect with WEP128 bit, is there a setting in Ubuntu for just WEP? Would that be why I can't get passed the security? Does this justify starting a new thread?

Ash

---

### Post by chili555 on 2011-06-11
> While in the Bell box, I noticed that the security was on WEP, in Ubuntu, it tries to connect with WEP128 bit, is there a setting in Ubuntu for just WEP? WEP 128-bit is 26 hex characters. Is that what you have? WEP 40/64-bit is ten hex characters. If your password is ten and it expects 26, that's a pretty good indicator that something in the driver, the hardware, wpa_supplicant or Network Manager is not working properly. 

You might try right-clicking the Network Manager icon and Edit Connections. Under wireless and IPv4 settings, change from DHCP to Manual. Fill in the address, netmask, gateway, DNS nameservers and WEP encryption. You can use all these settings from your Windows partition. I believe the netmask is handled a bit differently in Windows; in Ubuntu, it's 255.255.255.0.

---

### Post by Acrosby on 2011-06-11
my password is only 10 characters long, if that what you mean.and where is the network manager icon? I don't have any icons on my desktop?

Never mind, I found it. Where and How do I get the addresses and stuff?

---

### Post by chili555 on 2011-06-11
Ten characters is correct for 40/64-bit WEP. The NM icon should be at the top right. I will log in to my Natty computer running NM and post a screenshot. Are there icons up there you can hover over and see NM? BRB.

Edit: Here's the screenshot from my Natty install running Unity. The NM icon should be similar in all recent versions. It's that fan-looking item right above my cursor. I've clicked it and you can see I'm connected to GBR1. MAHB is my neighbor. If you are not connected, there are no waves in the fan and it looks more like a triangle or cone (mint chocolate chip, please).

---

### Post by Acrosby on 2011-06-11
LOL, ok, I found the numbers to enter in windows7, rebooted ubuntu, entered the numbers, I get a "connection established" doohicky with a good signal strength but when I open a web browser, Chrome or Fire fox, it says can't find, try again?

---

### Post by VOT Productions on 2011-06-11
Make sure that you have set the auto-connect to "Automatic with DHCP"

---

### Post by Acrosby on 2011-06-11
I'm so sorry, but where is that?, darn I hate being green!!!!

---

### Post by Acrosby on 2011-06-11
this line is the closest I can find to DHCP and it's ghosted

---

### Post by VOT Productions on 2011-06-11
Switch that to Automatic with DHCP instead of Manual.

---

### Post by Acrosby on 2011-06-11
Hello VOT, I don't know if you have been following this Thread, but this has been going on for a few days now, the wireless wouldn't connect in Auto mode, thats why we switched to manual ETC. the doctor seems to know whats going on here (he has been 99% right so far) and he has his kid gloves on so thank you for the input.

Doctor,
After re-entering the numbers I have my connection back, but still cannot connect to a website?
Ash

---

### Post by chili555 on 2011-06-11
No, no, don't re-enter the numbers. Drop down the Manual drop-down and select DHCP. Here's a screenshot. The numbers will go away and the system will figure all the rest out for you.

Or, is it the case that it *_only_* connects manually??

---

### Post by Acrosby on 2011-06-11
It shows me as connected but wont pull up a website,maybe if I reboot with the new settings? one minute please.

---

### Post by Acrosby on 2011-06-11
so far so good doctor,
 I think the reboot may have did something, I am typing you this unwired and all my links seem to work. is there a way to put in a double solved on the thread? I want to thank you so much for all your time a patience, and all your help
I will be back here if something crashes, but everything is looking good so far and there will probably be no issues.
Thank you
Ashley

---

### Post by chili555 on 2011-06-11
> I will be back here if something crashes, Please do. I'm glad it's working. Have fun!

---

### Post by VOT Productions on 2011-06-11
Wasn't I first to suggest DHCP?

---

### Post by jtarin on 2011-06-11
> **VOT Productions said:**
> Wasn't I first to suggest DHCP?No I don't think so.....unless you were in that bunch of guys back in 1993 that wanted to extend BOOTP! :p

---

### Post by chili555 on 2011-06-11
Ahh! BOOTP; those were the days. Remember when just about everything you needed was a tarball and dependency hell?

---

### Post by jtarin on 2011-06-11
> **chili555 said:**
> Ahh! BOOTP; those were the days. Remember when just about everything you needed was a tarball and dependency hell?Yea! I feel guilty, about half the time using Ubuntu. Sacrilege!!! :p

---

