---
title: "Ubuntu startup problem"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by zxy on 2009-03-29
Ok so I have tried repairing my windows vista with my restore cd and also removed wubi and anything related to ubuntu on add/remove programs... but this is still here.

[IMG]http://i8.photobucket.com/albums/a9/mppaki/P3230211.jpg[/IMG]

How do i get rid of the ubuntu option?

I want to still use ubuntu but I burned the cd and installed it wrong.

---

### Post by zxy on 2009-03-29
can anyone help me please? bump >.>

---

### Post by RedSingularity on 2009-03-29
You can reinstall the windows MBR with the windows CD.

---

### Post by jimv on 2009-03-29
I don't know the exact line to delete, but it's in your C:/boot.ini file.  That's what populates those entries in that menu.  If you can't get it fixed, you can run the command "fixboot" from Windows recovery console and that will create a brand spankin' new boot.ini file.

---

### Post by zxy on 2009-03-29
Ok so when I repair it brings back files of ubuntu but the wubi and program aren't installed.

And when i try to run fixboot it goes to the run and it has a run x:\ recovery something \:

and i type fixboot but nothing happens...

i tried doing fixboot in run from vista normal startup but it says not found.

---

