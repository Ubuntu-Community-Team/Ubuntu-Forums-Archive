---
title: "rt73usb problems - ubuntu 8.04"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by kirios on 2008-04-27
[COLOR="Sienna"]My Prolink wireless adapter seems to be recognized in Ubuntu 8.04 but I'm unable to connect to the network. It works fine in 7.10 (on a different partition). [/COLOR]

```
kirios@thinkcentre:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:1e:f6:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56200 (54.8 KB)  TX bytes:56200 (54.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0e:64:9d:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-0E-64-9D-CE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

```
kirios@thinkcentre:~$ lsusb
Bus 005 Device 003: ID 07b8:b21d D-Link Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08d9 Logitech, Inc. QuickCam Connect
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
```

```
kirios@thinkcentre:~$ modprobe -l rt73usb
/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
```

```
kirios@thinkcentre:~$ dmesg | tail
[  497.678754] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  497.878222] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  498.077704] wlan0: authentication with AP 00:12:0e:84:50:dd timed out
[  508.352546] wlan0: Initial auth_alg=0
[  508.352555] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  508.365890] wlan0: Initial auth_alg=0
[  508.365900] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  508.562521] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  508.762008] wlan0: authenticate with AP 00:12:0e:84:50:dd
[  508.961494] wlan0: authentication with AP 00:12:0e:84:50:dd timed out
```

[COLOR="Sienna"]I'm probably missing something quite obvious. Any suggestions?[/COLOR]

---

### Post by superprash2003 on 2008-04-27
are you able to see your wireless network?

---

### Post by kirios on 2008-04-27
Yes, but it doesn't accept the hex password. 

> **superprash2003 said:**
> are you able to see your wireless network?

---

### Post by kirios on 2008-04-30
Is this something to do with a new rt2500 driver?

---

### Post by kirios on 2008-05-02
Hmm ... Should I revert to 7.10 or forget about using the Internet? Or perhaps forget about using Ubuntu? Decisions, decisions...

---

### Post by ibutho on 2008-05-02
8.04 works fine with my rt73 usb adapter. Are you using WPA because the old rt73 driver does not play nicely with rt73 although the newer rt2x00 should work with WPA. Run "sudo lsmod | grep -i rt" to see which driver is being loaded.

---

### Post by kirios on 2008-05-03
> **ibutho said:**
> 8.04 works fine with my rt73 usb adapter. Are you using WPA because the old rt73 driver does not play nicely with rt73 although the newer rt2x00 should work with WPA. Run "sudo lsmod | grep -i rt" to see which driver is being loaded.

```
kirios@thinkcentre:~$ sudo lsmod | grep -i rt
[sudo] password for kirios: 
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
gameport               16008  1 snd_via82xx
rt73usb                27136  0 
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
snd_mpu401_uart         9728  1 snd_via82xx
snd_rawmidi            25760  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd                    56996  23 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                34760  1 via_agp
usbcore               146028  9 snd_usb_audio,snd_usb_lib,rt73usb,rt2x00usb,gspca,usbhid,ehci_hcd,uhci_hcd
```

[COLOR="DarkRed"]I'm using a hexadecimal WEP password. Btw I can connect to the network while running the live CD but the *lsmod* output looks similar:[/COLOR] 

```
ubuntu@ubuntu:~$ sudo lsmod | grep -i rt
gameport               16008  1 snd_via82xx
rt73usb                27136  0 
snd_mpu401_uart         9728  1 snd_via82xx
rt2x00usb              12800  1 rt73usb
rt2x00lib              22528  2 rt73usb,rt2x00usb
rfkill                  8592  1 rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
mac80211              165652  2 rt2x00usb,rt2x00lib
snd_rawmidi            25760  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
parport_pc             36260  1 
parport                37832  3 ppdev,lp,parport_pc
snd                    56996  23 snd_via82xx,snd_usb_audio,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_usb_lib,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
agpgart                34760  1 via_agp
usbcore               146028  9 snd_usb_audio,rt73usb,rt2x00usb,gspca,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd

``` 

[COLOR="DarkRed"]Any suggestions?[/COLOR]

---

### Post by ibutho on 2008-05-05
Thats puzzling because the right modules are being loaded. If all fails, try the rt73 drivers from [serialmonkey]("http://rt2x00.serialmonkey.com/").

---

### Post by kirios on 2008-05-05
Thanks! Will post again after giving it another try.

> **ibutho said:**
> Thats puzzling because the right modules are being loaded. If all fails, try the rt73 drivers from [serialmonkey]("http://rt2x00.serialmonkey.com/").

---

### Post by merdenoms on 2008-06-20
I have a wireless problem. i have rt73usb drivers and Ubuntu 8.04 has recognized the wireless card automaticly. But it doesn't work full speed. I have a 1mbit connection but it only downloads with 50kb/s. I used many other sites and many other servers in Synaptic. I have also Windows Vista on other partition and wireless works perfectly

---

