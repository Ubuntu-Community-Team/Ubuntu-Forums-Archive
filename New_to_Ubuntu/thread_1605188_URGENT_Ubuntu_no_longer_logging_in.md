---
title: "URGENT: Ubuntu no longer logging in"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-10-25
Hi,

Have a programming assignment due in 2h that I'm almost done - while procrastinating, I absentmindedly increased my workspace columns/rows from 2/2 to 16/16. Well, not quite, at 14/16, it froze.

I cursed my stupidity and reset the machine. Upon logging in, it freezes before anything comes up. I can only move the mouse. I assume it keeps trying to load my changes.

How can I revert this stupid change and get my machine logging in again?

Very urgent.... :(

---

### Post by SuaSwe on 2010-10-25
Having read around on the subject, I *think* the workspace switcher's config file knocks about here:

/schemas/apps/workspace_switcher_applet/prefs/

(Accessed via gconftool - see [http://jennyandlih.com/gconf-editor-command-line](http://jennyandlih.com/gconf-editor-command-line))

If it's incredibly urgent and you happen to have your install (Live) CD, you could always log on there and do whatever you need to do; provided there's not been any data corruption (and I don't see why there would have been!) you should be able to access everything.

---

### Post by cariboo on 2010-10-25
Boot from the Live CD and run fsck on your Ubuntu partition.

Open a terminal and type:

```
sudo fsck -y /dev/sda1
```

Substitute your drive and partition for the above example command.

---

### Post by nlsthzn on 2010-10-25
@cariboo907 ->

[S]For my own (and the OP's) learning benefit why should he run this command and what is it going to achieve?[/S] Never mind, did what I was supposed to do from the start "man fsck", but now another question, why do you think creating all of those extra workspaces has corrupted the file system?


Thanks
Neil

---

### Post by Pas_sa on 2010-10-25
Thanks SuaSwe, your post got me on the right track and I ended up solving the problem :) Ubuntu really needs a "safe mode" equivalent from Windows for when idiots like me screw **** up.

For anyone searching for this solution later: the trick is to disable Compiz. Workspace setting is dependent on your window manager, killing Compiz left me with just two workspaces. You can then edit the number of workspaces Compiz tries to create in the settings manager.

---

