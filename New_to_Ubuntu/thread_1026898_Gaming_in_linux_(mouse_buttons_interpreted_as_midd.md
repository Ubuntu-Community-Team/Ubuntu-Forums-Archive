---
title: "Gaming in linux (mouse buttons interpreted as middle click)"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by getut on 2008-12-31
I've recently started playing some games in linux and I am a 3d shooter kind of gamer. I'm having trouble with how linux is interpreting a left and right click at the same time for use with say rocket jumping in Open Arena.

A rocket jump requires a left click (fire) and a right click (jump) if not at the same time, in very rapid succession. Linux is interpreting that as a middle click. How can I get it to stop? I need left and right click both interpreted as is.

I found in xorg.conf where emulate 3 button mouse is, but it is already disabled and I am still getting that behavior.

Please help me.

---

### Post by Tim Sharitt on 2008-12-31
Are you using intrepid? If so, I believe xorg.cong is ignored and hal is used. If that's the case, there is a tutorial or two for hal x config on the forums somewhere. Not sure if that helps, but it's all that comes to mind right now.

---

