---
title: "Firefox 3.0.6 issues when loading"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by 133794m3r on 2009-02-11
whenever i shut down my pc occasionaly when i restart firefox will act like it's the first time i've ever used it.. showing little pages for my addons, showing the 3.0.6 page etc. Any hints with this?

---

### Post by 0bso on 2009-02-11
That's what it does after it gets updated. (the 3.0.6  update got released today/last night)

---

### Post by 133794m3r on 2009-02-11
I've already updated it you see... -_- i updated it several days ago. It's done it 3 times now. once 2 days ago, then yesterday, and now today. I already updated to 3.0.6 awhile ago... like the same day it was updated on the windows machines...

---

### Post by Malalo on 2009-02-11
Do you close Firefox prior to shutting down your computer ?
May sound silly, but perhaps shutting down the comp without closing Firefox might prevent it from keeping your latest settings...

---

### Post by 133794m3r on 2009-02-11
erm... normally i shutdown ff before shutting down the pc... and this issue's very intersting to me... :/

---

### Post by Dougie187 on 2009-02-11
You could try cleaning out your firefox profile, of course you would probably want to make a backup of that before you erased it for good just incase it didn't help any.

To clean your ff profile try this.

With FF not running
```
cp -R ~/.mozilla/firefox ~/FFBAKUP
rm [COLOR="Red"]-rf[/COLOR] ~/.mozilla/firefox 
```

Be very careful when you use the -rf flag on the rm command. After you run these commands try running firefox, and setting up your preferences. If it ends up not helping out you can do this to return your previous settings.

```
rm -rf ~/.mozilla/firefox
mv ~/FFBAKUP ~/.mozilla/firefox
```

And it should be back to the way it was.

---

### Post by 133794m3r on 2009-02-11
> **Dougie187 said:**
> You could try cleaning out your firefox profile, of course you would probably want to make a backup of that before you erased it for good just incase it didn't help any.

To clean your ff profile try this.

With FF not running
```
cp -R ~/.mozilla/firefox ~/FFBAKUP
rm [COLOR="Red"]-rf[/COLOR] ~/.mozilla/firefox 
```

Be very careful when you use the -rf flag on the rm command. After you run these commands try running firefox, and setting up your preferences. If it ends up not helping out you can do this to return your previous settings.

```
rm -rf ~/.mozilla/firefox
mv ~/FFBAKUP ~/.mozilla/firefox
```

And it should be back to the way it was.
ok i'll try it thanks

---

