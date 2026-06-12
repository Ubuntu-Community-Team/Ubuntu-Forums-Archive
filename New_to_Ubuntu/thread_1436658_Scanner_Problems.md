---
title: "Scanner Problems"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by bigal1932flying on 2010-03-22
In previous versions of Ubuntu I have been able to scan documents using my hp scanjet 3970 Scanner and XSane Image Scanner.
Now in 9.10 I find I cannot do this and after several attempts including  installing Simple Scan I now find that my scanjet has disappeared from the list of Available Devices.
Does anyone know how to fix this?

---

### Post by Psumi on 2010-03-23
Are libsane-extras and sane-utils installed?

---

### Post by lkraemer on 2010-03-23
What about trying to install xsane?

SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER

RELOAD, then search for xsane .......to see if it is installed.

lk

---

### Post by Psumi on 2010-03-23
> **lkraemer said:**
> What about trying to **install xsane**?

SYSTEM -> ADMINISTRATION -> SYNAPTICS PACKAGE MANAGER

RELOAD, then search for xsane .......to see if it is installed.

lk

> **bigal1932flying said:**
> In previous versions of Ubuntu I have been able to scan documents using my hp scanjet 3970 Scanner and **XSane Image Scanner**.

...

---

### Post by bigal1932flying on 2010-03-23
XSane has always been installed. I tried doing a re-install but nothing has changed. The scanner still does not show up in Available Devices.

---

### Post by lkraemer on 2010-04-04
In that case it probably is one of the following:
1.  No Power to Scanner from Power Supply.
2.  Scanner has a blown fuse and doesn't work on any OS.

Have you tried it on another OS where it was functional?

lk

---

### Post by prule on 2010-04-05
I've got scanner problems too - with my brother DCP-135C. If I run XSane, it only sees the web camera.

I thought it was a permissions problem, but after adding the user to the 'lp' group and doing a chmod 777 on the /dev/... dir I still haven't had any luck.

Printing works fine.

---

### Post by flyfishingphil on 2010-04-06
> **prule said:**
> I've got scanner problems too - with my brother DCP-135C. If I run XSane, it only sees the web camera.

I thought it was a permissions problem, but after adding the user to the 'lp' group and doing a chmod 777 on the /dev/... dir I still haven't had any luck.

Printing works fine.
Trying out Karmic Koala (v9.10)

Couldn't get my Canon scanner to work under Xsane but them was told to try Scanner Utility found in Applications>Ubuntu Software Center>Graphics. Works great now! Might try that.

---

### Post by bigal1932flying on 2010-04-06
Scanner works OK in Windows XP.
But the only Available Devices that appear when I open XSane are:
Leadtek Winfast and UVC Camera.
The Scanner used to appear but has now disappeared.

---

### Post by sandyd on 2010-04-06
> **bigal1932flying said:**
> Scanner works OK in Windows XP.
But the only Available Devices that appear when I open XSane are:
Leadtek Winfast and UVC Camera.
The Scanner used to appear but has now disappeared.
can you do
```

ls /dev
```?

---

