---
title: "Epson Stylus NX200 all-in-one help"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by ktwbug on 2009-01-11
Hello all!  I am running ubuntu 8.04 hardy heron, and I recently purchase an Epson Stylus all-in-one NX200 printer.  It recognizes the printer and I can print using the DX4800 driver (which it did automatically) but I can't get it to recognize the scanner through xsane image scanner.  Anyone know of any fixes??  

Thanks!

ktwbug

---

### Post by ktwbug on 2009-02-02
O.k.   After some wonderful help from folks on this forum I have a functioning Epson Stylus NX200 all-in-one!!!  Printer and Scanner!!!
I'm going to try to give the directions I used here...

**First I got the printer working by doing this:**
> [INDENT]for printing try to choose the driver for dx4800. Ubuntu Hardy Heron offers it.
(System>Administration>Printing(or sth similar)>Settings - change "type and model" (or shape?)
This advice is from here:
[http://forum.ubuntu-fr.org/viewtopic...44179#p2144179](http://forum.ubuntu-fr.org/viewtopic...44179#p2144179)[/INDENT]

[I]**THANKS hadimosuur!!!**
[/I]
**For scanning start with this:**> 
[INDENT]
On avasys.jp you can find a driver - debian package.

Direct link for download is:
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

but may be it won't work well. So you can go there from here:

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

You must choose here:
"Epson Stylus NX200/SX200/SX205/TX200/TX203"
and Distribution and Distrib. version - I chose "others"
and your country, connection environment - "print/scan with local printer or scanner"
and Location for the product - I chose "Individuals(Graphic/Image)"

And now you can click on "Next"

and there will be THE .deb package "iscan_2.12.0-4_i386.deb" - in the section "Scanner Driver"

So download it and save it![/INDENT]

> [INDENT]Now you must go to the command line. Go to the directory where you saved the package to (use the command cd -e.g.: cd /home/MyFolder). And now install the package: write "sudo dpkg --install iscan_2.12.0-4_i386.deb"
put the password

If there will be some failure you must install or uninstall other required packages (use Synaptic) and than try again (sudo dpkg etc.)

When everything is ok you will find Image Scan! in Menu>Applications>Graphics
So start Image Scan! - and may be it will work!![/INDENT]

[I][B]Thanks again hadimosuur!!!
[/B][/I]
[B]after this step I had i-scan but it didn't recognize my scanner so I followed these instructions:
[/B]
> [INDENT]Hello,

I've just bought an Epson Stylus SX205.
Printing was quickly made available by using the DX4800 drivers instead but scanning took me some time to work out.

Here is a solution I found on a french website and it worked great !

Open a terminal :

```


lsusb | grep -i epson

```
You should have something similar to this :


```
Bus 001 Device 006: ID 04b8:0849 Seiko Epson Corp.

```
Note the 04b8:0849 numbers, then,



```
sudo gedit /etc/sane.d/epson.conf
```

Look for the line


```
# usb 0x??? 0x???
```

Replace them by the numbers you've noted before : 0x48b 0x849
and uncomment the line ( by removing the # )

Uncomment also these two lines :

```
# usb /dev/usbscanner0
# usb /dev/usb/scanner0
```

Then, you will notice that Xsane only recognizes your scanner if you launch it as ROOT, but it is not recommanded.

Instead, just modify udev rules :


```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

( file may be empty )

And paste this :


```
# Epson Stylus SX205
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0849", MODE="664", GROUP="scanner"

```
Then, restart udev :


```
sudo /etc/init.d/udev restart

```
> ( You may also need to add yourself in the scanner group... see groups and membership options in gnome control center)

And voilà !

Hope it will work for other SX205 users too 
[/INDENT]
***Thank you to Kaho!!***

[B]So after that my scanner worked...but then the printer didn't....silly so here is the quick fix for that!
[/B]
> [INDENT]Haha, I wanted to print something a week ago and I got this damn " Printer 'Stylus-SX205' may not be connected " too !!

I found it very weird because printing worked fine before and couldn't determine if this problem was due to the scan trick I gave you before ( I don't remember if I tried to print something after these modifications... )

Anyways, I have just found a solution, again, on the french ubuntu forum :

Apparently, it has something to do with /dev/usb/lp0 being attributed to the 'scanner' group instead of the 'lp' group...

With a simple
Code:

```
sudo chgrp lp /dev/usb/lp0

```
> it returned to normal !
( the tip in the french thread says that this modification works if the printer is connected to the usb lp0 port...and that may be the case in most configurations )[/INDENT]

[B]*Thanks again Kaho!!!*   That did the trick!!!  Now both work and I am so thrilled.  I hope this helps you guys!
[/B]
[I]Here is a link to the thread where I got all of this info
[/I]
[[URL="http://ubuntuforums.org/showthread.php?t=932547&highlight=Epson+NX200+scanner"]http://ubuntuforums.org/showthread.php?t=932547&highlight=Epson+NX200+scanner]("http://ubuntuforums.org/showthread.php?t=932547&highlight=Epson+NX200+scanner")[/URL]

---

### Post by larsman1 on 2009-05-15
05/14/2009
I have an Epson RX580 all in one.  8.04 drivers work for the printer, but none of the Ubuntu 8.04 add-remove software applications for scanning work.
    The following works great on my AMD64 HP Slimline, and has more options than xSane scanning did on my Mandriva Spring 2009.
The download page is:
[http://avasys.jp/hp/menu000001300/hpg000001249.htm](http://avasys.jp/hp/menu000001300/hpg000001249.htm)
    The driver is toward the bottom of the page.

iscan_2.15.0-3_amd64.deb

:wink:

---

### Post by chudder on 2009-05-17
So i'm trying to install the iscan utility from avasys but I get an error, this what the terminal says:

```

sudo dpkg --install iscan_2.19.0-4_i386.deb
(Reading database ... 218302 files and directories currently installed.)
Unpacking iscan (from iscan_2.19.0-4_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 29: Bad substitution
dpkg: error processing iscan_2.19.0-4_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Processing triggers for menu ...
Errors were encountered while processing:
 iscan_2.19.0-4_i386.deb

```

I had a dependency issue before but I thought I fixed it, how do i find out what the problem is?

Thanks

Chud

---

### Post by jamesgthang on 2009-11-23
ktwbug's instructions were great.  I am using an Epson Stylus TX200 on Ubuntu 9.10 and it worked like a charm. 

Some differences:  My sane was configured to use epson2.conf.  I noticed there were two epson configuration files.  I found that out which one was enabled by looking into the dll.conf.

```
sudo gedit /etc/sane.d/dll.conf
```This showed that epson.conf was commented out and epson2.conf was not.  I added the productID and deviceID I found with lsusb to the epson2.conf.

```
sudo gedit /etc/sane.d/epson2.conf
```My epson2.conf file did not have the

```
# usb /dev/usbscanner0
# usb /dev/usb/scanner0
```entries, so I did not uncomment or add them. I followed everything else exactly as its written below and it worked.

Good luck.


========================



> **ktwbug said:**
> O.k.   After some wonderful help from folks on this forum I have a functioning Epson Stylus NX200 all-in-one!!!  Printer and Scanner!!!
I'm going to try to give the directions I used here...

**First I got the printer working by doing this:**

[I]**THANKS hadimosuur!!!**
[/I]
**For scanning start with this:**



[I][B]Thanks again hadimosuur!!!
[/B][/I]
[B]after this step I had i-scan but it didn't recognize my scanner so I followed these instructions:
[/B]


Open a terminal :

```


lsusb | grep -i epson

```You should have something similar to this :


```
Bus 001 Device 006: ID 04b8:0849 Seiko Epson Corp.

```Note the 04b8:0849 numbers, then,



```
sudo gedit /etc/sane.d/epson.conf
```Look for the line


```
# usb 0x??? 0x???
```Replace them by the numbers you've noted before : 0x48b 0x849
and uncomment the line ( by removing the # )

Uncomment also these two lines :

```
# usb /dev/usbscanner0
# usb /dev/usb/scanner0
```Then, you will notice that Xsane only recognizes your scanner if you launch it as ROOT, but it is not recommanded.

Instead, just modify udev rules :


```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```( file may be empty )

And paste this :


```
# Epson Stylus SX205
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0849", MODE="664", GROUP="scanner"

```Then, restart udev :


```
sudo /etc/init.d/udev restart

```***Thank you to Kaho!!***

[B]So after that my scanner worked...but then the printer didn't....silly so here is the quick fix for that!
[/B]


With a simple
Code:

```
sudo chgrp lp /dev/usb/lp0

```[B]*Thanks again Kaho!!!*   That did the trick!!!  Now both work and I am so thrilled.  I hope this helps you guys!
[/B]
[I]Here is a link to the thread where I got all of this info
[/I]
[http://ubuntuforums.org/showthread.php?t=932547&highlight=Epson+NX200+scanner](http://ubuntuforums.org/showthread.php?t=932547&highlight=Epson+NX200+scanner)

---

### Post by Kabezon on 2010-01-18
I got the scanner to work, but only as root, which is useless... I modified the udev rules as stated, but it still won't let scan unless I'm root :S I think the problem is the scanner group, which doesn't appear in the group list.

---

### Post by rizitis on 2010-02-03
[http://ubuntuforums.org/showthread.php?t=932547&page=4](http://ubuntuforums.org/showthread.php?t=932547&page=4)

I have SX 205 epson now I can run xsane as user and not only as root
I hope it will help you.

---

