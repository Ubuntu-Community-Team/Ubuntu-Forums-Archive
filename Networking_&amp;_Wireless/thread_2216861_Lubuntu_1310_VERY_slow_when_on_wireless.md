---
title: "Lubuntu 13/10 VERY slow when on wireless"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by bruce17 on 2014-04-14
New to Lubuntu as I had to "upgrade" an old Dell Inspiron laptop that was running XP. And ran XP and Firefox very satisfactorily.

Dell Inspiron 5100 with 1 Gb RAM, 40 Gb HD, dualboot with XP taking 35 Gb and Lubuntu 5 Gb. DLink Air Xpert DWL-AG650 wireless adapter.

Install went smooth, found my DLink DWL-AG650 wireless adapter. But Internet is so slow as to be useless. Like a 123 Mb upgrade ran all night and still not finished with half of the files failing to download. Browser was the included Firefox. Booted into XP and Firefox ran quickly as it normally does. Connected computer via Ethernet to my cable modem and Firefox on Lubuntu was extremely fast. Seems like it is the Lubuntu ath5k driver, possibly. Security is WEP40/128 bit. 

Any known issues with this adapter and/or driver or any other ideas of why it is so slow only on Lubuntu?

Bruce

---

### Post by praseodym on 2014-04-14
Hi,

please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```

---

### Post by bruce17 on 2014-04-14
etah@etah-Inspiron-5100:~$ lspci -nnk | grep -A2 net
  02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
              Subsystem: Dell Device [1028:0149]
              Kernel driver in use: b44
  --
  03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR5212/AR5213 Wireless Network Adapter [168c:0013] (rev 01)
              Subsystem: Qualcomm Atheros Device [168c:1026]
              Kernel driver in use: ath5k
  etah@etah-Inspiron-5100:~$ lsusb
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  etah@etah-Inspiron-5100:~$ lsmod
  Module                  Size  Used by
  zram                   18070  1 
  arc4                   12536  2 
  ath5k                 135055  0 
  ath                    19187  1 ath5k
  mac80211              517444  1 ath5k
  cfg80211              401762  3 ath,ath5k,mac80211
  joydev                 17097  0 
  gpio_ich               13229  0 
  snd_intel8x0           33069  1 
  snd_ac97_codec        105668  1 snd_intel8x0
  ac97_bus               12642  1 snd_ac97_codec
  snd_pcm                89488  2 snd_ac97_codec,snd_intel8x0
  snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
  snd_seq_midi           13132  0 
  snd_seq_midi_event     14475  1 snd_seq_midi
  dell_laptop            17161  0 
  snd_rawmidi            25094  1 snd_seq_midi
  dcdbas                 14383  1 dell_laptop
  radeon               1312332  2 
  snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
  parport_pc             31981  0 
  ppdev                  17391  0 
  bnep                   18959  2 
  rfcomm                 53664  0 
  bluetooth             323656  10 bnep,rfcomm
  microcode              18894  0 
  pcmcia                 51368  0 
  ttm                    75982  1 radeon
  snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
  snd_timer              24447  2 snd_pcm,snd_seq
  psmouse                90642  0 
  snd                    60790  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
  drm_kms_helper         46867  1 radeon
  yenta_socket           40193  0 
  serio_raw              13189  0 
  lpc_ich                16864  0 
  pcmcia_rsrc            18319  1 yenta_socket
  soundcore              12600  1 snd
  pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
  drm                   242400  4 ttm,drm_kms_helper,radeon
  i2c_algo_bit           13197  1 radeon
  mac_hid                13037  0 
  video                  18777  0 
  shpchp                 32129  0 
  lp                     13299  0 
  parport                40795  3 lp,ppdev,parport_pc
  hid_generic            12492  0 
  usbhid                 47361  0 
  hid                    87370  2 hid_generic,usbhid
  firewire_ohci          35463  0 
  b44                    31234  0 
  firewire_core          57656  1 firewire_ohci
  ssb                    51596  1 b44
  crc_itu_t              12627  1 firewire_core
  mii                    13654  1 b44
  etah@etah-Inspiron-5100:~$ iwconfig
  wlan0     IEEE 802.11abg  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  etah@etah-Inspiron-5100:~$ cat /etc/resolv.conf
  # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
  #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
  etah@etah-Inspiron-5100:~$ rfkill list
  0: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  etah@etah-Inspiron-5100:~$

---

### Post by bruce17 on 2014-04-14
I apologize for the formatting above. Because of the Internet problems I had to copy this and send it from another computer. I'm sure I could have done better. Thank you for your help and patience.

Bruce

---

### Post by praseodym on 2014-04-14
Deactivate the hardware encryption of the wireless driver and add nameservers to the /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
sudo service network-manager restart
```

---

### Post by mörgæs on 2014-04-14
Regarding formatting please edit the post and wrap CODE tags around the terminal output. Makes it easier for people to read.

---

### Post by bruce17 on 2014-04-14
How do I wrap CODE tags around terminal output?

How do I turn off hardware encryption? Is it part of the code that you sent or do I need to do it somehow before inputting the commands you sent? I apologize for the questions. I'm completely new at this and it is late at night here in Europe. Are there instructions somewhere on the forum about how to post and display terminal output?

I also only see the terminal output when I do "Go Advanced." I assume the moderator isn't allowing it to be displayed because of the poor formatting?

Bruce

---

### Post by bruce17 on 2014-04-14
Well, now I see all the posts. Not sure why I didn't before. I'm trying to get used to this as fast as I can.

---

### Post by bruce17 on 2014-04-14
Many thanks!!!. I ran the commands and Firefox is now working very fast. My wife will be happy as this is her computer and all she uses it for is surfing the Internet and email. I used to administrate a 4.2 BSD Unix on a VAX750 thirty years ago and then ran Bell ATT on 286's and 386's. I haven't dabbled in Unix since then. Just entering the commands starting to bring back memories. Thanks again for the quick response and fantastic help. What was the tip-off in the terminal output that identified the fix?

Bruce

---

### Post by praseodym on 2014-04-14
/etc/resolv.conf contained no nameservers, please compare now:
```

cat /etc/resolv.conf
```
The module parameter was experience with Atheros cards ;-)

---