### Post by bigal1932flying on 2010-04-07
Output from command:
adsp             loop1               ram13       tty    tty4     usbmon0
agpgart          loop2               ram14       tty0   tty40    usbmon1
audio            loop3               ram15       tty1   tty41    usbmon2
audio1           loop4               ram2        tty10  tty42    usbmon3
binder           loop5               ram3        tty11  tty43    usbmon4
block            loop6               ram4        tty12  tty44    v4l
bus              loop7               ram5        tty13  tty45    vbi0
cdrom            lp0                 ram6        tty14  tty46    vboxdrv
cdrom1           mapper              ram7        tty15  tty47    vboxnetctl
cdrw             mcelog              ram8        tty16  tty48    vcs
cdrw1            mem                 ram9        tty17  tty49    vcs1
char             midi2               random      tty18  tty5     vcs2
console          mixer               rfkill      tty19  tty50    vcs3
core             mixer1              rtc         tty2   tty51    vcs4
cpu_dma_latency  mixer2              rtc0        tty20  tty52    vcs5
disk             net                 scd0        tty21  tty53    vcs6
dmmidi2          network_latency     scd1        tty22  tty54    vcs7
dsp              network_throughput  sda         tty23  tty55    vcs8
dsp1             null                sda1        tty24  tty56    vcsa
dvd              nvidia0             sda2        tty25  tty57    vcsa1
dvd1             nvidiactl           sda5        tty26  tty58    vcsa2
dvdrw            oldmem              sequencer   tty27  tty59    vcsa3
dvdrw1           parport0            sequencer2  tty28  tty6     vcsa4
ecryptfs         pktcdvd             sg0         tty29  tty60    vcsa5
fd               port                sg1         tty3   tty61    vcsa6
fd0              ppp                 sg2         tty30  tty62    vcsa7
full             psaux               shm         tty31  tty63    vcsa8
fuse             ptmx                snapshot    tty32  tty7     video0
hidraw0          pts                 snd         tty33  tty8     video1
hidraw1          radio0              sndstat     tty34  tty9     zero
hpet             ram0                sr0         tty35  ttyS0
input            ram1                sr1         tty36  ttyS1
kmsg             ram10               stderr      tty37  ttyS2
log              ram11               stdin       tty38  ttyS3
loop0            ram12               stdout      tty39  urandom

---

### Post by lidex on 2010-04-08
How about:
```
lsusb
```

---

### Post by bigal1932flying on 2010-04-09
Output from lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:c215 Logitech, Inc. Extreme 3D Pro
Bus 001 Device 005: ID 046d:0805 Logitech, Inc. 
Bus 001 Device 004: ID 3000:0018  
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Scanner is plugged into 4 Port Hub

---

### Post by lidex on 2010-04-09
Try plugging it directly into a usb port, reboot, and then run that command again.

---

### Post by bigal1932flying on 2010-04-10
Tried plugging scanner directly into computer usb.
Results from command:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:c215 Logitech, Inc. Extreme 3D Pro
Bus 001 Device 005: ID 046d:0805 Logitech, Inc. 
Bus 001 Device 004: ID 3000:0018  
Bus 001 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Hope this helps doesn't mean anything to me.

---

