---
title: "No TV OUT on ATI 9700 Radeon Mobile Card"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Chrisandsue on 2010-04-04
Ok guys this is my first post so be gentle with me! Just installed Karmic on my Acer Travelmate 290 running an ATI 9700 Radeon Mobile graphics card. Got everything working except the tv out (S video). I have checked loads of posts on this subject but I am now more confused than ever. Is there an easy way to sort this problem? Any special software which can configure the tv out function without resorting to loads of terminal commands?
Any help / push in the right direction appreciated!

Don't forget I am completely new to Ubuntu so go easy on the technical stuff.

Cheers, Chris.

---

### Post by ugm6hr on 2010-04-04
Need some more detail:

What version of Ubuntu?
What kernel?
What ATI driver?

The answers are available if you post output from:
```
uname -a
lshw -class display
lspci | grep ATI
```

---

### Post by Chrisandsue on 2010-04-04
Hi, thanks for the reply.
I am using Ubuntu 9.10, kernel 2.6.31-20 generic, Gnome 2.28.1. As far as I know I am using the standard drivers installed with Ubuntu.

description: VGA compatible controller
       product: RV350 [Mobility Radeon 9600 M10]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

Cheers, Chris.

---

### Post by quadproc on 2010-04-04
> **Chrisandsue said:**
> Ok guys this is my first post so be gentle with me! Just installed Karmic on my Acer Travelmate 290 running an ATI 9700 Radeon Mobile graphics card. Got everything working except the tv out (S video). 

A while back (maybe half a year ago) I read that there was a known bug regarding lack of TV out in some Radeon cards.  This might be the same problem that you are experiencing.

Since it was a while ago, you might find that new graphics drivers would solve the problem. Your driver might be old, depending on where it came from. The newest should be available at the ATI site.  It might be worth perusing the ATI site for bug reports.

quadproc

---

### Post by Chrisandsue on 2010-04-04
Hi Quadproc,
Thanks for the reply. It seems that the tv out function may have worked on the previous version of Ubuntu but not in 9.10, at least this what I have worked out from some of the posts. I have just downloaded the ATI Catalyst driver version 9.3 which seems to be the correct one for my card. I also checked out the installation instructions which state that I should remove the propriety Linux driver before installing the new driver. Any instructions on how to do this appreciated.
The installation instructions also state the following should be installed,
XFree86-Mesa-libGL
&#8226; libstdc++
&#8226; libgcc
&#8226; XFree86-libs
&#8226; fontconfig
&#8226; freetype
&#8226; zlib
&#8226; gcc
How do I check/install these programs?
Sorry to ask so much, thanks for your help.
Chris.

---

### Post by quadproc on 2010-04-04
> **Chrisandsue said:**
> Hi Quadproc,
Thanks for the reply. It seems that the tv out function may have worked on the previous version of Ubuntu but not in 9.10, at least this what I have worked out from some of the posts. I have just downloaded the ATI Catalyst driver version 9.3 which seems to be the correct one for my card.
I think that you may be in the land of legacy drivers and cards.  Recently ATI decided that they would draw a line in the sand and would no longer support drivers for anything before that line.  I _think_ that 9.3 was the latest legacy release.  If so, I would suggest getting a copy of it and keeping it around in a safe place since it may become unavailable.
>  I also checked out the installation instructions which state that I should remove the propriety Linux driver before installing the new driver. Any instructions on how to do this appreciated.Yes, my experience seems to confirm this.  Leaving behind old drivers or their remnants can cause bizarre problems or sometimes complete nonfunctionality. Removing/uninstalling the present driver should be done in the same way that it was installed: that is, if you used Synaptic to install then use it again to uninstall by marking that package for complete removal. You can find Synaptic under System > Administration > Synaptic if it is installed. If you installed the driver by downloading it from the ATI site and running the <downloaded_file_name>.run then hopefully you used the --keep option; if so, there is an uninstall shell script in the directory which you can run by doing
```
cd <the_directory_where_the_script_is>
sudo sh fglrx-uninstall.sh
```If you installed it by using the Hardware Drivers utility then I am not sure which procedure you need to use; I find that that utility is problematic.
> The installation instructions also state the following should be installed,
XFree86-Mesa-libGL
• libstdc++
• libgcc
• XFree86-libs
• fontconfig
• freetype
• zlib
• gcc
How do I check/install these programs?Most of the time these are installed on your system but it is a good idea to be sure that they are all there.  Synaptic can tell you if packages are installed: type in the name and look in the "installed" column of Synaptic; if there is an entry then it is installed.  If not then you can mark that entry for installation.

Another information source that might be useful is the file finder in Places: choose Search For Files and enter the name.  This can tell you if a file of that name is present on your system but not if it is installed.

A few more words about drivers and versions: Ubuntu 8.10 used X windows version 1.5 but Ubuntu versions 9.04 and later use X windows version 1.6.  There is a substantial difference in the way that these two versions work and you cannot swap them around.  Also, ATI's older drivers require X version 1.5 while their newer drivers require X version 1.6.  It is akin to a mine field but there is a good path through the field.

Hope this helps

quadproc

---

### Post by ugm6hr on 2010-04-05
You may be wasting your time with Catalyst.

Ref: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.1&lang=English)

Your card is one of the "legacy" cards.  Unfortunately, Catalyst 9.3 is no longer compatible with newer X versions, so will not work with Ubuntu 9.10 (or 9.04, or 10.04 etc).

Ref: [http://ubuntuforums.org/showthread.php?t=1109768](http://ubuntuforums.org/showthread.php?t=1109768)

The radeon (open source) driver is improving, and apparently includes TV-Out support for R300 cards: [http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon)

I believe this is the correct driver for you - the RV350 is a R300 card (I think): [http://dri.freedesktop.org/wiki/ATIRadeon#head-7e40b0cb972475ff2ca532b0742f86d9ad997a2a](http://dri.freedesktop.org/wiki/ATIRadeon#head-7e40b0cb972475ff2ca532b0742f86d9ad997a2a)

You can check to see if it is being used by running:
```
lsmod | grep radeon
```

There is some advice re: modifying /etc/X11/xorg.conf here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
More advice on the Arch wiki: [http://wiki.archlinux.org/index.php/ATI#TV_out](http://wiki.archlinux.org/index.php/ATI#TV_out)

If you move to 10.04, you have to turn KMS off in order to use a manually configured xorg.conf - ask again if this becomes an issue - I can't remember how to do it with more googling to confirm.

I have an RS690 card on one computer, that I can only get black and white output from S-Video.  I believe that there are some bugs in the RS690 support though, perhaps relating to NTSC mode only working.

---

### Post by Chrisandsue on 2010-04-05
Hi guys,
Thanks for all the advice. Looks like it would be easier to just by a media hard drive rather than using the tv out function.

Thanks anyway, Chris.

---

