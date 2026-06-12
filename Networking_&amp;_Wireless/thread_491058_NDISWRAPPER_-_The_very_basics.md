---
title: "NDISWRAPPER - The very basics"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by newbun on 2007-07-03
I've have Ubuntu 7.04 installed, and I read somewhere on this forum that  NDISWRAPPER doesn't come as standard??  So I downloaded 1.47 and did this in terminal: 

tar -zxvf ndiswrapper-1.47.tar.gz  (following instructions from the ndiswrapper site)

Then I did:      cd ndiswrapper-1.47

My questions are:   Has it now been installed?? Where is it? And what exactly does it do???  

Basic language please.

---

### Post by tolgayucel on 2007-07-03
Hi,
I have also the problem of using my wireless card. In one of the threads I read that I have to install "ndiswrapper", though it didn't work through the terminal command. The easiest way to install it through "Synaptic Package Manager". Just search for "ndiswrapper" and install "ndiswrapper-common". I haven't tried it yet but will post my result.
Cheers
Tolga

---

### Post by spd106 on 2007-07-03
Try reading this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Although the userspace utilities (ndiswrapper-utils) aren't included in a default install, the kernel modules are (i.e. /lib/module/`uname -r`/kernel/drivers/net/ndiswrapper.ko)

This is confusing for some, but is probably the easiest way that it can be packaged for painless installation without requiring kernel headers and having to run make && make install etc.

I believe it comes down to a trade off between usability for those that need ndiswrapper and not taking up space unnecessarily for those that don't.

---

### Post by tolgayucel on 2007-07-03
I have installed the remaining packages related to "ndiswrapper", which are [COLOR="Red"]***"ndisgtk" , "ndiswrapper-source" ***[/COLOR]and[COLOR="Red"]*** "ndiswrapper-utils 1.9"***[/COLOR]. I tried again but wasn't successful to connect through the wireless. 
The system asks me all the time the "WEP" key 128 and 64 bit, which i type and can't connect.
No idea what is wrong.
I have an Intel(R) Pro/Wireless 3945 and the restricted drivers are installed. I read all the threads regarding this card but no solution:(
Cheers

---

### Post by tolgayucel on 2007-07-03
Hi, 
I am trying to use the command "dldrconfig linux-2.6.16-16kstack.patch", I get a message "***[COLOR="Red"]bash: dldrconfig: command not found[/COLOR]***".
I found my wireless card in the list of devices supported by "linux".

   [COLOR="Blue"]1.
      Card: Intel PRO/Wireless 3945ABG

    *
      pciid: 8086:4222
    *
      Driver: version 10.1.0.13 [http://www.intel.com/support/wireless/wlan/sb/cs-010623.htm](http://www.intel.com/support/wireless/wlan/sb/cs-010623.htm) (w39n51.inf, unfortunatly the download is 80MB because it’s packaged with “Intel PROset/Wireless software”, and drivers for the 2200BG and 2915ABG)
    *
      Other: Tested on Gentoo Linux, with gentoo patched kernel 2.6.15-r1 (SMP hasn’t been tested yet, I had some problems with it, so reverted to non-SMP). You need to patch your kernel to use 16K Stacks (rather than the default 8K). Patches can be found via LinuxAnt. I found mine at [http://www.linuxant.com/driverloader/wlan/downloads-patches.php](http://www.linuxant.com/driverloader/wlan/downloads-patches.php)

   [/COLOR]

---

