---
title: "Pidgin"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by usul503 on 2009-01-10
So my problem is simple to explain. I click on Pidgin and the window tab appears at the bottom it says loading and then disappears. The application never open, I was having the same issue with Firefox, but after updating it fixed and now for Pidgin it did not even after updates. Any idea what it could be?

---

### Post by kellemes on 2009-01-10
> **usul503 said:**
> So my problem is simple to explain. I click on Pidgin and the window tab appears at the bottom it says loading and then disappears. The application never open, I was having the same issue with Firefox, but after updating it fixed and now for Pidgin it did not even after updates. Any idea what it could be?

Open a terminal window and type "pidgin" <ENTER>
Post the output..

---

### Post by usul503 on 2009-01-10
usul503@usul503-laptop:~$ pidgin
Bus error
usul503@usul503-laptop:~$ Pidgin
bash: Pidgin: command not found

---

### Post by cerealtx on 2009-01-10
are u sure u have it installed type in ```
pidgin -v
```

---

### Post by usul503 on 2009-01-10
usul503@usul503-laptop:~$ pidgin -v
Pidgin 2.5.2

---

### Post by cerealtx on 2009-01-10
well its deffinately on there, but for some reason its not finding it how did u install it?? manually or did u use snyaptic? you might try uninstalling through snyaptic and reinstalling through snyaptic

---

### Post by usul503 on 2009-01-10
It was installed by itself on the Ubuntu install. I was given a Live OS CD for it and installed ubuntu on a new hard drive. So it all came on with the install.

---

### Post by kellemes on 2009-01-10
> **cerealtx said:**
> well its deffinately on there, but for some reason its not finding it how did u install it?? manually or did u use snyaptic? you might try uninstalling through snyaptic and reinstalling through snyaptic

Read post 3 ;-)
pidgin is found.. it's responding with "Bus error"

---

### Post by usul503 on 2009-01-10
What does that mean?

---

### Post by kellemes on 2009-01-10
> **usul503 said:**
> What does that mean?

Don't know ;-)

I'd go for a reinstall, and maybe remove (or at least move) your configuration settings. Don't know where they are actually, but probably something like /home/<user>/.pidgin or such?

---

### Post by usul503 on 2009-01-10
Ok, then can you guide me through the uninstall?

---

### Post by kellemes on 2009-01-10
> **usul503 said:**
> Ok, then can you guide me through the uninstall?

Remove/Purge:
```
sudo apt-get remove --purge pidgin
```

And install:
```
sudo apt-get install pidgin
```

---

### Post by usul503 on 2009-01-10
It worked!

Thank you.

---

