---
title: "USB Wireless RAILINK"
date: 2008-01-29
forum: Networking &amp; Wireless
---

### Post by shawfield on 2008-01-29
Before I installed Ubuntu on the hard disk, I ran it from the LiveCD & it immediately detected my EdiMax USB wireless dongle & networking was instantly available.

Having installed to the hard disk however, it now fails to recognise it. Trying to use 'manual config' via the desktop, doesnt work either.

I have several linux drivers on the driver CD that came with the Edimax, but cant see anyway to instal them.

Those available on the CD are SUSE, DEBIAN, FEDORA, MANDRAKE

How can I load them ?
Many Thanks

---

### Post by wieman01 on 2008-01-29
Thing is... The current Gutsy drivers are flawed and don't work for the majority of users. You are in all likelihood one of the unfortunate ones.

_You have 3 options though:_

1. Install Ubuntu Feisty Fawn instead. The Ralink drivers that come with it are fine.
2. Try my Ralink guide (see signature for more).
3. Try other tutorials available in the forums.

---

### Post by shawfield on 2008-01-29
Thanks for that.

Just for my information...
Any thoughts why the drivers work on LiveCD but not on the HD install ?

---

### Post by rklauco on 2008-01-29
It seems like kernel issue - starting old kernel, the card works just fine for me (PCMCIA version), newer kernel fails with error message about 80211 stack in dmesg output.

---

### Post by wieman01 on 2008-01-29
> **rklauco said:**
> It seems like kernel issue - starting old kernel, the card works just fine for me (PCMCIA version), newer kernel fails with error message about 80211 stack in dmesg output.
Yes, that's what I have heard as well.

Kernel version 2.6.24 will come with a number of new WLAN drivers, in particular Ralink ones. So watch out for the next release of Ubuntu (Hardy Heron).

---

### Post by shawfield on 2008-01-29
Oh dear...

Downloaded & Installed "Fiesty Fawn" Ubuntu release, & that doesnt even recognise the wireless device on LiveCD. so I am not not keen on an HD install.

Is there not a way to simply install the 'Debian' Linux driver on the CD that came with the Device ?

Thanks in anticipation

---

### Post by rklauco on 2008-01-29
Well, from my perspective, it should be very easy to install Gutsy and simply boot the original kernel from the installation - simply press escape during the grub boot prompt and select the oldest kernel available.

---

### Post by shawfield on 2008-01-29
Thanks for replying.

I tried your suggestion but there is only one Kernel available. 
2.6.22-14-generic. so no joy there.

Is there not a command to simply load the driver I have on CD for Debian Linux ?

By the way, I tried the various commands in the Railink wireless thread, but when I got to the unzip part, the system reports that the driver zip is not there ( blacklisting etc works ok ).

Thanks

---

### Post by wieman01 on 2008-01-29
> **shawfield said:**
> Thanks for replying.

I tried your suggestion but there is only one Kernel available. 
2.6.22-14-generic. so no joy there.

Is there not a command to simply load the driver I have on CD for Debian Linux ?

By the way, I tried the various commands in the Railink wireless thread, but when I got to the unzip part, the system reports that the driver zip is not there ( blacklisting etc works ok ).

Thanks
What driver have you got there? What's there name and suffix? It's by all means worth a shot.

---

### Post by shawfield on 2008-01-29
The driver is the same as the one available from the manufacturer on its website

RT73_linux_STA_drv1_0_4_0.zip is from the manufactuers website
RT73_Linux_STA_Drv1.0.4.0.tar.gz is fro the CD 

I copied both of them to the GUI desktop in preparation

Cheers

---

### Post by wieman01 on 2008-01-29
> **shawfield said:**
> The driver is the same as the one available from the manufacturer on its website

RT73_linux_STA_drv1_0_4_0.zip is from the manufactuers website
RT73_Linux_STA_Drv1.0.4.0.tar.gz is fro the CD 

I copied both of them to the GUI desktop in preparation

Cheers
OK, what's inside the ZIP files? And are there any instructions posted on the vendor's website?

---

### Post by shawfield on 2008-01-29
The file ending 'tar.gz' is contained in the zip

Cant find anything but windows instructions on support website.

Is there not a standard Linux app to install new drivers ?

---

### Post by shawfield on 2008-01-29
ok, I've found the files in the ZIP now :

defconfig
driver_railink.c
driver_railink_h
drivers.c
makefile
README
WPA_Supplicant_example.conf

The instructions are way beyond my knowledge & call for a program called WPA_supplicant to be downloaded & then the 'defconfig' file to be modifed, then updating the 'drivers.c' file with code they provide, then editing the 'makefile', then compiling the source code ( which fills me with fear ! ).

I now recall, why, 5 years ago, I gave up on linux ! :-)

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> ok, I've found the files in the ZIP now :

defconfig
driver_railink.c
driver_railink_h
drivers.c
makefile
README
WPA_Supplicant_example.conf

The instructions are way beyond my knowledge & call for a program called WPA_supplicant to be downloaded & then the 'defconfig' file to be modifed, then updating the 'drivers.c' file with code they provide, then editing the 'makefile', then compiling the source code ( which fills me with fear ! ).

I now recall, why, 5 years ago, I gave up on linux ! :-)
I don't think I will be able to help you with compiling the driver... Sorry. The only thing I can offer at the moment is my own Ralink tutorial. If you want to try it, let me know.

---

