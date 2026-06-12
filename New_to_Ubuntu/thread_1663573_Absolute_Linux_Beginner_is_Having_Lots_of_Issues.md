---
title: "Absolute Linux Beginner is Having Lots of Issues"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by DanPiazza on 2011-01-09
Hi guys, 

I'm pretty new to Linux. I decided to use UNR 10.10.  I barely understand the terminal. I've gotten the hang of apt-get and sudo, and some folder navigation, but still have a ways to go. 

I'm also experiencing some other problems. My Gparted Live USB boots up, I see a bunch of text, then eventually it just stops and never gets to the actual program. I'm hoping to partition my drive to use Linux, Windows, and a data partition. I don't really know how to describe my problem beyond that though.

Also, ever since installing the suggested proprietary drivers, my boot sequence has a huge resolution and looks plain ugly. Should I use other drivers? If so, which ones? I already had to uninstall Unity because that desktop environment had slanted text everywhere once I installed proprietary drivers.

I've also extensively Googled how to compile tar.gz files, to no success. Any suggestions? I already installed build-essentials and tried commands such as make and ./configure to no luck. I really need Linux for dummies or something.

Finally, does anyone know how to use Evolution with Google Apps accounts? I've followed all the instructions Google provided to no luck. My address ends in @bryantdeltachi.org, not @gmail.com, so maybe that has something to do with it.

I understand I'm being kind of vague, but I'm not experienced with a lot of computer jargon, especially Linux. I'm coming from fifteen years of using Windows (finally fed up with another BSOD and crashed partition.)

Thank you in advance for any help you guys can offer, and if you need any more details to aid me I'll be happy to provide them.

---

### Post by OldBoy44 on 2011-01-09
Hello there,

Personally from one newbie to another, I would suggest a fresh install and then controlling the urge to jump in without knowing what you are doing. I would then suggest that you then take your time over a few months to feel your way around. Ask plenty of questions on the forum if your aren't sure of something.

Cheers and good luck,  :D

---

### Post by DanPiazza on 2011-01-09
> **aussiebean said:**
> Hello there,

Personally from one newbie to another, I would suggest a fresh install and then controlling the urge to jump in without knowing what you are doing. I would then suggest that you then take your time over a few months to feel your way around. Ask plenty of questions on the forum if your aren't sure of something.

Cheers and good luck,  :D

My install is only a day old, but I appreciate the advice to take my time. If I get too frustrated, I'll end up dropping the whole idea of switching to Linux. However, it seems a lot more reliable than Windows so far. Some of the problems I listed are really bugging me though..haha.

---

### Post by Kasami on 2011-01-09
Why are you trying to compile tar.gz ?

And as for evolution, uppon first startup there should be a wizard to walk you though it. Type in your email and when you get to Network. Servertype: IMAP Server: imap.gmail.com and username: is whatever is before @bryantdeltachi.org.

Hope that helps a bit. As for proprietary drivers, how did you install them exactly?

---

### Post by DanPiazza on 2011-01-09
> **Kasami said:**
> Why are you trying to compile tar.gz ?

And as for evolution, uppon first startup there should be a wizard to walk you though it. Type in your email and when you get to Network. Servertype: IMAP Server: imap.gmail.com and username: is whatever is before @bryantdeltachi.org.

Hope that helps a bit. As for proprietary drivers, how did you install them exactly?

For a program called Tuxboot-9 that will help to to properly create the Gparted Live USB.

As for Evolution, I tried that and it says "cannot connect to IMAP server @ etc." However, it worked for my standard @gmail.com address.

The proprietary drivers were suggested upon first boot. It was only for graphics and I can view the one I installed through System > Administrative > Additional Drivers. Is it advisable to use these drivers or remove them?

---

### Post by TechWiz2100 on 2011-01-09
> **DanPiazza said:**
> For a program called Tuxboot-9 that will help to to properly create the Gparted Live USB.

Noobie mistake:
tar.gz is an archive not a source package. It needs to be extracted before it can be compiled

> **DanPiazza said:**
> As for Evolution, I tried that and it says "cannot connect to IMAP server @ etc." However, it worked for my standard @gmail.com address.

