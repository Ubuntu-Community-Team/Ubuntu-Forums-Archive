---
title: "[SOLVED] Broadcom BCM4313 / HP Mini Netbook"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by hoffman2 on 2013-10-14
I need help to fix wireless connection for the HP Mini Net Book.
I just installed Ubuntu 12.04 LTS as a replacement for Windows 7 Starter which was pre installed on the HP mini netbook.
After the installation, everything seems fine except for the wireless connection. I can't connect to my home wifi network.
Thus I can't download all the update for Ubuntu 12.04 LTS.

Anyway I found the thread where you can look into the status of the wireless. Here are the result when I typed it on the  terminal:
```
aiden@aiden-HP-Mini-110-3500:~$ cat/etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=12.04 
DISTRIB_CODENAME=precise 
DISTRIB_DESCRIPTION="Ubuntu12.04.3 LTS" 
Linux aiden-HP-Mini-110-35003.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013i686 i686 i386 GNU/Linux 
aiden@aiden-HP-Mini-110-3500:~$ lscpi-nnk | grep -iA2 net 
No command 'lscpi' found, did you mean:
 Command 'lscpu' from package'util-linux' (main) 
 Command 'lscp' from package'nilfs-tools' (universe) 
 Command 'lspci' from package'pciutils' (main) 
lscpi: command not found 
aiden@aiden-HP-Mini-110-3500:~$ lspci-nnk | grep -iA2 net 
01:00.0 Network controller [0280]:Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller[14e4:4727] (rev 01) 
    Subsystem: Hewlett-Packard CompanyDevice [103c:1483] 
    Kernel driver in use: bcma-pci-bridge 
-- 
03:00.0 Ethernet controller [0200]:Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express FastEthernet controller [10ec:8136] (rev 05) 
    Subsystem: Hewlett-Packard CompanyDevice [103c:1584] 
    Kernel driver in use: r8169 
aiden@aiden-HP-Mini-110-3500:~$ lsusb 
Bus 001 Device 005: ID 0951:1643Kingston Technology DataTraveler G3 4GB 
Bus 001 Device 002: ID 05c8:021a ChengUei Precision Industry Co., Ltd (Foxlink) 
Bus 005 Device 002: ID 0a5c:21b4Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR 
Bus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub 
aiden@aiden-HP-Mini-110-3500:~$iwconfig 
lo        no wireless extensions. 


eth0      no wireless extensions. 


aiden@aiden-HP-Mini-110-3500:~$ rfkilllist all 
0: hci0: Bluetooth 
    Soft blocked: yes 
    Hard blocked: no 
1: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
2: hp-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
aiden@aiden-HP-Mini-110-3500:~$ lsmod 
Module                  Size  Used by 
b43                   364596  0 
ssb                    51554  1 b43 
mac80211              541819  1 b43 
cfg80211              453853  2b43,mac80211 
bcma                   39810  1 b43 
nls_iso8859_1          12617  1 
usb_storage            48053  1 
rfcomm                 38400  0 
bnep                   17852  2 
parport_pc             27612  0 
ppdev                  12849  0 
joydev                 17329  0 
uvcvideo               72250  0 
snd_hda_codec_idt      64649  1 
videobuf2_core         39385  1uvcvideo 
videodev               96131  2uvcvideo,videobuf2_core 
snd_hda_intel          38819  3 
videobuf2_vmalloc      12920  1uvcvideo 
videobuf2_memops       13042  1videobuf2_vmalloc 
snd_hda_codec         118613  2snd_hda_codec_idt,snd_hda_intel 
coretemp               13324  0 
hp_wmi                 17748  0 
kvm                   384557  0 
sparse_keymap          13658  1 hp_wmi 
snd_hwdep              13276  1snd_hda_codec 
snd_pcm                85934  2snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25157  1snd_seq_midi 
i915                  550346  3 
btusb                  17951  0 
snd_seq_midi_event     14475  1snd_seq_midi 
snd_seq                51593  2snd_seq_midi,snd_seq_midi_event 
microcode              18433  0 
bluetooth             211435  14rfcomm,bnep,btusb 
snd_timer              28931  2snd_pcm,snd_seq 
snd_seq_device         14137  3snd_seq_midi,snd_rawmidi,snd_seq 
wmi                    18744  1 hp_wmi 
drm_kms_helper         47749  1 i915 
drm                   233935  4i915,drm_kms_helper 
lpc_ich                17048  0 
lp                     17455  0 
snd                    57014  15snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                82769  0 
i2c_algo_bit           13316  1 i915 
serio_raw              13031  0 
mac_hid                13077  0 
parport                40930  3parport_pc,ppdev,lp 
soundcore              12600  1 snd 
snd_page_alloc         18398  2snd_hda_intel,snd_pcm 
video                  19116  1 i915 
ahci                   25631  2 
libahci                26336  1 ahci 
r8169                  62532  0

```
Then I tried to install b43 file and still no luck
I am new to Ubuntu. Please I need help to fix this problem. And i need step by step and with plain english. As i don't really understand with the linux sudo languange. :D

