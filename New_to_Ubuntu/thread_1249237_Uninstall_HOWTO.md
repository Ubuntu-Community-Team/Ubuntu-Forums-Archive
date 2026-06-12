---
title: "Uninstall HOWTO"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by F411en on 2009-08-25
i've installed WeeChat using that three packages :
1 [http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-core_0.3.0-1~dev20090825_i386.deb](http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-core_0.3.0-1~dev20090825_i386.deb)
2 [http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-curses_0.3.0-1~dev20090825_i386.deb](http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-curses_0.3.0-1~dev20090825_i386.deb)
3 [http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-plugins_0.3.0-1~dev20090825_i386.deb](http://debian.flashtux.org/dists/stable/main/binary-i386/weechat-dev-plugins_0.3.0-1~dev20090825_i386.deb)

So ... now i want uninstall it . But how ? Packages are not listed in synaptic .
Also :

```
sudo apt-get remove weechat
``` and ```
sudo apt-get remove weechat -curses
``` doesn't work .

---

### Post by kansasnoob on 2009-08-25
Are you certain that if you open synaptic and click on Search (not quick search or rebuilding search) and search for weechat nothing shows up?

You might try:

```
sudo apt-get --purge remove weechat*
```

The * is a wildcard so it should remove anything beginning with weechat.

---

### Post by F411en on 2009-08-25
> **kansasnoob said:**
> Are you certain that if you open synaptic and click on Search (not quick search or rebuilding search) and search for weechat nothing shows up?

You might try:

```
sudo apt-get --purge remove weechat*
```

The * is a wildcard so it should remove anything beginning with weechat.

Not working .
```
sudo apt-get --purge remove weechat-curses
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package weechat-curses is not installed, so not removed
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by kansasnoob on 2009-08-25
But you ran the command:

```
sudo apt-get --purge remove weechat-curses

```

Not:

```
sudo apt-get --purge remove weechat*
```

Copy-n-paste that exact command with the * and post the output.

---

### Post by miklcct on 2009-08-25
```

sudo apt-get remove weechat-dev-{core,curses,plugins}

```

---

### Post by nns2006 on 2009-08-25
Are you able to see it in Application>>Add/Remove>>Installed?
See if your program is listed there.

---

### Post by F411en on 2009-08-25
> **kansasnoob said:**
> But you ran the command:

```
sudo apt-get --purge remove weechat-curses

```

Not:

```
sudo apt-get --purge remove weechat*
```

Copy-n-paste that exact command with the * and post the output.

Not worked .

> **miklcct said:**
> ```

sudo apt-get remove weechat-dev-{core,curses,plugins}

```

Thanks a lot . Worked .

---

