---
title: "simple question regarding installation of gparted live"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by razaz03 on 2010-05-19
Hello all,

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto) states:

To make your USB flash drive bootable, first change the working dir, e.g. "cd /media/usb/utils/linux", then run "bash makeboot.sh /dev/sdd1" (replace /dev/sdd1 as your USB flash drive device name), and follow the prompts to finish that.

I'm not sure why but I get a command not found error here. My USB is labeled sdc1 under /dev, and is called 4792-C0DA in the /media folder.

Can someone tell me the exact command needed here and which directory to navigate to when executing it please? (tried replacing to sdc1 in the shell with no joy)

Also and just to clarify, am I right in assuming sdc1 is it's block file name, and 479... is the name of the actual USB?

Apologies in advance for it's simplicity, I'm new to Ubuntu but I'm here to stay, hence my need for gparted live lol.

Regards,

razaz03

---

### Post by -humanaut- on 2010-05-20
Are you trying to install Gparted as an O.S. on a USB pendrive? I don't entirely understand what your trying to do but you can use the Ubuntu Usb Startup disk creator and create a bootable Ubuntu system on that and use that as a Rescue system so to speak if thats what your intend is with Gparted?

---

### Post by candtalan on 2010-05-20
gparted will not work as a live item on its own, it will need to be within an operating system. As suggested by -humanaut- the ubuntu startup disc (usb stick) can create a Ubuntu bootable usb stick which will contain gparted.
FWIW I frequently make use of parted magic live CD (or usb) which itself I think uses gparted.
[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

---

### Post by -humanaut- on 2010-05-20
> **candtalan said:**
> gparted will not work as a live item on its own, it will need to be within an operating system. As suggested by -humanaut- the ubuntu startup disc (usb stick) can create a Ubuntu bootable usb stick which will contain gparted.
FWIW I frequently make use of parted magic live CD (or usb) which itself I think uses gparted.
[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

Parted Magic does use Gparted Do they have USB .imgs yet? seems like it would be easier to create a rescue CD instead; I still think the easiest way to obtain an Ubuntu rescue Usb pendrive is to put Ubuntu directly on the pendrive can't really go wrong there.

---

### Post by -kg- on 2010-05-20
[LIST=1]
[/LIST]

If you want a bootable USB disk with GPartEd (if that's all you want it for) you might try [UNetBootin]("http://unetbootin.sourceforge.net/").  With it you can create virtually any distro or "toolset" (such as GPartEd) that you care to.

I don't know how encryption would be handled by UNetBootIn (the point of the Community Documentation page you linked to), but it will at least create the bootable USB disk.

---

