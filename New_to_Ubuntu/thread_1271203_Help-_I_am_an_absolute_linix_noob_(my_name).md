---
title: "Help- I am an absolute linix noob (my name)"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by ubuntnoob512 on 2009-09-20
**[COLOR=Red]Please help[/COLOR]. Windows XP wont boot after installing Ubuntu.**


I have a very special computer. Here is it's lifestory. Ok so, i bought it off of ebay as a 2.2gz Core 2 Duo (pretty fast), a 512 NVIDIA graphics card that i was told was relly good, It has a 15.4 inch screen (laptop), Mainly MSI brand whitebox, 111 gb HD, 4 gb of ram, and Windows XP 64 bit (one of the worst operating systems ever. My computer would freze and i would have to restart often.

The computer with powercord, drivers, and actuall win XP 64 bit disk was about $325. Yes, a great deal.

From there I installed Vista 32 bit, vista 64 bit, windows home 32 bit, and finally windows pro 32 bit.

I just recently have put Ubuntu 8.04 on my Xp 32 bit computer. I Partitioned the drive already so i had 5 GB for Testing operating systems like Ubuntu and in the future i want to try snow leopard, Google chrome, other versions of linix, and windows 7. 

In the Ubuntu set up, it would only let me put windows and Ubuntu on the same partion so i currently have a blank 5 GB partion.

Well the who point of this posting:

when i turn on my computer, it goes to the screen that lets me choose between the 2 operating systems.

If i click in Linix, it boots just fine and i am using linix as I am posting this question.

If i click on Windows Xp pro, i get the same blue screen that says something like:
If this is the first time you have seen this screen, restart your computer

If you have seen this screen before, uninstall all newly installed programs.

The only newly installed program is Ubuntu.

So, What do i do. I know a lot about computers but this is my first time using linix. I am not quite sure what to do. If you have read this whole thing and answered i thank you.
                                                      

                                     I forgot to say, I am 14, bad at spelling and i have the Actual Ubuntu disk. ( i burned it)

               

                                                 Linix is on the same partion as windows. And believe me, Windows 64 bit has thrown lots of hissy fits so i got him deleted.

---

### Post by Old_Grey_Wolf on 2009-09-20
Did you do a Wubi install, or Ubuntu inside Windows?

---

### Post by ubuntnoob512 on 2009-09-20
Ok, i backed linix to windows, that is all it said. I put everything that i need on a 1 gb flash drive. 

Someone please help.:popcorn:

I dont know what a wuby install is. Should i try to get rid of linix. I can get to all my files so they arnt deleted. Like i took my desktop backround from xp and put it on linix.

Oh, and ith there a 9.04, i only have Ubuntu 8.04. how do i upgrade?

oh, and what are beans. I have 2 i think.

---

### Post by mike555 on 2009-09-20
sounds like you should study the forums and sites that tell you about dual booting and/or hubi install before you delete windows by mistake ....... no offence , just a warning .

---

### Post by ubuntnoob512 on 2009-09-20
I just want my windows back :'( [-o< It would be nice to have ubuntu but the installing freakes me out. Whenever i try to install something like a flash player it says it is installed but youtube wont work.

---

### Post by mike555 on 2009-09-20
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)   is a good place to read up about different installs and getting boot loader back ...

---

### Post by piyushverma82 on 2009-09-20
I had the same problem some time age, found out that winxp does not support SATA drive, so change the SATA controller setting in BIOS to compatible mode, that will do the trick.

edit: according to me stick to ubuntu it is better.

---

### Post by ubuntnoob512 on 2009-09-20
Wow
wow
wow

i am a noob remember?

how in the world do i do that?

i know what sata is

and i have herd of bois

i think it has to do with the start up operating system

---

### Post by webwiller on 2009-09-20
I think you would need to study some paper before you go...if you like you could start from these:
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/~herman546/index.html")

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

[https://help.ubuntu.com/8.04/switching/dualboot-procedure.html]("https://help.ubuntu.com/8.04/switching/dualboot-procedure.html")

[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20and%20Boot%20Manager]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20and%20Boot%20Manager")

;) Just give it a try!

---

### Post by nhasian on 2009-09-20
It sounds like you installed ubuntu inside of windows (this is the wubi method) as it installed the Ubuntu Operating System inside the windows partition.  If you inserted the ubuntu disk while windows is running and started the install from within windows, then you did wubi.

