---
title: "Ubuntu 12.04 Not Finding Wireless Networks - Lenovo Ideapad w/ Windows 8 Dual Boot"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by badolato-c on 2014-02-26
Hello,

I installed Ubuntu 12.04 recently (dual-booting with Windows 8), and it won't recognize any wireless networks.  Upon searching the forums it appears as if the proper drivers aren't installed.

I know there's some code I should be pasting from inputing commands into the terminal, but I'm just starting to learn how to properly use Ubuntu and have no idea what those commands are.

Thanks.

---

### Post by wildmanne39 on 2014-02-26
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

---

### Post by badolato-c on 2014-02-26
Here you go.

---

### Post by varunendra on 2014-02-27
There seem to be two issues -

**1)** The driver "wl" is loaded which is a driver for Broadcom chips. You don't seem to have one, so this is mysterious. Let's get rid of it -
```
sudo modprobe -rv wl
sudo apt-get purge bcmwl-kernel-source
```
If the first command returns error, like "FATAL : drive in use" etc., simply ignore, run the second command and reboot.

**2)** The firmware required by the correct driver "iwlwifi" is missing in your system.

Download it from here [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode)

Assuming you have saved it on your Desktop, copy it to your /lib/firmware directory with the following command -
```
sudo cp Desktop/iwlwifi-7260-7.ucode /lib/firmware/
```

Then either reboot, or reload the driver manually -
```
sudo modprobe -rv iwlwifi
sudo modprobe -v iwlwifi
```

Reference threads that may be interesting for you :
[http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319](http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319)
[http://ubuntuforums.org/showthread.php?t=2178873](http://ubuntuforums.org/showthread.php?t=2178873)


**PS:**
@ Wild Man,
Isn't this mysterious to you as well ? -
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
	Kernel modules: **[COLOR="#FF0000"]wl[/COLOR]**, iwlwifi
```
Do you have any theory or idea how it may happen?

---

### Post by badolato-c on 2014-02-27
That worked, thanks!

---

### Post by varunendra on 2014-02-27
You're welcome! :)

Hope the performance is decent. Any comments?

---

### Post by wildmanne39 on 2014-02-27
> **varunendra said:**
> There seem to be two issues -

**1)** The driver "wl" is loaded which is a driver for Broadcom chips. You don't seem to have one, so this is mysterious. Let's get rid of it -
```
sudo modprobe -rv wl
sudo apt-get purge bcmwl-kernel-source
```
If the first command returns error, like "FATAL : drive in use" etc., simply ignore, run the second command and reboot.

**2)** The firmware required by the correct driver "iwlwifi" is missing in your system.

Download it from here [https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode](https://git.kernel.org/cgit/linux/kernel/git/egrumbach/linux-firmware.git/plain/iwlwifi-7260-7.ucode)

Assuming you have saved it on your Desktop, copy it to your /lib/firmware directory with the following command -
```
sudo cp Desktop/iwlwifi-7260-7.ucode /lib/firmware/
```

Then either reboot, or reload the driver manually -
```
sudo modprobe -rv iwlwifi
sudo modprobe -v iwlwifi
```

Reference threads that may be interesting for you :
[http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319](http://ubuntuforums.org/showthread.php?t=2204438&p=12924319#post12924319)
[http://ubuntuforums.org/showthread.php?t=2178873](http://ubuntuforums.org/showthread.php?t=2178873)


**PS:**
@ Wild Man,
Isn't this mysterious to you as well ? -
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 73)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:4262]
	Kernel modules: **[COLOR="#FF0000"]wl[/COLOR]**, iwlwifi
```
Do you have any theory or idea how it may happen?Yes it is strange I assume it is left over from another device that was installed, or was installed by mistake, or from a cloned hard drive.

---

### Post by jeremy-bricker on 2014-03-31
I've just dual booted a Panasonic CF-AX3 and had the same problem, but the same solution worked. Thanks for posting this stuff.

> **badolato-c said:**
> That worked, thanks!

---

### Post by varunendra on 2014-03-31
Welcome to Ubuntu Forums Jeremy!

Thanks for your feedback. :)

---

