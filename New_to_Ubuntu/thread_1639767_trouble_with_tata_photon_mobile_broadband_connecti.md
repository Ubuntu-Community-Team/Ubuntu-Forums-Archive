---
title: "trouble with tata photon mobile broadband connection"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by havtrouble on 2010-12-07
I use Tata Photon plus mobile broadband connection which is a USB device. I have configured this device as per advice in the thread [http://ubuntuforums.org/showthread.php?t=1274776&highlight=tata+photon](http://ubuntuforums.org/showthread.php?t=1274776&highlight=tata+photon) 
Thanks to makafsal in that thread.

My problem is that I can connect to braodband automatically when I boot my laptop (with the device plugged-in). No user-name and password required.
If I disconnect the broadband connection (with the device still plugged-in), I cannot reconnect to the broadband. 
No matter the number of times I try, it still comes up "disconnected" 
If I physically disconnect the device and after 30 secs plug it back in, the device connects automatically. 
Since I have a time-bound Internet plan I wish to connect and disconnect (without physically removing the device)  with ease.
Is that possible?

---

### Post by Hippytaff on 2010-12-07
Whats the connection called - you can find out by doing
```

iwconfig

```
 
then you can try using these commands to turn your connection on and off
For me it would be - on
```

eth0 up

```
and off
```

eth0 down

```
 
obivously eth0 should be replaced by whatever your wireless name is.
 
Also, when you disconnect you might not be able to reconnect because there are hard or soft blocks implamented. To check this, when you dicsonnect and try to reconnect do
```

rfkill list

```
this should return info on blocks. If there are blocks it will return something like 
```

soft block yes
hard block no

```
if there are any 'yes' then do
```

rfkill unblock all

```
 
...failing this, post the output of
```

lsusb

```
and```

iwconfig

```
when the usb is plugged in, but not working :-)

---

### Post by havtrouble on 2010-12-07
Thank you for the help
I tried iwconfig with my USB internet connection active and these are the results
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

 tried rfkill list with the USB internet connection disconnected and these are the results

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: noI tried lsusb with the USB internet connection on and these are the results

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 024: ID 12d1:140b Huawei Technologies Co., Ltd. EC1260 Wireless Data Modem HSD USB Card
Bus 005 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubLine 4 with Huawei Technologies is my USB internet connection

---

### Post by Hippytaff on 2010-12-07
When you do lsusb when the device is not working, does it appear as - usbstorage device?

---

### Post by havtrouble on 2010-12-07
This is the result of lsusb with the device physically connected but disconnected from the internet
> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Hippytaff on 2010-12-07
you might need to manually mount it, can you post the results of
```

mount

```
both while it works and when it doesn't

---

### Post by havtrouble on 2010-12-07
while it is working

> suneel@Satellite-L310:~$ mount
/dev/sda10 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suneel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suneel)
suneel@Satellite-L310:~$ 


While it is not working but connected

> suneel@Satellite-L310:~$ mount
/dev/sda10 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suneel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suneel)
suneel@Satellite-L310:~$ 


---

### Post by Hippytaff on 2010-12-07
Not sure, I think the driver, for some reason, ceases after you disconnect - did you try clicking on the wireless icon on the right of the top panel and looking to see if you can choose to connect from there.
what does
```
dmesg | tail
```
output when you plug the device in?

---

### Post by havtrouble on 2010-12-08
> did you try clicking on the wireless icon on the right of the top panel  and looking to see if you can choose to connect from there.
The only method I know and use to connect/disconnect from the internet is by using the wireless icon on the right on the top panel.
Results of dmesg | tail
> suneel@Satellite-L310:~$ dmesg | tail
[   19.223710] sd 8:0:0:1: Attached scsi generic sg3 type 0
[   19.244045] sd 8:0:0:1: [sdb] Attached SCSI removable disk
[   23.989060] Skipping EDID probe due to cached edid
[   24.012084] Skipping EDID probe due to cached edid
[   24.032058] Skipping EDID probe due to cached edid
[   24.052058] Skipping EDID probe due to cached edid
[   27.304091] Skipping EDID probe due to cached edid
[   30.653076] Skipping EDID probe due to cached edid
[   46.507950] PPP BSD Compression module registered
[   46.523499] PPP Deflate Compression module registered


---

### Post by Hippytaff on 2010-12-08
I think, for some reason, the device is not recognised once you disconnect, I think this may have something to do with the driver not kicking in when you want to restart the device. To be honest, I don't know how to fix this, but have a feeling its something to do with conflicting drivers.
 
If you do
```

lsmod | grep -i EC

```
you should get EC1260 returned...if there are any others similar, try blacklisting them, by adding them to the blacklist file found here - /etc/modprobe.d/blacklist (I think, not on my ubuntu box right now).

---

### Post by havtrouble on 2010-12-08
s> uneel@Satellite-L310:~$ lsmod | grep -i EC
snd_hda_codec_conexant    29939  1 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


Since the internet connection works and reconnecting alone is a bit of a hassle, I think I will accept the current situation.

---

### Post by Hippytaff on 2010-12-08
Fair enough, I'm reaching the limit of my (fairly limited knowledge) can't see your driver there either...could be a bug though.

Sorry I couldn't help you further :-)

---

### Post by havtrouble on 2010-12-09
Thanks for all the help. The last time I tried Ubuntu was in 2007 and the affair lasted barely a week before I headed back to Billsville. I wish I had persisted. Back then, never knew there were such useful help-forums. This time I am here for good. OK let me head out and start new threads to ask new questions

---

### Post by Hippytaff on 2010-12-09
Excellent - I tried linux about 12 years ago and had an horrific experience with Mandrake - went back to Bill until a few months ago. Ubuntu has won me over now though - completely windows free. (though the missus has it on her laptop- philistine :-) )
 
Now I'm comfortable with linux I'm going to dual boot with another linux distro (debian) and do a bit of distro hopping.
 
By the way, if you want to learn command line stuff INX livecd is and excellent introduction into the power of cli - I was amazed (though I am a bit of a nerd) :-)

---

