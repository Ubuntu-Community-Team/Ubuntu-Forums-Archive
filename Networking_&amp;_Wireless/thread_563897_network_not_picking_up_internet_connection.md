---
title: "network not picking up internet connection"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by clinto on 2007-09-30
I'm not very fluid with networking but I've been trying to learn the basics within the last month or so.

Here's the deal:
[LIST]
I have a machine housing both XP and Ubuntu.
I'm using a wired connection.
My networking goes: Verizon DSL(via rj-11) > DSL modem > Linksys WRT54G router > pc.
My DSL modem is at 192.168.1.1.
My Linksys router is at 192.168.3.1.
[/LIST]

I was using DHCP on both ends, but decided to use Static IP on both the Linksys router and pc. I was able to get XP to connect to the internet using 192.168.3.136. I figured I could use the same Static IP address with Ubuntu, went into the GUI and entered Static IP=192.168.3.136, Subnet Mask=225.255.255.0, and Gateway 192.168.1.1. Didn't work.

So I opened up the /etc/network/interfaces file and took a peek and saw this:
```

abnerdoon@koenigdesk:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.3.137
netmask 255.255.255.0
gateway 192.168.1.1




auto eth0


```

I'm not sure why it was out of order like that, so I put the "auto eht0" above the "iface eth0 inet static" and tried it, but it still did nothing.

Then I realized that the default gateway was set differently than it was set in Windows. So I changed it from 192.168.1.1 to 192.068.3.1. I restarted my pc and it still didn't work.

At that point, I gave up and tried setting my interfaces file back to the way it was and set it back to DHCP. Restarted and surprise, surprise, it didn't work. I'm not sure what could be different now, what I could have changed. It's probably some other network setting in the background that was changed when I altered the other settings.

Here's some other info:
--------------------------

abnerdoon@koenigdesk:~$ lspci | grep -i net
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)

abnerdoon@koenigdesk:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2688  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
ac                      6020  0 
button                  8720  0 
video                  16388  0 
container               5248  0 
sbs                    15652  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
battery                10756  0 
i2c_ec                  6016  1 sbs
af_packet              23816  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14208  1 
fat                    53916  1 vfat
nls_utf8                3072  1 
ntfs                  107764  1 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
serio_raw               7940  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
usblp                  14848  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
sis_agp                 9604  1 
agpgart                35400  1 sis_agp
i2c_sis96x              6532  0 
i2c_core               22656  2 i2c_ec,i2c_sis96x
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
ipv6                  268960  12 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  6 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  11 
pata_sis               14732  0 
ata_generic             9092  0 
libata                125720  2 pata_sis,ata_generic
scsi_mod              142348  1 libata
generic                 5124  0 [permanent]
floppy                 59524  0 
sis900                 24704  0 
mii                     6528  1 sis900
ehci_hcd               34188  0 
ohci_hcd               22532  0 
usbcore               134280  5 usbhid,usblp,ehci_hcd,ohci_hcd
sis5513                14856  0 [permanent]
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

abnerdoon@koenigdesk:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:A2:CE:73  
          inet addr:192.168.3.137  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::201:6cff:fea2:ce73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180 (180.0 b)  TX bytes:7998 (7.8 KiB)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5154 (5.0 KiB)  TX bytes:5154 (5.0 KiB)

---

### Post by noob12 on 2007-09-30
I'm not sure if this is a typo in your posting or you got it wrong when you set it but you said
> 
So I changed it from 192.168.1.1 to 192.068.3.1. I restarted my pc

You should have set it to 192.168.3.1 (not 068).

Two things that might help diagnosis:

From windows when you have networking working, post the output of the command **ipconfig /all** and **route print**

From Ubuntu, post the output of **route -n** and also make sure you can ping your router **ping 192.168.3.1**.

---

### Post by clinto on 2007-09-30
> **noob12 said:**
> I'm not sure if this is a typo in your posting or you got it wrong when you set it but you said

You should have set it to 192.168.3.1 (not 068).
Oh geez, yeah, I can't believe I missed that. Sorry. It was a typo.

Here's my output from the Windows shell:

```


C:\Documents and Settings\debi>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : PREFERRE-28FCCC
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Mixed
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Verizon DSL:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : SiS 900-Based PCI Fast Ethernet Adap
ter
        Physical Address. . . . . . . . . : 00-01-6C-A2-CE-73
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.3.136
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.3.1
        DNS Servers . . . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\debi>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 01 6c a2 ce 73 ...... SiS 900-Based PCI Fast Ethernet Adapter - Packet
 Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.3.1   192.168.3.136       20
    91.189.94.186  255.255.255.255      192.168.3.1   192.168.3.136       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.3.0    255.255.255.0    192.168.3.136   192.168.3.136       20
    192.168.3.136  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.3.255  255.255.255.255    192.168.3.136   192.168.3.136       20
        224.0.0.0        240.0.0.0    192.168.3.136   192.168.3.136       20
  255.255.255.255  255.255.255.255    192.168.3.136   192.168.3.136       1
Default Gateway:       192.168.3.1
===========================================================================
Persistent Routes:
  None


```

