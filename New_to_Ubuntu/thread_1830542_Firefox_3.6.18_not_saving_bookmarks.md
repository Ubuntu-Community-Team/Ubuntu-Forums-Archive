---
title: "Firefox 3.6.18 not saving bookmarks"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by _kate_ on 2011-08-21
Hi. I can't seem to save a bookmark to save my life anymore. I am running Firefox 3.6.18 on my machine. Will be happy to answer any questions which will help diagnose & solve this problem. Thank you in advance.

---

### Post by SoFl W on 2011-08-21
What happens when your type "ctrl-D"?
I think  3.6.20  is the latest 3.x.x

---

### Post by thatguruguy on 2011-08-21
Question #1: Why are you still running Firefox 3.6?

Can you access the bookmarks menu?  If so, you can always try making a backup of your current bookmarks, and then deleting your local profile.  Your local profile is available in your "home" directory in a hidden folder called ".mozilla".  Press ctrl+h in nautilus to show your hidden files and directories. Just delete the whole .mozilla directory.  The directory will be recreated when you open firefox again, and you can recreate your existing bookmarks by recovering from your backup.

---

### Post by dniMretsaM on 2011-08-21
Try updating to the latest stable version of FF.

---

### Post by Brushstroke on 2011-08-21
I have a hunch you are running 10.04 Lucid Lynx still. A lot of people have reverted back because they don't like Unity. One thing that kind of sucks about running Lucid is that it comes with Firefox 3.6.x, which is outdated. 

Run these commands in the Terminal: 

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
sudo apt-get upgrade
```And that will upgrade you to the latest version of Firefox. Your problem with Firefox not saving your bookmarks might be fixed if you do this.

---

### Post by SoFl W on 2011-08-22
> **Brushstroke said:**
>  One thing that kind of sucks about running Lucid is that it comes with Firefox 3.6.x, which is outdated. 

But [still supported]("https://www.mozilla.com/en-US/firefox/all-older.html").  3.6.20 was released last week.  The latest version has nothing to do with her bookmark problem.

---

### Post by lovinglinux on 2011-08-24
> **thatguruguy said:**
> Question #1: Why are you still running Firefox 3.6?

Can you access the bookmarks menu?  If so, you can always try making a backup of your current bookmarks, and then deleting your local profile.  Your local profile is available in your "home" directory in a hidden folder called ".mozilla".  Press ctrl+h in nautilus to show your hidden files and directories. Just delete the whole .mozilla directory.  The directory will be recreated when you open firefox again, and you can recreate your existing bookmarks by recovering from your backup.

Please don't recommend deleting the entire profile just because of bookmarks issues. It is totally unnecessary and will make the user restore passwords, extensions, settings and so on.

The bookmarks are stored in the file *places.sqlite* under you Firefox profile folder. You can find it inside ~/.mozilla/firefox. Removing that file from your profile should fix most bookmarks issues. Make sure to close Firefox first.

You can restore your bookmarks, by opening the bookmark manager, then clicking "Import & Backup >> Restore" and selecting the latest backup.

---

### Post by BoundaryValueProblems on 2011-08-24
This happened to me too today.  The problem was that I kept using Firefox 3.6.18 after my system updated it to 3.6.20.  So, in my case, it worked after I quit ff 3.6.18, and restarted ff, which is now 3.6.20.
So, you may want to quit the current Firefox session and restart it before trying other remedies.

Best,
BVP

---

### Post by Nysha on 2011-09-10
I don't believe this problem is caused by using older 3.6.x versions (although it could be 3.6.x as a whole), since I started experiencing the same about a month and a half ago, probably under 3.6.18 (although I don't know the version for sure), and continued to see the same behaviour through updates right up to 3.6.22 a couple of days ago, always using the latest version installed on my system. I am, however, as Brushstroke suggested, using 10.04.

Oddly enough, following lovinglinux's advice did not delete my existing bookmarks and did resolve the problem. I'm now able to add bookmarks by dragging tabs, through right-click menus, and via Ctrl-D, none of which worked previously. Thankyou, lovinglinux. :)

---

### Post by lovinglinux on 2011-09-11
> **Nysha said:**
> I don't believe this problem is caused by using older 3.6.x versions (although it could be 3.6.x as a whole), since I started experiencing the same about a month and a half ago, probably under 3.6.18 (although I don't know the version for sure), and continued to see the same behaviour through updates right up to 3.6.22 a couple of days ago, always using the latest version installed on my system. I am, however, as Brushstroke suggested, using 10.04.

Oddly enough, following lovinglinux's advice did not delete my existing bookmarks and did resolve the problem. I'm now able to add bookmarks by dragging tabs, through right-click menus, and via Ctrl-D, none of which worked previously. Thankyou, lovinglinux. :)

You are welcome.

---

