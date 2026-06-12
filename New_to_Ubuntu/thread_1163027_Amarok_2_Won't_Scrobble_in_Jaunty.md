---
title: "Amarok 2 Won't Scrobble in Jaunty"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by jpoRS on 2009-05-18
Hello,

Tried searching and got no results at all, which I found odd.

Anyway, I just did a fresh install of Jaunty and thus have been forced to make do with Amarok 2.  I wasn't happy about that to begin with, but now I discover that it won't scrobble to Last.fm for some reason.  Picks up radio fine, but no scrobbling.

I tried following [THIS]("http://webupd8.blogspot.com/2009/05/fix-amarok-2-and-lastfm-scrobbing-in.html") fix, but I got the following errors when try to leave Software Sources:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
```

And then:

```
An error occurred

The following details are provided:
[CODE]E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory

```[/CODE]

Followed by:

```
An error occurred

The following details are provided:
[CODE]E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

```[/CODE]

And then when I apt-get update:
```
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
```

. . . ?
Thanks,
jim

---

### Post by Didius Falco on 2009-05-18
Hi,

Open a Terminal and type ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
``` to make a backup copy of the file.

Then type```
gksudo gedit /etc/apt/sources.list
``` and copy/paste it to this thread. Put the code tags around it, please.

Then we can havea look at line 57 and see if the problem can be spotted.

Regards,

Didius

---

### Post by jpoRS on 2009-05-18
It is one of the lines I added after following the instructions at the link above.  I know it is them I just don't know why they won't work for me.

```
deb http://ppa.launchpad.net/ubuntu-experimental/ppa/ubuntu jaunty main deb-src http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty
deb-src http://ppa.launchpad.net/kubuntu-experimental/ppa/ubuntu jaunty
```

Thanks,
jim

---

### Post by jpoRS on 2009-05-18
Oo.  After posting I see that there are two items on one line. Fixed that but still get the following error on update:

```
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
```

?
jim

---

### Post by jpoRS on 2009-05-20
Anybody?

---

### Post by CatKiller on 2009-05-20
> **jpoRS said:**
> Oo.  After posting I see that there are two items on one line. Fixed that but still get the following error on update:

```
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
```?
jim

You probably don't need the source to the experimental Kubuntu packages anyway. Comment out the deb-src line (which is probably missing a main at the end).

Your experience may differ from mine, but I found the experimental Amarok to be really unstable, and it had forgotten how to read the tags of the files. So it was a choice of not scrobbling, or not knowing what it was playing for the short amount of time before it crashed. I decided to go back to not scrobbling, and I'd advise you to stay there and wait for a more thoroughly tested update too.

---

### Post by jpoRS on 2009-05-20
Bah!  Why on earth did they ruin the joy that was 1.4 with the misery that is 2.0?  Bah!  [/whining]

Thanks anyway.
jim

---

### Post by CatKiller on 2009-05-20
> **jpoRS said:**
> Bah!  Why on earth did they ruin the joy that was 1.4 with the misery that is 2.0?  Bah!  [/whining]


I'm pretty sure it's because of the KDE 4 stuff. It'll get there. I might even install Kubuntu in a couple of releases' time...

---

