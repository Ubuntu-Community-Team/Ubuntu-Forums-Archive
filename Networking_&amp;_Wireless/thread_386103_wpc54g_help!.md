---
title: "wpc54g help!"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by fleshberkowski on 2007-03-16
i was reading the forums on how to install the wpc54g wifi card and came across a posting  giving precise instructions for how to start from scratch and install the card.

[http://www.ubuntuforums.org/showthread.php?t=371035&page=2&highlight=WPC54G](http://www.ubuntuforums.org/showthread.php?t=371035&page=2&highlight=WPC54G)

i got to the point where you actually put the card in and type: "ndiswrapper -l" and when i did that, i got: "lsbcmnds invalid driver! lstinds invalid driver! i was wondering if anyone knew what could be causing this. i followed an almost identical set of instructions the other day, but remember getting to the point where it said: 

lsbcmnds driver installed
lstinds driver installed, 

but notice, it didn't say hardware installed. i feel like i've done so many of the guides on this forum for setting up wifi cards that i'm completely lost. any info would be greatly appreciated

thanks,

doug

ps. i'm runing a dell c600 and the wpc54g is version 3.1 (i got the 3.1 drivers off of the linksys ftp, and not the v2.0 listed in the guide)

---

### Post by MeeMaw on 2007-03-16
That would be a good one to follow if your card needs the BCM4311 (I think it said) driver...... If your Linksys needs a different driver (Linksys uses lots!) you need to get the driver for your card. Please post the output of 

sudo lspci

so we can see what you have.   Thanks!

---

### Post by chili555 on 2007-03-16
I am troubled by the WPC54G listings here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

It shows Version 3 as being the lovely Broadcom 4318 chip. It also says: > Couldn't get any of the windows drivers from linksys.com to work (they don't have a version 3 one listed right now) but I tried the driver off the installation CD with ndiswrapper and it worked like a charm! Just follow normal ndiswraper driver installation with the NT driver from the linksys install CD that comes with the card

Do you have the CD?

I went to the Linksys site and downloaded the version 3.1 driver and unzipped it and got this: ```
inflating: wpc54g_v31_driver_4.100.15.5_Vista/bcm43xx.cat  
  inflating: wpc54g_v31_driver_4.100.15.5_Vista/bcm43xx64.cat  
  inflating: wpc54g_v31_driver_4.100.15.5_Vista/bcmwl5.sys  
  inflating: wpc54g_v31_driver_4.100.15.5_Vista/bcmwl564.sys  
  inflating: wpc54g_v31_driver_4.100.15.5_Vista/Lsbcmnds.inf
```
I suggest doing lspci -v with the card inserted and if it is a Broadcom chip, try these instead.

Post back if we can help. 

PS - Hello, Sis!

---

### Post by MeeMaw on 2007-03-16
I agree with chili555
(Thanks, bro!)

---

### Post by fleshberkowski on 2007-03-16
i believe i ran that command before and it said bcm4318. i'm still at work but i'll be home in an hour and i'll doublecheck that.

also, what was chili referring to when he said "try these instead"?

---

### Post by fleshberkowski on 2007-03-17
ok, i ran sudo lspci and this what it spit out:
> 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge 
(rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420
00:03.1 CardBus bridge: Texas Instruments PCI1420
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



and then when i tried lspci -v, this is what i got:
> 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 32
        Memory at f4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fd000000-feffffff
        Prefetchable memory behind bridge: f8000000-fbffffff

00:03.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 28000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 22000000-23fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:03.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 28001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 24000000-25fff000 (prefetchable)
        Memory window 1: 26000000-27fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 32
        I/O ports at 0860 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at dce0 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
        Flags: medium devsel, IRQ 9

00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
        Subsystem: Dell Latitude C600
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=256]
        Memory at f3ffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
        Subsystem: 3Com Corporation Unknown device 6456
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d400 [size=256]
        Memory at f3ffdc00 (32-bit, non-prefetchable) [size=128]
        Memory at f3ffd800 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
        Subsystem: 3Com Corporation Unknown device 615b
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d000 [size=256]
        Memory at f3ffd400 (32-bit, non-prefetchable) [size=256]
        Memory at f3ffd000 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Latitude C600
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        I/O ports at ec00 [size=256]
        Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
        [virtual] Expansion ROM at fd000000 [disabled] [size=128K]
        Capabilities: <access denied>

06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys Unknown device 0048
        Flags: fast devsel, IRQ 11
        Memory at 26000000 (32-bit, non-prefetchable) [disabled] [size=8K]


---

### Post by fleshberkowski on 2007-03-17
and yes, i do have the cd.

---