FYI, my HP mini doesn't have ethernet cable connection. So the wireless is the only way to connect to the Internet. If I need to download a driver to fix this problem. I will use my other laptop then put into my USB then transfer it to my HP mini.

---

### Post by varunendra on 2013-10-14
Hello hoffman2, and Welcome to the forums ! :)

> **hoffman2 said:**
> 01:00.0 Network controller [0280]:Broadcom Corporation **BCM4313** 802.11b/g/n Wireless LAN Controller**[14e4:4727]** (rev 01) 
	Subsystem: Hewlett-Packard CompanyDevice [103c:1483] 
	Kernel driver in use: **bcma-pci-bridge** 

We can try to fix the problem via graphical tools, but the command line methods have the advantage that they are quick and if something wrong happens, like an error, you get the exact error message back in the terminal which is a great help, almost essential, in troubleshooting the problem.

So I hope you won't mind if I give you a few commands to run in a terminal :P

Please open the terminal (Ctrl-Alt-T) and run the following commands in it, one-by-one (you may copy-paste these to a text file, then copy-paste them back to the terminal to avoid errors) -
```
sudo modprobe -rv b43
sudo modprobe brcmsmac
```
When you first use the "sudo" command, it will ask you for your password. Type in your login password. You won't see anything on the screen while typing the password (security measure), just type it correctly and press "Enter".

If the above makes your wifi active, test its performance and report back to make it permanent.

