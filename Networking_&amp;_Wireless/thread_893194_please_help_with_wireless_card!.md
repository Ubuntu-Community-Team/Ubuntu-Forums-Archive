---
title: "please help with wireless card!"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by tankandre on 2008-08-18
I have a compaq presario v6000 with a 802.11 b/g card. I installed wubi, so now i have hardy and vista side by side. Everything worked fine but the wireless card, which is a "**Broadcom Corporation BCM94311MCG wlan mini PCI (rev 81)** doesnt work. Hardy told me to download a driver for this card to work, and i did, but wubi froze completly, and then shut down. I turn my laptop back on, but 2 seconds after, it will turn off by itself. It only turned on with the charger cable removed. That was really weird. Well, now my card is disabled and after reading through many guides about ndiswapper and fwcutter, i do not know what to do. The only thing i have done is install flash player for youtube. I am new to linux, so an easy guide will be really good. Thx a million.

---

### Post by Ayuthia on 2008-08-18
> **tankandre said:**
> I have a compaq presario v6000 with a 802.11 b/g card. I installed wubi, so now i have hardy and vista side by side. Everything worked fine but the wireless card, which is a "**Broadcom Corporation BCM94311MCG wlan mini PCI (rev 81)** doesnt work. Hardy told me to download a driver for this card to work, and i did, but wubi froze completly, and then shut down. I turn my laptop back on, but 2 seconds after, it will turn off by itself. It only turned on with the charger cable removed. That was really weird. Well, now my card is disabled and after reading through many guides about ndiswapper and fwcutter, i do not know what to do. The only thing i have done is install flash player for youtube. I am new to linux, so an easy guide will be really good. Thx a million.

