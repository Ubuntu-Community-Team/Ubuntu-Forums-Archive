---
title: "Delete recent history"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by trikster_x on 2011-06-09
I recently upgraded to 11.04 and I was wondering how to clear the recent history items on the files and folders page of the new unity desktop.  It seems like this should just be a simple .xml file I need to modify, but I can't figure out what it is called.  I would prefer not to install Ubuntu Tweak, since I like to minimize access to core system functions on my computers, just in case.  That means learning to do things the old fashioned way sometimes.

---

### Post by wildmanne39 on 2011-06-09
> **trikster_x said:**
> I recently upgraded to 11.04 and I was wondering how to clear the recent history items on the files and folders page of the new unity desktop.  It seems like this should just be a simple .xml file I need to modify, but I can't figure out what it is called.  I would prefer not to install Ubuntu Tweak, since I like to minimize access to core system functions on my computers, just in case.  That means learning to do things the old fashioned way sometimes.Hi, this is what you are looking for.
[http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/](http://www.omgubuntu.co.uk/2011/05/activity-log-manager-for-zeitgeist-lets-you-blacklist-files-and-apps-delete-your-history-more/)

---

### Post by trikster_x on 2011-06-09
@wildmanne39:

While that looks extremely useful for most people, I prefer to not use programs that provide an easy to use interface when changing the way a system operates.  I actually found a post on a thread which enabled me to come up with a simple script that I can hide anywhere and only use it when I want something removed from my history:

```

#! /bin/bash

DELPATH=/home/YOUR_USERNAME/.local/share

rm $DELPATH/recently-used.xbel
touch $DELPATH/recently-used.xbel
rm $DELPATH/zeitgeist/activity.sqlite
zeitgeist-daemon --replace

```

Now I am able to remove my history with a double-click.  Eventually I might figure out how to manipulate the .xbel file or just have a script create incremental back-ups to be able to delete only the items I absolutely don't want in history.

---

