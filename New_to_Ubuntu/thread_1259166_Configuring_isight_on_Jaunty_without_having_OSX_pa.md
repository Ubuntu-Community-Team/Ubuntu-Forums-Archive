---
title: "Configuring isight on Jaunty *without* having OSX partition?"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by confused_person on 2009-09-06
So I'm running jaunty on a Macbook 4,1 but I deleted the osx partition, and all of the guides i've seen for configuring isight (e.g. [http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/](http://handyfloss.net/2008.07/making-isight-camera-work-in-ubuntu/), [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight))  assume you have it. I downloaded the AppleUSBVideoSupport driver, but I'm not very terminal-savvy and I can't figure out how to configure it based on the file on my desktop rather than within my nonexistent OSX partition. Help is appreciated. Thanks!

---

### Post by duanedesign on 2009-09-06
1.First you need to get the firmware out of a particular file located on your OSX install. You can copy it to a USB drive or other location so that you can acess it from Ubuntu. It is located in:
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/
AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
**NOTE:** If you do not have your mac partition anymore you can get the firmware [here]("http://dl.getdropbox.com/u/332246/AppleUSBVideoSupport")

2. Boot into Ubuntu and install isight-firmware-tools
```
sudo apt-get install isight-firmware-tools
```

3. Go ahead and place the AppleUSBSupportVideo file in /lib/firmware
```
sudo cp AppleUSBSupportVideo /lib/firmware/
```

4. Now, extract the iSight firmware from the file
```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```

Shutdown your machine and then reboot it. Some guides on this subject recommend a complete shutdown/reboot as opposed to a restart.

Save the file isight.fw created in /lib/firmware directory. So in the future you will not need to extract it from the AppleUSBVideoSupport file. You will just place the isight.fw file in /lib/firmware/.

hope this helps.

---

### Post by confused_person on 2009-09-06
> **duanedesign said:**
> 1.First you need to get the firmware out of a particular file located on your OSX install. You can copy it to a USB drive or other location so that you can acess it from Ubuntu. It is located in:
/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/
AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
**NOTE:** If you do not have your mac partition anymore you can get the firmware [here]("http://dl.getdropbox.com/u/332246/AppleUSBVideoSupport")

2. Boot into Ubuntu and install isight-firmware-tools
```
sudo apt-get install isight-firmware-tools
```3. Go ahead and place the AppleUSBSupportVideo file in /lib/firmware
```
sudo cp AppleUSBSupportVideo /lib/firmware/
```4. Now, extract the iSight firmware from the file
```
sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
```Shutdown your machine and then reboot it. Some guides on this subject recommend a complete shutdown/reboot as opposed to a restart.

Save the file isight.fw created in /lib/firmware directory. So in the future you will not need to extract it from the AppleUSBVideoSupport file. You will just place the isight.fw file in /lib/firmware/.

hope this helps.

Awesome! Worked like a charm, thanks :) 

I did also have a problem with green/purple tint, but I did some digging around and downloading this [http://packages.ubuntu.com/karmic/libv4l-0](http://packages.ubuntu.com/karmic/libv4l-0) fixed it.

---

