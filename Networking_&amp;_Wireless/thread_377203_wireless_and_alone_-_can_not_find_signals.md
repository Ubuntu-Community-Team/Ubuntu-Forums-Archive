---
title: "wireless and alone - can not find signals"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by lala25 on 2007-03-05
Please help - I am trying to connect a toshiba 1400 series laptop with a cisco airnet 350 and can not find the signal.  I read another post and have captured some of the screen shots that were requested.  I don't know why the wireless card made two entries in my list (eth1 and wifi0).

here is the info I captured

bill@kitchen-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-110 dBm  Noise level=-110 dBm
          Rx invalid nwid:33226  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:129084   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-110 dBm  Noise level=-110 dBm
          Rx invalid nwid:33226  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:129084   Missed beacon:0

sit0      no wireless extensions.

bill@kitchen-laptop:~$ iwlist wifi0 scan
wifi0     No scan results
bill@kitchen-laptop:~$ iwlist eth1 scan
eth1      No scan results
bill@kitchen-laptop:~$ 


adTHANKSvance

---

### Post by chili555 on 2007-03-05
Please also let us see lsmod and lspci -vv | grep Network. Thanks.

---

### Post by lala25 on 2007-03-06
thanks for helping here is the requested information


bill@kitchen-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  8 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
toshiba_acpi           12224  0 
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
aes                    28864  1 
af_packet              24584  4 
airo_cs                 7552  1 
airo                   78496  1 airo_cs
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  1 airo_cs
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
floppy                 63044  0 
evdev                  11392  2 
smsc_ircc2             24732  0 
irda                  214332  1 smsc_ircc2
crc_ccitt               3200  1 irda
snd_ali5451            25356  1 
snd_ac97_codec         97696  1 snd_ali5451
snd_ac97_bus            3456  1 snd_ac97_codec
serio_raw               8452  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
psmouse                41352  0 
pcspkr                  4352  0 
yenta_socket           28812  4 
rsrc_nonstatic         15360  1 yenta_socket
e100                   38020  0 
ali_agp                 8320  1 
agpgart                34888  1 ali_agp
snd_pcm                84612  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_ali1535             7940  0 
i2c_ali15x3             8708  0 
pcmcia_core            43924  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
mii                     6912  1 e100
i2c_core               23424  3 i2c_ec,i2c_ali1535,i2c_ali15x3
snd                    58372  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  1 snd_pcm
usbhid                 45152  0 
ext3                  142728  1 
jbd                    62228  1 ext3
ohci_hcd               22532  0 
usbcore               134912  3 usbhid,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
generic                 5764  0 
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
bill@kitchen-laptop:~$ lspci -vv | grep Network
bill@kitchen-laptop:~$

---

