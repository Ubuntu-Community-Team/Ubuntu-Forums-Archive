---
title: "linmodem help, please"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by A2JC4life on 2008-08-10
I sent the scanmodem results to the linmodems discussion list, but I'm not sure if it went through.  And I remember the linmodems site saying that sometimes ISP's eat the discussion list posts so to check the recent archives, but I can't find that again now.  If someone can direct me to the right place, I'll be glad to check that again for responses to my post.  Or, if someone can help me by interpreting this file, here it is:

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_07_31

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 1307:0163 Transcend Information, Inc. 
 ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]

USB modems not recognized

For candidate card in slot 00:14.2, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:437b	1179:ff10	Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller 

 Modem interrupt assignment and sharing: 
 18:     136466   IO-APIC-fasteoi   HDA Intel, wifi0
 --- Bootup diagnostics for card in PCI slot 00:14.2 ----
[   43.447312] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[ 2682.959007] ACPI: PCI interrupt for device 0000:00:14.2 disabled
[   45.646375] PM: Writing back config space on device 0000:00:14.2 at offset f (was 1ff, writing ff)
[   45.646408] PM: Writing back config space on device 0000:00:14.2 at offset 1 (was 4100006, writing 4100002)
[   45.646435] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18

 The PCI slot 00:14.2 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: 
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-00: ALC861 Analog : ALC861 Analog : playback 1 : capture 1
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd0500000 irq 18

 PCI slot 00:14.2 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel         344728  1 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:14.2:
	Modem chipset  detected on
NAME="Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller "
CLASS=0403
PCIDEV=1002:437b
SUBSYS=1179:ff10
IRQ=18
HDA=1002:437b
SOFT=1002:437b.HDA
ArchivedChip=0x11c13026
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:14.2
   0403 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller 
      Primary device ID:  1002:437b
    Subsystem PCI_id  1179:ff10 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x11c13026
                        
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.2.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are n. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: ath0 eth0 wifi0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by ModelM on 2008-08-10
Here's the important part:

```
Download from http://linmodems.technion.ac.il/packages/smartlink/
the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
$ tar zxf SLMODEMD.gcc4.2.tar.gz
and read instructions therein. But briefly, the modem is setup with command:
sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
reporting dynamic creation of ports:
/dev/ttySL0 --> /dev/pts/N , with N some number
Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

```

Here at the end where they refer to reading this or that file, these files are to be found in the Modem directory where this file was, or the DOCs directory within it.

---

### Post by A2JC4life on 2008-08-10
> **ModelM said:**
> Here's the important part:

```
Download from http://linmodems.technion.ac.il/packages/smartlink/
the package SLMODEMD.gcc4.2.tar.gz having a compiled slmodemd. Unpack under Linux with:
$ tar zxf SLMODEMD.gcc4.2.tar.gz
and read instructions therein. But briefly, the modem is setup with command:
sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
reporting dynamic creation of ports:
/dev/ttySL0 --> /dev/pts/N , with N some number
Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

```

Here at the end where they refer to reading this or that file, these files are to be found in the Modem directory where this file was, or the DOCs directory within it.

I have no idea what this means.  I understand how to download the package, and I'm pretty sure I understand how to unpack it.  But what does "having a compiled slmodemd" mean?  And the part about "briefly," how to set up the modem is completely foreign to me.  :?

---

### Post by ModelM on 2008-08-10
Let me edit these instructions a bit...

Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
the package SLMODEMD.gcc4.2.tar.gz [which includes] a compiled slmodemd. 

Unpack under Linux with [the command]:

$ tar zxf SLMODEMD.gcc4.2.tar.gz

and read instructions therein.

[The instructions in the package are more complete] But briefly, the modem is setup with command:
sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
reporting dynamic creation of ports:
/dev/ttySL0 --> /dev/pts/N , with N some number

Read DOCs/Smartlink.txt and Modem/DOCs/YourSystem.txt for follow through guidance.

---

### Post by A2JC4life on 2008-08-11
Why, after all these years, and all the talk about making Linux accessible to the masses, is there *still* no sane way to connect to the internet?  The reality looks something like this:

Step 1: Go to linmodems.org and navigate the poorly-organized website to locate ScanModem and the accompanying instructions.  Write down the instructions.  Download ScanModem and copy it to some portable medium.

Step 2: Go to other computer, or reboot out of Windows installation, and get into Linux.  Run ScanModem.  (Hope the directions work as written, the first time.)  Copy the contents of the newly-created file back to a portable disk/drive.

Step 3: Go to other computer, or reboot out of Linux installation and go to Windows.  Connect to the internet.  Ask someone who has a clue, what the heck the contents of the newly-created file actually *mean*. Understand just enough to go on to step 4.

Step 4: Find the file to download.  Download file.  Copy it to portable disk/drive.  Go to other computer or reboot out of Windows.  Go back to Linux.  Figure out how to extract the file you just downloaded.  (For some reason, I can't get it to do this from the command line.  It just acts as if I never told it anything.  Thankfully, right-clicking it in Ubuntu gives me the option to extract it.)

Step 5: Read the four or so text files that are extracted.  Feel like you're reading Russian.  ('Cause Greek I could make more sense of than this.)  Wonder what the executable files are that were extracted.  Wonder if you can run them by double-clicking.  Try it, and discover that you can't.  Know that you probably can't get them to run from the command line, because so far nothing else has worked from the command line.  Go to other computer or reboot out of Linux.  Go back to Windows.  Connect to the internet. Find someone who has a clue (wondering all along how it is that there is anyone who actually got far enough to have a clue).

