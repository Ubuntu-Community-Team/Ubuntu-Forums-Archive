---
title: "Acer Aspire can't see my wireless card."
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by lorgonjortle on 2008-06-04
Ok, I have an Acer Aspire 5100... I am brand new to Linux, and don't know much, so if you give me some commands, please tell me exactly what I need to type. 
These are me ethernet devices:
Atheros AR5007EG Wireless network adapter, and Realtek RTL8139/810x Family Fast Ethernet NIC
'iwconfig' reported:
```

lo   no wireless extensions.

eth0 no wireless extensions.


```

'lsmod' reported:
```

Module                  Size  Used by

ipv6                  317192  10 

nls_iso8859_1           6528  0 

nls_cp437               8192  0 

vfat                   16128  0 

fat                    60208  1 vfat

usb_storage            81728  0 

libusual               22824  1 usb_storage

rfcomm                 47656  2 

l2cap                  28672  11 rfcomm

bluetooth              63876  4 rfcomm,l2cap

ppdev                  11272  0 

powernow_k8            16608  1 

cpufreq_conservative     9608  0 

cpufreq_powersave       3072  0 

cpufreq_ondemand       10896  1 

cpufreq_stats           8160  0 

freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats

cpufreq_userspace       6048  0 

battery                12424  0 

ac                      7304  0 

sbs                    21520  0 

video                  21140  0 

container               6400  0 

dock                   12264  0 

button                 10400  0 

parport_pc             41896  0 

lp                     15048  0 

parport                44172  3 ppdev,parport_pc,lp

joydev                 13440  0 

snd_hda_intel         337192  1 

snd_pcm_oss            50048  0 

snd_mixer_oss          20096  1 snd_pcm_oss

pcmcia                 46232  0 

snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss

snd_seq_dummy           5380  0 

snd_seq_oss            36864  0 

snd_seq_midi           11008  0 

snd_rawmidi            29824  1 snd_seq_midi

snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi

snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              27272  2 snd_pcm,snd_seq

snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

yenta_socket           30220  1 

pcspkr                  4608  0 

rsrc_nonstatic         14208  1 yenta_socket

sdhci                  21004  0 

pcmcia_core            46628  3 pcmcia,yenta_socket,rsrc_nonstatic

serio_raw               9092  0 

k8temp                  7680  0 

mmc_core               33416  1 sdhci

ath_pci               105392  0 

psmouse                45596  0 

snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore              10272  1 snd

snd_page_alloc         12560  2 snd_hda_intel,snd_pcm

i2c_piix4              11020  0 

wlan                  225736  1 ath_pci

i2c_core               30208  1 i2c_piix4

ath_hal               219888  1 ath_pci

shpchp                 38300  0 

pci_hotplug            36612  1 shpchp

evdev                  13056  6 

ext3                  146576  1 

jbd                    69360  1 ext3

mbcache                11272  1 ext3

sg                     41384  0 

sd_mod                 32512  3 

ide_cd                 35488  0 

cdrom                  41768  1 ide_cd

8139too                31232  0 

sata_sil               14600  2 

atiixp                  7824  0 [permanent]

ide_core              141200  3 usb_storage,ide_cd,atiixp

8139cp                 28032  0 

mii                     7424  2 8139too,8139cp

ata_generic             9988  0 

libata                138928  2 sata_sil,ata_generic

scsi_mod              172856  4 usb_storage,sg,sd_mod,libata

ehci_hcd               40076  0 

ohci_hcd               25092  0 

usbcore               161584  5 usb_storage,libusual,ehci_hcd,ohci_hcd

thermal                16528  0 

processor              36232  2 powernow_k8,thermal

fan                     6920  0 

fuse                   52528  1 

apparmor               47008  0 

commoncap               9472  1 apparmor


```

I haven't installed any drivers... I don't know where to go. I feel completely helpless right now, because I took off Windowz and I am borrowing a computer right now just to type this... What do I need to do to connect to my wireless internet? In Windowz, it just recognized it and I connected. When I go into System>>Network it only shows modem and plug-in. There is no wireless option...If someone could help me with this, I would greatly appriciate it, since my laptop is really the only computer I can use... and I need internet. 
Thanks for anything.

