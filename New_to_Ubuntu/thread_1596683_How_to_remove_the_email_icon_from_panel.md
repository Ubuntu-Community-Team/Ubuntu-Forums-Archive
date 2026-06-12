---
title: "How to remove the email icon from panel"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by zeroandone on 2010-10-14
I don't need the stupid email icon showing on my panel of Ubuntu 10.10, so how do I remove it? When I right-click on it and choose "Remove from Panel", it removes the whole Indicator Applet which also contains the volume control. I do not want to remove my volume control, just want to remove the email icon. It drives me nuts for not being able to do such a simple task.

Thanks,

Jeffrey

---

### Post by Ben Page on 2010-10-14
I don't exactly know how to remove the icon, but if you don't use the Evolution Mail client, remove it and the icon should be removed with it. Otherwise, I would look in the email client for option to remove the panel icon...

---

### Post by beew on 2010-10-14
YOU CAN'T WITHOUT ALSO REMOVING THE VOLUME ICON! I know that is crazy, but true. You can remove both by removing the indicator applet from the panel.

If you remove Evolution like "Ben Page" said you will also remove the volume icon. Try adding the indicator applet to the panel after removing evolution and you would see just a blank. I tried that (I have no need for stupid mail clients, I just log in to my email accounts to check email) Moreover you can't really *remove* evolution in the sense of removing Evolution data  and maybe a few other things without removing half of genome itself. You can only remove the actual software. It is stupid.

There is however an obscure way to get the volume icon  to show up without using the indicator applet.  You may find it helpful

[URL="http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/"]http://ubuntugenius.wordpress.com/2010/05/04/restore-missing-volume-button-to-system-tray-after-upgrade-to-ubuntu-10-04/

[/URL]

---

### Post by akoskm on 2010-10-14
What about removing the
```

indicator-messages

```
package?

---

### Post by Rex Bouwense on 2010-10-14
Did a search and found this [http://ubuntuforums.org/showthread.php?t=1495975&highlight=Remove+email+icon](http://ubuntuforums.org/showthread.php?t=1495975&highlight=Remove+email+icon).  It may be of interest.  Enjoy.

---

### Post by JustinR on 2010-10-14
> **Rex Bouwense said:**
> Did a search and found this [http://ubuntuforums.org/showthread.php?t=1495975&highlight=Remove+email+icon](http://ubuntuforums.org/showthread.php?t=1495975&highlight=Remove+email+icon).  It may be of interest.  Enjoy.

Hi,

It's completely removable:

```

sudo apt-get purge indicator-messages

```

To remove the Username-Status updater thing:
```

sudo apt-get purge indicator-me

```

Good Luck!

The people above should know better - Ubuntu is a huge set of packages - each one can be removed!

---

### Post by mrgavindb on 2010-10-27
```

sudo apt-get purge indicator-messages

```

That worked for me. Thank you very much.

---

### Post by zeroandone on 2010-11-08
> **JustinR said:**
> Hi,

It's completely removable:

```

sudo apt-get purge indicator-messages

```

To remove the Username-Status updater thing:
```

sudo apt-get purge indicator-me

```

Good Luck!

The people above should know better - Ubuntu is a huge set of packages - each one can be removed!

It worked like a charm! 

Thank you sooooo much Justin.

---

### Post by bhishan on 2010-11-26
> **JustinR said:**
> 

```

sudo apt-get purge indicator-messages

```

To remove the Username-Status updater thing:
```

sudo apt-get purge indicator-me

```



Worked like a charm!

---

### Post by XSAlliN on 2010-12-07
Good tip ;). 

They shouldn't make dependencies by packing specific applications with main components - forcing you to keep software you don't want... One of the main bonuses of Linux was modularity, as in more freedom in your options - yet with any new version of Ubuntu, they keep limiting your freedom when it comes tho the options you chose, being force to keep extra "bloat-ware" on your OS.

If they keep up with this, a future version of Ubuntu - may offer even more limitations than Windows...:frown: - and guess at that time, will have to look for alternatives - lucky, we have so many Linux distributions to chose from... so that won't be a problem. It's just sad to see Ubuntu, a distribution which most from here used it for so long - going the wrong way...

---

