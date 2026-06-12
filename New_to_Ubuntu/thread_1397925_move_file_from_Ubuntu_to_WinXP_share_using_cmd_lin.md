---
title: "move file from Ubuntu to WinXP share using cmd line"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Blackhood on 2010-02-03
I need to come up with a script that will move a file from my Ubuntu download folder to a windows share.

The equivalent Windows batch file would look like this:

```

@echo off
move %1 \\server\share\folder

```

I grew up in DOS and have played with Linux off and on but always go back because I get stuck on something that *I* cant do.

Any and all help is appreciated!

---

### Post by jken146 on 2010-02-04
[http://www.novell.com/coolsolutions/feature/11666.html](http://www.novell.com/coolsolutions/feature/11666.html)

---

### Post by Blackhood on 2010-02-04
> **jken146 said:**
> [http://www.novell.com/coolsolutions/feature/11666.html](http://www.novell.com/coolsolutions/feature/11666.html)

Ok, I read through that, stripped it down, looked in a few other places, and came up with this:

```
smbclient //dvr/transfers -U=Administrator%secret -c "put $1"
```

This does exactly what I need.  But only from the terminal.

What I am trying to do is associate the script with .torrent files in Firefox.  When I download a .torrent file the script should copy it automatically to the //dvr/transfers share where a running bittorrent client is scanning and auto loading.

In the terminal it works fine. If I have an existing .torrent file I type:

```
movetorrent.scr whatever.torrent
```

and it moves the file over and it gets loaded automatically.  But this doesn't occur when I set Firefox to use the script on .torrent files I download.

Any ideas?

---

