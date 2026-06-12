---
title: "I'm running Jaunty.  Is it safe to packages from Karmic or Debian?"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-06
I'm thinking about testing out a new grsync (a rsync frontend) [version that is in the Karmic]("http://packages.ubuntu.com/karmic/grsync") and Debian repos but not yet available for Jaunty.  Is it safe to download the package and install it manually?  I'm not clear on the details but I heard somewhere that I need to make sure the packages are "binary compatible" and that sometimes Ubuntu packages are just taken straight from Debian without modifications.  If anything goes wrong with grsync, could I simply remove the package and go back to the old Jaunty package without a reinstall?

A friend of mine mentioned that he has used new Jaunty packages on Intrepid without issues which is why I bring this up.

[http://packages.ubuntu.com/karmic/grsync](http://packages.ubuntu.com/karmic/grsync)
[http://packages.debian.org/squeeze/grsync](http://packages.debian.org/squeeze/grsync)

---

### Post by Rocket2DMn on 2009-06-06
You should be able to manually install a small packagea like this.  Its dependencies are most likely already met in Jaunty, so go ahead and try.  If it doesn't want to install, it will tell you, and if the program just fails to work, you can remove it since you are installing using a .deb file.

---

### Post by Rubicon_82 on 2009-06-06
The Debian package format includes a list of dependencies within the *.deb file.  So, if you're trying to manually install a *.deb file, the worst that should happen is dpkg refusing to install it due to unmet dependencies.

However, you shouldn't add a repository to your /etc/apt/sources.list from Karmic unless you're planning to upgrade your whole distribution.  Once you do upgrade, it will be *nearly* impossible to downgrade back to Jaunty.

It is an even worse idea to add a Debian repository to a Ubuntu distribution.  Doing so will risk severely breaking your system.  The consequences of doing this are nicely described by Randall Monroe (xkcd author) here: [http://blag.xkcd.com/2009/04/03/what-happened-to-my-laptop/](http://blag.xkcd.com/2009/04/03/what-happened-to-my-laptop/)

---

### Post by learningcurb on 2009-06-06
Thanks for the tips folks. I'm glad to know it's relatively safe to install Karmic .debs without having to wait for them to show up in backports, as long as I don't mess around the with dependencies.

Also, that xkcd post was a good read.  Reminded me of [http://xkcd.com/349/](http://xkcd.com/349/)

---

