---
title: "A couple of simple questions"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by rramsay on 2010-05-20
I'm going to install 10.4 later today, how do I add Medibuntu repository, or, any repository for that matter.

Also, I've been using firefox for a long time and have several add ons and plug ins already installed, will firefox recognize my ip address and load them, or will I have to reinstall all of them?

I'm a Linux virgin be gentle, thanks.

---

### Post by ubunterooster on 2010-05-20
open: system>administration>software sources

See [http://www.ubuntu-tweak.com](http://www.ubuntu-tweak.com) for a easy to use tool that has many extra sources

---

### Post by Paqman on 2010-05-20
You can add Medibuntu in one step by pasting this code block into a terminal:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

As for your Firefox profile, unless you've backed up the contents of your .mozilla folder in your home folder, then you'll have to resintall them.

---

### Post by rramsay on 2010-05-20
okay, thank you. I have some work to do.

---

### Post by lovinglinux on 2010-05-20
See [Profiles](http://firefox-tutorials.blogspot.com/2010/05/profiles.html) and [Backup](http://firefox-tutorials.blogspot.com/2010/05/backups.html) tutorials.

---

### Post by -kg- on 2010-05-20
The [Medibuntu Howto Page]("https://help.ubuntu.com/community/Medibuntu") in the Community Documentation (linked to from the Medibuntu site) will show you exactly how to do this, and give you a few hints and kinks, to boot.

---

