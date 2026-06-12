---
title: "Solved How to get ubuntustudio to install wireless card"
date: 2018-02-02
forum: Networking &amp; Wireless
---

### Post by diode84 on 2018-02-02
Hello
I am totally new to ubuntustudio and am having trouble installing the wireless card, a bcm4312 on a dell vostro. I did try ubuntu 16.04 and the driver installed and works.
The ethernet connection is pretty broken but can work if I hold it in so is there any I could install it. Additional drivers doesnt find it.
Ubuntu 16.04 uses broadcom 802.11 linux sta wireless driver source from bcmwl-kernel-source (proprietry) and is working and installed on the laptop.
Any ideas.
thanks
diode84

---

### Post by wildmanne39 on 2018-02-02
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by wildmanne39 on 2018-02-02
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by diode84 on 2018-02-03
Is this what you mean? I am connecting with a unknown wireless usb adapter at the moment but would like to use the internal wifi.
```

xxxxx@xxxxx-Vostro-1320:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
Linux xxxxx-Vostro-1320 4.10.0-28-lowlatency #32~16.04.2-Ubuntu SMP PREEMPT Thu Jul 20 11:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
```
xxxxx@xxxxx-Vostro-1320:~$ lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:02bb]
    Kernel driver in use: r8169
    Kernel modules: r8169
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
```
```
xxxxx@xxxxx-Vostro-1320:~$ lsusb
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 004: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
xxxxx@xxxxx-Vostro-1320:~$ iwconfig
enp8s0    no wireless extensions.

wlx48022a1a8654  IEEE 802.11bgn  ESSID:"Fairplay-Net"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 84:16:F9:D5:EB:2B   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.
```
```

xxxxx@xxxxx-Vostro-1320:~$ rfkill list all
```
```
xxxxx@xxxxx-Vostro-1320:~$ lsmod
```

---

### Post by coffeecat on 2018-02-03
@diode84, you posted your terminal output without code tags, which caused it to lose formatting and to acquire a number of spurious smileys. Did you not see those when you posted? I've added code tags to your most recent post, but please use BBCode code tags when posting terminal output. If you don't know how, there is a link in my sig.

Also - there is no output posted for "rfkill list all" and "lsmod". It must have gone awol when you copy-pasted. Please post the output of these two commands so that members can help you.

---

### Post by diode84 on 2018-02-03
Hello coffeecat
I dont understand the brackets and cant find any.
rfkill list all in terminal gives nothing
lsmod gives
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
xxxxx@xxxxx-Vostro-1320:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS"
Linux xxxxx-Vostro-1320 4.10.0-28-lowlatency #32~16.04.2-Ubuntu SMP PREEMPT Thu Jul 20 11:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
xxxxx@xxxxx-Vostro-1320:~$ lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:02bb]
    Kernel driver in use: r8169
    Kernel modules: r8169
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
xxxxx@xxxxx-Vostro-1320:~$ lsusb
Bus 002 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
xxxxx@xxxxx-Vostro-1320:~$ iwconfig
wlx48022a1a8654  IEEE 802.11bgn  ESSID:"Fairplay-Net"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 84:16:F9:D5:EB:2B   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=98/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

enp8s0    no wireless extensions.
```

```
xxxxx@xxxxx-Vostro-1320:~$ rfkill list all
xxxxx@xxxxx-Vostro-1320:~$ lsmod
Module                  Size  Used by
r8712u                176128  0
dell_laptop            20480  0
dell_smbios            16384  1 dell_laptop
dcdbas                 16384  1 dell_smbios
dell_smm_hwmon         16384  0
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
coretemp               16384  0
kvm                   593920  0
irqbypass              16384  1 kvm
b43                   413696  0
bcma                   57344  1 b43
mac80211              794624  1 b43
joydev                 20480  0
input_leds             16384  0
snd_hda_codec_idt      57344  1
snd_hda_codec_generic    73728  1 snd_hda_codec_idt
serio_raw              16384  0
snd_hda_intel          40960  3
cfg80211              610304  2 b43,mac80211
snd_hda_codec         126976  3 snd_hda_intel,snd_hda_codec_idt,snd_hda_codec_generic
snd_hda_core           81920  4 snd_hda_intel,snd_hda_codec,snd_hda_codec_idt,snd_hda_codec_generic
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
lpc_ich                24576  0
snd                    77824  16 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_hda_codec_idt,snd_timer,snd_rawmidi,snd_hda_codec_generic,snd_seq_device,snd_pcm
soundcore              16384  1 snd
shpchp                 36864  0
mac_hid                16384  0
cuse                   16384  3
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
i915                 1449984  8
i2c_algo_bit           16384  1 i915
drm_kms_helper        151552  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
psmouse               139264  0
firewire_ohci          40960  0
drm                   352256  10 i915,drm_kms_helper
firewire_core          65536  1 firewire_ohci
r8169                  81920  0
pata_acpi              16384  0
ssb                    57344  1 b43
sdhci_pci              28672  0
crc_itu_t              16384  1 firewire_core
mii                    16384  1 r8169
sdhci                  45056  1 sdhci_pci
fjes                   77824  0
video                  40960  2 dell_laptop,i915
xxxxx@xxxxx-Vostro-1320:~$ ~~~
```


Let me know about the brackets

---

### Post by jeremy31 on 2018-02-03
Diode84 use [noparse]```
 before terminal output and 
``` after[/noparse] In advanced reply there is a # button above the reply window that places the code tag and you can just CTRL + v to paste your content

---

### Post by chili555 on 2018-02-03
The proprietary Broadcom STA driver, also known as bcmwl-kernel-source, is incorrect for your device. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

With a working internet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Detach the USB wireless, reboot and tell us if the internal Broadcom is working.

---

### Post by diode84 on 2018-02-03
> **chili555 said:**
> The proprietary Broadcom STA driver, also known as bcmwl-kernel-source, is incorrect for your device. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

With a working internet connection, open a terminal and do:```
sudo apt-get update
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Detach the USB wireless, reboot and tell us if the internal Broadcom is working.
chili555
It did seem to download a few files but a reboot still didnt find the internal card.

---

### Post by praseodym on 2018-02-03
The problem is, that this installer doesn't contain the files needed (any more) for the low power chipset LP-PHY. Install this one containing them
```

wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```

---

### Post by diode84 on 2018-02-03
> **praseodym said:**
> The problem is, that this installer doesn't contain the files needed (any more) for the low power chipset LP-PHY. Install this one containing them
```

wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Thanks praseodym
That did the job and installed it at once.
Thanks again for the help.

---

### Post by diode84 on 2018-02-03
Thank you all for all the help, I have now got the internal card working.
I was about to give up on ubuntustudio but after all of the positive help I will continue as I feel its the best operating system I have used so far.
As I am a total beginner I will be back for help.
All the best
diode84

---

### Post by diode84 on 2018-02-03
> **jeremy31 said:**
> Diode84 use [noparse]```
 before terminal output and 
``` after[/noparse] In advanced reply there is a # button above the reply window that places the code tag and you can just CTRL + v to paste your content

Thanks jeremy31
I see what you mean. I have never come across advanced reply before today.
diode84

---

### Post by jeremy31 on 2018-02-03
The code tags preserve formatting of terminal output and prevent the smilies that occur if the tags aren't used and it does make it easier to scroll through the info.  In advanced reply, you can highlight with mouse/touchpad and then click on the # above the reply window and it will add the tags also

---

