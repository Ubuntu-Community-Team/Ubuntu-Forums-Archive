---
title: "wireless doesn't work on HP Pavilion DV6000 (ubuntu 12.04)"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by Claudia_Fiorenza on 2013-09-06
Hi! 
I have ubuntu since at least one year and till yesterday my wifi worked properly. then it stopped working and i am using the wired connection. I tried to fix it bymyself reading some other's posts but i only ended up making other problems and i had to spend all the day fixing them. (at one point i must have written the wrong line in the terminal that it caused a low resolution of my desktop and it freezed every 2 minutes...NOW EVERYTHING WORKS AGAIN AND FASTER THAN BEFORE BUT MY WIFI STILL DOESNT WORK).

please guide me step by step with the relosution of this problem and try to explain it very easy :)

claudia

---

### Post by wildmanne39 on 2013-09-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2013-09-06
*Thread moved to **Networking & Wireless**.*

---

### Post by Claudia_Fiorenza on 2013-09-07
since i have ethernet, i used the command and i got 2 files: the one you said and anoter one named wireless_script(it can be read or run)

i only menaged to attach the file wireless-info.txt

---

### Post by praseodym on 2013-09-07
Hi,

your card is off ("Txpower = off"). Any button/switch/key/key combination? Tried
```

sudo rfkill unblock all
```
Please show afterwards:
```

rfkill list
lsmod
```
Maybe resetting your BIOS to default settings?

---

### Post by Claudia_Fiorenza on 2013-09-07
please note that i run these command with the wifi switcher off..cus it kept interfiering with my wired connection
--------------------------
------------------------------

claudia@claudia-HP-Pavilion-dv6700-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
claudia@claudia-HP-Pavilion-dv6700-Notebook-PC:~$ lsmod
Module                  Size  Used by
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   174313  1 
arc4                   12473  2 
snd_hda_intel          32719  3 
iwl3945                73186  0 
binfmt_misc            17292  1 
iwl_legacy             71187  1 iwl3945
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
mac80211              436493  2 iwl3945,iwl_legacy
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                86546  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
cfg80211              178877  3 iwl3945,iwl_legacy,mac80211
r852                   17901  0 
sm_common              16772  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
r592                   17808  0 
memstick               15857  1 r592
nvidia              10286823  53 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21784  1 nand_bch
nand_ecc               13105  1 nand
video                  19115  0 
wmi                    18744  1 hp_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  56396  0

--------------------------------------------
---------------------------------------------
how can i reset my BIOS to default settings?

---

### Post by praseodym on 2013-09-07
Reboot, and check the display, it should read sth. like "Press DEL for entering SETUP". In your BIOS there should be a key like F7 or F9 for loading default settings.

F10 is "Save&Exit"

---

### Post by Claudia_Fiorenza on 2013-09-07
rebooted, then "press F10 for entering setup", then in my BIOS i found in the last "tab" on the right side of the display F9 for loadong default settings, i pressed it and then i pushed "enter" to confirm, then i pressed F10 to save changes and exit, and finally pressend "enter" to confirm save&exit.

it restarted and now i  see no changes at all. :( WIFI STILL DOESN'T WORK..

what did I do wrong?

---

### Post by praseodym on 2013-09-07
You did nothing wrong.

Try to press the keys permanently or repeatedly during boot-up.

Can you change the boot-mode to "Networking" on #1 and the OS on #2 in the BIOS?

---

### Post by Claudia_Fiorenza on 2013-09-07
i restarted the pc and pressed F10, then in the BIOS  i looked for something called networking with the option of changing the number to 1...and the same goes for OS

i'm lost. actually i couldn't find anything with some numbers as options..can you explaint it better, please?

so sorry for being so dumbie!

---

### Post by praseodym on 2013-09-07
Try a reinstallation of the kernel
```

sudo apt-get install --reinstall linux-image-$(uname -r)
```
Reboot.

---

### Post by Claudia_Fiorenza on 2013-09-08
done it. rebooted and switched on the wifi: STILL NOTHING. the pc froze and reported an internal error and i took a screen shot of the report details since i couldnt select the lines and save them. in total are 13 screenshots. do you want me to look for anything in particular written in it and attach the specific shot?

---

### Post by praseodym on 2013-09-08
Does it boot at all?

---

### Post by Claudia_Fiorenza on 2013-09-08
if you are talking about the wifi: when i switch it on i can see on the upright corner of my display that it activates and seems to detect a connetion and tries to establish a wificonnection but after few seconds it freese itself and anyother application i am running (exept for my mouse) and after a little bit pops up the message that it coulnd establish a connection and the rest of applications start working again

---

### Post by praseodym on 2013-09-08
Can you connect via cable? If yes, reinstall the network-manager:
```

sudo apt-get install --reinstall network-manager network-manager-gnome
sudo service network-manager restart
```

---

### Post by Claudia_Fiorenza on 2013-09-08
yes i have via cable connection. so i did what you said and rebooted. still not working. (also: i just checked that the wifi is working perfecly on my windows7 partition...just to be sure that my pc didn't got broken somehow)

---

### Post by praseodym on 2013-09-08
Maybe Windows shuts down the card?! Check the system settings there...

---

### Post by Claudia_Fiorenza on 2013-09-13
i tried and i got wifi connection with the portable wifi hotspot of my mobilephone. so, i don't think windows partition is related to my problem in ubuntu..am i right?

---

