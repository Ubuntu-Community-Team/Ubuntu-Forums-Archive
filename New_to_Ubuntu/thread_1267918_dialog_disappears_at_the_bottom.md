---
title: "dialog disappears at the bottom"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by lanzcc on 2009-09-16
Greets,
 
Running 9.04 via virtualBox in Windows XT on a Dell Inspiron.
 
I went to one of the file manager dialog boxes, but the tab I need was below the cutoff
at the bottom of the Ubuntu window.
 
So I thought I was clever, and went to change the screen resolution (this fixes similar
problems in Windows)
 
But I was in fact stupid, because I changed the resolution to the only other available setting (which was a lower res)
 
This made the problem so pervasive that I can no longer even access the tabs on the display dialog box that would allow me to return to the original resolution. The Display Preferences dialog is cut off right below the "Panel icon" in boldface at the left.
 
How Can I Change The Screen Resolution If I Can't Access The Tabs? Command line, maybe?
 
I have tries restart in recovery mode, using the ifix option to try to autofix graphics problems. No Luck, no change
 
HELP
 
[EMAIL="lanzcc@potsdam.edu"]lanzcc@potsdam.edu[/EMAIL]

---

### Post by tomBorgia on 2009-09-16
Alt-A will press the apply button for you...

---

### Post by lanzcc on 2009-09-16
Yes, I figured that out, but is there no way to see what&#347; at the bottom of other dialogs that go too low, where I don know in advance what keys are there?

---

### Post by tomBorgia on 2009-09-17
Ok... you'll need to reconfigure the Xserver...

Log off and press ```
<ctrl><alt><F1>
``` this take you to a terminal...

Log in and kill the xserver ```
sudo killall gdm
``` (I think)

Reconfig X -

```
sudo dpkg-reconfigure -phigh xserver-xorg
``` - Follow the onscreen instructions.

Restart X -

```
sudo gdm
``` - The graphical login screen should come back up.

Hope this helps.

---

