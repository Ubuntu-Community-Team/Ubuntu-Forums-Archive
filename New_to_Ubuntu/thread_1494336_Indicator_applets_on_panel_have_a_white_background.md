---
title: "Indicator applets on panel have a white background after enabling LiNsta, Help? ^^,"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by iMattcotv on 2010-05-26
I have 2 issues actually lol :P

1. The indicator applets havent changed the background color like the rest of the things on the panel after installing and enabling LiNsta.. What happened?
Heres a pic:
[img]http://img200.imageshack.us/img200/4429/bar1q.png[/img]

Also to note, see that grey line on the very bottom? well that panels height is set to 24, and at one point there was no grey line like you see.. I know its because the height is more than what the image height is, so it vertically repeats.. but heres the problem.. Im pretty sure the image height is 24, but even if I set the panel height to 21 the grey line still doesnt go away..

Is there anyway to fix this?

---

### Post by Ozymandias_117 on 2010-05-26
You could try right clicking on the panel, properties, background. Select Background Image: and navigate to ~/.themes/LiNsta/gtk-2.0/Panel/ and see if there is a file panel-bg.png. Most themes will put one there, but they don't get auto-applied.

---

