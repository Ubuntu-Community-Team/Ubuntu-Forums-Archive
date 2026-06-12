---
title: "wireless button on hp 6735s not working"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by FlyingFish on 2008-10-03
Hi,

I have just done a clean install on my new hp compaq 6735s laptop with Ubuntu (Hardy). Ubuntu is not recognizing my wireless card and I believe it is because the button toggle is not working properly.
[B][U]
Update[/U][/B]:
Just upgraded to 8.10 which is supposed to have proprietary support for my Broadcom wireless card (The driver is working but not being used). The wireless button still is not working, neither is the wireless.  I tried following jorgitovk's advise below which worked for others with similar laptops, but not mine.  Does anyone else have a solution?

Your help is much appreciated.  Thanks!

FF

---

### Post by lenu on 2008-10-05
i'm having the same issue. just installed ubuntu 8.04.1 with wubi and no wireless.

---

### Post by asusu90 on 2008-11-08
Hi

I have the same problem... with 8.10.
I think the major problem:
Ubi know the bcm4322 card as a pci device (not hotpluggable)
If I press my button during the boot, usually my wifi is working.

(the button works to switch bluetooth on/off anyway)

8.04.1 dont know anything  about the second processor core...
(at the moment I'm using 8.10, so I cannot "cat /proc/cpuinfo")
What about you?

---

### Post by IQRules on 2008-12-24
How you like this HP 6735s with Ubuntu? I am thinking to buy one.

---

### Post by asusu90 on 2009-01-14
I like it! There was some audio problem, but it is can be fixed...very easily.
And of course: ATI HD3200, I couldn't install the correct driver, so the fullscreen doesn't work, and if I wanna see any video, I have to switch off my Compiz.

---

### Post by jorgitovk on 2009-04-03
Hi,

I follow this steps:

- switch off computer
- extract the battery and insert again
- boot, press "ESC" and enter BIOS (F10)
- load defaults

- Boot GNU/Linux (ubuntu 8.10 "intrepid")

The wireless button turns on blue again!!

Hope it helps,

jorge

---

### Post by FlyingFish on 2009-04-20
Problem....not solved!  Thanks for trying jorgitovk.  I've followed your sequence, but to no avail.  I'm still working to figure this out.

---

### Post by Ayuthia on 2009-04-20
> **FlyingFish said:**
> Problem....not solved!  Thanks for trying jorgitovk.  I've followed your sequence, but to no avail.  I'm still working to figure this out.

Have you checked System->Administration->Hardware Drivers and make sure that the Broadcom STA option is enabled.  If it still does not work, try the following in the Terminal:
```
sudo modprobe -r b43 ssb ndiswrapper wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

If it still does not work, please check:
```
dmesg|grep wl
```

---

### Post by HairyIguana on 2009-05-10
Hi Guys,

I am new to both the forums and linux as a whole, so apologies if anything is a little out of place here.

Basically I have a newly purchased HP 6735s and have setup a dualboot with Vista and Ubuntu (Jaunty Jacakalope) and I am having some of the same difficulties regarding the wireless network. 

I used some information I found somewhere on here regarding the synaptic package manager to install ndisgtk and using the new interface I have installed the windows drivers for my wireless card.

I am still finding that every time I boot into Ubuntu the wireless adaptor is not recognised, however if I go into system>administration>hardware drivers the driver is there but it says "the device is active but not currently in use" if I then deactivate the driver and reactivate it the wireless network kicks straight in.

Does anyone have any ideas for how I can get this to work at bootup rather than needing to go through this process?

Thanks in advance for any ideas...

Cheers
Alan

---

### Post by onionparadise on 2010-01-06
I'm having the same problem described here, and find myself unable to solve it. I'm running a persistent boot of 9.10 on a portable hard drive, and the wireless button continues to stay amber and turned off no matter what. I've tried all the solutions posted here, to no avail. When I try the code suggested by Ayuthia, I get the following:```
WARNING: Failed to open config file blacklist-bcm43.conf: Input/Output Error 
```

The STA driver is installed, and indicates that the driver is not being used even though it's activated. I tried installing the actual driver files through the Windows Wireless Drivers tool (ndiswrapper), and that indicates that hardware is not present. I tried resetting the computer's BIOS settings, but that isn't working either. Has anyone solved this problem?

---

### Post by megamaced on 2010-02-18
I am having the same issue:

I installed Ubuntu 9.10 64-BIT and was able to install the Broadcom driver through the Restricted Drivers. Wireless WAS working fine. However since pressing the Wireless ON/OFF button on the laptop, Ubuntu does not pick up the wireless, however Bluetooth, which is also controlled by the same button, does turn ON and OFF as expected!

The broadcom device does not show up at all with an lscpi command now.

Any pointers?

---

### Post by megamaced on 2010-02-18
I have found some info on this issue but don't have my HP 6735s laptop with me to test this:

From [http://www.linlap.com/wiki/hp-compaq+6735s](http://www.linlap.com/wiki/hp-compaq+6735s)

> This wifi device (BCM4312 with PCI ID 14e4:4315 (rev 01)) tends to cease working from time to time. This has always happened to me when pressing the “Wifi” button. It stops working and can't be turned on again, neither rebooting nor cold booting. 

I used to fix this by reseting the BIOS setup (Load Default Values), until one day this fix just stopped working. Tried upgrading the BIOS, tried removing the card from the laptop, tried lots of things. No success. 

Finally, I've made it by looking for the device under the /sys/class/pci_bus directory. Mine can be found at /sys/class/pci_bus/0000:06/device/0000:06:00.0 

Just browse all the possible folders and look for a vendor file containing 0x14e4 and a device of 0x4315. 

Then it is as easy as doing echo 1 > broken_parity_status just did that and it resurrected instantly, turning the Wifi led blue. 

Hope this helps someone :) 

---

### Post by Rytron on 2010-08-16
The readme file for the drivers at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) is very complex. Could someone condense it for installing the 32bit driver at that site? Thanks.

---

### Post by om~namas~ganga on 2010-10-12
Did you solved the wireless button issue at some point? 

I am installing Ubuntu 9.10 in a HP6735s too and having the same issue.

Please any help is welcome, I am on the hunt of a maybe..

If it didn´t work with Ubuntu , anybody tried with another distribution?

---

### Post by Rytron on 2010-10-12
> **om~namas~ganga said:**
> Did you solved the wireless button issue at some point? 

I am installing Ubuntu 9.10 in a HP6735s too and having the same issue.

Please any help is welcome, I am on the hunt of a maybe..

If it didn´t work with Ubuntu , anybody tried with another distribution?

Install Windows Driver. Google for it.

```
sudo modprobe wl
```
```
sudo gedit /etc/modules
```

Insert "wl" to new line (without brackets), save and close. May need to reboot.

	sudo apt-get install b43-fwcutter

Then install Wireless Firmware from sendspace.com/file/9qchv0 with command "sudo lspci | grep Network"

These drivers were also an option broadcom.com/support/802.11/linux_sta.php

---

### Post by Rytron on 2010-10-12
> **om~namas~ganga said:**
> Did you solved the wireless button issue at some point? 

I am installing Ubuntu 9.10 in a HP6735s too and having the same issue.

Please any help is welcome, I am on the hunt of a maybe..

If it didn´t work with Ubuntu , anybody tried with another distribution?

Install Windows Driver. Google for it.

```
sudo modprobe wl
```
```
sudo gedit /etc/modules
```

Insert "wl" to new line (without brackets), save and close. May need to reboot.

```
sudo apt-get install b43-fwcutter
```

Then install Wireless Firmware from sendspace.com/file/9qchv0 with command "sudo lspci | grep Network"

These drivers were also an option broadcom.com/support/802.11/linux_sta.php

Note: Not all steps maybe needed. However some or all of the above worked for me. Cheers.

---

### Post by SatchMan on 2011-06-19
> **jorgitovk said:**
> Hi,

I follow this steps:

- switch off computer
- extract the battery and insert again
- boot, press "ESC" and enter BIOS (F10)
- load defaults

- Boot GNU/Linux (ubuntu 8.10 "intrepid")

The wireless button turns on blue again!!

Hope it helps,

jorge

Thank you for the advice! I've been searching for days and your method worked for me! I'm on Maverick for in case other users are having the same problem. Thanx again!::D

---

### Post by bittner on 2011-08-17
> **jorgitovk said:**
> Hi,

I follow this steps:

- switch off computer
- extract the battery and insert again
- boot, press "ESC" and enter BIOS (F10)
- load defaults

- Boot GNU/Linux (ubuntu 8.10 "intrepid")

The wireless button turns on blue again!!

Hope it helps,

jorge

Thanks Jorge, this worked! :popcorn:

---

