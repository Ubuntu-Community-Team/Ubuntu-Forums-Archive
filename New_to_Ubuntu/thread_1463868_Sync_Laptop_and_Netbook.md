---
title: "Sync Laptop and Netbook"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-04-27
I am trying to sync my laptop and netbook to be as identical as possible. Grsync makes this easy for Home files but what about all the added programs and tweaks? Is there a way to list all the installed programs, settings, and tweaks on my laptop so I can add them to the netbook? Thank you

---

### Post by undecim on 2010-04-27
Have a look at [http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

It's a good howto on backing up packages lists, but it can be used for syncing packages just as well.

Most anything else should be in your home directory.

---

### Post by Hospadar on 2010-04-27
In terms of application settings, they are almost entirely stored in the hidden files and folders (those files and folders who's name begins with a '.', use Ctrl-H in the file browser to see them), and syncing those files would preserve settings across computers.

As for applications, there are tools to save and restore package lists, but for me personally, I'd prefer to just install things when I need them.  It's so easy to do through synaptic or the command line, I have difficulty imagining a tool which would be simpler enough (for syncing installed apps) to warrant my use.

---

### Post by Arla on 2010-04-27
> **cmcanulty said:**
> I am trying to sync my laptop and netbook to be as identical as possible. Grsync makes this easy for Home files but what about all the added programs and tweaks? Is there a way to list all the installed programs, settings, and tweaks on my laptop so I can add them to the netbook? Thank you

I may have to look into Grsync since I'm trying to figure syncing two computers right now, for programs try the UMarks extension for firefox, I just used it and it can generate a list of installed (and removed) packages, and then replicate that over, it doesn't install "custom" packages (those outside the repositories) but for the most part it's working nicely (at least for me).

---

