---
title: "Broadcom BCM43222 Driver Installation"
date: 2013-12-09
forum: Networking &amp; Wireless
---

### Post by Kirk Schnable on 2013-12-09
In an effort to upgrade some of our older laptops to dual band cards, we purchased a batch of Broadcom BCM43222 mini-PCI cards from eBay.  We thought we had done adequate testing with the card before we ordered a batch of them, but now we are having trouble deploying them due to driver issues.  

If anyone would like any additional information about this problem, please let me know what you'd like me to paste for you.  Here's what I think is going to be useful in diagnosing this problem:

Relevant information from lshw -C network:
```
  *-network
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=wl latency=64
       resources: irq:21 memory:90304000-90307fff
```

Relevant information from lspci -vv:
```
04:02.0 Network controller: Broadcom Corporation Device 4350
    Subsystem: Broadcom Corporation Device 04d2
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at 90304000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: wl
    Kernel modules: wl
```

Relevant information from lspci:
```
04:02.0 Network controller: Broadcom Corporation Device 4350
```

Related packages we have installed from dpkg --list | grep Broadcom:
```
ii  bcmwl-kernel-source                           6.20.155.1+bdcom-0ubuntu0.0.1           Broadcom 802.11 Linux STA wireless driver source
ii  broadcom-sta-common                           5.100.82.112-4                          Common files for the Broadcom STA Wireless driver
ii  broadcom-sta-source                           5.100.82.112-4                          Source for the Broadcom STA Wireless driver
```

Lsmod:
```
Module                  Size  Used by
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_tcpudp              12531  2 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  4 xt_state,xt_tcpudp,iptable_filter,ip_tables
pcmcia                 39826  0 
wl                   3032542  1 
joydev                 17393  0 
snd_intel8x0           33455  0 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
i915                  428021  2 
snd_seq_midi           13132  0 
thinkpad_acpi          73942  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27428  0 
cfg80211              178877  1 wl
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia_rsrc            18367  1 yenta_socket
drm_kms_helper         45466  1 i915
nsc_ircc               23240  0 
lib80211               14040  1 wl
drm                   197641  3 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96718  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 i915
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62218  8 snd_intel8x0,snd_ac97_codec,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
nvram                  14029  1 thinkpad_acpi
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
irda                  185517  1 nsc_ircc
crc_ccitt              12627  1 irda
video                  19115  1 i915
mac_hid                13077  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tg3                   137318  0 
```

uname -a:
```
Linux test-r52 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:45:16 UTC 2013 i686 i686 i386 GNU/Linux
```

iwconfig:
```
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.
```

Any suggestions would be appreciated! :)

Thanks,
Kirk

---

### Post by chili555 on 2013-12-09
Does this not suggest that the correct driver is not wl but b43? [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) Is your device 14e4:4350 from lspci -nn?

I suggest you experimentally remove bcmwl-kernel-source and install linux-firmware-nonfree.

---

### Post by Kirk Schnable on 2013-12-30
> **chili555 said:**
> Does this not suggest that the correct driver is not wl but b43? [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) Is your device 14e4:4350 from lspci -nn?

I see your point. 

I removed the existing driver.

```
sudo apt-get remove bcmwl-kernel-source --purge
```

 I installed the B43 drivers the way which the link you provided specifies to do so.

```
sudo apt-get install firmware-b43-installer
```

After a reboot, the wireless card is still not detected.  B43 module does not load upon boot.

I tried:
```
sudo modprobe b43
```

This loaded the module, but the card is still unclaimed for some reason.

```
  *-network UNCLAIMED
       description: Network controller
       product: BCM43222 Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:90304000-90307fff
```

