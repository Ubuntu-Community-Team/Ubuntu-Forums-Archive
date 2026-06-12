---
title: "Lenovo wireless problems"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by Vilsad_P_P on 2014-07-03
Hi,
I am nt able to connect using wifi in my lenovo z570. it shows wifi is desabled by hardware switch. but the switch is on and i am able to use it with other distros. i am attaching the result of the command below. please advise

---

### Post by varunendra on 2014-07-04
Welcome to the forums Vilsad!

Do you have "ideapad-laptop" module loaded? Please open a terminal (Ctrl-Alt-T) and check with following command -
```
lsmod | grep idea
```
If you see "ideapad_laptop" in the outputs, try blacklisting it with the following command -
```
echo "blacklist ideapad_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..reboot and try the on/off switch again. If it still remains hardblocked, make sure the module is not loaded again by checking with the same "lsmod.." command above.

If the module is not loaded but the problem is still there, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Vilsad_P_P on 2014-07-04
hi
Thank you for assisting me
I am still having the ideapad driver loaded. below is my result for the lsmod command. 
> ideapad_laptop         18216  0 
sparse_keymap          13948  2 acer_wmi,ideapad_laptop

I have already attached the result of wireless script. please find it in my first reply.

Thanks in advance.

---

### Post by varunendra on 2014-07-04
> **Vilsad_P_P said:**
> I have already attached the result of wireless script. please find it in my first reply.
Yeah, I noticed that report. What I asked is an experimental version of that script which provides a lot more info than the regular one. That extra info may be very useful in pin-pointing the problem and troubleshoot it.

Also, please use 'Code' tags instead of 'Quote' tags for posting command outputs. It preserves the formatting of the output making it more readable. Please follow the "Use Code Tags" link in my signature to see a quick howto with screenshots, if required. :)

---

### Post by jeremy31 on 2014-07-04
> **Vilsad_P_P said:**
> hi
Thank you for assisting me
I am still having the ideapad driver loaded. below is my result for the lsmod command. 

I have already attached the result of wireless script. please find it in my first reply.

Thanks in advance.

Just why is acer_wmi in there?  ```
sudo modprobe -rv acer_wmi
```

---

### Post by Vilsad_P_P on 2014-07-04
Dear Varun,
Sorry, I thought the commands are same, Attaching the new file now. thank you for assisting me

---

### Post by Vilsad_P_P on 2014-07-04
dear jeremy,
I executed the command and restarted, still saying WIFI is disabled by hardware switch. if i slide the switch to off mode, the bluetooth is turning off, when i move it to the on mode, the bluetooth is turning on. no action on the WIFI though

---

### Post by varunendra on 2014-07-05
> **jeremy31 said:**
> Just why is acer_wmi in there?  ```
sudo modprobe -rv acer_wmi
```

Yup, I am concerned about that too. It often loads in some other models too where it is not supposed to, e.g. some Asus models, and is most often the cause of trouble. Don't know how it skipped my mind when writing my previous posts.


@Vilsad_P_P,

It seems you never blacklisted the 'ideapad_laptop' module - either you forgot or the command to blacklist it was wrong. But as jeremy31 said, lets get rid of acer_wmi first, maybe then we won't need to play with ideapad_laptop or any other stuff. Manually removing it using the 'modprobe -r' command may not work once it is loaded. These modules have to be loaded or prevented from the very beginning, when the OS is loading.

To permanently block acer_wmi from loading, please run this code in a terminal (whole line at once, better copy-paste to avoid errors) -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
..reboot, and make sure the "acer_wmi" module is not loaded -
```
lsmod | grep wmi
```
you shouldn't see "acer_wmi" in the outputs. If so, check the wifi on/off key and report back if it can be turned on now. If not, also post back with your comments, the following outputs -
```
grep blacklist /etc/modprobe.d/blacklist.conf
lsmod
```
..within 'Code' tags this time. :)

---

### Post by Vilsad_P_P on 2014-07-05
Dear Varun,
Thanks for the quick reply.

Still not working,

Below is the output for the commands i entered. 

```
vilsad@vilsad-Ideapad-Z570:~$ echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for vilsad:
blacklist acer_wmi
```

```
vilsad@vilsad-Ideapad-Z570:~$ lsmod | grep wmi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi


```

```
vilsad@vilsad-Ideapad-Z570:~$ grep blacklist /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist acer_wmi

```

```
vilsad@vilsad-Ideapad-Z570:~$ lsmod
Module                  Size  Used by
bnep                   19624  2 
rfcomm                 69160  8 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  5 
snd_hda_codec_realtek    61438  1 
rts5139               335409  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
arc4                   12608  2 
kvm                   451511  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17381  0 
serio_raw              13462  0 
snd_hda_intel          52355  5 
snd_seq_midi           13324  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath9k                 164164  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
btusb                  32412  0 
mac80211              626557  1 ath9k
bluetooth             395423  22 bnep,btusb,rfcomm
lpc_ich                21080  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
nouveau              1097199  1 
cfg80211              484040  3 ath,ath9k,mac80211
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
i915                  783703  3 
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
ttm                    85115  1 nouveau
soundcore              12680  1 snd
video                  19476  2 i915,nouveau
drm_kms_helper         53081  2 i915,nouveau
drm                   303102  7 ttm,i915,drm_kms_helper,nouveau
mac_hid                13205  0 
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
psmouse               102222  0 
r8169                  67581  0 
ahci                   25819  3 
libahci                32168  1 ahci
mii                    13934  1 r8169
 
