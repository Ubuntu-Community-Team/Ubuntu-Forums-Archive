---
title: "Lost Sound after update just now"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by iamgeniusrnti on 2009-12-11
ARRGG!!!!!  To the Ubuntu gods of Linux... PLEASE STOP TAKING AWAY MY SOUND PLEASE!!!!!!!  I BEG YOU PLEASE STOP!!!!  I just want to listen to my mp3s (which I paid for on Amazon BTW) in peace!  

Accepted updates mainly to KDE environment this morning.  Lost sound.  Last time I lost sound I had to recompile my alsa drivers, run a bunch of commands... took hours... days like these make me wish I could reinstall Windows...

Output of lsmod:
genius@K-Netbook:~$ lsmod                        
Module                  Size  Used by            
nls_iso8859_1           3740  1                  
nls_cp437               5372  1                  
vfat                   10716  1                  
fat                    51452  1 vfat             
usb_storage            52608  1                  
binfmt_misc             8356  1                  
ppdev                   6688  0                  
snd_hda_codec_realtek   202336  1                
snd_hda_intel          26624  3                  
snd_hda_codec          78300  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec                      
snd_pcm_oss            37312  0                                    
snd_mixer_oss          16188  1 snd_pcm_oss                        
snd_pcm                75232  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1660  2                                        
snd_seq_dummy           2752  0                                        
snd_seq_oss            29312  0                                        
ecb                     2524  2                                        
joydev                 10272  0                                        
snd_seq_midi            6624  0                                        
snd_rawmidi            22208  1 snd_seq_midi                           
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
iptable_filter          3100  0                                        
ath5k                 124580  0                                        
ip_tables              11692  1 iptable_filter                         
snd_seq                51120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables                                                
snd_timer              21540  2 snd_pcm,snd_seq                                          
mac80211              181076  1 ath5k
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath                     8060  1 ath5k
snd                    60932  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
cfg80211               93052  3 ath5k,mac80211,ath
uvcvideo               59112  0
psmouse                56500  0
videodev               36736  1 uvcvideo
lp                      8964  0
led_class               4096  1 ath5k
atl1c                  31136  0
v4l1_compat            14496  2 uvcvideo,videodev
serio_raw               5280  0
parport                35340  2 ppdev,lp
dm_raid45              84228  0
xor                    15620  1 dm_raid45
fbcon                  36640  72
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221672  2
drm                   160224  2 i915
i2c_algo_bit            5760  1 i915
intel_agp              27748  2 i915
agpgart                35020  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video




sound-test produces no sound and alsa-mixer is unmuted however everytime I rebooted I have always had to unmute my audio and select the audio card.

Help?

---

### Post by iamgeniusrnti on 2009-12-11
Well the Gods punished me.  I went to uninstall alsa and the Ubuntu Gods saw me trying to fix my sound again and took away my KDE.
 
Time to reinstall.

---

### Post by iamgeniusrnti on 2009-12-11
OK... I didn't do a complete uninstall--I simply went into the prompt and did a apt-get install kde-desktop.  Then rebooted and got a black desktop.  So I installed Gnome and I am back to life with sound.

Now I have to do the unthinkable, install each update one at a time until I lose my sound again.  Then we will know once and for all which update the Gods of Ubuntu are handing out and screwing us Acer One owners.

---