```
# lsmod 
Module                  Size  Used by
b43                   342801  0 
mac80211              436493  1 b43
cfg80211              178877  2 b43,mac80211
bcma                   25651  1 b43
ssb                    50691  1 b43
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_state               12514  1 
nf_conntrack           73847  2 nf_conntrack_ipv4,xt_state
xt_tcpudp              12531  2 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  4 xt_state,xt_tcpudp,iptable_filter,ip_tables
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  428092  2 
joydev                 17393  0 
snd_rawmidi            25424  1 snd_seq_midi
pcmcia                 39826  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
nsc_ircc               23240  0 
drm_kms_helper         45466  1 i915
yenta_socket           27428  0 
thinkpad_acpi          73942  1 
pcmcia_rsrc            18367  1 yenta_socket
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
irda                  185517  1 nsc_ircc
psmouse                96744  0 
nvram                  14029  1 thinkpad_acpi
drm                   197641  3 i915,drm_kms_helper
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62218  16 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
crc_ccitt              12627  1 irda
serio_raw              13027  0 
mac_hid                13077  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
video                  19115  1 i915
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
parport_pc             32114  1 
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
binfmt_misc            17292  1 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60184  0 
tg3                   141465  0 
```

```
# iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.
```

```
# dpkg --list | grep b43
ii  b43-fwcutter                                  1:015-9                                  Utility for extracting Broadcom 43xx firmware
ii  firmware-b43-installer                        1:015-9                                  Installer package for firmware for the b43 driver
```

I'm still at a loss unfortunately.  Any suggestions would be appreciated!

---

### Post by Kirk Schnable on 2013-12-30
> **chili555 said:**
> I suggest you experimentally remove bcmwl-kernel-source and install linux-firmware-nonfree.

I removed the b43 drivers I installed earlier.

```
sudo apt-get remove firmware-b43-installer --purge
```

I installed linux-formware-nonfree as you suggested.

```
sudo apt-get install linux-firmware-nonfree
```

After a reboot, the card is still unclaimed.

---

### Post by chili555 on 2013-12-30
It would be lovely if you confirmed the card details:```
lspci -nn | grep 0280
```And also check for clues in the logs:```
dmesg | grep b43
```

---

### Post by Kirk Schnable on 2013-12-30
> **chili555 said:**
> It would be lovely if you confirmed the card details:```
lspci -nn | grep 0280
```
Sure thing.

```
# lspci -nn | grep 0280
04:02.0 Network controller [0280]: Broadcom Corporation BCM43222 Wireless Network Adapter [14e4:4350]
```

> **chili555 said:**
> And also check for clues in the logs:```
dmesg | grep b43
```

dmesg | grep b43 produces nothing.
cat /var/log/syslog | grep b43 also produces nothing.

Nothing in the logs that I see at all that we can go on...

---

### Post by Kirk Schnable on 2013-12-30
I've rounded up some similar threads:

Mark Uhde's thread titled "BCM43222 driver": [http://ubuntuforums.org/showthread.php?t=2007471](http://ubuntuforums.org/showthread.php?t=2007471)  (unsolved)
alanclick's thread titled "After Reboot, Broadcom STA Driver not working": [http://ubuntuforums.org/showthread.php?t=2030025](http://ubuntuforums.org/showthread.php?t=2030025) (supposedly solved by installing b43 drivers)
nutpants's thread titled "login to desktop takes over 60 seconds to start": [http://ubuntuforums.org/showthread.php?t=2073537](http://ubuntuforums.org/showthread.php?t=2073537) (supposedly he's running rmmod wl then modprobe wl at every boot to resolve his issue on the same chipset)

I found this thread as well, on Linuxquestions.org, where a Slackware Linux user has to use ndiswrapper to get this card working with Windows drivers because the native drivers don't work:
[http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesn%27t-yet-work-944073/page3.html](http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesn%27t-yet-work-944073/page3.html)


I think that this card is not very commonly used because it is a Mini PCI form factor and that seems to be the only type of card which uses this chipset.  It seems that in general the people using the cards aren't getting them working and solutions aren't forthcoming for them either.

---

