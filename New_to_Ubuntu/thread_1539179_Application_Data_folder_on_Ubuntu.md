---
title: "Application Data folder on Ubuntu"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by dorians58 on 2010-07-26
Hi all,

What is the "Application Data" folder equivalent on Ubuntu( and on MacOS if you know please)?

Thank you in advance

---

### Post by viralmeme on 2010-07-26
> **dorians58 said:**
> Hi all,

What is the "Application Data" folder equivalent on Ubuntu( and on MacOS if you know please)?

[Linux's directory structure]("http://www.tuxfiles.org/linuxhelp/linuxdir.html"). The MAC is different :o

---

### Post by kwacka on 2010-07-26
Also check hidden files/directories in your home directory e.g. .Skype, .xchat, .bashrc

---

### Post by danwsc on 2010-07-29
Hi I have the same issue here.
My application tries to store data files in the /home/$USER directory.

Only problem is that when I do a dpkg -i *.deb, it says that superuser privilege is required.  But when I do a sudo dpkg -i *.deb, the $USER becomes root and the $HOME root home.

So how did the apps get to be installed in the /home/$USER directory in the first place please?

OR is there a fixed place to put the application data directory in Ubuntu?

An answer to any of these would be much appreciated.

Thanks.

---

### Post by aeiah on 2010-07-29
apps dont get stored in the home directory, application settings and user data get stored there (in hidden files and folders)

root has write access to the whole filesystem and will, when installing something, usually install the binary file to /usr/bin/programname and the default settings to each home directory, eg: /home/user/.programname or /home/user/.config/programname

this is fairly simplified of course. much more than just an executible in /usr/bin .. there'll be /usr/lib/ libraries, man files, documents, blah blah blah.

so really there is no set place. everything gets put in different places and you never need to know where they go (apart from user settings, but those are all in one place, in their respective folder in home)

OS X has a similar structure, since its based on unix.

---