if however you booted off the Ubuntu CD, partitioned your hard disk, and installed ubuntu onto the blank unpartitioned space on your hard disk, then you are dual booting.

Installing an operating system is considerably more difficult than installing a piece of software.  You should have a basic understanding of hard disk partitions, file system types, changing bios settings, etc.

---

### Post by ubuntnoob512 on 2009-09-20
I dont know how to install a flash player in linix so i couldent watch that video.

Ok, so i partioned the disk

and then i restarted the computer

and after it started to turn on i pressed f11

and put the disk in

and thin installed it while booting off of the disk

---

### Post by jmszr on 2009-09-20
ubuntnoob512,
 
The others seem to have your other problems in hand so I'm limiting myself to the Flash/YouTube concern you have: Click on Applications > Accessories > Terminal and when the Terminal comes up Copy & Paste this into it:```
sudo apt-get install ubuntu-restricted-extras
```and then press Enter. Type in your password when prompted (it won't be visible when you type it-security) and then press Enter. That should do it.

---

### Post by ubuntnoob512 on 2009-09-20
That did something, it just diddent allow me to watch videos. here is what it said:

Download done.
Flash Plugin installed.

Setting up flashplugin-nonfree (10.0.32.18ubuntu0.9.04.1) ...
Setting up freepats (20060219-1) ...
Setting up libavutil-unstripped-49 (3:0.svn20090303-1ubuntu2+unstripped1) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libmp3lame0 (3.98-0.0) ...

Setting up libx264-65 (1:0.svn20081230-0.0ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu3) ...

Setting up libavcodec-unstripped-52 (3:0.svn20090303-1ubuntu2+unstripped1) ...

Setting up libavformat52 (3:0.svn20090303-1ubuntu6) ...

Setting up libpostproc51 (3:0.svn20090303-1ubuntu6) ...

Setting up libswscale0 (3:0.svn20090303-1ubuntu6) ...

Setting up gstreamer0.10-ffmpeg (0.10.6.2-1ubuntu2) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu1) ...
Setting up libenca0 (1.9-6) ...

Setting up libass1 (0.9.5-2) ...

Setting up libcdaudio1 (0.99.12p2-7) ...

Setting up libcelt0 (0.5.1-0ubuntu1) ...

Setting up libdc1394-22 (2.0.2-1) ...

Setting up libdca0 (0.0.5-0.1) ...

Setting up libdvdread4 (4.1.3-4ubuntu2) ...

Setting up libdvdnav4 (4.1.3-3) ...

Setting up mysql-common (5.1.30really5.0.75-0ubuntu10.2) ...
Setting up libmysqlclient15off (5.1.30really5.0.75-0ubuntu10.2) ...

Setting up libgmyth0 (1:0.7.1-1ubuntu1) ...

Setting up libiptcdata0 (1.0.2+libtool01-2ubuntu1) ...

Setting up libxml++2.6-2 (2.24.0-1ubuntu1) ...

Setting up libffado0 (2.0~rc1-0ubuntu2) ...

Setting up libfreebob0 (1.0.11-0ubuntu1) ...

Setting up libjack0 (0.116.1-3ubuntu3) ...

Setting up libraptor1 (1.4.18-2) ...

Setting up liblrdf0 (0.4.0-1.1) ...

Setting up libmms0 (0.4-2) ...

Setting up libmodplug0c2 (1:0.8.4-3ubuntu1.1) ...

Setting up libmpcdec3 (1.2.2-1build1) ...

Setting up libneon27-gnutls (0.28.2-6.1) ...

Setting up libfftw3-3 (3.1.2-3.1ubuntu1) ...

Setting up libofa0 (0.9.3-3) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libsoundtouch1c2 (1.3.1-2) ...

Setting up libwildmidi0 (0.2.2-2) ...

Setting up gstreamer0.10-plugins-bad (0.10.11-2ubuntu1) ...
Setting up libquicktime1 (2:1.1.0+debian-1build1) ...

Setting up libmjpegtools-1.9 (1:1.9.0-0.0ubuntu3) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.11-0ubuntu1) ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...

Setting up libid3tag0 (0.15.1b-10) ...

Setting up libmad0 (0.15.1b-4) ...

Setting up libmpeg2-4 (0.4.1-3) ...

Setting up libsidplay1 (1.36.59-5) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up gstreamer0.10-plugins-ugly (0.10.10.2-1build1) ...
Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.7-2) ...
Setting up raptor-utils (1.4.18-2) ...
Setting up ttf-liberation (1.04.93-1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ttf-mscorefonts-installer (2.6) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-09-20 18:25:07--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:07--  [http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2009-09-20 18:25:07--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/octet-stream]
Saving to: `./andale32.exe'

