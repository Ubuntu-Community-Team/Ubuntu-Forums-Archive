---
title: "Wubi should install, but won't"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by fastermx on 2011-07-13
I'm a total newbie.  Can't get the Windows version of Ubuntu to do anything.  I extracted the download file into Program Files\Ubuntu OS.  Then, as the site told me, I clicked wubi.exe.  Nothing happened.  Just an hourglass for about a minute, then nothing.  It wasn't shown on the menu from ctl-alt-del, either, so it wasn't even trying.

I've copied the downloaded file and the extracted files to a CD, but don't know how to use it to install Ubuntu.

My system has barely enough memory - 256MB Ram, but it is supposed to be adequate, even if slow.

Bios allows me to boot from a CD.  I chose the DVD-CD that contains the original download file and all the files extracted from it - including Wubi.exe.  When I rebooted, it didn't ask if I wanted to boot from the CD as it always has when I reinstalled Windows.  It just went, after a minor pause, into the regular bootup mode.  I chose my HD as the second bootup choice, and it chose that, but I don't know why.

In pure dos, at the command prompt, I went to the wubi.exe file in Program Files/Ubuntu OS.  It wouldn't run.

My OS is W98SE.  For ages now, just about anything I try to download and install is not compatable any more with it.  But I was surprised that Ubuntu wouldn't install on W98SE, because it is supposed to work WITH a Windows OS.  The WHOLE reason I wanted Ubuntu was so that I could continue with W98SE, which is the latest Windows version that lets me use my indispensable apps and favorite old DOS-based games.  Moreover, I can't AFFORD to buy a newer Windows OS.  If Ubuntu isn't compatable with W98SE, what good is it to me?

How can I install this puppy?  The websites are empty of the knowledge I seek.

---

### Post by GWBouge on 2011-07-13
I'm assuming the file you downloaded was an .iso file?  Or did you get the wubi.exe file from the Windows Install download section?  I've never used the wubi.exe download, nor do I know whether or not it's compatible with Win98, so I'm no help there, but if you got the .iso ...

You don't extract an iso and burn the files, you burn the iso *image* to a CD, or mount the iso with something like Daemon Tools.  If you don't know how to do this, either goto the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download"), down to section 2, and click 'Show Me How' ... or Google around.

Also, for a system with 256MB of RAM, you might get a better experience out of [Lubuntu]("http://lubuntu.net/") or [Xubuntu]("http://www.xubuntu.org/").  And for what it's worth, you don't *need* a Wubi install to use both Linux and Windows on the same machine, and a Wubi install is only recommended for a temporary installation, just to check things out.  At some point, you might want to check out setting up a true dual boot system.

Oh, and you can also check out [http://appdb.winehq.org/]("http://appdb.winehq.org/") to see if those indispensable Windows apps might work through WINE, and most old DOS-based games I've tried work pretty well through [DosBOX]("http://www.dosbox.com/") =o)

---

### Post by Rubi1200 on 2011-07-13
Hi and welcome to the forums fastermx :)

> **Which Operating Systems are supported?**

 Windows  Vista, XP, and 2000 are known to work with Wubi. [COLOR=Red]Windows 98[/COLOR] **should** also  work,_ but has not been thoroughly tested_. Windows ME is not supported
(my highlighting of the relevant information)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

The Wubi Guide I linked to also has additional information that you will find useful, especially the part about placing the downloaded .iso image and .exe in the same folder.

Good luck!

---