---

### Post by Coffeeman51 on 2008-06-04
I have an Acer Aspire 5520 and this thread gives detailed instructions on how to get the atheros card working...

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

Hope it helps...

---

### Post by lorgonjortle on 2008-06-06
Ughh.. I went through all of the steps and all it did was waste time and make me not able to open the Network manager anymore. I had to re-install Ubuntu, because I have no clue how to fix things. Will some one just tell me what to do, plain and simple? Not just give me these instructions that aren't meant for my wireless card(Atheros AR5007EG Wireless network adapter, and Realtek RTL8139/810x Family Fast Ethernet NIC) or even my version of Ubuntu (Gusty Gibbon). Thanks for the try, but that didn't work.:confused:

---

### Post by Naif.1 on 2008-06-06
Hope to find the sloution, I am having the same problem.


Thanks.

---

### Post by manis on 2008-06-07
Never give up. Because I took one week to setup, configure/install Antheros AR5007EG in toshiba notebook L200-N402. Now I can surfing using wireless connection on ubuntu 7.10.tk

---

### Post by lorgonjortle on 2008-06-07
To Manis:
How did you do it? We have the same exact card and distro... do you remember how?

---

### Post by manis on 2008-06-08
Dear Longonjortle,

I glad to help you. 

2. A few thing to consider a) my notebook is Toshiba L200-N402. In windows XP this card ( Antheros) said it was AR5007EG, but Ubuntu read it as AR5006EG.

3. At first I installed and UPGRADE Ubuntu 7.10. This upgrade is important because if you ugrade afTER your install madwifi driver,the wireless connection is dead( cannt make a connection)

4. Download madwifi driver at [http://madwifi.org/tickets/1679](http://madwifi.org/tickets/1679)
- look for already patch file, ( madwifi-nr-r3366-ar5007)
5. complier this ..but before this you must install build-essential. 
   - a command line type #sudo apt-get install build-essential
6 After finish make sure you add module using this command #sudo modprobe ath_pci
  - you can see this module load using this command; #sudo cat /etc/modules
  - if not open the /etc/modules and add ath_pci ( small cap pls)
  # sudo gedit /etc/modules

6 someone (in this forum) suggest to uncheck Antheros Hal Abstraction Layer ( HAL) - but in my case I do not uncheck this HAL.

7. restart the machine and pull out RJ45 Cable ( wired connection), After this the rm-applet will search/attemting to connect to the wireless Acess Point.
8 Try ping the router or acess point and also to your DNS server ( given by your Internet service provider (ISP)

9  And, hope your problem is oke now. Let me know.
see you again
thanks

---

### Post by lorgonjortle on 2008-06-08
Thanks everyone for their help. I found a solution. If you would like to see it, I'll post it here:
```

sudo aptitude update && sudo aptitude -y install build-essential linux-headers-$(uname -r)
cd ~
wget -O driver.tar.gz http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz
tar xf driver.tar.gz
cd madwifi-*
make
sudo make install
echo ath_pci | sudo tee -a /etc/modules
sudo modprobe ath_pci

```

After trying several other things without success, this did a treat the first time. Goodluck to anyone out there with this same card. I hope I could help.

---

### Post by manis on 2008-06-08
To L,

did you get wireless conection now?
:)

---

### Post by lorgonjortle on 2008-06-08
Yep, but I ran into an even bigger problem (In my opinion). My wireless is all fine and dandy, and I was trying to set up desktop effects (Compiz check came out peachy), and I must have done something wrong, but I rebooted, since I had just installed 211 updates, and when I logged back on, my rez is like 600x400 or something, and I can't change it back... then my screen started fuzzing up and everything went triple vision on me. I rebooted, and there is no more triple, but the rez is really low and it is stuck there and I still don't have desktop effects.... Bummer.

---

### Post by manis on 2008-06-08
My Dear,
Congrat because your can using wifi now. Your new problem can be solve by 

1. choose recover mode in ubuntu ( in boot menu)

2. on terminal : sudo dpkg-reconfigure xserver-xorg and your system will be to normal ( hopefully)

3. pls inform me if you can solve this problem

---

### Post by lorgonjortle on 2008-06-08
Manis, thank you so much for that one! Worked like a charm.

---