### Post by chili555 on 2013-12-30
Let's try to provoke a response, or, as we say in the South, kick the skunk:```
sudo modprobe b43
dmesg | grep b43
```>  It seems that in general the people using the cards aren't getting them working and solutions aren't forthcoming for them either. I think we are a *long* way from, "It won't work, forget it." Please hang in there.

---

### Post by Kirk Schnable on 2013-12-30
> **chili555 said:**
> Let's try to provoke a response, or, as we say in the South, kick the skunk:```
sudo modprobe b43
dmesg | grep b43
```

Does literally nothing.

```
root@test-r52:~# sudo modprobe b43
root@test-r52:~# dmesg | grep b43
root@test-r52:~# 
```


> **chili555 said:**
> I think we are a *long* way from, "It won't work, forget it." Please hang in there.
I'm hanging in there. :P

---

### Post by chili555 on 2013-12-30
Please reboot so that we have a clean slate and then do:```
lsmod > wifi.txt
dmesg >> wifi.txt
iwconfig >> wifi.txt
```Find the file wifi.txt in your user directory, paste it here and give us the link in your reply. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> Please reboot so that we have a clean slate and then do:```
lsmod > wifi.txt
dmesg >> wifi.txt
iwconfig >> wifi.txt
```Find the file wifi.txt in your user directory, paste it here and give us the link in your reply. [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Sure thing.  See here:  [http://paste.ubuntu.com/6678707](http://paste.ubuntu.com/6678707)

I anticipated since there's not much of use in there that the next thing you'd ask me to do is run "modprobe b43" and generate the same file, so I did that for you already:   [http://paste.ubuntu.com/6678727](http://paste.ubuntu.com/6678727)

---

### Post by chili555 on 2014-01-02
We don't see the expected driver b43 loading at all! I suspect it may be blacklisted. May we see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | tail -n10
```Does your wireless spring to life if you do:```
sudo modprobe b43
iwconfig
dmesg | grep b43
```Thanks.

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> Does your wireless spring to life if you do:```
sudo modprobe b43
iwconfig
dmesg | grep b43
```Thanks.

Did you see my edit from about 9 minutes ago where I posted the follow-up?  Does not help the wireless situation.  I'll get you blacklist info in a moment.

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> We don't see the expected driver b43 loading at all! I suspect it may be blacklisted. May we see:```
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | tail -n10
```

I did find that it was blacklisted due to residual configs left over from Broadcom STA drivers:

```
root@test-r52:/etc/modprobe.d# cat broadcom-sta-common.conf 
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b44
blacklist b43legacy
blacklist b43
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
root@test-r52:/etc/modprobe.d# mv broadcom-sta-common.conf /tmp
root@test-r52:/etc/modprobe.d# cat * | grep "b43"
# replaced by b43 and ssb.
root@test-r52:/etc/modprobe.d# 
```

I have since removed the blacklist entry and I am rebooting.  I will produce another new file for you in a few minutes.

---

### Post by Kirk Schnable on 2014-01-02
After removing the blacklist, B43 still isn't loading automatically at boot time.  See here: [http://paste.ubuntu.com/6678811](http://paste.ubuntu.com/6678811)

---

### Post by chili555 on 2014-01-02
> **Kirk Schnable said:**
> After removing the blacklist, B43 still isn't loading automatically at boot time.  See here: [http://paste.ubuntu.com/6678811](http://paste.ubuntu.com/6678811)I'm not sure exactly what you removed but please try this:```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```Now reboot with the ethernet detached and let us see a paste again. 

This actually looks pretty hopeful:> [  408.923952] cfg80211: Calling CRDA to update world regulatory domain
[  409.334599] Broadcom 43xx driver loaded [ Features: PNL ]
[  409.869473] cfg80211: World regulatory domain updated:
[  409.869484] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  409.869493] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  409.869502] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  409.869510] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  409.869518] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  409.869526] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> I'm not sure exactly what you removed but please try this:```
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```
The blacklist for B43 is already gone.  

```
root@test-r52:/etc/modprobe.d# ls -1
alsa-base.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-rare-network.conf
blacklist-watchdog.conf
dkms.conf
vmwgfx-fbdev.conf
root@test-r52:/etc/modprobe.d# cat * | grep "b43"
# replaced by b43 and ssb.
root@test-r52:/etc/modprobe.d# 
```


> **chili555 said:**
> Now reboot with the ethernet detached and let us see a paste again. 
Doing so now.  Will update with the results shortly.

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> Now reboot with the ethernet detached and let us see a paste again.

After a reboot, the B43 driver does not load, and the part of dmesg you thought looked hopeful does not occur.

This is the generated information after a fresh reboot (no network cable plugged in):
[http://paste.ubuntu.com/6679136](http://paste.ubuntu.com/6679136)

Then, after a fresh reboot and immediately after running "modprobe b43":
[http://paste.ubuntu.com/6679118](http://paste.ubuntu.com/6679118)

---

### Post by chili555 on 2014-01-02
Although b43 and its co-driver ssb are supposed to drive your devices, apparently it doesn't.```
$ modinfo ssb | grep 4350
alias:          pci:v0000[COLOR="#FF0000"]14E4[/COLOR]d0000[COLOR="#FF0000"]4350[/COLOR]sv*sd*bc*sc*i*
```Worse, dmesg gives no clue as to why. Let's try a different approach. There is an updated proprietary Broadcom STA driver available. Let's try it:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Add these lines at the bottom:```
blacklist b43
blacklist ssb
blacklist bcma
```Proofread, save and close gedit. Now, with a temporary wired ethernet connection, do:```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
sudo mkdir /usr/src/hybrid-portsrc_x86_32-6.30.223.141
wget http://media.cdn.ubuntu-de.org/forum/attachments/36/49/2865859-hybrid-portsrc_x86_32-v6_30_223_141_dkms.tar.gz
sudo tar xvf 2865859-hybrid-portsrc_x86_32-v6_30_223_141_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_32-6.30.223.141 
sudo dkms add -m hybrid-portsrc_x86_32 -v 6.30.223.141
sudo dkms build -m hybrid-portsrc_x86_32 -v 6.30.223.141
sudo dkms install -m hybrid-portsrc_x86_32 -v 6.30.223.141 


