---
title: "Panel Help"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Morphayne on 2010-06-11
I installed the latest version of Ubuntu today.  After installing OS updates I began to have trouble withe top panel after a reboot.
[IMG]http://i727.photobucket.com/albums/ww276/Meavy_Hetal/panelissue.png[/IMG]

As you can see at the top right, there are duplicate objects in the panel.  This is the default panel, I haven't made any of my own changes.  Is there any way to get the panel back to its original state?:confused:

Edit: I forgot to mention that I'm using the 64-bit version of Ubuntu.  Sorry.

---

### Post by cfhowlett on 2010-06-11
To reset the gnome panel to defaults, type this in a terminal: 

gconftool --recursive-unset /apps/panel && killall gnome-panel

You'll have the opportunity to rebuild your panel exactly as you wish after that.

---

### Post by Morphayne on 2010-06-11
> **charlesh1609 said:**
> To reset the gnome panel to defaults, type this in a terminal: 

gconftool --recursive-unset /apps/panel && killall gnome-panel

You'll have the opportunity to rebuild your panel exactly as you wish after that.

Thanks for your suggestion.  It did help to reset the panel, but once I  do a restart the issue returns.  
Help?:oops:

---

