---
title: "Strange network issue"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by bonewhat on 2005-10-26
Hello

I am fairly experienced with linux and currently I use 5.04 on my laptop. I have also tried various distros but I have to say that Ubuntu is the most rewarding to me so far. Yay Ubuntu :D

However, with the last Ubuntu just recently being released (5.10), I wanted to install it on my server/development-box/jukebox. Basically it's a server with apache/mysql/php/sshd/samba and virtual remote desktop for music-playing. Brilliant for use with development, storing stuff and playing music :)

All of the above works perfectly.

Except, after about 4-5 minutes of use it no longer responds (network-wise). I find this VERY odd because tcpdump is still dumping the activity on the network. The link is still up, but I have to do ifdown/ifup or network restart for it to respond again. Then it lasts for x minutes, and we're off again.

I've tried both dhcp and static ip. Result is the same.

/var/log/messages spits out insane amounts of netdev watchdog-messages that tells me that transmit timed out.

My primary thought is perhaps forcing the speed to 100mbit, and not letting the card figure it out itself. However, I dont know where to do this.

Sidenote: Earlier, when I used Gentoo (stage1 :D ) the network card didnt work untill the installation was complete.

The card is an onboard gigabit Yukon-thingymabob on my Asus-motherboard.
(Network is 100mbit)

Please help, as this is far beyond my knowledge.

---

### Post by fabiand on 2005-10-26
hey,

which driver are you using? .. or provide a very nnice `lsmod`

- fabiand

---

### Post by tehwa on 2005-10-26
Also, this could be a DNS problem. If your connection gets up, then resolv.conf is overwritten (every 4-5 minutes) you lose DNS, and much connection. I was plagued by this after setting up Breezy.

You can verify that this is not the case by getting a fresh working connection, then opening ```
/etc/resolv.conf
```and checking DNS server entries. After your connection goes down, check the file again, and see if it has been changed.

---

### Post by bonewhat on 2005-10-26
root@Wrah:~# lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  17
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
i2c_viapro              7696  0
i2c_core               19728  2 i2c_acpi_ec,i2c_viapro
emu10k1_gp              3712  0
gameport               14472  2 emu10k1_gp
snd_emu10k1_synth       6528  0
snd_emux_synth         31744  1 snd_emu10k1_synth
snd_seq_virmidi         6912  1 snd_emux_synth
snd_seq_midi_emul       6528  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                44688  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul                                           ,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1            96772  3 snd_emu10k1_synth
snd_rawmidi            22816  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,s                                           nd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         72188  1 snd_emu10k1
snd_pcm_oss            46368  1
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         10120  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8608  2 snd_emux_synth,snd_emu10k1
snd                    48644  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_                                           seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_                                           oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9184  2 snd
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
via_agp                 9472  1
dm_mod                 50364  1
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  2 via_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  3 ehci_hcd,uhci_hcd
sata_via                8836  0
libata                 47876  1 sata_via
scsi_mod              124872  1 libata
skge                   33040  0
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  7
ide_generic             1664  0
via82cxxx              12188  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   24624  735
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

ouch....

---

### Post by bonewhat on 2005-10-26
DNS doesnt change....

---

### Post by bonewhat on 2005-10-26
64 bytes from 10.0.0.2: icmp_seq=76 ttl=128 time=0.206 ms
64 bytes from 10.0.0.2: icmp_seq=77 ttl=128 time=0.386 ms
ping: sendmsg: No buffer space available
ping: sendmsg: No buffer space available


:confused:

---

### Post by fabiand on 2005-10-27
Hmm, ... well...

Have you installed the latest kernel?

---

### Post by bonewhat on 2005-10-28
A little update on the problem:

1. It seems like TX is the only thing failing
2. Drivers are right
3. Kernel is the one from 5.10, dont have the compy here to check the ver.
4. When moderately used (ssh), it doesnt choke. But when using remote desktop or several users on samba it dies fairly quick.

I think the tx-buffer isnt emptied fast enough when there is a high load. My suspicions are that somehow its expecting the tx-buffer to empty as fast as it would on 1000mbit even though its autodetected to 100mbit. Where can I manually set the speed and tx-queuelength ?

In any case this is very very weird and what I've found on the net describing similar cases doesn't help me at all.

