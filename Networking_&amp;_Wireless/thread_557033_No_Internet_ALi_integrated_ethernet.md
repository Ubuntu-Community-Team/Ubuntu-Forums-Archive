---
title: "No Internet: ALi integrated ethernet"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by Somnus07 on 2007-09-22
Hello,

my NIC is an ALi integrated ethernet and I can not connect to a network/internet from Kubuntu 7.04 (Feisty) but can from windows xp.

I have attached a file with some common requests to connection problems. I have just joined a university network and should be able to get the IP from the DHCP. I have tried manually configuring the connection but then it looses the default gateway and goes back to an old IP address (ie the 169.254.7.21. I used the numbers that were in windows for the gateway and even for the IP, but to no avail.

If anyone could help that would be great. I have only been using linux for the last few months, so be gentle please.

Thanks,
Somnus

---

### Post by noob12 on 2007-09-22
OK.  So, do you notice the "link: no" and "Link detected: no" in the lshw and ethtool outputs?  Well, that means you have no ethernet link established.  We need to resolve that before you will be able to make progress.   Everything depends on having link established.

I'm assuming you have an ethernet cable plugged into your host with an active port on the other side.

Are you dual booting this box?  If so, try this and see if it helps:   Shutdown the host cleanly and unplug it from the wall.  Wait 20 seconds.  Plug in, reboot.  See if you now have link detected at least.

If that doesn't work, can you post the output of **dmesg** and **tail /var/log/kern.log** after that boot.

---

### Post by Somnus07 on 2007-09-23
Hi, thanks for your help,

I am running dual boot.  Yes i would assume its an active port on the other side just connected to a gateway somewhere in this halls of residence, as i just have the telephone/ethernet ports in my room.

The shutdown didnt work, still link:no. Have added the output as zip.  Notepad cant read it properly so give me a shout if it isnt formatted in the right way.

---

### Post by noob12 on 2007-09-23
I'm assuming you didn't just shutdown but did the whole unplug ritual, which is important in this case.  Apply the full voodoo if you didn't before.  There's an explanation if it works.

I don't see a problem with the driver loading in your **dmesg** other than it saying that the link is down.     It used to be the case with some older versions of the kernel and this driver that you would have to reload it to get it to detect the link properly.  It's supposed to be fixed, but can you try to reload it as follows:

```

sudo ifdown eth0
sudo modprobe -r uli526x
sudo modprobe uli526x

```

Check if there is link detected using this command
```

sudo ethtool eth0

```
Look for the link detected line and see if it says "yes" now.

If so, run
```

sudo ifup eth0

```
and it should work.  

If not, more diagnostics will be needed.  

The same box is able to get a connection on this same port when booted WIndows XP, correct?

---

### Post by Somnus07 on 2007-09-23
Yes sorry i meant i did the whole ritual - i had read one of your previous posts where this worked for someone else, but no it doesnt seem to work here.  I did an ethtool eth0 afterwards and it still said no link.  I have posted the rest of the commands into the file.

I have had previous problems in which when i was back home i had a router set up and sometimes i had to restart the connection twice in knetwork manager to get it working - have tried that here but still no luck.  I guess those commands do pretty much the same thing if not a much thorough job.

And yes the same box connects to the same port, im not changing anything physical round.  Also i dont think the gateway has any problems with linux boxes as other people in the halls with them can get on fine.

Thanks again.

---

### Post by noob12 on 2007-09-23
This is still on the original tack of something to do with Windows leaving the adapter in a state that the linux driver isn't going to reenable it.   

While in Windows, can you navigate to your Network Connections, select your wired connection, then right-click on it and select Properties.  Click the Configure .. button next to the driver name.  Select the Advanced tab and see if there is any option related to Wake-on-LAN or Wake Up.  If there is a setting, check that it is set so that Wake-on-LAN remains enabled after shutting down.

Also, check your BIOS settings and see if there is anything controlling the initial state of the network device.

---

### Post by Somnus07 on 2007-09-23
There is nothing in windows on the properties related to Wake-on-LAN or Wake Up.  Only:
Connection Type: AutoSense
PME: ALL
Store And Forward: Enabled
Transmit Threshold: High

Also in the BIOS the only things i could see relating to the ethernet were:

Boot from network: disabled
onboard LAN: enabled

---

### Post by noob12 on 2007-09-23
I still don't see anything and I'm running out of ideas; do you mind posting **lsmod**  ?

---

### Post by Somnus07 on 2007-09-23
Hey here is the lsmod:

```
somnus@Cube:~$ lsmod
Module                  Size  Used by
ipv6                  268960  12
rfcomm                 40856  0
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0
cpufreq_conservative     8200  0
cpufreq_userspace       5408  0
cpufreq_powersave       2688  0
cpufreq_ondemand        9228  0
cpufreq_stats           7360  0
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
dev_acpi               12292  0
tc1100_wmi              8068  0
sony_acpi               6284  0
pcc_acpi               13184  0
video                  16388  0
sbs                    15652  0
ac                      6020  0
asus_acpi              17308  0
button                  8720  0
battery                10756  0
dock                   10268  0
container               5248  0
i2c_ec                  6016  1 sbs
backlight               7040  1 asus_acpi
nls_iso8859_1           5120  2
nls_cp437               6784  2
vfat                   14208  2
fat                    53916  1 vfat
lp                     12452  0
fuse                   46612  11
af_packet              23816  4
snd_intel8x0           34332  2
snd_ac97_codec         98464  1 snd_intel8x0
cx88_alsa              14600  1
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss
analog                 12832  0
snd_seq_midi            9600  0
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1
parport                36936  3 ppdev,lp,parport_pc
gameport               16520  1 analog
pcspkr                  4224  0
serio_raw               7940  0
psmouse                38920  0
tuner                  61864  0
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uli526x                17556  0
cx8800                 35212  0
compat_ioctl32          2304  1 cx8800
snd                    54020  17 snd_intel8x0,snd_ac97_codec,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  6656  0
soundcore               8672  1 snd
cx88xx                 67364  2 cx88_alsa,cx8800
ir_common              31236  1 cx88xx
i2c_algo_bit            8712  1 cx88xx
tveeprom               15888  1 cx88xx
i2c_ali1563             8708  0
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
videodev               28160  2 cx8800,cx88xx
v4l2_common            25216  3 tuner,cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev
video_buf              26116  3 cx88_alsa,cx8800,cx88xx
amd64_agp              13700  1
ali_agp                 8064  0
agpgart                35400  2 amd64_agp,ali_agp
btcx_risc               5896  3 cx88_alsa,cx8800,cx88xx
i2c_ali1535             8324  0
i2c_ali15x3             8964  0
i2c_core               22656  8 i2c_ec,tuner,cx88xx,i2c_algo_bit,tveeprom,i2c_ali1563,i2c_ali1535,i2c_ali15x3
shpchp                 34324  0
pci_hotplug            32576  1 shpchp
tsdev                   8768  0
evdev                  11008  5
ext3                  133128  1
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
usbhid                 26592  0
hid                    27392  1 usbhid
sg                     36252  0
sd_mod                 23428  12
usb_storage            72256  1
libusual               17936  1 usb_storage
ide_cd                 32672  0
cdrom                  37664  1 ide_cd
generic                 5124  0 [permanent]
floppy                 59524  0
sata_uli                8836  8
ehci_hcd               34188  0
ohci_hcd               22532  0
usbcore               134280  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
alim15x3               13196  0 [permanent]
ata_generic             9092  0
libata                125720  2 sata_uli,ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
thermal                14856  0
processor              31048  1 thermal
fan                     5636  0
fbcon                  42656  0
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0
capability              5896  0
commoncap               8192  1 capability
```

I think im just going to buy a new pci nic tomorrow and see if that works, as you said there have been prolems with this integrated one before, and to me this seems like the most likely answer.

---

### Post by noob12 on 2007-09-23
Yes.  Sorry.  I was hoping to see a dependency on a module that did report problems in your boot, but don't see it.  There are some (I think) unrelated issues in your boot from the smbbus support complaining about an out-of-date bios or the need to force an address.  I don't have any clue about how to address those.

Better help needed.

---

### Post by Somnus07 on 2007-09-24
Hey thanks for your help anyway.  I bought a pci nic (realtek8139) in the end and it seems to work fine. Finally managed to get rid of windows ;).
):P

---

