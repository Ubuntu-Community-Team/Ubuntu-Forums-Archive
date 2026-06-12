---
title: "Portable KeePassX on a USB drive"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by echo314 on 2009-03-30
I use KeePassX on my Ubuntu machine and am happy with it. Computers at my college labs use XP and Vista. I've done some searching, but could only find info on the last .0.2.something release, and I didn't understand any of it. Can I use my home comp to get a portable WIndows version of KeePassX on a jump drive?

---

### Post by card_ace on 2009-04-13
try [www.portableapps.com](www.portableapps.com)  There are all kinds of programs that have been modified to run off of USB drives.

---

### Post by kellemes on 2009-04-13
There are portable versions of keepass on there download page.
[http://keepass.info/download.html]("http://keepass.info/download.html")

---

### Post by bitchballs on 2009-10-03
> **kellemes said:**
> There are portable versions of keepass on there download page.
[http://keepass.info/download.html]("http://keepass.info/download.html")

There is a problem with this. 

1. Keepass is not KeepassX.  The two are separate projects and use different password databases.  There are workarounds, but having to work around the PAF suite defeats the purpose of having it in the first place.  Easier to just run KeepassX straight of the thumbdrive.  Which you can do, it has a windows version. 
 And 2. The portableapps suite doesn't support linux.  At all.  It is loaded with great apps and very nice overall, but totally useless if your goal is to be able to pop it into a linux or windows box and use the same apps the same way.  Kinda undermines the whole portability benefits.

I would suggest storing your keepassx file on the thumbdrive and just setting your desktop based kpx to use it.  The usb based kpx can do the same, thereby eliminating the platform issue, unless you want to use it on another non-windows box.  This way also preempts having to sync the databases.  Keep a backup somewhere tho.

---

### Post by mike555 on 2009-10-03
I use Keepassx on Ubuntu and Keepass on windows they share the same data from a thumbdrive , so the versions I have open the same .kdb  file ..........

---

### Post by bitchballs on 2009-10-03
> **mike555 said:**
> I use Keepassx on Ubuntu and Keepass on windows they share the same data from a thumbdrive , so the versions I have open the same .kdb  file ..........

KeepassX can use Keepass 1.x kdb files.  Keepass is currently beyond 2.x, but still supports saving in the 1.x format.  KeepassX kdbs cannot run under Keepass.  At least that is what the website says.

Anyway, I did some experimenting and the problem isn't what I thought..  You can extract the zip for the windows version of KeepassX onto your usb stick and place it into the portableapps directory.  It shows up in the portableapps menu, no further config required.  With this I have no idea why anyone would want to keep using Keepass.  Just use KeepassX.  It looks better.  Plus I always get a niggling from mixing the two.  Sooner or later the two projects are going to be too removed from eachother to support each others databases.  Actually they already are.  Keepass 2.x users already have to save/export kdb into the 1.x format to have them usable under KeepassX.  

The only draw back I see here is that I don't think you can use portableapps' update feature since KeepassX is not officially supported.  But if you plan to use keepassx on your linux desktop you can't really keep updating keepass in portablepps either, once they drop support for saving/exporting in the 1.x format you lose compatibility with KPX anyway.

---

### Post by mike555 on 2009-10-03
I use version 4.1 Keepassx on Ubuntu and portable Keepass 1.14 on Windows XP and they both open my .kdb file I keep on Dropbox .........




that should be version 1.16 ....

---

### Post by bitchballs on 2009-10-03
> **mike555 said:**
> I use version 4.1 Keepassx on Ubuntu and portable Keepass 1.14 on Windows XP and they both open my .kdb file I keep on Dropbox .........




that should be version 1.16 ....

Right.  Exactly as I said.  KeepassX supports Keepass 1.x .kdb files.

---

### Post by ninjapirate89 on 2009-10-03
The Portableapps suite works great under wine for me. Haven't specifically tried KeePass Portable for it but it's worth a try.

---

### Post by bitchballs on 2009-10-03
Yeah, I'm actually using it right now.  Some of my initial concerns have been alleviated in the research I did while making these posts.  It still bothers me to have to use wine at all though.  Also, I use totally different applications natively under KDE, and most of them don't mesh too well, if at all, with the portableapps I have setup.  Basically all portapps is doing for me is providing me a comfortable setup to carry around and use on campus computers.  Still a neat little suite of programs though.  It appears that one could use some simple tools and follow the standards provided on the portapps website and make your own portapps.  I'll have to look into this.

---

