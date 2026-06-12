---
title: "How do I uninstall the following programs?"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by todayisgood on 2010-08-28
I'd like to remove the following software from Ubuntu, but I have no idea how:


[LIST]
[*]AcidRip DVD Ripper
[*]MPlayer Media Player
[*]Sun VirtualBox
[/LIST]
How can I get rid of these?

---

### Post by Zzl1xndd on 2010-08-28
If you installed them through the software centre (or any of the other Package Managers), you should be able to go back, search for them and they will now have a remove option as opposed to install when you select them.

---

### Post by Spice Weasel on 2010-08-28
> sudo apt-get remove mplayer virtualbox-ose virtualbox

Not sure about AcidRip.

---

### Post by Dayofswords on 2010-08-28
> **Spice Weasel said:**
> Not sure about AcidRip.

```
sudo apt-get remove acidrip
```

---

### Post by Spice Weasel on 2010-08-28
Oh yeah, don't forget to run "sudo apt-get autoremove" afterwards or you'll end up only half removing the programs if they use separate packages.

---

### Post by themusicalduck on 2010-08-28
Even if they weren't installed through the Software Centre you should be able to remove them. Look under Installed Software for a list of all installed stuff.

---

