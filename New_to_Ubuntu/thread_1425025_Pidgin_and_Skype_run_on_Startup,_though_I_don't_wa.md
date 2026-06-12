---
title: "Pidgin and Skype run on Startup, though I don't want them to..."
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Wataru8675 on 2010-03-08
Just as the description says, Pidgin and Skype are running on startup, though I don't want them to.  This wasn't an issue until I started playing around with the Startup Applications settings, and even then all I did was add Korganizer to run on startup (which I DO want), and I checked for it to remember running applications when logging out.  The latter option I unchecked after I decided I didn't want it.

However, now Pidgin and Skype continue to open on startup.  I don't see them listed under Startup Programs, and I can't find any options in the programs themselves......any suggestions?

Thanks,
Kyle

---

### Post by Method X on 2010-03-08
Hi
Locate for System->Preferences->Startup applications->options.
Uncheck "Automatic remember running applications"

Now open your terminal.
```
pushd .config/gnome-session/saved-session/

ls -a

rm -r *

```

I think it will be ok from now.;)

---

### Post by Wataru8675 on 2010-03-08
Oooh, okay, so Gnome saved the applications, and kept running off of the saved data, even though it was unchecked?

---

### Post by Wataru8675 on 2010-03-08
Ah, okay, so Gnome kept going off the saved data, even though it was unchecked?  What do each of those commands do, exactly?

This was the fix I needed.  Thanks a lot! ^^

EDIT:  Oops...sorry for the double post. o.o;

---

### Post by Method X on 2010-03-08
> **Wataru8675 said:**
> Oooh, okay, so Gnome saved the applications, and kept running off of the saved data, even though it was unchecked?

Yes.
Well, i think you pushed button "Remember currently running application" and it saved your skype and pidgin. Very helpful option for some situations.

Folder /home/user-name/.config/gnome-session/saved-sessions/ contains files with saved sessions.

-----
pushd .config/gnome-session/saved-session/        <--- go to folder (pushd: push path into stack; pop: go back)

ls -a                                                                           show all files in folder

rm -r *                                                                        delete all files in folder


Have fun ;)

---

