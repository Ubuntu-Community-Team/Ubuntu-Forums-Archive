---
title: "where's the guide/link for the completely clueless? -install via usb flash"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by bubbleoffplumb on 2009-09-03
hello
I am a bit embarrassed to post this - but I'm getting nowhere on my own and have to start somewhere.

I will be attempting to put ubuntu on my eee pc (via USB flash drive) and appreciate any assistance.
Below I have listed the computers and flash drive I have available.

I've been reading and searching, but haven't found the "how to - for complete and utter idiots" guide yet.

there seems to be quite a bit of information on this site, but I'm not confident that I can follow it all without some help.
I'm not even sure I'm looking in the right place. I see a lot of information about windows - i have an imac and an asus eee pc.
 
**questions from one who (obviously) hasn't a clue:**
which computer should I use to download to the flash drive (imac or eee pc)?

How do I prepare? the flash drive? - which computer should I use - the eee pc?

I found this:
[https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/9.04/installation-guide/i386/boot-usb-files.html)

but believe it or not, it still seems confusing to me - anyone know of any "hand holding" step by step instructions (imac or eee pc) for folks that don't understand things like "source for packages, possibly in combination with a mirror." 

yes, I'm that bad -
I don't mind reading and following - but if I don't understand what I'm reading, I'm lost.

is there a link somewhere for the completely clueless??

thanks for any help
-she who longs to embrace her inner geek

----------------------
my stuff:

iMac - Desktop

  Model Name:    iMac
  Model Identifier:    iMac8,1
  Processor Name:    Intel Core 2 Duo
  Processor Speed:    3.06 GHz
  Number Of Processors:    1
  Total Number Of Cores:    2
  L2 Cache:    6 MB
  Memory:    4 GB
  Bus Speed:    1.07 GHz
  Boot ROM Version:    IM81.00C1.B00
  SMC Version (system):    1.30f1


Asus Eee PC 900 Netbook with 1.6GHz Atom Processor

BIOS version: 0607
BIOS date: 09/24/2008
software version: Eee PC 1.6.1.3
Build info: 2008-08-06 05:53
CPU type: Intel (R) Mobile Processor
Memory Size: 1024 MB
Motherboard version x.xx

SanDisk
Cruzer Micro 
USB 2.0 Flash Drive    
*****NOTE
this Flash drive has U3 software ?? according to a 
review at amazon it cannot be removed ???

will I need a different flash drive? 
if yes, any recommendations ?

---

### Post by misterfixit on 2009-09-03
USe your Asus machine and go to the following web site:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Follow the instructions therein.

Come back here with more questions.  We are all here to help one another, BTW.

HTH, YMMV,. LSMFT

---

### Post by wojox on 2009-09-03
Did you look at this one as well:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Sealbhach on 2009-09-03
Don't be embarrassed, we've all had to ask something here at some stage.

.

---

### Post by bubbleoffplumb on 2009-09-03
thank you all for responding.

misterfixit -
wemt to the site on the asus
clicked the download for linux
saved file in folder
file system

page still says your download will start shortly ...

somehow I found all file systems - file manager
all I see there  is 
/dev/sda1
ex2 file system (twice)
and
/dev/sda2
ex3 file system

I used "tools" to look for
"unetbootin-linux-356
but it is not found
tried the direct link - same thing

maybe I'm just not used to this asus, but it appears that nothing is happening
still on the page that says
download will start shortly...

wojox
yes I did see that -
I could try it. but before I attempt another approach, I want to see if I'm missing something with my first attempt above.

the instructions aren't very clear to me, but could ask here as I try to get thru it.
would I start by just putting the flash drive in one of the usb ports?

Sealbhach
thanks for the encouragement
I'm afraid it's going to get worse for me before I start doin' any happy dances.

so...
am I right to assume things didn't work out at UNetbootin?
 should I attempt the foreign languages at wojox's link
or any other suggestions???

---

### Post by bubbleoffplumb on 2009-09-03
fwiw
when I plug this usb flash drive in the asus
I get 

"removable storage device was found connected to your system. which program do you want to open it with?"

eta:
also in file manager, now I also see another file icon named:
/media/D:/dev/sb1
vfat file system

and a disk icon:
/media/E:/dev/sr0
iso9660 file system

can I just pull the usb thinggy out, or does it have to be "ejected".
if it does have to be ejected, how do I do that?

---

### Post by mikewhatever on 2009-09-03
What's the operating system you are running on the asus? It seems to be Linux from what you describe, is it? At what stage is the installation of Ubuntu now?

---

### Post by bubbleoffplumb on 2009-09-03
mikewhatever
the asus eee pc has linux
I also have an imac available, but the asus is where I want the ubuntu.

I haven't attempted the ubuntu download yet
I was waiting on UNetbootin.
was just now going to select a "mirror" ??? to try to download from another location??

