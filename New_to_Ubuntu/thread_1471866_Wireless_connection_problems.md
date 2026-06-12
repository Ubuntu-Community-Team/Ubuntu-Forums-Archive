---
title: "Wireless connection problems"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by browny254 on 2010-05-03
Hi Im using the kubuntu netbook remix on an acer aspire one zg5 and am having lots of problems with wireless connections.

Whats happening is that my wireless is dropping out after about 2-30 minutes, but still shows as connected, so therefore it is not automatically reconnecting. All I have to do it click on my network in knetworkmanager to reconnect and all is fine again until the next drop out, but after about 4 or 5 times doing this it refuses to reconnect and just keeps coming up with the screen to enter the network password. 

This is where I am getting really stuck though, because no matter how many reboots I do, I cant reconnect to the network - last time after 14 reboots and 90 minutes it reconnected again with all that I did between restarts was try different combinations of booting with my wireless disabled or enabled and with a connection already set up in knetworkmanager or not. None of these did anything and it just happened one time I was able to connect again.

At the same time, if I already have a connection set up, I am unable to create a new connection (there are a couple of unsecured wireless networks I can see). If I try connecting to one of these networks the network set up screen just uses all the information about the original network no matter what I enter and it doesnt show up in the list of networks once created anyway. If I delete all networks, reboot and try connecting to one of these networks as my first created network that doesnt connect either.

I have just installed wicd and since restarting to enable that to work, have not been able to connect - that is saying I am entering a bad password, which is not true, and for the unsecured networks is saying unable to get IP address.


I first had this problem using 9.10 and was unable to resolve it, but by enabling the backports something partially fixed it where I was able to stay connected from about 30 minutes to 12 hours or so rather than just minutes beforehand, but since upgrading to 10.04 its back to having connections last only minutes again.

I cant figure out whats causing the disconnect or any pattern to what I am doing that may cause it so Im not sure what other info I can provide...

I didnt have any problems with windows xp, which I have since removed and my housemate has no problems on his windows xp pc either (im using that now) also my old laptop was using kubuntu 9.10 with no problems either so the problem seems to be something about the netbook remix I guess.

Any help or workarounds would be really appreciated.
Cheers.

---

### Post by browny254 on 2010-05-03
Just a follow up...I created a wired connection and it works perfectly, so it is definatley something to do with wireless.

---

### Post by GSF1200S on 2010-05-03
Can you please post the results of:
```
lsmod
```
here for us?

Your wireless card should use the ath5k driver, but it can also use the madwifi drivers which may work better for you. Post the above results and well go from there..

---

### Post by udippel on 2010-05-04
> **browny254 said:**
> Hi Im using the kubuntu netbook remix on an acer aspire one zg5 and am having lots of problems with wireless connections.

Whats happening is that my wireless is dropping out after about 2-30 minutes, but still shows as connected, so therefore it is not automatically reconnecting. All I have to do it click on my network in knetworkmanager to reconnect and all is fine again until the next drop out, but after about 4 or 5 times doing this it refuses to reconnect and just keeps coming up with the screen to enter the network password. 



Don't worry, it is not your fault. I've seen exactly the same since I put 10.04 netbook remix into action here; on an Acer Aspire One (L110).
Only, until half an hour ago I put the blame squarlely on Tomato (WAP), because it takes down ALL wireless links. For the last half hour I've been sitting next to my trusted m0nowall in my office, and here the other links are unaffected; only the netbook brings its own link down once it start transferring somewhat larger amounts of data.

Someone should urgently file a bug. I guess many people are affected!

Uwe

---

### Post by browny254 on 2010-05-04
> **GSF1200S said:**
> Can you please post the results of:
```
lsmod
```
here for us?

Your wireless card should use the ath5k driver, but it can also use the madwifi drivers which may work better for you. Post the above results and well go from there..

Looks like it is the ath5k...I've posted everything from lsmod because I'm not sure what is helpful from it.
```
$ lsmod
Module                  Size  Used by
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi                                           
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  2 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath5k                 121792  0 
acerhdf                 6691  0 
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
drm                   162471  3 i915,drm_kms_helper
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
intel_agp              24177  2 i915
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
cfg80211              126485  3 ath5k,mac80211,ath
i2c_algo_bit            5028  1 i915
led_class               2864  1 ath5k
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  33884  0 
mii                     4381  1 r8169
```

I still haven't been able to connect with wireless since my original post so I guess I was just getting lucky in being able to reconnect previously...

---

