---
title: "Disabling middle-click paste"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ikajaste on 2009-01-06
Hi!

Is there a simple way to disable the middle mouse button paste action?

I understand many linux users seem to prefer the middle click as paste, but I really dislike it. It's quite manageable when the clipboard contains a few character snippet... but I really don't want a large amount of text, especially with newlines, to be pasted to the shell window by accident. I also want to keep the mouse as a navigation, selection and manipulation device, and pasting is a typing equivalent action for me, so it really feels wrong as a direct mouse action.

I did find some references to editing xorg.conf ([1](http://ubuntuforums.org/archive/index.php/t-430006.html), [2](http://ubuntuforums.org/showthread.php?t=830773&highlight=disable+middle+click+paste), [3](http://ubuntuforums.org/showthread.php?t=59730&highlight=disable+middle+click+paste)). Are these really a good way of doing this - seems a bit fidgety to me?

If editing xorg.conf is really the way to do this, would this be something that one could write an [Ubuntu Community](https://help.ubuntu.com/community) page about? How would I go about that - is it ok to just go and write a page, or should I discuss it first somewhere?

---

### Post by stanz on 2009-01-10
Configuration Editor?

;)

---

### Post by ghostis on 2009-01-15
IHMO, that we are even asking this question is a bug in Xorg.  It seems silly that we can configure nearly everything in the Ubuntu GUI, except what actions the mouse takes on an arbitrary button click.  Does anyone know a way to assign arbitrary actions to any hardware event in Xorg?  Can the new HAL infrastructure do it?

My .02,

-Ghostis

---

### Post by ghostis on 2009-01-15
BTW

[*This post*]("http://tomcat.ranta.info/2008/11/30/howto-disable-middle-button-click-when-pressing-left-and-right-mouse-button-in-xorg-74/") implies a method to remap the middle button with the new HAL-configured Xorg.  The settings one would put in the file would be different than the one he uses to disable emulation of 3 buttons, though.

I haven't tried it yet.

---

