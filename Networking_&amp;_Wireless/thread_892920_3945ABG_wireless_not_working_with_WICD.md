---
title: "3945ABG wireless not working with WICD"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by rocklee on 2008-08-17
So wireless was working every now and then with the default ndiswrapper and the 3945 wireless card in my notebook, but works perfectly in Vista.

After installing WICD, wireless no longer works in Ubuntu.

It sees the wireless networks but cannot connect with the settings I have in Vista.  Encryption types, pass keys are all the same but cannot connect to my network.

---

### Post by rocklee on 2008-08-17
Anyone?

---

### Post by imdano on 2008-08-17
3945 has a native driver that works really well in most cases.  Why are you using ndiswrapper?  Can you connect to networks without encryption?

---

### Post by rocklee on 2008-08-18
I resorted to using ndiswrapper because I couldn't get the 3945ABG driver to work.  The ndiswrapper driver actually came from my previous setup on a different notebook as it seems to be a universal wireless driver that works.

Basically, I can see my wireless network but I can't connect to it.  I've read that network manager might be interfering with WICD, should I disable that?  

I am also using thinkfinger for my fingerprint reader, does that have any effect on wicd?

All of this is confusing me.  I got Gutsy working before on my older notebook (wireless and ATI card with compiz) so I have some ubuntu experiences but this one really baffles me.

---

### Post by cpetercarter on 2008-08-18
I am not sure that you need ndiswrapper. But you do need the linux-backports-modules-hardy-generic package. Have a look at [http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/]("http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/")

---

### Post by rocklee on 2008-08-18
Hi I got it to work.

Ndiswrapper didn't work for me either so I tried 3945 again (very troublesome). I couldn't even see my networks anymore.  

The wireless was disabled and I had no idea how to enable it.

Basically I had to play around with a few things including the ubuntu network settings because I thought wicd will do all that.  Enable wireless and ethernet so that it will update itself.

Here's the output before it worked :

> rock@rock-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:56:15:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:7e:9a:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
rock@rock-laptop:~$ 

==============================================================================

rock@rock-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:56:15:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2491 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:127486 (124.4 KB)  TX bytes:127486 (124.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:7e:9a:fe  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10563 (10.3 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:7e:9a:fe  
          inet addr:169.254.9.112  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-7E-9A-FE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

==============================================================================

rock@rock-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"clarendon"  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:0F:3D:B8:DA:34   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

==============================================================================

rock@rock-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4992  2 
nls_cp437               6656  2 
vfat                   14464  2 
fat                    54556  1 vfat
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_ondemand        9740  1 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5284  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
ipv6                  267780  10 
arc4                    2944  2 
ecb                     4480  2 
blkcipher               8324  1 ecb
iwl3945                93940  0 
iwlwifi_mac80211      219108  1 iwl3945
cfg80211               15112  1 iwlwifi_mac80211
led_class               6020  1 iwl3945
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
uinput                 10240  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
af_packet              23812  4 
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
mmc_block              14980  2 
snd_seq_oss            35584  0 
joydev                 13120  0 
snd_seq_midi            9376  0 
uvcvideo               58116  0 
snd_rawmidi            25760  1 snd_seq_midi
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
v4l1_compat            15492  2 uvcvideo,videodev
nvidia               7106084  26 
v4l2_common            18304  2 uvcvideo,videodev
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core               24832  1 nvidia
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  19076  0 
ndiswrapper           192920  0 
sky2                   47492  0 
video                  19856  14 
output                  4736  1 video
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               51460  2 mmc_block,sdhci
serio_raw               7940  0 
wmi_acer                9644  0 
battery                14212  0 
iTCO_wdt               13092  0 
ac                      6916  0 
evdev                  13056  6 
intel_agp              25492  0 
button                  9232  0 
iTCO_vendor_support     4868  1 iTCO_wdt
soundcore               8800  1 snd
agpgart                34760  2 nvidia,intel_agp
dcdbas                  9504  0 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
psmouse                40336  0 
pcspkr                  4224  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_piix               19588  0 
sg                     36880  0 
ata_generic             8324  0 
sd_mod                 30720  4 
usb_storage            73664  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
libusual               19108  1 usb_storage
pata_acpi               8320  0 
ahci                   28420  3 
ohci1394               33584  0 
libata                159344  4 ata_piix,ata_generic,pata_acpi,ahci
scsi_mod              151436  6 sbp2,sr_mod,sg,sd_mod,usb_storage,libata
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  8 uvcvideo,ndiswrapper,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  5 
rock@rock-laptop:~$ 

==============================================================================


But it still wouldn't connect.

Here's the result that I got from wicd :

> Obtaining IP address...connecting....<no results>


I tried the linux-backports-modules-hardy-generic package which I have tried many times as a random attempt and then reboot and it worked.

Now because I was changing a lot of things, I can't even remember how I got it to work which isn't really useful to anyone unfortunately.  None of the guidelines that I found on ubuntu and on the net were that useful either.  


All I can say is :

- uninstall networkmanager (if it is installed)
- install wicd
- make sure that you can see your wireless settings in network settings and enable it

- do these :

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945

- and these :

sudo apt-get install linux-backports-modules-hardy-generic
reboot

And for some reason wicd will connect to my network.

Is there a way for me to backup my settings (or create an image of my linux partition so that I can play around with the settings again and revert back to the working configuration again?

I know a lot of people have this problem of getting the intel 3945 driver to work on the XPS 1530, it would be good to finally have a walkthrough to resolve it.

---

### Post by rocklee on 2008-08-18
Ah crap its been disabled again after I rebooted it.

---

### Post by rocklee on 2008-08-18
OK so Ubuntu works after booting up in Vista and rebooting again.

Hmm....something is not sticking or Vista is doing something magical to my wireless settings?

---

