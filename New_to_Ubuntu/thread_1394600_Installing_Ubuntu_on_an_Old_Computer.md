---
title: "Installing Ubuntu on an Old Computer"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by bgphelps on 2010-01-30
Hi,

I am working in a rural community in Peru and two of the four computers the school uses broke down and will not boot.

Since I use Ubuntu personally, I thought I would take a shot and try to install this (specifically install Xubuntu 9.10) on these two computers.

The problems:

I have tried to install Xubuntu with both a USB and with the CDROM. The USB would not boot even though it was detected in BIOS and I set USB to first priority in booting. The CDROM was simply too slow (the CD is fine I tried it Live on two other computers).

My first attempted solution was to borrow a working CDROM Drive from Lima. I installed this and tried to install the Xubuntu disc but even with a new CDROM drive it was slow and eventually would freeze.

Any suggestions? I would love to get these computers working again so I can continue my typing courses with the kids here. 

Best,

Brian

PS. There is no Internet in this community, if that is important. Also, there are two other working computers plus my laptop that I have access too if there is some way to hook the computers together and install Xubuntu this way.

---

### Post by oldos2er on 2010-01-30
What are the specs of these computers?

---

### Post by houseworkshy on 2010-01-30
If the computers are *very* old you may fare better with Puppy linux.  It is the smallest one which works well that I know.  The word processor is abword but it is ok.

---

### Post by Primefalcon on 2010-01-30
use an alt disc, install the base system

boot up and run the following commands

```
sudo apt-get update
sudo apt-get install lxde
sudo mkdir /usr/share/backgrounds
```

this setup will run on only half of the resources that even xubuntu needs

---

### Post by bgphelps on 2010-01-30
I was afraid of that.

The truth is I don't have that information with me right now and the soonest I can find out, and then make a new post, will be a week from today (Feb 6).

Also, since the computers cannot turn on. How can I check the specs? Would I do that in BIOS?

Thanks,

Brian

---

### Post by Easy Limits on 2010-01-30
If the computers don't even turn on then it may be time for a new CMOS battery or the power supplies are shot.

---

### Post by Bartender on 2010-01-30
I don't know how rough things are for you in Peru.  I mean, there's probably not a Fry's store nearby where you could pick up some basic stuff ;)

If the PC's don't hardly boot, I'd say you're wasting your time trying to install an OS until you've checked out the hardware problems.

#1 Guess:  Power supply failing.  Power supplies should be easy to swap back and forth, especially if they're all old 20-pin ATX power supplies and PATA drives, not a mish-mosh of 24 pin ATX, SATA, etc.

#2 Guess: The little coin battery on the motherboard might be dead.  These batteries are generally good for about 5 years, less if the PC has sat around unused.  When you pop out the old battery and pop in a new one all the BIOS settings will go back to default, but that shouldn't be a big deal.

If you think you have a good power supply and you've replaced the coin battery, try to boot into BIOS.  All you need to get to that stage is a CPU and heatsink installed, some RAM plugged into the motherboard, and a keyboard, mouse, and monitor.  I'm assuming these PC's have onboard graphics.  If not, you'll need to have the graphics card plugged in.

If you can get one of them to boot by swapping around power supplies and/or RAM, then shut it down and add a hard drive on the #1 PATA ribbon cable.  Fire it up, go back into BIOS, see if the drive is recognized.  You may have to fuss with the little jumper on the back of the drive.

Start with the very basic setup (motherbaord and RAM) and work up from there.  Best way to find out what is or isn't working.

Oh, yeah, if it runs, but then shuts down in 10 or 15 minutes, the thermal paste under the CPU heatsink is probably no good.  You can watch CPU temps from BIOS unless these PC's are *really* ancient.

---

### Post by bgphelps on 2010-01-30
> **Primefalcon said:**
> use an alt disc, install the base system

boot up and run the following commands

```
sudo apt-get update
sudo apt-get install lxde
sudo mkdir /usr/share/backgrounds
```

this setup will run on only half of the resources that even xubuntu needs

Hi Primefalon,

Can you go into more detail about what this means? I truly am a beginner. 

Also, whenever I have used apt-get it has involved downloading from the Internet. Will this still work without internet access?

>> houseworkshy

