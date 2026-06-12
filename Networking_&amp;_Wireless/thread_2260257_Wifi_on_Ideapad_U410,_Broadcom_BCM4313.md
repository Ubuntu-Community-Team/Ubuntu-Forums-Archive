---
title: "Wifi on Ideapad U410, Broadcom BCM4313"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by eugen-koslowski on 2015-01-10
hey guys,

i just installed ubuntu on my ideapad u410, but wifi does not work. can somebody tell me how i can get this to work? 

thanks!!

---

### Post by jeremy31 on 2015-01-10
> **eugen-koslowski said:**
> hey guys,

i just installed ubuntu on my ideapad u410, but wifi does not work. can somebody tell me how i can get this to work? 

thanks!!

Open a terminal and enter ```
rfkill list
``` and paste results

---

### Post by eugen-koslowski on 2015-01-10
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

what does this mean?

---

### Post by jeremy31 on 2015-01-10
What wifi device ```
lspci -nnk | grep -iA2 net
```

---

### Post by jeremy31 on 2015-01-10
> **eugen-koslowski said:**
> what does this mean?
The soft blocked: yes should be able to be cleared with the FN combo to enable wireless.  However the hard block might be a driver issue

---

### Post by eugen-koslowski on 2015-01-10
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0587]
    Kernel driver in use: wl

---

### Post by jeremy31 on 2015-01-10
Try ```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-dkms
```
Reboot

---

### Post by eugen-koslowski on 2015-01-10
did it... nothing changed

---

### Post by jeremy31 on 2015-01-10
Is rfkill still showing wifi blocked?
```
rfkill list all
```
And check the driver for the wifi
```
lspci -nnk | grep -iA2 net
```

---

### Post by eugen-koslowski on 2015-01-10
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by jeremy31 on 2015-01-10
This sometimes works ```
sudo modprobe -r ideapad_laptop
```
```
sudo rfkill unblock all
```
Hopefully that will change the hard block to no, unless there is a switch or wifi is disabled in BIOS
```
rfkill list
```

---

### Post by eugen-koslowski on 2015-01-10
Soft blocked: no
    Hard blocked: yes

:/

---

### Post by jeremy31 on 2015-01-10
Found one thing in a search reboot, or shutdown and use the Novo button if you have one.  Get into BIOS and reset to defaults, then boot into Ubuntu and see if the hard block is clear.

#2 thing to check ```
lsmod | grep wmi
```

---

### Post by eugen-koslowski on 2015-01-10
i cant get into bios since i formated my windows partition and installed ubuntu :/ is there another possibility?

---

### Post by jeremy31 on 2015-01-10
Don't you have a startup screen during boot that you can press F2 or FN+F2 and access BIOS as it shouldn't depend on windows

---

### Post by eugen-koslowski on 2015-01-10
no, unfortunately this skips since the installation (the boot screen is only a few milliseconds seeable and no text appears that shows FN+f2 to enter bios`as it was before)

afrosamuraiy@afrosamuraiy-Lenovo-U410:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
afrosamuraiy@afrosamuraiy-Lenovo-U410:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


before and after pressing f7 key

is there some unofficial driver i can use?

unfortunately the option of pressing f2 or FN+f2 diappeared since the installation of ubuntu or the formatting of my windows partition. with the novo key i can only enter the startup manager (which just starts ubuntu as usual), enter the recovery mode, and enter the boot menu.

---

### Post by Hadaka on 2015-01-11
Hi, Fn/F7 is the key combo for your wifi please press ONE time
and do and post,,
```
rfkill list all
#press the fn/f7 one time
rfkill list all
```
thanks

---

### Post by jeremy31 on 2015-01-11
Show the results of ```
lsmod | grep wmi
``` as there is a slight chance another module is involved that shouldn't be there

---

### Post by eugen-koslowski on 2015-01-11
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69322  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi



i dont know what you mean whith a module that shouldn't be there?

---

### Post by jeremy31 on 2015-01-11
> **eugen-koslowski said:**
> mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69322  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi



i dont know what you mean whith a module that shouldn't be there?

Occasionally we will see a module for acer or whatever loaded on a different laptop and it can cause issues, however that doesn't seem to be the case.
Blacklisting the ideapad_laptop module and rebooting might have a chance to work ```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad-laptop.conf
``` reboot, check rfkill, and see if ```
sudo rfkill unblock all
``` will clear a hard block if it is there

---

### Post by eugen-koslowski on 2015-01-11
the rfkill after blacklisting:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

---

### Post by jeremy31 on 2015-01-11
Please go here [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug) and file a bug report as I don't know what to do in this situation.  Usually blacklisting ideapad_laptop works on the Lenovo models with hard block.  There may be a patch in the new kernel but I doubt if your wifi driver will work with it as it usually needs a patch to work with newer kernels.

Have you tried a different version of Ubuntu, currently 12.04, 14.04, and 14.10 are supported

---

### Post by eugen-koslowski on 2015-01-12
thank you nevertheless for your help!!!

sorry for my question, but how does this work? how can i report this bug? i cannot do anything with your link :(

---

### Post by jeremy31 on 2015-01-21
Try here: [https://bugs.launchpad.net/ubuntu/+source/linux/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

---

### Post by eugen-koslowski on 2015-01-24
i reported a bug, but after they suggested me to install the new kernel there is no process. i dont know whether i did something wrong or not - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413214](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413214)

---

### Post by jeremy31 on 2015-01-24
> **eugen-koslowski said:**
> i reported a bug, but after they suggested me to install the new kernel there is no process. i dont know whether i did something wrong or not - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413214](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413214)

Probably just have to be patient.  It wouldn't surprise me if the bcmwl-kernel-source failed to build with the 3.19 kernel

---

### Post by Eugen_Koslowski on 2015-02-11
I have installed elementary os now and hardblock changed to "no" now, but still no access to wifi. there is no scan for wifi connections.

---

