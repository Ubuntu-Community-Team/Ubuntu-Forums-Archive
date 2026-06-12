---
title: "Where can apps be found in file system?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Not unique on 2011-05-10
Where can apps be found?
or applets (panel widgets) should I say.

I recently installed a app called "System monitor Indicator" but I can't get it to load at start by adding it to my start-up applications list because I can't find it in Bin or Usr/Bin or anywhere else I looked???
Can anyone help please??

---

### Post by synapsys on 2011-05-10
To find out where the binary is stored, use the "which" command.

For example,

```
which firefox
```

produces the output

```
/usr/bin/firefox
```

If you have an icon for the program, but don't know the command, right click on the icon and click "properties."

---

### Post by Rubi1200 on 2011-05-10
You can try looking for it from the terminal:

```
locate <name_of_package/file etc.>
```

---

### Post by Not unique on 2011-05-10
The first command "which" did not work and the second command "locate" has brought up so many pages in the terminal I don't know where I'm at.
Would it be a binary being a panel app??

---

### Post by synapsys on 2011-05-10
If it's a panel app, right click on it and click "properties." The entry for "command" is the command that is run to start the program. Use that with the "which" command, and it will tell you where it's located.

---

### Post by Ozitraveller on 2011-05-10
[https://help.ubuntu.com/community/FindingFiles](https://help.ubuntu.com/community/FindingFiles)

---

### Post by Not unique on 2011-05-10
> **synapsys said:**
> If it's a panel app, right click on it and click "properties." The entry for "command" is the command that is run to start the program. Use that with the "which" command, and it will tell you where it's located.

I tried right and left click but no properties on this one just about, remove, move and lock to panel.
And a search brings nothing up.

---

### Post by Not unique on 2011-05-10
dpkg -L System monitor Indicator said:
[I]Not me@Not me-OptiPlex-GX60:~$ dpkg -L System monitor Indicator
Package `system' is not installed.
Package `monitor' is not installed.

Package `indicator' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
jamie@jamie-OptiPlex-GX60:~$[/I]

If I find the DEB or PPA can anyone help please?

This is the site for it:  [https://launchpad.net/indicator-applet](https://launchpad.net/indicator-applet)

---

### Post by Not unique on 2011-05-10
**_SORTED !!!_**

I tried again with different spellings, grammar etc and wouldn't you know this worked:


[B][I]Not me@Not me-OptiPlex-GX60:~$ which indicator-sysmonitor
/usr/bin/indicator-sysmonitor
Not me@Not me-OptiPlex-GX60:~$ locate indicator-sysmonitor
/home/Not me/.indicator-sysmonitor.json
/home/Not me/Desktop/indicator-sysmonitor.desktop
/usr/bin/indicator-sysmonitor
/usr/share/applications/indicator-sysmonitor.desktop
/usr/share/doc/indicator-sysmonitor
/usr/share/doc/indicator-sysmonitor/changelog.Debian.gz
/usr/share/doc/indicator-sysmonitor/copyright
/var/lib/dpkg/info/indicator-sysmonitor.list
/var/lib/dpkg/info/indicator-sysmonitor.md5sums
Not me@Not me-OptiPlex-GX60:~$ [/I][/B]

So the locate command worked after all  with the right name that is. ha ha.

---

### Post by deconstrained on 2011-05-10
*apt-cache search* and bash completion are your friends.

---

### Post by Paqman on 2011-05-10
> **Not unique said:**
> I can't get it to load at start by adding it to my start-up applications list because I can't find it in Bin or Usr/Bin or anywhere else I looked???


On Linux you don't need to know the full path to the file to launch it.

For example, the path to the Firefox executable is "/usr/bin/firefox", but to launch it you just use "firefox". The system is clever enough to sort it out for you.

---

### Post by Not unique on 2011-05-10
Yes but I was trying to add it manually to the start-up list so I don't have to re-start every time round(very annoying).

---

### Post by Paqman on 2011-05-10
> **Not unique said:**
> Yes but I was trying to add it manually to the start-up list so I don't have to re-start every time round(very annoying).

You still don't need the full path. Just the name will do.

---

### Post by compmodder26 on 2011-05-10
> **Paqman said:**
> You still don't need the full path. Just the name will do.

Just to clarify, you don't need the full path so long as the program is in a directory that is part of your $PATH environment variable.

You can open a terminal and type the following to see what directories are part of your path:

```
echo $PATH
```

---

### Post by Rubi1200 on 2011-05-10
> **Not unique said:**
> **_SORTED !!!_**

I tried again with different spellings, grammar etc and wouldn't you know this worked:


[B][I]Not me@Not me-OptiPlex-GX60:~$ which indicator-sysmonitor
/usr/bin/indicator-sysmonitor
Not me@Not me-OptiPlex-GX60:~$ locate indicator-sysmonitor
/home/Not me/.indicator-sysmonitor.json
/home/Not me/Desktop/indicator-sysmonitor.desktop
/usr/bin/indicator-sysmonitor
/usr/share/applications/indicator-sysmonitor.desktop
/usr/share/doc/indicator-sysmonitor
/usr/share/doc/indicator-sysmonitor/changelog.Debian.gz
/usr/share/doc/indicator-sysmonitor/copyright
/var/lib/dpkg/info/indicator-sysmonitor.list
/var/lib/dpkg/info/indicator-sysmonitor.md5sums
Not me@Not me-OptiPlex-GX60:~$ [/I][/B]

So the locate command worked after all  with the right name that is. ha ha.
Glad you got things worked out, nice one :-)

---

