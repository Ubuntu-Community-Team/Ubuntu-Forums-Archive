---
title: "my panel has disappeared"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by ricardopresto on 2009-09-28
Help! My panel has disappeared and I don't know how to get it back!

---

### Post by j.bell730 on 2009-09-28
Right click an existing panel and click "New Panel".
Right click the new panel and select **Properties**, in the **Orientation** dropdown, select the side of the screen that it belongs on.

---

### Post by SPARTAN-118 on 2009-09-28
Hmm.... what do you mean, "disappeared"?

Do you mean it just vanished, with no trace, or did you perhaps change a setting that you didn't know what it would do...?

Perhaps it's just invisible; try right-clicking on all four corners of your desktop, and try switching to any other desktops you may have (ex: Desktop 2, 3, or 4) by scrolling on a blank area on the Desktop, or pressing Ctrl+Alt+left/right (or by pressing and holding Ctrl+Alt+down and switching that way).

---

### Post by ricardopresto on 2009-09-28
Thanks for the advice. Tried right-clicking everywhere - nothing. Tried switching desktops - nothing. Tried re-booting - same problem. Do you have any other ideas?

---

### Post by oboedad55 on 2009-09-28
> **ricardopresto said:**
> Thanks for the advice. Tried right-clicking everywhere - nothing. Tried switching desktops - nothing. Tried re-booting - same problem. Do you have any other ideas?

You can use this script. It will restore your panels back to like a new isntall, so any customization you had will need to be redone. This has bailed me out when I did seomthing foolish.

mv $HOME/.gconf/apps/panel $HOME/.gconf/apps/panel-old 
sudo /etc/init.d/dbus restart

---

### Post by fooman on 2009-09-28
try pressing the alt-f2 keys and see if it brings up a run dialog box...if it does, type the following into it and then click "run":

```
gnome-panel &
```

see if that brings it back.

---

### Post by humphreybc on 2009-09-28
Try "killall gnome-panel"

---

### Post by SPARTAN-118 on 2009-09-28
> **humphreybc said:**
> Try "killall gnome-panel"

and then restart gnome-panel.

---

### Post by humphreybc on 2009-09-28
In theory, killall should restart the panel on its own, but try restart anyway and see what happens.

If it doesn't restart, i'm guessing there is something wrong with the gnome-panel application. Try this as a last resort:

```

sudo apt-get remove --purge gnome-panel
sudo apt-get install gnome-panel ubuntu-desktop

```

(ubuntu-desktop because I think gnome-panel depends on it).

That should re-install the packages, hopefully fixing your problem... now, gotta run, my toasties are burning!

EDIT: I just realised you are using Ubuntu Netbook Remix, not Ubuntu.... so it won't be "ubuntu-desktop", it'll be "ubuntu-netbook-remix" I THINK.

Could someone please clarify? I know nothing about UNR.

---

### Post by ricardopresto on 2009-09-29
Thanks for all the advice everyone. Everything back to normal! :P

---