```


I am new to linux, not yet started working with it.

---

### Post by varunendra on 2014-07-05
Assuming the above results are from after a reboot, please try blacklisting the "ideapad_laptop" module too. But before that, please try -
```
sudo rfkill unblock all
```
Then check -
```
rfkill list all
```
Does "phy" interface still appear as blocked? If yes, proceed with blacklisting -
```
echo "blacklist ideapad_laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Reboot and try the switch and the above "rfkill unblock.." command if required. Any improvement? If not, please post back -
```
grep blacklist /etc/modprobe.d/blacklist.conf
lsmod
rfkill list all
```

---

### Post by Vilsad_P_P on 2014-07-05
Dear Varun,
Thanks again,
The output was after reboot as you assumed. 

Still not working, i am posting the results for the commands.


Before Reboot :
```
rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

After reboot :

```
grep blacklist /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist acer_wmi
blacklist ideapad_laptop
```

```

lsmod
Module                  Size  Used by
btusb                  32412  0 
bnep                   19624  2 
rfcomm                 69160  8 
bluetooth             395423  22 bnep,btusb,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46207  5 
snd_hda_codec_realtek    61438  1 
rts5139               335409  0 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
snd_hda_intel          52355  5 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
arc4                   12608  2 
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   451511  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
joydev                 17381  0 
ath9k                 164164  0 
serio_raw              13462  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626557  1 ath9k
lpc_ich                21080  0 
cfg80211              484040  3 ath,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 18627  0 
mei                    82276  1 mei_me
nouveau              1097199  1 
i915                  783703  3 
mxm_wmi                13021  1 nouveau
ttm                    85115  1 nouveau
soundcore              12680  1 snd
video                  19476  2 i915,nouveau
wmi                    19177  2 mxm_wmi,nouveau
drm_kms_helper         53081  2 i915,nouveau
drm                   303102  7 ttm,i915,drm_kms_helper,nouveau
mac_hid                13205  0 
i2c_algo_bit           13413  2 i915,nouveau
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
ahci                   25819  3 
libahci                32168  1 ahci
psmouse               102222  0 
r8169                  67581  0 
mii                    13934  1 r8169


```

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


```

---

### Post by Vilsad_P_P on 2014-07-05
Dear Varun,
I got the problem resolved. 
I did as this thread istructed.
[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)

> 
Check these 3 opportunities one by one:

[LIST=1]
[*]Check in your BIOS: "Config -> Network -> Wireless LAN ..." if it is activated
[*]Hardware-reset:
[LIST]
[*]shutdown, shut off, remove the current cable and the battery
[*]Press the power button for at least 30 seconds
[*]put the battery/current back in and restart
[/LIST]


[*]BIOS default:
[LIST]
[*]Go into your BIOS with e.g. F1
[*]Reset with F9
[*]Save & Exit with F10
[*]When the Logo occurs, press the power button for ca. 10 seconds for shutting off
[*]Restart
[/LIST]
[/LIST]



Thak you so much for trying to help me. I appreciate it very much.

---

### Post by varunendra on 2014-07-05
Awesome! I was going to suggest point 2 above.. stuck firmware issue almost certainly. :)

**PS:**
To remove "ideapad_laptop" from blacklist (since it is proven now that it was not the culprit) -
```
sudo sed -i '/ideapad_laptop/ d' /etc/modprobe.d/blacklist.conf
```
That module may be required to help some other functions, probably "Fn" key combos.

---

### Post by Vilsad_P_P on 2014-07-05
Varun,
Thanks again,
Executed the command.

---

### Post by Vilsad_P_P on 2014-07-05
Dear Varun,
After restarting the laptop, the wifi was again went to previous state. i blacklisted and did the reset process to make it work again.

---

### Post by varunendra on 2014-07-05
> **Vilsad_P_P said:**
> Dear Varun,
After restarting the laptop, the wifi was again went to previous state. i blacklisted and did the reset process to make it work again.
You mean you needed to blacklist the "ideapad_laptop" module again? If so, it would be great if you can keep it on test bed for a day or two, and THEN post back that the wifi is not blocked again after the blacklisting.

I have seen only a couple of posts so far that suggest that the "ideapad_laptop" module can be problematic. Of course modules are designed to *help* something, so if one of them needs to be blocked like this, it is a bug that only users like you who have that particular hardware can and *should* report (at a bug reporting system like launchpad), so that it can get attention of the developers and be fixed.

I'd love to hear your confirmation after a reasonably long testing. Thanks for your interest in feedbacks, it definitely helps us a lot to be able to offer better help next time! :)

---

### Post by Vilsad_P_P on 2014-07-08
Dear varun,
I had to repeat the procedure several times in the last 3 days. so i think the issue is not with the ideapad driver. also my wifi seams to be a bit slow some times, i had to restart to make it fast again. what to do for that ?

---

### Post by varunendra on 2014-07-10
I would like to see a fresh report of the wireless_script ([this one]("http://ubuntuforums.org/showpost.php?p=13024222")) before suggesting anything, if at all.

---

