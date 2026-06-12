---
title: "How do i access a device listed in lsusb, but not in my places?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-01-06
my lsusb shows

mckenzie@mckenzie-home:~$ lsusb
***Bus 005 Device 004: ID 0421:04fa Nokia Mobile Phones*** 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


and my phone appears connected as it displays the message 'transferring data' , but i can't seem to access it - as it is not in my places.

Im sure this is very simple, but that am being very ignorant.

cheers in advance!

---

### Post by phantomjoker on 2009-01-06
i would also like to add - i could access this device fine with 8.04, but i can't on 8.10

---

### Post by phantomjoker on 2009-01-07
anyone?

---

### Post by sam_delta on 2009-01-07
what does the following command return:
```
sudo fdisk -l
```

sam

---

### Post by mc4man on 2009-01-07
If your phone is a music player, it may be interesting to see if something was removed in 8.10 (not a solution

Open up another firefox, remove the address in the location bar and paste this in.

```
file:///usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

It should take you to a .fdi file. (I'm on 8.04, if it doesn't just browse there, d. click and it will open in firefox

Go ctrl+f on keyboard and in the little search box use nokia

This is the first listing in the nokia section, your phones vendor id is 0x421, see if it's still listed


> <!-- Nokia -->
&#8722;
<match key="@storage.originating_device:usb.vendor_id" int="[COLOR="Red"]0x421[/COLOR]">
<!-- Nokia 770, N800 -->
&#8722;
<match key="@storage.originating_device:usb.product_id" int_outof="0x431;0x4c3">
<addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
<append key="portable_audio_player.output_formats" type="strlist">audio/aac</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-wav</append>
</match>

---

### Post by phantomjoker on 2009-01-07
my nokia is the 6300 and yes it is listed

> <!-- Nokia 6300 -->
&#8722;
<match key="@storage.originating_device:usb.product_id" int="0x4fa">
<addset key="portable_audio_player.access_method.protocols" type="strlist">storage</addset>
<append key="portable_audio_player.output_formats" type="strlist">audio/aac</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
<append key="portable_audio_player.output_formats" type="strlist">audio/x-wav</append>
<append key="portable_audio_player.audio_folders" type="strlist">music/</append>
</match>

and also the one you quoted is also found there too.

---

### Post by phantomjoker on 2009-01-07
fdisk -l returns:

> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b099b09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        3648    19535040   83  Linux
/dev/sda4            4014       91201   700337610    5  Extended
/dev/sda5            4014        4535     4192933+  82  Linux swap / Solaris
/dev/sda6            4536        5840    10482381   83  Linux
/dev/sda7            5841        8451    20972826   83  Linux
/dev/sda8            8452       91201   664689343+  83  Linux


---

### Post by phantomjoker on 2009-01-08
any help?

---

### Post by phantomjoker on 2009-01-31
how about now, any ideas?

---

