---
title: "[SOLVED] Cannot get internet working using Intel DP35DP Motherboard"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by FrozenFlame22 on 2007-09-12
I've never had so many problems just connecting to the internet! For years, I've maintained a Windows LAN and kept computers running fairly well long past their prime. I've always considered myself more than computer literate. Heck, I've just built a computer last night with no problems... except...

I just can't connect to the internet. 

I'm ready to toss the whole thing out the window. Especially with Ubuntu, the computer is nigh useless unless I can get the ethernet adapter working. Everything else works beautifully! Just can't bloody connect. ](*,)

Here is my specific build:
Intel Core 2 Duo Processor E6850
Intel DP35DP Motherboard
e-GeForce 8500 GT Graphics Card
Nspire 750W battery
G.Skill DDR2 1GB x 2 (Dual Channel)
Frankensteined DVD drive and 250GB SATA HDD

This is on a home LAN using a Linksys Wireless-G Broadband Router WRT54GS and DSL Actiontec Modem GT701. Both hardware firewalls are off. Other computer in the LAN connects just fine using wireless connection. I'm attempting a wired connection. I've tried using DHCP as well as giving it a static IP, but neither did anything.

I've tried downloading and installing the Gigabit Network Adapter Base Driver for Linux* with 2.4.18 to 2.6.x kernels (e1000-7.6.5.tar.gz) from the Intel download center, but I have several errors. While using Root in the terminal (if my terminology is off, please excuse me, I'm still learning Ubuntu), I followed the Readme instructions exactly. First error was after I typed the command "make install", to which it seemed to follow correctly until this line:

man:
cannot write to /var/cache/man/cat7/e10007.gz in catman mode
e1000.

and the install stops cold. I tried to continue the installation instructions with the command "modprobe e1000", but then I get no feedback. I recognize that some commands don't give any feedback, so I continue to the next: "ifconfig ethx <ip address>" which I entered with the ip address that this computer will have on my LAN. In response I get:

SOICSIFADDR: No such device
ethx: ERROR while getting interface flags: No such device

:confused: I've got too little experience with Linux, much less Ubuntu, to try to move forward with this method, so I tried popping in an old D-link ethernet PCI card. Still nothing.

Thinking that my motherboard might be just too new for Feisty Fawn, I tried installing Gutsy Gibbon, but that yielded identical results. I know it's not the cable, because I used this exact same cable to connect on my other desktop PC just two weeks ago (when it blew capacitors on it's motherboard, but that's another story).

Am I just missing something simple? I don't think I've ever been this frustrated with computers before now. I thought that building the dang thing would be the hard part, not connecting to the internet! :?

Edit:

Solved! See page 2 for solution.

---

### Post by ctzaf on 2007-09-12
I'm having the same issue, although my linksys usb nic connects to the router, but  I can't the DHCP to assign an IP address to the *&^HD t!!!    thing. Pretty aggraviting because it's like 50% there...

