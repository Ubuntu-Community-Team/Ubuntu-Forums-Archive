---
title: "Wi-Fi not working"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by fslezak on 2010-06-06
Hello. I have a Broadcom B43 wireless card, and it will not pick up my Linksys Wi-Fi network, even with the proprietary driver installed. What can I do? I am running Ubuntu 10.04. This card worked fine in 8.04.

---

### Post by TeoBigusGeekus on 2010-06-06
Try wicd instead of gnome network manager - it's better for wireless
```
sudo apt-get install wicd
```

---

### Post by beew on 2010-06-06
Did you install the b43-fwcutter? (can find it in synaptic or do " sudo apt-get install" in the terminal)

I had problem with some guy's computer using a broadcom wireless and this works perfectly.

---

### Post by Gone fishing on 2010-06-06
> Did you install the b43-fwcutter? (can find it in synaptic or do " sudo apt-get install" in the terminal)

I had problem with some guy's computer using a broadcom wireless and this works perfectly.

Odd I had the opposite experience - try both of them!

---

### Post by admiralspark on 2010-06-06
If all else fails, you can use ndiswrapper to make the windows driver work. That solution worked great for me since I began on 9.04. 
Please run this in a terminal:
```
lspci | grep Network
``` and copy/paste the output back here so that we can be more card-specific on advice.

---

### Post by fslezak on 2010-06-06
.

---

### Post by fslezak on 2010-06-06
I have b43-fwcutter installed.

Output for " lspci | grep Network " :

02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by sandyd on 2010-06-06
> **fslezak said:**
> I have b43-fwcutter installed.
do you have bcmwl-kernel-source installed.

If you do, you **must** remove one of them because they both conflict

---

### Post by cariboo on 2010-06-06
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by fslezak on 2010-06-06
No

---

### Post by lkraemer on 2010-06-06
Post the output of:
```

lsmod

```

lk

---

### Post by fslezak on 2010-06-06
From LSMOD:


Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
nfsd                  238935  11 
lockd                  64849  1 nfsd
nfs_acl                 2245  1 nfsd
auth_rpcgss            33735  1 nfsd
sunrpc                193181  10 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs                3437  1 nfsd
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
font                    7557  1 fbcon
snd_seq_dummy           1338  0 
bitblit                 4707  1 fbcon
snd_seq_oss            26726  0 
softcursor              1189  1 bitblit
pcmcia                 33024  0 
snd_seq_midi            4557  0 
vga16fb                11385  0 
snd_rawmidi            19056  1 snd_seq_midi
yenta_socket           20408  1 
vgastate                8961  1 vga16fb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
rsrc_nonstatic         10015  1 yenta_socket
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i915                  282354  3 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29297  1 i915
b43                   157218  0 
mac80211              204922  1 b43
cfg80211              126485  2 b43,mac80211
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               2864  1 b43
drm                   162471  4 i915,drm_kms_helper
joydev                  8708  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
intel_agp              24177  2 i915
ndiswrapper           184677  0 
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
shpchp                 28820  0 
video                  17375  1 i915
psmouse                63245  0 
output                  1871  1 video
serio_raw               3978  0 
parport                32635  2 ppdev,lp
8139too                18545  0 
8139cp                 16186  0 
ssb                    37336  1 b43
mii                     4381  2 8139too,8139cp

---

### Post by Gone fishing on 2010-06-07
My experience with my daughters compaq mini was that it wouldn't work with the b43-fwcutter driver but worked fine with the proprietary STA driver.

So If you haven't tried that driver I would suggest removing the b43 driver and trying the STA driver.

---

### Post by madnessjack on 2010-06-07
Hi, I have the same card and I always use this tutorial to get it working
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Never failed me yet :P

Hope this helps

---

### Post by lkraemer on 2010-06-07
Post the output of:
```

ndiswrapper -l

```
It looks as if you also have ndiswrapper installed.  If ndiswrapper -l
doesn't show any drivers loaded remove it, but if ndiswrapper shows drivers
loaded, keep removing them until ndiswrapper doesn't display any loaded.
That is......if you have decided what method you will use, and it isn't
with ndiswrapper....

Ref: **REMOVE WINDOWS DRIVERS:**
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto)

Then decide what method you will use.......stick with it until you have
it working.  No sense trying more than one method at a time.

If you are sticking with B43, verify that the firmware has been copied to
/lib/firmware.  There should be a b43 and a b43legacy subdirectory there.
Then go to Hardware Drivers, DISABLE, and RE-ENABLE those drivers.

lk

---

### Post by fslezak on 2010-06-07
Whats the command name for the STA driver discussed in post No. 13?

P.S. I do not have NDISWrapper.

---

### Post by SlidingHorn on 2010-06-07
> **fslezak said:**
> From LSMOD:


ndiswrapper           184677  0 

It appears that you do....

---

### Post by fslezak on 2010-06-07
My Mistake.

What is the command for the STA driver that was talked about in Post No. 13?

---

### Post by fslezak on 2010-06-07
From NDISWrapper " ndiswrapper -l " :

```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
```

---

### Post by SlidingHorn on 2010-06-07
could you post the output of:

```
lshw -C Network
```

---

### Post by lkraemer on 2010-06-07
OK, your problem is you have both b43 drivers, and ndiswrapper using
bcmwl5 and also ssb as alternate.  At some point you must have tried
installing ndiswrapper and also b43.  So, HOLD ON.....DON'T install
STA also because you already have two conflicting, and you want to add
a third......Not the correct thing to do.......
```

bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)

```

So, now you need to make a command decision.  Is it Ndiswrapper using
bcmwl5 (assuming you have selected the proper 32 or 64 Bit Windows Driver
that matches your Ubuntu 10.04 32 or 64 Bit install) OR will you try using
the B43 Drivers and the Firmware that is needed to support the Broadcom
Wifi?  Select ONLY one and Get it working............DON'T MIX-N-MATCH!!!!

Since B43 is the DEFAULT for 10.04 I'd suggest trying that from a LiveCD,
and download the Firmware and copying it to the locations specified in
my previous posting for the HOWTO: ....Broadcom.  I know that works 
because I've tested it twice.  When you have it working from the LiveCD,
use the directions from my previous HOWTO: ...Broadcom, to remove the
Windows Drivers, and also the ndiswrapper module.  That should get our
Wifi functional with B43.

If you must have bcmwl5 and ndiswrapper then you will need to blacklist
the b43 and associated modules to let ndiswrapper work properly.

Post the choice that you select.  Go from there.

lk

---

### Post by fslezak on 2010-06-07
Just got rid of everything but NDISWrapper, and it works fine now! THX!

---

