---
title: "Can't recognize belkin fd5060 wireless USB adapter"
date: 2004-11-16
forum: Networking &amp; Wireless
---

### Post by rafaeldelinares on 2004-11-16
sorry for my poor english.
first, thx for this distribution and thx for this forum and distributions list as well spanish like english, for all users. The information about the distribution does to wake up it.
the cuestion is my ubuntu can't recognize belkin fd5060 wireless USB adapter, in the spanish's distribution list can`t help me. I don´t know if this adapter can`t work with linux. 
Who can i learn me plesase ? for dummies  :grin: Enyway please tell me other wifi adapter usb work fine with ubuntu. 
my mail is [email]rafaeldelinares@gmail.com[/email]

---

### Post by costoa on 2004-11-16
The Belkin F5D6050 uses the Atmel AT76C503/505A chipset which suffers from poor GNU/Linux support from the vendor. While there are two different GPL drivers out there both have their own problems.

Quite honestly you would be much better off buying an external ethernet to wireless bridge (like the linksys WAP54G). Much, much easier to set up. Maybe someone here could also recommend an internal wireless PCI card too.

While it's possible to get your adaptor working IMO it's not worth the extensive effort needed. Sorry, I wish I could give you better news.

[at76c503a - linux driver for Atmel AT76C503/505A based USB WLAN adapters](http://at76c503a.berlios.de/) 

[Atmel AT76C5XXx Wireless LAN Driver](http://atmelwlandriver.sourceforge.net/news.html)

---

### Post by keverets on 2005-03-28
I've just got my Belkin F5D6050 working with hoary.  To do so, I followed this simple 17 step process:

I added the hoary/multiverse to my /etc/apt/sources.list, then did:

```
apt-get install at76c503a-source atmel-firmware
```

(and made sure that I had the linux-headers installed, in my case linux-headers-k7).  Then:

```

cd /usr/src
tar xvzf at76c503a.tar.gz
cd modules/at76c503a
debian/rules binary-modules KVERS=2.6.10-5-k7
cd ..
dpkg -i <modulename.deb>
depmod -a

```

At that point, unplug and replug the belkin.  That didn't seem to get it in my case, so I did a ```
modprobe -v at76c503a-rfmd-acc
```, which seemed to find the device fine.  I then had a "wlan0" which I could configure with iwconfig, or better still is to put the appropriate settings in /etc/network/interfaces so that they show up on each boot.

So, the Belkin can be made to work with Ubuntu.  It's just a big pain due to the atmel wackiness.

---

### Post by hotspoons on 2005-04-12
[QUOTE=keverets]I've just got my Belkin F5D6050 working with hoary.  To do so, I followed this simple 17 step process:

I added the hoary/multiverse to my /etc/apt/sources.list, then did:

```
apt-get install at76c503a-source atmel-firmware
```

(and made sure that I had the linux-headers installed, in my case linux-headers-k7).  Then:

```

cd /usr/src
tar xvzf at76c503a.tar.gz
cd modules/at76c503a
debian/rules binary-modules KVERS=2.6.10-5-k7
cd ..
dpkg -i <modulename.deb>
depmod -a

```

At that point, unplug and replug the belkin.  That didn't seem to get it in my case, so I did a ```
modprobe -v at76c503a-rfmd-acc
```, which seemed to find the device fine.  I then had a "wlan0" which I could configure with iwconfig, or better still is to put the appropriate settings in /etc/network/interfaces so that they show up on each boot.

So, the Belkin can be made to work with Ubuntu.  It's just a big pain due to the atmel wackiness.[/QUOTE]

Thanks for the writeup!  I have an old box I'm trying to get running on a fresh install of hoary with a belkin F5D6050.  If this is a *fresh* install, you have one PC already loaded and hooked to the internet, and can transfer files between the two systems with a USB key or burned CD's, you need to do the following...

[list]
[*]Boot up your freshly installed hoary box, log in as root (I did "sudo passwd", made a root PW, and enabled "Allow root to login with GDM" under system->administration->Login Screen Setup->Security because sudo is a PITA and I like being root) or prepare to sudo a bunch of crap.

[*]Run system->administration->Synaptic Package Manager, install the following off of the CD:
-- linux-headers-2.6.10-5-386
-- gcc
-- gcc-3.3 (probably only need one of those gcc's...was too lazy to figure it out so I put both on)

[*]On the computer that is already connected to the internet, open a terminal and type:
apt-get install -d at76c503a-source atmel-firmware

[*]With nautilus or the command line, change to the directory /var/cache/apt/archives

[*]Copy at76c503a-source_0.12.beta19-4_all.deb and atmel-firmware_1.0-0ubuntu1_i386.deb (versions as of today) to your USB key or CD-R (or floppy...I haven't used a floppy in years except to load WinXP onto an SATA drive).

[*]Put your removable media into the freshly installed machine, copy those two files to your desktop or somewhere.

[*]Open up a terminal, change directories to where you stuck those files, and type the following two lines:
-# dpkg -i at76c503a-source_0.12.beta19-4_all.deb
-# dpkg -i atmel-firmware_1.0-0ubuntu1_i386.deb

[*]Follow the rest of the instructions for the previous post, and you should get it working (though modprobe doesn't want to find mine and it doesn't really work, it should be working...damn it :( )

[/list]

Hope that helps someone.

-rich

---

### Post by Anguilla on 2005-04-20
I think there is a bug because I get this error:


/usr/src/modules/at76c503a/at76c503-fw_skel.c: firmware atmel_at76c503-rfmd.bin not found.
/usr/src/modules/at76c503a/at76c503-fw_skel.c: You may need to download the firmware from [http://www.thekelleys.org.uk/atmel](http://www.thekelleys.org.uk/atmel) or [ftp://ftp.berlios.de/pub/at76c503a/firmware/](ftp://ftp.berlios.de/pub/at76c503a/firmware/)
at76c503-rfmd: probe of 1-1:1.0 failed with error -14
usbcore: registered new driver at76c503-rfmd

and I searched on google founding this:

[http://lists.debian.org/debian-kernel/2005/03/msg00232.html](http://lists.debian.org/debian-kernel/2005/03/msg00232.html)

how can I resolv the hotplug bug???

---

### Post by angel12 on 2005-05-02
well, after i have done everything above, i plug my card in and i gont get a wlan0. here is what i get via dmesg:
usb 1-1.3: USB disconnect, address 5
usb 1-1.3: new full speed USB device using uhci_hcd and address 6
/usr/src/modules/at76c503a/at76c503-fw_skel.c: downloading firmware atmel_at76c503-rfmd-acc.bin
/usr/src/modules/at76c503a/at76c503-fw_skel.c: firmware atmel_at76c503-rfmd-acc.bin not found.
/usr/src/modules/at76c503a/at76c503-fw_skel.c: You may need to download the firmware from [http://www.thekelleys.org.uk/atmel](http://www.thekelleys.org.uk/atmel) or [ftp://ftp.berlios.de/pub/at76c503a/firmware/](ftp://ftp.berlios.de/pub/at76c503a/firmware/)
at76c503-rfmd-acc: probe of 1-1.3:1.0 failed with error -14

---

### Post by keverets on 2005-05-05
[QUOTE=Anguilla]I think there is a bug because I get this error:


/usr/src/modules/at76c503a/at76c503-fw_skel.c: firmware atmel_at76c503-rfmd.bin not found.
/usr/src/modules/at76c503a/at76c503-fw_skel.c: You may need to download the firmware from [http://www.thekelleys.org.uk/atmel](http://www.thekelleys.org.uk/atmel) or [ftp://ftp.berlios.de/pub/at76c503a/firmware/](ftp://ftp.berlios.de/pub/at76c503a/firmware/)
at76c503-rfmd: probe of 1-1:1.0 failed with error -14
usbcore: registered new driver at76c503-rfmd

and I searched on google founding this:

[http://lists.debian.org/debian-kernel/2005/03/msg00232.html](http://lists.debian.org/debian-kernel/2005/03/msg00232.html)

how can I resolv the hotplug bug???[/QUOTE]

I see this error the first time the module is loaded.  I work around it by doing:

# cd /etc
# modprobe -r at76c503-rfmd-acc
# modprobe -v at76c503-rfmd-acc

a few times.  It will normally pick it up in the second run (you can check how it's doing by doing a "tail -f /var/log/syslog" in another terminal and watching as it tries).

Hope that helps.

---

### Post by whistl on 2005-05-12
I tried everything mentioned here, and kept getting the syslog message:

May 12 16:05:01 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: downloading firmware atmel_at76c503-rfmd.bin
May 12 16:05:11 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: firmware atmel_at76c503-rfmd.bin not found.
May 12 16:05:11 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: You may need to download the firmware from [http://www.thekelleys.org.uk/atmel](http://www.thekelleys.org.uk/atmel) or [ftp://ftp.berlios.de/pub/at76c503a/firmware/](ftp://ftp.berlios.de/pub/at76c503a/firmware/)

I read the debian message referenced by Anguilla at:

[http://lists.debian.org/debian-kern...3/msg00232.html](http://lists.debian.org/debian-kern...3/msg00232.html)

and tried the workaround the author mentioned.  After running:

echo /sbin/hotplug > /proc/sys/kernel/hotplug

then I unplugged and plugged in my Belkin F5D6050 use wireless network adaptor, and the firmware was successfully downloaded:

May 12 16:07:37 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: downloading firmware atmel_at76c503-rfmd.bin
May 12 16:07:37 localhost kernel: /usr/src/modules/at76c503a/at76c503-fw_skel.c: got it.

Now I have a wlan0 interface too.

Thanks everyone!

---

### Post by whistl on 2005-05-13
The problem came back the next time I powered up.  Then I found a couple of lines commented out in /etc/rcS.d/S40hotplug:

case "$1" in
start)
    log_begin_msg "Starting hotplug subsystem..."
    #echo /sbin/hotplug > /proc/sys/kernel/hotplug
    run_rcs $1
    log_end_msg 0
    ;;

stop)
    log_begin_msg "Stopping hotplug subsystem..."
    run_rcs $1
    #echo /bin/true > /proc/sys/kernel/hotplug
    log_end_msg 0
    ;;

Uncommented the two "echo" commands, and power cycled again, and viola!  Now it comes up at boot time - no problem!

---

### Post by Anguilla on 2005-06-14
nice work!! thanks to everyonr for the great solution!!
there is also an other solution:
compiling!

---

### Post by ketzel on 2005-08-12
Hello,
first of all excuse for me poor english.
I'm trying that ubuntu recognise a belkin usb wifi f5d6051. I looked for information on the web and found the drivers for its chipset (Zydas 1201). I followed the instructions but I got an error when i did 'make' in the folder containing this drivers.
The error was 

make[1]: ***No hay ninguna regla para construir el objetivo***

in english i suppose is something like "there is no rule to build this objetivo".

Im not sure if i must copy the drivers to an especific folder to do the 'make' work.
Can someone else help me?

---

### Post by deer421 on 2005-08-13
When I did:
debian/rules binary-modules KVERS=2.6.10-5-k7

I got:
You don't have the compiler that your kernel was built with installed

Please help. I am running ubuntu 5.04 for PowerPC.

---

### Post by samkivi on 2005-09-09
hi guys, I've been trying to get my f5d6050 belkin usb wireless installed following these instructions, (still found it pretty confusing as the apt- get command couldn't find the two files, so I had to search for them in google and download them)

i got to this point:
root@ubuntu:/usr/src/modules # modprobe -v at76c503a-rfmd-acc
FATAL: Module at76c503a_rfmd_acc not found.

and got the error at FATAL.
tried replugging the usb device - no luck
I have no idea how to go from here - can someone help?

thanks!!

---

### Post by keverets on 2005-09-10
[QUOTE=samkivi]hi guys, I've been trying to get my f5d6050 belkin usb wireless installed following these instructions, (still found it pretty confusing as the apt- get command couldn't find the two files, so I had to search for them in google and download them)

i got to this point:
root@ubuntu:/usr/src/modules # modprobe -v at76c503a-rfmd-acc
FATAL: Module at76c503a_rfmd_acc not found.

and got the error at FATAL.
tried replugging the usb device - no luck
I have no idea how to go from here - can someone help?

thanks!![/QUOTE]

apt-get should have found the files for you... it's in both breezy/multiverse and hoary/multiverse.  Did you carefully follow the instructions to add the multiverse to your /etc/apt/sources.list?

Does the following find the module? 

```
find /lib -name "at76c503*"
```

If it doesn't, then you have to make sure that you've installed the binary package and you can check its installed files with:

```
dpkg -L <modulename.deb>
```

(replacing <modulename.deb> with the resulting deb from your build with a name like: "at76c503a-modules-2.6.10-5").

Hope that helps.

---

### Post by keverets on 2005-09-10
[QUOTE=deer421]When I did:
debian/rules binary-modules KVERS=2.6.10-5-k7

I got:
You don't have the compiler that your kernel was built with installed

Please help. I am running ubuntu 5.04 for PowerPC.[/QUOTE]

If you're on PPC, you definitely don't want to be using KVERS=2.6.10-5-k7 ... that's for an x86 (specifically an AMD Athlon).  You'll have to use the appropriate KVERS for your current kernel (you can probably check that with "uname -a" or similar).  You have to make sure that you have the appropriate linux-headers package installed (NOT -k7 in your case).

Hope that helps.

---

### Post by samkivi on 2005-09-10
[QUOTE=keverets]apt-get should have found the files for you... it's in both breezy/multiverse and hoary/multiverse.  Did you carefully follow the instructions to add the multiverse to your /etc/apt/sources.list?

Does the following find the module? 

```
find /lib -name "at76c503*"
```

If it doesn't, then you have to make sure that you've installed the binary package and you can check its installed files with:

```
dpkg -L <modulename.deb>
```

(replacing <modulename.deb> with the resulting deb from your build with a name like: "at76c503a-modules-2.6.10-5").

Hope that helps.[/QUOTE]


ok thanks i got the apt-get working (i had had package manager open and it was locking everything out)
no when I type in

modprobe -v at76c503a-rfmd-acc

it says FATAL: Module at76c503a_rfmd_acc not found.

i can't find any wlan0 or anything showing up in networking.
when plugging/unplugging usb cable, and reading from dmesg i get:

usb 1-1.3: USB disconnect, address 5
usb 1-1.3: new full speed USB device using uhci_hcd and address 6

what do i need to do here? I completely linux illiterate, and if there's anything I also need to do to have this wlan0 setup automatically when i log in i would appreciate info on that also.

THANKS!!

---

### Post by samkivi on 2005-09-12
I would really appreciate an answer to my problem in the message above if anyone knows. please!!!

---

### Post by astroboysoup on 2005-09-27
[QUOTE=ketzel]Hello,
first of all excuse for me poor english.
I'm trying that ubuntu recognise a belkin usb wifi f5d6051. I looked for information on the web and found the drivers for its chipset (Zydas 1201). I followed the instructions but I got an error when i did 'make' in the folder containing this drivers.
The error was 

make[1]: ***No hay ninguna regla para construir el objetivo***

in english i suppose is something like "there is no rule to build this objetivo".

Im not sure if i must copy the drivers to an especific folder to do the 'make' work.
Can someone else help me?[/QUOTE]

Ketzel: you're getting that error becuase you don't have the essential builds installed on to your system.

I found the command at [http://www.ubuntuguide.com](http://www.ubuntuguide.com)
try ryping this in...

[INDENT]sudo apt-get install build-essential[/INDENT]

and now for my problem...

[INDENT]peter@ubuntu:/usr/src/modules/at76c503a$ debian/rules binary-modules KVERS=2.6.1 2-8-powerpc
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/at76c503a'
mkdir -p .tmp_versions
cp /lib/modules/2.6.12-8-powerpc/build/.tmp_versions/*.mod /usr/src/modules/at76 c503a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.12-8-powerpc/build/.tmp_versions/*.mod': No su ch file or directory
make[1]: [modules] Error 1 (ignored)
/usr/bin/make -C /lib/modules/2.6.12-8-powerpc/build SUBDIRS=/usr/src/modules/at 76c503a MODVERDIR=/usr/src/modules/at76c503a/.tmp_versions \
EXTRA_CFLAGS="" modules
make: *** /lib/modules/2.6.12-8-powerpc/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: ** * [modules] Error 2
make[1]: Leaving directory `/usr/src/modules/at76c503a'
make: *** [build-stamp] Error 2[/INDENT]

I'm almost there.

I have the 2.6.12-8-powerpc kern on my iBook. I think I need to install the linux-headers-powerpc... but where do i get this...? Its driving me nuts getting this Belkin wireless working.

Is this what I'm looking for ??? [http://packages.ubuntu.com/hoary/devel/linux-headers-powerpc-smp]("http://packages.ubuntu.com/hoary/devel/linux-headers-powerpc-smp")

---

### Post by toojays on 2005-09-28
The package you want to install is called "linux-headers-powerpc". When you don't know what a package is called, the easiest way to find it is to do a search in Synaptic package manager. Do make sure that the version installed is the same as the kernel you are running (especially since breezy still hasn't stabilised the version number, you may need to upgrade linux-image-powerpc and linux-headers-powerpc at the same time).

For breezy, most packages are built using gcc-4, but the kernel bits are made using gcc-3.4, so you should install that as well.

Another useful package to install for building packages is fakeroot.

When you want to build the at76c503a package, use the command "fakeroot debian/rules binary-modules". Don't set KVERS yourself, the rules file should be able to figure that out from looking at the kernel you are running.

If all goes well, you will end up with a deb file in the **parent directory** of at76c503a. You can install this with "sudo dpkg -i <packagename>.deb".

It is unfortunate that this package does not list the necessary dependencies for building. :(

---

### Post by murkin on 2005-10-15
i've gotten all the way to:

/usr/src/modules/at76c503a$ sudo debian/rules binary-modules KVERS=2.6.12-9

at this point the rules files runs a script which searches for and copies files from:

usr/src/linux-headers-2.6.12-9/lib/modules/2.6.12-9/build/.tmp_versions/*.mod

maybe this could be found in previous versions of the kernel or hoary, but I can't find these folders or directories anywhere on my system. to be more specific, i get to usr/src/linux-headers-2.6.12-9/lib/modules/2.6.12-9 but can't find the /build directory.

am i missing a package?

this is driving me crazy!!

well...off to bed. i hope someone stumbles on this by the time i wake up in the morning. or there goes the rest of my saturday!

Thanks in advance!

---

