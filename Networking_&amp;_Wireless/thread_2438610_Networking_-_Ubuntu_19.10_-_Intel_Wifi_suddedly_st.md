---
title: "Networking - Ubuntu 19.10 - Intel Wifi suddedly stopped working, flashing wifi menu?"
date: 2020-03-15
forum: Networking &amp; Wireless
---

### Post by lazerdude on 2020-03-15
Hello guys!  I have been using my Xiaomi Redmibook 14 running Ubuntu 19.10 for a good while now, and there have been no issues. But just a few days ago, wifi stopped working and it has been quite frustrating. I have tried almost everything I could find (iwlwifi packports, rfkill), but nothing seems to work. rfkill seems to show that the wireless ethernet is softblocked, but even when I run the command to stop the soft block, a restart brings the problem back. 

Network controller is: Intel Corporation Device 02f0.

I am still quite new to Ubuntu so please let me know what outputs I should be posting along with this post. Also, I really don't want to reinstall ubuntu, as I have customized quite a lot and I have a lot of files in differnet places, so it would be a massive time commitment for a busy college student :) 

Here is the flashing wifi icon problem, haven't seen it anywhere else. Also flashes like this from the taskbar.[IMG]https://imgur.com/a/ndZeBaT[/IMG]
[https://imgur.com/a/ndZeBaT](https://imgur.com/a/ndZeBaT)[https://i.imgur.com/dOvV9O3.gif](https://i.imgur.com/dOvV9O3.gif)


When I run: 

[COLOR=#242729][FONT=Consolas]lspci -knn | grep Net -A2[/FONT][/COLOR]

I get: 

00:14.3 Network controller [0280]: Intel Corporation Device [8086:02f0]
    Subsystem: Intel Corporation Device [8086:02a4]
    Kernel driver in use: iwlwifi

____________________________________________________________________________________________________________________________________________________________

I'm really not sure what to do now. 
Additional drivers shows that the option for the iwlwifi backport driver is selected, but nothing is happening.

Thank you in advance for the help!

---

### Post by lazerdude on 2020-03-15
I apologize I posted in the wrong subforum. Could a mod possibly move it for me? Sorry again, long time lurker, first time posting here!

---

### Post by wildmanne39 on 2020-03-15
Hello and welcome to the forum.

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Your post is in the correct forum.

---

### Post by lazerdude on 2020-03-15
Thank you for the advice!!!

---

### Post by chili555 on 2020-03-15
Please run and post:

```
uname -r
dmesg | grep iwl
```

---

### Post by lazerdude on 2020-03-15
> **chili555 said:**
> Please run and post:

```
uname -r
dmesg | grep iwl
```

Here is the output: 

```

      lazerdude@redmibook-14:~$ uname -r
5.3.0-29-generic


      lazerdude@redmibook-14:~$ dmesg | grep iwl



[    2.556693] iwlwifi: unknown parameter 'disable_msix' ignored
[    2.565297] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-48.ucode failed with error -2
[    2.568637] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-47.ucode failed with error -2
[    2.572983] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-46.ucode failed with error -2
[    2.584681] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-45.ucode failed with error -2
[    2.584767] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-44.ucode failed with error -2
[    2.584795] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-43.ucode failed with error -2
[    2.584811] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-42.ucode failed with error -2
[    2.584835] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-41.ucode failed with error -2
[    2.584854] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-40.ucode failed with error -2
[    2.584873] iwlwifi 0000:00:14.3: Direct firmware load for iwlwifi-QuZ-a0-jf-b0-39.ucode failed with error -2
[    2.584876] iwlwifi 0000:00:14.3: no suitable firmware found!
[    2.584881] iwlwifi 0000:00:14.3: minimum version required: iwlwifi-QuZ-a0-jf-b0-39
[    2.584882] iwlwifi 0000:00:14.3: maximum version supported: iwlwifi-QuZ-a0-jf-b0-48
[    2.584883] iwlwifi 0000:00:14.3: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git


  
```

---

### Post by chili555 on 2020-03-15
With a temporary internet connection by ethernet, tethering or whatever means possible, open a terminal and do: ```
sudo apt install --reinstall linux-firmware
```Next, do:```
sudo nano /etc/modprobe.d/iwlwifi.conf
```I suspect that there is a line: ```
options iwlwifi disable_msix=Y
```It may be =1 or =yes or some such. In any event, remove the entire line. Save and close the text editor.

Reboot. Now is the wireless working?

---

### Post by lazerdude on 2020-03-15
> **chili555 said:**
> With a temporary internet connection by ethernet, tethering or whatever means possible, open a terminal and do: ```
sudo apt install --reinstall linux-firmware
```Next, do:```
sudo nano /etc/modprobe.d/iwlwifi.conf
```I suspect that there is a line: ```
options iwlwifi disable_msix=Y
```It may be =1 or =yes or some such. In any event, remove the entire line. Save and close the text editor.

Reboot. Now is the wireless working?

Unfortunately nothing. I already deleted the option lines before.
My config file looks like this:

```

# /etc/modprobe.d/iwlwifi.conf# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
 
```

---

### Post by chili555 on 2020-03-15
Let's see:```
ls /etc/modprobe.d
ls /lib/firmware | grep iwlwifi-Qu
sudo dpkg -s linux-firmware
```1.183.4?

---

### Post by lazerdude on 2020-03-15
> **chili555 said:**
> Let's see:```
ls /etc/modprobe.d
ls /lib/firmware | grep iwlwifi-Qu
sudo dpkg -s linux-firmware
```1.183.4?

Yep. 


```


lazerdude@redmibook-14:~$ ls /etc/modprobe.d


   alsa-base.conf                    blacklist-ideapad.conf
   amd64-microcode-blacklist.conf  blacklist-modem.conf
   backports.conf                    blacklist-oss.conf
   blacklist-ath_pci.conf           blacklist-rare-network.conf
   blacklist.conf                       dkms.conf
   blacklist.conf.dpkg-old         droidcam.conf
   blacklist-firewire.conf           intel-microcode-blacklist.conf
   blacklist-framebuffer.conf     iwlwifi.conf


lazerdude@redmibook-14:~$ ls /lib/firmware | grep iwlwifi-Qu

   iwlwifi-Qu-b0-hr-b0-48.ucode
   iwlwifi-Qu-b0-jf-b0-48.ucode
   iwlwifi-Qu-c0-hr-b0-48.ucode
   iwlwifi-Qu-c0-jf-b0-48.ucode
   iwlwifi-QuZ-a0-hr-b0-48.ucode
   iwlwifi-QuZ-a0-jf-b0-48.ucode


lazerdude@redmibook-14:~$ sudo dpkg -s linux-firmware


  [sudo] password for lazerdude: 
  Package: linux-firmware
  Status: install ok installed
  Priority: optional
  Section: misc
  Installed-Size: 473804
  Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
  Architecture: all
  Multi-Arch: foreign
  Version: 1.183.4
  Replaces: atmel-firmware, linux-firmware-snapdragon (<= 1.2-0ubuntu1), linux-restricted-common
  Provides: atmel-firmware
  Breaks: linux-firmware-snapdragon (<= 1.2-0ubuntu1)
  Conflicts: atmel-firmware
  Description: Firmware for Linux kernel drivers
   This package provides firmware used by Linux kernel drivers.



```

What does that mean?

---

### Post by chili555 on 2020-03-15
Your firmware file says:```

   iwlwifi-Qu-b0-hr-b0-48.ucode
   iwlwifi-Qu-b0-jf-b0-48.ucode
   iwlwifi-Qu-c0-hr-b0-48.ucode
   iwlwifi-Qu-c0-jf-b0-48.ucode
   iwlwifi-QuZ-a0-hr-b0-48.ucode
   i[COLOR="#FF0000"]wlwifi-QuZ-a0-jf-b0-48.ucode[/COLOR]

```But the error was:> iwlwifi 0000:00:14.3: Direct firmware load for [COLOR="#FF0000"]iwlwifi-QuZ-a0-jf-b0-48.ucode[/COLOR] failed with error -2I don't understand.

Has the error disappeared?```
dmesg | grep iwl
ls -al /lib/firmware | grep iwlwlfi-Qu
cat /etc/modprobe.d/backports.conf
```

---

