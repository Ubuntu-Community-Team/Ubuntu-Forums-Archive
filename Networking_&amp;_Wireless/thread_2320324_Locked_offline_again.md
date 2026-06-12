---
title: "Locked offline again"
date: 2016-04-12
forum: Networking &amp; Wireless
---

### Post by jdkcarlson on 2016-04-12
I am the same problem here:

[http://ubuntuforums.org/showthread.php?t=2316533](http://ubuntuforums.org/showthread.php?t=2316533)

My computer came back from a suspend with the GUI unresponsive to mouse clicks and typing. I suspended and unsuspended and the problem persisted. The notice when you hit the power button—if you want to suspend, save your files first, etc.—appeared and wouldn't go away, as clicking the x wouldn't close it. Eventually the computer bailed and restarted on its own.

When it came back, wireless was gone.

sudo modprobe ath10k yielded the same fatal error it did the first time around. Backports was in the same place. Many of the errors from the first time round were the same. I went though the entire thing trying to redo everything, but things still aren't back now.

sudo modprobe ath10k still yields FATAL: module not found.

modinfo ath10k_pci | grip 003E gives an error that says the firmware is not in place.

I found the folders from this answer 

[http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation) 

and tried to recreate the same steps. I renamed the files in /lib/firmware/QCA6174/hw3.0 to .old and replaced them with the things unzipped from the master.zip folder, but things haven't improved. I'm probably missing something obvious but I don't know what. Please help.

Wireless in the upper right corner was showing "device not ready" for a bit but now just shows disconnected and doesn't show networks. It remembers old networks under Edit Connections... but there doesn't seem to be an option to connect to any of them.

:(:confused:

Thanks.

---

### Post by jeremy31 on 2016-04-13
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Post the contents of the wireless-info.txt file

---

### Post by jdkcarlson on 2016-04-13
[http://pastebin.com/NXt1ax80](http://pastebin.com/NXt1ax80)

Hopefully it isn't something I messed up myself. I needed to tether to use github, in case it notes I was connected.

Thank you.

---

### Post by jeremy31 on 2016-04-13
I am not quite sure what is happening now.  Reboot and hold the SHIFT key until the Grub menu appears, scroll down to Advanced options or Previous linux versions and select a kernel less than 3.19.0-58, there may be a 3.19.0-57.  Press enter to boot into the older kernel and see if wireless works

---

### Post by jdkcarlson on 2016-04-13
I have 3.19.0-56, but wireless doesn't work there. Is it possible I moved the wrong files or followed the instructions wrong? I could have sworn I did the same thing as before, including the sudo make installs and things. Is there a way to check if I messed that up?

---

### Post by jeremy31 on 2016-04-15
You could do a ```
ls | grep backport
``` 

Actually it should show the driver was compiled from backports check ```
modinfo ath10k_pci | grep backport
```

---

### Post by jdkcarlson on 2016-04-15
The first comes up empty, no feedback. The second gives

```
version:    backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
```

---

### Post by jeremy31 on 2016-04-16
But the backport-4.4.2-1 directory does not exist?

You may have to run the commands to download and install them again.  Hopefully then ```
dmesg | grep ath
``` Will provide some useful help

---

### Post by jdkcarlson on 2016-04-17
"ls | grep backport" gives no feedback but "locate backports | less" gives a whole lot. In particular, /home/MY_USER_NAME/backports-4.4.2-1 has many files. When I navigate there and do "ls | grep backport" I find just the folder "backport-include". Is that what you meant? I didn't realize you meant to navigate to that folder, if that is what you meant.

---

### Post by jdkcarlson on 2016-04-17
dmesg grep | ath gets a lot of good errors. Most of them are "Direct firmware load failed with error -2" or "could not fetch firmware file." The files it says this about are of the form "firmware-#.bin" for # between 0 and 5. I can locate a lot of these, but they look like they're mostly in 

/lib/firmware/ath10k/QCA6174/hw2.1/ath10k-firmware-master/QCA####/hw#.#  

or 

/lib/firmware/ath10k/QCA98##/hw2.1/

itself. Should I try moving them to

/lib/firmware/ath10k/QCA6174/hw3.0/ 
?

**Update**: I got it working. Although the new installation replaced most of the files, I didn't have a working substitute for firmware-4.bin. Replacing this file, doing the 

echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf

again for good measure, and restarting got me back wireless. Moreover, for whatever reason, I now no longer have to try to connect to a hidden network.

**Thank you!**

---

