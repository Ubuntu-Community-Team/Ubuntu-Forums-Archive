---
title: "Iwconfig settings offbase?"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by Jeff D on 2007-01-24
Hi was curious to know if these settings are normal or do they look way off.  The card is a prism 2.5 mini-pci running the orinoco_pci driver.  Is it possible there is a conflict going on?

blitzoid@blitzoid-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"eNF"  Nickname:"eNF"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:E0:5F:99   
          Bit Rate=11 Mb/s   Sensitivity:1/3  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=92/92  Signal level=5/153  Noise level=114/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:234  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by phossal on 2007-01-24
Are you connected to the router and the Internet?

---

### Post by Jeff D on 2007-01-24
> **phossal said:**
> Are you connected to the router and the Internet?

  Thanks for the reply and sorry for the lack of info as I wasn't thinking to clearly at 5am this morning after work  :)   I am connected to the net via a router which was working flawlessly.  Here is the output of lsmod.  I might be mistaken but it seems i have both the orinoco and hostap drivers loading...

```
blitzoid@blitzoid-laptop:~$ lsmod
Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
radeon                118816  2 
drm                    74644  3 radeon
speedstep_lib           5764  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ipv6                  272288  10 
nls_utf8                3200  1 
ntfs                  112116  1 
af_packet              24584  2 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
lp                     12964  0 
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  0 
snd_ali5451            25356  1 
snd_ac97_codec         97696  1 snd_ali5451
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_pcm                84612  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
parport_pc             37796  1 
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                41352  0 
serio_raw               8452  0 
floppy                 63044  0 
evdev                  11392  2 
parport                39496  2 lp,parport_pc
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
hostap_pci             59152  0 
hostap                123012  1 hostap_pci
snd                    58372  12 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
ieee80211_crypt         7552  1 hostap
snd_page_alloc         11400  1 snd_pcm
prism2_pci             74752  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
i2c_ali1535             7940  0 
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_ali15x3             8708  0 
orinoco_pci             8320  0 
orinoco                45076  1 orinoco_pci
hermes                  9472  2 orinoco_pci,orinoco
natsemi                30688  0 
ati_agp                10636  1 
agpgart                34888  2 drm,ati_agp
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
usbhid                 45152  0 
ext3                  142728  1 
jbd                    62228  1 ext3
uhci_hcd               24968  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
usbcore               134912  4 usbhid,uhci_hcd,ehci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  4 
generic                 6276  0 
alim15x3               13324  0 [permanent]
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

```

  Here is also the ifconfig if that helps...


```
blitzoid@blitzoid-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:01:24:D0:AA:A1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:24ff:fed0:aaa1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10741 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6189 errors:229 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6902807 (6.5 MiB)  TX bytes:1307930 (1.2 MiB)
          Interrupt:10 Memory:d000a000-d000afff
```

  Thanks again for any help!!!

---

### Post by phossal on 2007-01-24
I might be naive, but I'm very easy to persuade with the argument that if it works *well enough* I shouldn't try to fix it. 

You can always blacklist drivers if you feel it's really using both. I suspect that isn't true. Your output to iwconfig appears okay to me.

---

### Post by Jeff D on 2007-01-24
> **phossal said:**
> I might be naive, but I'm very easy to persuade with the argument that if it works *well enough* I shouldn't try to fix it. 

You can always blacklist drivers if you feel it's really using both. I suspect that isn't true. Your output to iwconfig appears okay to me.

  Ok I was just a little concerned about the Signal Level 5/153 which seems low and the fact that it seemed multiple drivers were being loaded which might in turn affect the performance.  Would it be better to blacklist the orinoco drivers or the hostap drivers for my Prism 2.5 mini-pci?  Thanks for your prompt reply!

---

### Post by phossal on 2007-01-24
Man, Jeff, I don't know. I actually wrote a fairly well regarded tutorial on installing the wireless component I use, the Netgear wg111v2.  It had a horrible reputation for requiring a lot of voodoo, and was reported to work only about 50% of the time. It took a lot of work to sort out the good information from the bad. 

I don't want to contribute to such a reputation for your hardware. I suggest searching the forums, google, yahoo, and other sites for as much information as you can find about your hardware. Only then will you be able to make a good decision for yourself. I wish I could help more.

Out of curiosity, is your impression that your hardware is under-performing?

---

### Post by Jeff D on 2007-01-24
> **phossal said:**
> Man, Jeff, I don't know. I actually wrote a fairly well regarded tutorial on installing the wireless component I use, the Netgear wg111v2.  It had a horrible reputation for requiring a lot of voodoo, and was reported to work only about 50% of the time. It took a lot of work to sort out the good information from the bad. 

I don't want to contribute to such a reputation for your hardware. I suggest searching the forums, google, yahoo, and other sites for as much information as you can find about your hardware. Only then will you be able to make a good decision for yourself. I wish I could help more.

Out of curiosity, is your impression that your hardware is under-performing?

 My card seems to be great at times and other times not so great.  I have did quite a bit of googling on my card and the adherant problems with it.  Maybe I'm just expecting too much lol.  I can connect to the net, usually get good receive rates and can load it into in monitor mode when the need arises.  Anyhow I'll keep plugging away to search for ways to improve and take your advice and do some more searching around.  Thanks for your time...It really is appreciated.  Without people like you I would have reverted back to windows a while ago and my g/f and parents wouldn't have gnome running on their puters lol.

  Cheers,

  Jeff D.

---

