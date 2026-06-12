---
title: "How do I get bluetooth working w/ T610 (Feisty)"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by se2131 on 2007-04-27
I had this working at one point in Edgy, but I'm not sure how I got it to work, and then it stopped after that one time (I'm not sure why though)

I have a Sony Ericcson T610 phone, and a DBT-120 bluetooth adapter.  When I do hcitool scan, I see my cell phone address just fine:

```
00:0A:D9:83:C2:1F       T610
```

But when I run kbluetoothd, I can't seem to get into the actual program.  What I mean is, I see the icon come up in the top right of my screen.  However, I can only go into the right-click menu options (Open-recent, configuration, help, etc).  I distinctly remember there being a GUI available which sort of allowed me to browse what was on my computer and what was on the cell phone, but that seems to have completely disappeared.

I also can't use gnome-obex-send or anything to transfer files.

Any ideas?

---

### Post by se2131 on 2007-04-28
bump

---

### Post by se2131 on 2007-04-29
bump again

---

### Post by Roner on 2007-04-29
Make sure you install all of gnome's bluetooth components (especially gnome-bluetooth and bluetooth manager). The gnome bluetooth applications are far better than they used to be, and they are taking over the connection and pairing mechanisms - no longer bluepin, kbluepin or bluez-pin.

---

