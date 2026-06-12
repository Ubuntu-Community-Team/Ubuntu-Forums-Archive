---
title: "How to find the launching file?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-12-14
Hi,

I need to know which file to choose.

When I click on an IRC link, I have the ability to choose which program I want to use for such links.

Pidgin is what I use, but which file is the one I need to link to this type of link?

Current Pidgin files are numerous:

> 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/pidgin
/usr/share/doc/pidgin/copyright
/usr/share/menu
/usr/share/menu/pidgin
/usr/share/applications
/usr/share/applications/pidgin.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/pidgin.1.gz
/usr/share/man/man3
/usr/share/man/man3/Pidgin.3pm.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/pidgin
/usr/share/gconf
/usr/share/gconf/schemas
/usr/share/gconf/schemas/purple.schemas
/usr/bin
/usr/bin/pidgin
/usr/lib
/usr/lib/perl5
/usr/lib/perl5/Pidgin.pm
/usr/lib/perl5/auto
/usr/lib/perl5/auto/Pidgin
/usr/lib/perl5/auto/Pidgin/Pidgin.so
/usr/lib/perl5/auto/Pidgin/Pidgin.bs
/usr/lib/pidgin
/usr/lib/pidgin/cap.so
/usr/lib/pidgin/gestures.so
/usr/lib/pidgin/gevolution.so
/usr/lib/pidgin/musicmessaging.so
/usr/lib/pidgin/ticker.so
/usr/lib/pidgin/convcolors.so
/usr/lib/pidgin/extplacement.so
/usr/lib/pidgin/gtkbuddynote.so
/usr/lib/pidgin/history.so
/usr/lib/pidgin/iconaway.so
/usr/lib/pidgin/markerline.so
/usr/lib/pidgin/notify.so
/usr/lib/pidgin/pidginrc.so
/usr/lib/pidgin/sendbutton.so
/usr/lib/pidgin/spellchk.so
/usr/lib/pidgin/timestamp.so
/usr/lib/pidgin/timestamp_format.so
/usr/lib/pidgin/xmppconsole.so
/usr/share/doc/pidgin/README
/usr/share/doc/pidgin/AUTHORS
/usr/share/doc/pidgin/NEWS.gz
/usr/share/doc/pidgin/changelog.Debian.gz


I'm guessing I need to pick one, but have no idea which one.

Any ideas? 

Thanks!

---

### Post by Daveth on 2008-12-14
this one

/usr/bin/pidgin

---

### Post by drs305 on 2008-12-14
You can find the location of the run command if you know the app name by running:
```
which *appname*
```

In this case, here is the command and result:
```

drs@computer:~$ [B]which pidgin
/usr/bin/pidgin[/B]

```

---

### Post by Paqman on 2008-12-14
On Linux, you don't need to know the full path to launch an app like you do on Windows.

So to launch Pidgin, you only need the command;
```
pidgin
```

The system is clever enough to figure the rest out for you.

---

