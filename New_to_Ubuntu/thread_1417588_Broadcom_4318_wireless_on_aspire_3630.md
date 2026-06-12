---
title: "Broadcom 4318 wireless on aspire 3630"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by celticbhoy on 2010-02-27
Cant get wireless to work on this, in network manager the tick box to enable wireless is greyed out. Getting this from the command line :-



mary@jacks-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

mary@jacks-laptop:~$ dmesg|grep -e b43 -e wlan
[    2.010867] b43-pci-bridge 0000:00:0b.0: enabling device (0000 -> 0002)
[    2.010893] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.202743] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   18.861372] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   18.927283] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   18.935272] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   18.942056] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.075363] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   19.153740] Registered led device: b43-phy0::tx
[   19.153765] Registered led device: b43-phy0::rx
[   19.153789] Registered led device: b43-phy0::radio
[   19.154132] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.184046] b43-phy0: Radio hardware status changed to DISABLED
[  263.816059] Modules linked in: dm_crypt binfmt_misc ppdev joydev pcmcia snd_intel8x0 snd_ac97_codec ac97_bus arc4 ecb snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy iptable_filter snd_seq_oss ip_tables x_tables snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device yenta_socket rsrc_nonstatic b43 mac80211 cfg80211 led_class snd soundcore snd_page_alloc pcmcia_core psmouse serio_raw shpchp lp parport i2c_sis96x dm_raid45 xor usbhid sis900 mii ssb sis_agp agpgart
mary@jacks-laptop:~$ 



Any help?

---

### Post by lkraemer on 2010-02-28
Try reading Posting #3 here:
[http://ubuntuforums.org/showthread.php?t=1314852&highlight=b43](http://ubuntuforums.org/showthread.php?t=1314852&highlight=b43)

It looks as if you are trying to use b43 and the firmware.
Selection #3 in the above posting should get you going.

lk

---

### Post by spiky001 on 2010-02-28
I know this seems strange but have you got wireless turned on?

---

