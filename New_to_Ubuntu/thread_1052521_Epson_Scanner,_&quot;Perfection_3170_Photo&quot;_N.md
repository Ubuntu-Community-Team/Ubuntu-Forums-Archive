---
title: "Epson Scanner, &quot;Perfection 3170 Photo&quot; Need help with Driver"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Ronok on 2009-01-27
[SIZE="3"]Hi, about Epson Scanner, "Perfection 3170 Photo" 
I could use some help with the Driver [/SIZE]

**a**) getting the right driver or
**b**) making the driver work

**1**) the computer can "see" it with lsusb 

ronok@LuoDianNao:~$ lsusb
Bus 005 Device 005: ID 04b8:0116 Seiko Epson Corp. Perfection 3170 (GT-9400)

**2**) it is known to be a good working scanner so
**3**) I looked at the following links:

[SIZE="1"]
[http://manpages.ubuntu.com/manpages/intrepid/man5/sane-epson.5.html](http://manpages.ubuntu.com/manpages/intrepid/man5/sane-epson.5.html)

[http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=3170&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=3170&bus=usb&v=&p=)

[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)

[http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

[https://launchpad.net/ubuntu/intrepid/+source/sane-backends/1.0.19-6ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/sane-backends/1.0.19-6ubuntu1)[/SIZE]

**4**) the avasys site eventually gets to a download Question about:
.  (for gcc 3.4 or later)  / (for gcc 3.2/3.3)  ???
**5**) and after looking at the launchpad link 
**6**) I used the _packet manger_ myself to get the: "**1.0.19-6ubuntu1**"

I thought that would do it **but the scanner still wont scan** ??

what should I do next ?
Thanks

---

### Post by Ronok on 2009-02-05
hi 
**[SIZE="2"]I am still not able to use the Epson "Perfection 3170 Photo" scanner at all[/SIZE]**
[SIZE="2"]I really like Ubunto, but I dont know what to do next[/SIZE]
[SIZE="1"]I tried to get some "tar" files from here:
[http://alioth.debian.org/frs/?group_id=30186](http://alioth.debian.org/frs/?group_id=30186)
but I don't know what to do with them, or they might be the wrong thing[/SIZE]

I like Ubunto so much that I have talked other people in to using it
for them a new HP Deskjet Multifunction Printer/ Copier/ Scanner
Model: F4280 worked great right out of the box,

but I would like to get my:
Epson Scanner, "Perfection 3170 Photo"
to work, it was a higher quality scanner

I am willing to learn but I dont know a lot about:
tar.bal.diff.dsc.gz,  DFSG, GCC-version, CVS repository  
sorry, I am still very entry level
I really am not sure what is the next step to take?
Thanks

---

### Post by Elysia on 2010-02-19
I'm having the same problem getting Epson Perfection 3170 to work under Ubuntu 9.10. The system sees it, but the scanner software can't find it. Any suggestions please? I've installed iscan from the Avensys site and that's not helped. :confused:

---

### Post by arochester on 2010-02-19
Have you looked at [http://ubuntu.flowconsult.at/en/epson-3170-installation/9.04/](http://ubuntu.flowconsult.at/en/epson-3170-installation/9.04/) ?

---

### Post by Ronok on 2011-03-01
Hollo All
2 years ago started Trying to get the Epson to Scan 
with Ubuntu 8.04 up through and Currently:
Linux Kernel: 2.6.35-27-generic (i686)
Distribution: Ubuntu 10.10
Gnome: 2.32.0
and here is where things stand after looking at many Threads including

[http://ubuntu.flowconsult.at/en/epson-3170-installation/9.04/]("http://ubuntu.flowconsult.at/en/epson-3170-installation/9.04/") ---> Thanks: arochester
and others including:
[http://ubuntuforums.org/showthread.php?t=1028064]("http://ubuntuforums.org/showthread.php?t=1028064")

**[SIZE="3"]My Trouble shooting sequence of Epson "Perfection 3170 Photo"[/SIZE]** and
Some generic Trouble shooting tips for Scanners in general
I tried the following: (with CODE = user@computer:~$ enter it here)

**1)** 
first see where things stand Is the Scanner USB properly connected to the computer ?
```
lsusb
```
> Bus 001 Device 007: ID 04b8:0116 Seiko Epson Corp. Perfection 3170 (GT-9400)

**2)** 
Check that SANE & XSANE are Present:
```
sudo apt-get install sane &&
sudo apt-get install libsane &&
sudo apt-get install libsane-extras &&
sudo apt-get install sane-utils &&
sudo apt-get install xsane &&
sudo apt-get install xsane-common &&
sudo apt-get install libstdc++5
```
**3)** Check That the system is upto date:
System > Administration > Update Manager (or)
```
sudo apt-get update && sudo apt-get upgrade
```

**4)** 
Then lets see where things stand:
```
xsane
```
Get a Pop up Window:
> No Devices available

