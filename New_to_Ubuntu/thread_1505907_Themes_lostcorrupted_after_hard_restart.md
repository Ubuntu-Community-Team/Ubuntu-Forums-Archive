---
title: "Themes lost/corrupted after hard restart"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Metrop021 on 2010-06-09
Not exactly sure what happened here, but my comp went into standby overnight (for some reason the standby timer reset to default, thought i had it off), and i was unable to get out of standby (this is the reason i had the timer set to 'never' in the first place). So i went ahead and hard restarted. When i booted back up, i had a strange theme as my theme, compiz still worked, but the theme was strange. It seems all of my themes got corrupted/deleted or something (see picture below). I tried to install new themes but they don't seem to applied 100% (the status icons at the top right don't change), and they can't be seen in the appearance menu. Then if i try to install that same theme again, I get the error message "Impossible to move a repertoire onto another". Any ideas?


[http://img814.imageshack.us/img814/5127/capture1.png](http://img814.imageshack.us/img814/5127/capture1.png)

---

### Post by cariboo on 2010-06-09
Try booting from the Live CD and once at the desktop, open a terminal and type:

```
sudo fsck -a /dev/sda1
```

The above command should repair any corrupted files. Substitute your partition for the one in the example above.

---

### Post by Metrop021 on 2010-06-09
I did that, the output said all clean. But the theme problem persists... it's not a functionality thing or anything important but it still bugs me.

---

### Post by Metrop021 on 2010-06-09
quick update, i downloaded the default ambience theme from somewhere and it seems to have applied properly except for the status icons at the top right. and i still can't apply the themes i 'installed' because of the cannot overwrite repository or whatever error

---

### Post by Metrop021 on 2010-06-10
i settled for a temporary fix (i chose a theme that matched the status icons, so it doesnt look out of place anymore).

but if anyone stumbles across this thread and has an idea that'd be great

---

### Post by Metrop021 on 2010-06-10
ah well just in case anyone ever digs up this thread, it looks like that hard restart managed to mess up a lot of things because i started getting a lot of new error messages. so i just decided to backup and reinstall 10.04.

---

