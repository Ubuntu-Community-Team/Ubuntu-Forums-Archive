---
title: "Panic Time..."
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Weighty Ghost on 2011-01-19
Hey Everyone,

Very sorry, but Windows has "auto-updated" my main biz cpu into uselessness (needs to be rebooted every 10mins to stay connected to the internet).
I'm in hella trouble now because I've got a lot of work to do and 8am tomorrow is only 12hrs away.

I'm not necessarily new to Ubuntu, but its been long enough since I last used it that I have to re-read all of the install tutorials from scratch (*stress*).

I'll definitely have some q's as I go, but I thought rather than spam the board with my frantic situation I'd just keep my crisis in one thread.

I know how the search button works, and I'll be reading as fast as I can. I'll post whatever probs I have below. If anyone can help as I go please feel welcome to reply.

Sorry about this,

---

### Post by Weighty Ghost on 2011-01-19
Ok here I go,
 
Nothing on the netbook/get-ubuntu page not pertaining to a CD or usb install.

I've got the ISO open and seeing wubi.exe Is this the one? 
It lets me choose the size of my install so I'm assuming it will handle the partitioning on its own?

---

### Post by Bucky Ball on 2011-01-19
Welcome.

Hold on. Are you installing from USB or CD? Don't go for Wubi as that installs inside Windows and Windows is broken.

Download 10.04 LTS and install but you need some free space (or an unwanted partition) to do it. You can run Ubuntu off the disk (or USB), it all depends what it is you want to do. Running from disk you can get online with a cable, wireless would be more problematic.

---

### Post by DOSIX on 2011-01-19
just download the iso from the website under netbook. once you have the iso, use the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to make the flashdrive bootable. then it's just a matter of selecting the bootmenu when you reboot your computer and selecting to boot off of usb.

---

### Post by Weighty Ghost on 2011-01-19
the /desktop/get-ubuntu page says yes this is the install executable.

Is it going to try and re-download all of the source files? or does it know to get them from the disc image?

[edit] sorry guys, did'nt see your replies before i hit "post"

---

### Post by Weighty Ghost on 2011-01-19
[edit] sorry guys, did'nt see your replies before i hit "post"

...gimme a sec to read them,

---

### Post by Weighty Ghost on 2011-01-19
> **Bucky Ball said:**
> Welcome.

Hold on. Are you installing from USB or CD? Don't go for Wubi as that installs inside Windows and Windows is broken.

Download 10.04 LTS and install but you need some free space (or an unwanted partition) to do it. You can run Ubuntu off the disk (or USB), it all depends what it is you want to do. Running from disk you can get online with a cable, wireless would be more problematic.

My acer doesn't have a rom drive, and my usb stick has zero storage space (internet only). I wanted to open iso buster and install it out of the disc image.

I understand vista comes w/ a partition utility. I'll google it and get some space reserved to install.

Thanks,

---

### Post by Weighty Ghost on 2011-01-19
> **DOSIX said:**
> just download the iso from the website under netbook. once you have the iso, use the [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to make the flashdrive bootable. then it's just a matter of selecting the bootmenu when you reboot your computer and selecting to boot off of usb.

My bad, I thought the netbook version was a light-weight version of desktop.

I'll download the correct version as per Bucky's advice.
Thanks for the help

---

### Post by Weighty Ghost on 2011-01-19
Oh man, might as well just shoot myself now and be done.
47min d/l...

Before I start messing w/ vista, does "ubuntu-10.10desktop-i...iso"
come w/ a partition utility?

[edit] looks like during the install, I can simply choose whether I'd like to Install Ubuntu alongside vista, and how much space to allocate to it. Does Ubuntu handle all of the partitioning on its own?

---

### Post by audiomick on 2011-01-19
Yep. When you boot into the Live environment, i.e. choose "try ubuntu without changing" or whatever the wording is, there is a thing in System> Administration> 
called Gparted. It is a partitioning tool. 

I should mention here having read that one should use windows partitioning tools to work on windows partitions, and that one should do backups before one does any partitioning work with any tools on any system.

If you change the windows partition, start windows at least once and let it run its' disk check thing it it wants to.

---

### Post by Weighty Ghost on 2011-01-19
> **audiomick said:**
> Yep. When you boot into the Live environment, i.e. choose "try ubuntu without changing" or whatever the wording is, there is a thing in System> Administration> 
called Gparted. It is a partitioning tool. 

I should mention here having read that one should use windows partitioning tools to work on windows partitions, and that one should do backups before one does any partitioning work with any tools on any system.

If you change the windows partition, start windows at least once and let it run its' disk check thing it it wants to.

Thanks,

But i don't think I can do the live thing from an iso file, can I (i don't have a rom drive)?
I have to download to my HP notebook, than upload via shared downloads to my Acer notebook (this is going to take all night).

