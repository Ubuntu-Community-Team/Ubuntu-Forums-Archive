---
title: "[HELP]Wireless disabled by hardware switch .. worked fine before shutting down"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by TerminalSkunk on 2014-07-25
Hi There, 

So yesterday i installed 14.04 and the wireless worked fine all day without any issues, However after shutting down my machine and walking home i powered my laptop back on and aparently my wifi is being disabled by a hardware switch .. i dont have a wifi switch on my laptop (psychical nor in the bios)

Can anybody help?

This is the contents of my RFKill list: 

```
0: phy0: Wireless LAN
            Soft Blocked: no
            Hard blocked: yes

1: hci0: Bluetooth
          Soft Blocked: no
          Hard Blocked: no
```

Even a wired connection isn't working.

Okay so i have been trying other things, So far i have tried; 

[Threads]
[http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285](http://ubuntuforums.org/showthread.php?t=2111690&p=12490285#post12490285)  :Not Working

[Other Things]
New HDD running Windows 7: Not Working.
Removing Battery and holding power for 30 secs for Hardware Reset
Bios Reset: Not Working.

---

### Post by praseodym on 2014-07-25
What kind of computer is it? Tried a BIOS reset?

---

### Post by TerminalSkunk on 2014-07-25
It is a Samsung NP270E5E-K04UK and I have just come back from restarting my PC after a bios reset.

---

### Post by praseodym on 2014-07-25
Check:
```

dmesg | egrep 'radio|kill|switch'
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
```

---

### Post by TerminalSkunk on 2014-07-25
Hi There, 

This is the pastebin of what i got after inputting the commands listed above: 
[http://pastebin.com/WP4sdgbt](http://pastebin.com/WP4sdgbt)

```

terminalskunk@TerminalSkunk:~$ dmesg | egrep 'radio|kill|switch'
[   11.618221] Console: switching to colour frame buffer device 170x48
[   14.613831] init: failsafe main process (617) killed by TERM signal
[   15.140066] init: cups main process (722) killed by HUP signal
terminalskunk@TerminalSkunk:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
	Kernel driver in use: ath9k
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Samsung Electronics Co Ltd Device [144d:c708]
	Kernel driver in use: r8169
terminalskunk@TerminalSkunk:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2232:1041  
Bus 001 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
terminalskunk@TerminalSkunk:~$ lsmod
Module                  Size  Used by
rfcomm                 69160  8 
bnep                   19624  2 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  1 
snd_hda_codec_realtek    61438  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
coretemp               13435  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             143060  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
kvm                   451511  1 kvm_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
ghash_clmulni_intel    13216  0 
cryptd                 20359  1 ghash_clmulni_intel
joydev                 17381  0 
serio_raw              13462  0 
arc4                   12608  2 
parport_pc             32701  0 
ath9k                 164164  0 
ath3k                  13318  0 
ath9k_common           13551  1 ath9k
ppdev                  17671  0 
btusb                  32412  0 
ath9k_hw              453856  2 ath9k_common,ath9k
bluetooth             391196  23 bnep,ath3k,btusb,rfcomm
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
lp                     17759  0 
snd                    69238  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport                42348  3 lp,ppdev,parport_pc
cfg80211              484040  3 ath,ath9k,mac80211
soundcore              12680  1 snd
i915                  783805  3 
wmi                    19177  0 
video                  19476  1 i915
mei_me                 18627  0 
drm_kms_helper         53081  1 i915
mei                    82276  1 mei_me
drm                   303102  4 i915,drm_kms_helper
lpc_ich                21080  0 
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
psmouse               106678  0 
ahci                   25819  3 
r8169                  67581  0 
libahci                32560  1 ahci
mii                    13934  1 r8169
terminalskunk@TerminalSkunk:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
terminalskunk@TerminalSkunk:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
```

Thanks for the help so far :)

---

### Post by praseodym on 2014-07-25
```

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="#FF0000"]off[/COLOR]   
```
Lets try:
```

sudo modprobe -rfv ath9k
sudo rfkill unblock all
echo "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo modprobe -v ath9k
sudo service network-manager restart
```
Any key combination (Fn+F5 or similar)?

---

### Post by TerminalSkunk on 2014-07-25
This is the log from the codes you asked me to enter before; 

```

terminalskunk@TerminalSkunk:~$ sudo modprobe -rfv ath9k
[sudo] password for terminalskunk: 
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
terminalskunk@TerminalSkunk:~$ sudo rfkill unblock all
terminalskunk@TerminalSkunk:~$ echo "nameserver 8.8.8.8\nameserver 8.8.8.4" | sudo tee /etc/resolv.conf
nameserver 8.8.8.8\nameserver 8.8.8.4
terminalskunk@TerminalSkunk:~$ sudo modprobe -v ath9k
insmod /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
terminalskunk@TerminalSkunk:~$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2178

```

After doing this the rfkill list looks like the following; 
```

1: hci0: Bluetooth
          Soft Blocked: no
          Hard Blocked: no

2: phy0: Wireless LAN
            Soft Blocked: no
            Hard blocked: yes
```


I have FN+F12 on the actual keys but pressing the combination does nothing on the actual laptop.

---

### Post by praseodym on 2014-07-25
Ok, please take out the battery and shut off the current for 15 minutes. Then try it again.

---

### Post by TerminalSkunk on 2014-07-25
Okay, I'll report back after i have done this :) 

Thanks again for the help.
--------------------------------------
EDIT: Okay after leaving it for a while and trying it all again its still displays the same as above.

---

### Post by varunendra on 2014-07-25
Samsung models are a mystery for me so far, but resetting BIOS once fixed a similar problem.

So.. IF the installation is _NOT_ UEFI based, try resetting the BIOS and let us know if it changed anything.

**PS:**
You should post updates in new posts, not by editing existing posts, otherwise your thread won't get highlighted in the search results of the person helping you and they won't know you have posted an update.

---

### Post by TerminalSkunk on 2014-07-25
I have tried a bios reset since i previously posted (read edited), The issue is still ongoing.

Thanks for the help so far everybody :) 

**PS**:
Thanks for the advice :) I didn't wanna be double posting or bumping to quickly.

---

### Post by varunendra on 2014-07-25
In your edit, you mentioned doing what praseodym suggested - taking the battery out and leaving it for a while. That is not the same thing as a BIOS reset (the BIOS settings are retained since the CMOS chip is powered by a separate battery on motherboard).

So please confirm - did you just do the power cycle like praseodym suggested or also tried a BIOS reset separately?

---

### Post by TerminalSkunk on 2014-07-25
I tried both the power cycle and i also reset the bios after this failed to work.

Sorry for the confusion

---

### Post by varunendra on 2014-07-26
Your lsmod has certain modules that I don't have here on my old installation (12.04) to check myself, so I'd like you to please post their modinfo so I can see what they are and if some of then can likely interfere with wifi switch. To do that in one go, please post back the output of -
```
modinfo intel_rapl intel_powerclamp crct10dif_pclmul crc32_pclmul mei_me ahci libahci | sed '/^alias/ d; s/^filename/\n&/'
```

and..
```
cat /proc/cmdline
```

---

### Post by TerminalSkunk on 2014-07-28
Sorry about the delay in gathering this information, I have been away from any internet connection for the weekend and didn't bring the machine to work with me today, I will get the required information and post it here tomorrow.

---

### Post by fernando44 on 2015-04-07
Hi, exactly the same problem(and machine)... any updates?

---