I hadn't heard of Puppy Ubuntu before. I see on Wikipedia that one can use a floppy disc to manage the USB install. This might work for me...


>> Easy Limits and Bartender

I can boot into BIOS just fine. I only reach problems when Windows begins to load (blue screen)

Also, when I try the Ubuntu CD it loads on both computers, and after selecting 'Install Ubuntu' I have arrived as far as the install screen that asks for your language selection, but it has never loaded past this. 

With these facts in mind, is it still likely a hardware issue? I don't have a Fry's store nearby : ) but there are enough locally owned computer stores that I'm sure I could find some parts if it were necessary.

---

### Post by *Raz0r* on 2010-01-30
It sounds like you really cannot do much because of the old computers. If they cannot even read properly CD-Drive than I see no other way of how you can get the OS installed on them. You also mention that USB did not work either. Maybe both Ubuntu and Xubuntu specifications are far to high for those computers? You can always try damn smanll linux, it is so low on the requirements that even those PC's should be able to read through floppy or cd-drive.

---

### Post by Primefalcon on 2010-01-30
Sure even I say install a base system using the alternate disc, it'll install a command line only system which is very basic and resource friendly


this will update your repository of software so that they're at the latest version
```
sudo apt-get update
```

this will install a very very light graphical enviroment, half the resources that even xfce needs
```
sudo apt-get install lxde
```

this is just to create a background folder that the screensaver needs
```
sudo mkdir /usr/share/backgrounds
```

---

### Post by bgphelps on 2010-01-30
Mildly unrelated question:

With ongoing conversations, is it good forum etiquette to announce if I will not be responding to messages for a certain time period?

That is to say, my internet cabin time is up, and I need to grab a late dinner before the restaurants close. If my wireless improves I'll have internet until Monday evening, but I won't be able to take a look at the computers in question until Wednesday.

Best,

Brian

---

### Post by lkraemer on 2010-01-30
Brian,
Your initial post didn't specify what version of Windows is installed?
Win98, Win98 SE, XP, NT, or Vista?

If it is XP there is a good website that has Eight Steps to getting XP
booting again.
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)

You might want to check out this article.

If you have Win 98 installed, then it will be somewhat harder.  Have
you tried booting from a Windows Boot Floppy or a DOS Boot floppy?
You could always do that, and then run some Diagnostics on the machines
to verify that they are working properly.  This would also give you
some idea of what is inside these computers.

Also, this site has some good information.
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)
Check the menu on the left side for more options.