100%[======================================>] 198,384      483K/s   in 0.4s    

2009-09-20 18:25:08 (483 KB/s) - `./andale32.exe' saved [198384/198384]

--2009-09-20 18:25:08--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:08--  [http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2009-09-20 18:25:09--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

100%[======================================>] 168,176      456K/s   in 0.4s    

2009-09-20 18:25:09 (456 KB/s) - `./arialb32.exe' saved [168176/168176]

--2009-09-20 18:25:09--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:10--  [http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2009-09-20 18:25:10--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

100%[======================================>] 554,208      869K/s   in 0.6s    

2009-09-20 18:25:11 (869 KB/s) - `./arial32.exe' saved [554208/554208]

--2009-09-20 18:25:11--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:11--  [http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/comic32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2009-09-20 18:25:11--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

100%[======================================>] 246,008      772K/s   in 0.3s    

2009-09-20 18:25:12 (772 KB/s) - `./comic32.exe' saved [246008/246008]

--2009-09-20 18:25:12--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:12--  [http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2009-09-20 18:25:12--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

100%[======================================>] 646,368     1.05M/s   in 0.6s    

2009-09-20 18:25:13 (1.05 MB/s) - `./courie32.exe' saved [646368/646368]

--2009-09-20 18:25:13--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:13--  [http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2009-09-20 18:25:14--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

100%[======================================>] 392,440      929K/s   in 0.4s    

2009-09-20 18:25:14 (929 KB/s) - `./georgi32.exe' saved [392440/392440]

--2009-09-20 18:25:14--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:15--  [http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2009-09-20 18:25:15--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

100%[======================================>] 173,288      459K/s   in 0.4s    

2009-09-20 18:25:16 (459 KB/s) - `./impact32.exe' saved [173288/173288]

--2009-09-20 18:25:16--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:16--  [http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2009-09-20 18:25:16--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

100%[======================================>] 661,728     1.16M/s   in 0.5s    

2009-09-20 18:25:17 (1.16 MB/s) - `./times32.exe' saved [661728/661728]

--2009-09-20 18:25:17--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:17--  [http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2009-09-20 18:25:17--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

100%[======================================>] 357,200      766K/s   in 0.5s    

2009-09-20 18:25:18 (766 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2009-09-20 18:25:18--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:18--  [http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2009-09-20 18:25:18--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/octet-stream]
Saving to: `./verdan32.exe'

100%[======================================>] 351,992      904K/s   in 0.4s    

2009-09-20 18:25:19 (904 KB/s) - `./verdan32.exe' saved [351992/351992]

--2009-09-20 18:25:19--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--2009-09-20 18:25:19--  [http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://downloads.sourceforge.net/sourceforge/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2009-09-20 18:25:20--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

100%[======================================>] 185,072      688K/s   in 0.3s    

2009-09-20 18:25:20 (688 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ubuntu-restricted-extras (31) ...
Setting up unrar (1:3.8.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by jmszr on 2009-09-20
ubuntboob512,

Try installing Flash from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)  In the "Select version to download" dropdown menu select ".deb for Ubuntu 8.04+" and then on the next page "Agree and Install now" . The default GDebi package installer should take it from there.

---

### Post by mike555 on 2009-09-20
before you install flash close all firefox windows , so it can install properly.

---

### Post by ubuntnoob512 on 2009-09-21
Ouch, ya, that probably would work, but i don't have enough disk space on my computer.

I have a new post: [http://ubuntuforums.org/showthread.php?p=7986908#post7986908](http://ubuntuforums.org/showthread.php?p=7986908#post7986908)

right now I am focusing on restarting my fail ad dual booting windows and ubuntu.

I am clearing off the hard drive.

---

