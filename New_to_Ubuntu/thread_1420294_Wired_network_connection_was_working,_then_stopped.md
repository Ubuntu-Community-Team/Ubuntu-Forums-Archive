---
title: "Wired network connection was working, then stopped. How to connect to the net?"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by appsman on 2010-03-02
OK - I searched around but can't find any answers. All I want to do is connect to the net. The laptop was connecting through the wired connection but then stopped. My other machines are still working.

When the laptop was working, it was doing it automagically. When it stopped, I made it to the KDE Control Module for Network Connections and created a new wired connection. However, there is not much to it. I left these items alone:
   "Restrict To Interface" = "Any"
   "MTU" = "Automatic"

So first question, after I know my Network Connection setting is correct, how do I actually command it to connect??

I'm running Kubuntu 9.10 Koala.

Results of ifconfig check follow

```
$ ifconfig -a

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5280 (5.2 KB)  TX bytes:5280 (5.2 KB)


```

---

### Post by Iowan on 2010-03-03
I'm not really familiar with Kubuntu - but your thread looked lonely, and in need of a bump...
I presume your using Network Manager (or Kubuntu's version - what's it called?) **sudo lshw -C network** (from a terminal) should still show interface details.

---

### Post by appsman on 2010-03-04
Thanks.

My network manager is called 'KNetworkManager'. That's where I identified 
> "Restrict To Interface" = "Any"
"MTU" = "Automatic"
but didn't change anything.

I ran 
```
$ sudo lshw -C network
```
as you say, but got nothing. I saw some text fly by, such as:
 SCSI
 PCI
 DMI
 CPUID
but they just flew by real fast. I also did
```
$ sudo lshw -C network > tmp.txt
```
but the text file was 0 byte in size and was blank.

I also tried
```
$ sudo lshw > tmp.txt
```
but when I searched for the word 'network' nothing appeared. I'm not posting the results because the info was kind of personal.

What now? How could "sudo lshw -C network" produce *nothing*?

---

### Post by appsman on 2010-03-06
bump - no progress yet

---

### Post by patchwork on 2010-03-06
If you're on dhcp, try

```
sudo ifup -a && sudo dhclient
```

---

### Post by appsman on 2010-03-07
Thanks for the response. I ran
```
sudo ifup -a && sudo dhclient
```

which output "No broadcast interfaces found - exiting."

I found this thread which started out sounding like my problem
[http://ubuntuforums.org/showthread.php?t=819269](http://ubuntuforums.org/showthread.php?t=819269)

I got nearly identical outputs as in the above thread, until I reached this part:
```
sudo lshw -C network
```
Which gave no output (again).

I ran "lshw" but the word "network" did not appear in the output.

This must be hitting on the real problem - how could "lshw -C network" give **nothing** for output?

---

### Post by appsman on 2010-03-13
bump

---

### Post by chaanakya_chiraag on 2010-03-13
That's not good... could you please post the output of ```
lsmod
```  It seems like the driver for your network card got unloaded somehow...

---

### Post by appsman on 2010-03-18
Thanks for coming back chaanakya_chiraag.

So this is getting interestinger. I just powered up the laptop, and it automatically connected to the net (wired connection)!

So first off, here is the answer to your question:
```

$ sudo lsmod
Module                  Size  Used by
usb_storage            52576  0 
dm_crypt               12928  0 
snd_es1938             18532  2 
gameport               11368  2 snd_es1938
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  2 snd_es1938,snd_pcm_oss
snd_page_alloc          9156  1 snd_pcm
snd_opl3_lib           10396  1 snd_es1938
snd_hwdep               7200  1 snd_opl3_lib
snd_mpu401_uart         6940  1 snd_es1938
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
joydev                 10240  0 
pcmcia                 36808  0 
snd_timer              22276  3 snd_pcm,snd_opl3_lib,snd_seq
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
yenta_socket           24296  1 
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
rsrc_nonstatic         11644  1 yenta_socket
psmouse                56500  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   6688  0 
snd                    59204  16 snd_es1938,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             31940  1 
serio_raw               5280  0 
i2c_piix4               9932  0 
parport                35340  3 lp,ppdev,parport_pc
soundcore               7264  1 snd
shpchp                 32272  0 
led_class               4096  0 
e100                   32420  0 
mii                     5212  1 e100
intel_agp              27484  1 
agpgart                34988  1 intel_agp
floppy                 54916  0 

```
OK - so now that the network connection works again, I ran lshw again
```

$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: 08
       serial: 00:d0:59:0e:32:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:5 memory:80100000-80100fff ioport:7480(size=64) memory:80200000-802fffff

```
So now my network is back up, I see Konqueror wants to run a bunch of updates (I **think** this is what set off my problem in the first place).

Then after that runs, the network connection crashes again. So running lshw and lsmod again I get the following differences.

As to "lshw -C network", no differences.

New to lsmod:
```

> nls_iso8859_1           3740  0
> nls_cp437               5372  0
> vfat                   10716  0
> fat                    51452  1 vfat

```

I rebooted and the network is still crashed. Now what?

Thanks again for the help!

---