your not alone  I have not been to linksys' website maybe there  some informatiohttp://ubuntuforums.org/images/smilies/icon_sad.gif
:(n there:guitar:[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)
:)[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by slira on 2007-09-12
Hi
do you "see" your card(s) in System>Networking?
(this are the KDE names, you probably have something alike)

If yes, sorry, I'm not able to help...

If not, you are probably missing the drivers for your card(s)

What ethernet card do you have? In a LG lap top with the agere 131x card I had a long hard fight to install the drivers!!! 
(please see [http://ubuntuforums.org/showthread.php?t=396467&page=3](http://ubuntuforums.org/showthread.php?t=396467&page=3))

Sorry not helping more, I'm not an expert myself... just learning!

Hope it works
slira

---

### Post by FrozenFlame22 on 2007-09-12
In the network tools I see both cards. The onboard ethernet adapter is eth0 and the PCI card is eth1. I don't know exactly what the PCI card is beyond that it is a D-Link card I bought in 2000. I know Ubuntu has the controller for this one (D-Link System Inc RTL8139) , since it comes up in the hardware list. As for the onboard adapter... installing the driver is the problem; it doesn't seem to install properly (see above errors).

---

### Post by FrozenFlame22 on 2007-09-12
*bump*

Still having problems with this. I'm open to any suggestions!

---

### Post by slira on 2007-09-13
Hi again
just an idea... as I said I'm not an expert, far from that...

do you have the right linux-headers in place, before trying to compile the drivers? 

in a shell type [FONT="Courier New"]uname -r[/FONT]

you get your kernel version

go to [http://packages.ubuntu.com](http://packages.ubuntu.com) select your linux and go to Development

search for the linux-headers matching your kernel. The syntax should be something along the lines of linux-headers-"uname -r result"-386

download it and the dependency called linux-headers-"uname -r result" (do not worry about other dependencies, they should be installed from the cd, if you got build-essentials, and all the dependencies, specially make; if not, you can still do it from your cd)

double click the linux-headers-"uname -r result" and install; the same for the other package

after that you should not get errors trying to do "make"

hope it works!
slira

---

### Post by mips on 2007-09-13
How about showing us your corrent configs + network details.

Have you tried a static ip config yet ?

---

### Post by slira on 2007-09-13
Hi, just another thing I though of:
 when you did "make install", "modprobe e1000" and "ifconfig ethx <ip address>" did you use sudo (switch user (and) do), this makes you root for that command and allows you to write to any directory and execute the commands with full permissions. Which you need to make install modprobe and ifconfig. 

Also, in "ifconfig ethx <ip address>" did you replace the x with the number of your device? I.E. as your pci card is eth1 I believe you should do "ifconfig eth1 <ip address>"

Good luck with getting it working,
Slira

---

### Post by FrozenFlame22 on 2007-09-13
Re: slira:

Thank you very much for responding! It's nice to know I'm not alone in battling this thing. :)

I downloaded and installed this: [http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-15](http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-15)
and it said that it was already installed. I did a reinstall anyway. I ran the driver install again, and still got the same errors. 

I'm not sure what you mean by dependencies. I looked around that page you gave me and I didn't see anything to that effect, besides the headers file. I saw another header file 2.6.20-16, but that's the next number up from my "uname -r" result. I'm probably missing something simple because I'm so new to Linux.

Re: mips

Thanks for responding too! :D

Yup I've tried a static ip too. Same result. I'm pretty sure it's a problem with the driver itself. :/

configs + network details... sorry, no idea what you mean. Is that a terminal command?

---

### Post by FrozenFlame22 on 2007-09-13
re: slira

I took so long replying that I almost missed your last message! Thanks again for all your suggestions! If nothing else, I'm learning more about how Linux operating systems work. :)

In an attempt to isolate the problem, I pulled the PCI card out again. It's supposed to have an LED on the back that is lit regardless of connection, but it wasn't lighting up. I'm thinking that this little card is dead too, so it's back to the drawing board.

When installing the driver, the first thing I did was use "su -" and I did the whole thing as root. 

No I didn't replace the x with the number of the device. I didn't really understand what that was! Thanks for explaining that, and the meaning behind sudo. When I know what things mean, it's easier to remember. ;)

Just for completeness, here's everything copied and pasted from the terminal up to the "catman" error. I saved it and moved it to my other computer via flash drive. I'm going to try your "ethx" suggestion now.

```
frozenflame@Erebor:~$ su -
Password:
root@Erebor:~# lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:01.0 PCI bridge: Intel Corporation Unknown device 29c1 (rev 02)
00:03.0 Communication controller: Intel Corporation Unknown device 29c4 (rev 02)
00:19.0 Ethernet controller: Intel Corporation Unknown device 294c (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.1 PCI bridge: Intel Corporation Unknown device 2942 (rev 02)
00:1c.2 PCI bridge: Intel Corporation Unknown device 2944 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0421 (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
root@Erebor:~# cd /home/frozenflame
root@Erebor :/home/frozenflame# tar xvzf e1000-7.6.5.tar.gz
e1000-7.6.5/
e1000-7.6.5/src/
e1000-7.6.5/src/Makefile
e1000-7.6.5/src/e1000.h
e1000-7.6.5/src/e1000_80003es2lan.c
e1000-7.6.5/src/e1000_80003es2lan.h
e1000-7.6.5 /src/e1000_82540.c
e1000-7.6.5/src/e1000_82541.c
e1000-7.6.5/src/e1000_82541.h
e1000-7.6.5/src/e1000_82542.c
e1000-7.6.5/src/e1000_82543.c
e1000-7.6.5/src/e1000_82543.h
e1000-7.6.5/src/e1000_82571.c
e1000-7.6.5 /src/e1000_82571.h
e1000-7.6.5/src/e1000_api.c
e1000-7.6.5/src/e1000_api.h
e1000-7.6.5/src/e1000_defines.h
e1000-7.6.5/src/e1000_ethtool.c
e1000-7.6.5/src/e1000_hw.h
e1000-7.6.5/src/e1000_ich8lan.c
e1000-7.6.5 /src/e1000_ich8lan.h
e1000-7.6.5/src/e1000_mac.c
e1000-7.6.5/src/e1000_mac.h
e1000-7.6.5/src/e1000_main.c
e1000-7.6.5/src/e1000_manage.c
e1000-7.6.5/src/e1000_manage.h
e1000-7.6.5/src/e1000_nvm.c
e1000-7.6.5 /src/e1000_nvm.h
e1000-7.6.5/src/e1000_osdep.h
e1000-7.6.5/src/e1000_param.c
e1000-7.6.5/src/e1000_phy.c
e1000-7.6.5/src/e1000_phy.h
e1000-7.6.5/src/e1000_regs.h
e1000-7.6.5/src/kcompat.c
e1000-7.6.5/src/kcompat.h
e1000-7.6.5/src/kcompat_ethtool.c
e1000-7.6.5/COPYING
e1000-7.6.5/README
e1000-7.6.5/ldistrib.txt
e1000-7.6.5/pci.updates
e1000-7.6.5/e1000.spec
e1000-7.6.5/e1000.7
e1000-7.6.5/SUMS
root@Erebor :/home/frozenflame# cd e1000-7.6.5/src
root@Erebor:/home/frozenflame/e1000-7.6.5/src# make install
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/frozenflame/e1000-7.6.5/src modules
make[1]: Entering directory `/usr/src/linux- headers-2.6.20-15-generic'
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_main.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_82540.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_82542.o
 CC [M]  /home/frozenflame/e1000- 7.6.5/src/e1000_82571.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_82541.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_82543.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_ich8lan.o
 CC [M]  /home/frozenflame/e1000- 7.6.5/src/e1000_80003es2lan.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_mac.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_nvm.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_phy.o
 CC [M]  /home/frozenflame/e1000- 7.6.5/src/e1000_manage.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_param.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/e1000_ethtool.o
 CC [M]  /home/frozenflame/e1000-7.6.5/src/kcompat.o
 CC [M]  /home/frozenflame/e1000- 7.6.5/src/e1000_api.o
 LD [M]  /home/frozenflame/e1000-7.6.5/src/e1000.o
 Building modules, stage 2.
 MODPOST 1 modules
 CC      /home/frozenflame/e1000-7.6.5/src/e1000.mod.o
 LD [M]  /home/frozenflame/e1000- 7.6.5/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
gzip -c ../e1000.7 > e1000.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.20-15-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.20-15-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.20-15-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man:
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.
root@Erebor:/home/frozenflame/e1000- 7.6.5/src#
```

---

### Post by FrozenFlame22 on 2007-09-13
Just tried pinging from each computer and both are responding to pings, but the internet is not working. I'm using [http://www.google.com](http://www.google.com) to test, but it doesn't even try communicating with the server, and goes directly to the "server not found" page. I've checked in Network Tools to make sure that eth0 is selected, but internet still doesn't work.

On launchpad, I was told that the "catman mode" error has to do with documentation and shouldn't affect the install, so I tried finishing up the install with "lsmod" to check my work. Here are those results:

```
root@Erebor:/home/frozenflame/e1000-7.6.5/src# modprobe e1000
root@Erebor:/home/frozenflame/e1000-7.6.5/src# lsmod
Module                  Size  Used by
e1000                 191552  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
usb_storage            72256  1 
libusual               17936  1 usb_storage
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  2 
cpufreq_userspace       5408  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
battery                10756  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
asus_acpi              17308  0 
ac                      6020  0 
button                  8720  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
backlight               7040  1 asus_acpi
af_packet              23816  4 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
xpad                    9988  0 
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
agpgart                35400  0 
i2c_core               22784  1 i2c_ec
snd_seq_dummy           4740  0 
serio_raw               7940  0 
pcspkr                  4224  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
psmouse                38920  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  5 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  2 
pata_marvell            7936  0 
ata_generic             9092  0 
libata                125720  3 ata_piix,pata_marvell,ata_generic
scsi_mod              142348  6 usb_storage,sbp2,sd_mod,sg,sr_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
uhci_hcd               25360  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
usbcore               134280  7 usb_storage,libusual,xpad,usbhid,uhci_hcd,ehci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
root@Erebor:/home/frozenflame/e1000-7.6.5/src#
```

---

### Post by mips on 2007-09-13
> **FrozenFlame22 said:**
> Just tried pinging from each computer and both are responding to pings, but the internet is not working. 

If you can ping between two computers it tells me your network card is working just fine.

I would suggest:
1. Disable IPv6 Globally (Do a search here and you can use my name as well to find posts on disabling IPv6)
2. Manually configure your DNS servers. Might want to use the OpenDNS servers.

The above should fix your problems.

---

### Post by FrozenFlame22 on 2007-09-13
Thanks again for responding! :)

I've disabled the IPv6 in Firefox and I've used the OpenDNS servers to manually configure my DNS. Still nothing. I even tried giving it a static IP again, just for kicks, but that didn't change anything.  I'm going to open up the case again and put sleeves on all my interior cables, so I'll switch out the Cat5 ethernet cable while I'm at it (even though I -know- this cable is fine).

At this point I've got very few theories left.
1. could be that the motherboard still needs some drivers or firmware update (but I'm not sure what else beyond the e1000 driver.)
2. Ubuntu is incompatible with this motherboard for some other reason that's only manifesting itself right now through the internet not working. (a bit of a stretch there)
3. Router or modem problems (again unlikely because the other computer is working fine)

---

### Post by mips on 2007-09-13
> **FrozenFlame22 said:**
> Thanks again for responding! :)

I've disabled the IPv6 in Firefox and I've used the OpenDNS servers to manually configure my DNS. Still nothing. I even tried giving it a static IP again, just for kicks, but that didn't change anything.  I'm going to open up the case again and put sleeves on all my interior cables, so I'll switch out the Cat5 ethernet cable while I'm at it (even though I -know- this cable is fine).

At this point I've got very few theories left.
1. could be that the motherboard still needs some drivers or firmware update (but I'm not sure what else beyond the e1000 driver.)
2. Ubuntu is incompatible with this motherboard for some other reason that's only manifesting itself right now through the internet not working. (a bit of a stretch there)
3. Router or modem problems (again unlikely because the other computer is working fine)

If you can ping between computers and your router the card is working, leave the drivers alone.

Can you ping google or other sites by there ip address instead of their host name ?

When I said disable ipv6 globally it means system wide and not just in firefox.

Let us know what happens.

---

### Post by FrozenFlame22 on 2007-09-13
Thanks for your patience in staying with me! :)

Disabled ipv6 globally and rebooted as per [this thread]("http://ubuntuforums.org/showthread.php?t=307758").

Pinging Google by IP works (I used 64.233.167.99), but still can't ping by domain. Still no internet access either.

---

### Post by FrozenFlame22 on 2007-09-14
:biggrin: [COLOR="Blue"][SIZE="5"]It's working!!![/SIZE][/COLOR] :biggrin:

I went back to the OpenDNS website and read some more about it, then I set their DNS on my router and modem. That did the trick! Previously, both the router and modem had dynamic DNS rather than static DNS.

Woohoo! :guitar:

Thanks for  all your help! I couldn't have done this without you! :KS :KS :KS :KS :KS

---