---

### Post by noob12 on 2007-09-30
OK.  Try the same settings in Ubuntu using **System | Administration | Network**.  (Check that you type the address and gateway correctly.) You can also configure your DNS server there in the DNS tab to be **192.168.1.1** .

Make sure you can ping your local router: **ping 192.168.3.1**
If this doesn't work you have a more fundamental problem.

Then try to ping an external point by ip address: **ping 72.14.253.99**
If this works your connectivity is working.

Then try by name: **ping [www.google.com](www.google.com)**
If only this last thing doesn't work.  We just need to fix up your DNS settings.

---

### Post by clinto on 2007-09-30
Yeah, it must just be the DNS settings then.

```

abnerdoon@koenigdesk:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 eth0
abnerdoon@koenigdesk:~$ ping 192.168.3.1
PING 192.168.3.1 (192.168.3.1) 56(84) bytes of data.
64 bytes from 192.168.3.1: icmp_seq=1 ttl=64 time=7.43 ms
64 bytes from 192.168.3.1: icmp_seq=2 ttl=64 time=1.09 ms
64 bytes from 192.168.3.1: icmp_seq=3 ttl=64 time=1.10 ms
64 bytes from 192.168.3.1: icmp_seq=4 ttl=64 time=1.22 ms
64 bytes from 192.168.3.1: icmp_seq=5 ttl=64 time=1.35 ms
64 bytes from 192.168.3.1: icmp_seq=6 ttl=64 time=1.13 ms
64 bytes from 192.168.3.1: icmp_seq=7 ttl=64 time=1.17 ms
64 bytes from 192.168.3.1: icmp_seq=8 ttl=64 time=1.18 ms
64 bytes from 192.168.3.1: icmp_seq=9 ttl=64 time=1.21 ms
64 bytes from 192.168.3.1: icmp_seq=10 ttl=64 time=1.14 ms

[1]+  Stopped                 ping 192.168.3.1
abnerdoon@koenigdesk:~$ ping 72.14.253.99
PING 72.14.253.99 (72.14.253.99) 56(84) bytes of data.
64 bytes from 72.14.253.99: icmp_seq=1 ttl=240 time=123 ms
64 bytes from 72.14.253.99: icmp_seq=2 ttl=240 time=126 ms
64 bytes from 72.14.253.99: icmp_seq=3 ttl=240 time=125 ms
64 bytes from 72.14.253.99: icmp_seq=4 ttl=240 time=127 ms
64 bytes from 72.14.253.99: icmp_seq=5 ttl=240 time=124 ms
64 bytes from 72.14.253.99: icmp_seq=6 ttl=240 time=123 ms
64 bytes from 72.14.253.99: icmp_seq=7 ttl=240 time=126 ms
64 bytes from 72.14.253.99: icmp_seq=8 ttl=240 time=125 ms

[2]+  Stopped                 ping 72.14.253.99
abnerdoon@koenigdesk:~$ ping google.com
ping: unknown host google.com
abnerdoon@koenigdesk:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.3.136
netmask 255.255.255.0
gateway 192.168.3.1




auto eth0

```

---

### Post by noob12 on 2007-09-30
OK.  

In **System | Administration | Network | DNS tab** did you set your server to 192.168.1.1 as you had in Windows?  This would be pointing to your local proxy in the modem.

If you did that, and it is still not working, try these two server addresses instead.  They are the OpenDNS servers:  

208.67.222.222
208.67.220.220

---

### Post by clinto on 2007-10-01
I wanted to ask something. In the DNS tab, there were a few different addresses there already. There was 192.168.3.136, 192.168.3.137, and 192.168.3.138. Do I need to delete those? I just added the 192.168.1.1 to the list and it didn't do anything. I didn't try using those other server addresses yet.

Also, after I make changes, what do I do to restart the network? I've been doing
sudo ifdown eth0
sudo ifup eth0

Is that correct? I saw where others said to use
sudo etc/init.d/networking restart

but every time I try that it says that I'm using it wrong or can't find the command

---

### Post by clinto on 2007-10-01
WOOT! It's working. I'm not sure if I did what I should have, but I deleted all the addresses that were there before, kept the 192.168.1.1 that I use for windows(which is the address for my DSL modem), and added those OpenDNS server numbers as well. ifdown and ifup and it works.

I need to learn more about networking, I'm not sure exactly what I did to get it connected again.

---

### Post by noob12 on 2007-10-01
Great! 

To answer your question, **sudo /etc/init.d/networking restart**  essentially does **ifdown** **ifup** on all interfaces that are in your **/etc/network/interfaces** file.  

If you get errors there, it is usually due to having configuration stanzas for interfaces that don't actually exist on your machine.  Ubuntu ships with a default file that has a bunch of interfaces that users might have.  They are benign errors (but do take a small amount of time at boot); you can run **ifconfig -a** and find the interfaces that you have, then remove the sections from **/etc/network/interfaces** for ones that are not listed.

---

### Post by clinto on 2007-10-02
Sweet! That worked. Thanks you. I really appreciate it. Now I don't have to log into Windblows every time I want to use the internet.

---