If not, try installing the proprietary driver. It is located in the **/pool/restricted/b/bcmwl/** folder in the CD/USB from where you installed Ubuntu. Just copy the "**bcmwl-kernel-source.....**" file to your desktop and double-click to install it. Then reboot to see if it worked.

Let us know how it goes.

**PS:**
You should always use '**Code**' box to post commands & terminal outputs. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by wildmanne39 on 2013-10-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by hoffman2 on 2013-10-14
> **varunendra said:**
> :smile:



[COLOR=#222222][FONT=Verdana]We can try to fix the problem via graphical tools, but the command line methods have the advantage that they are quick and if something wrong happens, like an error, you get the exact error message back in the terminal which is a great help, almost essential, in troubleshooting the problem.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]SoI hope you won't mind if I give you a few commands to run in aterminal [/FONT][/COLOR]:razz:



[COLOR=#222222][FONT=Verdana]No I don't mind with the command line. Actually I am hoping to learn it but sometimes when the command line is way to long and there are several of them and also I don't understand what is each line trying to do. That is what make me kind of confuse. But anyway for now just I will just copy paste the command line to fix the problem. I will try to learn it later about the command line.[/FONT][/COLOR]

> **varunendra said:**
> [COLOR=#000000][FONT=Verdana]Please open the terminal (Ctrl-Alt-T) and run the following commands in it,one-by-one (you may copy-paste these to a text file, then copy-paste them back to the terminal to avoid errors) -[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Code:
sudo modprobe -rv b43
sudo modprobe brcmsmac[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Whenyou first use the "sudo" command, it will ask you for yourpassword. Type in your login password. You won't see anything on thescreen while typing the password (security measure), just type itcorrectly and press "Enter".
[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana]Now I tried to type the first command line. It didn't came up with anything. And then it asked for the password. I typed the password. Then I typed the second command line and again it didn't come up with anything again. But now the wifi worked and it could detect my home Wifi connection and could connect to the internet. I tried to restart Ubuntu just to see if this works permanently. After I restarted then the wireless is not working anymore.

I tried the to install the bcmwl file that is located on the USB installation. And it didn't work either after the installation. 

Then when I was on the internet, I install the additional driver. After that it asked me if I want to install the STA driver. I click activate it didn't install and I got error window. It says " Sorry, installation of this driver failed. Please have a look at the log file for details: var/log/jockey.log"

So the wifi is actually working but it just can't stay there permanently. I have to type in sudo modprobe again to make activate it. So is there any other way to make the wifi stays activated permanently.




[/FONT][/COLOR]

---

### Post by varunendra on 2013-10-15
The **bcmwl** and the **sta** driver suggested by "Additional Drivers" program are same, only different versions usually. The one you got from the "Additional Drivers" program failed to install most probably because of a bug either in the driver or the kernel updates (missing headers).

Anyway, if the one on the CD didn't work, it is very likely that the one from updates won't work either (unless it is the latest 6.30.. version, which has improved a lot). While if the native brcmsmac is working fine after loading, it is much better to just stick with it and make its loading permanent (which is default by the way, something must be wrong with your configurations).

So moving towards the fix, please purge the sta driver and all its settings -
```
sudo apt-get purge bcmwl-kernel-source
```

Then post back the outputs of -
```
cat /etc/modules
cat /etc/rc.local
egrep -iR 'brcm|bcm|b43' /etc/modprobe.d
cat /etc/udev/rules.d/70-persistent-net.rules
```
I suspect some custom setting is preventing the brcmsmac driver from loading automatically. The above outputs will show us the common settings where it may be hiding.

Please note that any attempt to install the sta driver will again blacklist the native drivers, preventing them to load at startup. So avoid trying it and ignore any suggestions for the wireless by the "Additional Drivers" program.

---

### Post by hoffman2 on 2013-10-16
```
aiden@aiden-HP-Mini-110-3500:~$ sudo modprobe -rv b43
[sudo] password for aiden: 
rmmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
rmmod /lib/modules/3.8.0-29-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.8.0-29-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
rmmod /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
aiden@aiden-HP-Mini-110-3500:~$ sudo modprobe brcmsmac
aiden@aiden-HP-Mini-110-3500:~$ sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 106 not upgraded.
After this operation, 3,656 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 143172 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-29-generic
^[[aiden@aiden-HP-Mini-110-3500:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
b43
aiden@aiden-HP-Mini-110-3500:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
aiden@aiden-HP-Mini-110-3500:~$ egrep -iR 'brcm|bcm|b43' /etc/modprobe.d
/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb.
/etc/modprobe.d/blacklist.conf:blacklist bcm43xx
aiden@aiden-HP-Mini-110-3500:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="78:ac:c0:cb:df:75", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="cc:52:af:0b:8e:04", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
aiden@aiden-HP-Mini-110-3500:~$ 

```

I did what you told me to and up above is what came up after typing each command line that you give me.

And now the wifi is working flawlessly. I tried to restart my netbook twice just to make sure that the wifi stays permanently.

Anyway, I would like to say thank you for varunendra and wildman for assisting me.

*big smile*

---

### Post by mörgæs on 2013-10-16
Good, please mark the thread 'solved' using 'thread tools'.

---

### Post by Hadaka on 2013-10-16
Hi hoffman2,varun is having computer problems and asked if i would
lend a hand.
pleas do..one line at a time..
```
sudo apt-get autoremove
sdo apt-get update
sudo apt get upgrade
```
then we need to edit this file..please do
```
sudo gedit /etc/modules
```
*remove this one line...b43 or make it look like this #b43
save and close gedit.
finally please do..
```
sudo modprobe -rf brcmsmac
soudo modprobe -v brcmsmac
```
wireless working??
** Late to the party..sorry about that...glad its working..!!

---

### Post by varunendra on 2013-10-17
Thank you Hadaka for taking care of it. 5th day and power has still not resumed here. Running on 'resumed power' in my lead-acid batteries. :(

@ hoffman2
While it is solved now, the problem may reoccur if the "b43" entry remains in the /etc/modules file -
> **hoffman2 said:**
> ```
~$ cat /etc/modules
....
lp
**[COLOR="#FF0000"]b43[/COLOR]**

```
Accordingly, please do what Hadaka suggested to comment it out.

Or simply remove it with -
```
sudo sed -i '/b43/ d' /etc/modules
```

---