### Post by lidex on 2010-04-10
Looks to me like it's not being recognized. Is this a multi-function unit? Have a look here:
[http://ubuntuforums.org/showthread.php?t=1337731]("http://ubuntuforums.org/showthread.php?t=1337731")

BTW: lsusb on my system shows this entry for scanner:
Bus 002 Device 003: ID 04b8:0110 Seiko Epson Corp. Perfection 1650

---

### Post by SoFl W on 2010-04-10
There are a lot of problems with the latest libsane.  [SIZE=2]**[See this]("https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/428476")**[/SIZE]

---

### Post by bigal1932flying on 2010-04-11
Command line sudo sane-find-scanner result:
found USB scanner (vendor=0x0001 [hewlett packard], product=0x0058 [hp scanjet]) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
afrancis@afrancis-desktop:~$ scanimage -L
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
device `v4l:/dev/video1' is a Noname Leadtek Winfast 2000XP Expert virtual device
device `v4l:/dev/video0' is a Noname UVC Camera (046d:0805) virtual device

---

### Post by CressidaJL on 2010-04-12
> **bigal1932flying said:**
> In previous versions of Ubuntu I have been able to scan documents using my hp scanjet 3970 Scanner and XSane Image Scanner.
Now in 9.10 I find I cannot do this and after several attempts including  installing Simple Scan I now find that my scanjet has disappeared from the list of Available Devices.
Does anyone know how to fix this?
According to the [Ubuntu help page](https://wiki.ubuntu.com/HardwareSupportComponentsScannersHp), you should be able to sort it as the hp 3900 driver is supported. Although it does mention that on some computers it doesn't work automatically; you have to download [this file]("http://downloads.sourceforge.net/hp3900-series/hp3900-series_0.12.tar.gz?modtime=1206122562&big_mirror=0"), extract it into your driver directory, then move into said directory, open a terminal, and run: "sudo ./UPDATE.sh".

---

### Post by bigal1932flying on 2010-04-12
Have downloaded File but I do not know how to proceed.
Thanks!

---

### Post by lidex on 2010-04-13
> **bigal1932flying said:**
> Have downloaded File but I do not know how to proceed.
Thanks!
Extact the files from the archive and open the readme file for help.

---

### Post by bigal1932flying on 2010-05-05
I have updated to 10.04 and now have a different problem. 
When I try to open Xsane Image Scanner I receive the message:
"no devices available"
I obviously still need help. PLEASE!

---

### Post by lidex on 2010-05-05
Just do the same fix as last time.

---

### Post by bigal1932flying on 2010-05-10
Trouble is I didn't  have a fix last time.

---

### Post by lidex on 2010-05-11
Have you tried post #19?

---

### Post by bigal1932flying on 2010-05-12
I don't know how to extract file into Driver Directory and so on.

---

### Post by lidex on 2010-05-12
I'm guessing you've downloaded this file at some point. Move it onto your desktop. Right-click the file icon and select 'extract here'. Open a terminal="Applications->Accessories->Terminal". Enter these commands, one line at a time, pressing enter for each and allowing to complete. Enter your user password when prompted - it will not display.
```
sudo -i
cd ~/Desktop/hp3900-series_0.12/
./INSTALL.sh --type 2 --adistro
```

Restart.

---

### Post by bigal1932flying on 2010-05-14
I have " hp3900-series_0.12.tar.gz" file on my desktop but when I enter command line "cd ~/Desktop/hp3900-series_0.12/" it says no such File.
I have tried adding the "tar.gz" but still receive the same answer.
Have just noticed that as well as the tar package on my Desktop I also have a File "hp3900-series_0.12"
Thanks very much for your help so far.
Sorry about my ignorance.

---

### Post by lidex on 2010-05-14
I guess root needs a different path syntax. Do this: open a terminal
and enter:
```
sudo -i
```
Now type in 
```
cd
```
and hit the spacebar. Drag the directory (not the tar.gz file) from your desktop into the terminal. The path should appear. Hit <enter>
Now enter this command:
```
./INSTALL.sh --type 2 --adistro
```

---

### Post by expatCM on 2010-05-15
hmmm ...  I have the exact same scanner running on 9.10.  No issues at all.

I think I had to install the hplip package from synaptic in order to get it going ....  if I remember correctly.

I use it with xsane, gimp and gscan2pdf.  gscan2pdf is especially useful since the program detects your scanner as part of the program and if it is not found or there is a problem you know quickly ...

---

### Post by bigal1932flying on 2010-05-15
Tried the advice in #29. Everything seemed to go OK Terminal said success.
Then tried Restart but still received the message "no devices available"

---

### Post by expatCM on 2010-05-15
I have been trying to remember what I did when I installed this scanner.

I think I installed this package
[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)
I have not read the whole thread so you may have been here already.

I seem to recall that I also had to change the permissions (or was it user and group) on the USB port.

---

### Post by lidex on 2010-05-16
Also make sure your user is in the 'saned' group. 'System>Administration>Users and Groups'

Or buy an Epson :)

---

### Post by expatCM on 2010-05-18
I just installed 10.04 fresh and now my 3970 scanner does not work.  Identical in every respect to the problem in this thread.

The error message is the device is not available, not that it is not found.  To me that suggests a permissions error.

I think the solution is to change the group of the usb port to saned (which is the scanner group).  I have tried this but the group is changed back automatically by the system (even though use of sudo to change the setting).  (the libusb information is found at /dev/bus/usb)

---

### Post by AgentZ86 on 2010-10-20
I have same problem on karmic koala 64

I use to use my scanner just fine then one day no scanners.

I can plug em in and they detect ok, but when I scan I end up with the error message.

I think this is something to do with sane 1.0.14 or some version that recently updated in ubuntu 64 versions

All my other 32bit versions of 9.10 ubuntu all scanners work and I can interchange them around so I know the scanners themself are working.

But on my 64 bit machine it does not work anymore for some reason.

Here is my thread on it as well

[http://ubuntuforums.org/showthread.php?t=1565340](http://ubuntuforums.org/showthread.php?t=1565340)

---

### Post by AgentZ86 on 2010-11-19
Update of my attempts:

Scanners either detect then fail with error I/O or after the error I/O they no longer detect.

There must be no doubt there something to do with the updates.

From 9.10 64bit through current 10.10

I basically need a scanner and re-installed fresh 10.10 and same thing

Detects and starts to scan with simple scan and xsane but freezes, then error I/O

But just about any scanner I have worked on the 32 bit versions

I have no idea why or how to diagnose this I've tried various solutions but no effect.

---

### Post by pme 72 on 2010-11-19
I just read this today in Rickford Grant's book Ubuntu for Non-Geeks (Lucid):

If you receive a message telling you that no scanners were detected here are a few things you can try:

1-Install the libsane-extras package using the Ubuntu Software Center. This contains a handful of scanner drivers that are not installed by default. Once installed, try opening your scanning program again.

2-Press ALT-F2 to open the Run Application window; then type 

gksudo simple-scan

and click Run, entering your password if prompted. This will start Simple Scan with root privileges, a step that sometimes manages to raise the scanner from its slumber.

3-Check out [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners) to see whether there are any special instructions that you need to follow.

---

### Post by AgentZ86 on 2010-11-20
> **pme 72 said:**
> I just read this today in Rickford Grant's book Ubuntu for Non-Geeks (Lucid):

If you receive a message telling you that no scanners were detected here are a few things you can try:

1-Install the libsane-extras package using the Ubuntu Software Center. This contains a handful of scanner drivers that are not installed by default. Once installed, try opening your scanning program again.

2-Press ALT-F2 to open the Run Application window; then type 

gksudo simple-scan

and click Run, entering your password if prompted. This will start Simple Scan with root privileges, a step that sometimes manages to raise the scanner from its slumber.

3-Check out [https://wiki.ubuntu.com/HardwareSupportComponentsScanners](https://wiki.ubuntu.com/HardwareSupportComponentsScanners) to see whether there are any special instructions that you need to follow.

Yep, I've done all of these and much more

Currently I can scan line art faithfully no problems there.

But as soon as I change it to grey or color no matter the resolution or quality it starts the scan process, then same ole error I/O

When running xsane from the command prompt there is a message which says error bulk read.

But this only occurs when I change from lineart to grey or color.

Sometimes it scans with grey for only (1) page, but the second page has never scanned it freezes the scanner and then the I/O message.

Once I get the I/O message then basically when I try to start xsane it then says no device detected, I have to power off the scanner and back on again so then xsane will see the scanner and I can print lineart again.

Thats about all I can do is line art and this problem exists with other scanners that are working on other machines. I can put them on this machines with 64bit ubuntu 10.10 and they all do the same thing.

And not just on 9.10 but now on fresh install of 10.10 I thought it might solve this.

This appears to be a bug but I don't know enough to fix it.

I considered trying to compile sane separately and installing it, but not sure which version etc ? 

Oh well, thanks for any help on this. Back to the drawing board. LOL

---

### Post by AgentZ86 on 2010-11-20
It appears that scanning lineart in xsane works for the most part

But changing any setting to grey or color will result in the freezup / IO error etc.

Also I cannot copy,email,fax or any other setting except save, or view with lineart as well.

I would have to say this is a bug, or at least a bug with my scanner matchup.

I would get another scanner if I thought that would solve anything, but 3 others scanners here produce the same effect on ubuntu 64bit from 9.10 through 10.10

OH well, back to the drawing board.

---