**5)**
To get a list of devices
```
scanimage -L
```
> No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
**6)**
See if SANE can see the Scanner ?
```
sane-find-scanner
```
> found USB scanner (vendor=0x04b8, product=0x0116) at libusb:001:007
**7)**
open and maybe edit this file Check to see that "epson" & epson2" are uncommented (that is with out"#")
```
sudo gedit /etc/sane.d/dll.conf
``` 
**8)**
(with Epson issues all roads seem to lead here) so Go to:
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do]("http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do")
Fill in the form and download: 
---> iscan-2.10.0-1.c2.i386.rpm
---> iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
to the Desktop
thats your:
```
cd ~/Desktop && pwd
```
**9)**
Get Alien
Alien allows you to convert [".rpm"]("http://en.wikipedia.org/wiki/RPM_Package_Manager") files into Debian [".deb"]("http://en.wikipedia.org/wiki/Deb_%28file_format%29") packages, which can be installed with dpkg.
```
sudo apt-get install alien
```
**10)**
Make the ".deb" file from the ".rpm" file (Note in the code-example the "*" takes the place of
e.g: "-plugin-gt-9400-1.0.0-1.c2.i386"
```
cd ~/Desktop
sudo alien -d iscan*.rpm
sudo dpkg -i iscan*.deb
```
**11)**
Edit the libsane-extras.rules
```
sudo gedit /etc/udev/rules.d/50-libsane-extras.rules
```
**12)** 
if it is empty add this line:
> SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="0666", GROUP="scanner"