And for Boot Disks and CDR's:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
[http://www.allbootdisks.com/](http://www.allbootdisks.com/)

I'd recommend trying the latest version of Damn Small Linux.
[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

Can you provide the error messages, if any of the machines that won't
boot.  The error messages are a good place to start when trying to
recover from non booting machines.

Thanks.

lk

---

### Post by louieb on 2010-01-30
Kind of sounds like these PCs don't have enough ram to run Ubuntu. You should be able to find how much these machines have in BIOS setup.  Knowing that will go a long way in helping you 
  A leaner Distribution such as Puppy or DSL  should do what you need. Both will run on PCs to low in ram or cpu to run Ubuntu.

 The commands Primefalcon gave do require the PC have an Internet connection. Or another option - there are several companies that for about $30 US will send you a DVD set with the entire Ubuntu software repository.   Or even another option is to use one of Ubuntu spin offs that come with a lighter desktop. 

> With ongoing conversations, is it good forum etiquette to announce... 

Actually it a good idea. Especially if you know you won't be back for some time.

---

### Post by Kixtosh on 2010-01-31
Well, I don't know how old is "old", but I'm running Ubuntu on two laptops that are about ten years old ... and if you consider that laptops nearly always have lower specifications than desktops, they are both equivalent to desktops from at least twelve years ago, or more. These are both shown in my signature, but **the oldest is the 1999 Dell** Latitude CPi R400GT:

- Processor: Mobile Pentium II, **400MHz**.
- RAM at maximum, which is **256MB**.
- CMOS battery is so weak that it loses time if it is not plugged in for ten days or so.

Overall, I'd say both of these laptops are working very well after about a week with Ubuntu. There are a few pesky configuration issues to resolve still (audio for the DELL, and external monitor issues for the Portégé), but speed so far is much improved over Windows 2000. In fact, if I can resolve the issues, I'd say that they've never worked any better.

So, if the computers you are trying to fix are no older than ten or twelve years, I'd be hopeful that things will work out, although I might try Xubuntu first. Xubuntu is probably what I will end up using on these too, but Ubuntu works well enough that I'm sticking with it until I've ironed out the issues.

Perhaps you should also consider Edubuntu, since this is for classroom use?

**Also, about the _blue screen issues_: **I had these on the Toshiba Portégé listed below, after it got dropped by accident. The hard disk was fried. I just bought a new hard drive, and it's working like new now. Do you think you might have hard drive issues too? Are the drives of a reasonable size (they should be, if the machines are not really ancient)?

Best of luck with your project!

---

### Post by Jazzy_Jeff on 2010-01-31
I would recommend getting Puppy Linux as well and put it on the CD. You can actually run from the CD if the hard drive is bad. I have an old computer without a hard drive and puppy flies on it with on the CD.

---

### Post by dzon65 on 2010-01-31
+1 for puppy.However,if you want to stay in the ubuntu family,you might wanna install minimal ubuntu.Takes about 70mb.Once installed you can "customize"it to your needs and likings.There are a lot of available windowmanagers,browsers......If you want to stay as close to the "full ubuntu",you could install gnome-core,some gnome-themes etc...It will still be far less demanding than the standard ubuntu.
As for older pc's,even when they're set to boot from cd or usb,(by the way,don't forget to save those settings in the bios) they won't boot from it.If you're running out of options,you might be lucky to find a bios upgrade.
In 99% of the cases,this will make the machine read cd's and usb's.If no pgrade is available,the only way to boot is by swapping hd's.Therefore you'll need a bootable pc however.
Here's some info on minimal:[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by dzon65 on 2010-01-31
> **Primefalcon said:**
> Sure even I say install a base system using the alternate disc, it'll install a command line only system which is very basic and resource friendly


this will update your repository of software so that they're at the latest version
```
sudo apt-get update
```this will install a very very light graphical enviroment, half the resources that even xfce needs
```
sudo apt-get install lxde
```this is just to create a background folder that the screensaver needs
```
sudo mkdir /usr/share/backgrounds
```

first thing to install though:sudo aptitude install xorg

---

### Post by egalvan on 2010-01-31
Since you have no Internet connections where the computers are,
you should download the following when you are at a good broadband.

Low-resource Distros:
TinyCore
  [http://www.tinycorelinux.com/](http://www.tinycorelinux.com/)

TinyMe
  [http://tinymelinux.com/doku.php/home](http://tinymelinux.com/doku.php/home)

Puppy
  [http://www.puppylinux.com/](http://www.puppylinux.com/)

SliTaz
  [http://www.slitaz.org/en/](http://www.slitaz.org/en/)

CrunchBang 
 [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---------------
utilitiy distros:
SystemRescueCD
  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

PartedMagic LiveCD
  [http://partedmagic.com/](http://partedmagic.com/)

SuperGRUB
  [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

----------
Sources for mail-order media

OSDisc  
[http://www.osdisc.com/cgi-bin/view.cgi/index.html?affiliate=distrowatch](http://www.osdisc.com/cgi-bin/view.cgi/index.html?affiliate=distrowatch)

LinuxCD  
[http://www.linuxcd.org/?ref=distrowatch](http://www.linuxcd.org/?ref=distrowatch)

---

### Post by egalvan on 2010-01-31
Since you are working with old computers...

A GOOD cleaning is in order.
using compressed air (preferably from an air compressor, not that canned stuff) completely blow out all the dust and dirt...
don't forget the inside of the power supply, and *carfully* blow out the insides of the floppy and optical drives.
Make sure any heat-sink is dust-free.
This will remove the insulating layers of dust and dirt.


One by one, disconnect and reconnect EVERYTHING.
this should help remove any rust/corrosion/oxide on any connection.


Get a tube of heat-sink thermal paste.
Remove any removable heat-sink, clean the contact area,
any daub on a SMALL amount of paste...
spread it out, and re-install heat-sink
It should be an absolute minimum thickness.
The intent is to fill the microscopic voids in the metals,
not cushion the parts...


Replace the BIOS battery. It should be a 2032.
Next visit to the US, buy some off eBay,
make sure they are name-brand (Sony, Memorex, Mallory, Eveready, etc)
the no-names usually are not worth the low prices.

Boot the machine, go into the BIOS and set things right.
date/time, boot order, hardware present, etc.


Boot a LiveCD that has the Mem86 memory test program...
it will be some variation of the name
'mem86'
'memtest86'
'memtest86+'

let it run at least one full cycle.

If everything OK,
then the machine is ready to rumble.


Oh yeah,,, if you want to erase the hard drives, to use only *nix stuff...
then down-load dban (Darik's Boot And Nuke)
[www.dban.org](www.dban.org)

boot and nuke the whole drive from orbit...
it's the only way to be sure the aliens are gone... :)

Sounds like a lot of work, but it will save much grief in the future.
Grubbing around the insides will give you an intimate knowledge of what's there, and the conditions of the insides.

---

### Post by Abhijit Navale on 2010-01-31
> **bgphelps said:**
> 

I can boot into BIOS just fine. I only reach problems when Windows begins to load (blue screen)



You said that your computers are working. I mean thy are not completely dead.

I have a 7 yr old desktop at my home. When I try to install Ubuntu 9.04 on it then it gives me the same problem as yours. Until BIOS everthing is ok but probem starts at Ubuntu splash screen.

In my case, as per my knowledge my problem is due to less ram capacity. I have 128mb ram. 

I think all these problems are due to old and outdated hardwares.

You said that you have two more comps which are working. I suggest you to use ram chips and graphics chips of that working comps on these dead comps.

I thinkg, considering my experience this problems is due to old ram chips and graphics chips.

I have intel 845 chipset. Intel pentium 4 (1.8ghz) on that old desktop.

The manufacturer have provided me special cd containing drives for graphics, network, sound etc etc. Each time I do the reinstallation ( I have wiondows on that old machine) I must have to manually install all these drivers from the cd.

I suggest you to check if your comp requires such drives installation manually or what?

---

### Post by bgphelps on 2010-02-01
I will be heading back to the community I work in this evening. My plan for the week (regarding the computers) is to

1) Figure out the specs on these computers (and they are XP btw)
2) Attempt installs with an alt disc and Puppy Linux
3) Try most of the stuff Ikraemer and egalman mentioned
4) Try installing a new version of BIOS to get the USB install to work as dzon65 mentioned
5) Try to find an air compressor and clean, and maybe dbaning

Thanks everyone for your help, and I'll post an update this Saturday

Best,

Brian

---

### Post by lkraemer on 2010-02-01
Brian,
Here are a couple more bookmarks that I had on my Desktop for
troubleshooting Registry Problems. 

[http://ubuntuforums.org/showthread.php?t=624943](http://ubuntuforums.org/showthread.php?t=624943)
[http://blogs.techrepublic.com.com/window-on-windows/?p=1165](http://blogs.techrepublic.com.com/window-on-windows/?p=1165)

Also, unless you have enough Heat Transfer Lube, like Artic Silver 5,
I'd suggest not removing the CPU heatsinks.  Too little Heat Transfer
Lube can cause more problems that slightly too much.  Been there,
done that!

UPDATE: 01-02-2010
Also this site might be of help:
[http://forums.majorgeeks.com/showthread.php?t=35407](http://forums.majorgeeks.com/showthread.php?t=35407)

Good Luck.

lk

---

### Post by Bartender on 2010-02-01
Be careful with the air compressor.  You don't want to blast oil or water or rust from the insides of the air compressor into your PC.  I've used an air compressor plenty of times, but I turn the regulator down to about 25 psi or so.  It'd be a good idea to let the compressor sit for a bit before using it.  Let the water and dirt settle.  

Stick a pencil or something between the fan blades before blasting them.  You can destroy a fan by spinning it up to about 10,000 RPM with a direct shot.

---

### Post by bgphelps on 2010-02-08
Hey friends,

Here's the report from the week:

**Specs:**

I wasn't entirely sure how to pull this information up from BIOS and only managed to get some info from one of the computers. Here is what we know.


> 
Floppy Drive B: None
Display Type: VGA/EGA
AMIBIOS Date : 01/31/02
External Cache 256, Enabled
Serial Port(s) : 3F*
Parallel Port(s): 378
Processor Clock : 1.30 GHz
Power Management : APM/ACPI

Hard Disk(s)
Primary Master CYL = 40395 Head = 16 Sector = 63 Size = 20848 MB  LBA Mode = LBA 32bit Mode 32bit Mode = On Block Mode = 16Sec PIO Mode = 4 ATA Mode = 33

PCI Devices:

Onboard IDE, IRQ14, 15 Onboard USB Controller, IORQ10. Onboard Communication Device, IRQ11, Onboard Multimedia Device, IRQ9, AGP VGA

Intel Celeron 1.3 GHZ 

PC One


I'm not sure that most of this info is useful but I thought I'd put it all up just in case.

**Problems with Computers**

Here are the error messages I received:

*When turning on computer A*
> 
Receive the following error

*** STOP: 0x0000007B (0x000009C, 0x00000000, 0x00000000)
INACCESSIBLE_BOOT_DEVICE

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps. 

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Refer to your Getting Started manual for more information on troubleshooting stop errors.

*When Turning on Computer B:*
> 
Registro no puede cargar la sección (archivo):

SystemRoot\System32\Config\SOFTWARE
su registro o alternativo.
Está dañado, austente o no se puede escribir

Empezando el volcado de memoria física
Descarga de memoria fisica completa.
Póngase en contacto con su administrador de sistema o grupo de suporte técnico para obte

My Rough Translation : 

The registry is unable to load the archive SystemRoot\System32\Config\SOFTWARE, your registry is damaged, absent, or unable to write. 

Starting the dump of physical memory. Download of physical memory complete. Contact your system administrator or technical support group to obtai





**What I did this week**

1) Cleaned the computers with air compressor

2) Attempted to install the following programs and received the following errors

- Crash Bang

When using CrashBang Disc received the following error:

Invalid or corrupt local kernel image

- Puppy Linux

When loading Puppy Linux (2 different burn attempts, one on slowest speed)

Just wait 5 seconds for normal startup!
For a list of boot options, press the <F2> key
Loading vmlinux.isolinux: Disk error 20, AX=4271, drive EF

- Tiny Core

ISOLNIUX 3.82 2009-06-09 ETCD Copyright (C) 1994-2009 H. Petre Anvin et al 
iso linux: Disk error 20, AX = 4258, Drive EF
Boot failed: press a key to retry




And that's all I have to show right now. I will have Internet all day today (Feb 8th) and early in the morning tomorrow (Feb 9th) (GMT -5)

Thanks

Brian

---

### Post by coolbrook on 2010-02-08
Another option is to install from the [Ubuntu Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") (and do not choose Ubuntu Desktop when prompted.)  You can then add the applications and functionality you prefer after the install.  I'm posting this from a 1.0 GHz machine with 1.5 GB RAM, 128 MB video card and it's running smoothly with Gnome as the desktop environment.

All the system needed was a browser, e-mail client, office, DVD playback/burning and a driver for a printer.

([Multimedia HowTo]("http://ubuntuforums.org/showthread.php?t=766683"))

Arch Linux is a distro worth trying.  The documentation is fantastic.  I haven't used Gentoo but I keep reading about how it flies, so I'm trying that one next.

---

### Post by lkraemer on 2010-02-08
I'd suggest booting some diagnostics and testing the RAM first.  If that
checks good, I'd run more Diagnostics on the Hard Drive and system.

This site has good information on the 0x7B Error:
[http://kadaitcha.cx/xp/stop_error.html#0x0000007B](http://kadaitcha.cx/xp/stop_error.html#0x0000007B)

Does the BIOS detect the drive?  If so, it most likely can be
made to boot Windows.  You may have to rebuild Windows, which if
done correctly won't create a FRESH install.  
[http://michaelstevenstech.com/XPrepairinstall.htm](http://michaelstevenstech.com/XPrepairinstall.htm)
[http://tech.icrontic.com/articles/repair_windows_xp/](http://tech.icrontic.com/articles/repair_windows_xp/)

Re-read my posting #22 on fixing the Registry with Linux.  That will probably
fix computer B.

lk

---

