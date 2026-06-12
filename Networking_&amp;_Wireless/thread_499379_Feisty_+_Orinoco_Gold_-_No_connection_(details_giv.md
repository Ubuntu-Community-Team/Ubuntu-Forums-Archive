---
title: "Feisty + Orinoco Gold - No connection (details given)"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by avogadro623 on 2007-07-12
I am trying to get connected using my Lucent Gold pcmcia card. I am not able to connect at all (with and without hex 128 bit WEP). I searched and found some tips and ran the usual commands -iwconfig, ifconfig,lsmod, dmesg. I looked for any other drivers - hostap, prism etc to blacklist and I found nothing using the lsmod command.  Here are the details:

**iwconfig**
[INDENT]lo        no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"gollum"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]
**ifconfig**
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:02:2D:07:EB:89  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59140 (57.7 KiB)  TX bytes:59140 (57.7 KiB)[/INDENT]

**lsmod | grep orinoco**
orinoco_cs             16900  1 
orinoco                43028  1 orinoco_cs
hermes                  8448  2 orinoco_cs,orinoco
pcmcia                 39212  1 orinoco_cs
pcmcia_core            40852  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic

**dmesg**
......
[  617.728000] orinoco_cs 0.0: resuming
[  617.916000] orinoco_cs 0.0: suspend
[  618.020000] orinoco_cs 0.0: resuming
[  618.020000] orinoco_cs 0.0: resuming
[  618.204000] orinoco_cs 0.0: suspend
[  618.308000] orinoco_cs 0.0: resuming
[  618.308000] orinoco_cs 0.0: resuming
[  618.492000] orinoco_cs 0.0: suspend
[  618.596000] orinoco_cs 0.0: resuming
[  618.596000] orinoco_cs 0.0: resuming
[  620.668000] orinoco_cs 0.0: suspend
[  620.772000] orinoco_cs 0.0: resuming
[  620.772000] orinoco_cs 0.0: resuming
[  624.096000] ADDRCONF(NETDEV_UP): eth0: link is not ready

Please let me know if any more details are required.

---

### Post by ugm6hr on 2007-07-16
This will tell you which driver you are using (in the configuration / driver=.... line):
```
lshw -C network
```

You could search for the driver to see how stable it is.

```
lspci
```
Will also list the correct device details (as Network / Ethernet controller).

---

