---
title: "Command to safely close firefox"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-03
I am looking into writing my first script.

Just a simple one to close firefox upon shutdown.

Someone told me to try _pkill firefox_ but when I do this firefox still shows a crash report when I reopen it.

Is what I am wanting to do even possible?

What would be the command?

and is there a place I can learn about writing scripts so I can cross reference my Idea and how to implement it?

---

### Post by iaculallad on 2008-12-03
What about doing:

```
killall firefox
```

---

### Post by nakama85 on 2008-12-03
> **iaculallad said:**
> What about doing:

```
killall firefox
```

I tried that but firefox still shows it as a crash

---

### Post by user12021 on 2008-12-03
Try doing "killall -s 3 firefox"

---

### Post by nakama85 on 2008-12-04
> **user12021 said:**
> Try doing "killall -s 3 firefox"

Unfortunately it still shows as crashed. Perhaps There is no way around this.

---

### Post by HittingSmoke on 2008-12-04
For me, the only way to get Firefox to restore tabs on startup is if it crashes or I shut down with it running. If I try a "Save and quit", it just comes up with a blank page when I start up again so I usually just shut down and let it die. Whats the advantage of what you're proposing?

---

### Post by nakama85 on 2008-12-04
> **HittingSmoke said:**
> For me, the only way to get Firefox to restore tabs on startup is if it crashes or I shut down with it running. If I try a "Save and quit", it just comes up with a blank page when I start up again so I usually just shut down and let it die. Whats the advantage of what you're proposing?

I'm not really sure what the advantage is other than it asking "would I loke to restore the previous session" rather than "firefox crashed would you like to try to restore the previous session"

Just a minor annoyance.

Really I am just looking for a reason to try to write my first script and get a feel for it.

_*Note: I am using TabMixPlus plugin. The best tabed browsing plugin in ever (in my opinion) Gives full customization over your tabed experience*_

---

### Post by PocketDog on 2008-12-04
You can set Firefox to never prompt restore sessions after a crash by setting the **browser.sessionrestore.resume_from_crash** value to 'false'. (Type **about:config** in the address bar.) I can't figure out how to force-resume a previous session without prompting though.

---

### Post by nakama85 on 2008-12-04
> **PocketDog said:**
> You can set Firefox to never prompt restore sessions after a crash by setting the **browser.sessionrestore.resume_from_crash** value to 'false'. (Type **about:config** in the address bar.) I can't figure out how to force-resume a previous session without prompting though.

Well because I am using tabmixplus it takes over the firefox restore function and uses it's own. I can set tabmixplus to do the same thing your suggesting, however I find this feature very usefull because if a page were to crash firefox I can choose not to restore the same page that crashed it.

---

