---
title: "Does Ubuntu automatically tell you when upgrades are available?"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by tc101 on 2010-08-05
Does Ubuntu automatically tell you when upgrades are available? Or do I need to go to Update manager on a regular basis and see what is available?

---

### Post by mike555 on 2010-08-05
no, it will tell you when updates are though ..... most of the time if you want to upgrade an app you will need to add it's ppa to your software source list ... if this is what you want to do "Ubuntu-tweak " makes it easy .

---

### Post by oldfred on 2010-08-05
You can adjust some settings/options with update manager's settings (left lower corner).

---

### Post by sgosnell on 2010-08-05
It may or may not tell you, depending on the settings.  You can have Update Manager run at boot or not, your choice, and choose what it does if it is running.  Like most Linux features, it is very configurable.

---

### Post by s3a on 2010-08-05
Go to System=>Administration=>Software sources=>Automatic Updates and optimize the settings for yourself.

---

### Post by mcduck on 2010-08-05
> **tc101 said:**
> Does Ubuntu automatically tell you when upgrades are available? Or do I need to go to Update manager on a regular basis and see what is available?

By default the Update Manager will automatically inform you about available updates, but it only opens immediately for security updates, for normal updates it's set to open only once per every seven days (and that timeout resets if you update manually, so if you do a manual update once per week chances are that you'll never see the Update Manager opening automatically).

It also tries to avoid interrupting you, so you'll usually have to leave the computer alone for a while before it pops open automatically.

It's also possible to change the Update Manager back to the traditional behavior it had in previous Ubuntu versions, showing an icon in the Notification Area as soon as there are updates available (and never automatically popping up the Update Manager window). This option isn't available in the graphical setting tools, though, only through gconf-editor.

(so, the sort answer is that the Update Manager will tell you when you have updates available and you never need to open it manually. At least unless you configure it to behave otherwise.)

---

