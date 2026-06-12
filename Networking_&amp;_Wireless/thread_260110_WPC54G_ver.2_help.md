---
title: "WPC54G ver.2 help"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by Melcar on 2006-09-18
I'm trying to get a WPC54G Ver.2 to work.  I already looked at several older threads about the subject and the closest I got was with this [http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g]("http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g").
The card is being detected and I can even perform scans with it (iwlist shows all available networks, including mine), but I can't connect.

---

### Post by Melcar on 2006-09-19
Anybody?

---

### Post by clcoyle on 2006-09-19
I'm a Noob, but I'll pass along what confusing little I think I know.

I got mine to work using this process plus some fiddling, not sure exactly what the finishing touch was, but it was more than just the 4 steps in the how-to.  

I do know that I re-booted at some point, and I also de-activated and re-activated wlan0 in the network manager.  

I just had to play this game again, because I was messing with it trying to get it working with Samba, and I torched something in the process and lost control of the wlan card.

An hour ago, I got it working, and I still don't know exactly what the catch was, although in the end, it was the second time around with steps 1-4 that got it working.  

I couldn't ping the AP, nothing.  This may not be your problem, but it only takes a few minutes to run through the 4 steps (cut-n-paste the commands, don't try to type them in like I did at first) and re-boot.

HTH,

Lee

---

### Post by Melcar on 2006-09-20
Still have not gotten it to work.  Yesterday I tried this:
- Stop the default module for the card
  
      sudo modprobe -e acx

- Add it to the blacklist

      sudo mousepad /etc/modprobe.d/blacklist

- Install ndiswrapper; install the driver for the card (I extracted the entire contents of the .zip file onto the desktop just in case)

      sudo ndiswrapper -i lsbcmnds.inf

- Checked that everything was fine

      ndiswrapper -l
      lsbcmnds installed   Hardware present

- Loaded up ndiswrapper (this step gives me errors; something about an invalid argument)

      sudo modprobe ndiswrapper

As I understand it Xubuntu should now be using ndiswrapper instead of the default module, but when I do a lshw the wireless card shows as "Unclaimed" and the little lights on the card are off.  Keep in mind that with the default acx driver I can at least scan for networks.

**Edit**: When I do a modprobe of ndiswrapper I get "Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument"

---

### Post by Melcar on 2006-09-20
Bump

---

### Post by alex_mayorga on 2006-09-22
Please see [http://www.ubuntuforums.org/showpost.php?p=1530644&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1530644&postcount=6) for the fix.

Hope it works for you as well.

---

### Post by CCPhil on 2006-11-05
I'm having similar trouble with this card using xubuntu edgy (actually installed ubuntu edgy 1st - same problem).
Heres a clip from syslog

Nov  5 20:31:19 ubuntu3 kernel: [ 5422.338867] pccard: CardBus card inserted into slot 0
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.748641] acx: Loaded combined PCI/USB driver, firmware_ver=default
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.748671] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.752245] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.752291] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.753141] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x12020000, phymem2:0x12000000, mem1:0xcea24000, mem1_size:8192, mem2:0xcebc0000, mem2_size:131072
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.809513] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Nov  5 20:31:20 ubuntu3 firmware_helper[4244]: main: error loading '/lib/firmware/acx/default/tiacx111c16' for device '/class/firmware/0000:02:00.0' with driver 'acx_pci'
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.830912] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.830944] acx: reset_dev() FAILED
Nov  5 20:31:20 ubuntu3 firmware_helper[4247]: main: error loading '/lib/firmware/acx/default/tiacx111' for device '/class/firmware/0000:02:00.0' with driver 'acx_pci'
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.846630] acx_pci: probe of 0000:02:00.0 failed with error -5
Nov  5 20:31:20 ubuntu3 kernel: [ 5422.848648] usbcore: registered new driver acx_usb

I have no acx dir under /lib/firmware
I have seen related posts suggesting link(s) be created to the correct location - these dont seem to work in this case

Any help is appreciated

---

### Post by squibT on 2006-11-05
***************************************************************************************************
    * If you have acx module loaded.... acx module interferes with windows driver, we need to remove it if it is found. 

lsmod | grep acx

    * Remove the acx module if found. It could also be acx_pci or similar. Please Note: New kernel updates will auto load the acx module again. So repeat the following two commands every time the kernel is updated. 

sudo rmmod acx
sudo mv /lib/modules/2.6.15-26-386/kernel/drivers/net/wireless/acx /root/
***************************************************************************************************

[http://www.ubuntuforums.org/showthread.php?t=292317&highlight=naiya](http://www.ubuntuforums.org/showthread.php?t=292317&highlight=naiya)

---

### Post by dmizer on 2006-11-06
if you have edgy installed, you shouldn't have to do any configuration what so ever to get this card to connect.

i would avoid using ndiswrapper because the windows driver has case sensitive file naming issues that are difficult to find and resolve.

i was using ndiswrapper in breezy to get this card to work, but it broke during an update and i have not since been able to make it work correctly.

edit: op posted this way back in september and no updates.  i think this one is dead.

---

