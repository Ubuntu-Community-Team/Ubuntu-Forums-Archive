---
title: "new madwifi version problem"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by aantoon on 2007-06-20
I did a new install ubuntu 6.06 the outcome of lspci gave me 
"0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)" 
my wifi card was not working. after that i tryed the new drivers for atheros using script [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html) still....lspci gave me the same "unknown device. i'm stuck here, what must i do?? below are the outcome of lspci, print from script, iwconfig, ifconfig and lsmod

root@pc1:/home/pc1# lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
0000:00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 0c)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
*****************************************************************************************************
root@pc1:/home/pc1# lsmod
Module                  Size  Used by
af_packet              22920  2
ipv6                  265856  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
nvram                   9224  1
uinput                  9088  1
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_iso8859_1           4224  3
nls_cp437               5888  3
vfat                   13440  3
fat                    53020  1 vfat
ext2                   68488  1
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
tsdev                   8000  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
floppy                 62148  0
pcspkr                  2180  0
snd_via82xx            28824  1
gameport               15496  1 snd_via82xx
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via686a                17672  0
psmouse                36100  0
i2c_isa                 4992  1 via686a
rtc                    13492  0
serio_raw               7300  0
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
i2c_viapro              8980  0
e100                   40580  0
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
nvidia               4551028  0
soundcore              10208  1 snd
i2c_core               21904  5 i2c_acpi_ec,via686a,i2c_isa,i2c_viapro,nvidia
mii                     5888  1 e100
wlan                  144924  3 ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
via_agp                 9856  1
agpgart                34888  2 nvidia,via_agp
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
evdev                   9856  2
ext3                  135944  2
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33808  0
usbcore               130820  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  9
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
root@pc1:/home/pc1#
*****************************************************************************************************
root@pc1:/home/pc1# ifconfig
ath0      Link encap:Ethernet  HWaddr 00:13:F7:XX:XX:XX
          inet addr:10.0.0.16  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:f7ff:fe12:3e5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4242 errors:55277 dropped:0 overruns:0 frame:55277
          TX packets:3951 errors:117 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:4239998 (4.0 MiB)  TX bytes:623154 (608.5 KiB)
          Interrupt:177 Memory:e8980000-e8990000

eth0      Link encap:Ethernet  HWaddr 00:02:55:1E:41:3B
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2850 (2.7 KiB)  TX bytes:2850 (2.7 KiB)
*****************************************************************************************************
root@pc1:/home/pc1# iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SpeedTouchXXXXXX"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:14:93:15
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
          Rx invalid nwid:7970  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:117  Invalid misc:117   Missed beacon:50

eth0      no wireless extensions.

sit0      no wireless extensions.
*****************************************************************************************************
#the used script
#!/bin/sh

# This script will install the madwifi drivers for Atheros cards.
# The script must be run in a root terminal with 755 permission

# Install essential tools
sudo apt-get -y install build-essential bin86

# Install the sharutils package
sudo apt-get -y install sharutils

# Change to the /usr/src folder
cd /usr/src

# Get the necessary drivers from [www.stchman.com](www.stchman.com)
sudo wget [http://www.stchman.com/tools/madwifi-0.9.3.1.tar.gz](http://www.stchman.com/tools/madwifi-0.9.3.1.tar.gz)

# unpack the tarball
sudo tar -xzf /usr/src/madwifi-0.9.3.1.tar.gz

# Change to the folder that the tarball created
cd /usr/src/madwifi-0.9.3.1

# Make the drivers
sudo make clean
sudo make
sudo make install

# Make backup of /etc/modules file
sudo cp /etc/modules /etc/modules.bak

# Append to the end of the /etc/modules file by using >>
# First insert a carriage return in to the /etc/modules file
sudo echo -e '\n' >> /etc/modules
sudo echo "ath_pci" >> /etc/modules

# Enable WEP, WPA. WPA2 via network manager
# Install wpa supplicant
sudo apt-get -y install wpasupplicant

# Install Network Manager (this will allow you to see all available wireless networks)
sudo apt-get -y install network-manager-gnome network-manager

# Make backup of the /etc/network/interfaces file
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

# Make new /etc/network/interfaces file with just "lo" entry in it.
# The single > will create a new file, >> appends to a file
sudo echo "# The loopback network interface" > /etc/network/interfaces
sudo echo "auto lo" >> /etc/network/interfaces
sudo echo "iface lo inet loopback" >> /etc/network/interfaces

# Create a file called /etc/default/wpasupplicant
# This file does not exist, but the > command will create it
sudo echo "ENABLED=0" > /etc/default/wpasupplicant

sudo touch /etc/default/wpasupplicant

# Reboot the machine, wireless should now be enabled!!!!
sudo reboot
*****************************************************************************************************

---

### Post by conjur3r on 2007-06-20
What's the matter?  According to the ifconfig, it looks like your wireless is recognised ok.  It even has networking configuration too.  What exactly doesn't work?

---

### Post by aantoon on 2007-06-20
well it keeps disconnecting to the ap evry 3min or so, also the signal strength go up and down and do not represent realety in that matter.

---

### Post by aantoon on 2007-06-20
forgot to metion my shipset is ar2413a.......hope this helps to solve my problem

---

