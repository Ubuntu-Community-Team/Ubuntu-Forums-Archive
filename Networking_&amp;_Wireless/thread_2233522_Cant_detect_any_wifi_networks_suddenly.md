---
title: "Cant detect any wifi networks suddenly ?"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by guldberg72 on 2014-07-09
hey guys. suddenly today when i turned my computer on (ubuntu 13.10) my wifi couldnt detect any wirreless networks ? and yesterday there was atleast 10 including my own. my ipad have no problem...

```
sudo iwlist scandaniel@daniel-K53BR:~$ sudo iwlist scan[sudo] password for daniel: 
usb0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


daniel@daniel-K53BR:~$ sudo iwlist scan
usb0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


daniel@daniel-K53BR:~$ sudo iwlist scan
usb0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


daniel@daniel-K53BR:~$ sudo iwlist scan
usb0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


daniel@daniel-K53BR:~$ lspci | grep Network
04:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
daniel@daniel-K53BR:~$ lsmod
Module                  Size  Used by
cdc_ether              14351  0 
usbnet                 43877  1 cdc_ether
cdc_acm                28803  0 
fglrx                8085343  185 
amd_iommu_v2           19054  1 fglrx
nvram                  14411  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  1 snd_seq
snd                    69238  5 snd_timer,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
binfmt_misc            17468  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
psmouse               102222  0 
r8169                  67581  0 
mii                    13934  2 r8169,usbnet
pata_atiixp            13271  0 
ahci                   25819  2 
libahci                32168  1 ahci
daniel@daniel-K53BR:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:bf:48:56:1b:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1857 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:161500 (161.5 KB)  TX bytes:161500 (161.5 KB)


usb0      Link encap:Ethernet  HWaddr 9e:5b:62:03:04:6a  
          inet addr:192.168.42.163  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::9c5b:62ff:fe03:46a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1709779 (1.7 MB)  TX bytes:350814 (350.8 KB)



```

---

### Post by Adler on 2014-07-09
Hi All,

I am having the same exact problem with my H-P Ultrabook running 64-Bit 14.04. I should mention I have been running very well with the 3.15 Linux Kernel. It seems that I drained the battery, and upon re-boot suddendly no Wifi. In Network-Manager I can access Ethernet, but not WiFi.

Reading through Forums I discovered that by hitting F7 on my keyboard I can access previous Kernels. Using Linux Kernel 3.14 I do get WiFi back, but my Virtual Machines running under both Virtualbox, and VMWare, are no longer accessible. The reason there is that I'd build drivers for both these machines based off of Linux Kernel 3.15.

So, I do have a short term fix, but need a more permanent solution. Any help would be appreciated.

Adler
*On the Jersey Shore*

---

### Post by grahammechanical on 2014-07-09
@Adler. Interesting problem but it is not your thread. Actually you have a different problem. True? We cannot support two people in the same thread. Thank you.

@guldberg72

What is usb0? Is that your Wireless adapter? If it is then the printout says

> UP BROADCAST RUNNING MULTICAST

So, it should be working. If it did not say RUNNING then it would not be connected to the router. But it should be detecting wireless access points because the report says BROADCAST and it is transmitting (TX bytes 350.8KB) and receiving (RX bytes 1.7MB).

If usb0 is not your normal wireless adapter then I am wondering if the wireless adapter is switched on

```
rfkill list
```

should give you something like this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Soft blocked = WiFi or Networking not enabled
Hard blocked = wireless adapter switched off by a method in hardware such as a key combination. What other OS do you have on that machine? I understand that if we switch wireless off in the Windows OS then it cannot get switched on by Ubuntu when it loads.

Try

```
rfkill unblock wifi
```

Otherwise you will have remove what is hard blocking the wireless adapter.

Regards.

---

### Post by Adler on 2014-07-09
>  			 			@Adler. Interesting problem but it is not your thread. Actually you  have a different problem. True? We cannot support two people in the same  thread. Thank you.

grahammechanical,

THX. I'll go into lurker mode...

Adler
*On The Jersey Shore*

---

