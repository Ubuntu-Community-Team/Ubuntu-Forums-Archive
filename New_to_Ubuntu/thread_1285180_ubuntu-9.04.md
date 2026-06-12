---
title: "ubuntu-9.04"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by jimbo160 on 2009-10-07
My system size is 2.69GHz, 1.24GB of ram. I downloaded the program from a wubi page that told me after the download, it would be auto installed on my system, giveing me a dual boot with windows xp, and ubuntu. When the download finished, it told me to reboot, but when i rebooted, it went straight to windows. Nothing was done, or guided me to ubuntu. I found some files for ubuntu on my c drive, and contained a few folders there, and none of those said to be ISO. This was the second time i done this, and both did the same. I do not know where to go from there, and hate to do this for the 3rd time, and same thing to happen. Can someone guide me to correct this? thanks,          Jimmy

---

### Post by seamushc on 2009-10-07
My understanding of Wubi is that it sticks a new entry into the default windows bootloader that chainloads grub (linux bootloader).  Try the following:

1. Go to add/remove programs and make sure that ubuntu is listed in there.
2. Right click on my computer and click properties->advanced->startup and recovery->settings and make sure that the windows boot loader is giving you a chance to select somthing other then windows (make sure the first two options are checked and on for a few seconds)

Also, when you run wubi, do you notice it downloading the iso?

---

### Post by jimbo160 on 2009-10-07
ubuntu is in my add/remove page, but only shows 2.04MB in size, is that ok? my default start up option is windows xp, and there is ubuntu there. this is the reading i got for manual.....[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\wubildr.mbr = "Ubuntu"
.......
           I am at a lose on all this, but if you will help me, maybe i can find something. When the program was downloading from wubi, at the top of the graph, showing time remaining, there was a name above that , "downloading ubuntu 9.04 ISO". I only assume it is ISO, for the files i see that was downloaded, do not say, ISO
          I will work with this for awhile to make it work, and if not, i will search for something other than ubuntu. If you can help me, i would appreciate.

---

### Post by QIII on 2009-10-07
Please remember that Wubi is not a final solution and is best used as a chance to "test it out".

Your difficulties with Ubuntu at this point are somewhat more indicative of your Wubi install than they are Ubuntu itself.

Someone will be able to help you, I am certain.

But don't confuse Wubi issues with the relative value of Ubuntu itself.

---

### Post by BQAggie2006 on 2009-10-07
> timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW  S
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro  soft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\wubildr.mbr = "Ubuntu"Since your timeout is set to 0 and your loader defaults to Windows, it will not present you with boot options and boot straight into Windows. You will need to change your timeout to equal 5. Once you change this and reboot, you should be presented with the option to boot into either Windows or Ubuntu.

---

### Post by abelbrito on 2009-10-07
can someone walk me through installing the ath5k or ath9k driver? in the driver manager it says that the  madwifi driver has been disabled but is still in use. and every time i click on activate i get the same story. how  do i fix this?
running on a compaq presario f700. 
thanks :)

---

### Post by CaptainMark on 2009-10-07
an easier way to setup a proper dual boot would be to install ubuntu from an ubuntu live cd and follow the options for dual booting. this way the linux bootloader is first used and that recognises the windows partition, ive heard if you use the windows bootloader it will only recognise windows partitions. I havent done this myself so i dont know how true it is.

---

### Post by jimbo160 on 2009-10-07
i saw the time factor there, changed it, rebooted, and wha lha. There it was, my option for windows or ubuntu. It started loading up, got to grub>, and there was a flashing mark that i let flash for 20 minutes. I do not know if it does anything or not. If that gives you a clue on something, let me know.
       I also am considering the other thread, for a disc would be a safe investment for future use of ubuntu. Can you give me a good place to start with downloading ubuntu again, and putting it on a disc. If there are any special instructions you can share with me about doing this, please share with me. I am just an ole man that is unfamiliar with these new machines. Thanks,        Jimmy

---

### Post by orngjce223 on 2009-10-07
You can actually order a free Ubuntu disc.  Just poke around on the website.

Also, for the record, it's spelled "voila".  :D

---

### Post by jimbo160 on 2009-10-07
The free disc would take up to 10 weeks. That is to long for me. Can the images i have already downloaded be converted to Iso and burnt to a disc? Also, i am sorry for the grammer, for it all means the same to me. he he he

---

### Post by BQAggie2006 on 2009-10-07
You can go here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) to download the Ubuntu ISO. Make sure you select a location to download from before you click the Begin Download Button.

Once your download has finished, you can go here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) for instructions on how to burn the ISO to a CD.

And finally, once you have your CD burned and are ready to perform a dual-boot installation, you can go here: [https://help.ubuntu.com/9.04/switching/dualboot.html](https://help.ubuntu.com/9.04/switching/dualboot.html) for instructions

---

