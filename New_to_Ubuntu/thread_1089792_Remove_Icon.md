---
title: "Remove Icon"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by bj218 on 2009-03-07
How can I remove icon's from the desktop?

---

### Post by simtaalo on 2009-03-07
delete them?

which icons in particular?

---

### Post by Dadsgé on 2009-03-07
icons on the desktop, you mean launchers?
do you want to delete the icon or the entire launcher?

---

### Post by starcannon on 2009-03-07
For Launcher/Link Icons, simply Right Click and Move to Trash.

For Icons that represent Drives/File Systems:

[LIST=1]
[*]Keycombo: ALT+F2
[*]Type: gconf-editor
[*]Navigate to: apps/nautilus/desktop
[*]Untick: volumes_visible
[*]Close gconf-editor
[/LIST]
That should do it.
GL

---

### Post by bj218 on 2009-03-12
> **Dadsgé said:**
> icons on the desktop, you mean launchers?
do you want to delete the icon or the entire launcher?
I currently have 2 items on the desktop one is for keepassx (my PW mgr.)
 and if I clk on it the program will launch. However the program is listed
 under accessories and I can launch it from there. The other icon is the
 database for my PW mgr. and I do not if it exist's any where else on the system?

---

### Post by bj218 on 2009-03-12
> **starcannon said:**
> For Launcher/Link Icons, simply Right Click and Move to Trash.

For Icons that represent Drives/File Systems:

[LIST=1]
[*]Keycombo: ALT+F2
[*]Type: gconf-editor
[*]Navigate to: apps/nautilus/desktop
[*]Untick: volumes_visible
[*]Close gconf-editor
[/LIST]
That should do it.
GL

I don't know what a Launcher/Link Icon is? Would a File System Icon Launch a program if you clk on it?

---

### Post by hostilejosh on 2009-03-12
a Launcher/Link icon is one that opens a program, a Driver/File System Icon would open the CD drive if you clicked it, a File System Icon would open a folder.

---

### Post by ENigma885 on 2009-03-12
As *hostilejosh* told u Launcher/Link is used to launch a program or an application. Those icons can be removed by deleting them as any usual file
Unlike other icons like the mounted volumes, Thrash icon, and Computer that cannot be removed the same way;

either to make wat *starcannon* suggested (in the 4th post) or
use [COLOR="Red"]Ubuntu Tweak[/COLOR] a small program provides some tweaks and other cool shortcuts u can download it from  [[COLOR="Red"]HERE[/COLOR]]("http://rsync.labby.co.uk/getdeb/ubuntu/hardy/ub/ubuntu-tweak_0.4.6-1~getdeb1_all.deb") and check the Desktop tab to control over the icons present on ur desktop 
it has also other helpful things try them =)

---

### Post by bj218 on 2009-03-12
> **hostilejosh said:**
> a Launcher/Link icon is one that opens a program, a Driver/File System Icon would open the CD drive if you clicked it, a File System Icon would open a folder.

It looks to me like I may have one of each!! If I clk on Keepassx it opens my PW Mgr. program and if I 2 clk on the Database.kdb Icon Firefox comes on and sys it a BIN file whatever that is? 
From what I have learned so far it looks like I can trash the Keepassx icon, but should
use the commands from post #4 (STARCANNON) For The Database.kdb Icon. If I do this where
will my Keepassx database be located I do not want to lose it?

---

