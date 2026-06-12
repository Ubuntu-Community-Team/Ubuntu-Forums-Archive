---
title: "Copy/Paste"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by donescamillo on 2010-04-24
Hi,

I open two gedit windows. From the first one I copy some text. I want to paste it in the second one. The paste operation works only if the first gedit window ( the one I am copying from) is open. As soon as I close it, I cant paste the text in the second, the entry in the right-click menu is grayed. Is this how it should work? Does not the copied text (or whatever it is) go in a clipboard like in Windows, or somewhere else from where it can be accessed later?

Regards, 
donescamillo

---

### Post by Talon2 on 2010-04-24
This is the bug I would like to see fixed more than any bug in Ubuntu.

For more information and to see that this bug has existed for years:

[https://bugs.launchpad.net/ubuntu/+bug/11334](https://bugs.launchpad.net/ubuntu/+bug/11334)

---

### Post by garvinrick4 on 2010-04-24
> **donescamillo said:**
> Hi,

I open two gedit windows. From the first one I copy some text. I want to paste it in the second one. The paste operation works only if the first gedit window ( the one I am copying from) is open. As soon as I close it, I cant paste the text in the second, the entry in the right-click menu is grayed. Is this how it should work? Does not the copied text (or whatever it is) go in a clipboard like in Windows, or somewhere else from where it can be accessed later?

Regards, 
donescamillo Try opening the window you want to paste and save to from the terminal Code:

gksudo gedit /etc/default/grub

In other words use gksudo (for Nautilus root) gedit (for type of editing package)
and last of all the file system route.
 If you do not want root powers just leave off the gksudo. If you just want to see in Terminal what a file looks like without opening a editor like gedit, CODE:

cat /etc/default/grub

---

### Post by 2hot6ft2 on 2010-04-24
[Install Parcellite by clicking this]("apt:parcellite")
Then open it in Applications > Accessories > Parcelleite
You can right click on it in the top right panel and set the options how you want them.

---

### Post by _0R10N on 2010-04-24
I don't see that as a bug. I think it's related to buffers maintenance. I also find this behavior a little annoying, but I get used to it.

_0R10N >>

---

### Post by takisan on 2010-04-24
Apparently another reason that I like windows (but still think Ubuntu and / or Debian is better.) The copy/paste works even after you close out of a window.

---