unless you have a different suggestion?

---

### Post by mikewhatever on 2009-09-04
Well, good luck downloading. Meanwhile, I suggest backing up everything important on the USB because it gets formatted when the installation files are copied over. The same applies to the files on asus.

---

### Post by bubbleoffplumb on 2009-09-04
I'm still at it, but I think I'm gonna give it a break for a few hours.
I've opted to download to my mac and try it that way.
was able to download the img file? for netbook remix,
and I have almost completed "readying" the flash drive (I think) -
having issues with sudo commands in terminal -
will not let me type in a password. I am logged in as an administrator,
but apparently this has something to do with "root user"????
found something online about fixing this in netinfo manager, but I don't see netinfo manager anywhere.

one thing I noticed - none of the hashes??? / md5sum matched up.
([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))
I tried different locations, and same location different download - not ONE of them matched.

the link above warns about proceeding if the hashes don't match. I tried 5 times.
anyone else have this issue?
maybe I'm reading them incorrectly?

thanks for the help
I'll be back soon to push forward.

---

### Post by mikewhatever on 2009-09-04
It doesn't really matter if you download on the mac or the asus, as long as you can move the file around. What OS is there on the mac?
I think you are making things complicated trying to use CLI instead of GUI. Why? As for md5sum mismatches, there is no way to prevent it, other then useing bittorrent.

[http://releases.ubuntu.com/9.04/ubuntu-9.04-netbook-remix-i386.img.torrent](http://releases.ubuntu.com/9.04/ubuntu-9.04-netbook-remix-i386.img.torrent)

---

### Post by bubbleoffplumb on 2009-09-04
os x 10.5.7
I would prefer GUI (had to look those up, by the way ;)
have to agree, things seem very complicated to me too,
I suspect this is due to lack of knowledge, rather than choice.

I used this get ubuntu link:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

once I clicked the download button - more links came up
one on how to create a bootable usb stick
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)
it was here the use of terminal and command lines came up -
I didn't see any other options available.

iirc one of the (many) links I followed mentioned the file couldn't be dragged and dropped.

If you know of any links on making a bootable usb flash drive GUI style - please let me know.

thanks

---

### Post by mikewhatever on 2009-09-04
I now see you were following the instructions for MAC osx, for which there is no UnetBootin. Sorry to tell, but I am not at all familiar with OSX, and can't offer any help.

Regular download options should be fine in most cases, however sometimes, errors happen and there are md5sum mismatches. I remember having to download an iso file several times once, and always prefer bittorrent when available. You can use Transmission for the MAC.
[http://www.transmissionbt.com/download.php](http://www.transmissionbt.com/download.php)

---

### Post by bubbleoffplumb on 2009-09-04
still trying - but losing hope a little...
1st - how do I determine that I have the img file on my usb flash drive?
next -
how do I determine that unetbootin download was successful to the asus eee pc (linux)?
I tried looking in file manager, but didn't see anything there. I am not familiar with the workings of this eee pc (linux).

at one point, I put the usb in (asus) and hit escape

two sandisc cruzer (usb) options come up - the first:

boot error

the second:
Intel UNDI, PXE-2.1 (build 082)
Copyright (c) 1997-2000 Intel Corporation
For Atheros AR8121/AR8113 PCIE Ethernet Controller v1.0.0.4 (2008/01/13)

CLIENT MAC ADDR: 00 23 54 3C )D AF
Check cable connection!
PXE-M0F: Exiting Intel PXE ROM.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

(after I press a key)
boot error

---------
which brings me back a question in my op
can I use this usb flash drive for this purpose? (U3)????

If there is no issue with this flash drive - I will try again - on the asus.
after I figure out either IF UNetbootin was installed, or how to get it to install.

if I don't hear from anyone in a bit - I may start a new post
try this again from the top??

eta: when I plug the usb flash drive into the mac - 

autorun.inf
casper
dists
install
md5sum.txt
pics
pool
preseed
README.diskdefines
syslinux
wubi.exe

I found this "jaunty" folder under dists folder:

main
multiverse
Release
Release.gpg
restricted
universe

I assume this means jaunty is on there.
so It's only a matter of getting the asus to cooperate??

or am I totally in the dark here??

---

### Post by mikewhatever on 2009-09-04
If the img is already on the flash drive, all you need to do is boot from it, in other words, reboot the computer with the flash drive connected. Hopefully the BIOS is set to boot from USB.

---

### Post by mikewhatever on 2009-09-04
It looks like at least some of the files are on the flash drive. Is that the outcome of the procedure for MAC or Unetbootin?

---

### Post by bubbleoffplumb on 2009-09-04
that was the outcome from mac
I started another thread - specific to the boot issues, and I listed the system info for the asus there.

---

