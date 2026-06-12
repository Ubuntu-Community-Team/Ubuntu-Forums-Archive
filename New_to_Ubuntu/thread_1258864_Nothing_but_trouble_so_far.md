---
title: "Nothing but trouble so far"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by mwhenry16 on 2009-09-05
Having been in the market for a netbook, I just purchased a Dell Inpiron 11z. It did not have an Ubuntu option, and I wanted to try Ubuntu, so I of course went to Ubuntu.com to figure out how I could load it on this computer. The site has a good, easy to follow link to the UNR download link, from which I DL'ed the .IMG file. It also had a link next to the download location to the effect "How to install UNR". From that page I understood to download win 32 Image writer, and understood little of the MD5 sum section.
 
Following the download of the win32 image writer, I attempted to follow the instructions to use it. Heres where things started to go south. When I "opened" win32 it appeared to extract files to a windows folder which opened. It did not appear to install a desktop or startup icon, and the only file I could see that appeared usable to me was an application file, which just redid what I had already done, duplicating the same files. I could never get to the win32 example shown on the Ubuntu website.
 
Dead in the water, i next thought perhaps I could use another "writer" program. So I searched for a trial version of some programs, which either sent me into an endless useless loop to buy 300,000 things I didn't want, or didn't support the IMG. Interestingly at this point, the only two I found that would work fully on any machine were a $100 apple version, or a trial that would only work on 300mb files during trial, unless I spent $70 to "upgrade".
 
Next I thought I'd perhaps try a different version, say Debian or whatever. To a beginner this was worse, and even more confusing. So, I went back to Ubuntu, and tried the forums. Aha, a beginners guide, and free too! (God bless the author). But of course the link was dead to me.
 