### Post by shawfield on 2008-01-30
I tried your tutorial yesterday & only managed to get various CD Rom errors

The first command < sudo apt-cdrom add> works ok & tells me that 2 packages were found but suggests I should repeat this command for all disks in the set. There are no other disks.

The second command <sudo apt-get update > gives about 20 error messages about not being able to resolve 'http://gb.archive.ubuntu.com', followed immediately by a simialr number of error messages about 'could not resolve security.ubuntu.com'

So it seems to be trying ot get ot the internet for some reason, but of course there is no internet, as the wireless drivers wont work.

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> I tried your tutorial yesterday & only managed to get various CD Rom errors

The first command < sudo apt-cdrom add> works ok & tells me that 2 packages were found but suggests I should repeat this command for all disks in the set. There are no other disks.

The second command <sudo apt-get update > gives about 20 error messages about not being able to resolve 'http://gb.archive.ubuntu.com', followed immediately by a simialr number of error messages about 'could not resolve security.ubuntu.com'

So it seems to be trying ot get ot the internet for some reason, but of course there is no internet, as the wireless drivers wont work.
Could you get a **wired** internet connection to work?

---

### Post by shawfield on 2008-01-30
Yes I have now had to move the PC to a different room so I can plug into the Router. Online now.

I'll report back

---

### Post by shawfield on 2008-01-30
When I reach "unzip RT73usb.exe", I get a 'not found' error.
Repeating this with "unzip /home/mike/rt73usb.exe" I get the same error.

Where is the driver file supposed to be ?

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> When I reach "unzip RT73usb.exe", I get a 'not found' error.
Repeating this with "unzip /home/mike/rt73usb.exe" I get the same error.

Where is the driver file supposed to be ?
Inside the EXE file. Could you extract it using Windows? You need to get hold of the 2 files mentioned in the tutorial. If that fails, I will try to find out where Windows puts them (i.e. in which directory) and post instructions here later on.

---

### Post by shawfield on 2008-01-30
Now you've really lost me. I dont have Windows on this PC.

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> Now you've really lost me. I dont have Windows on this PC.
There are Windows driver files inside that file. So we somehow need to extract them, be it using Unzip or by installing your wireless adapter on a Windows machine. Unless we retrieve those file, we cannot install your device. Does that make more sense? Is there a driver ZIP file also available by chance?

---

### Post by shawfield on 2008-01-30
I found an RT73usb folder in the path, /etc/ndiswrapper, but the folder is empty. 

There are also RT73usb files with extensions 'ko' & 'bin'.
The former in /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00
The latter in /lib/firmware/2.6.22-14-generic

Not sure that helps much

---

### Post by shawfield on 2008-01-30
I tried unzipping the RT73_lunux_sta_drv1_0_4_0.zip that I copied to my desktop from the Edimax driver disk, but I get the same error message about 'unzip' not being able to find it, which is strange since I can see it onmy desktop, so its definitely there

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> I found an RT73usb folder in the path, /etc/ndiswrapper, but the folder is empty. 

There are also RT73usb files with extensions 'ko' & 'bin'.
The former in /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00
The latter in /lib/firmware/2.6.22-14-generic

Not sure that helps much
No, these are the modules loaded by default. Nothing to do with the Windows files.

Inside the EXE, there should be 3 files:

1. .cat
2. .sys
3. .inf

These are the files that we need...

---

### Post by shawfield on 2008-01-30
Sounds like a dead duck to me.

No rt73usb.exe or zip file anywhere on the Ubuntu disk or installed to the 'file system'.
The zip file from the manufacturers  driver disk extracts ok, but only contains WEP_Supplicant.exe & various other files mentioned earlier in the thread. No .inf or anything similar.
Sounds like I have to wait for a version of linux that actually detects the RAIlink device.

Thanks anyway

---

### Post by wieman01 on 2008-01-30
> **shawfield said:**
> Sounds like a dead duck to me.

No rt73usb.exe or zip file anywhere on the Ubuntu disk or installed to the 'file system'.
The zip file from the manufacturers  driver disk extracts ok, but only contains WEP_Supplicant.exe & various other files mentioned earlier in the thread. No .inf or anything similar.
Sounds like I have to wait for a version of linux that actually detects the RAIlink device.

Thanks anyway
You need to download the Windows XP driver file for 32-bit systems. That's the one I am talking about. Any luck?

---

### Post by royleith on 2008-01-30
I have found that,

Ubuntu 7.10, kernel 2.6.20-16-generic, dated 23/09/2007

works fine, but

Ubuntu 7.10, kernel 2.6.22-14-generic, dated 18/12/2007

seems to initialise, but does not make the wireless connection.

My wireless card details are,

 00:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
 Subsystem: Micro-Star International Co., Ltd. Unknown 802.11g mini-PCI Adapter
 Flags: bus master, slow devsel, latency 64 IRQ 22
 Memory at d2204000 (32-bit, non-prefetchable) [size=8k]
 Capabilities <access  denied>

I got the 2.6.20-16 kernel from the Gutsy Gibbon installation DVD. I assume that you can download and burn the CD ISO to a CD-R and copy the files to  /boot/  for this kernel version. 'sudo kate' or 'sudo gedit' the file /boot/grub/menu.lst and add the additional boot option to the top of the list of options. I'm not sure if you can just copy the existing System.map2.6.22-14-generic file as System.map2.6.20-16-generic. The alternative would be to do a new install from the CD.

Regards
Roy Leith

---

