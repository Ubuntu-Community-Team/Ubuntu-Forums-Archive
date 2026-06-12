---
title: "'usage' error?"
date: 2010-08-16
forum: New to Ubuntu
---

### Post by Roffmanjoe on 2010-08-16
Hi  i'm unsure about this line of txt that i've been getting after trying to install , how do i remove it ?

[U][B]E: Type 'usage:' is not known on line 61 in source list /etc/apt/sources.list
E: The list of sources could not be read.
[/B][/U]

---

### Post by Zeike on 2010-08-16
Sounds like an error happened along the line somewhere and some stray text go added to your /etc/apt/sources.list file.

You can open it up by running 'gksu gedit /etc/apt/sources.list'

Look on line 61 for the text 'usage' and see if it seems out of place.  You can either try to fix it yourself, or paste it here if you're not sure what to do.

---

### Post by Roffmanjoe on 2010-08-16
well here are the lines 49 - 71
i'm not sure how to remove

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock
[U]usage: sudo -h | -K | -k | -L | -V
usage: sudo -v [-AknS] [-p prompt]
usage: sudo -l[l] [-AknS] [-g groupname|#gid] [-p prompt] [-U username] [-u
            username|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...[/U]
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) lucid cairo-dock ## Cairo-Dock-Stable
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) lucid main ## Cairo-Dock-PPA

---

### Post by gdonwallace on 2010-08-16
If you use gedit like in the previous post, it works just like any text editor.  Just highlight the lines that need to be removed and press Delete.

If you are using a text editor like Vi, Vim, or nano, it can be a little more complicated.  For Vi or Vim, the command to delete a line is dd.  Just make sure that you are at the beginning of the correct line to delete.  In nano, it ctrl+k.  That will actually cut the line and place it in memory to be pasted somewhere else, but if you "Cut" all the lines and save it and exit, then the lines will be erased for you.

Good luck.

---