### Post by chili555 on 2007-03-17
Look on the CD and find the .inf and .sys files from the Windows NT folder, copy them to any convenient place, like /home/<your_username>. Remove the non-working files: ```
ndiswrapper -e lsbcmnds
ndiswrapper -e lstinds
```
You will probably have to remove them from your system altogether by doing sudo updatedb, then locate lstinds, then sudo rm /path/to wherever/lstinds. Do the same for the other non-working file. Be sure not to rm the files in /home/<your_username>.

Do the follwing: ```
ndiswrapper -i filename.inf
ndiswrapper -i filename.sys
ndiswrapper -l
```
Any complaints about the driver?

---

### Post by fleshberkowski on 2007-03-17
yea, it says the "bcmwl5.sys" is an invalid driver. the lsbcmnds driver is installed and it says, hardware present (which it didn't say before).

---

### Post by chili555 on 2007-03-17
So you have driver installed and hardware present. Are you now able to configure your card and connect?

---

### Post by fleshberkowski on 2007-03-17
no. when i go into network manager, it says there's a wired connection and it's enabled, but when i remove the ethernet cable, it doesn't connect. does it make a difference that my network connection is "lo" or "etho"? also, in my network settings, it only says that there's a wireless connection and a modem... so is my ethernet wrongly configured as my wireless? if you couldn't  tell i'm a bit of anovice, just got ubuntu last thursday.

---

### Post by shawnb on 2007-03-17
I believe I am having the same problem has the previous poster here. I am still looking for a solution, but have not come across anything yet. Using ndiswrapper I have the driver loaded, and hardware present. Here is a copy of my ndiswrapper -l output.

> 
lsbcmnds                driver installed, hardware present
lstinds         driver installed
net5211         driver installed, hardware present


This is using v3.0 drivers from Linksys (the version of my card). The lstinds in the list is probably useless (someone confirm this for me please), it is from a tutorial for version 2.0 (I was desperate for a solution). The net5211 is for my built-in wireless (Acer 3100 Aspire); and it works fine, hence my ability to post this.

Despite there being hardware present, I am unable to get the connection up. I am using wpa_supplicant to connect to my wireless using WPA encryption. WPA works perfectly with my builtin wireless. Issuing the command:
> sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant.conf

results in the following.

> 
SIOCSIFFLAGS: No such file or directory
Could not set interface 'eth1' UP
l2_packet_receive - recvfrom: Network is down
ioctl[SIOCSIWSCAN]: No such device
Failed to initiate AP scan.


Notice the first line, I believe it is not finding firmware. Though I am not sure where it should be looking, or where I should be looking to get the proper firmware. Here is the result of dmesg | tail

> 
[17202387.300000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


As you can see, it looks like I am missing bcm43xx_microcode5.fw. If anyone has an insight into this, it would be greatly appreciated by myself, and I'm sure the previous poster is suffering from the same issue.

If I find the solution, I'll make a follow up posting.

-Shawn

---

### Post by shawnb on 2007-03-17
Solution found!

Ok, to anyone who is still having trouble with the WPC54G v3.0 this is what I have done since my last post to get it working.

1st. I removed the lstinds driver. It was unnecessary.
> sudo ndiswrapper -e lstinds

2nd. The issue as I suspected last time was firmware related, basically unless I missed it in the tutorial; there was no firmware installed for the card. So I found that i needed a program called bcm43xx-fwcutter which could take the driver file for the broadcomm chip and extract the firmware, for us non-windows users. It was in my apt sources, here is my sources.list just in case it is not in yours you can copy mine.
> 
# 
# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
#deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END


I used the command > sudo apt-get install bcm43xx-fwcutter  to get the program.

3rd. Go back to your folder where you drivers are (either from the Linksys ftp; or from the driver CD included with your card) and type this at the terminal:
> 
sudo bcm43xx-fwcutter -w /lib/firmware/ BCMWL5.SYS


It's going to bitch a little about a copy of firmware files it could not extract, but overall it doesn't seem to really matter, as I am using the card right now to post this.

4th. Edit /etc/modprobe.d/blacklist and get rid of the kernel drivers, by adding this line: 
> 
# get rid of the default kernel drivers
blacklist bcm43xx


I also added the following line to my /etc/iftab file. I'm not sure this was necessary, but it doesn't seem to hurt. Be sure you replace my MAC address with whatever yours is.
> 
eth1 mac 00:18:39:87:7A:D9 arp 1


Hope this helps whoever out there still has this card not working. I'm been using Kubuntu for about a year now on my laptop, so I have some experience with it. If anyone needs anything cleared up, I'll do my best to do so.

-Shawn

---

### Post by fleshberkowski on 2007-03-17
hey shawn,

i'm going to try this. i had a question. what exactly does blacklisting do? i blacklisted something the other day when i was trying to get this card to work and didn't notice a difference. also, the mac address.. what is that? you're not referring to your ip address right? oh and one last thing, is there a way to find out what networks are available? currently, we steal wifi from our neighbors (i know it's unethical... but it's free and i'm poor), and i know the name of a couple of wifi networks to choose from but was wondering if there was some sort of gui i can download that detects wifi connections in the area. 


-doug

---

### Post by fleshberkowski on 2007-03-17
ok, tried it with the exception of the last guide (adding the mac address) and it stildoesn't work. i already had bwcutter and had it listed. gah! help please.

---

### Post by shawnb on 2007-03-17
> i'm going to try this. i had a question. what exactly does blacklisting do? i blacklisted something the other day when i was trying to get this card to work and didn't notice a difference. also, the mac address.. what is that? you're not referring to your ip address right? oh and one last thing, is there a way to find out what networks are available? currently, we steal wifi from our neighbors (i know it's unethical... but it's free and i'm poor), and i know the name of a couple of wifi networks to choose from but was wondering if there was some sort of gui i can download that detects wifi connections in the area.

