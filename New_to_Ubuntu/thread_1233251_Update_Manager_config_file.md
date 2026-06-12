---
title: "Update Manager config file"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by ubudog on 2009-08-06
Where is the Update Manager config file?

---

### Post by mcduck on 2009-08-06
Update Manager stores it's settings in gconf (editable with the gconf-editor), but there's hardly anything there so most likely that's not what you are looking for.

Perhaps if you tell what you are trying to do we'll be able to help more. :)

---

### Post by ubudog on 2009-08-06
I'm trying to make Update Manager show up on the panel instead of it popping up.  I thought maybe I could do this by editing the config file.  Thanks for the response.  :)

---

### Post by mcduck on 2009-08-06
Ok. Here's how to do that:

1. Press Alt-F2 and run "gconf-editor" (or start it from a temrinal)
2. Browse to apps/update-notifier
3. Disable the "auto_launch"-key.

This will change the updates to work like they did in previous Ubuntu versions, you'll see an icon in the notification area when there are updates available and Update Manager only pops up when you click the icon, not on it's own.

---

### Post by ubudog on 2009-08-06
> **mcduck said:**
> Ok. Here's how to do that:

1. Press Alt-F2 and run "gconf-editor" (or start it from a temrinal)
2. Browse to apps/update-notifier
3. Disable the "auto_launch"-key.

This will change the updates to work like they did in previous Ubuntu versions, you'll see an icon in the notification area when there are updates available and Update Manager only pops up when you click the icon, not on it's own.

Thanks!  :P

---

### Post by ubudog on 2009-08-06
Yep it's showing up on the panel now.  Thanks for the help! :o

---

