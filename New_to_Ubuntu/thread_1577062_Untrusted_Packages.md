---
title: "Untrusted Packages"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-09-18
Hi forum! I'm trying to install Lyx from Software Center and I'm getting this error
> The action would require the installation of packages from not authenticated sources.
And in details it shows some packages
> dvipng lacheck latex-beamer latex-xcolor libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libboost-regex1.40.0 libboost-signals1.40.0 libt1-5 lmodern luatex lyx lyx-common pgf preview-latex-style prosper ps2eps psutils tex-common texlive-base texlive-binaries texlive-common texlive-doc-base texlive-extra-utils texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc texlive-generic-recommended texlive-latex-base texlive-latex-base-doc texlive-latex-extra texlive-latex-extra-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pictures texlive-pictures-doc texlive-pstricks texlive-pstricks-doc tipa ttf-lyx
Here is a [[COLOR="Purple"]screenshot[/COLOR]]("http://tinypic.com/r/2r5rhqt/7") of the error. And it just don't let me install it...
Any idea what causing it?

---

### Post by Christian Knudsen on 2010-09-18
This is the first hit that shows up when googling that error message:

[http://ubuntuforums.org/showthread.php?t=1327907](http://ubuntuforums.org/showthread.php?t=1327907)

> My steps were:
System>Administration>Software Sources
I had "Proprietary Drivers" and "Software Restricted by copyright or legal issues" checked.
I unchecked the two of these. I then went to the Authentication tab. I clicked "restore defaults", although nothing changed.
I closed the window, and tried the Software manager again.
Worked like a charm. Don't know how the settings were changed in the first place, but whatever.

Have you tried this?

---

### Post by abs_kkk on 2010-09-18
update then try installing lynx again
go to update manager via System>Administration>Update manager.
Click on check and then select all then click on install updates.

---

### Post by nick_goodfate on 2010-09-18
> **Christian Knudsen said:**
> This is the first hit that shows up when googling that error message:

[http://ubuntuforums.org/showthread.php?t=1327907](http://ubuntuforums.org/showthread.php?t=1327907)

Have you tried this?

Yes it worked, i'm sorry for that...

---

### Post by Christian Knudsen on 2010-09-18
No worries. I'm just glad I could help. :)

---

