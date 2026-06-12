---
title: "Error during installation"
date: 2018-06-06
forum: Networking &amp; Wireless
---

### Post by delfiler on 2018-06-06
[COLOR=#111111][FONT=Ubuntu]I am trying to install citadel and following their steps and everything goes fine until this pops up:

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]Dependencies: gcc -M -I/usr/local/ctdlsupport/include  -g -I/usr/local/ctdlsupport/include -I. -I ./include/  | sed -e 's!.o!.o /.o buildinfo!' > buildinfo[/FONT][/COLOR]
Compile: gcc -I/usr/local/citadel  -I/usr/local/ctdlsupport/include  -g -Wall -Wcast-qual -Wcast-align -Wstrict-prototypes -Wno-strict-aliasing -D_REENTRANT -pthread -I ./include/ -I/usr/local/ctdlsupport/include  -g -I/usr/local/ctdlsupport/include -I. -I ./include/ -DHAVE_CONFIG_H -DDIFF="/usr/bin/diff" -DPATCH="/usr/bin/patch" -c  -o buildinfo
LDFLAGS: -L/usr/local/citadel -L/usr/local/ctdlsupport/lib -Wl,--rpath -Wl,/usr/local/ctdlsupport/lib  -L/usr/local/ctdlsupport/lib

/usr/bin/install -c citserver /usr/local/citadel/citserver
/usr/bin/install -c citmail /usr/local/citadel/citmail
/usr/bin/install -c sendcommand /usr/local/citadel/sendcommand
/usr/bin/install -c base64 /usr/local/citadel/base64
/usr/bin/install -c setup /usr/local/citadel/setup
/usr/bin/install -c chkpw /usr/local/citadel/chkpw
/usr/bin/install -c chkpwd /usr/local/citadel/chkpwd
/usr/bin/install -c msgform /usr/local/citadel/msgform
/usr/bin/install -c ctdlmigrate /usr/local/citadel/ctdlmigrate
/usr/bin/install -c ./database_cleanup.sh /usr/local/citadel/database_cleanup.sh
/usr/bin/install -c ./migrate_aliases.sh /usr/local/citadel/migrate_aliases.sh
/bin/sh: 1: Syntax error: end of file unexpected
Makefile:209: recipe for target 'install-data' failed
make: *** [install-data] Error 2
 Citadel Easy Install is aborting. [COLOR=#111111][FONT=Consolas] The last few lines above this message may indicate what went wrong.[/FONT][/COLOR]
```

[COLOR=#111111][FONT=Ubuntu]And I have no clue what is wrong. so this might be too broad but it is the only lead i got
this is what i get when i run he installation of citadel [/FONT][/COLOR][https://paste.ubuntu.com/p/GFh2NcJ2th/](https://paste.ubuntu.com/p/GFh2NcJ2th/)[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by yapidumoac on 2018-06-07
> **delfiler said:**
> /bin/sh: 1: Syntax error: end of file unexpected

Maybe its a DOS format file and needs to be converted to [FONT=arial]Unix format using [/FONT][COLOR=#000000][FONT=Verdana][dos2unix]("https://en.wikipedia.org/wiki/Unix2dos")?[/FONT][/COLOR]

---

### Post by delfiler on 2018-06-07
well problem is solved citadel had a error in their installation script and the developers of citadel fixed it

---

