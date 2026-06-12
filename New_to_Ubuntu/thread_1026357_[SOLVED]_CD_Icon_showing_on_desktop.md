---
title: "[SOLVED] CD Icon showing on desktop"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Dumbestcrayon on 2008-12-31
When I insert a CD into my drive I would like it to NOT show up on my desktop. I don't like a bunch of mess on my desktop. I would rather just have it in Places where it is anyways.

Is there a way to stop it from displaying on the desktop when I insert a cd?

---

### Post by eBoxNet on 2008-12-31
1. open terminal and type in “gconf-editor” and hit enter.

2. on the screen that pops up, look for a key called “apps” (this will be the first item on the left). Click on this item to expand it.

3. look for a key called “nautilus”, click on “nautilus” to expand it. click on the key called “desktop”.

4. on the right hand side of this window look for an entry called volumes_visible, uncheck this item and you are done.

Here is a screen shot of what the above procedure looks like

[IMG]http://liltux.files.wordpress.com/2007/05/screenshot.png?w=384&h=252[/IMG]

source : [http://liltux.wordpress.com/2007/05/22/disabling-drive-mount-icons-on-the-ubuntu-desktop/](http://liltux.wordpress.com/2007/05/22/disabling-drive-mount-icons-on-the-ubuntu-desktop/)

---

### Post by fooman on 2008-12-31
you can stop *all* mounted volumes from appearing on the desktop with the configuration editor....not sure if there is a way to stop *only* the cd drive.

go to applications > accessories > system tools > configuration editor.

in the editor,  go to apps > nautilus > desktop

in the right side...uncheck "volumes visible"

that should do it.

edit: wow...i type way too slow.

---

### Post by Dumbestcrayon on 2008-12-31
Thank you very much. I knew it could be done and it was something simple.

---

### Post by eBoxNet on 2008-12-31
You are more than welcome,pls mark as SOLVED.

---

