---
title: "Dell wireless 1450 wireless USB adapter"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by hammanrj on 2006-12-28
Hi.

I recently installed ubuntu 6.10 on a dell computer. It's great, however, I still cannot get the wireless USB adapter working. because of this, I have to internet access on the machine. I can get files on to it through a usb drive I have. The wireless adapter is called: "Dell Wireless 1450 Wireless USB adapter. Please give me some instructions on how to fix it as soon as possible.

Thanks in advance :KS

---

### Post by hammanrj on 2006-12-28
*Bump*

Anyone? please?

---

### Post by Silentvoice on 2006-12-29
Dell is really bad about not releasing their wlan specs, so you will most likely have to use ndiswrapper to load and modprobe into the kernel.

Lucky for you the ndiswrapper wiki list of known devices to work does clarify that this device has worked before. ubuntu comes with a precompiled version of ndiswrapper already with your kernel, so the hardest part is done for you (that is constantly guess and checking different versions of ndiswrapper)

All information I am about to tell you can also be found on the ndiswrapper wiki 
( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page) )

first of all open your terminal and do sudo apt-get ndiswrapper-utils

This will install a perl script (that normally comes with ndiswrapper) that allows you to modify in user space the kernel space module ndiswrapper.ko

apt should automadically put this in your path, so once this is installed, go ahead and extract out DELLNIC.INF from the CD that came with your usb device (or see if you can download it somewhere)

next issue these commands in the directory that the driver is in:

ndiswrapper -i DELLNIC.INF (This loads the windows driver into ndiswrapper)

next do

ndiswrapper -l

If this says Device loaded, hardware present, you're good to go just do these commands next

sudo depmod -a

If this command turns no errors, go ahead and do the next command below. (this is just a saftey net of sorts.. always be careful when messing with kernel modules and double check your work at all times)

sudo modprobe ndiswrapper

now do iwconfig and see if your wireless extension showed up, if not print out a dmesg and post it here and it can probably be fixed.

*edit* I just realized apt-get will require an internet connection, I kind of lose my common sense sometimes.  Try to download it from here [http://archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper-1.1/](http://archive.ubuntu.com/ubuntu/pool/universe/n/ndiswrapper-1.1/)  and move it over. then do sudo dpkg -i thepackage.deb

after that all instructions above still apply.

---

### Post by hammanrj on 2006-12-29
Thanks a lot!

I managed to get ndiswrapper working, but I've lost the CD with the drivers (dellnic.inf)!

Do you know any place I could get these drivers?

Thanks again!

---

### Post by hammanrj on 2006-12-29
Okay, I managed to find the drivers, and followed your steps. There were no errors, but my wireless won't work. I tried:

```
iwlist eth2 scan
```

It returned eth2: no scan results returned](*,) 

(or something like that)
Please reply asap, as I need to get it working quite soon!

Thanks again!;)

---

### Post by Silentvoice on 2006-12-29
well first copy out a dmesg for me after you modprobe ndiswrapper, and an iwconfig as well.

although this does mean that your device is getting some base functionality, otherwise iwlist would return "Device does not support scanning"

---

### Post by jamesstansell on 2006-12-30
I haven't used ndiswrapper (yet) but from my reading it always uses wlan0 for the devicename.  So try ```
iwlist wlan0 scan
``` and if that doesn't work try it with sudo: ```
sudo iwlist wlan0 scan
```

---

### Post by Silentvoice on 2006-12-30
OH yeah I didn't even notice that. ndiswrapper always does wlan0 for the device.

---

### Post by jvanoort05 on 2007-10-15
thanks it worked great. I have this wireless adapter and gusty 7.10 but is only conected for 30s. I installed the ndiswrapper and it worked perfectly. :-) thanks again for the information.

---

### Post by HuoMaKe on 2007-12-08
I'm having the same problem with my slightly newer dell adapter (I think, but I haven't checked) and BOTH Ubuntu and Kubuntu 7.10 (recently decided that the adware was too much to keep Windows any more).
Does anyone know if it works with madwifi?

---

### Post by teague31 on 2007-12-15
I recently tried this and was able to get through the commands without returning any errors.  The system claims to be connected to the wireless network, but I can't actually load any web pages.  

iwconfig returns the following:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys-g"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:58:F2:55   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=79/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth2      IEEE 802.11b  ESSID:"Batuta"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:11:71:E0:30   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=15/92  Signal level=-71 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:63
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If i try iwconfig again...maybe 10 minutes later, it returns the same thing except under wlan0 it says ESSID: "" and "Access point: Not Associated" and "Link Quality:0  Signal level:0  Noise level:0" rather than reporting the signal level

Anybody have any suggestions?

---

### Post by teague31 on 2007-12-15
Sorry, all those smiley faces that show up in my message are actually supposed to be [colon], character "O"

---

