---
title: "RT3290 No wireless after resume from suspend 14.04"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by vignesh8 on 2015-02-08
Hello, My rt3290 wireless is not working after resuming from sleep. I tried all solutions from all forums , but none of them worked. Actually 'nmcli nm' says the state of wireless as 

'**disconnected**'

This the wireless info before sleep.

**[http://paste.ubuntu.com/10126212/](http://paste.ubuntu.com/10126212/)**

And the dump after resume from sleep

[B][http://paste.ubuntu.com/10126380](http://paste.ubuntu.com/10126380)



Please help me [/B]. Everytime I have to restart my system to get it working. And to mention,** network-manager restart, SUSPEND_MODULES = 'xxx $SUSPEND_MODULES', and other  Solutions **given in many forumns did not work.

---

### Post by chili555 on 2015-02-08
> /var/lib/dkms/rt3290sta/2.6.0.0How and why did you install that creaky antique? I'm quite surprised it even builds on a 3.18 kernel. Speaking of that, why did you need to install 3.18? 

What was wrong with the built-in driver rt2800pci that you felt the need to install its grandfather?

We are not surprised that it doesn't work properly; we are surprised that it works *at all*!

You have been busy!

---

### Post by vignesh8 on 2015-02-09
I have tried everything that i could do from installling a new kernel to changing the driver. rt2800pci is working well ofcourse but still its getting disabled after resuming from suspend. None of the fix given in net worked. What would u need me to to fix it.

---

### Post by chili555 on 2015-02-09
First, please post:```
cat /etc/pm/config.d/config
```Next, we'd like to try to decipher what, exactly, is not restarting upon resume. Please suspend and then resume. Then check. Is the driver loaded?```
lsmod | grep -e rt3 -e rt2
```Is Network Manager running?```
ps aux | grep -i network
```Is wpa_supplicant running?```
ps aux | grep -i wpa
```After resume, are there any clues in dmesg?```
dmesg | tail -n20
```You can copy and paste from the terminal into a text document, save it and reboot so you can post it on paste.ubuntu.com.

---

### Post by vignesh8 on 2015-02-09
I changed back to rt2800pci module, if rt3290sta hiurts you sir!!

and here is the new dump

[http://paste.ubuntu.com/10142844/](http://paste.ubuntu.com/10142844/)

and here are the outputs you asked.

[COLOR=#000000][FONT=Ubuntu Mono]http://paste.ubuntu.com/10142902/

[/FONT][/COLOR]
And the cat command said the fle does'nt exist.
vignesh@vignesh-HP-Pavilion-15-Notebook-PC:~$ cat /etc/pm/config.d/config
cat: /etc/pm/config.d/config: No such file or directory

---

### Post by chili555 on 2015-02-09
> [COLOR="#FF0000"]rt3290sta[/COLOR]            1174632  0 
[COLOR="#FF0000"]rt2800pci  [/COLOR]            13674  0 
rt2800mmio             21082  1 rt2800pci
rt2800lib              95583  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13661  2 rt2800pci,rt2800mmio
rt2x00lib              56113  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              697159  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              520257  2 mac80211,rt2x00lib
hp_wmi                 14017  0 
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
sparse_keymap          13890  1 hp_wmi
mxm_wmi                13021  1 nouveau
wmi                    19379  3 hp_wmi,mxm_wmi,nouveauWonderful. *BOTH* drivers are loaded. Let's fix it:```
sudo -i
echo "blacklist rt3290sta"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r rt3290sta
exit
```> vignesh@vignesh-HP-Pavilion-15-Notebook-PC:~$ cat /etc/pm/config.d/config
cat: /etc/pm/config.d/config: No such file or directory Ah, ha! Then you didn't try *everything* on the forums! We may have one more trick. Again, from a terminal:```
sudo -i
echo "SUSPEND_MODULES="rt2800pci"  >  /etc/pm/config.d/config
exit
```You may safely copy and paste these commands into the terminal.

Reboot and test.

---

### Post by vignesh8 on 2015-02-09
I did what you said exactly. Now a slight improvement. Instead of hardware disconnected, it says,

 **wifi is disabled by hardware switch**
**rfkill unblock all** doesn't work. i restarted network manager also. What should I do sir ?

---

### Post by chili555 on 2015-02-09
> **vignesh8 said:**
> I did what you said exactly. Now a slight improvement. Instead of hardware disconnected, it says,

 **wifi is disabled by hardware switch**
**rfkill unblock all** doesn't work. i restarted network manager also. What should I do sir ?Does it only become hardware blocked after suspend? Or always?

This is weird!

---

### Post by vignesh8 on 2015-02-09
Only after suspend, It says wifi is disabled by hardware switch.

---

### Post by chili555 on 2015-02-09
> **vignesh8 said:**
> Only after suspend, It says wifi is disabled by hardware switch.After suspend, did the module *hp-wmi *load as expected?```
lsmod | grep wmi
```We probably can add it to the suspend modules file we created above.

---

### Post by vignesh8 on 2015-02-09
Output of lsmod. It did load after suspend

```
vignesh@vignesh-HP-Pavilion-15-Notebook-PC:~$ lsmod | grep   wmi
hp_wmi                 14017  0 
snd_rawmidi            31197  1 snd_seq_midi
sparse_keymap          13890  1 hp_wmi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    84025  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mxm_wmi                13021  1 nouveau
wmi                    19379  3 hp_wmi,mxm_wmi,nouveau
```

---

### Post by chili555 on 2015-02-09
Please try the solution at post #8 here: [http://ubuntuforums.org/showthread.php?t=2218043&p=13000035#post13000035](http://ubuntuforums.org/showthread.php?t=2218043&p=13000035#post13000035)

---

### Post by vignesh8 on 2015-02-09
That file is already present with that content and is executable also sir! :(:frown:

---

### Post by chili555 on 2015-02-09
Studying...back a bit later.

---

