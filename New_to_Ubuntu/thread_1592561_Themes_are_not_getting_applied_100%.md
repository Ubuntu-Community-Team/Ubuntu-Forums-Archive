---
title: "Themes are not getting applied 100%"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by getut on 2010-10-10
I've been running Maverick since early late alpha and am having issues with themes not getting applied. Window decorations are there but panels and firefox do not get themed.

I posted a question about this about a month back and some kind soul told me killing gnome-setting-daemon and then restarting it would get themes to completely apply. It does. But I assumed this was a bug and that it would be fixed before release day for Maverick. Well it is release day and I still have the issue.

Curiously enough I have have it times 4. I have 3 Core I7 laptops and 1 Core I7 desktop all doing exactly the same thing. Some worse than others. My Core I7 desktop does it almost every reboot.

All 4 of the machines were installed at some point during the beta process. With whatever nightly CD there was for Maverick. All 4 are 64 bit desktops with various Nvidia graphics chipsets and all 4 have SSD's.

I assumed that since I was having the problem on 4 different machines that this was a widespread problem and therefore would be fixed quickly. I created a bug report, [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670) but only 1 other person has added on it to it.

I have also searched the forums and can't find anyone else having the issue. I can only assume that it is something I am doing during the install that makes machines I have touched have this problem.

---

### Post by getut on 2010-10-14
3 day out Bump... can anyone help?

---

### Post by andrewthomas on 2010-10-14
> **getut said:**
> 

I have also searched the forums and can't find anyone else having the issue. I can only assume that it is something I am doing during the install that makes machines I have touched have this problem.
That's funny, it seems that I have seen this exact question at least five times.

---

### Post by Sealbhach on 2010-10-14
Are these the Ubuntu system themes? Maybe try, as an experiment to add a theme from Gnome Look, log out and log back in again...

---

### Post by ankspo71 on 2010-10-15
Hi,
This problem is going around a bit lately. 

Try doing what this post says to do then log out then log back in:
[http://ubuntuforums.org/showthread.php?t=885038](http://ubuntuforums.org/showthread.php?t=885038)

If that doesn't help, see the post made by "serfcx" here:
[http://ubuntuforums.org/archive/index.php/t-688522.html](http://ubuntuforums.org/archive/index.php/t-688522.html)

If neither of them help, then try what I said in this post:
[http://ubuntuforums.org/showpost.php?p=9958138&postcount=3](http://ubuntuforums.org/showpost.php?p=9958138&postcount=3)

Hope this helps.

---

### Post by getut on 2010-10-15
> **ankspo71 said:**
> Hi,
This problem is going around a bit lately. 

Try doing what this post says to do then log out then log back in:
[http://ubuntuforums.org/showthread.php?t=885038](http://ubuntuforums.org/showthread.php?t=885038)

If that doesn't help, see the post made by "serfcx" here:
[http://ubuntuforums.org/archive/index.php/t-688522.html](http://ubuntuforums.org/archive/index.php/t-688522.html)

If neither of them help, then try what I said in this post:
[http://ubuntuforums.org/showpost.php?p=9958138&postcount=3](http://ubuntuforums.org/showpost.php?p=9958138&postcount=3)

Hope this helps.

Thank you for the assistance. It still isn't fixing the issue, but your post has brought me hope and I'm glad to see that my last post to the ubuntu bug tracker doesn't seem to be far off base. I posted 10/11 in my bug report 625670 that the problem seems to happen MUCH more "reliably" on my fastest PC. A 6 core I7 with SSD. My observation, mostly non-technical, was this was a timing issue or race condition made worse by the fast machine. Your workaround of delaying the start seems to indicate the same thing.

AndrewThomas's insinuation that I had not searched is not true. I saw some of those other issues that you post ankspo, but I ruled those out as being different problems because ***MY*** gnome-settings-daemon does NOT crash and it does NOT fail to start. It is there running happily with no errors at all yet I have to end it and restart it manually to get my theme to apply anywhere near 100% and it sometimes doesn't even do it then. If I kill gnome-settings-daemon and then start it from the console, not a single error goes by.

Also, best I can tell, your fix of delaying the start of g-s-d seems to fail on my machine because mine does not fail to start. It is already there running but not theming anything.

---

### Post by juliobahar on 2010-10-15
> **getut said:**
> 
Also, best I can tell, your fix of delaying the start of g-s-d seems to fail on my machine because mine does not fail to start. It is already there running but not theming anything.

Can you explain what do you mean by "gnome-setting-daemon is running but not theming"?

Probably by attaching a screenshot of your desktop

---

### Post by getut on 2010-10-15
> **juliobahar said:**
> Can you explain what do you mean by "gnome-setting-daemon is running but not theming"?

Probably by attaching a screenshot of your desktop

Screenshots attached. Most noticeable in the gnome panels.

After a restart and logging in, the panels and many other things are not themed. They are the default gnome theme. Most of the time, the window decorations are there and working though.

I can kill the running gnome-settings-daemon then start it again manually and most everything gets properly themed with my chosen settings.. but most of the time nautilus folders still doesn't get completely themed.

---

### Post by juliobahar on 2010-10-15
> **getut said:**
> Screenshots attached. Most noticeable in the gnome panels.

Try to make a new gnome session with a different username. See whether the problem persists. I'm out of ideas at the moment, have to dig deep into the gnome session and gnome-settings-daemon.

have you tried reinstalling gnome?

---

### Post by getut on 2010-10-16
> **juliobahar said:**
> Try to make a new gnome session with a different username. See whether the problem persists. I'm out of ideas at the moment, have to dig deep into the gnome session and gnome-settings-daemon.

have you tried reinstalling gnome?

Logging on with a second username causes this to happen 100% of the time. Logging on with the primary username seems to my newbie eyes to be related to the speed of the machine. The faster the PC, and thus the faster it gets to the desktop, the more likely the theme is to be incomplete when it gets there.
Like I said, I have 4 PC's all affected by this. 2 Core I7 laptops with SSD's, a Core I7 Desktop with SSD, and a Core 2 Duo desktop with SSD. The Core 2 Duo hardly ever does it, the 6 Core I7 desktop does it probaly 99.9% of the time. The laptops do it probably 95% of the time.

I don't think there is any software missing perse. I think there is a race condition where the faster machines are getting to the desktop before some other piece of the puzzle that is loading in parallel rather than series is not ready yet.

---

### Post by sandman6471 on 2010-10-16
[B][B][B]I'm not sure, I'm kind of a newbie myself. I've run linux mint and now ubuntu 10.10 and never had problem with themes. Either built in system themes or gtk+2 themes from gnome-look.org. I run compiz and have installed gtk-ch theme to help with applying the themes. Maybe you could try above theme application to see if it helps any. Just an idea, i'm not a linux guru by no means.


Linux is Great.....
Take Care Everyone.....[/B][/B][/B]

---

### Post by druhboruch on 2010-10-16
I experience the same problems.
In my case the first login after boot is OK.  When I logout and log back in my theme is messed-up.

Restarting gnome-settings-daemon fixes it until the next login.

---

### Post by getut on 2010-10-17
Please sign up on launchpad and tag this bug as affecting you if you are seeing this. So far it has not gotten developer attention or questions from us to give them more information.

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/625670)

---

