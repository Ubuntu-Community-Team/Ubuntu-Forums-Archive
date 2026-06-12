---
title: "Driver or Firmware for USB DVB TV tuner stick"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by ginner on 2011-01-29
I have installed Ubuntu and Myth TV and got an old analogue PCI tuner working. What I really want it to be able to use my USB DVB-T USB stick (Peak 102569AGPK) with USB ID 1b80:d395)

I have Googled and found a package which appears to contain what I need to get it working:  [http://aur.archlinux.org/packages.php?ID=36746]("http://aur.archlinux.org/packages.php?ID=36746")

> after poking round a bit I found some newer source at [http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/dvb-usb-rtl2832u-1.4.2-3.2.src.rpm](http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/dvb-usb-rtl2832u-1.4.2-3.2.src.rpm). After extracting dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2 (using rpmextract.sh), this built and worked perfectly including channel scanning. The only change I had to make was for my USB stick (Peak 102569AGPK) with USB ID 1b80:d395. I added #define USB_PID_KWORLD_WARM_5 0xD395 to rtl2832u.h and
{ USB_DEVICE(USB_VID_KWORLD_1ST, USB_PID_KWORLD_WARM_5) }, to rtl2832u.c. 

I'm not sure what 'dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2' is - a driver or firmware, and if I need to compile etc.

Can anyone help?

Many thanks,

---

### Post by robsoles on 2011-01-29
Before going to the trouble of compiling a driver, try plugging your USB TV stick in, give your system a couple of minutes and open "System"->"Administration"->"Hardware Drivers" and see if it mentions the DBV-T stick.

Grab MeTV from the Ubuntu Software Centre (it's easier than MythTV) and then, in MeTV, have a look under "View"->"Devices" and make sure your DBV-T stick isn't listed - select it if it's listed and try it out.

How's that work out for you?

---

### Post by ginner on 2011-01-30
Thanks for the advice. There is nothing shown under Hardware Drivers in Ubuntu and nothing found in Me TV.

lsusb -v gives me

```
Bus 001 Device 004: ID 1b80:d395 Afatech 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b80 Afatech
  idProduct          0xd395 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```

The circuit board is stamped HU394-T and has a Realtek RTL2832U chip on it.

Thanks

---

### Post by robsoles on 2011-01-30
Try searching Synaptic Package Manager for "DVB driver" -  a non-free firmware/driver pack turns up when I look. Enable more sources if you can't find it.

Synaptic is under "System"->"Administration" and you can access software sources in it under "Settings"->"Repositories" - enable all but 'Source code"

---

### Post by albert s on 2011-01-30
afatech could be the dvb USB stick,
that is what mine shows up as,
it has a major overheating issue and I had to tape a USB fan to the side of it,
otherwise after about 30seconds it wouldnt work.
MeTv is what I use, much easier than anything else I have come across.
try blowing a fan over your USB stick and try it again, that is what I did to find the solution.

HTH

---

### Post by ginner on 2011-01-30
I tried the a non-free DVB firmware/driver pack but didn't appear to work. Again nothing in Hardware Drivers or in Me TV.

Looking at the comments from the ArchLinux post (quoted in my first post) he had to add his device ID so the existing driver worked with this USB stick. 

Would dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2 be a driver or firmware? Am I right in thinking I would have to compile a driver but firmware just needs to be put in the firmware folder? 

I found dvb-usb-rtl2832u-1.4.2.tar.bz2 (older version) here [http://www.openbricks.org/src/1.2.4/]("http://www.openbricks.org/src/1.2.4/") and I can see the files to add the ID to.

Thanks

---

### Post by asmoore82 on 2011-01-30
You need to unplug and replug the DVB stick after loading that firmware package.

Check the output of ```
dmesg | grep -i dvb
``` to see what's going on.

---

### Post by albert s on 2011-01-30
```
Bus 001 Device 008: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
```

is what I get using  
```
 lsusb
```

but it overheats within 60seconds of turning on so I need a fan on it and then it works perfect for me in MeTv , otherwise its not even recognised.

---

### Post by ginner on 2011-01-31
I get nothing after 
```
dmesg | grep -i dvb
```

---

### Post by julianjm on 2011-02-01
Mine is:

Bus 001 Device 004: ID 1b80:d399 Afatech

Is anybody building a .deb with the new usb ids, or have a ppa?

Also, build instructions would be welcome ;)

Julian.

---

### Post by ginner on 2011-02-03
> **julianjm said:**
> Mine is:

Bus 001 Device 004: ID 1b80:d399 Afatech

Have you checked inside to see if you actually have an Afatech chip, or a Realtek?

I added the details of mine to the Linux TV [Realtek wiki here]("http://www.linuxtv.org/wiki/index.php/Talk:Realtek_RTL2831U")

---

### Post by julianjm on 2011-02-03
> **ginner said:**
> Have you checked inside to see if you actually have an Afatech chip, or a Realtek?

I added the details of mine to the Linux TV [Realtek wiki here]("http://www.linuxtv.org/wiki/index.php/Talk:Realtek_RTL2831U")

I've just opened it (couldn't take a picture clear enough with my crappy 3MP camera ;))