### Post by chili555 on 2007-03-06
I saw this: [http://www.linuxquestions.org/questions/showthread.php?t=473822&highlight=aironet](http://www.linuxquestions.org/questions/showthread.php?t=473822&highlight=aironet) which suggested the problem was the bitrate being specified at 11 Mb/s. Please try sudo iwconfig eth1 rate auto followed by sudo iwconfig essid any and then followed by sudo ifup eth1.

---

### Post by lala25 on 2007-03-06
> **chili555 said:**
>  Please try sudo iwconfig eth1 rate auto followed by sudo iwconfig essid any and then followed by sudo ifup eth1.

I tried the first command and it prompted me for my password, after that I tried the second one.  it said unrecognized wireless request "any".  I then went back and did a iwconfig and noticed the bit rate did not change from 11 to auto.  Don't know why.

---

### Post by chili555 on 2007-03-06
Sorry about that. sudo iwconfig **eth1** essid any. I promise to prooooofreed myselv betrr from nwo on.

After you do these three commands in sequence, what is the outcome?

---

### Post by lala25 on 2007-03-06
ok here is what happened
for command iwconfig eth1 rate auto - no change to bit rate
for command iwconfig eth1 essid any - essid is now blank
for command ifup eth1 - message "interface eth1 already configured"

---

### Post by chili555 on 2007-03-06
OK, we are getting closer.

Let's try sudo iwconfig eth1 rate auto; sudo iwconfig eth1 essid any; sudo dhclient eth1. 

I am a bit puzzled by the existence of *both* eth1 and wifi0. You might try these commands with wifi0, as well, to see if you connect.

Also, I wonder if your scan works now after these commands: sudo iwlist eth1 scan and sudo iwlist wifi0 scan.

---

### Post by lala25 on 2007-03-06
[COLOR="Blue"]here is the output from the commands for eth1 and wifi0 and then a iwconfig.  after that I have included the scan results[/COLOR]

bill@kitchen-laptop:~$ sudo iwconfig eth1 rate auto; sudo iwconfig eth1 essid any; sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0d:bc:63:00:fc
Sending on   LPF/eth1/00:0d:bc:63:00:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@kitchen-laptop:~$ sudo iwconfig wifi0 rate auto; sudo iwconfig wifi0 essid any; sudo dhclient wifi0
There is already a pid file /var/run/dhclient.pid with pid 16660
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@kitchen-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0/100  Signal level:-110 dBm  Noise level:-86 dBm
          Rx invalid nwid:3289  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13727   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0/100  Signal level:-110 dBm  Noise level:-86 dBm
          Rx invalid nwid:3289  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13727   Missed beacon:0

sit0      no wireless extensions.

[COLOR="blue"]And now for the scan results[/COLOR]

bill@kitchen-laptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:15:C7:AB:99:10
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/100  Signal level=-68 dBm  Noise level:-110 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s

bill@kitchen-laptop:~$ sudo iwlist wifi0 scan
wifi0     Scan completed :
          Cell 01 - Address: 00:15:C7:AB:99:10
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/100  Signal level=-65 dBm  Noise level:-110 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s

---

### Post by chili555 on 2007-03-06
Ah ha! We can see the access point we want to connect to, and it says 'Encryption key: on'. Now we are getting *real* close. Please do sudo iwconfig eth1 key <your_wireless_key> followed by sudo dhclient eth1. We do not want the passphrase, we want the alphanumeric key, something like this: 93c8530b2df51711bad5596f91. Check the administration pages in your router if you need to find the key.

---

### Post by lala25 on 2007-03-07
[COLOR="Blue"]OK, I am getting excited.  I ran the two commands you provided me and for my key passed it the wep key that is for my system.  this is a 128 bit hex key.  Please see below.[/COLOR]

bill@kitchen-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0d:bc:63:00:fc
Sending on   LPF/eth1/00:0d:bc:63:00:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@kitchen-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5508
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:0d:bc:63:00:fc
Sending on   LPF/eth1/00:0d:bc:63:00:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
bill@kitchen-laptop:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:14:6C:3E:A2:52
                    ESSID:"Beatty"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/100  Signal level=-77 dBm  Noise level:-110 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
          Cell 02 - Address: 00:13:10:88:D8:01
                    ESSID:"baker"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=99/100  Signal level=-46 dBm  Noise level:-110 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s

bill@kitchen-laptop:~$ 


[COLOR="blue"]I see my router and my neighbor's router.  One thing that is confusing to me is when I go into the menu "[/COLOR][COLOR="Red"]System - Administration - networking[/COLOR][COLOR="blue"]" I don't get the essid's shown above in the drop down. Could this be part of the problem?  Since I am know away from those routers I may not be able to try suggestions quickly (I do have the laptop).  Thanks for all of your help so far.[/COLOR]

---

### Post by chili555 on 2007-03-07
The ESSID's are certainly one of the essential elements. I guess I'm a bit confused. When you scanned a few posts ago, the ESSID was "" indicating no ESSID's were being broadcast. Now we have Beatty and baker!

Let's sudo gedit /etc/network/interfaces and make *both* eth1 and wifi0 look like this:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
``` Save and close. Of course, substitute your details. Restart networking sudo /etc/init.d/networking restart and let us know.

---

### Post by lala25 on 2007-03-08
I am now connected, Thank you for your help.  I am unclear why the essid's still do not show up in the user interface, but it is not a big deal.

---

