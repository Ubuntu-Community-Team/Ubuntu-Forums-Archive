---
title: "Intel Centrino Advanced-N 6235 / Asus Zenbook Prime ux31a"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by Christoph_Lee on 2013-09-25
Hello,  I've recently done a fresh install of ubuntu 12.04 on a new laptop (asus zenbook prime ux31a).  I'm able to connect to the internet using wifi, but usually it takes a good 10-15 minutes of repeated attempts to connect before the network manager makes the connection.  I've uninstalled the default network manager and am using wicd right now, but it has the same issues.  It basically gets indefinitely hung up on the "Obtaining IP address..." step.  I've searched around online for a solution but haven't been able to find one yet.

If someone could point me to a solution or help out I'd appreciate it.

Here is some info that may be useful:

```

$ iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"hide yo kids, hide yo wifi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:01:DF:17:EA   
          Bit Rate=117 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4531  Invalid misc:1888   Missed beacon:0

```

```

$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi

```

```

$ lsmod
Module                 Size  Used by
snd_hda_codec_hdmi     37407  1 
snd_hda_codec_realtek    79916  1 
joydev                 17613  0 
btusb                  22431  0 
uvcvideo               82214  0 
videobuf2_core         40785  1 uvcvideo
videodev              130053  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55495  1 
ablk_helper            13597  1 aesni_intel
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
rts5139               351018  0 
aes_x86_64             17255  1 aesni_intel
xts                    12922  1 aesni_intel
gf128mul               14951  2 lrw,xts
asus_nb_wmi            12854  0 
asus_wmi               24581  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
arc4                   12573  2 
iwldvm                249093  0 
mac80211              630977  1 iwldvm
snd_hda_intel          44339  3 
snd_hda_codec         141761  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwlwifi               183603  1 iwldvm
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
microcode              23017  0 
psmouse                97873  0 
serio_raw              13215  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
mac_hid                13253  0 
cfg80211              525244  3 iwldvm,mac80211,iwlwifi
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19256  1 asus_wmi
i915                  620419  4 
lpc_ich                17144  0 
snd                    69533  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bnep                   18258  2 
rfcomm                 47864  12 
drm_kms_helper         49597  1 i915
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
drm                   287564  5 i915,drm_kms_helper
bluetooth             247024  24 btusb,bnep,rfcomm
i2c_algo_bit           13564  1 i915
video                  19652  2 asus_wmi,i915
mei                    41820  0 
parport_pc             28284  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   25879  2 
libahci                31606  1 ahci

```

---

### Post by Christoph_Lee on 2013-09-25
I should also mention that the wireless network I'm using works fine with my old laptop, it connects immediately every time.  Also, I've noticed that on the new laptop the screen will sometimes switch to terminal mode (like ctrl+alt+f7) and display a bunch of messages which look something like:

