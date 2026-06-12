---
title: "Places Menu Items Try to Open Archive Manager"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Penguin Guy on 2010-06-13
Every time I clicked an item in the [COLOR="Green"]Places[/COLOR] menu, the computer tried to open it with the archive manager. I fixed this by removing the [FONT="Courier New"]indode/directory=[/FONT] line from my [FONT="Courier New"]~/.local/share/applications/mimeapps.list[/FONT] file.
```

[Added Associations]
x-content/audio-cdda=rhythmbox.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=f-spot-import.desktop;
x-content/software=nautilus-autorun-software.desktop;
application/pgp-keys=gedit.desktop;openoffice.org-writer.desktop;userapp-seahorse-URKECV.desktop;
application/x-extension-crx=chromium-browser.desktop;
application/x-extension-INF=nautilus-folder-handler.desktop;
video/x-theora+ogg=vlc.desktop;
video/ogg=vlc.desktop;
video/mpeg=vlc.desktop;
audio/mpeg=vlc.desktop;
[COLOR="Red"]inode/directory=file-roller.desktop;[/COLOR]

```
I just thought I'd post the solution here to help out anyone else with the same problem.

---

### Post by Handssolow on 2010-10-13
Many thanks.
There I am playing around with a new wifi card and downloaded a new driver, I open Places and get an error message from Archive Manager. Could not create Archive. Archive type not supported.
Earlier I couldn't open Synaptic and was asked to run "sudo dpkg --configure -a", which worked.

A sudo gedit in front of your line, a couple of ## to comment out the line and things are back to normal.

---

### Post by vakosel on 2010-11-21
That's great my friend ,thank you a lot !
:popcorn::p

---

### Post by lkanab on 2010-12-13
Thanks a lot!
I had it too.
any Idea why is this happening?

---

### Post by linhax on 2011-02-16
cheers mate this works something ubuntu devs should look into for a auto fix....

---

### Post by p014k on 2011-04-12
Thanks a lot!

---

### Post by barrydrake on 2011-04-21
I'm really grateful to you for posting this.  I hadn't a clue where to look for a solution, and the problem was really annoying.  Thanks!

---

