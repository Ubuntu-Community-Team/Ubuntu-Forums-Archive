---
title: "Ubuntu clipboard"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by newport_j on 2010-03-09
How does one use the Ubuntu/Linux clipboard. I copied something to it on gnuplot, and I now want to access it. How do I do it?

newport_j

---

### Post by undecim on 2010-03-09
Right-click and choose paste where you want to paste it, or just press Ctrl+V where you want to paste it.

There is also glipper, which can manager the clipboard for you (clipboard history, etc)

EDIT: Also, if you want to use hotkeys when pasting to or from the terminal, you need to use shift (Ctrl+Shift+C, Ctl+Shift+V)

---

### Post by rewyllys on 2010-03-09
> **undecim said:**
> . . . .There is also glipper, which can manager the clipboard for you (clipboard history, etc). . . .

As a user of GNOME in Karmic, I'd like to have access to at least the last ten or so items I put in the clipboard, so your mention of glipper interests me.  Unfortunately, in Karmic neither the Synaptic Package Manager nor the Ubuntu Software Center offers glipper.  SPM does offer klipper, which I understand is the KDE clipboard manager.  

Do you happen to know whether klipper would work in GNOME, or whether there is some other clipboard manager available for GNOME?

---

### Post by undecim on 2010-03-09
@rewyllys: Glipper is in the universe repositories, which need to be enabled (System -> Administration -> Software Sources)

I wouldn't recommend using klipper with gnome, as that would likely load many libraries from KDE. It may or may not work though... you'll just have to try it.

---

### Post by rewyllys on 2010-03-09
> **undecim said:**
> @rewyllys: Glipper is in the universe repositories, which need to be enabled (System -> Administration -> Software Sources). . . .

Thanks, undecim.  I'd have sworn I'd already added the universe repositories to SPM, but in fact I hadn't.  That's now corrected, and glipper has been installed.:popcorn:

---

### Post by ankspo71 on 2010-03-09
Hi,
I think Parcellite is a very nice clipboard manager. I'm using this because some of the things I wanted to paste wouldn't retain in the clipboard after closing the applications I was copying from. It also keeps things in the clipboard after a reboot.
Hope this helps.

---

### Post by undecim on 2010-03-10
> **ankspo71 said:**
> Hi,
I think Parcellite is a very nice clipboard manager. I'm using this because some of the things I wanted to paste wouldn't retain in the clipboard after closing the applications I was copying from. It also keeps things in the clipboard after a reboot.
Hope this helps.

Wow, parcellite is pretty nice. Thanks, ankspo71

---

### Post by antiplex on 2011-01-30
i just stumbled over this thread sometime ago while looking for a way to configure a custom keyboard shortcut for parcellite to use **<Windowskey> + 'v'** as history shortcut instead of the default **<Ctrl> + <Alt> + 'v'**.

i also really like parcellite altough i miss some features:
- command to directly insert/paste something (number X) from the history instead of 'just' selecting what should be in the clipboard.
- static entries (things you constantly type).
- insert current timestamps in a self-defined format (e.g. '%YY-%mm-%dd').

considering parcellite is rather young i am confident there might be chances for features like the ones mentioned to be added.

since one has to type the shortcuts one needs to know what would be the match for the windows-key in ubuntu.

i just managed to find out that entering **<Mod4>V** as a hotkey-entry for the history key combination maps the history to my desired key-combination.

regards, anti

---

