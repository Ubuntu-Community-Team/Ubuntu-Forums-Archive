---
title: "Scanner Trouble in Ubuntu 8:10"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by zoey_s on 2009-03-08
I am running ubuntu 8..10 and I have had no luck in getting my Epson perfection 3490 photo scanner to work.  I belong to the scanner group and my scanner is recognized, but I get this message when I try to run it; Failed to open device snapscan:libusb:008:002':invalid argument

  I found a how to in this forum and this is what I did, but I still get the same message.

First I made sure that libsane-extras is installed.

Next I made sure that all users who are allowed to use the scanner belong to the "scanner" group.

Got the firmware, which is in a cab archive on the CD that came with the scanner; extracted files to find Esfw52.bin; copied file to /usr/local/lib/firmware

Checked snapscan.conf and scanner was listed  Changed firmware line in snapscan.conf to firmware /usr/local/lib/firmware/Esfw52.bin

Added file 10-udev.rules containing these lines;
 #scanner devices   
  scanner:root:scanner:066                             usb/scanner*:root:scanner:0660    
 to /etc/udev/rules.d     

I would appreciate any suggestions.

               Thanks, zoey

---

### Post by rburkartjo on 2009-03-08
zoey have to tried to install the program xsane. get it from add/remove do search it will be installed under graphics. i had to use to get my hp scanner to work

---

### Post by zoey_s on 2009-03-08
> **rburkartjo said:**
> zoey have to tried to install the program xsane. get it from add/remove do search it will be installed under graphics. i had to use to get my hp scanner to work

I probably should have said that xsane is what I am using.

Thanks, zoey

---

### Post by ivanvajar on 2009-03-08
What does 

sudo sane-find-scanner

say?

---

### Post by ivanvajar on 2009-03-08
Also, when you plug your scanner in, does Ubuntu do ANYTHING? It should at least inform you if no devices were found.

---

### Post by zoey_s on 2009-03-08
> **ivanvajar said:**
> What does 

sudo sane-find-scanner

say?

 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8 [EPSON], product=0x0122 [EPSON Scanner]) at libusb:008:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program

 scanimage -L
device `snapscan:libusb:008:004' is a EPSON EPSON Scanner flatbed scanner

zoey

---

### Post by zoey_s on 2009-03-08
> **ivanvajar said:**
> Also, when you plug your scanner in, does Ubuntu do ANYTHING? It should at least inform you if no devices were found.

No, ubuntu doesn't do anything when I plug the scanner into the usb port.

I get the message Failed to open device snapscan:libusb:008:002':invalid argument when I click on XSane.

zoey

---

### Post by zoey_s on 2009-03-08
I did a Google search and found that ubuntu 8.10 is missing the epkowa file, so I followed the directions (cut and paste) and created one in/etc/sane.d. 
I then followed these directions:
The next step may not be necessary, but I edited /etc/sane.d/dll.conf: commented out the line "epson" and added a line "epkowa".

Now edit /etc/sane.d/epkowa.conf and comment out the "scsi" line; the only uncommented line should read simply "usb".

I then unplugged the scanner usb connection, did a restart, plugged it back in, clicked on XSane and got the very same error that I got before making all of the changes.   Rats!

zoey

---

### Post by ivanvajar on 2009-03-09
OK. So, your system detected scanner at libusb:008:004. Now, I had similar situation with HP 2400 Scanjet. In Terminal, type

cd /usr/lib/sane/
ls

and post me complete output. You also need to tell me what exactly is the model of your scanner.

The idea is that Ubuntu will not copy all the files into /lib/usb/sane/ that Sane needs to run scanner, because of it's security permissions.

---

### Post by steve-shinn on 2009-03-09
Try the instructions posted by rbmorse, .... it worked for my epson perfection 4490, and should work for the 3490 also (See moschops post) :-
[http://ubuntuforums.org/archive/index.php/t-587371.html](http://ubuntuforums.org/archive/index.php/t-587371.html)

---

### Post by ivanvajar on 2009-03-09
[ATTACH]105849[/ATTACH]

[ATTACH]105850[/ATTACH]

Here you have *.deb you need to install your scanner. I've downloaded them from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do) and made *.deb with alien

If the main iscan package will not install cleanly because it reports
file conflicts with certain sane-related packages previously installed,
just go ahead and force dpkg to overwrite

sudo dpkg -i --force-overwrite iscan_2.10.0-2_i386.deb

The plugin should not have a conflict.

This completes the installation. To test things out make sure the
scanner is powered up and connected and then type

sudo scanimage -L

---

### Post by zoey_s on 2009-03-10
Thanks all, 

Someone from another forum pointed me to this post and it worked.

[http://ubuntuforums.org/showpost.php?p=5094750&postcount=59](http://ubuntuforums.org/showpost.php?p=5094750&postcount=59)

I used the instructions posted by Rmantingh.

zoey

---

