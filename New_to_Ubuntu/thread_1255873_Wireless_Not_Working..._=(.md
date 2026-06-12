---
title: "Wireless Not Working... =("
date: 2009-09-02
forum: New to Ubuntu
---

### Post by qwerty123abc on 2009-09-02
Ok.. I have a Atheros wireless card and ubuntu says that i should use the madwifi driver for Atheros wireless cards... I activated the madwifi driver and rebooted.. no wireless. I've tried using the ndiswrapper thing and it says that the driver is already installed...
After awhile i noticed that while booting into ubuntu on the splash screen right at the start the wireless LED light turns on then towards the end of the splash screen loading thing it turns off.

Help Please :D

---

### Post by 3rdalbum on 2009-09-02
So you've got madwifi and Ndiswrapper both set up to try and use the card? That's not likely to end well.

---

### Post by Gone fishing on 2009-09-02
I agree with 3rdalbum. I think I'd remove the ndiswrapper, then restart the networking sudo /etc/init.d/networking restart or reboot then run sudo iwconfig and see if the wireless device is working.

---

### Post by qwerty123abc on 2009-09-02
Madwifi didn't work so i disabled it and used ndiswrapper but ndiswraper said the driver is installed.

---

### Post by nothingspecial on 2009-09-02
If you run ```
lsmod
```do you see ath5k or ath_pci?

---

### Post by qwerty123abc on 2009-09-02
> **nothingspecial said:**
> If you run ```
lsmod
```do you see ath5k or ath_pci?

Sorry for taking so long to reply.

> Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
usb_storage            82880  1 
binfmt_misc            16776  1 
ppdev                  15620  0 
radeon                342816  2 
drm                    96296  3 radeon
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
arc4                    9856  2 
snd_rawmidi            29696  1 snd_seq_midi
ecb                    10752  2 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               63240  0 
ath5k                 107008  0 
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
videodev               41600  1 uvcvideo
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            24440  0 
mac80211              217208  1 ath5k
serio_raw              13316  0 
pcspkr                 10496  0 
v4l1_compat            21764  2 uvcvideo,videodev
i2c_piix4              18448  0 
shpchp                 40212  0 
ati_agp                14988  0 
agpgart                42696  2 drm,ati_agp
soundcore              15200  1 snd
video                  25360  0 
atl2                   34200  0 
led_class              12036  2 ath5k,asus_laptop
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
cfg80211               38032  2 ath5k,mac80211
usbhid                 42336  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


---

### Post by nothingspecial on 2009-09-02
> mac80211 217208 1 ath5k

The madwifi driver is ath_pci (last time I checked).

Try enabling it again.

---

### Post by nothingspecial on 2009-09-02
Or search synaptic for an earlier kernel. The one that ends with .13 works with atheros cards. You need the image and the headers.

---

### Post by qwerty123abc on 2009-09-02
Madwifi didnt work and neither did the kernel.. i think it didn't anyway..

How do you search for wireless networks?

Thing is it worked fine on the live cd.. I clicked on the network manager icon and under "Wireless Networks" i saw my wireless network..(but i didnt try to connect) Now when i click on the icon it just says.. "Wiresless Networks" and nothing is under it. 

So i dunno.

Also my wireless works fine in windows..

---

### Post by nothingspecial on 2009-09-02
You have to boot into the earlier kernel.

Reboot and when the screen says grub loading press escape and choose the kernel that ends in .13.

---

### Post by qwerty123abc on 2009-09-02
I did.. Is it 2.6.28-13? The kernel?

---

### Post by nothingspecial on 2009-09-02
That`s strange. I just did that the other day on my wifes aspire one. Her wireless works with that kernel:-k

---

### Post by qwerty123abc on 2009-09-02
Ugh.. Im stuck then. Would ubuntu 8.0.4 work?

---

### Post by nothingspecial on 2009-09-02
Yes but you`d have to manually compile the madwifi drivers.

---

### Post by jonick on 2009-09-02
you apear to be still loading the kernel driver (ath5k) not the mad wifi driver (if you still have mad wifi installed) ... try blacklisting the ath5k driver,so that you get the ath_pci driver to load. If you don't have one or other driver blacklisted, sometimes the two drivers conflict with each other on bootup causing the card to become un-responsive.

---

### Post by nothingspecial on 2009-09-02
Try the madwifi driver manually

```
gksudo gedit /etc/modules
```

add ```
ath_pci
``` to the end of that file.

type ```
ls /etc/modprobe.d/
```

There is a new blacklist.conf for madwifi but I can`t remember what its called
```

gksudo gedit /etc/modprobe.d./*[COLOR="Red"]whatever_the_madwifi.conf_is_called[/COLOR]*
```

and put a # infront of anything in there. It should say blacklist ath_pci so make it #blacklist ath_pci.```


gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add ```
ath5k
``` to the bottom of that file.

I`m sorry if this advice sounds sketchy but they changed those file names in jaunty and I`m not using it at the moment and I can`t remember exactly what they are called. I can check and get back to you in about an hour.

---

### Post by nothingspecial on 2009-09-02
Oh yes and after you`ve done that try both kernels.

---

### Post by qwerty123abc on 2009-09-02
Ugh tried it quickly.. didn't work.. I have to go but ill be back later.

Thing is that wireless worked on the live cd. 

By the way thanks for all your help.:D

---

### Post by jonick on 2009-09-02
Weirdest thing is, I came back to Ubuntu, cause it was the only distro that my Atheros card worked with straight out of the box :-)

I'm currently running a NB100 netbook with more or less the same Atheros card as you quite happily on Karmic.

---

### Post by qwerty123abc on 2009-09-02
Ill try Karmic.

---

### Post by qwerty123abc on 2009-09-03
HA:D I installed Karmic & wireless works fine now. Thanks

---

### Post by nothingspecial on 2009-09-03
And you now know how to blacklist kernel modules.

Cool hey? :D

---

### Post by jonick on 2009-09-03
Good result !!! :-)

---

