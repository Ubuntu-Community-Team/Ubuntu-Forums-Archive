---
title: "Installing New Hardware Drivers if provided"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by robert-drury on 2011-06-30
Hi Folks at Ubuntu!
I recently purchased new hardware:  M-Audio Audiophile 2496 SoundCard with Midi output
and iomega Home Media Network Hard Drive Cloud Edition.
These include usual Windows7/Mac Drivers Disk. They also quote Linux support.
For Audiophile 2490: Linux == Redhat, Iomega Storage Manager == Redhat and Debian 4

For Iomega Storage Manager Software you download "Storagemgr-setup.bin"
into my home downloads folder == /home/username/downloads/storagemgr-setup.bin
BUT THEN WHAT DO I DO WITH IT? Please. You can call me "Jumbo Dumbo" if it help you!
But there are no clues as to how to install, or I don't have a clue!
I tried, "sudo apt-get install storagemgr.bin
and  sudo apt-get install /home/username/downloads/storagemgr.bin 
E:error message, Nothing doing. 
This product is new, supports FTP & other protocols but not Samba
but can not be found in Nautilus when searching Network. 
I can access only the drive by default intra-web page: /192.168.1.68/ 
but I need the storage manager to manipulate storage
Nautilus can find my other NAS: QNAP TS-209 II 
Sorry I vote with my feet, "NO WEB CLOUDS IN THE SKY, BUT ONLY THOSE ON MY DESK!"
Please see the embed:[IMG]http://ubuntuforums.org/home/robert/downloads/storagemgr-setup.bin[/IMG] and or **_see the attachment_**, should be included!
Tks. robert-drury

---

### Post by frankbooth on 2011-06-30
.bin files are similar to Windows' .exe files, but you'll need to make the .bin file executable before you can run it.

I'll show you how you can achieve this through the terminal.

**1)** Launch a terminal ;) and navigate to the file (if needed).

**2)** Make the file executeable by typing:```

chmod +x storagemgr-setup.bin

```

**3)** Now run the file by typing: ```

./storagemgr-setup.bin

```

---