Evolution is probably having problems auto configuring settings for that mail server, you may have to do it manually

> **DanPiazza said:**
> The proprietary drivers were suggested upon first boot. It was only for graphics and I can view the one I installed through System > Administrative > Additional Drivers. Is it advisable to use these drivers or remove them?

Yes, use proprietary drivers for best performance, unless you wanna stay completely open source

---

### Post by DanPiazza on 2011-01-09
> **TechWiz2100 said:**
> Noobie mistake:
tar.gz is an archive not a source package. It needs to be extracted before it can be compiled.

I read about that after Googling for instructions. Unfortunately, even when I've navigated to the extracted folder in terminal, the commands aren't doing anything. I really need a step by step guide for tar.gz compiling.

> **TechWiz2100 said:**
> Evolution is probably having problems auto configuring settings for that mail server, you may have to do it manually.

I've tried that without the automatic wizard and run into the same issue. I'll take another look though.

Edit: As far as tarbells, I would also like to compile and use this plugin for Rhythmbox so I can keep my music organized similar to iTunes.

> [https://launchpad.net/rb-fileorganizer](https://launchpad.net/rb-fileorganizer)

---

### Post by Kasami on 2011-01-09
What does it say when you go through System > Administration > Additional Drivers ?

You should always do the drivers through there if they're activated in there, de-activate them and it will go back to the default drivers which may look better for you.

To create a live USB, the easiest way I have found is to use the Ubuntu startup disk creator. Download a fresh GParted ISO and then go to System > Administration > Startup Disk Creator. Put your USB in and it should load in Device. Search for your iso up the top, choose the USB drive (You may have to erase the disk) Then click make startup disk.

However you may have already deleted your Windows partition depending on how you installed it. Check by running in a terminal:

```
sudo fdisk -l
```

Hope that clears up a few problems for you.

---

### Post by DanPiazza on 2011-01-09
> **Kasami said:**
> What does it say when you go through System > Administration > Additional Drivers ?

You should always do the drivers through there if they're activated in there, de-activate them and it will go back to the default drivers which may look better for you.

To create a live USB, the easiest way I have found is to use the Ubuntu startup disk creator. Download a fresh GParted ISO and then go to System > Administration > Startup Disk Creator. Put your USB in and it should load in Device. Search for your iso up the top, choose the USB drive (You may have to erase the disk) Then click make startup disk.

However you may have already deleted your Windows partition depending on how you installed it. Check by running in a terminal:

```
sudo fdisk -l
```

Hope that clears up a few problems for you.

This seems like it took care of the problem. Thanks.

My remaining problems are my inability to compile tarbells and the strange resolution issues on boot. I'll test with and without the proprietary drivers installed.

Oh, and while I'm here, how come deleting files on a USB drive only creates a folder on that drive called .Trash1000 with all of the deleted files? I shouldn't have to bring that USB back into Windows in order to permanently delete those files.

Edit: Make Startup Disk won't allow me to select the GParted ISO. It sees it in Nautilus, but then never opens in the program once I hit open.

---

### Post by Kasami on 2011-01-09
It's part of the Unix awesomeness that both Linux and OSX share. To permanantly delete them then in the browser press the eject button, a popup will ask if you want to empty trash and say yes. This will move the files from the .Trash1000 folder.

---

### Post by Kasami on 2011-01-09
> **DanPiazza said:**
> This seems like it took care of the problem. Thanks.

My remaining problems are my inability to compile tarbells and the strange resolution issues on boot. I'll test with and without the proprietary drivers installed.

Oh, and while I'm here, how come deleting files on a USB drive only creates a folder on that drive called .Trash1000 with all of the deleted files? I shouldn't have to bring that USB back into Windows in order to permanently delete those files.

Edit: Make Startup Disk won't allow me to select the GParted ISO. It sees it in Nautilus, but then never opens in the program once I hit open.

Can you supply a screen shot of nautilus with the file and Disk Creator not finding it? Accessories > Screenshot and then click manage attachments on here.

---

### Post by TechWiz2100 on 2011-01-09
Source compiling is different for each program but its usually something along the lines of
```
cd /path/to/src
./configure
make
sudo make install

```

Be sure to check the source of your tarball for building instructions because some require specific compiling programs such as cmake or qmake and most programs have dependencies that you can install via
```
sudo apt-get install <package>
```

[http://www.geeknewz.com/content/view/157/2/]("http://www.geeknewz.com/content/view/157/2/")
That link should help you get a general feel for the build process. Keep in mind that some builds can easily take a few mins to even hours (usually mins tho =P)

I also recommend you seek your apps via Ubuntu Software Center in the Applications menu or finding pre-built binaries and binary install packages (.deb) to avoid building until you're more confident with the terminal if you feel this is all too much.

---

### Post by amsterdamharu on 2011-01-09
1. compile tarbells 
Can you provide a link with the tarball?

2. the strange resolution issues on boot.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
under common issues (I would not recommend un installing the driver I assume you have nvidia)

3. Boot disk
Use unetbootin, it can make any unix distro iso a bootable usb.
```
sudo apt-get install unetbootin
```To start it press alt + F2, type gksu unetbootin and click run.

---

### Post by DanPiazza on 2011-01-09
The first screenshot is after clicking "Other..." in Startup Disk Creator. The second is after I select the .iso and click open. Nothing appears in the program.

---

### Post by DanPiazza on 2011-01-09
> **amsterdamharu said:**
> 1. compile tarbells 
Can you provide a link with the tarball?

2. the strange resolution issues on boot.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
under common issues (I would not recommend un installing the driver I assume you have nvidia)

3. Boot disk
Use unetbootin, it can make any unix distro iso a bootable usb.
```
sudo apt-get install unetbootin
```To start it press alt + F2, type gksu unetbootin and click run.

I won't need to compile the Tuxboot tarbell now that I'm using unetbootin. However, I still would like to be able to compile the tarbell for this Rhythmbox plugin.

> [https://launchpad.net/rb-fileorganizer](https://launchpad.net/rb-fileorganizer)

---

### Post by DanPiazza on 2011-01-09
After using unetbootin with the same .iso that's in the picture I posted, this happens: SYSLINUX 4.01 debian-20100714 EDD Copyright (C) 1994-2010 H. Peter Anvin et al.

---

### Post by amsterdamharu on 2011-01-09
1. compile tarballs 

Downloaded this file, created a folder on the Desktop named install and copied the file there:
[http://launchpad.net/rb-fileorganizer/trunk/1.0.1/+download/rb-fileorganizer1.0.1.tar.bz2](http://launchpad.net/rb-fileorganizer/trunk/1.0.1/+download/rb-fileorganizer1.0.1.tar.bz2)
Then ran the following commands
```
cd ~/Desktop/install
tar -jxvf rb-fileorganizer1.0.1.tar.bz2
./configurator.py 
make
sudo make install
```You can use the mouse (right click) to copy and paste all the commands in a terminal and do the same to copy and paste all the output and post it here if anything goes wrong.

---

### Post by amsterdamharu on 2011-01-09
> After using unetbootin with the same .iso that's in the picture I  posted, this happens: SYSLINUX 4.01 debian-20100714 EDD Copyright (C)  1994-2010 H. Peter Anvin et al.

It usually shows a message like that and ends with a line boot: you should press enter there and a boot menu should appear.

If you still have the Ubuntu iso and the usb is 1G you can use unetbootin to put this on the usb, when you start you can select "try ubuntu" and it'll run off the usb. From there you can start gparted as well.

Please be careful and have patience. Gparted can take a long time to complete and might fail sometimes causing data loss.

---

### Post by DanPiazza on 2011-01-09
> **amsterdamharu said:**
> 1. compile tarballs 

Downloaded this file, created a folder on the Desktop named install and copied the file there:
[http://launchpad.net/rb-fileorganizer/trunk/1.0.1/+download/rb-fileorganizer1.0.1.tar.bz2](http://launchpad.net/rb-fileorganizer/trunk/1.0.1/+download/rb-fileorganizer1.0.1.tar.bz2)
Then ran the following commands
```
cd ~/Desktop/install
tar -jxvf rb-fileorganizer1.0.1.tar.bz2
./configurator.py 
make
sudo make install
```You can use the mouse (right click) to copy and paste all the commands in a terminal and do the same to copy and paste all the output and post it here if anything goes wrong.

Maybe I misunderstood, but I just put the downloaded file in a folder on my Desktop called intall. The extract seemed to work, as well as the configure and make, but not the sudo make install. Here's what I did.

> daniel@daniel-ThinkPad-X100e:~/Desktop/install$ tar -jxvf rb-fileorganizer1.0.1.tar.bz2
AUTHORS
configurator.py
configurator.pyc
fileops.py
fileops.pyc
fileorganizer.py
fileorganizer.pyc
fileorganizer.rb-plugin
INSTALL
LICENSE
Makefile
README
TODO
tools.py
tools.pyc
UNINSTALL
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ ./configurator.py
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ make
# Make environment
mkdir -p "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer"
# Copy files, forcefully
cp * "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer" -f
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ tar -jxvf rb-fileorganizer1.0.1.tar.bz2
AUTHORS
configurator.py
configurator.pyc
fileops.py
fileops.pyc
fileorganizer.py
fileorganizer.pyc
fileorganizer.rb-plugin
INSTALL
LICENSE
Makefile
README
TODO
tools.py
tools.pyc
UNINSTALL
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ ./configurator.py
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ make
# Make environment
mkdir -p "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer"
# Copy files, forcefully
cp * "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer" -f
daniel@daniel-ThinkPad-X100e:~/Desktop/install$ sudo make install
[sudo] password for daniel: 
# Make environment
mkdir -p "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer"
# Copy files, forcefully
cp * "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer" -f
"The Fileorganizer plugin has been installed. You may now restart Rhythmbox and enable the 'Fileorganizer' plugin."
/bin/sh: The Fileorganizer plugin has been installed. You may now restart Rhythmbox and enable the 'Fileorganizer' plugin.: not found
make: *** [install] Error 127


---

### Post by amsterdamharu on 2011-01-09
It looks like this only installs in your home directory so you don't need sudo make install as it's only installed for you.

You can retry installing it after you delete what sudo has done:
> sudo rm -R /home/daniel/.gnome2/rhythmbox/plugins/fileorganizer

Then install it again but no sudo.

sudo make install wasn't needed. You can try to start Rhythmbox and see what it does.

---

### Post by DanPiazza on 2011-01-09
> **amsterdamharu said:**
> It looks like this only installs in your home directory so you don't need sudo make install as it's only installed for you.

You can retry installing it after you delete what sudo has done:


Then install it again but no sudo.

sudo make install wasn't needed. You can try to start Rhythmbox and see what it does.

Well I undid the sudo command and proceeded to "make install." However, there's still the error message at the end.

> daniel@daniel-ThinkPad-X100e:~/Desktop/install$ make install
# Make environment
mkdir -p "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer"
# Copy files, forcefully
cp * "/home/daniel/.gnome2/rhythmbox/plugins/fileorganizer" -f
"The Fileorganizer plugin has been installed. You may now restart Rhythmbox and enable the 'Fileorganizer' plugin."
/bin/sh: The Fileorganizer plugin has been installed. You may now restart Rhythmbox and enable the 'Fileorganizer' plugin.: not found
make: *** [install] Error 127


Edit: It seems like it installed, however I'm still confused why there is an error message at the end of the make install command. Tarbells are so confusing to me, why doesn't everyone use .deb?

---

### Post by DanPiazza on 2011-01-09
> **amsterdamharu said:**
> It usually shows a message like that and ends with a line boot: you should press enter there and a boot menu should appear.

If you still have the Ubuntu iso and the usb is 1G you can use unetbootin to put this on the usb, when you start you can select "try ubuntu" and it'll run off the usb. From there you can start gparted as well.

Please be careful and have patience. Gparted can take a long time to complete and might fail sometimes causing data loss.

Pressing enter or any other button at this point does nothing.

---

### Post by amsterdamharu on 2011-01-10
I came across this script that might help you out creating the bootable USB but it formats the usb drive so make sure no other drive is plugged in and there is no important data on the one you're going to boot with.

[http://sourceforge.net/projects/multibootusb/](http://sourceforge.net/projects/multibootusb/)

If that still doesn't work then try downloading [tinycore]("http://www.tinycorelinux.com/") (10MB linux with gui ) and use unetbootin to stick that on your USB, if it still doesn't boot I'd look into the bios or maybe the stick isn't capable of booting.

Did you get your plugin in Rhytmbox?

Did you fix the resolution on startup?

---

### Post by DanPiazza on 2011-01-10
> **amsterdamharu said:**
> I came across this script that might help you out creating the bootable USB but it formats the usb drive so make sure no other drive is plugged in and there is no important data on the one you're going to boot with.

[http://sourceforge.net/projects/multibootusb/](http://sourceforge.net/projects/multibootusb/)

If that still doesn't work then try downloading [tinycore]("http://www.tinycorelinux.com/") (10MB linux with gui ) and use unetbootin to stick that on your USB, if it still doesn't boot I'd look into the bios or maybe the stick isn't capable of booting.

Did you get your plugin in Rhytmbox?

Did you fix the resolution on startup?

Thanks for the response. Rhythmbox seems to be working fine, but the resolution is still really messed up on boot. I'm going to try the USB with the script (and Tinycore if it doesn't work) right now.

Edit: I got a menu with the bootable USB this time, but when I select GParted I get:

> error: file not found.
error: you need to load the kernel first

Press any key to continue...

Edit 2: I tried to remove to proprietary driver. This succeeded in fixing the boot resolution, but resulted in much slower performance all around. I reinstalled it as a result. 

My boot also mentions something about needing a reserved MMIO region or it not being found (or something to that nature.) It doesn't seem to affect anything, but it's rather annoying to see on every boot.

---

### Post by oldos2er on 2011-01-10
Python code (*.py files) doesn't need to be compiled. According to the web page you linked to, "When you have the files downloaded, you will notice an INSTALL file. Just run it (by double-clicking, of course) and you will get the plugin installed--just like that." Read the README if you need more help.

I think the low resolution during boot that you see when proprietary drivers are installed is a problem with plymouth. See [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by DanPiazza on 2011-01-10
> **oldos2er said:**
> Python code (*.py files) doesn't need to be compiled. According to the web page you linked to, "When you have the files downloaded, you will notice an INSTALL file. Just run it (by double-clicking, of course) and you will get the plugin installed--just like that." Read the README if you need more help.

I think the low resolution during boot that you see when proprietary drivers are installed is a problem with plymouth. See [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Thanks, other than the strange text about the MMIO regions, the resolution on my boot and shutdown has been fixed even with proprietary drivers. It's just unfortunate that I haven't found a good way to split this one 250GB partition (that includes my Ubuntu installation) into two others (one for Windows 7 and one for data.)

---

### Post by amsterdamharu on 2011-01-10
Boot resolution:
Does the boot menu show up? (it's where you can choose what to boot like Ubuntu and Ubuntu resque).
If it does you can select the entry you want to boot (usually the top one) press e to edit and replace splash with nosplash.

Bootable USB:
It seems that the iso is broken or something. If tinycore works and you have a cable internet connection you can try to install gparted on tinycore and run it from there. But I would advice taking the ubuntu iso and stick it on the usb with unetbootin, then update gparted and run from there.

---

### Post by DanPiazza on 2011-01-11
> **amsterdamharu said:**
> Boot resolution:
Does the boot menu show up? (it's where you can choose what to boot like Ubuntu and Ubuntu resque).
If it does you can select the entry you want to boot (usually the top one) press e to edit and replace splash with nosplash.

Bootable USB:
It seems that the iso is broken or something. If tinycore works and you have a cable internet connection you can try to install gparted on tinycore and run it from there. But I would advice taking the ubuntu iso and stick it on the usb with unetbootin, then update gparted and run from there.

The boot seems stable and in the proper resolution now. Maybe I'm just used to how clean the Windows 7 splash was compared to all the text I get before the Ubuntu splash on both boot and shut down.

---