I have no idea how to proceed, to get my modem to work.  Even if/when I get my modem working, I still don't understand how to create a working dial-up connection.  I have read the entire Ubuntu help file on this topic, and I see places to set up a connection, but nowhere to say, "NOW, *connect* with this setup."  I've been using a dial-up network connection from Windows, so it's not as if I've been relying on AOL all along or something.  And when I had another distro before, it used Kppp, which bears a fundamental resemblance to Windows' networking connections.  But I can't find anything in Ubuntu that vaguely resembles a dialer.  (The user probably has to install one.  From a software repository.  Which requires an internet connection.)

I am sorry to sound so frustrated, but I have been trying this (off and on) for at least eight years, and I have never been able to successfully use Linux because I have *never* been able to create a working internet connection.  And it frustrates me to know that there's no way I can recommend Linux to anyone else as an alternative to Microsoft, because normal people can't actually *use* it.

---

### Post by ModelM on 2008-08-12
One of the main reasons people have trouble with dialup on non-Microsoft operating systems is semantics. 

You never hear of anyone looking for a driver for their cable modem or having trouble compiling the kernel module for their DSL modem. So why do people have problems with dialup modems? It's simply because many of these devices which manufacturers label as modems are not. They are semi modems, or half modems or another term you may have heard, win-modems.

A modem for dialup, just as a DSL or cable modem, contains all the necessary hardware & software to do the job. If it doesn't, it's not a modem. I don't think manufacturers should be allowed to call these other devices modems. They should call them a "modem" - including the quotes - or modem-lite.

If you want the easiest method to connect through dialup, use a modem. This would be a device you connect to your computer, tell your software where the modem is (/dev/ttyS0, /dev/ttyACM0, etc) and go online. No drivers, no kernel modules, no confusion or frustration, it just works.

[_Here's_](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002) one which would work fine.

If you don't have a serial port to connect a modem, but do have USB, [_this_](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006) one would do the trick. I use one of these with my laptop.

Anyway, sorry I added to your frustration. I really was trying to help.

---

### Post by A2JC4life on 2008-08-13
No, no, *you* didn't add to my frustration.  This process just *is* frustrating.  You've been very helpful. :)

A hardware modem isn't a very portable option for a laptop, is it?  The one I had before was huge - probably half the size of my current laptop.  (I bought it last time I was trying to get online with Linux, for these same reasons.  Unfortunately, it didn't last long before it died, so I don't have it now.)

---

### Post by ModelM on 2008-08-13
The US Robotics USB modem I linked to in the above message is the one I use with my laptop. It's only about the size of two disposable lighters glued together.

With no power supply required & no software to install, it's about as easy to use as a USB memory stick.

---

### Post by A2JC4life on 2008-08-13
> **ModelM said:**
> The US Robotics USB modem I linked to in the above message is the one I use with my laptop. It's only about the size of two disposable lighters glued together.

Oh, really?  That isn't apparent from the photo (no frame of reference), so I just assumed it was big like the one I had before.  I'll have to check these out.

---

### Post by A2JC4life on 2008-08-13
Another modem question: how can I tell if a modem (on an online retailer's site, in particular) is a hardware modem?  Is it sure to be a hardware modem if it's external?

---

### Post by ModelM on 2008-08-14
I bought my first dialup modem in 1984. (Yeah, I know - a geologist can guess my age more accurately than a doctor can.) I've never seen an RS232 modem which was not a hardware modem.

USB modems are more difficult with most being win-modems of some sort. The USR 5637 I've talked about is a hardware modem, of course. The new phrase some manufacturers are using is "controller based" - meaning a hardware modem.

[_Zoom makes one_](http://www.newegg.com/Product/Product.aspx?Item=N82E16825115022), however, which is a puzzle. If you read the sales blurb, they say it's a controller-based hardware modem & even mention Linux. But there is at least one review on Newegg in which the fellow talks about how easy it was under Linux to compile/install the driver. Since a hardware modem does not require a driver, this makes no sense to me.

The only USB modem I really know is the only one I've used - the USR 5637. You might be interested in reading [_this thread_](http://ubuntuforums.org/showthread.php?t=873268) where I was lucky enough to be able to help a fellow get his working.

---

### Post by A2JC4life on 2008-08-14
Yeah; I read, and was puzzled by, the same things you did about the Zoom modem.  What about [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006")?  The review says there are no drivers to install; that it just plugs in and goes under Linux.

---

### Post by ModelM on 2008-08-14
Yes, that modem is the one I've been speaking of. Mine works quite well.

---

### Post by A2JC4life on 2008-08-15
Oh, cool!  For some reason, that's not the one I saw when I clicked your link.  (Might explain why I wasn't sure about the size.)  But that's really good to know, 'cause I will look into getting one of these!  Thanks. :)

---