Here is a guide for installing the b43 driver:
[http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

Here is one for ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If you want to try and troubleshoot what you have, can you go into the Terminal and post the results of:
```
lshw -C network
```

Also, did you add any boot parameters (noapic, etc.)?  It sounds like you might have an interrupt conflict.

---

### Post by tankandre on 2008-08-18
*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:5e:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

this is what i get with the lshw c network command. I haven't tried the forums yet, cause there's a hurricane where i live. Thx for the quick reply, and no, i don't have noapic or something like that, and that error that happened never occurred again.

---

### Post by falcon61102 on 2008-08-18
Ok, it looks like you don't have any drivers installed for your wireless card, which is good because you can start fresh.  I highly recommend the second link that Ayuthia posted for you.  While it looks a little clutterred, it is a very good guide.  It lists a bunch of different drivers on the site, you just need to find the one for your card, just look for BCM4311 and you should be good to go.  If you have any questions or get any errors, just post them here and we'll help.

---

### Post by Ayuthia on 2008-08-18
> **tankandre said:**
> *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:5e:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

this is what i get with the lshw c network command. I haven't tried the forums yet, cause there's a hurricane where i live. Thx for the quick reply, and no, i don't have noapic or something like that, and that error that happened never occurred again.

If you have a working wired connection, I would check and see if System->Administration->Hardware Drivers to see if there is an option for Broadcom.  If there is, enable it.  If there is not, then you will need to install it by doing this in the Terminal:
```
sudo apt-get install b43-fwcutter
```

---

### Post by tankandre on 2008-08-18
Before i wrote the first message, ubuntu offered b43 fwcutter through the hardware drivers menu, but then my computer froze and turned off. I followed the second guide given to me by ayuthia, but when i get to the hardy bug fix, i still receive the module=ssb message even after the fix. Was i supposed to run the third step, and then check with "lshw -C network"? Or check first, fix the bug, and then the bug fix. I did the bug fix first, but i still got the module ssb message. Is there anything else i could try? ( I found out that my wireless is "14e4:4318 (rev 02)" so i ran step 2a before step 3. Thank you for all of your efforts!

---

### Post by falcon61102 on 2008-08-18
Try doing the Hardy Bug Fix, except don't reload the SSB module.  When you are going through the fix, don't use the line that says:
```
sudo modprobe ssb
```

See if that works for you.

---

### Post by tankandre on 2008-08-18
The update-modules command is deprecated and should not be used!

I got this message when i did step 3 of ayuthia's second guide before doing the hardy bug check, so i won't mess with it any longer. Please help

---

### Post by falcon61102 on 2008-08-18
Can you be a little more specific when you say Step 3.  There are many lines of code in that step, which one actually gave you the error?

---

### Post by tankandre on 2008-08-19
thank you so much falcon 61102. Removing the sudo modprobe ssb line made my wireless work right away. To make this permanent i follow the how to make permanent version 0.3 of the guide right? (The second guide posted by Ayuthia) I did the commands in this order. step 1, step 2a, hardy bug fix, step 3, and then make permanent.

---

### Post by falcon61102 on 2008-08-19
Just make sure when you do those steps to leave out the line that says:
```
modprobe ssb
```

It's embedded in the line of code there, so just leave it out before you run that code.

---

### Post by tankandre on 2008-08-20
After reboot the changes are not permanent, and my wireless does not work anymore.  now when i do the hardy fix, the first line (which is sudo rmmod 43) causes my computer to reboot. Can i omit this line and modprobe ssb too? Please, i really need to get this wireless working

---

### Post by falcon61102 on 2008-08-20
Go back through the Hardy Fix again and be careful with the code because the line you printed is not in it.  Remember to not use the line that says:
```
sudo modprobe ssb
```

Also, to make it permanent, run the following lines instead of the one posted:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

See if that works for you.

---

### Post by Ayuthia on 2008-08-20
> **tankandre said:**
> After reboot the changes are not permanent, and my wireless does not work anymore.  now when i do the hardy fix, the first line (which is sudo rmmod 43) causes my computer to reboot. Can i omit this line and modprobe ssb too? Please, i really need to get this wireless working

If you are still having problems with the b43 module doing funny things, you can try moving the firmware out of /lib/firmware:
```
sudo mv /lib/firmware/b43 $HOME
sudo mv /lib/firmware/b43legacy $HOME

```
This will move the b43 and b43legacy folders from /lib/firmware to your home directory.  This will make your b43 module no longer operate so in theory, it will no longer cause your computer to freeze or reboot.  Once you move the files, reboot because I think the modules already have the firmware in memory.

---

### Post by tankandre on 2008-08-21
First of all thx u guys for all or ur help. This is what happens. I follow step 1, I copy everything exactly. I get messages like file arleady exists and no need to upgrade. So far so good. Then I follow step 2a. After that, when step 3 comes up, I do the lshw -C network command and I get:

*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 **module=ssb**
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:5e:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

So before doing step 3, I do the hardy bug fix. This used to work before. My wireless worked twice after falcon 61102's advice. But it never persisted after reboot. But now this is what happens. The first line of the hardy bug fix is this one 

**sudo rmmod b43**

I copy this option, and after I press enter, my computer freezes completely, and I have to pull out the battery. I am running hardy on wubi, so I know hard reboots are nasty on wubi, so I don't want to do this anymore. Here are the messages I get when doing step 1:

art@art-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for art: 
blacklist bcm43xx
art@art-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.
art@art-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/art/bcm43xx': File exists
art@art-laptop:~/bcm43xx$ 


now step 2a:

art@art-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.
art@art-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--16:50:58--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe.4'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [<=>                                  ] 4,494,456    376.60K/s             

16:51:13 (305.48 KB/s) - `sp34152.exe.4' saved [4494456]

art@art-laptop:~/bcm43xx$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
art@art-laptop:~/bcm43xx$ 


After this I do the hardy fix, my computer freezes on the first command. Can i skip the first command, or is this happening because I have done this several times already? Thank again!

---

### Post by Ayuthia on 2008-08-21
> **tankandre said:**
> First of all thx u guys for all or ur help. This is what happens. I follow step 1, I copy everything exactly. I get messages like file arleady exists and no need to upgrade. So far so good. Then I follow step 2a. After that, when step 3 comes up, I do the lshw -C network command and I get:

*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 **module=ssb**
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:1b:5e:a0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

So before doing step 3, I do the hardy bug fix. This used to work before. My wireless worked twice after falcon 61102's advice. But it never persisted after reboot. But now this is what happens. The first line of the hardy bug fix is this one 

**sudo rmmod b43**

I copy this option, and after I press enter, my computer freezes completely, and I have to pull out the battery. I am running hardy on wubi, so I know hard reboots are nasty on wubi, so I don't want to do this anymore. Here are the messages I get when doing step 1:

art@art-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for art: 
blacklist bcm43xx
art@art-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.
art@art-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/art/bcm43xx': File exists
art@art-laptop:~/bcm43xx$ 


now step 2a:

art@art-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 98 not upgraded.
art@art-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
--16:50:58--  [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
           => `sp34152.exe.4'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... done.    ==> RETR sp34152.exe ... done.

    [<=>                                  ] 4,494,456    376.60K/s             

16:51:13 (305.48 KB/s) - `sp34152.exe.4' saved [4494456]

art@art-laptop:~/bcm43xx$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
art@art-laptop:~/bcm43xx$ 


After this I do the hardy fix, my computer freezes on the first command. Can i skip the first command, or is this happening because I have done this several times already? Thank again!

The thing is that you need to remove the b43 module or else ndiswrapper will not work.  Can you post the results of:
```
ls /lib/firmware/b43
```
I would like to see if there is firmware out there or not.

EDIT:
By the way, ndiswrapper is installed ok and it looks like you have the right driver.  It is a matter of figuring out how to safely remove the b43 module.

---

### Post by tankandre on 2008-08-21
alright, heres is the result of me running **ls /lib/firmware/b43:**

art@art-laptop:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory
art@art-laptop:~$

---

### Post by Ayuthia on 2008-08-21
> **tankandre said:**
> alright, heres is the result of me running **ls /lib/firmware/b43:**

art@art-laptop:~$ ls /lib/firmware/b43
ls: cannot access /lib/firmware/b43: No such file or directory
art@art-laptop:~$
Ok.  Can you now post the following (I forgot to ask earlier):
```
lspci -nnd 14e4:*
cat /etc/modprobe.d/blacklist |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
cat /etc/modules |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
```
The lspci -nnd 14e4:* should only show one card.  If it shows more than one, you might have a card that uses the b44 module.

/etc/modprobe.d/blacklist should have the following:
```
blacklist b43
blacklist bcm43xx
```
/etc/modules should only have:
```
ndiswrapper
```

If all this looks fine, we are going to do the following:
```
sudo update-initramfs -u
```
This will update the blacklist info in the initramfs (used when booting).

---

### Post by tankandre on 2008-08-21
OK. Here is what i get when i type the commands you suggested:

art@art-laptop:~$ lspci -nnd 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
art@art-laptop:~$ cat /etc/modprobe.d/blacklist |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
art@art-laptop:~$ cat /etc/modules |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
ndiswrapper
ndiswrapper
art@art-laptop:~$ 

should i run the sudo update?

---

### Post by Ayuthia on 2008-08-21
> **tankandre said:**
> OK. Here is what i get when i type the commands you suggested:

art@art-laptop:~$ lspci -nnd 14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
art@art-laptop:~$ cat /etc/modprobe.d/blacklist |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
art@art-laptop:~$ cat /etc/modules |grep -i -e b43 -e ssb -e ndiswrapper -e bcm43xx -e wl
ndiswrapper
ndiswrapper
art@art-laptop:~$ 

should i run the sudo update?

Not yet.  You need to do the following:
```
echo blacklist b43|sudo tee -a /etc/modprobe.d/blacklist
echo blacklist ssb|sudo tee -a /etc/modprobe.d/blacklist
```

After that, you can do:
```
sudo update-initramfs -u
```
Then you should reboot.  Hopefully that will remove the b43 and load the ndiswrapper module.

---

### Post by tankandre on 2008-08-21
I did everything you said, and after reboot, the wireless light turned on and now the wireless worx. YEEEEEEEEEES! Thank you so much. Will this be permanent?

---

### Post by Ayuthia on 2008-08-21
> **tankandre said:**
> I did everything you said, and after reboot, the wireless light turned on and now the wireless worx. YEEEEEEEEEES! Thank you so much. Will this be permanent?

It should be since you rebooted and the light turned on!  Congratulations!

---

