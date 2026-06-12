---
title: "HOWTO crank-0.1.4 and gtk 1.2"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by mwjones on 2010-05-24
**Synopsis:**
Get the crank source and some old .deb packages from jaunty.
```
sudo dpkg -i --force-architecture <package.deb>
```

**Process:**
[LIST=1]
[*]Download and install the following packages, in order:
[LIST=1]
[*][http://packages.ubuntu.com/jaunty/libgtk1.2-common](http://packages.ubuntu.com/jaunty/libgtk1.2-common)
[*][http://packages.ubuntu.com/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/jaunty/libglib1.2ldbl)
[*][http://packages.ubuntu.com/jaunty/libglib1.2-dev](http://packages.ubuntu.com/jaunty/libglib1.2-dev)
[*][http://packages.ubuntu.com/jaunty/libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2)
[*][http://packages.ubuntu.com/jaunty/libgtk1.2-dev](http://packages.ubuntu.com/jaunty/libgtk1.2-dev)
[/LIST]
[*]Download and build crank:
[LIST=1]
[*][http://crank.sourceforge.net/downloads.html](http://crank.sourceforge.net/downloads.html)
[*][FONT="Courier New"]tar zxvf crank-0.1.4.tar.gz[/FONT]
[*][FONT="Courier New"]cd crank-0.1.4/[/FONT]
[*][FONT="Courier New"]./configure[/FONT]
[*][FONT="Courier New"]make[/FONT]
[/LIST]
[*]Add plugins:
[LIST=1]
[*]sudo mkdir /usr/local/lib/crank
[*]sudo ln -s $(pwd)/plugin-src /usr/local/lib/crank/plugins
[/LIST]
[/LIST]

**Notes:**
[LIST]
[*]If you've already run configure, you'll need to clear out the results. Certain findings get cached, which can cause inaccurate results.
[*]You may need other packages; take a look at the dependencies (and their dependencies).
[/LIST]

---

