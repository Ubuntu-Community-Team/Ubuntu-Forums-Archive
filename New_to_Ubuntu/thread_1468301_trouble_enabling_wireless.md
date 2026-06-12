---
title: "trouble enabling wireless"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by audit on 2010-05-01
I am having trouble with my wireless. It says my wireless has been disconnected, but it will not let me connect. Up until last night it worked fine.

Additional note in this same house on another computer running 9.10 am now using 10.04 the wireless is working so I know there is a signal.

---

### Post by P4man on 2010-05-01
some more info would be useful. Do you get a list of access points when you click the network icon? Is the network secured (WEP/WPA) and if so, does it prompt for a password? What network card do you have ? (if you dont know, enter the following commands:

```
lspci
``` 

```
lsusb
```

and post the output.

---

### Post by audit on 2010-05-01
It is a secure network and it does not prompt me for the password. I did check and the password is entered correctly. 
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

notes:
1.) when I click on the i network icon "enable wireless" is not checked, but it will not allow me to select it.
2.) it also states the the "wireless is disabled"
3.) I have been using 10.04 for a week and today is the first time that I have had a problem.
4.) there is another computer in this house using 9.10 and the wireless without a problem.

---

### Post by P4man on 2010-05-01
Hmm.. it might help if you have a lucid livecd or usb stick to boot from, and tell us if it works on there or not. If it does, then its something about the upgrade, if it doesnt work in a livesession, you may need other drivers. 

It would also help if you could disable temporarily the access point wep/wpa security and see if you can connect then or not.

Finally, you can try this to pull in newer drivers:

```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

requires reboot.

---

### Post by randolf_ambrose on 2010-05-01
i'm having the same problem with my Broadcom wireless...

wired is working fine...

but lucid doesnt even detect a wireless!!!

my wireless was workin fine with jaunty!!!

what shall i do...

LSMOD
> Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10802  1 
fat                    55350  1 vfat
rfcomm                 40329  0 
sco                     9617  0 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  0 
l2cap                  34774  4 rfcomm,bnep
btusb                  12969  0 
bluetooth              58621  5 rfcomm,sco,bnep,l2cap,btusb
snd_hda_codec_conexant    28745  1 
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
joydev                 11072  0 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43                   174953  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515131  2 
mac80211              238128  1 b43
ttm                    60815  1 nouveau
sdhci_pci               6700  0 
drm_kms_helper         30742  1 nouveau
cfg80211              148386  2 b43,mac80211
snd                    70978  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  17928  1 sdhci_pci
led_class               3732  2 b43,sdhci
k8temp                  3912  0 
edac_core              45423  0 
edac_mce_amd            9214  0 
psmouse                64608  0 
serio_raw               4918  0 
drm                   198770  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_nforce2             6099  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
usbhid                 40988  0 
hid                    83376  1 usbhid
ieee1394               94675  1 ohci1394
pata_amd               11962  0 
forcedeth              55592  0 
ssb                    43517  1 b43
ahci                   37646  3 

---

### Post by P4man on 2010-05-01
> **randolf_ambrose said:**
> i'm having the same problem with my Broadcom wireless...

wired is working fine...

but lucid doesnt even detect a wireless!!!

my wireless was workin fine with jaunty!!!

what shall i do...

LSMOD


Have a look here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by neonathon on 2010-05-01
i had the same problem when i upgraded my laptop. Here's some things that might help
 
[LIST=1]
[*]Your network encryption might be too high, mabe take it down a notch
[*]download WINE and try to use that to use that to install wireless-card drivers
[*]get a new wireless card (belkin seems to work best with ubuntu)
[/LIST]

---

### Post by P4man on 2010-05-01
> **neonathon said:**
> i had the same problem when i upgraded my laptop. Here's some things that might help
 
[LIST=1]
[*]Your network encryption might be too high, mabe take it down a notch
[*]download WINE and try to use that to use that to install wireless-card drivers
[*]get a new wireless card (belkin seems to work best with ubuntu)
[/LIST]

wine is not going to help (maybe you meant ndiswrapper?)  The other solutions, are, well, kind of last resort.

---

### Post by neonathon on 2010-05-01
well i had a wireless card that would not be recognized by ubuntu, i downloaded wine, and installed the installation CD and now it works. I would considder WINE being help

---

### Post by P4man on 2010-05-01
> **neonathon said:**
> well i had a wireless card that would not be recognized by ubuntu, i downloaded wine, and installed the installation CD and now it works. I would considder WINE being help

Thats just.. not possible. Maybe by installing wine you pulled in updates that actually fixed it, but a windows program/driver can not enable wireless, Are you telling me your wireless doesnt work until you launch the windows software through  applications > wine > program files > whatever windows program ?

---

### Post by neonathon on 2010-05-01
yep, somehow, it works, or well, it used to work until my pcmcia slot broke

---

### Post by audit on 2010-05-01
I feel as if my problem is different than the others that are being posted.

My wireless worked until 4:00am last night;  10.04 had been installed and was in use for over a week.

No updates were performed between the time it worked and the time it did not.

Although this seems to me as if it is unrelated--my daughter who was using the computer last night ran the battery down to nothing.

I am sure I am doing something stupid.

Right now I am creating a bootable cd to see what will happen but my connection is slow and it looks like I still have another hour to wait.

New question if it doesn't work--is there anyway to downgrade to ubuntu 9.10 using apt-get?

---

### Post by P4man on 2010-05-01
> **audit said:**
> 
Although this seems to me as if it is unrelated--my daughter who was using the computer last night** ran the battery down to nothing.**


This might be a vital little clue.
This may sound silly, but right click the network manager icon, and make sure wireless is **enabled.**. Ubuntu will disable it when it runs critically low on juice.

Also make sure if you have a hardware button to enable/disable wifi that its enabled. Your laptop may do the same.


> New question if it doesn't work--is there anyway to downgrade to ubuntu 9.10 using apt-get?

No. you can not downgrade unfortunately

---

### Post by audit on 2010-05-01
my wireless now is listed enabled--originally it was not; but I cannot seem to get any wireless--there is a button on my computer but it is always blue which I assume means that it is on.

---

### Post by audit on 2010-05-01
The problem was obviously the result of my battery being run down to nothing which both disabled my wireless--also my computer disabled my wireless.

To get it to connect again I had to press the button on my computer which allowed me to enable wireless through ubuntu--and then for some reason I had to reboot?

I am still not completely sure why or what happened, but I am back. Any insight would be appreciated. 

Note to anyone who reads this don't let you battery run down to nothing.

---

### Post by P4man on 2010-05-01
I suspect its ubuntu getting confused if the laptop turns off the wifi without the button being pressed, but thats just a guess.

---