Maybe a different distro would solve it......

[EDIT: typos]

---

### Post by mattisf on 2006-01-02
Hey there,

Did you ever get this resolved? I'm in a similar situation - after a while my network goes down and I get the "ping: sendmsg: no buffer space available" error. I'm using a wireless card with the ndiswrapper ... it wouldn't surprise me at all if the problem is in the driver somewhere. I don't think it's related to the network at all - I have another machine running on the same wireless net and it's just chugging along nicely.

I just started looking into it, so I don't really know much about the problem yet.

Cheers,

Mattis

PS. One more thing - I noticed that if I try to restart the network and run "dhclient" again, the machine freezes totally. I've rarely seen a linux machine behave that badly...

---

### Post by malte on 2006-01-27
Same thing happening here!
I'm using the at76c503 module for an Atmel wireless USB card
```

malte@malteo ~ $ lsmod |grep at76
at76c503_rfmd          42500  0
at76c503               97248  1 at76c503_rfmd
at76_usbdfu             6084  1 at76c503
usbcore               118396  7 quickcam,at76c503_rfmd,at76c503,at76_usbdfu,ehci_hcd,uhci_hcd

```
Without any apparent reason, my connections stops working and I get this in /var/log/messages
```

[4311820.929000] NETDEV WATCHDOG: wlan0: transmit timed out
[4311820.929000] /home/malte/Download/at76c503a/at76c503.c: wlan0: tx timeout.

```
I need to ifup/ifdown wlan0 to get it running again.

This is so bad! :(

---

### Post by feztbrus on 2006-02-20
I'm expecting the same problems with Kubuntu breezy 5.10. The problems occur as soon as I connect to a VPN or remote desktop, then I loose the connection every 4-5 minutes, then it returns again automatically after 2-3 minutes..

---

### Post by smarri on 2006-02-20
Just chiming in to say I am experiencing the same problem also. My internet connection can be fine whilst downloading and suddenly it will stop. I have to stop and start eth0 to get it to carry on. Any light shed on this problem would be appreciated!

---

### Post by adamonduty on 2006-02-21
Each of you should post your dmesg output, as I know I have intermittant problems with my wireless card when the firmware crashes and has to restart.

---

### Post by TylerD75 on 2006-02-28
First off, I'm actually a Gentoo user, but I found this thread in Google.  And as you might expect, I experience the exact same thing.  My if is a D-Link System Inc Gigabit Ethernet Adapter (rev 11), and the driver I use is skge.
I recently read somewhere that skge was better then the old sk98lin driver, but with the old driver I never had these problems.

The error occurs faster if I use a bitTorrent client on the computer, so I have  to agree that it seems as if it has something to do with the amount recieved or transmitted.
Below is what I can see in syslog:
Feb 28 00:36:39 tank kernel: NETDEV WATCHDOG: eth0: transmit timed out
Feb 28 00:37:14 tank last message repeated 7 times
Feb 28 00:38:19 tank last message repeated 13 times
Feb 28 00:39:19 tank last message repeated 12 times

And this is dmesg:
NETDEV WATCHDOG: eth0: transmit timed out
The above line is repeated until I restart my if.  So there's not much to go on to debug this problem.  But it is obvious that the occurance is proportional with the amount of tx/rx packages.
Until anyone finds a fix, I intend to fall back to the sk98lin driver...

Cheers,
TylerD75

---

### Post by Lambert on 2006-02-28
Not sure if directly related, but you will find that netdev watchdog error with  acpi/apci problems. Try booting with acpi=off and/or noapci

You can do a google search for more info as there are quite a few hits. This search narrowed it to 85 links.
[http://www.google.com/search?hl=en&lr=&q=%22NETDEV+WATCHDOG%22+ACPI%3DOFF+gigabit&btnG=Search](http://www.google.com/search?hl=en&lr=&q=%22NETDEV+WATCHDOG%22+ACPI%3DOFF+gigabit&btnG=Search)

---

### Post by TylerD75 on 2006-03-24
The acpi=off option seem to have done the trick!  Thanks a LOT Lambert!!!
I'll post a new msg if it fails again, but I've transfered several Gb now without a hitch.

Cheers,
TylerD

---

