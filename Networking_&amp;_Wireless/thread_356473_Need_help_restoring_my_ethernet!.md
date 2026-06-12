---
title: "Need help restoring my ethernet!"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by Troubled on 2007-02-08
I'm completely new to Ubuntu and even Linux in general, and I've just installed Ubuntu 6.10. Wanting to get online, and thinking that there's no way that Linux could have built-in support for my designed-for-Windows Intel 3945ABG wireless card, I downloaded some tars of source  from Intel's Linux-support site, and began following the directions in the INSTALL file from ieee80211-1.2.16.tgz that I got from ieee80211.sf.net. (sourceforge)

Being completely Linux-illiterate (my computer mastery level is somewhere around "Press Start to begin"), I managed to overwrite my existing networking files (which already had pre-installed drivers) with something completely unusable, without knowing how to undo this.

Could anyone tell me how to restore the default system settings on Ubuntu? I don't mind doing a complete reset, as I haven't begun working under Ubuntu yet, but if there's some (easy) way of fixing the networking directories, that would be preferred.

Help would be much appreciated!

---

### Post by chili555 on 2007-02-08
Hmmmm....my Ubuntu install, outa da box, contains: /lib/modules/2.6.17-10-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko

Before we go too far, which files do you feel like you've botched? If you don't know, let's look at the usual suspects first and see if we can repair them. Open up a terminal and do cat /etc/network/interfaces and post the result here.

We will get it going!

---

### Post by Troubled on 2007-02-08
Well, I did something to the nature of "sudo make install" in the unzipped tar's directory, and it prompted me as to whether I wanted to overwrite the existing files. I assumed that this was but one step on the path to connectivity, and let it overwrite whatever it was that it wanted to overwrite.

In any case, eth1 (my wireless card) no longer appears under my Networking menu, nor does ifconfig or iwconfig bring it up. Is there some sort of system-wide reset button that I can use to restore my original files?

I don't think I modified anything under the directory you specified, though I can't be sure. I'll have to restart and load Linux to find out; I'm currently connecting with Windows.

Do you think you could perhaps take a look at the ieee files for me and see what it tried to do? Thanks! :)

---

### Post by chili555 on 2007-02-08
Well, there is a drastic reset button: you drop the DVD in the drive and re-install. But there are a lot of things we can do before that.

First, your Ubuntu install includes ieee80211, but it's not always as up-to date as Intel's fast-moving  development of IPW. From [http://packages.ubuntu.com/edgy/net/ieee80211-source](http://packages.ubuntu.com/edgy/net/ieee80211-source)
> Though it has been incorporated in latest kernel versions, the bundled one might not be up-to-date to build third-party wireless modules such as ipw2100 or ipw2200 which are common on Centrino notebooks.
So, you are on the right track installing the latest version.

What is the output of sudo ifconfig and sudo iwconfig?

---

### Post by Troubled on 2007-02-08
They deny the existence of my wireless card, though when I run Ubuntu from the CD, the wireless connection shows up. Is there some place I could download a fresh network directory from?

---

### Post by chili555 on 2007-02-08
Is this the road you were headed down? [http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL) I wonder if your problem may be that you are only half done??? You have done the ieee80211 piece but not the ipw3945 piece.

---

### Post by Troubled on 2007-02-08
Yes, I did try to follow those install instructions, but I ran into all sorts of nasty errors when I tried to run make with the 3945 driver.

Anyway, I've done a complete re-install. Networking now sees the wireless card, but I don't know how to make it work. :(

---

### Post by chili555 on 2007-02-08
Hit the reset switch, I see!

See if the correct module is inserted: sudo lsmod | grep ipw3945

Are you using WEP or WPA? If not, I might just try sudo ifup eth1 and see what happens. If so, I'd try temporarily disabling it on your router to see if you can connect.

If you are successful you should see output on the terminal indicating you were assigned an IP address, like this:

```
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.113 -- renewal in 42259 seconds.

```

Let us know.

---

### Post by Troubled on 2007-08-10
My ethernet works now. Thanks for your support!

---

