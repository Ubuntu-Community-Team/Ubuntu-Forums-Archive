---
title: "Top apnel keeps getting hidden by Firefox"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by myolbug on 2009-05-07
I have Ubuntu 8.10 and the latest version of FF.  The thing that is happening is that when I open FF, it removes the top panel.  I have to hit F11 twice to get it back.  Once will put me in fullscreen and twice will restore it to normal size and then the top panel shows again.  I do have the top panel locked but it still happens.  The bottom panel is unaffected.

---

### Post by Didius Falco on 2009-05-07
Right-click the top panel, go into **Properties** and see if it is set to Autohide. If it is, uncheck that box.

Regards,

Didius

---

### Post by Elfy on 2009-05-07
There were some bugs

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276640](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276640)

This seems to have helped some people [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640/comments/7](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/276640/comments/7)

---

### Post by myolbug on 2009-05-07
Thanks for the link forestpixie, this fixed it; > 3. Switch from maximized to normal Window  This seems to have cleared it up.:guitar:

---

### Post by myolbug on 2009-05-07
It was still doing it.  I did however go into the properties of the top panel of Firefox and selected Restore to Default as I didn't have the Title bar and the minimize/restore X box on top, nor the bottom panel of Firefox.  The restore to default added these back, so I'll see if that is it.  I feel pretty good that this is the problem, we'll see.

---

### Post by Peter09 on 2009-05-07
In compiz-settings-manager go to the 'window management' section and enter the 'place windows' area. Make sure window placement is set to 'smart'

Edit - misread your problem - doubt whether this will help.

---

### Post by inearlygaveup on 2009-05-07
Thanks forestpixie it seems to have worked for me.=D>

---

### Post by myolbug on 2009-05-07
Thanks Peter, it is already set up that way, I do think that the restoring to default is the fix here!  I have been trying to duplicate the problem and I haven't been able to!

---

### Post by myolbug on 2009-05-07
Well I believe that this is totally fixed.  Maybe this should be a sticky, cause I have had this problem on multiple machines and others have had this issue as well.  I have had zero problems since!!!

Again, right click the top Firefox panel, then select Customize> Restore Default Set.  In Firefox 3.0.10 it is a button on the lower right hand side of the window.

---

### Post by myolbug on 2009-05-11
Hey I just thought that I would update you on this.  I noticed tonight that my browser had the same glitch look to it, so I hit F11 to full screen, then again to return it to normal and then R clicked the top bar with the file edit etc.  I chose customize and then restore to default.  Fixed it again.  I am not sure what is causing the glitch, maybe some full screen page on Facebook.  Either way, this is the fix for sure!!!

This really should be stickied!

Can someone please correct my spelling on the title?

Thx!

---

### Post by myolbug on 2009-05-11
I upgraded to 9.04 last night and I haven't had this happen.

---