One chip reads:

RTL2832U
A5A9882
GA190

The other, near the antenna connector:

FC0012
G0943
9AN1L

As I said earlier, the usb id is 1b80:d399

Thanks

---

### Post by robsoles on 2011-02-03
> **julianjm said:**
> ...

One chip reads:

RTL2832U
A5A9882
GA190

...

I did a little more digging and I think you need exactly the same thing that ginner needs, albeit using a slightly different id number

ginner: 1b80:d395
julianjm: 1b80:d399

On [http://cvs.linuxtv.org/wiki/index.php/DiBcom_USB_devices#DiBcom_DVB-T](http://cvs.linuxtv.org/wiki/index.php/DiBcom_USB_devices#DiBcom_DVB-T) I found RTL2832U based devices of which the firmware and drivers may be nearer matches than one based on a RTL2831U.

Open the page and search ([CTRL]+[F] in good browsers) for instances of 2832 on the page.

Any help?

---

### Post by Anisset on 2011-02-07
> **ginner said:**
> I have installed Ubuntu and Myth TV and got an old analogue PCI tuner working. What I really want it to be able to use my USB DVB-T USB stick (Peak 102569AGPK) with USB ID 1b80:d395)

I have Googled and found a package which appears to contain what I need to get it working:  [http://aur.archlinux.org/packages.php?ID=36746]("http://aur.archlinux.org/packages.php?ID=36746")



I'm not sure what 'dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2' is - a driver or firmware, and if I need to compile etc.

Can anyone help?

Many thanks,

Hello, I have a dvb stick with de same usb id 1b80:d395.

I will try to compile the drivers of the web you said:
[http://aur.archlinux.org/packages.php?ID=36746]("http://aur.archlinux.org/packages.php?ID=36746")

You must download the file source and both patches. 
To patch the source code, unzip the *.tar.bz2 and copy the patch inside the directory, then type: 
patch -p1 < dvb-usb-rtl2832u-add-device.patch 
patch -p1 < dvb-usb-rtl2832u-compilefix.patch 

The rest of the instructions are in the readme.txt file included with the driver. I think that usb stick doesn't need any firmware.

I have errors when I try to compile the v4l-dvb drivers but I will keep trying...

---

### Post by ginner on 2011-02-07
Thanks. I had seen the Realtek sticks on LinuxTV but not noticed the two different numbers RTL2832U versus the more common RTL2831U. Unfortunately the two sticks using the 2832 don't appear to have working drivers. 

The comments on the archlinux site refer to my exact model working  ( [http://aur.archlinux.org/packages.php?ID=36746](http://aur.archlinux.org/packages.php?ID=36746) ) albeit not on Ubuntu.

---

### Post by Anisset on 2011-02-07
I compiled the drivers succesfully!!!

The error:

```
firedtv-fw.c:244: note: expected 'u32 *' but argument is of type 'const u32 *'
```

To solve it:
[http://webcache.googleusercontent.com/search?q=cache:77vEdrUNfbYJ:blogs.udp.cl/comment/reply/1457+%22firedtv-fw.c:244:+note:+expected+%27u32+*%27+but+argument+is+of+type+%27const+u32+*%27%22&cd=12&hl=ca&ct=clnk&source=www.google.cat]("http://webcache.googleusercontent.com/search?q=cache:77vEdrUNfbYJ:blogs.udp.cl/comment/reply/1457+%22firedtv-fw.c:244:+note:+expected+%27u32+*%27+but+argument+is+of+type+%27const+u32+*%27%22&cd=12&hl=ca&ct=clnk&source=www.google.cat")

make menuconfig <-- exit and save the changes.
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m for CONFIG_DVB_FIREDTV=n
make
sudo make install

Now the usb stick is detected, but when I scan the channels it detects nothing.
Maybe it's a hardware problem, maybe I didn't applyed the patch correctly.

---

### Post by Anisset on 2011-02-07
> **ginner said:**
> Thanks. I had seen the Realtek sticks on LinuxTV but not noticed the two different numbers RTL2832U versus the more common RTL2831U. Unfortunately the two sticks using the 2832 don't appear to have working drivers. 

The comments on the archlinux site refer to my exact model working  ( [http://aur.archlinux.org/packages.php?ID=36746](http://aur.archlinux.org/packages.php?ID=36746) ) albeit not on Ubuntu.

Looking in the windows driver's cd, I've found the RTL2832U driver. 

Have you tried to compile it?
If you need help, tell me.

---

### Post by ginner on 2011-02-08
Couldn't find anything non-Windows on the Windows driver CD.

I don't know how to compile drivers. Which did you try? on [http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/]("http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/") there is currently
>  dvb-usb-rtl2832u-1.1-5.4.src.rpm                                                   24-Jun-2010 09:23       87K
 dvb-usb-rtl2832u-2.0.1-8.2.src.rpm                                              05-Feb-2011 00:29       179K

Thanks

---

### Post by Anisset on 2011-02-08
In the windows cd I found the windows driver, but there I confirmed that I need the RTL2832U driver.

To compile you need to download the sources files in the web you posted.
[http://aur.archlinux.org/packages.php?ID=36746]("http://aur.archlinux.org/packages.php?ID=36746")

The links are:
[https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u-add-device.patch?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&]("https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u-add-device.patch?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&")

[https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u-compilefix.patch?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&]("https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u-compilefix.patch?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&")

[https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u.tar.bz2?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&]("https://api.opensuse.org/public/source/home:jvroosmalen:branches:home:polyconvex/dvb-usb-rtl2832u/dvb-usb-rtl2832u.tar.bz2?rev=4074ef2d7ae35cc4c97dcd9bd8e318c0&")

You must patch the the source as I said three post above, and follow the readme.txt.

You will need to download the v4l-dvb source drivers as said in the readme.txt

$hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

---

### Post by ginner on 2011-02-08
> You will need to download the v4l-dvb source drivers as said in the readme.txt

$hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

I'm not sure how to use this repository - do I just click one of
[LIST]
[*]bz2
[*]zip
[*]gz
[/LIST]
on the left?

---

### Post by wep940 on 2011-02-08
Also make sure you have installed the build-essential package via Synaptic Package Manager.  Without that, you can' t compile.

---

### Post by Anisset on 2011-02-08
To download v4l-dvb sources you need to install mercurial
In a terminal:

$sudo apt-get install mercurial
$hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

In the readme.txt before the 5d you need to go to the v4l-dvb folder,
$cd /root/Desktop/v4l-dvb 
(or wherever you put it)

Then you can compile with the usual,

$make clean
$make
$sudo make install

---

### Post by ginner on 2011-02-09
OK, I got errors after $make with the firedtv-1394 

```
CC [M]  /home/ben/Desktop/v4l-dvb/v4l/firedtv-1394.o
/home/ben/Desktop/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
```

I assumed this might be the same as your:

> The error:

Code:
```
firedtv-fw.c:244: note: expected 'u32 *' but argument is of type 'const u32 *'
To solve it:
http://webcache.googleusercontent.co...www.google.cat
```

make menuconfig <-- exit and save the changes.
gedit v4l/.config <-- change CONFIG_DVB_FIREDTV=m for CONFIG_DVB_FIREDTV=n
make
sudo make install

so I tried $make menuconfig

but I got

```
Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[3]: *** [scripts/kconfig/dochecklxdialog] Error 1
make[2]: *** [v4l-mconf] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make[1]: *** [/lib/modules/2.6.32-21-generic/build/scripts/kconfig/mconf] Error 2
make[1]: Leaving directory `/home/ben/Desktop/v4l-dvb/v4l'
make: *** [menuconfig] Error 2
```

so I ran 
$ sudo apt-get install ncurses-dev

and got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libncurses5-dev instead of ncurses-dev
The following NEW packages will be installed:
  libncurses5-dev
0 upgraded, 1 newly installed, 0 to remove and 394 not upgraded.
Need to get 1,564kB of archives.
After this operation, 6,627kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libncurses5-dev
Install these packages without verification [y/N]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid/main libncurses5-dev 5.7+20090803-2ubuntu3 [1,564kB]
Fetched 1,564kB in 6s (256kB/s)                                                                             
Selecting previously deselected package libncurses5-dev.
(Reading database ... 138670 files and directories currently installed.)
Unpacking libncurses5-dev (from .../libncurses5-dev_5.7+20090803-2ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up libncurses5-dev (5.7+20090803-2ubuntu3) ...
```

Tried 
$make menuconfig  
again but I still get 
'make menuconfig' requires the ncurses libraries. Install ncurses (ncurses-devel) and try again.

Any ideas?


Also noticed a number of errors relating to the RTL2832U:

```
 CC [M]  /home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mxl5007t.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_fc2580.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mt2266.o
/home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mt2266.c: In function 'demod_pdcontrol':
/home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mt2266.c:825: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/ben/Desktop/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mt2266.c:826: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/ben/Desktop/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
/home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_mt2266.c:1082: warning: passing argument 3 of 'MT2266_GetParam' from incompatible pointer type
/home/ben/Desktop/v4l-dvb/v4l/tuner_mt2266.h:990: note: expected 'UData_t *' but argument is of type 'u32t *'
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/rtl2832u.o
In file included from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u.c:5:
/home/ben/Desktop/v4l-dvb/v4l/rtl2832u.h:20:1: warning: "USB_VID_AZUREWAVE" redefined
In file included from /home/ben/Desktop/v4l-dvb/v4l/dvb-usb.h:26,
                 from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u.h:7,
                 from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u.c:5:
/home/ben/Desktop/v4l-dvb/v4l/dvb-usb-ids.h:67:1: warning: this is the location of the previous definition
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/rtl2832u_fe.o
In file included from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u_fe.c:4:
/home/ben/Desktop/v4l-dvb/v4l/rtl2832u.h:20:1: warning: "USB_VID_AZUREWAVE" redefined
In file included from /home/ben/Desktop/v4l-dvb/v4l/dvb-usb.h:26,
                 from /home/ben/Desktop/v4l-dvb/v4l/foundation.h:17,
                 from /home/ben/Desktop/v4l-dvb/v4l/dvbt_demod_base.h:278,
                 from /home/ben/Desktop/v4l-dvb/v4l/demod_rtl2832.h:73,
                 from /home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_tua9001.h:78,
                 from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u_fe.h:5,
                 from /home/ben/Desktop/v4l-dvb/v4l/rtl2832u_fe.c:2:
/home/ben/Desktop/v4l-dvb/v4l/dvb-usb-ids.h:67:1: warning: this is the location of the previous definition
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/rtl2832u_io.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.o
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL_Soft_Reset':
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c:1140: warning: unused variable 'Status'
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL_Tuner_RFTune':
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c:1224: warning: unused variable 'Status'
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c: In function 'MxL5007_Init':
/home/ben/Desktop/v4l-dvb/v4l/tuner_mxl5007t.c:824: warning: 'myIRV' may be used uninitialized in this function
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/tuner_fc2580.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/tuner_mt2266.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/tuner_tua9001.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/nim_rtl2832_tua9001.o
  CC [M]  /home/ben/Desktop/v4l-dvb/v4l/ttusb2.o
```

---

### Post by Anisset on 2011-02-09
> **ginner said:**
> OK, I got errors after $make with the firedtv-1394 

so I ran 
$ sudo apt-get install ncurses-dev

```
Reading package lists... Done
Note, selecting libncurses5-dev instead of ncurses-dev
The following NEW packages will be installed:
  libncurses5-dev

```


I had the same error and I installed ncurses-dev. That worked for me.
Note that apt-get selected libncurses5-dev, not ncurses-dev. 
Try to upgrade and reinstall the ncurses-dev.

$sudo apt-get update
$sudo apt-get upgrade
$sudo apt-get install ncurses-dev

If it doesn't word try to force the install. I don't remember how to do that, maybe is easier with synaptic.


> **ginner said:**
> 
Also noticed a number of errors relating to the RTL2832U:


This are only warnings, momentarily ignore them.

---

### Post by ginner on 2011-02-10
> Try to upgrade and reinstall the ncurses-dev.

$sudo apt-get update
$sudo apt-get upgrade
$sudo apt-get install ncurses-dev

I am using a 3G dongle at the moment and the Ubuntu Update manager is saying there are 481 MB of files which I don't really want to download. Will apt-get update & upgrade download that amount?

---

### Post by robsoles on 2011-02-10
> **ginner said:**
> I am using a 3G dongle at the moment and the Ubuntu Update manager is saying there are 481 MB of files which I don't really want to download. Will apt-get update & upgrade download that amount?

'apt-get upgrade' will.

In Synaptic Package Manager you may have better luck specifying the package you really want without having to take all the update packages first - can you find synaptic?

---

### Post by robsoles on 2011-02-10
Just an afterthought: The 'real/proper' fix for your problem **might** be amongst those updates that you are avoiding :roll:

---

### Post by ginner on 2011-03-01
Hi - eventually got a phone line and Broaband (3 months arter moving house!) and so I updated & upgraded.

Still get the issues in my post above. 

$make menuconfig says i need ncurses-devel but when i try to install i get 
```
Note, selecting libncurses5-dev instead of ncurses-dev
```
Any ideas?

---

### Post by ginner on 2011-03-04
Did an update upgrade again and
$make menuconfig
worked

After 
$make 
I got the same warning messages as before and the stick is not recognised.

I added the following
#define USB_PID_KWORLD_WARM_5 0xD395 to rtl2832u.h and
{ USB_DEVICE(USB_VID_KWORLD_1ST, USB_PID_KWORLD_WARM_5) }, to rtl2832u.c.

and tried again

but still not recognised....

---

### Post by robsoles on 2011-03-04
which 'libncurses' did you land up with being installed?

---

### Post by ginner on 2011-03-13
Hi, Just to let you know I got it working (scaning working as well). I upgraded o Ubuntu 10.10 then compiled the newer drivers from
[http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/](http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/)

dvb-usb-rtl2832u-2.0.1-9.4.src.rpm                              27-Feb-2011 01:38  179K

Brief summary of what I did using the notes on this thread and the instructions in the archive above...

Extracted 
```
compat-2.6.38.patch
dvb-usb-rtl2832u.spec
dvb-usb-rtl2832u.tar.bz2
```

copied patch into dvb-usb-rtl2832u
```
$cd ~/Desktop/dvb-usb-rtl2832u
ran 
$ patch -p1 < compat-2.6.38.patch
patching file rtl2832u.c
```

make menuconfig

add the following lines to Kconfig in v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb.	
```
config DVB_USB_RTL2832U
	tristate "Realtek RTL2832U DVB-T USB2.0 support"
	depends on DVB_USB
	help
	  Realtek RTL2832U DVB-T driver.
```

added the following
```
#define USB_PID_KWORLD_WARM_5 0xD395
``` to rtl2832u.h and
```
{ USB_DEVICE(USB_VID_KWORLD_1ST, USB_PID_KWORLD_WARM_5) }
```, to rtl2832u.c

added to v4l....\linux\drivers\media\dvb\Kconfig
```
comment "Supported FireWire (IEEE 1394) Adapters"
	depends on DVB_CORE && IEEE1394
	source "drivers/media/dvb/firewire/Kconfig
```

make 
make install

Thanks everyone for your help!

---

### Post by chrisjunkie on 2011-03-24
Hi All,

Been trying for the past 2 weeks to try and get this driver to install and no matter what I do I can't for the life of me get it to work! Every time I try to compile, I get errors.

Now I am not actually running ubuntu but instead Gentoo, but all the driver support is on your forums :)

Current system setup: 2.6.36-gentoo-r5 and I have JUST downloaded the latest linuxtv dvb media_build git repo, and used various RTL2832 sources but always get the same error.

Can anyone help out or do I need to install ubuntu to get it to work :D

```

/root/realtek/media_try/v4l/nim_rtl2832_mt2266.c: In function 'rtl2832_mt2266_UpdateFunction':
/root/realtek/media_try/v4l/nim_rtl2832_mt2266.c:423: warning: passing argument 6 of 'demod_pdcontrol' from incompatible pointer type
/root/realtek/media_try/v4l/nim_rtl2832_mt2266.h:250: note: expected 'uint32_t *' but argument is of type 'long unsigned int *'
In file included from /root/realtek/media_try/v4l/rtl2832u.c:5:
/root/realtek/media_try/v4l/rtl2832u.h:41:1: warning: "USB_VID_GTEK" redefined
In file included from /root/realtek/media_try/v4l/dvb-usb.h:26,
                 from /root/realtek/media_try/v4l/rtl2832u.h:7,
                 from /root/realtek/media_try/v4l/rtl2832u.c:5:
/root/realtek/media_try/v4l/dvb-usb-ids.h:35:1: warning: this is the location of the previous definition
/root/realtek/media_try/v4l/rtl2832u.c:37: error: array type has incomplete element type
/root/realtek/media_try/v4l/rtl2832u.c: In function 'rtl2832u_rc_query':
/root/realtek/media_try/v4l/rtl2832u.c:563: warning: type defaults to 'int' in declaration of 'type name'
/root/realtek/media_try/v4l/rtl2832u.c:563: warning: type defaults to 'int' in declaration of 'type name'
/root/realtek/media_try/v4l/rtl2832u.c:563: error: negative width in bit-field '<anonymous>'

```

Appreciate the help!

Chris

---

### Post by ginner on 2011-05-03
Arghhhhh! my USB stick is no longer recognised. 

lsusb gives
```
Bus 001 Device 004: ID 1b80:d395 Afatech
``` 
but 
dmesg | grep -i dvb gives nothing and MythTV does not see the stick.

Could this have been caused by an update, or installation of a different version of MythTV?

I re-complied and installed from the same patched sources used above but no joy.

The stick still works fine on windows.

Any ideas?

---

### Post by ginner on 2011-05-07
I am trying to reinstall the RTL2832u driver using the latest sources trying to follow the method I successfully used before.

I am currently running Ubuntu 11.04 and 
$ uname -r gives
2.6.38-8-generic

but when i run
$ make clean
$ make

I get Preparing to compile for kernel version 2.6.35 and erors...

```
make -C /home/ben/Desktop/v4l-dvb/v4l 
make[1]: Entering directory `/home/ben/Desktop/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.35
File not found: /lib/modules/2.6.35-28-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/home/ben/Desktop/v4l-dvb/v4l'
make[1]: Entering directory `/home/ben/Desktop/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.35
File not found: /lib/modules/2.6.35-28-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/ben/Desktop/v4l-dvb/v4l'
make: *** [all] Error 2
```

Any ideas?

---

### Post by ginner on 2011-05-09
I have managed to install again on a fresh install of Ubuntu 11.04 (2.6.38-8-generic) on another laptop.

Chris - I got the same warnings as you, but no errors and it is working

```
CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_mxl5007t.o
  CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_fc2580.o
  CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.o
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.c: In function 'rtl2832_mt2266_UpdateFunction':
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.c:423:3: warning: passing argument 6 of 'demod_pdcontrol' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.h:250:1: note: expected 'uint32_t *' but argument is of type 'long unsigned int *'
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u.o
In file included from /home/ben/Desktop/media_build/v4l/rtl2832u.c:5:0:
/home/ben/Desktop/media_build/v4l/rtl2832u.h:42:0: warning: "USB_VID_GTEK" redefined
/home/ben/Desktop/media_build/v4l/dvb-usb-ids.h:35:0: note: this is the location of the previous definition
/home/ben/Desktop/media_build/v4l/rtl2832u.c:468:12: warning: 'rtl2832u_rc_query' defined but not used
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u_fe.o
In file included from /home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:4:0:
/home/ben/Desktop/media_build/v4l/rtl2832u.h:42:0: warning: "USB_VID_GTEK" redefined
/home/ben/Desktop/media_build/v4l/dvb-usb-ids.h:35:0: note: this is the location of the previous definition
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c: In function 'rtl2832_set_parameters':
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:1545:5: warning: passing argument 3 of 'read_usb_sys_register' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:96:1: note: expected 'int *' but argument is of type 'unsigned char *'
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:1553:5: warning: passing argument 3 of 'read_usb_sys_register' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:96:1: note: expected 'int *' but argument is of type 'unsigned char *'
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u_io.o
  CC [M]  /home/ben/Desktop/media_build/v4l/tuner_mxl5007t.o
```

I also used the latest linuxtv dvb media_build git repo and this RTL2832U source:
[http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/](http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/)

dvb-usb-rtl2832u-2.0.1-9.10.src.rpm       05-May-2011 17:25  179K   Details

I am still having problems on my Desktop - 'make' is referencing the wrong (old) kernel version. Do you know how I fix?

---

### Post by robsoles on 2011-05-09
Look in Synaptic for 'linux headers', you should be able to find it's old pack and the pack which relates to your kernel; Install the one you want and ditch any that appear to be getting in the way.

---

### Post by wep940 on 2011-05-09
Do any of the readme's or instructions mention running configure?  Usually when we see something be made, you do a ./configure in the main folder that everything unpacked to.  This supposedly makes sure you have everything the package needs to compile and it sets some things to be specific to your installation.

Normally, when installing from source, the sequence would be:

- unpack the source
- ./configure
- make
- sudo make install

You may want to double-check the instructions to see if you are missing a configure or if they aren't using it.

Also, as already mentioned, be sure to install build-essential.  If you did a bare install of 11.04, you'll need to reinstall build-essential.

---

### Post by ElseCZ on 2011-05-12
> **ginner said:**
> I have managed to install again on a fresh install of Ubuntu 11.04 (2.6.38-8-generic) on another laptop.

Chris - I got the same warnings as you, but no errors and it is working

```
CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_mxl5007t.o
  CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_fc2580.o
  CC [M]  /home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.o
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.c: In function 'rtl2832_mt2266_UpdateFunction':
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.c:423:3: warning: passing argument 6 of 'demod_pdcontrol' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/nim_rtl2832_mt2266.h:250:1: note: expected 'uint32_t *' but argument is of type 'long unsigned int *'
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u.o
In file included from /home/ben/Desktop/media_build/v4l/rtl2832u.c:5:0:
/home/ben/Desktop/media_build/v4l/rtl2832u.h:42:0: warning: "USB_VID_GTEK" redefined
/home/ben/Desktop/media_build/v4l/dvb-usb-ids.h:35:0: note: this is the location of the previous definition
/home/ben/Desktop/media_build/v4l/rtl2832u.c:468:12: warning: 'rtl2832u_rc_query' defined but not used
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u_fe.o
In file included from /home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:4:0:
/home/ben/Desktop/media_build/v4l/rtl2832u.h:42:0: warning: "USB_VID_GTEK" redefined
/home/ben/Desktop/media_build/v4l/dvb-usb-ids.h:35:0: note: this is the location of the previous definition
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c: In function 'rtl2832_set_parameters':
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:1545:5: warning: passing argument 3 of 'read_usb_sys_register' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:96:1: note: expected 'int *' but argument is of type 'unsigned char *'
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:1553:5: warning: passing argument 3 of 'read_usb_sys_register' from incompatible pointer type
/home/ben/Desktop/media_build/v4l/rtl2832u_fe.c:96:1: note: expected 'int *' but argument is of type 'unsigned char *'
  CC [M]  /home/ben/Desktop/media_build/v4l/rtl2832u_io.o
  CC [M]  /home/ben/Desktop/media_build/v4l/tuner_mxl5007t.o
```

I also used the latest linuxtv dvb media_build git repo and this RTL2832U source:
[http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/](http://195.135.221.134/repositories/home:/jvroosmalen:/branches:/home:/polyconvex/openSUSE_Factory/src/)

dvb-usb-rtl2832u-2.0.1-9.10.src.rpm       05-May-2011 17:25  179K   Details

I am still having problems on my Desktop - 'make' is referencing the wrong (old) kernel version. Do you know how I fix?

try ```
make distclean
```

Than you will compile for your new kernel, anyway i fail with error

```
  CC [M]  /usr/src/media_build/v4l/nim_rtl2832_mt2266.o
/usr/src/media_build/v4l/nim_rtl2832_mt2266.c: In function 'rtl2832_mt2266_UpdateFunction':
/usr/src/media_build/v4l/nim_rtl2832_mt2266.c:423:3: warning: passing argument 6 of 'demod_pdcontrol' from incompatible pointer type
/usr/src/media_build/v4l/nim_rtl2832_mt2266.h:250:1: note: expected 'uint32_t *' but argument is of type 'long unsigned int *'
  CC [M]  /usr/src/media_build/v4l/rtl2832u.o
In file included from /usr/src/media_build/v4l/rtl2832u.c:5:0:
/usr/src/media_build/v4l/rtl2832u.h:41:0: warning: "USB_VID_GTEK" redefined
/usr/src/media_build/v4l/dvb-usb-ids.h:35:0: note: this is the location of the previous definition
/usr/src/media_build/v4l/rtl2832u.c:37:27: error: array type has incomplete element type
/usr/src/media_build/v4l/rtl2832u.c: In function 'rtl2832u_rc_query':
/usr/src/media_build/v4l/rtl2832u.c:561:20: warning: type defaults to 'int' in type name
/usr/src/media_build/v4l/rtl2832u.c:561:20: warning: type defaults to 'int' in type name
/usr/src/media_build/v4l/rtl2832u.c:561:20: error: negative width in bit-field '<anonymous>'
/usr/src/media_build/v4l/rtl2832u.c: At top level:
/usr/src/media_build/v4l/rtl2832u.c:37:27: warning: 'rtl2832u_rc_keys_map_table' defined but not used
/usr/src/media_build/v4l/rtl2832u.c:466:12: warning: 'rtl2832u_rc_query' defined but not used
make[3]: *** [/usr/src/media_build/v4l/rtl2832u.o] Error 1
make[2]: *** [_module_/usr/src/media_build/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/media_build/v4l'
make: *** [all] Error 2
```

any idea?

---

### Post by ElseCZ on 2011-05-12
So i beat it!!! It's WORKING finally with kernel 2.6.38-8. There's steps how i did it.

1) download v4l-dvb sources:
```

cd /usr/src/
git clone git://linuxtv.org/media_build.git 
cd media_build 
./build.sh

```

2) download sources with driver from: [https://build.opensuse.org/package/files?package=dvb-usb-rtl2832u&project=home%3Ajvroosmalen%3Abranches%3Ahome%3Apolyconvex](https://build.opensuse.org/package/files?package=dvb-usb-rtl2832u&project=home%3Ajvroosmalen%3Abranches%3Ahome%3Apolyconvex) and unpack it copy it to "/usr/src/media_build/linux/drivers/media/dvb/dvb-usb/" except Makefile and Kconfig files.

Read readme and do steps in readme.

3) Use patch which is included
```

patch -p1 < compat-2.6.38.patch

```

4) check your usb vendor and product id 
```

root@pc:/usr/src/media_build# lsusb                                                                                                                                                                           
Bus 002 Device 010: ID 0a81:0101 Chesen Electronics Corp. Keyboard                                                                                                                                                 
Bus 002 Device 009: ID 04f2:b11c Chicony Electronics Co., Ltd                                                                                                                                                      
Bus 002 Device 008: ID 0458:707f KYE Systems Corp. (Mouse Systems)  <<THIS IS MY TUNER>>

```

and correct ids header file "/usr/src/media_build/linux/drivers/media/dvb/dvb-usb/rtl2832u.h"
```

#define	USB_VID_GTEK				0x0458
#define	USB_PID_GTEK_WARM			0x707f

```

5)Compile it and install from with
```

cd /usr/src/media_build/
make distclean
make
make install

```

Hope it will help

E.

---

### Post by kem on 2011-06-13
Thanks ElseCZ,

I successfully applied your steps on Leadtek WinFast DTV Dongle mini (orange). Here are (a little bit more detailed) steps:

% download v4l-dvb sources:
```
mkdir leadtek; cd leadtek
git clone git://linuxtv.org/media_build.git 
cd media_build 
./build.sh
```

% dowloaded dvb-usb-rtl2832u.tar.bz2 from [https://build.opensuse.org/package/files?package=dvb-usb-rtl2832u&project=home%3Ajvroosmalen%3Abranches%3Ahome%3Apolyconvex](https://build.opensuse.org/package/files?package=dvb-usb-rtl2832u&project=home%3Ajvroosmalen%3Abranches%3Ahome%3Apolyconvex)
% copied all files to '/leadtek/media_build/linux/drivers/media/dvb/dvb-usb' except Makefile. Kconfig file is not in downloaded library.

> % Read readme and do steps in readme. (??) 
==========================
What do you exactly mean by "do steps"? I suppose steps (1)-(5a) are already done at this moment. 

So I started with step (5b) - added the following lines to Makefile in v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb.
```
dvb-usb-rtl2832u-objs = demod_rtl2832.o	dvbt_demod_base.o dvbt_nim_base.o foundation.o math_mpi.o nim_rtl2832_mxl5007t.o nim_rtl2832_fc2580.o nim_rtl2832_mt2266.o rtl2832u.o rtl2832u_fe.o rtl2832u_io.o tuner_mxl5007t.o tuner_fc2580.o tuner_mt2266.o tuner_tua9001.o nim_rtl2832_tua9001.o tuner_fc0012.o nim_rtl2832_fc0012.o demod_rtl2836.o dtmb_demod_base.o dtmb_nim_base.o nim_rtl2836_fc2580.o nim_rtl2836_mxl5007t.o tuner_e4000.o nim_rtl2832_e4000.o tuner_mt2063.o demod_rtl2840.o tuner_max3543.o nim_rtl2832_mt2063.o nim_rtl2832_max3543.o nim_rtl2840_mt2063.o nim_rtl2840_max3543.o qam_demod_base.o qam_nim_base.o
obj-$(CONFIG_DVB_USB_RTL2832U) += dvb-usb-rtl2832u.o
```

(5c) added the following lines to Kconfig in v4l-dvb-(version)/linux/drivers/media/dvb/dvb-usb.	
```
config DVB_USB_RTL2832U
	tristate "Realtek RTL2832U DVB-T USB2.0 support"
	depends on DVB_USB
	help
	  Realtek RTL2832U DVB-T driver.
```

Rest of steps (make clean -> make -> ...) skipped for now
=========================

% Copied compat-2.6.38.patch into '/leadtek/media_build/linux/drivers/media/dvb/dvb-usb' and run

```
cd ./linux/drivers/media/dvb/dvb-usb/
patch -p1 < compat-2.6.38.patch
```

% Corrected ids header file "/media_build/linux/drivers/media/dvb/dvb-usb/rtl2832u.h"

```
#define	USB_VID_GTEK					       0x0413
#define	USB_PID_GTEK_WARM			       0x6a03
```

% compile
```
make distclean
make
sudo make install
```

It seems working so far.

---

### Post by chrisw2 on 2011-09-21
Has anyone tried out the FM and DAB side of the rtl2832u with any success?

---

### Post by zooey on 2011-11-05
Hi all,

I had problems with installing RTL2832u on kernel 2.8-38, i have Gigabyte U7300 dvb usb, so i wrote to the realtek support and they give me a link to dropbox with driver i made it public so you can download it at [http://dl.dropbox.com/u/48306120/20110822_RTL2832_LINUX_OUT_OF_BOX.tar.gz]("http://dl.dropbox.com/u/48306120/20110822_RTL2832_LINUX_OUT_OF_BOX.tar.gz") , just install according README, everything works for me :) :)

---

### Post by s1hr on 2011-12-11
> **ginner said:**
> I have installed Ubuntu and Myth TV and got an old analogue PCI tuner working. What I really want it to be able to use my USB DVB-T USB stick (Peak 102569AGPK) with USB ID 1b80:d395)

I have Googled and found a package which appears to contain what I need to get it working:  [http://aur.archlinux.org/packages.php?ID=36746]("http://aur.archlinux.org/packages.php?ID=36746")



I'm not sure what 'dvb-usb-rtl2832u-1.4.2-3.2.tar.bz2' is - a driver or firmware, and if I need to compile etc.

Can anyone help?

Many thanks,

I don't use that card,but i use that driver.
That is driver.
1st to try: to follow README inside folder.
Basically put that tar.bz2 and install.sh in one folder,and then true terminal go to that folder,and type
sudo sh install.sh
2.if that not work ,there is many how to ..but lets first see result of this. Compiling driver to kernel give best results,but many times that is not necessarily. But for this driver i think its not enough that what they say in read-me,at least in my case was necessarily to compile.


3 I can say to you one more recommendation from my expirience: update ur ubuntu system fully as there is bug in ubuntu about FIREDTV,which prevent sucessfully to compile drivers,for systems older then 5july2011 or manually change that.-->firedtv=m->firedtv=n,what is more better,as many drivers works up to Lucid LTS,and after with newer kernel still not have support...but many thing are in progress..so in other hand for many how-to is better to not have upgraded system and new kernels..so first try with that u have now.

as far as i know now this driver in version 1.4 (without .2)support this maker but in version 1.4 this models from maker ur interested:
                usb:v0BDAp2839d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1F4DpA803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]1B80[/COLOR]pD[COLOR="Blue"]398[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:[COLOR="red"]v1B80[/COLOR]pD[COLOR="blue"]393[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="red"]1B80[/COLOR]pD[COLOR="blue"]397[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3234d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1164p6601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1680pA332d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp2838d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D19p1103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D19p1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D19p1101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B80pD396d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3274d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp2832d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb


[COLOR="Purple"]as far as i know that is driver for dvb-t(digital tv)..at least i use it for.[/COLOR]
i red colored maker ur interested,but ur model is not listed(only models 393,397,398 ) ,maybe if u add code of your card will work,maybe not. Usually yes.As in new versions ussually they ad new codes of new discovered dvb-t cards which have that realtek chip inside,or to say they are based on it.

Sorry on my english..i am croatian.

---

