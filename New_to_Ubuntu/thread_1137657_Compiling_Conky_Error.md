---
title: "Compiling Conky Error"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by System Monitor on 2009-04-25
I get this error when I am trying to compile conky.

```
checking for XdbeQueryExtension in -lXext... no
configure: error: Could not find XdbeQueryExtension in -lXext

```

---

### Post by Tibuda on 2009-04-25
You really want to compile it, if you can install it from the ubuntu repositores? (I ask this because this is the "Absolute beginner" forum)

---

### Post by steve101101 on 2009-04-25
i would just install it using synaptic.

---

### Post by kevdog on 2009-04-25
Did you try enabling extra features?  Are you doing conky v1 or v2??

---

### Post by llamabr on 2009-04-25
Why would you compile this, rather than install from the repositories?

---

### Post by h4p0 on 2009-09-01
Maybe for enable extra feature...
I've got the same problem...tons of errors...
I tried many versions....always the same story... :(

$./configure --enable-xmms2 --disable-mpd
[....]
conky 1.7.0 configured successfully:

 Installing into:   /usr/local
 System config dir: ${prefix}/etc
 C compiler flags:   -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W
 Linker flags:       -Wl,-O1
 Libraries:         -lrt  -lm -lxmmsclient    -lX11   -lXext   -lXdamage -lXfixes   -lXft   -lglib-2.0  

 * X11:
  X11 support:      yes
  XDamage support:  yes
  XDBE support:     yes
  Xft support:      yes

 * Music detection:
  Audacious:        no
  BMPx:             no
  MPD:              no
  MOC:              yes
  XMMS2:            yes

 * General:
  math:             yes
  hddtemp:          yes
  portmon:          yes
  RSS:              no
  wireless:         no
  IBM:              no
  nvidia:           no
  eve-online:       no
  config-output:    yes

$make
[...]
xmms2.c:100: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
xmms2.c:180: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
xmms2.c:199: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
xmms2.c:233: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
xmms2.c: In function &#8216;update_xmms2&#8217;:
xmms2.c:291: error: &#8216;handle_curent_id&#8217; undeclared (first use in this function)
xmms2.c:291: error: (Each undeclared identifier is reported only once
xmms2.c:291: error: for each function it appears in.)
xmms2.c:293: error: &#8216;handle_playtime&#8217; undeclared (first use in this function)
xmms2.c:295: error: &#8216;handle_playback_state_change&#8217; undeclared (first use in this function)
xmms2.c:297: error: &#8216;handle_playlist_loaded&#8217; undeclared (first use in this function)
make[2]: *** [xmms2.o] Error 1
make[2]: Leaving directory `/home/h4p0/conky-1.7.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/h4p0/conky-1.7.0/src'
make: *** [all-recursive] Error 1

---

### Post by Bachstelze on 2009-09-01
> **h4p0 said:**
> 
$make
[...]
xmms2.c:100: error: expected ‘)’ before ‘*’ token
xmms2.c:180: error: expected ‘)’ before ‘*’ token
xmms2.c:199: error: expected ‘)’ before ‘*’ token
xmms2.c:233: error: expected ‘)’ before ‘*’ token
xmms2.c: In function ‘update_xmms2’:
xmms2.c:291: error: ‘handle_curent_id’ undeclared (first use in this function)
xmms2.c:291: error: (Each undeclared identifier is reported only once
xmms2.c:291: error: for each function it appears in.)
xmms2.c:293: error: ‘handle_playtime’ undeclared (first use in this function)
xmms2.c:295: error: ‘handle_playback_state_change’ undeclared (first use in this function)
xmms2.c:297: error: ‘handle_playlist_loaded’ undeclared (first use in this function)
make[2]: *** [xmms2.o] Error 1
make[2]: Leaving directory `/home/h4p0/conky-1.7.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/h4p0/conky-1.7.0/src'
make: *** [all-recursive] Error 1

You cut too low, please paste the whole output.

---

### Post by mc4man on 2009-09-01
You may want to post what release of ubuntu your using and if using that release's repo libs of xmms2

While I'm using hardy with it's slight limitations, due to a few mods  I'm able to build package sets of both the jaunty source and karmic source versions of xmms2 (xmms2.0.5DrLector and xmms2.0.6DrMattDestruction respectively
 
Doing a quick compare to the installed xmms2 libs needed for conky (only 3 xmms2 packages needed) with versions 1.6.x and 1.7.x shows the exact errors your seeing if using the 0.5DrLector version while trying to build the 1.7.x conky.

Using the needed lib packages from 0.6DrMattDestruction then conky 1.7.2 builds fine with --enable-xmms2

So you should be able to build a 1.6.x conky without issue if your xmms2 version is 0.5....

For a 1.7.x conky you'd either need a patch (if possible) for one or more of the xmms2 libs or update your xmms2 install to 0.6... one way or the other. 
( or wait for karmic to release.

If you were to decide to build a 0.6 version of xmms2 you may want to apply  the debian.diff and build off of the debian/rules due to the extreme number of libs and plugins produced. You may not need or want them all installed (i count 68 .debs produced from the 0.6 build

---

### Post by ngaro on 2010-01-24
> **System Monitor said:**
> I get this error when I am trying to compile conky.

```
checking for XdbeQueryExtension in -lXext... no
configure: error: Could not find XdbeQueryExtension in -lXext

```

You are missing a lib: ```
aptitude install libxext-dev
```

---

### Post by dmillerct on 2010-01-24
You can get the 1.7.2 rev with all features (imlib, ciaro, lua, etc.) enabled here:

[http://old.getdeb.net/app/Conky]("http://old.getdeb.net/app/Conky")

---

