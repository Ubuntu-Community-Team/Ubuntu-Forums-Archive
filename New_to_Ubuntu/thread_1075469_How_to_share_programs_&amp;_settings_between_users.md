---
title: "How to share programs &amp; settings between users?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by valmiki9 on 2009-02-20
Hello, first post on here, and new to ubuntu (using 8.10)

I've managed to sort out a lot of the problems that I have encountered along the way, but need help with one issue at present.

I have setup two users on my machine, one for me and one for my wife.

I have then changed all the settings, etc. on my user profile to use Firefox including various apps and themes.

I would like to share these same settings with my wife's profile as well, ideally system-wide?

Could someone pinpoint me to where I could get some info on this? I have already tried search, but that tended to send me to pages about sharing profiles between Windows and ubuntu, rather than between users?

I'm figuring I'm going to need how to do this in the future as well, as I'm bound to install programs that my wife and I both use, or will I need to install program separately?

thanks in advance :D

valmiki

---

### Post by mcduck on 2009-02-20
All programs installed through Ubuntu's package management are installed system-wide, and are automatically available to all users.

Program settings, on the other hand, are personal and stored in each user's home directory in hidden files & directories. This also applies to installed themes and such stuff (the rule is that everything that requires using sudo password to install is installed system-wide, everything that can be installed without password is personal).

For firefox settings, I suppose it should be possible to simply create symbolic links from one user's configuration files to the other user's home directory.

---

### Post by valmiki9 on 2009-02-20
thanks for the reply, I'll investigate further.

valmiki9

---

