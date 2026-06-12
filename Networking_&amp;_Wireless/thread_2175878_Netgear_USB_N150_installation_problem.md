---
title: "Netgear USB N150 installation problem"
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by subhendu2 on 2013-09-21
I ahve got Netgear USB N150 wifi adapter for my Ubuntu 12.04 LTS desktop. But I could not install it after trying for 5 hours. 
I have many combinations done. I have already formatted it once. So if there is a tested method , I am ready to format and start again

$ lsusb 
Bus 001 Device 008: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I then tried to install the drivers from the Realtek website. and install them . But no fruitfull results. My home wifi network is without any password. The Wifi is trying to connect and then fails. 

I then even tried to install the Windows installation given by Chii555 in a post with ndisgtk. But failed. 

But surprisingly after 5 hours research , the blue light of the Wifi adapter is not lighting up and now there is no Wireless activity. (!!!!!!!!!!!) 
ifconfig even doesnot show the adapter also.
:~$ lsmod | grep -e ndis -e 8192
ndiswrapper           196777  0 

Please help. I need this to work to test my project.

---

### Post by kurt18947 on 2013-09-22
That device should work well with the driver from Realtek.  Ubuntu versions after 12.10 do not work with the Realtek driver unless that driver is tweaked and some problems fixed.  The Realtek driver is here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

This driver includes an install script which I had pretty good luck with.  Ubuntu 12.04.3 also seems to have better support for the rtl8188cus chip than does the 12.04 original.  I haven't used 12.04.3 enough to judge how stable the RTL8188CUs is.  If you tried NDISwrapper, you may need to remove that completely before trying anything else.

---

### Post by subhendu2 on 2013-09-22
Dear Kurt18947
I had initially installed that driver of realtek . But nothing happened. It is trying to connect and the getting disconnected.
Presently , I am re installing the OS (Ubuntu 12.04.2) which will be automatically upgraded to 12.04.3. 
Can you please give me a step by step instruction.

---

### Post by subhendu2 on 2013-09-22
In fact during installation of the OS , it detected my Netgear N150. But it couldnot connect.

---

### Post by subhendu2 on 2013-09-22
its trying to connect but after sometime it is showing disconnected. This is without the realtek driver. Should I installl the driver?

---

### Post by kurt18947 on 2013-09-23
I'm not certain Realtek's driver will work with 12.04.3.  I think the kernel version in 12.04.3 is the same as 13.04 and the Realtek driver won't build on 13.04. You might try Tim Phillips' solution posted here:

 [https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/)

I did a fresh install of 12.04.3 and my Edimax 7811Un ran stable on that install for the half hour I tried it using the native driver.  How well the native driver works appears to depend on what hardware it's running on.

---

### Post by subhendu2 on 2013-09-24
Bus 001 Device 003: ID 18ec:3399 Arkmicro Technologies Inc. 
Bus 001 Device 009: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 002: ID 2341:0001  
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

But the blue light at the back of the Netgear module is not lighting. The netwok toolbox is also not showing wireless option. 

I installed the realtek driver .
After that i blacklisted the following ones rtl8192cu , rtl8192c_common , rtlwifi in /etc/modprobe.d/blacklist.conf

then I rebooted

robot@robot:~$ lsmod |grep 8192
robot@robot:~$ lsmod | grep 8188
robot@robot:~$ lsmod | grep rtl

returned nothing
robot@robot:~$ lsmod
Module                  Size  Used by
vesafb                 13518  1 
hid_generic            12485  0 
snd_usb_audio         106661  1 
snd_intel8x0           33463  2 
snd_ac97_codec        106118  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                81124  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_hwdep              13277  1 snd_usb_audio
snd_usbmidi_lib        24590  1 snd_usb_audio
rfcomm                 38104  0 
bnep                   17791  2 
snd_seq_midi           13133  0 
snd_seq_midi_event     14476  1 snd_seq_midi
bluetooth             189625  10 rfcomm,bnep
uvcvideo               72249  0 
ppdev                  12850  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
videobuf2_core         32212  1 uvcvideo
snd_rawmidi            25426  2 snd_usbmidi_lib,snd_seq_midi
videodev              100265  2 uvcvideo,videobuf2_core
usbhid                 46054  0 
microcode              18396  0 
videobuf2_vmalloc      12757  1 uvcvideo
cdc_acm                22416  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_timer              28932  2 snd_pcm,snd_seq
hid                    82511  2 hid_generic,usbhid
snd_seq_device         14138  3 snd_seq_midi,snd_seq,snd_rawmidi
serio_raw              13032  0 
snd                    62675  16 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
ns558                  12655  0 
gameport               15089  2 ns558
drm                   227273  0 
soundcore              14636  1 snd
parport_pc             32115  1 
lpc_ich                16993  0 
snd_page_alloc         14109  2 snd_intel8x0,snd_pcm
shpchp                 32326  0 
mac_hid                13078  0 
i2c_algo_bit           13317  0 
compat                 14565  1 drm
video                  19117  0 
lp                     17456  0 
parport                40931  3 ppdev,parport_pc,lp
8139too                23312  0 
8139cp                 26719  0 
floppy                 60214  0 



