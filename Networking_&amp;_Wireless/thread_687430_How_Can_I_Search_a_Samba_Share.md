---
title: "How Can I Search a Samba Share?"
date: 2008-02-04
forum: Networking &amp; Wireless
---

### Post by ReverendJ1 on 2008-02-04
Sorry if this has been answered before, but I couldn't find any relevant posts. My problem is I am connecting to an XP box via Samba, but cannot for the life of me figure out how to run a search on it from my Ubuntu box. I connected to the Samba share by clicking 'Connect to Server...' in the Places menu.
When I click search in Nautilus my Samba shares do not show up in my places to select, and I can't figure out where they actually mount to. Does anyone know how to do this?
Thanks.

---

### Post by hyperair on 2008-02-04
Well from what I know, Nautilus doesn't need to mount a Samba share in order to access it. What you need to do is actually mount it before you can start searching. Unfortunately there isn't an easy way to do that (yet), so you gotta use the terminal:
```

sudo mount -t cifs //server/share /path/to/mountpoint

```
or
```

sudo mount -t cifs //server/share /path/to/mountpoint -o user=<username>

```
Then you can use Nautilus's search dialog normally with that mount point.

---

### Post by ReverendJ1 on 2008-02-04
That makes sense. Thanks. I figured since whenever I connect to a Samba share it makes an icon for it on my desktop that it had to be mounting them automagically, but I guess it isn't.

---

### Post by hyperair on 2008-02-04
It's not. I take it that you're using Ubuntu Hardy? This behaviour is rather new I reckon.

---

### Post by ReverendJ1 on 2008-02-04
No, I'm using Gutsy Gibbon. It did the same thing in Feisty Fawn for sure, and I'm pretty sure Edgy Eft too. Try it out, whenever you connect through connect to a server, it will create a shortcut on your desktop for it indefinitely.

---

