---
title: "Barry installation"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by piercleo on 2008-01-08
Hello all,

I am trying to sync my Blackberry (8100 Pearl) to my laptop which is running under Ubuntu Gutsy Gibbon (AMD64), and in particular to evolution. My goal is to have my contacts, calendar events and tasks synchronised between the two of them, preferably without using an online website such as syncevolution. Therefore, I have chosen the *barry* solution:

[http://www.netdirect.ca/software/packages/barry/install.php](http://www.netdirect.ca/software/packages/barry/install.php)

I am using the following website to help me through the (slightly) painful installation process:

[http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html](http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html)

The following packages are installed on my machine:

- pkg-config 0.22-1
- libusb, stable-0.1-4
- openssl 0.9.8e-5ubuntu3.1
- libopensync0 0.19-1.2ubuntu1
- opensync-plugin-evolution 0.19-1ubuntu2

I am stuck at the opensync update part...arg !!!

When I add the two following repositories to my sources.list...
[I]
deb [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) etch main
deb-src [http://opensync.gforge.punktart.de/repo/opensync-0.21/](http://opensync.gforge.punktart.de/repo/opensync-0.21/) etch main[/I]

... I get the following error message:

[http://opensync.gforge.punktart.de/repo/opensync-0.21/dists/feisty/Release:](http://opensync.gforge.punktart.de/repo/opensync-0.21/dists/feisty/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

I feel like it's going to be hard for a newbie like me to...

a/ install Barry properly
b/ learn how to use it in command line

...but I really need to synchronise my phone and evolution.

Any help would be greatly apreciated.

Thank you all in advance,

PC

---

### Post by DoctorMO on 2008-01-08
Your going to need to install all the components from source, those repositories don't even give you the headers you would need to compile barry with sync support.

Install opensync and barry from source, install everything else from packages but remember to install the -dev versions too so you can compile everything correctly.

---

### Post by piercleo on 2008-01-08
Hey, thank you for the answer but it is still quite complicated for me.

I read, i read but wow, so many new words and things to learn.

from what I understand, first step is to downloaded libopensync-0.22.tar.bz2
Go in a console, access the extracted folder and type:
[I]
./configure
make
sudo make install
make clean[/I]

So far so good. Had to install a few things during the configuration process, I installed the dev when it didn't work and kept retrying until the I get to the end of it.

Then I do the same thing with libopensync-plugin-evolution2-0.22.tar.bz2 and I get the following mistake :

*configure: error: No compatible evolution-data-server was found*

I'm stuck, back to looking over the internet.

PC

---

### Post by piercleo on 2008-01-09
If anybody has any idea on what the problem is here, I would greatly appreciate it.

It is really important that I synchronise my BlackBerry with my computer since I am often on the road and I would hate to have to go back to Windows. I have spent two days researching the subject and am having no luck at all.

Thank you in advance,

PC

---

### Post by piercleo on 2008-01-15
Up, Still no solution found to my barry installation problem. Any help would be greatly appreciated.

---

### Post by piercleo on 2008-01-22
Ok i'll ask the question differently : is there any way to install Barry on a machine running Ubuntu Gutsy Gibbon AMD 64 ?

Any help would be greatly appreciated

PC

---

### Post by v912485 on 2008-05-04
Did you have any luck installing Barry on a AMD64 machine? If so can you post the steps? Thanks

---

### Post by ztirffritz on 2008-05-08
I need to figure this out too.  It should be possible to compile from source, but I haven't tried it yet.

---

### Post by thieves.honor on 2008-05-21
make sure you have the evolution-data-server-dev package installed.  thats what got me passed that error.  getting an error now on the make portion.

---

### Post by chipbennett on 2008-05-31
I can't vouch for its applicability to 64-bit Ubuntu, or to Gutsy, but I have written a [how-to for synchronizing a BlackBerry with Kubuntu Hardy]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/").

Let me know if it helps!

---

### Post by karlatsaic on 2008-06-27
> **ztirffritz said:**
> I need to figure this out too.  It should be possible to compile from source, but I haven't tried it yet.

I just compiled the source today running Hardy 8.04 for AMD64 (a Dell XPS M1330 laptop) and it worked well. These were the steps:

[LIST=1]
[*]using synaptic, I installed: libusb-dev, libssl-dev, libtar-dev, libgtkmm-2.4-dev, libglademm-2,4-dev, zlib1g-dev so that I would have necessary header (.h) files for the build.
[*]Downloaded barry-0.12.tar.bz2 from [http://sourceforge.net/projects/barry/](http://sourceforge.net/projects/barry/)
[*]unpack and cd to barry-0.12/
[*]./configure --enable-gui
[*]sudo make install
[*]sudo cp modprobe/blacklist-berry_charge /etc/modprobe.d/
[*]sudo gedit udev/10-blackberry.rules.Debian and replace /usr/sbin/bcharge everywhere with /usr/local/sbin/bcharge. You can specify a prefix in step 4 for the configure script to have the utilities (and libraries and includes) to go to /usr instead of the default /usr/local. I wanted things in /usr/local as a reminder to me that this is the only (non-synaptic) manual mod to my system. Then...
[*]sudo cp udev/10-blackberry.rules.Debian /etc/udev/rules.d/10-blackberry.rules
[*]reboot
[/LIST]
 I just wanted bcharge, barrybackup, and btool (an Exchange server keeps all my stuff in sync - blackberry, evolution(s), outlook--yikes) - so I did not configure --enable-opensync-plugin in step 4. As noted in 7. above, you can also install wherever you like but make sure you edit the udev rules.Debian file in 7 to correctly locate bcharge.

Now, just plug in your blackberry to a USB port. If you type 'bcharge', you should see something like:
```
khr@khr-laptop:~/Computer/barry-0.12$ bcharge
Scanning for Blackberry devices...
Found device #007...already at 500mA...already in desired Pearl mode...no change
```
We all need to **thank** Chris Frey <cdfrey@foursquare.net> for providing a very detailed e-mail response as this did not work for me the first time (missing the correct mods to udev/10-blackberry.rules.Debian) . If you wish to also contact Chris directly mention "barry" and the version you are looking at in the Subject line. Also, he requests you consider joining the barry-devel mailing list on sourceforge to keep the barry issues focused there.  He also explained to me how I could actually create a dpkg 8.04_x86_64.deb package so we could install with the package manager. I am happy with my current configuration, but in hopes someone else will take that on: here is the entire e-mail thread between Chris and me:

```
On Fri, 2008-06-27 at 13:26 -0700, Chris Frey wrote:
> On Fri, Jun 27, 2008 at 01:11:34PM -0700, karlatsaic wrote:
> > I got your e-mail address from the AUTHORS file which came with
> > barry-0.12.tar.bz2. I apologize if you are the wrong contact (could you
> > point me to another e-mail or a forum on which to post - I looked in my
> > usual places - mostly ubuntu forums and couldn't find what I was looking
> > for. Namely a 64-bit ubuntu 8.04 installation of barry).
> 
> Hi Karl,
> 
> You found the right person! :-)
> 
> 
> > I am running ubuntu 8.04 on a Dell XPS M1330 laptop (64-bit). Since
> > the .deb packages on the project site were only for i386, I decided it
> > best to build directly. Note that I have (via apt-get): libusb-dev,
> > libssl-dev, libboost-serialization-dev, libtar-dev, libgtkmm-2.4-dev, 
> > libglibmm-2.4-dev,libglademm-2.4-dev,zlib1g-dev.
> > It is almost working. These are the steps I took
> > 1. unpack tarball and cd to barry-0.12/
> > 2. ./configure --enable-gui  (I only want bcharge and barrybackup)
> > 3. sudo make install
> > 4. sudo cp modprobe/blacklist-berry_charge /etc/modprobe.d/
> > 5. sudo cp udev/10-blackberry.rules /etc/udev/rules.d/
> > 6. sudo mkdir -p /etc/hotplug/usb/  (it did not exist)
> >    sudo cp hotplug/barry /etc/hotplug/usb/
> >    sudo cp hotplug/barry.usermap /etc/hotplug/usb/
> >    sudo addgroup barry
> >
> > Steps 1-3 were straightforward, but 4-6 (esp. 6) were just guessed at by
> > going into the subdirectories and reading READMEs (I would actually
> > liked to just have built a .deb package to use dpkg for installation
> -
> > it looks like all the stuff is there but I have never done that).
> 
> Some notes:
> 
>         - You didn't specify a prefix in the configure line, so you are
>                 installing by default in /usr/local.  This is fine, but
>                 probably not what you want (see below).  Since bcharge
>                 is now in /usr/local/sbin/bcharge, the udev rules
>                 are incorrect, and pointing to /usr/sbin/bcharge.
>                 You'll need to manually edit the 10-blackberry.rules
>                 to point to the right location
> 
>         - If you are using udev, you do not need to bother with hotplug
>                 Hotplug is for pre-udev systems, which don't exist much
>                 anymore.
> 
>         - As you are using Ubuntu, you will likely want to use the
>                 10-blackberry.rules.Debian instead of 10-blackberry.rules.
>                 The Debian version is found in udev/ as well.
> 
>         - Building a .deb package for your system is quite easy... off the
>                 top of my head, you'll need to install the following
>                 packages using apt-get or your favourite package manager:
> 
>                         fakeroot
>                         debhelper
>                         cdbs
> 
>                 Then run the following from inside barry-0.12/
> 
>                         fakeroot -- debian/rules binary
> 
>                 This will generate .deb files in the parent directory
>                 specific for your system.
> 
> > I rebooted just to make sure all is well. I plugged my blackberry into
> > the USB port and this is the output of bcharge:
> >
> >         khr@khr-laptop:~/Computer/barry-0.12/hotplug$ bcharge
> >         Scanning for Blackberry devices...
> >         Found device #003...adjusting charge setting
> >         usb_control_msg failed: code: -1, error sending control message:
> >         Operation not permitted
> 
> Yes, bcharge needs to be run as root, and udev, once properly
> configured with a good rules file, will run bcharge automatically as root, and
> change the permissions so you don't need to be root to run the backup
> and btool commands.
> 

> > It looks like I'm close. Is this a permission problem. What are
> > those "*perm" files? Any other hints?
> 
> The perm files are specific to Fedora systems... I haven't needed them
> on Debian and Ubuntu.
> 
> 
> > Thanks for your time - karlatsaic
> >
> > p.s. on my previous 32-bit laptop the 7.10-i386.deb packages worked
> > perfectly! It would be nice if there were an 8.04-x86_64.deb package
> > as well.
> 
> Great to hear!  Thanks for the report.
> 
> I'd recommend you build your own .deb files as above.  If you run into
> any errors while doing so, let me know.  It is intentionally easy to
> do. :-)
> 
> - Chris


```

---

### Post by siddhantkaul on 2008-07-15
I just completed the steps above as outlined by karlatsaic. When I connect my blackberry bcharge seems to get activated automatically as the "insufficient power" message on the device turns off and lsusb shows the device in the correct mode.

[INDENT][FONT="System"]Bus 002 Device 006: ID 0fca:0004 Research In Motion, Ltd. [/FONT][/INDENT]

However when I run btool, I get the following error message.

[INDENT][FONT="System"]-laptop:~$ btool -v
btool: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory[/FONT]
[/INDENT]

I am running Ubuntu 8.04 (64 bit) on a Vaio SZ430N. I have a 8800. 

Please help...

---

### Post by hamsandwich on 2008-07-16
I had these same errors. I think it implies missing libraries. Did you follow his step #1 exactly?

> using synaptic, I installed: libusb-dev, libssl-dev, libtar-dev, libgtkmm-2.4-dev, libglademm-2,4-dev, zlib1g-dev so that I would have necessary header (.h) files for the build.

or more easily just use "sudo apt-get install " and list each of these separated by a space on the command line. Once I did this, I went to the barry directory, did a "sudo make clean" and redid the configure/make/make install process. After that I had no errors.

good luck. I can see my blackberry now but when launching XmBlackBerry I cannot get the modem info just yet. It tells me "GPRS modem not detected".

---

### Post by siddhantkaul on 2008-07-18
> **siddhantkaul said:**
> 
However when I run btool, I get the following error message.

[INDENT][FONT="System"]-laptop:~$ btool -v
btool: error while loading shared libraries: libbarry.so.0: cannot open shared object file: No such file or directory[/FONT]
[/INDENT]

Well the error had gone away the next day.  (I did nothing except reboot a couple of times in the normal course). However the blackberry kept rebooting when I used btool. Chris Frey, suggested I check if the usb_storage module was installed and to remove it if it was..

[INDENT][INDENT]> -------- Original Message --------
Subject: Re: Barry CVS version on Ubuntu 8.04 (64 bit)
From: Chris Frey
Check whether usb_storage is loaded.  You can do this with the following
command:

    lsmod |grep storage

If it is, unmount any flash storage that might be mounted on your system
(since the Blackberry uses SD cards and they show up as USB Mass Storage
to Linux).  And remove the module:

    rmmod usb_storage

Then try running btool and/or barrybackup again. 
[/INDENT][/INDENT]

This took care of my problem. However you have to remove the usb_storage module ***After*** connecting the blackberry since it is reloaded automatically each time the blackberry is connected.

I have now been able to get the entire package working including the contact/calendar sync-ing

---