And yeah, I know this is a bad idea to just dive in w/o doing any backups. 
My os is effectively dead already since it wont let me restore to before it bricked my machine. If I end up having to reinstall vista or buy a new computer tomorrow morning, than thats how it is. 

<rant>Even my telephone can go online, but windows cant. Therefore its not a business machine. The only reason I keep is for quickbooks</rant>

---

### Post by audiomick on 2011-01-19
Ok, just went over the last few posts again. It seems you have a way of getting the installer to run without having made a USB stick or burning a CD. Didn't know that was possible, but anyway...

Yes, the installer has a partitioning tool
Yes, if you choose "install alongside" the installer will shrink your Vista partition and put Ubuntu into it's own partition next to it.

If, during the install at the appropriate moment, you choose the "manual" option, you can manually do the partitioning bit that the installer would otherwise do autimagically. Then you can determine exactly how big a partition Ubuntu gets. I don't know if this is possible otherwise. I haven't done an install without manually partitioning for too long.

Don't be worried about going through the installer just to have a look at what it does. It doesn't do anything final without telling you about it. If you bail out when face with the "this is irreversible" warning, nothing will have been changed on your computer.

---

### Post by Weighty Ghost on 2011-01-19
Cheers Mick,

I'll let you know how it goes.
Thanks,

---

### Post by Bucky Ball on 2011-01-19
I would advise 10.04 LTS. 10.10 has a few issues right now. ;)

---

### Post by victorhugo289 on 2011-01-19
He doesn't have a CD ROM drive. He's somehow trying to install Ubuntu from USB. Ubuntu 10.10 is better because it comes with codecs and works very nice from the beginning. It does have some issues but you find them over time, not immediately.

---

### Post by Bucky Ball on 2011-01-19
> **victorhugo289 said:**
> He doesn't have a CD ROM drive. He's  somehow trying to install Ubuntu from USB. Ubuntu 10.10 is better  because it comes with codecs and works very nice from the beginning. It  does have some issues but you find them over time, not  immediately.

The issue of killing Broadcom wireless configuration or the faulty  installer wiping Windows when you try a side-by-side install, among  other things, you will find immediately.

The kernel in question is 2.6.35-24. Before you begin to tell me how  wonderfully it is working for you (I am using the same kernel without  issue) these issues don't affect all hardware configurations. The faulty  installer does when side-by-side is attempted.

New user in a hurry probably doesn't want to spend hours tweaking with  an unfamiliar operating system. 10.04 LTS would possibly give a smoother  ride in this situation (not to mention MUCH longer support). ;)

---

### Post by HermanAB on 2011-01-20
Hold the horses!

First backup your data!!!

You don't have a CD in the netbook, so you need to make a bootable USB stick instead.  This is easy with the RPM distros, but tricky with the Debian distros.

If you use OpenSuse or Fedora, then you can simply copy the ISO to a USB memory stick, using Data Definition, then use that to boot the netbook and copy your data off to another memory stick and then reboot and install it.

Get OpenSuse or Fedora from [http://mirrors.kernel.org](http://mirrors.kernel.org)

If the PC has only ONE disk drive:
# dd if=susefile.iso of=/dev/sdb

La voila.

---

### Post by mastablasta on 2011-01-20
while with Ubuntu you can use Unebooting or Linux Live USB creator [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/).
 
if you just need it for work, you can stick USB inside, run it live (try out the system), do the work. and then later after you do everyhting oyu have to do take some time to install the system. i too would advise to use 10.04. you can always upgrade later if necessary.

---

### Post by Weighty Ghost on 2011-01-20
Thanks Guys,

For all the helpful replies.
Seems you can't install from the ISO anymore as wubi.exe needs a torrent file from the web. The best I can get is 5mins 30secs away from a complete download before vista corrupts my internet connection. After reboot Ubuntu installer needs to uninstall before it can try again.
Panic time is over, It's a non-starter, I'm ****'ed.

To be clear, I do not have a usb storage device on hand. I needed to install from cd rom. But not having a rom drive i usually rip discs with iso buster and just transfer the raw files to my Acer netbook. 
The only executable on the disc is wubi.exe, but it needs the internet connection I don't have to work (i thought the install files would be on the disk, but I guess its a boot-disk only).

I'll have to do a clean Vista install.

Thanks so much for the help everyone. I'll get Ubuntu running after Vista and Quickbooks are restored, but I'm sure from here the mods would appreciate it if I used the proper sub-forums, as it really wont be an emergency situation at that point.

Patience and help appreciated.
G'night everyone,

---

### Post by audiomick on 2011-01-20
I meant to say earlier: My escape from Quickbooks was GnuCash. You might like to have a look at that.

---

