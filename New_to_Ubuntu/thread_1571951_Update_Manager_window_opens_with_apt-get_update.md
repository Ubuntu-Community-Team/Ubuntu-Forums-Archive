---
title: "Update Manager window opens with apt-get update"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by seawolf167 on 2010-09-10
This should [hopefully] be an easy workaround, I just can't find/figure it out.

Say I ssh into another computer or even open the terminal on my computer and type the command to update the package list

```
sudo apt-get update
```Immediately after, the "Update Manager" window opens and minimizes itself to the tray. Is there a way to make this window **not** open? (or is there a way to close this window using terminal commands?)

I've looked in [System -> Administration -> Update Manager] and  [gconf-editor -> apps -> update-manager] but didn't find anything in either places.

I could change the window size to (0,0) but then I just wouldn't be able to see it, it'd still be there.

Any thoughts?

---

### Post by TCHebb on 2010-09-10
Hmm... If this is only on your computer, there might be some weird trigger opening the update manager when you run "apt-get update." Does the manager show any available updates? If it does, try installing them and see if it still happens.

---

### Post by Gen2ly on 2011-09-22
Not to revive a dead topic :), but I was wondering if anyone else has come across this.  When I run apt-get install from the command line, the Update Manager will come up.  Since I usually install from the command line, I'd be interested if anyone knows how to fix this.

---

### Post by Elfy on 2011-09-22
If you run from a command line I guess you could just remove the package and it'll not be there to 'come up'.

---

### Post by Krytarik on 2011-09-22
> **Gen2ly said:**
> When I run apt-get install from the command line, the Update Manager will come up.  Since I usually install from the command line, I'd be interested if anyone knows how to fix this.
How about this?:
> **TCHebb said:**
> Does the manager show any available updates? If it does, try installing them and see if it still happens.
@forestpiskie: Obviously, you didn't get the point. ;-)

---

