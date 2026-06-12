---
title: "Creating Shortcut that Requires Sudo to Run"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by justinmiller87 on 2009-08-16
In order to run the Rockbox updater properly, it has to be run as an administrator. I moved the file into /opt and now want to make a shortcut and put it in my menu. Should I make the shortcut as "gksudo /opt/rbutilqt" or is there some other method of letting the system know the shortcut should be run as an administrator by default?

Thanks.

---

### Post by Paddy Landau on 2009-08-16
gksudo will be absolutely fine. I use it myself on a launcher.

Why don't you test it?

---

### Post by justinmiller87 on 2009-08-16
I know it works, I had tested it. I just wondered if that was the "right" way to do it.

---

### Post by Paddy Landau on 2009-08-16
> **justinmiller87 said:**
> I just wondered if that was the "right" way to do it.
There are only two ways that I know of.

[LIST=1]
[*]Run it in a terminal; possible only if it's a CLI-type command. Then sudo will work.
[*]Use gksudo as you did.
[/LIST]
AFAIK, gksudo is always fine, even for CLI commands, whereas sudo is fine only for CLI commands and not for GUI commands.

[More information about sudo and gksudo]("https://help.ubuntu.com/community/RootSudo").

---

