---
title: "Lucid Lynx update failed - grub&gt;"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by joannkatana on 2010-05-31
Hi -

I'm very new to the forum and very computer-uninformed.  I have an old AMD computer that is running Windows XP that hypatia helped load ubuntu (er, I think a version 9) onto last year. I did one one version upgrade that went well, and then I tried to upload Lucid Lynx, and now I get only the following:

GRUB4DOS 0.4.4 2009-04-20, Memory: 639K / 990M, MenuEnd: 0x43426 [ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ESC at any time exits. ]

grub>_

-I found a few threads that may be applicable, but my computer inexperience is pretty bad, so I'm hesitant to just do it, since I'm not sure it's correct -

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) - I'm assuming since I can run Windows XP still, and I think it got installed via a virtual CD mount(?) that I'm a Wubi user, and therefore this potential problem would apply to me?

and this: 

[http://ubuntuforums.org/showpost.php?p=9235797&postcount=16](http://ubuntuforums.org/showpost.php?p=9235797&postcount=16) because maybe the main log-in screen is the splash screen?

so, er.  Help?

---

### Post by bcbc on 2010-05-31
From what you described it sounds like you've been running wubi since version 9.04. Therefore the fix for wubildr probably does not apply to you.

Having said that, I'm not sure what your problem is. Perhaps it's because 9.04 used grub legacy and you might have switched to grub2 during the upgrade (that's a wild stab in the dark).

First thing I'd do is backup the file c:\ubuntu\disks\root.disk 
This contains all your ubuntu files and data and it will be large (5GB or more) so perhaps copy to an external drive.

If you have an ubuntu cd you could boot from it in live mode ('try without changes') and run some diagnostics. e.g. [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results back here.

Or you can try the following [link]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") (not the fsck part)

---

