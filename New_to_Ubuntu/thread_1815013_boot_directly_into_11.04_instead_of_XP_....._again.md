---
title: "boot directly into 11.04 instead of XP ..... again"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by nichos on 2011-07-30
Wthin XP I used "...Windows installer-ubuntu..." which gives Wubi to install Ubuntu 11.04, ie dual booting as described in 1st post.

Now that I managed, with your help ofcource, to use F.Fox, write letters, print wirelessly, network, use yutube & manage fotos in Linux (except for FSX I boot XP) I would like Linux priority in the 1st menu.

On booting I get the 1st menu below, XP? or Ubuntu?,
If I do nothing boots into XP, if I select Ubuntu I get the 2nd menu.

What shall I transpose so that I get in the 1st menu Ubuntu priority?. 

1st)

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

2nd)

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

---

### Post by raja.genupula on 2011-07-30
[http://ubuntuforums.org/showthread.php?t=820056](http://ubuntuforums.org/showthread.php?t=820056)

---

### Post by Mark Phelps on 2011-07-30
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=820056](http://ubuntuforums.org/showthread.php?t=820056)

What part of this being a Wubi install did you not see?

To the OP -- do NOT mess with GRUB.  Period.  You do NOT have GRUB; instead, you have GRUB4DOS -- which is quite different.

If you force the install of GRUB, you will hose up your system bigtime.

Since you are running Win7, the CORRECT way to fix this is to do the following:
1) Click the button at the lower-left of the destkop, and when the text box comes up, enter MSCONFIG and press Enter.
2) Select the Boot tab
3) Select the row you want in the top box and click the Set as default button.

When you next restart, the Ubuntu line will be highlighted in your OS menu, and that will be the default.

---

### Post by raja.genupula on 2011-08-01
@phelps thank you man .

---

