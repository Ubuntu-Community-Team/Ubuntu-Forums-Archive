---
title: "Intel Pro 2200BG"
date: 2013-11-19
forum: Networking &amp; Wireless
---

### Post by cespuny on 2013-11-19
Hello & thanks to everyone,

I have problems with my wifi card (Intel Pro 2200BG card) after installing Lubuntu 12.04 on my laptop. It works perfectly under Windows XP.

I have tried waths it's writen in the next post, but it doesn't work :(
[http://ubuntuforums.org/showthread.php?t=1982509](http://ubuntuforums.org/showthread.php?t=1982509)

I have also tried to unblock hard like:
[http://askubuntu.com/questions/155391/my-wireless-is-hard-blocked](http://askubuntu.com/questions/155391/my-wireless-is-hard-blocked)

But nothing again :(

Here some information about my laptop:

```

cespuny@Portatil:~$ rfkill list all0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

cespuny@Portatil:~$ lspci -nn | grep 2200
02:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

cespuny@Portatil:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 jul 12 16:00 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 jul 12 16:00 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 jul 12 16:00 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 jul 12 16:00 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 jul 12 16:00 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 jul 12 16:00 ipw2200-sniffer.fw

```

Thanks again!

---

### Post by praseodym on 2013-11-19
Treid to reset your BIOS to default settings? What laptop is it? Please show
```

lsmod
```

---

### Post by cespuny on 2013-11-20
My laptop is an ACER TravelMate 290.

```

cespuny@Portatil:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  1 
pcmcia                 39826  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17393  0 
snd_usb_audio         101566  1 
snd_hwdep              13276  1 snd_usb_audio
snd_usbmidi_lib        24588  1 snd_usb_audio
snd_intel8x0           33455  4 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_seq_midi           13132  0 
snd_pcm                80916  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  18 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
psmouse                96744  0 
videodev               86588  1 uvcvideo
soundcore              14635  1 snd
serio_raw              13027  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  1 
mac_hid                13077  0 
bluetooth             158447  10 bnep,rfcomm
ppdev                  12849  0 
shpchp                 32265  0 
ipw2200               146210  0 
libipw                 46732  1 ipw2200
cfg80211              178877  2 ipw2200,libipw
lib80211               14040  2 ipw2200,libipw
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
radeon                733899  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
firewire_ohci          40180  0 
i2c_algo_bit           13199  1 radeon
8139too                23283  0 
8139cp                 22633  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

Thanks!

---

### Post by praseodym on 2013-11-20
Any button/switch/key combination? Tried to reset the BIOS to default?

---

### Post by cespuny on 2013-11-20
Yes, I have reseted the BIOS and nothing.
I also tried to press some combination keys, and nothing again!!
There's a little switch on the side of the laptop to turn on/off the wireless card, but it's always ON.

:(

---

### Post by praseodym on 2013-11-20
AFAIK this card only supports channels 1-11. On which channel does your router send?

Check
```

iwlist chan
iwconfig
rfkill list
```

---

### Post by cespuny on 2013-11-20
My router is configured on channel 11.

```

cespuny@Portatil:~$ iwlist chan
lo        no frequency information.


eth1      11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Channel:0


eth0      no frequency information.


cespuny@Portatil:~$ iwconfig
lo        no wireless extensions.


eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth0      no wireless extensions.


cespuny@Portatil:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

The _*Hard blocked: yes*_ is very strange, isn't it?

---

### Post by praseodym on 2013-11-20
Try to press/use the keys and buttons permanently or, alternatively, repeatedly during boot-up.

Does LAN work? If yes, install ACER_Hotkeys, but first: Is it 32 or 64 bit?

---

### Post by cespuny on 2013-11-20
Which keys I have to press?

It's 32 bits.

How I can install ACER_Hotkeys? I'm pretty new on linux , sorry!

Thanks again!

---

### Post by cespuny on 2013-11-21
By the way, LAN works perfectly, 
I'm responding connected to that!! :)

---

### Post by cespuny on 2013-11-21
Searching in the forum I found this:
[http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

Maybe is this causing the problem?
What do you think?

---

### Post by praseodym on 2013-11-21
In your case acer-wmi is not loaded. Try it on the fly
```

sudo modprobe -v acer_wmi
sudo rfkill unblock all
rfkill list
```
Check buttons, etc

---

### Post by cespuny on 2013-11-21
Yeahhhhh!! I have solved the problem!!!!
I have installed the ACE_Hotkeys and it worked!!!!

I have followed these web: [http://wiki.ubuntuusers.de/Acer_Hotkeys](http://wiki.ubuntuusers.de/Acer_Hotkeys)

Thank you very much for your help!!!

---

### Post by praseodym on 2013-11-22
This would have been the next link ;-)

There is also a PPA available:

[https://launchpad.net/~cogito-16/+archive/ppa](https://launchpad.net/~cogito-16/+archive/ppa)

---

