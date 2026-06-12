---
title: "upgrading programs in intrepid"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by shaggorama on 2008-12-21
I'm currently running opera 9.62 and open office 2.4 in intrepid. I want to upgrade to opera 9.63 and open office 3.0. I'm fairly certain that there is aa feature built in here somewhere that will allow me to upgrade my software without manually uninstalling and replacing my existing software with the newer packages.

I've poked around in synaptic and update manager and haven't found anything to work with. Could anyone point me in the right direction? I'm still getting the hang of this

---

### Post by jbrown96 on 2008-12-21
Unfortunately, Opera doesn't appear to be in the repositories. They do provide .deb packages, which makes it a lot easier. Go to this page [http://www.opera.com/download/index.dml?platform=linux]("http://www.opera.com/download/index.dml?platform=linux") I don't know about opera, but in Firefox, when you download a .deb it offers to install the package if you "open" instead of saving. If this option is not provided, open a terminal, and do ```
sudo dpkg -i PACKAGENAME
``` You need to change PACKAGENAME to the name of the package along with its location.

---

### Post by jimmy the saint on 2008-12-21
I insalled open office 3 by going to the open office website and downloading the english .deb file from here:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)
save it to your desktop then double click.  It will install automagically.

I would not recommend it though.  The only "new" feature is intergrated support for office 2007 files, but there are ways to open them in 2.4 from what I understand.  OpenOffice3 is buggy on Ubuntu.  The window decorations are corrupted and occasionally there are glithces that frag a document that I am working on.  I downgraded back to 2.4.
I don't know about opera.

---

### Post by shaggorama on 2008-12-21
one of my problem with my office package is that i don't seem to have all of the applications. Really, I can only find writer, calc, draw, impress, and math. I also can't find a global application launcher for office, i need to laucnh em individually.

I've heard that 3.0 is buggy, but I'm kidna frustrated with what I've got. Any ideas on how I could find/download the missing pieces?

---

