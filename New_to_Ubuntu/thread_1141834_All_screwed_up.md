---
title: "All screwed up"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by wlg on 2009-04-28
I'm a newbie and I'm afraid I screwed the pooch.  I need help!

I recently upgraded from 8.10 to 9.04.  Ever since the upgrade I've had trouble logging into ebay plus streaming audio or video.  I've googled my problems and looked at dozens of sites that recommended how to fix this.  I've blindly accepted lots of web advice and entered lots of commands through copy/paste. After 4 or 5 days I am no closer to my solution and I'm
afraid I might have a massive bundle of knots from blindly entering commands. Is there anyone out there who could tell where to start to find out my problems and find out of the bundles of knots?

---

### Post by MightySeb on 2009-04-28
For your Ebay connection problem, it's probably Firefox's configuration files that got "screwed" ( :P ) in the upgrade process.

To restore Firefox to it's default state :

[LIST=1]
[*]Close Firefox
[*]Go in your home folder
[*]Press CTRL + H to show hidden files
[*]find the ".mozilla" folder and rename it to something else ( like ".mozilla-backup)
[*]Start firefox (Another .mozilla folder will be created with the default settings)
[/LIST]

By the way, your problems could come from a bad internet connection. Before going on, you should at least test on another computer if you have the same problems or not.

If your problems persists, maybe you will be forced to make a [clean install]("https://help.ubuntu.com/community/Installation").

---

