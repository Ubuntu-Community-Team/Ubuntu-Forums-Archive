---
title: "Strange Problem With Program Icons"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-08-25
Ok, so I installed Eclipse from the default repositories and I have a little graphical problem. On the Kickoff menu, it shows the little icon next to the program. But when I add it to the panel, the applications is there, but you can't see an icon. And when I open the properties there is no way to change the icon. If I'm browsing with admin permissions (kdesudo dolphin) in /usr/share/applications the icon is showed on the eclipse.desktop, but not in the preview but not in the preview. When I'm browsing without admin permissions, the icon isn't show on either eclipse.desktop or the preview. So any ideas how to fix this?

---

### Post by dniMretsaM on 2011-08-26
Bump.

---

### Post by dniMretsaM on 2011-08-27
Anyone?

---

### Post by dniMretsaM on 2011-08-30
Still wondering...

---

### Post by dniMretsaM on 2011-08-31
Bump (again).

---

### Post by dniMretsaM on 2011-09-10
I feel like I've done this before...

---

### Post by ubudog on 2011-09-10
This seems to be a permissions issue.  What is the path of the icon file?

You can probably fix this like so:
```
sudo chown username:group /locationtoicon/icon.png
```

That will give your regular user permissions... hope this helps.  Not sure what else this could be.

---

### Post by dniMretsaM on 2011-09-10
> **ubudog said:**
> This seems to be a permissions issue.  What is the path of the icon file?

You can probably fix this like so:
```
sudo chown username:group /locationtoicon/icon.png
```That will give your regular user permissions... hope this helps.  Not sure what else this could be.

Not sure where the icon is stored. Any idea? I'll do a little searching and post back if I find it. By the way congratulations on becoming a mod!

EDIT: I found the icon and ran the following:
```
sudo chown bryan /usr/share/icons/hicolor/32x32/apps/eclipse.png
```

It made the change. I then removed the icon from the the panel and then re-added it but it's still blank. I must say, this is one of the oddest issues I've had.

---

### Post by ubudog on 2011-09-10
Thanks!

Strange, try this:
```
sudo chown bryan:bryan /usr/share/icons/hicolor/32x32/apps/eclipse.png
```

---

### Post by dniMretsaM on 2011-09-10
Tried that and it didn't work. However, I decided to change the owner of eclipse.desktop to myself and see what happened. That didn't work right away but it allowed me to change the icon. I changed it to something else and it showed up. When I changed it back to the eclipse icon it stopped showing up. Then I tried the Eclipse icon under "Other icons" instead of "System icons" (which is what I had been using) and it showed up just fine. So it must have been a problem with whatever icon it was trying to use (pointing to a blank file maybe?). So anyway, solved. Thanks for the help. Again, really odd problem...

---

### Post by ubudog on 2011-09-10
Strange, well glad you got it working.

---