Blacklisting stops Ubuntu from loading the kernel driver. As far as I know. Basically since you are getting the driver from Linksys, you don't want to have it conflicting.

MAC (Media Access Control) address is a hardware address which uniquely identifies your hardware. If you pull out your card, and look on the back, it has written MAC: nn:nn:nn:nn:nn:nn. Where each pair of nn is a hexadecimal number.

Wireless Lan Assistant will show you which networks are available in your area. I use KDE so, if you are running Gnome I'm not sure where it would be, but you can run it from the terminal by calling: wlassistant. Just a heads up though. If you do not have a router in your possession to test with you may not be getting a fully accurate account of what the problem you are having is. Your neighbors, though they may have an unsecured connection, may be using a MAC filter; thereby not allowing anyone but them to connect and you would not be informed of the case; as far as you would see it just wouldn't be working. So, despite your monetary situation, you may want to at least get yourself a router you have control over, at least until you know what is going on with your system.

From your command line type:
> sudo ifconfig [your network interface name] up

Where I put [your network interface name], you need to replace that with the interface name you have configured for this card. After issuing that command, post back here what you get from:
> dmesg | tail

-Shawn

---

### Post by fleshberkowski on 2007-03-17
ok, for the network name i tried a whole bunch of possibilities and the one that didn't return an error was "lo" could that be right? if not where could i find the network name? well this is what "lo" spit out:

> 
[17206198.276000] cpufreq: change failed with new_state 0 and result 0
[17206200.424000] cpufreq: change failed with new_state 1 and result 0
[17206249.480000] cpufreq: change failed with new_state 0 and result 0
[17206253.616000] cpufreq: change failed with new_state 1 and result 0
[17206259.908000] cpufreq: change failed with new_state 0 and result 0
[17206263.036000] cpufreq: change failed with new_state 1 and result 0
[17206279.408000] cpufreq: change failed with new_state 0 and result 0
[17206283.600000] cpufreq: change failed with new_state 1 and result 0
[17206454.304000] cpufreq: change failed with new_state 0 and result 0
[17206460.264000] cpufreq: change failed with new_state 1 and result 0


---

### Post by jglen490 on 2007-03-17
Looks like you are pretty close to being there.  Need to know what modules are actually loaded.  What quite often happens is the module gets installed on the machine, but is not registered as a kernel module.

Please enter this in a terminal:

```
lsmod
```

It's possible that you still have "dueling drivers" :guitar: .  (Sorry, couldn't find a banjo)

---

### Post by fleshberkowski on 2007-03-17
here's what i got:

> 
Module                  Size  Used by
nls_cp437               6912  0 
isofs                  38076  0 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
xt_limit                3840  8 
xt_tcpudp               4480  9 
iptable_mangle          3968  0 
ipt_LOG                 8320  8 
ipt_MASQUERADE          4864  0 
ip_nat                 19884  1 ipt_MASQUERADE
ipt_TOS                 3456  0 
ipt_REJECT              6784  1 
ip_conntrack_irc        7920  0 
ip_conntrack_ftp        8816  0 
xt_state                3328  6 
ip_conntrack           53216  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,xt_state
nfnetlink               8216  2 ip_nat,ip_conntrack
iptable_filter          4224  1 
ip_tables              15204  2 iptable_mangle,iptable_filter
x_tables               16132  8 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,ip_tables
r128                   42368  2 
drm                    74644  3 r128
ipv6                  272288  8 
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
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ndiswrapper           208656  0 
lp                     12964  0 
af_packet              24584  4 
joydev                 11200  0 
floppy                 63044  0 
pcmcia                 40380  0 
tsdev                   9152  0 
serio_raw               8452  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
evdev                  11392  2 
snd_maestro3           27524  1 
snd_ac97_codec         97696  1 snd_maestro3
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
psmouse                41352  0 
pcspkr                  4352  0 
snd_pcm                84612  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd_page_alloc         11400  1 snd_pcm
snd                    58372  8 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
i2c_piix4              10000  0 
yenta_socket           28812  3 
rsrc_nonstatic         15360  1 yenta_socket
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
3c59x                  47912  0 
mii                     6912  1 3c59x
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
soundcore              11232  1 snd
i2c_core               23424  2 i2c_ec,i2c_piix4
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
ext3                  142856  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
usbcore               134912  3 ndiswrapper,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
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


