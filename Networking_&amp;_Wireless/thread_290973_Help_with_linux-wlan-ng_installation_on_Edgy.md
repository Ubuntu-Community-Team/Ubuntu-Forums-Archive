---
title: "Help with linux-wlan-ng installation on Edgy"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Rhadamanthus on 2006-11-01
I'm an absolute newbie to Ubuntu. That said, I have an A535 notebook (Walmart) that is the first of 5 computers that I'm switching to Ubuntu. Naturally it would give me problems.
I installed the linux-wlan-ng package from the Dapper disk without trouble. The Network Manager then (finally) recognized and enabled the "card". My wireless is built-in and uses the Airvast Prism3 wlan USB adapter (vendor 124a product 168b)
The problem is that the Network Manager says "go" and Firefox says "no".  What do I still need to do to make this wretch work?
 My /etc/network/interfaces file reads:

auto lo
iface to inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid SOHO


auto eth0

auto wlan0

Question: is there more I need to add? Here, elsewhere or both?
I have been fighting with this for several days and while my Windows skills are good, my Linux skills are pitiful (as yet).
Thanks for any help.  8)

Adding Info I located,  IWCONFIG

lo      no wireless extensions

eth0    no wireless extensions

wlan0   IEEE 802.11-DS  ESSID:"SOHO"  Nickname:"SOHO"
        Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0A:CB:3C:19:2B
        Bit Rate:2 Mb/s    Tx-Power:2346 dBm
        Retry min limit:8   RTS thr:off   Fragment thr:off
        Encryption key:off
        Link Quality:0  Signal level:0   Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0    no wireless extensions

                       IFCONFIG

eth0   Link encap:Ethernet   HWaddr 00:11:5B:2C:80:66
       UP BROADCAST MULTICAST   MTU:1500   Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 Carier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0b)  TX bytes:0 (0.0b)
       Interrupt:5 Base address:0xaf00

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr:  ::1/128 Scope:Host
       UP LOOPBACK RUNNING  MTU:16436  Metric:1
         (packets, collisions, bytes same as above)

wlan0   Link encap:Ethernet  HWaddr  00:0A:E9:04:19:2B
        inet6 addr: fe80::20a:e9ff:fe04:192b/64  Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0b)  TX bytes:10176 (9.9 KiB)

This is all the info that I have found so far, the problem is that I don't know what should be there and what should be added - and if these are the only places.  I really would appreciate it if someone who knows more then me could point me in a new (and hopefully right) direction.
           Thanxx

---

### Post by Rhadamanthus on 2006-11-16
Bump:-k

---

### Post by FrodoB on 2006-11-16
Have you tried to run dhclient at at terminal prompt?

sudo dhclient wlan0

What is the output?

Can you run:

sudo iwlist wlan0 scanning

What is the output?

---

### Post by Rhadamanthus on 2006-11-17
Here is dhclient wlan0 output:


Listening on LPF/wlan0/00:0a:e9:04:19:2b
Sending on   LPF/wlan0/00:0a:e9:04:19:2b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Here is iwlist wlan0 scanning output:

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:79:FF:10
                    ESSID:"LinksysR79ff10"
                    Mode:Master
                    Encryption key:off
                    Channel:6
                    Quality:13/92  Signal level:-76 dBm  Noise level:-89 dBm


I have no encryption or other security on the laptop since I live in the country about 1/2 mile from road and 2 miles from nearest neighbor.

---

### Post by FrodoB on 2006-11-17
> **Rhadamanthus said:**
> Here is dhclient wlan0 output:


Listening on LPF/wlan0/00:0a:e9:04:19:2b
Sending on   LPF/wlan0/00:0a:e9:04:19:2b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Here is iwlist wlan0 scanning output:

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:79:FF:10
                    ESSID:"LinksysR79ff10"
                    Mode:Master
                    Encryption key:off
                    Channel:6
                    Quality:13/92  Signal level:-76 dBm  Noise level:-89 dBm


I have no encryption or other security on the laptop since I live in the country about 1/2 mile from road and 2 miles from nearest neighbor.


Well your signal quality is bad, are you far from the access point? I don't know if you can connect to this or not, but you can try like this for starters, it it works then you can configure it the right way.

Cut the following script and paste it into the Text Editor and save it as test.sh and then use chmod, so the process will be:

$ chmod 755 test.sh


#!/bin/sh
/sbin/iwconfig wlan0 essid "LinksysR79ff10"
/sbin/iwconfig wlan0 mode "Managed"
#/sbin/iwconfig wlan0 rate 11M auto 
#/sbin/iwconfig wlan0 key "XXXXXXXXXXXXXXXXXXXXXXX"
#/sbin/iwconfig wlan0 key "s:XXXXXXXXXXXXX"
#/sbin/dhclient wlan0 


You probably already know, the "#" is the comment character for shell scripts. So all you need to try at first is to connect to your Access Point in managed mode. You iwlist says it has no security so it may connect, even though your signal is down in the mud.

With the script in your current directory just type:

$ ./test.sh

You should see nothing happen until you give an iwconfig command and it hopefully shows you access point name and the MAC identifier of your ap.

If you get that far you could uncomment the dhclient line and let it try to get an address. Please give us the output of iwconfig and iwlist after you have run the script.

---

### Post by Rhadamanthus on 2006-11-18
I copied script and saved it as ./test.sh then I ran chmod 755 test.sh and then ./test.sh both in terminal mode. I received:

Error for wireless request "Set ESSID"  (8B1A)  :
    SET failed on device wlan0 : Operation not permitted.
Error for wireless request "Set Mode"  (8B06)  :
    SET failed on device wlan0 : Operation not permitted.


I then ran iwconfig and got:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"SOHO"  Nickname:"SOHO"
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 02:0A:98:49:19:2B   
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I then ran iwlist and got:

Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event


I also don't know why I am getting such a low signal strength. When running under Windows I was getting a very strong reading from several rooms away; but now (in order to reply to you) I have the laptop sitting on the desk beside my main computer - about 3 feet (1 meter) away from the wireless router. It should be being blown off the desk.

---

### Post by Rhadamanthus on 2006-11-20
Bump

---

### Post by FrodoB on 2006-11-20
A long shot. Do an lsmod and see it you are somehow getting an orinoco_cs driver to also load. If so then blacklist it in

$ lsmod |more

$ sudo gedit /etc/modprobe.d/blacklist

---

### Post by Rhadamanthus on 2006-11-22
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  10 
powernow_k7             8872  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k7,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
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
lp                     12964  0 
af_packet              24584  4 
ieee80211              35272  0 
ieee80211_crypt         7552  1 ieee80211
joydev                 11200  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
prism2_usb             79236  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
evdev                  11392  1 
snd_timer              25348  1 snd_pcm
psmouse                41352  0 
pcspkr                  4352  0 
serio_raw               8452  0 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixe
r_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
r1000                  17792  0 
r8169                  32136  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
sis_agp                 9860  1 
agpgart                34888  1 sis_agp
i2c_sis96x              6660  0 
i2c_core               23424  2 i2c_ec,i2c_sis96x
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 prism2_usb,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
sis5513                15368  1 
generic                 5764  0 
thermal                15624  0 
processor              31560  2 powernow_k7,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability


Here is the lsmod. I don't see anything in it that would help.
BTW, Thank you for trying to help me and I hope I won't offend you by wishing you a Happy Thanksgiving to you and yours.

---

### Post by FrodoB on 2006-11-23
I did some investigation using a prism card today, you should not have had to install anything on Edgy to get it to work. 

I recommend a clean install of Edgy then report the outputs as you did earlier.

---

