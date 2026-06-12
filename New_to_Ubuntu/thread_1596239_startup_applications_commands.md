---
title: "startup applications commands?"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by sallam on 2010-10-14
Greetings

Is there a list somewhere of the commands we can use with programs that we add in the Startup "Applications" tool?
For example, I need a couple of startup applications (alarm clock and transmission) to start minimized. What command should I add with their names there?

I hope someone could point me to a document or list of such commands to use when needed.

Many thanks.

---

### Post by amjjawad on 2010-10-14
> **sallam said:**
> Greetings

Is there a list somewhere of the commands we can use with programs that we add in the Startup "Applications" tool?
For example, I need a couple of startup applications (alarm clock and transmission) to start minimized. What command should I add with their names there?

I hope someone could point me to a document or list of such commands to use when needed.

Many thanks.


Perhaps here: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by AndyM3 on 2010-10-14
Look into [AllTray]("http://alltray.trausch.us/") if you want them to start minimized to tray. I think it's in the default repositories.

Also, the "man" command or running the application with the "--help" or "-h" parameter might help you.

---

### Post by sallam on 2010-10-14
> **AndyM3 said:**
> running the application with the "--help" or "-h" parameter might help you.
That's what i was looking for. Many thanks.
Turned out that Transmission can have -m added to its command to strup minimized in tray, and Alarm Clock can have --hidden added for the same effect.

Now I know where to find programs' options and parameters.
Many thanks.

---