```This assumes yours is a 32-bit system; verify:```
arch
```If yours is a 64-bit system, then the process is changed slightly:```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/36/49/2865859-hybrid-portsrc_x86_64-v6_30_223_141_dkms.tar.gz
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v6_30_223_141_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-6.30.223.141 
sudo dkms add -m hybrid-portsrc_x86_64 -v 6.30.223.141
sudo dkms build -m hybrid-portsrc_x86_64 -v 6.30.223.141
sudo dkms install -m hybrid-portsrc_x86_64 -v 6.30.223.141 
```Reboot, detach the ethernet and cross your fingers.

---

### Post by Kirk Schnable on 2014-01-02
> **chili555 said:**
> This assumes yours is a 43-bit system; verify:```
arch
```
It's an i686 architecutre.  Not sure what qualifies as "43-bit", but I am certain it's not a 64-bit architecture.  I am running with the 32-bit instructions and I will let you know how it goes.  Fingers crossed!

---

### Post by Kirk Schnable on 2014-01-02
Still no luck...  Here's the information this time (lsmod, dmesg, and lshw -C network).
[http://paste.ubuntu.com/6679388](http://paste.ubuntu.com/6679388)

Still no wireless devices listed in iwconfig.

---

### Post by chili555 on 2014-01-02
> **Kirk Schnable said:**
> It's an i686 architecutre.  Not sure what qualifies as "43-bit", but I am certain it's not a 64-bit architecture.  I am running with the 32-bit instructions and I will let you know how it goes.  Fingers crossed!What constitutes 43-bit is clumsy old hands. Post edited...sorry.

---

### Post by chili555 on 2014-01-02
> In an effort to upgrade some of our older laptops to dual band cards, we purchased a batch of Broadcom BCM43222 mini-PCI cards from eBay.The last resort to get these cards going is ndiswrapper: [http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesn't-yet-work-944073/page3.html](http://www.linuxquestions.org/questions/linux-hardware-18/broadcom-bcm43222-slackware-13-37-doesn't-yet-work-944073/page3.html)  See post #36. However, I am quite confident that the creaky old XP driver is not going to do dual-band. We could try it or you could return or re-sell the cards. What do you prefer?

---