**13)**
Edit the epson.conf
```
sudo gedit /etc/sane.d/epson.conf
```
**14)** 
add this line (the USB device ID from step #1 above) at the end:
> usb 0x04b8 0x0116
**15)**
Add yourself to the scanner group (adding the scanner group if needed) 
System > Administration > Users and Groups > manage groups > unlock > add > check self
**16)**
Do a complete Shutdown & restart the machine
**17)**
Try To get a list of devices again
```
scanimage -L
```
first got:
> Segmentation fault
Now get:
> device `epson:libusb:001:006' is a Epson  flatbed scanner
**18)**
```
iscan
```
get a Pop up Window: 
> Could not send command to scanner. Check the scanner's status

**19)**
anyway I Like and Just Want to use XSANE 
```
xsane
```
I get the "Xsane 0.997 window"  & "Preview window"
Both "Preview botton" & "Scan Botton"
Get pop up window:
> Failed to start scanner: invalid argument

[CENTER][B]- - - > at a Dead End < - - -
- - - > Still Will Not Scann < - - -[/B][/CENTER]

Has anyone had any recent Success under **Ubuntu 10.10**
see any errors in what I did ? any Help or ideas ?
**Thanks** Ronok
[My < Linux > Command Line Interface Page]("http://www.gongkuo.com/linuxcli.htm")

---

### Post by lidex on 2011-03-02
Wish I could help. My perfection 1650 worked with very little effort. If you're not tired of looking...
[http://www.linuxidx.com/linux.php?q=Perfection+3170](http://www.linuxidx.com/linux.php?q=Perfection+3170)

---

### Post by The Cog on 2011-03-02
I had a problem with my perfection640 scanner which was fixed by editing /etc/sane.d and try this: un-comment epson and comment out epson2 instead. Reboot to be sure whatever-it-is that reads the file is restarted.

I don't know if that'll fix your scanner, but it's a quick and easy fix if it does.

---

### Post by Ronok on 2011-03-17
Thank you kindly: **lidex** & **The Cog**
for your tips and quick replies,

I will be off the road and back at that machine in some weeks

at that time I will try your tips and report back in here

thanks

R

---

### Post by james_xxx on 2011-03-23
The Cog,

I am trying to get a different Epson scanner (a Perfection 610) going in 10.10, and also running into issues.

I had used it with no problem in 10.04.

It is completely unclear to me what you mean by commenting out epson2, and commenting epson. On my machine, /etc/sane.d is a directory containing many config files. The files epson.conf and epson2.conf are there, but I cannot figure out what you are suggesting to comment and uncomment.

Thanks in advance for the help!

---

### Post by The Cog on 2011-03-23
> **james_xxx said:**
> It is completely unclear to me what you mean by commenting out epson2, and commenting epson.
Ooh! It looks like I was having a brain-fart that night. Sorry.

The file is **/etc/sane.d/dll.conf** and in there, you will find the lines 
```
#epson
epson2
```
which I changed to
```
epson
#epson2
```which I think is re-enabling an older version of epson driver. I'm not sure what needs to be restarted after this change, so rebooting is the crude way to make sure.

---

### Post by james_xxx on 2011-03-24
The Cog,

I made your suggested change, and my Perfection 610 appears to be working fine!

I was ultimately able to use this scanner yesterday by connecting it to a laptop running Fedora 14. I have looked at the /etc/sane.d/dll.conf on that machine, and interestingly, the file there looks like the unmodified dll.conf in Ubuntu (epson is commented out, and epson2 is uncommented).

At any rate, it is now able to work with my desktop. :D

Many thanks for your help!!

---

### Post by The Cog on 2011-03-24
That's good news.

And it's interesting that epson2 works on Fedora. I'll have to keep my eyes open for clues on that mystery.

---

### Post by wil on 2011-05-27
I also have the Perfection 3170 and I have exact same problems with natty.

If somebody has found a solution please post and I really need my scanner.

Thanks

---

### Post by wil on 2011-05-27
OK one thing is not to use a USB3.0 port (blue). I am using normal USB2.0 port now and it seems to be working better now.

---

### Post by olandesevolante on 2011-07-22
Same here, Maverick, tried every cure proposed on this thread, no luck :-(

Pity really, as the 3170 is one excellent scanner.

---

### Post by Tweak42 on 2011-07-27
Thank you Cog.  Changing /etc/sane.d/dll.conf from epson2 to epson driver worked for my Epson Perfection 1650.  This was for Ubuntu 10.10 installation.

---

### Post by lidex on 2011-08-17
> **Tweak42 said:**
> Thank you Cog.  Changing /etc/sane.d/dll.conf from epson2 to epson driver worked for my Epson Perfection 1650.  This was for Ubuntu 10.10 installation.

Interesting. Using perfection 1650 as well and never made any changes to that file. It has worked from intrepid to oneiric.

---

### Post by mikeprosceo on 2012-04-16
I am using 64 bit ubuntu 11.10 and the only epson driver I can find for my perfection 3170 is 32 bit. Alien won't even convert the rpm package to a deb because of the wrong environment.   Is there a way to force the 32 bit to work in the 64 bit environment?  I have a brother 32 bit lazer printer and was able to make it work in my 64 bit with the help of Brother.  I have searched all over the web but have dead ended.  Please help.

---

### Post by oldos2er on 2012-04-16
Closed. See thread [http://ubuntuforums.org/showthread.php?t=1960070](http://ubuntuforums.org/showthread.php?t=1960070)

---