[http://i.imgur.com/OvZpZy4.jpg](http://i.imgur.com/OvZpZy4.jpg)

---

### Post by wildmanne39 on 2013-09-28
Hi, the first thing to do is take the spaces and special characters like commas out of your network name then copy and paste this command in the terminal (ctrl+alt+t) one line at a time:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
if the issue is not resolved after you do the above please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz or netinfo.txt in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz or netinfo.txt file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2013-09-28
Please use thumbnails or create an url for your images because many people have slow connections and it is very hard for them to load pages with large images.
Thanks

---

### Post by Christoph_Lee on 2013-09-29
Sorry about the image.  Disabling 11n doesn't seem to have fixed the problem.  I've attached the tar file.  Thanks.

---

### Post by varunendra on 2013-10-02
> **Christoph_Lee said:**
> Sorry about the image.  Disabling 11n doesn't seem to have fixed the problem.  I've attached the tar file.  Thanks.

Please try a few things, in the order as suggested -

Please first try changing the encryption type in the router from WPA/WPA2 mixed mode to pure **WPA2-PSK (AES)**. No mixed mode, no TKIP.

If the above alone doesn't make any difference, try two new parameters besides what Wild Man already suggested -
```
sudo sed -i 's/options.*/& swcrypto=1 bt_coex_active=N/' /etc/modprobe.d/iwlwifi.conf
```
This will modify your already existing conf file to contain two new parameters.

After this, remove and reload the drivers for the above to take effect -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```

Hopefully, it should improve the connectivity. If not, please also try changing the channel in your router from 6 to 1 or 11.

**PS:**
Almost forgot, you have power management On on the wireless interface. Please try disabling it before any of the changes above -
```
sudo iwconfig wlan0 power off
```
Leave it off even if it doesn't help.

Given the kind of problem you are having, I'm most hopeful with the change in encryption type combined with the swcrypto=1 parameter.

---

### Post by Christoph_Lee on 2013-10-06
Thank you very much for your suggestions!  Turning power management off did not seem to make a difference.  After I made the change to iwlwifi.conf, things seemed to improve and I did not have any trouble connecting wirelesly to the internet for about 2 days.  However, it is now acting pretty much like it was before.. I get stuck on "obtaining ip address" and then it just fails to connect.  Every so often I'll still get involuntarily switched into terminal mode with errors similar to in the image I attached previously.  I tried switching the router to channel 11, though that doesn't seem to have helped.

Christoph

---

### Post by varunendra on 2013-10-07
Please post back the fresh report of wireless_script, Plus, the output of -
```
ifconfig
dmesg | grep 80211
```

---

### Post by Christoph_Lee on 2013-10-07
I reran the wireless_script and attached the tar file.

Also:

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 9c:eb:e8:0d:b4:6f  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102704 errors:42 dropped:0 overruns:0 frame:3
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101259881 (101.2 MB)  TX bytes:11496191 (11.4 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:5868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:589650 (589.6 KB)  TX bytes:589650 (589.6 KB)

```

```

$ dmesg | grep 80211
[    1.700426] cfg80211: Calling CRDA to update world regulatory domain
[    1.803651] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   20.745305] cfg80211: Calling CRDA for country: US
[   72.214656] cfg80211: Calling CRDA to update world regulatory domain
[  124.144792] cfg80211: Calling CRDA to update world regulatory domain
[  177.092911] cfg80211: Calling CRDA for country: US
[  229.023410] cfg80211: Calling CRDA to update world regulatory domain
[  578.612699] cfg80211: Calling CRDA for country: US
[  630.548027] cfg80211: Calling CRDA to update world regulatory domain
[  682.482027] cfg80211: Calling CRDA to update world regulatory domain
[  734.419849] cfg80211: Calling CRDA for country: US
[ 1083.006753] cfg80211: Calling CRDA to update world regulatory domain
[ 1134.943624] cfg80211: Calling CRDA to update world regulatory domain
[ 1186.886541] cfg80211: Calling CRDA for country: US
[ 1239.810533] cfg80211: Calling CRDA to update world regulatory domain
[ 1542.936487] cfg80211: Calling CRDA for country: US
[ 1554.247206] cfg80211: Calling CRDA to update world regulatory domain
[ 1862.418539] cfg80211: Calling CRDA to update world regulatory domain

```

Christoph

---

### Post by varunendra on 2013-10-07
The power management is still On. Did it turn off the last time? Sometimes it doesn't. So please run the command again -
```
sudo iwconfig wlan0 power off
```
Then check -
```
iwconfig
```
Does "Power Management" appears to be turned off? If not, post back and we may try other things to turn it off.

If it is turned off, also check if TX power increased or not (in the same iwconfig output above, currently it is 15 dBm). If not, try this -
```
sudo iwconfig wlan0 txpower 20
```
Then check "iwconfig" again. Did it change?

---

### Post by Christoph_Lee on 2013-10-07
Yes I did turn power management off before.  Just did it again.  Here is the new info:

```

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



```

```

$ sudo iwconfig wlan0 txpower 20
$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



```

So Tx-Power stayed at 15.

Christoph

---

### Post by Christoph_Lee on 2013-10-08
Looks like power management gets turned back on again when I reboot.

Christoph

---

### Post by varunendra on 2013-10-10
> **Christoph_Lee said:**
> Looks like power management gets turned back on again when I reboot.

Christoph

Sorry for not being able to get back to you, kinda stuck in something..

Please try creating a blank file in /etc/pm/power.d to disable the default script in /usr/lib/pm-utils/power.d directory -
```
sudo touch /etc/pm/power.d/wireless
```

Then turn off the power management -
```
sudo iwconfig wlan0 power off
```
..recheck to make sure it turned off, then reboot. Does it still revert to be turned on? If yes, please try -

```
echo "iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```
Now reboot and see if it remains turned off.

If not, please download this version of wireless_script (it is slightly more verbose) : [http://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](http://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) , run it and post back the fresh report it creates.

Along with the report, please also post the output of -
```
grep -R [[:alnum:]] /sys/module/iwlwifi/parameters
```

---

### Post by Christoph_Lee on 2013-10-13
So after I created the empty file "wireless" I have been having no issues connecting for the past 2 days or so.  Power management stays off at all times now from what I can tell.  I'd like to see if any issues return over the next few days (like happened before), but for the moment it seems to be working! Thanks!

Christoph

---

### Post by varunendra on 2013-10-13
> **Christoph_Lee said:**
> So after I created the empty file "wireless" I have been having no issues connecting for the past 2 days or so.  Power management stays off at all times now from what I can tell.  I'd like to see if any issues return over the next few days (like happened before), but for the moment it seems to be working!

That was probably the last arrow in my quiver, not sure if I'd be able to find more, so let's keep the fingers crossed ! ;)

---

### Post by jamaas on 2014-07-11
After months of struggle this has fixed my ASUS ux31a!  Thanks.  One of the problems with mine might have also been the virgin media super hub 2 which automatically hyphonates the name of the network.  I changed the broadcast name, removed the hyphen and that seems to help as well.  Strange, it should be the same as any other character!

J

---

