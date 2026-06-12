---
title: "Fresh install, no sound"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Vschiffy on 2010-06-06
Hello, I just finished installing Ubuntu and am unable to get my sound to work.

So I figured I just needed to install the sound driver for my Creative x-fi Platinum... However, when I go  to download the driver, instead of getting a nice little .exe like in Windows, I get a folder filled with files that I don't have any idea what to do with. 

This folder does have a readme file with instructions but these instructions are not comprehensive enough for a new Ubuntu user such as myself.

Help?

The attached picture is a screen shot of the folder I downloaded, plus the open readme file.

---

### Post by an0dos on 2010-06-06
I think that beginning with Ubuntu 9.10 they started supporting Creative x-fi out of the box. 
Click on Applications-->Accessories-->Terminal to start up the terminal application then type in "alsamixer" and press enter.

Post a screenshot of it here.

You may want to check out this forum thread: [http://ubuntuforums.org/showthread.php?t=870001&page=62](http://ubuntuforums.org/showthread.php?t=870001&page=62)

---

### Post by Vschiffy on 2010-06-06
> **an0dos said:**
> I think that beginning with Ubuntu 9.10 they started supporting Creative x-fi out of the box. 
Click on Applications-->Accessories-->Terminal to start up the terminal application then type in "alsamixer" and press enter.

Post a screenshot of it here.

You may want to check out this forum thread: [http://ubuntuforums.org/showthread.php?t=870001&page=62](http://ubuntuforums.org/showthread.php?t=870001&page=62)


Thank you! I ran that command and saw that my integrated sound card was selected, so I hit F6 and selected my Creative sound card and now my sound works just fine. :)

---