---

### Post by jglen490 on 2007-03-17
O.K., you have ndiswrapper loaded.  Assuming that you have blacklisted bcm43xx, and have rebooted after doing that, there should be no driver conflicts.

One more time, please, enter this in a terminal:

```
ndiswrapper -l
```

There should be one line that shows the driver that you installed with the "ndiswrapper -i" command.

You should then be able to enter:

```
iwlist wlan0 scan
``` if your wifi is on some other device like eth1, then use that in place of wlan0.  The result should be the APs that your card sees.

---

### Post by fleshberkowski on 2007-03-17
ndiswrapper said this: 
> 
Installed drivers:
bcmwl5.sys      invalid driver!
lsbcmnds                driver installed, hardware present 


and this is what i got entering wlan scan:
> 
wlan0     Scan completed :
          Cell 01 - Address: 00:E0:98:FE:12:F6
                    ESSID:"05B404076478"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 02 - Address: 00:12:0E:0F:37:90
                    ESSID:"tetrad"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-88 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=50
                    Extra:atim=0
          Cell 03 - Address: 00:E0:98:FD:95:19
                    ESSID:"05B412899279"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-96 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
          Cell 04 - Address: 00:E0:98:CD:A6:E5
                    ESSID:"04Z410206545"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-67 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0


---

### Post by fleshberkowski on 2007-03-18
i feel like i'm so close, i finally have a wlan option in the network manager shortcut (before it was just eth0 and lo) but i'm still not getting a connection. i'm actually typing this on my other computer right now.

---

### Post by fleshberkowski on 2007-03-18
ahh! i got it working! i don't know how exactly, i restarted, tried one essid, didn't work tried another and it did. hope it's not a fluke. thanks to all who helped.

---

### Post by shawnb on 2007-03-18
Congratulations on getting it working, however I don't think you should be seeing that invalid driver in the list. I in fact do not even have a listing for bcmwl5.sys, only lcmnds. I'm wondering if you put that in there in some of your attempts to get it working, and it is just unnecessary at this point.

I've been using mine for a few hours now, and I'll share some things I've noticed so far. The card suffers like almost every pcmia card and is under powered. It does not find many networks in my area, and doesn't stay connected to one for too long before just falling off. I'm not sure if that is because of the errors with the firmware or whether it is the card just not working well. I'll try to put it through some more rigorous tests tomorrow.

-Shawn

---

### Post by jglen490 on 2007-03-18
> ndiswrapper said this:
Quote:
Installed drivers:
bcmwl5.sys invalid driver!
lsbcmnds driver installed, hardware present


The bcmwl5._sys_ is an invalid driver.  The bcmwl5 may or may not be invalid for your card and usually ndiswrapper uses the _.inf_ file to install whatever is needed for that driver to work.  If you still see it, you could probably simply uninstall it with:

```
ndiswrapper -e bcmwl5.sys
``` spelling out the entire file name with the _.sys_ included.

It's good that it's working.

---

### Post by kemp_samurai on 2007-03-18
I have a WPC54G v3 card that, I installed the NT drivers off the Cd via ndiswrapper, and i get the following message when i type:
> sudo -s
ndiswrapper -l

i get > lsbcmnds        driver present, hardware present

---

### Post by shawnb on 2007-03-18
> 
I have a WPC54G v3 card that, I installed the NT drivers off the Cd via ndiswrapper, and i get the following message when i type:
Quote:
sudo -s
ndiswrapper -l
i get
Quote:
lsbcmnds driver present, hardware present


Forgive me for sounding blunt, kemp_samurai, but what's the problem?

-Shawn

---

### Post by jgcamp99 on 2007-03-19
With the pcmcia cardbuses I have, I found it wasn't an issue of the card or drivers, it was that the router needed to be reset. I wound up resetting it back to factory default and then reconfigured it. All of a sudden Ubuntu worked and so did my Apple PB.

---