### Post by GSF1200S on 2010-05-04
**Before doing any of the below, open a terminal and do:
```
sudo apt-get update
```
and then go to System>Administration>Hardware Drivers. Do you see any options for your wireless card like perhaps a different one that you dont currently have enabled? If not, proceed.. Obviously, you will need an internet connection for some of it- do you have a router you can plug into temporarily?

Open a terminal and type:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add the following line to it:
```
blacklist ath5k
```

Then go to this link and download the tarball there:
[http://madwifi-project.org/](http://madwifi-project.org/)

Place the tarball in your /home/username folder. Then, right click on it and click "Extract Here" in the context menu. Open a terminal and type:
```
cd /home/username/madwifi-0.9.4
```
where username is whatever your login name is.

Then ensure you have all the packages necessary to build/use the drivers:
```
sudo apt-get install build-essential hal
```

Finally, install the driver:
```
make
sudo make install
sudo make clean
```
If you get errors when you try run the above commands (make is the one that gives the most trouble), then post the results here in a set of code tags (the # symbol when you make a post).

After you do this and reboot, see if your wireless works- I dont know if the driver will automatically add modules to be loaded, because I dont have an atheros chipset. If your wireless doesnt work, try each of the following one at a time and then see if you are able to connect to a network with your network manager:
```
sudo modprobe ath_pci
```
and stop to test your wireless with network manager. If nothing, then:
```
sudo rmmod ath_pci
```
to unmount that module. Then try:
```
sudo modprobe ath9k
```
and test your wireless again. Report back with whatever happens. I cant guarantee this will work, but without a machine that has an atheros chipset, this is the best I can do.

---

### Post by udippel on 2010-05-04
Thanks, GSF1200S, but that's not the solution. Ubuntu has been supporting the ath5k for the last versions, and officially so. If there happens to be a problem, the user in 2010 should not go back to the solutions of the last millenium: command line, compile, try, try another. Please, don't forget that the netbook remix 9.10 was running splendidly on that same hardware.
We must not regress like what you propose; without any criticism to your well-meant proposal.

Uwe

---

### Post by GSF1200S on 2010-05-04
> **udippel said:**
> Thanks, GSF1200S, but that's not the solution. Ubuntu has been supporting the ath5k for the last versions, and officially so. If there happens to be a problem, the user in 2010 should not go back to the solutions of the last millenium: command line, compile, try, try another. Please, don't forget that the netbook remix 9.10 was running splendidly on that same hardware.
We must not regress like what you propose; without any criticism to your well-meant proposal.

Uwe

If the "solution of the last millennium" fixes my wireless connection, then im going to use it. I didnt say it was a perfect solution, or that it was convenient, or hell even that it would work. It was merely an option to try. What good does having the "officially supported" ath5k module do if in this particular case it doesnt give one an internet connection (although many others are not having issues with the driver)?

If netbook remix 9.10 runs splendidly on that hardware, then run 9.10 UNE on the netbook. If one wants wireless access and 10.04 and the "officially supported" method doesnt work, then we need to try other approaches (and hopefully someone familiar with atheros chipsets will be able to suggest some new approaches).

---

### Post by udippel on 2010-05-04
> **GSF1200S said:**
> It was merely an option to try.
 

And I'm grateful for it! And I do hope someone else might be able to use it. Just make a search, and you'll find a bunch of people reporting the same issue in the last few days: Disconnecting within a few minutes.

> **GSF1200S said:**
> 
If netbook remix 9.10 runs splendidly on that hardware, then run 9.10 UNE on the netbook. If one wants wireless access and 10.04 and the "officially supported" method doesnt work, then we need to try other approaches (and hopefully someone familiar with atheros chipsets will be able to suggest some new approaches).

Yep. But 10.04 is seriously a fine OS, and looks not any less good than a Mac. I am so happy with it ... .
Anyway, I have been digging deeper, and hope for some responsible developer to rectify the situation.

Again, of course, thanks. I'm simply too tried for 'playing' around with it; and IMHO, the times of the BBSes is over. Ubuntu promises this and that, and I expect them to keep their word.

Uwe

---

### Post by xumuk37 on 2010-05-04
```
lspci|grep -i wireless
``` and then just reinstall the drivers ```
sudo apt-get install --reinstall ath5 ath9k
``` or whatever appears next to Wireless...

---

### Post by browny254 on 2010-05-05
[QUOTE=GSF1200S]
Finally, install the driver:
```
make
sudo make install
sudo make clean
```
If you get errors when you try run the above commands (make is the one that gives the most trouble), then post the results here in a set of code tags (the # symbol when you make a post).
[/QUOTE]

Thanks for the replies, had to wait for my housemate to go to work because the router is in his room.

Im getting an error during the make stage as you said...

```
andrew@Acer:~/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.32-21-generic/build SUBDIRS=/home/andrew/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
  CC [M]  /home/andrew/madwifi-0.9.4/ath/if_ath.o
In file included from /home/andrew/madwifi-0.9.4/ath/../net80211/ieee80211_monitor.h:45,
                 from /home/andrew/madwifi-0.9.4/ath/if_ath.c:71:
/home/andrew/madwifi-0.9.4/ath/../ath/if_athvar.h:98: error: conflicting types for 'irqreturn_t'
include/linux/irqreturn.h:16: note: previous declaration of 'irqreturn_t' was here
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_attach':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:402: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:678: error: 'struct net_device' has no member named 'open'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:679: error: 'struct net_device' has no member named 'stop'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:680: error: 'struct net_device' has no member named 'hard_start_xmit'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:681: error: 'struct net_device' has no member named 'tx_timeout'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:683: error: 'struct net_device' has no member named 'set_multicast_list'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:684: error: 'struct net_device' has no member named 'do_ioctl'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:685: error: 'struct net_device' has no member named 'get_stats'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:686: error: 'struct net_device' has no member named 'set_mac_address'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:687: error: 'struct net_device' has no member named 'change_mtu'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_detach':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:958: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1005: error: 'struct net_device' has no member named 'stop'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_create':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1014: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1084: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_vap_delete':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1248: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_suspend':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1350: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_resume':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1359: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_intr':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1652: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bmiss_tasklet':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1843: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_init':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:1886: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop_locked':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2014: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_stop':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2078: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_reset':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2182: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_startraw':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2343: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_hardstart':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2558: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mgtstart':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:2875: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_alloc':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3237: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_delete':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3304: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_set':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3380: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_begin':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3395: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_key_update_end':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3416: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mode_init':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3504: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_updateslot':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3555: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_config':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3585: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_beacon_dturbo_update':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3633: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_turbo_switch_mode':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:3776: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_bstuck_tasklet':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:4368: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_alloc':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:4820: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_cleanup':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:4855: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_node_free':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:4909: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_capture':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:5404: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_capture':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:5437: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_recv_mgmt':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:5502: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rx_tasklet':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:5574: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_start':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:6013: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_grppoll_stop':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:6226: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_wme_update':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:6441: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_uapsd_flush':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:6460: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_start':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:6655: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:7495: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet_q0123':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:7516: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_tasklet':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:7551: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_tx_timeout':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:7574: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_calibrate':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:7937: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_start':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8003: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_scan_end':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8023: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_channel':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8041: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_coverageclass':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8057: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_mhz2ieee':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8067: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newstate':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8082: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_stationkey':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8471: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_newassoc':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8631: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getchannels':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8662: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_xr_rate_setup':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8832: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_setup_subrates':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8861: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rate_setup':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:8904: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_getstats':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9141: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_set_mac_address':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9164: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_change_mtu':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9196: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_ioctl':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9283: error: 'struct net_device' has no member named 'priv'
cc1: warnings being treated as errors
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_sysctl_halparam':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9370: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9370: error: too many arguments to function 'proc_dointvec'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9562: error: passing argument 5 of 'proc_dointvec' from incompatible pointer type
include/linux/sysctl.h:985: note: expected 'loff_t *' but argument is of type 'size_t *'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9562: error: too many arguments to function 'proc_dointvec'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: At top level:
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9574: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9580: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9586: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9592: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9598: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9604: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9610: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9616: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9623: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9630: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9636: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9642: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9648: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9654: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9660: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9667: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9673: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9680: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9686: error: initialization from incompatible pointer type
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_announce':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9779: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c: In function 'ath_rcv_dev_event':
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9926: error: 'struct net_device' has no member named 'priv'
/home/andrew/madwifi-0.9.4/ath/if_ath.c:9928: error: 'struct net_device' has no member named 'open'
make[3]: *** [/home/andrew/madwifi-0.9.4/ath/if_ath.o] Error 1
make[2]: *** [/home/andrew/madwifi-0.9.4/ath] Error 2
make[1]: *** [_module_/home/andrew/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [modules] Error 2

```

---

### Post by browny254 on 2010-05-05
Ok, I couldn't build it because I have a new kernal (I think), but I downloaded this one [http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz) and was able to build and install with no errors, but Im not getting any wifi at all after restarting.

I tried sudo modprobe ath_pci and ath9k and got nothing. So I have removed ath5k from the blacklist and restarted and have wifi again, but cant connect still.

Does this mean that I have made a mistake with installing madwifi?

---

### Post by GSF1200S on 2010-05-05
> **browny254 said:**
> Ok, I couldn't build it because I have a new kernal (I think), but I downloaded this one [http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz) and was able to build and install with no errors, but Im not getting any wifi at all after restarting.

I tried sudo modprobe ath_pci and ath9k and got nothing. So I have removed ath5k from the blacklist and restarted and have wifi again, but cant connect still.

Does this mean that I have made a mistake with installing madwifi?

Ehhh.. If it didnt work for you, but you did manage to install it, there is nothing more you can do with Madwifi. Rereading your first post, you stated you managed to get it working using backports on 9.10. Please post the results of:
```
lspci
```
so that we can see what wireless chipset you have. Then, I will try to find out what drivers it used on 9.04 (as the backports for 9.10 should be from 9.04) and see if I can find which deb needs to be installed. Hopefully, we wont run into any dependency issues. It also depends on the kernel and whether or not it will support the driver.

---

### Post by browny254 on 2010-05-05
[QUOTE=GSF1200S]Ehhh.. If it didnt work for you, but you did manage to install it, there is nothing more you can do with Madwifi.[/Quote]
Hmm thats a shame. 

> 
Rereading your first post, you stated you managed to get it working using backports on 9.10. Please post the results of:
```
lspci
```
so that we can see what wireless chipset you have. Then, I will try to find out what drivers it used on 9.04 (as the backports for 9.10 should be from 9.04) and see if I can find which deb needs to be installed. Hopefully, we wont run into any dependency issues. It also depends on the kernel and whether or not it will support the driver.

It didnt work 100% on 9.10 with the backports, just the drop outs were less frequent, only a couple a day rather than a couple an hour.

Anyway,
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

---

### Post by GSF1200S on 2010-05-06
> **browny254 said:**
> Hmm thats a shame. 



It didnt work 100% on 9.10 with the backports, just the drop outs were less frequent, only a couple a day rather than a couple an hour.

Anyway,
```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

While I search for this, do you have the windows driver for this wireless card? We may be able to use ndiswrapper to make the wireless card work... Ill edit this post with any info I find on the backports..

**EDIT** Try the following package:
> sudo apt-get install linux-backports-modules-wireless-lucid-generic
I dont really think its going to help, but thats all I can find on backports. I think your best bet is to try ndiswrapper... Backports are packages that are on a newer release ported back to an older release, so I dont know what this package does.

---

### Post by browny254 on 2010-05-06
I dont have a Windows driver, but have found [http://download.cnet.com/WLan-Driver-Atheros-802-11abg-4-2-2-7-zip/3000-2112_4-162469.html](http://download.cnet.com/WLan-Driver-Atheros-802-11abg-4-2-2-7-zip/3000-2112_4-162469.html) which I guess is it.

How hard is ndiswrapper to set up? ie will I need to be coached through it or should it be fairly straight forward?

I got to head out for an hour or 2 but I will give it a try as soon as Im back. Thanks for all your help so far anyway.

---

### Post by GSF1200S on 2010-05-06
> **browny254 said:**
> I dont have a Windows driver, but have found [http://download.cnet.com/WLan-Driver-Atheros-802-11abg-4-2-2-7-zip/3000-2112_4-162469.html](http://download.cnet.com/WLan-Driver-Atheros-802-11abg-4-2-2-7-zip/3000-2112_4-162469.html) which I guess is it.

How hard is ndiswrapper to set up? ie will I need to be coached through it or should it be fairly straight forward?

I got to head out for an hour or 2 but I will give it a try as soon as Im back. Thanks for all your help so far anyway.

I would check out the package I posted above first to see if it works.

Its not too bad (ndiswrapper). First, install ndiswrapper:
```
sudo apt-get install ndiswrapper-utils-1.9
```
Next, you need the .inf driver for your card. You do:
```
sudo ndiswrapper -i driver.inf
```
(or whatever its called)
Then you do:
```
sudo ndiswrapper -l
```
and see if it lists the driver and that the hardware is present.
```
sudo depmod -a
sudo modprobe ndiswrapper
```
and then restart the computer. It worked for me along time ago.. Tell me if this gives you any issues...

**EDIT** Hmmm, another guy with a similar chipset and madwifi worked for him:
[http://ubuntuforums.org/showthread.php?t=1469799]("http://ubuntuforums.org/showthread.php?t=1469799")

He says it worked using a link here:
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
This link does some things I did not have you do- perhaps you could try it and see if it works.

---

