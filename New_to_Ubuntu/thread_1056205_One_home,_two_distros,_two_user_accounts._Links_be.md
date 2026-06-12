---
title: "One /home, two distros, two user accounts. Links between the two?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by dorkdork777 on 2009-01-31
This is probably a very stupid question, but here goes.

I've been experimenting with KDE Four Live, which is a LiveCD based on openSUSE - and I'd like to install it. From my previous experiences, I've decided it's overall a better option to have different usernames, on the same /home partition. Of course, I need my music, videos, etc to be accessible by both, and I'd quite like my Firefox settings to be shared.

I've heard this is possible by creating a directory in /home, away from both those user accounts, putting those files and settings in there, and linking the directories. But I don't know what precautions I should take to make sure both distros like what I'm doing, and both have read/write powers, even though it's two separate user accounts. And I'm not too sure on how to do the linking properly.

Any help would be appreciated :)

---

### Post by jbrown96 on 2009-01-31
If you're going to link the whole directory, then the two distros are sharing the exact same files. This is essentially no different that using the same username on each system, except that it's a lot more work. I understand that you want to share your documents/media files, and you can do this in Gnome very easily (I'm not at a computer with KDE) by right clicking on a file/folder (they're the same thing in *NIX) and choosing "make link". The command link will also do this. Check ```
man link
```

If you've had trouble using the same username on multiple distros, I don't think linking an entire /home/user directory would help at all. I think you should try linking just a couple of directories within there like Documents, Music, etc. You should also be fine linking .mozilla to share your settings, but you might run into problems with a mixed Gnome/KDE environment. I know that KDE 4 has a "scroll-bar fix" for Firefox in System Settings and that probably changes something in .mozilla, which might make a bad change when/if you use Gnome.

Edit: If you change the home directories to be fully read and writable, you will get a .dmrc error whenever you login to Ubuntu. To fix this, you need to run ```
sudo chmod 644 /home/USER/.dmrc
``` to restore the proper permissions

---

### Post by unutbu on 2009-01-31
The key to easy sharing of files is to have the two user accounts share the same UID.
The command
```

id
```

will show you the user's UID. On Ubuntu, the first normal user account has UID=1000.

Each file and directory on an unix filesystem has an owner. Although we usually refer to the owner by a name such as 'root' or 'user', the operating system really sees each file and directory as being owned by a UID. So if a file (such as an mp3 file) is owned by UID=1000, and if on Ubuntu UID=1000 is associated with user Joe, then Joe owns the file as far as Ubuntu is concerned. But if KDE Four Live has a user Sally which it thinks is UID=1000, then Sally owns the same file as far as KDE Four Live is concerned.


So the setup you are looking for should look like this:
```

                  owned by
                  UID
/home/Joe         1000
/home/Sally       1000
/home/data        1000
```

Allow /home/Joe to contain all the configuration dot files that the Ubuntu apps make for Joe (like .mozilla, .bashrc, .profile, etc)

Allow /home/Sally to contain all the configuration dot files that KDE Four Live apps make for Sally (like .mozilla, .bashrc, .profile, etc)

Put Music, Docs, Pictures, and other sharable data in /home/data.

To complete the illusion, you can use symlinks like this:
```

ln -s /home/data/Music /home/Joe/Music
```

This creates a symlink from /home/Joe/Music to /home/data/Music.
That means you can navigate to music files by going to /home/Joe/Music, even though in reality the files will be stored in /home/data/Music.

There are ways to change a user's UID even after it has been created. The command
```

sudo usermod --uid 1000 Sally
```
changes Sally's uid to 1000. It also changes the UID (ownership) of each file in /home/Sally for you too. Be careful that there is no other user who has UID=1000 if/when you issue this command.

---

### Post by dorkdork777 on 2009-01-31
Fantastic; thanks a lot, both of you! :D

EDIT: Worked like a charm. I'm posting this from my installed version of KDE Four Live, as planned; everything is working perfectly. KDE4 4.2 is brilliant too, but I'm gonna give it some time before I switch over completely ;)

EDIT 2: Glad I gave it some time :P I love KDE4.2, but... it just doesn't feel as complete as GNOME. I think Jaunty will help, but there's still some bugs. I'm back on GNOME for now, back on my beloved Ubuntu :)

---