PLEASE HELP

---

### Post by kurt18947 on 2013-09-25
I may not be seeing well but I don't see the Realtek driver loaded.  There should be "8192cu" (NOT rtl8192cu, that's the open source driver) listed in lsmod.  Assuming either the Realtek driver or Tim Phillips' tweak built properly, you could try loading the module manually.  You could try this:
```
sudo modprobe 8192cu
```
If that's the issue, the device should be active within seconds.  If this works, there's a means to ensure the module loads automatically.

---

### Post by subhendu2 on 2013-09-26
[COLOR=#000000]Confirm that it is possible to get the NetGear WNA1000M adapter (USB ID 0846:9041) running with the Realtek drivers in Ubuntu 10.04. However, for me it was not trivial, I had to go through the following procedure, to make it work.[/COLOR]

[LIST]
[*]I have downloaded drivers from the Realtek site: [http://www.realtek.com.tw/downloads/...true#RTL8192CU]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU")
[*]After unpacking I went to the drivers directory and unpacked yet another .tar.gz file there, that contains actual driver code.
[*]In the newly created directory (rtl8188C_8192C_8192D_usb_linux_v3.3.2_3192.201201 03 in the current version) I had to find the os_dep/linux/usb_intf.c file and add the following line to the "8192CUS Dongle" group (around line 150):
[/LIST]

[COLOR=#000000]Code:
    {USB_DEVICE(0x0846, 0x9041)},//NetGear WNA1000M[/COLOR]

[LIST]
[*]After that I have used the standard commands to build and install the driver:
[/LIST]

[COLOR=#000000]Code:
make
sudo make install[/COLOR]
[COLOR=#000000]Then I issued commands 
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu


But the connection is very erratic. And is often disconnecting. And signal strength is very low.
How to make the commands permanent. 
Every time  I have to unplug and re plug the USB after standby mode.  - Is there any solution to it?

But I am happy atleast I can see the blue light blinking after 10 days of fighting and 3 times OS loading[/COLOR]

---

### Post by varunendra on 2013-09-26
> **subhendu2 said:**
> Presently , I am re installing the OS (Ubuntu 12.04.2) which will be automatically upgraded to 12.04.3.

Did you ever upgrade to kernel 3.8+ ? I can confirm that the rtl8192cu driver in that kernel has support for your device (0846:9041). If it did not work properly, we could try some parameters, some external setting to make it work better. As a last resort, we could try the backported driver from kernel 3.11.

As you figured out yourself, the proprietary realtek driver is way outdated and does not support your card by default, you had to manually add its id to make it work. And even when compiled, it does not work very well.

As such, I'd suggest you try the native one with some tweaks first. If they fail, try the backported one.

A frequently disconnecting dodgy driver on an unsupported, outdated system doesn't look even close to a satisfactory solution to me.

---

### Post by kurt18947 on 2013-09-26
> A frequently disconnecting dodgy driver on an unsupported, outdated  system doesn't look even close to a satisfactory solution to me.

I certainly agree with this.  While the proprietary drivers from Realtek are better, the 'baked-in' driver in 13.10 seems quite usable.  I find it also makes a difference what wireless router/access point is in use.

---

### Post by subhendu2 on 2013-09-26
> **varunendra said:**
> Did you ever upgrade to kernel 3.8+ ? I can confirm that the rtl8192cu driver in that kernel has support for your device (0846:9041). 

I have some specific questions as I am a newbie in Ubuntu. 
1. Presently I am using 12.04 LTS. I have done sudo apt-get update & upgrade. But the kernel did not upgraded to 3.8. How will I upgrade to kernel 3.8?
2. I have openCV + python running in my system. Will kernel upgrade means I will have to install them again?
3. What if it does not work in 3.8 ? Is there anyway to come back to the original kernel?

Something not related to Netgear. 
My webcam is not being recognized by cheese and VLI , although I can initialize the webcam through openCV . Do anyone have any solution? Will 3.8 upgrade solve this issue. ?

---

### Post by varunendra on 2013-09-26
> **subhendu2 said:**
> 1. Presently I am using 12.04 LTS. I have done sudo apt-get update & upgrade. But the kernel did not upgraded to 3.8. How will I upgrade to kernel 3.8?
Unless you have disabled some update types manually, you should have been automatically prompted to do the upgrade. However, you can also do it as follows -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

> 2. I have openCV + python running in my system. Will kernel upgrade means I will have to install them again?
If the packages were installed using default package managers (apt-get or Software Center or Synaptic) and from default repositories (not PPAs), then they will be automatically upgraded. Packages from PPAs are not guaranteed to upgrade properly.

> 3. What if it does not work in 3.8 ? Is there anyway to come back to the original kernel?
The older kernels are always retained unless you manually remove them. So you can always go back to older kernel (from advance grub menu at boot time).

> My webcam is not being recognized by cheese and VLI , although I can initialize the webcam through openCV . Do anyone have any solution? Will 3.8 upgrade solve this issue. ?
Newer drivers and packages *may* solve the issue. If not, post the problem in a different thread with relevant title under "Multimedia & Video" section.

---

### Post by subhendu2 on 2013-09-27
> **varunendra said:**
> 
```
sudo apt-get update
sudo apt-get dist-upgrade
```


 That produced no upgrades
```
 uname - a 
``` 
gives linux robot 3.5.0-40- generic #62 precise1- Ubuntu SMP

Now what?

---

### Post by varunendra on 2013-09-27
Interesting, because the same thing did that [post=12800075]here[/post], although the OP there was already on kernel 3.8.0-19.

Are you using the first release ISO of 12.04 or the third one (12.04.2)? Sometimes it is not possible to directly jump to a much higher version and it has to be done successively (meaning more than one upgrade cycle). Please show us -
```
lsb_release -d
apt-cache show linux-image* | grep ^Package.*image-3.[15-9] | sort -V
```

Whatever be the path to get there, out target is to get you on kernel 3.8+ and then try the native driver first, if that fails, the backported one from 3.11. So if it takes too many upgrades, it makes sense to just download the ISO of 12.04.3 which already contains kernel 3.8 as far as I know.

---

### Post by subhendu2 on 2013-09-27
Here is the output

robot@robot:~$ lsb_release -d
Description:    Ubuntu 12.04.3 LTS
robot@robot:~$ apt-cache show linux-image* | grep ^Package.*image-3.[15-9] | sort -V
Package: linux-image-3.5.0-18-generic
Package: linux-image-3.5.0-19-generic
Package: linux-image-3.5.0-21-generic
Package: linux-image-3.5.0-22-generic
Package: linux-image-3.5.0-23-generic
Package: linux-image-3.5.0-24-generic
Package: linux-image-3.5.0-25-generic
Package: linux-image-3.5.0-26-generic
Package: linux-image-3.5.0-27-generic
Package: linux-image-3.5.0-28-generic
Package: linux-image-3.5.0-30-generic
Package: linux-image-3.5.0-31-generic
Package: linux-image-3.5.0-32-generic
Package: linux-image-3.5.0-34-generic
Package: linux-image-3.5.0-36-generic
Package: linux-image-3.5.0-37-generic
Package: linux-image-3.5.0-39-generic
Package: linux-image-3.5.0-40-generic
Package: linux-image-3.8.0-19-generic
Package: linux-image-3.8.0-21-generic
Package: linux-image-3.8.0-22-generic
Package: linux-image-3.8.0-23-generic
Package: linux-image-3.8.0-25-generic
Package: linux-image-3.8.0-26-generic
Package: linux-image-3.8.0-27-generic
Package: linux-image-3.8.0-29-generic
Package: linux-image-3.8.0-30-generic

---

### Post by varunendra on 2013-09-27
> **subhendu2 said:**
> Package: linux-image-[COLOR="#FF0000"]3.8.0-30[/COLOR]-generic

So it IS available, not sure why you didn't get it in the updates. Maybe its priority is currently 'optional', maybe it wants to upgrade in successive steps like I mentioned before, I can't say for sure.

What does this give you -
```
apt-cache show linux-image-generic | grep ^Depends
```
Some versions higher than your current one? (uname -r)

As far as know, the next upgrade will install the highest version listed in the above output. If it is not 3.8, perhaps you need many upgrade cycles ;)

Or you can choose to directly install the 3.8.0-30 kernel manually -
```
sudo apt-get install linux-image-3.8.0-30-generic linux-headers-3.8.0-30 liunx-headers-3.8.0-30-generic
```

I'd like to clarify that I have never installed a much newer kernel myself (skipping too many in-between), so can't say if it has any potential to break anything. But since it is coming from default repositories and we are not 'forcing' it, I *assume* its installation should be smooth and there should be no side effects.

---

### Post by subhendu2 on 2013-09-27
robot@robot:~$ apt-cache show linux-image-generic | grep ^Depends
Depends: linux-image-3.2.0-53-generic, linux-firmware
Depends: linux-image-3.2.0-23-generic, linux-firmware

---

### Post by varunendra on 2013-09-27
> robot@robot:~$ apt-cache show linux-image-generic | grep ^Depends
Depends: linux-image-3.2.0-53-generic, linux-firmware
Depends: linux-image-3.2.0-23-generic, linux-firmware
Not even a higher version? Your current kernel is newer than these :)

I'd say, just download the 12.04.3 ISO and try it in live mode. Do the testings on it instead of messing with the installed system.

---

### Post by subhendu2 on 2013-09-27
> **varunendra said:**
> Not even a higher version? Your current kernel is newer than these :)



I really donot want to mess around. In fact after you started posting , my wifi has started to response better. It is not getting disconnected anymore. most probably it is afraid and decided to serve me better :D:P

But please tell me how to make these two commands permanent
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu

---

### Post by varunendra on 2013-09-27
> **subhendu2 said:**
> In fact after you started posting , my wifi has started to response better. It is not getting disconnected anymore. most probably it is afraid and decided to serve me better :D:P
Yeah, definitely afraid (..who knows what this guy's upto.. :/)

> But please tell me how to make these two commands permanent
sudo modprobe -r rtl8192cu
sudo modprobe 8192cu

If you haven't already blacklisted the offending driver, please do -
```
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And to make the other one load automatically at startup -
```
echo "8192cu" | sudo tee -a /etc/modules
```

Usually the last trick should not be required if everything is done properly, but sometimes... (afterall, it is an 'OS created By hackers, For hackers..' ;))

---

### Post by subhendu2 on 2013-09-27
> **varunendra said:**
> 
If you haven't already blacklisted the offending driver, please do -
```
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And to make the other one load automatically at startup -
```
echo "8192cu" | sudo tee -a /etc/modules
```



This is working perfect. But there is a small hitch left. Once I get ur answer I will close the thread

After I rebooted the system with the adapter on the USB , the adapter didnot get turned on automatically. I had to unplug the adapter and then plug it again. Why is this so? Is there a way out to get it started without any un plug and plug method?

Your suggestions are working great. Waiting for the last one

---

### Post by varunendra on 2013-09-27
> **subhendu2 said:**
> This is working perfect. But there is a small hitch left. Once I get ur answer I will close the thread
Given the nature of the problem you mentioned, I doubt if it is going to be my last post :)

> After I rebooted the system with the adapter on the USB , the adapter didnot get turned on automatically. I had to unplug the adapter and then plug it again. Why is this so? Is there a way out to get it started without any un plug and plug method?
These device probing/initializing events are usually handled by udev rules (besides some other scripts to take care of some specific situations). So the best *I* can do (many others in the forum may be able to go deeper and offer better help) is to update initramfs (which loads the initial kernel and modules), reset the udev rules, and start with a fresh one.

To try that, please make sure ONLY the required 8192cu driver is loaded, not any conflicting one, then do -
```
sudo update-initramfs -u
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
sudo udevadm trigger
sudo modprobe -r 8192cu
sudo modprobe 8192cu
```

The second command will move the existing udev rule file for network devices to your home. With the last command, a fresh new file should be created. Check it with -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
Is the file there? If yes, it should have only one entry pertaining to wlan0 (or whatever your wifi interface is named), and only the 8192cu driver should be associated with it.

You can compare it with the one moved to your home (70-persistent-net.rules.bak). I suspect currently there may be at least two entries pertaining to wlan0, and the top one would be related to the older driver (rtl8192cu).

Reboot and see if it gets activated automatically this time. If not, you can try a dirty workaround : unloading - reloading the driver using /etc/rc.local file. But I hope we won't need that.

---

### Post by subhendu2 on 2013-09-27
> **varunendra said:**
> Given the nature of the problem you mentioned, I doubt if it is going to be my last post :)


These device probing/initializing events are usually handled by udev rules (besides some other scripts to take care of some specific situations). So the best *I* can do (many others in the forum may be able to go deeper and offer better help) is to update initramfs (which loads the initial kernel and modules), reset the udev rules, and start with a fresh one.

To try that, please make sure ONLY the required 8192cu driver is loaded, not any conflicting one, then do -
```
sudo update-initramfs -u
sudo mv /etc/udev/rules.d/70-persistent-net.rules 70-persistent-net.rules.bak
sudo udevadm trigger
sudo modprobe -r 8192cu
sudo modprobe 8192cu
```

The second command will move the existing udev rule file for network devices to your home. With the last command, a fresh new file should be created. Check it with -
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
Is the file there? If yes, it should have only one entry pertaining to wlan0 (or whatever your wifi interface is named), and only the 8192cu driver should be associated with it.

You can compare it with the one moved to your home (70-persistent-net.rules.bak). I suspect currently there may be at least two entries pertaining to wlan0, and the top one would be related to the older driver (rtl8192cu).

Reboot and see if it gets activated automatically this time. If not, you can try a dirty workaround : unloading - reloading the driver using /etc/rc.local file. But I hope we won't need that.

I tried these commands
```
 robot@robot:~$ sudo update-initramfs -u
[sudo] password for robot: 
update-initramfs: Generating /boot/initrd.img-3.5.0-40-generic
robot@robot:~$ sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:0a.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0b:6a:e7:01:45", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0846:0x9041 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="10:0d:7f:c1:0b:7d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

Will executing your commands be any help?

---

### Post by varunendra on 2013-09-27
Apparently not, but run them anyway. I don't know myself if udev rules are also maintained somewhere else, so running "udevadm trigger" should take care of it.

If it does not help, try adding a command line in /etc/rc.local file -

Open it with root access -
```
gksu gedit /etc/rc.local
```
Insert the following line in it (just above the last line that says - "exit 0")
```
sleep 30 && modprobe -r 8192cu && sleep 2 && modprobe 8192cu
```
The file must end with "exit 0" line, so make sure to insert the line above it. Proofread, save and close. Reboot and pray.

---

### Post by subhendu2 on 2013-09-28
I was planning to write "SOLVED" , but today I noticed something strange. 

My laptop on windows 7 and the desktop on ubuntu 12.04 with the wifi is running side by side
when i issue commands
```
 ping 192.168.1.1
```

the laptop is taking 2ms average time , whereas the ubuntu system is taking average of 1000ms. Sometimes it is going to 2300 ms. And no point of time it is coming below 20ms.

Why is this so?

---

### Post by varunendra on 2013-09-29
> **subhendu2 said:**
> My laptop on windows 7 and the desktop on ubuntu 12.04 with the wifi is running side by side
when i issue commands
```
 ping 192.168.1.1
```

the laptop is taking 2ms average time , whereas the ubuntu system is taking average of 1000ms. Sometimes it is going to 2300 ms. And no point of time it is coming below 20ms.

Please make sure IPv6 is set to "Ignore" in Network Manager then reconnect, retry. If there is no change in ping times, please follow this [post=12640479]post[/post] to completely disable it. If still no change, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

Please also post the following outputs along with the script report -
```
ifconfig
ping -c4 google.com
```

---

### Post by subhendu2 on 2013-10-02
Thanks everybody. My Netgear N150 , Realtek 188CUS is working fine. This is what I had to do in mmy Ubuntu 12.04 LTS with the latest kernel even. 
1. Downloaded the latest driver from the Realtek site. 
2. Unzipped the driver. Within the unzipped folder there is a folder called driver. Within that folder there is another zipped file. Unzipped that file. Here is the tricky part. You will find that there is already a unzipped file in the same name and it is locked. Delete that file and then unzipp. 
3. Then run make , sudo make install from the unzipped file.
  sudo modprobe -r rtl8192cu
  sudo modprobe 8192cu
5. The modem should work now. The blue light at the back should blink. 
6.  Then run the following commands to make the changes permanent
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf

echo "8192cu" | sudo tee -a /etc/modules


The modem is working

---