So being totally at a standstill, I swallowed my hatred of registering on any site, I did so here, so i could post. I find it interesting that Dell could offer a free upgrade to Win 7 (according to many the best thing since sliced bread, like we haven't heard that since win 3.11), but no upgrade or option to Ubuntu.
 
I'd love to try Ubuntu or linux, and I'd much rather do it through options other than buying a disk or waiting weeks to get one even if it (disk) is free. Internet speed isn't a problem. I'm not a total newcomer to computing, but at this point I sure feel like one.
 
If anyone could get me going past the download, I'd sure appreciate it.

---

### Post by snowpine on 2009-09-05
Hi there, welcome to the forums! Sorry I can't help you troubleshoot the win32 problem, as I've never used that particular application. Here are two other suggestions, neither of them will work with Ubuntu Netbook Remix, but they will work with the regular (non-netbook) Ubuntu release:

1. Buy or borrow a external USB CD drive and install using the Ubuntu Live CD.
2. Download Unetbootin for Windows and use it to create an Ubuntu Live USB:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Either way, you should try Ubuntu for a while in "Live" mode before installing. The 11z is fairly new on the market, so I am not 100% Ubuntu will support all of your hardware. Good luck!

---

### Post by LewRockwell on 2009-09-05
we're on it...

be right back with some links:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[http://en.wikipedia.org/wiki/UNetbootin](http://en.wikipedia.org/wiki/UNetbootin)

[http://en.wikipedia.org/wiki/Ubuntu_(operating_system](http://en.wikipedia.org/wiki/Ubuntu_(operating_system))

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

.

---

### Post by jnorthr on 2009-09-05
just checked the spec of your system and it has 2xUSB ports, so maybe you create a USB version of ubuntu on a 2gb or 4gb key. let me look to see how you could do this from vista.

ok, here's one idea [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

one more: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/]("http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/")
this one looks promising...

---

### Post by Paqman on 2009-09-05
How big is your hard drive? If you can spare a few GB then it's completely possible to have both Windows and Ubuntu on the same machine, set up as a dual-boot.

The easiest way to do this on a machine without an optical drive is to use [Wubi]("http://wubi-installer.org/"). Wubi is an installer for Ubuntu that runs as a Windows program. Just run the wubi.exe, it'll download a disk image for Ubuntu and install it. If you've already got a .iso image, put it in the same folder as wubi.exe and it will use that image instead of downloading a new one. 

Make sure you give Ubuntu at least about 10GB when you install. Enjoy!

---

### Post by bodhi.zazen on 2009-09-05
If you want to try the UNR try the 9.10 alpha :

[http://cdimage.ubuntu.com/releases/karmic/alpha-5/karmic-netbook-remix-i386.iso](http://cdimage.ubuntu.com/releases/karmic/alpha-5/karmic-netbook-remix-i386.iso)

You can then "install" the iso to your usb using unetbootin, which is far easier.

If you do not want to use that alpha release as of yet , use the regular desktop iso.

the netmix is as of now just an interface and can be installed later if you wish (there ar eno specific customizations for netbooks).

There are other netbook specific distros if you prefer including moblin, jolicloud, and kuki.

You may also wish to look at crunchbang or lubuntu :

[LXDE - first lubuntu test iso available]("http://blog.lxde.org/?p=514") 

lubuntu is nice and light, should be very fast, although it may not have all the features of a full desktop.

At any rate, unetbootin is much much easier to use.

---

### Post by mwhenry16 on 2009-09-05
> **snowpine said:**
> Hi there, welcome to the forums! Sorry I can't help you troubleshoot the win32 problem, as I've never used that particular application. Here are two other suggestions, neither of them will work with Ubuntu Netboanok Remix, but they will work with the regular (non-netbook) Ubuntu release:
 
1. Buy or borrow a external USB CD drive and install using the Ubuntu Live CD.
2. Download Unetbootin for Windows and use it to create an Ubuntu Live USB:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
Either way, you should try Ubuntu for a while in "Live" mode before installing. The 11z is fairly new on the market, so I am not 100% Ubuntu will support all of your hardware. Good luck!
 
I do have an external USB drive. I did DL unetbootin, and used the ISO file I had downloaded to write it to a CD-R. Now I have a disk that reads in "My computer" as  F: Install Ubuntu with a list of files, including an application file called wubi, which doesn't seem to do anything, although active in task manager.
 
So if I go this route, what next?

---

### Post by snowpine on 2009-09-05
> **mwhenry16 said:**
> I do have an external USB drive. I did DL unetbootin, and used the ISO file I had downloaded to write it to a CD-R. Now I have a disk that reads in "My computer" as  F: Install Ubuntu with a list of files, including an application file called wubi, which doesn't seem to do anything, although active in task manager.
 
So if I go this route, what next?

Basically, you reboot the computer and boot from the CD. More info:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by mwhenry16 on 2009-09-05
250gb. I also have SDHC, external drive, and USB thumbdrive. Wubi shows up on the burned CD, but doesn't appear to do anything, as I pointed out to another poster. But then I don't know how to use it either. Lots of good stuffed being replied by you and other folks, so thanks.

---

### Post by ScorpKing on 2009-09-05
I use Unetbootin to create a USB live disk whenever I have to install Ubuntu on a Laptop/Netbook with no CD-ROM. After you created the USB disk you need to boot from it. There should be an option to boot from USB when you restart the computer. It is possible that you have to enable the option to boot from USB in the BIOS first.

---

### Post by hockeytux on 2009-09-05
> **mwhenry16 said:**
> 250gb. I also have SDHC, external drive, and USB thumbdrive. Wubi shows up on the burned CD, but doesn't appear to do anything, as I pointed out to another poster. But then I don't know how to use it either. Lots of good stuffed being replied by you and other folks, so thanks.

If you have the .iso file burned on CD now just install it like you are used to from Windows. Put the CD in, reboot and there you are :)

Remember to burn the iso file as image and not just as a data cd. Also there will be a 'check disk for errors' option which is quite useful.

---

### Post by mwhenry16 on 2009-09-05
> **snowpine said:**
> Basically, you reboot the computer and boot from the CD. More info:
 
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
 entioned
Apparently this computer will not allow booting from the USB external drive, or the image or files on the drive are not allowing it to be seen as bootable, the files I mentioned before. I guess I will move on to other options. Thanks.

---

### Post by Paqman on 2009-09-05
> **mwhenry16 said:**
> Wubi shows up on the burned CD, but doesn't appear to do anything, as I pointed out to another poster. 

The actual wubi.exe is tiny, only about 5MB or so. So you could d/load it from their site. By default it will download a whole new disk image when you run it though, so it might not be the quickest route (although if your machine doesn't want to boot from USB it might be your only option...)

---

### Post by ScorpKing on 2009-09-05
Here are a few links that might help (some more that others):

[http://www.plop.at/en/bootmanager.html#runwin](http://www.plop.at/en/bootmanager.html#runwin) <-- this one looks good
[http://ubuntuforums.org/showthread.php?p=4127061](http://ubuntuforums.org/showthread.php?p=4127061)
[http://www.911cd.net/forums//index.php?showtopic=17581](http://www.911cd.net/forums//index.php?showtopic=17581)
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

---

### Post by mwhenry16 on 2009-09-05
I followed one of the links, and with ubootin and an ISO file was able to boot to a Linux menu upon reboot. However, there were three menu option; default, help, and oem-manufac,turer. In addition there was a 10 second timer to “automatic boot” , and a “tab for boot option” or some such verbiage. Pushing enter for any of the three did nothing, the timer just kept recycling, and tabbing brought up a short comman line I’m not familiar with.

---

### Post by bodhi.zazen on 2009-09-05
On that screen, the graphical unetbootin screen. select "default".

If it does not work, back to step 1, check the md5 sum of your iso, wipe the USB, and try again.

---

### Post by stormvinyl on 2009-09-05
Interesting how difficult this is becoming.  This is how I installed Ubuntu.  I downloaded the img file and burned it to a spare usb jump drive I had laying around.  I booted my laptop from the jumpdrive, set in bios, and lloaded Ubuntu live from it.  There are options for disk management, effectively cleaning your harddrive and loading ubuntu fresh, or you can run ubuntu directly from drive to just take it for a test drive and see how you like it.  I learned how to do all this from the "how to install ubuntu" on ubuntus homepage.  And I have loved ever since.  I love telling people, "I dont use windows."

---

### Post by mwhenry16 on 2009-09-06
Solved! By hook or crook, but probably the many links and avenues offered by folks, I was able to get a bootable version on a USB thumb drive.

---

### Post by Torgas Prim on 2009-09-06
Why don't you check [www.support.dell.com](www.support.dell.com) ?
If your system was designed for ubuntu recently, they have the downloadable image available on their website.

---

