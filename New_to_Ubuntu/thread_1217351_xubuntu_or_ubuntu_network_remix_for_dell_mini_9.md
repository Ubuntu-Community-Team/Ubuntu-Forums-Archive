---
title: "xubuntu or ubuntu network remix for dell mini 9?"
date: 2009-07-19
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-07-19
Hello there,

The title is rather self-explanatory, but I was wondering which flavor would be more efficient for use on my netbook.  I know that xubuntu is for lower-performance systems, and I know little about the netbook remix.  I had XP installed on my mini 9 when I got it, so it wouldn't be a matter of switching from the remix to xubuntu.

Thanks for any and all suggestions.

--Red

---

### Post by snowpine on 2009-07-19
Hi Red, either will work fine on the Mini 9, it is just a question of personal preference. Both Xubuntu and Ubuntu Netbook Remix are the same "core" system, with a different user interface (Xfce vs. Gnome+netbook launcher). Performance should be about the same (the Dell Mini 9 is easily capable of running either). I personally do not care for the Remix interface (I prefer a traditional desktop to the "big icons"), so I would vote Xubuntu. Why not try both in Live mode and see which you prefer?

ps Here is a neat reference site for Ubuntu on the Mini: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by ugm6hr on 2009-07-19
My personal suggestion is to download and install the 9.04 Netbook Remix (NBR).  This is predominantly because it comes ready to be copied directly to a USB to be installed on the Mini.

Give it a go, and see how you like it.

I have recently installed xfce4 on top of the NBR with just a 74MB download in preference to the NBR / Gnome:
```
sudo apt-get install xfce4 xfce4-mixer
```

Just adjust the Sessions / Startup to remove some of the NBR rubbish from botting at startup.

Other options are to add some GTK / XFCE applications rather than Gnome ones (I am still using original Gnome apps perfectly well though). e.g. mousepad, xfce4-terminal, thunderbird (or other email), parcellite (clipboard) - more [here]("http://www.xfce.org/projects/")

Some further detail you might find useful re: XFCE
[http://ubuntuforums.org/showthread.php?p=7631053#post7631053](http://ubuntuforums.org/showthread.php?p=7631053#post7631053)
[http://ubuntuforums.org/showpost.php?p=7621935&postcount=13](http://ubuntuforums.org/showpost.php?p=7621935&postcount=13)

Main downside to XFCE: no easy access to Samba (Windows) shares.  But I use NFS for my FreeNAS home server, so no problems there.

---

### Post by mikeypc2006 on 2009-07-19
I run standard Ubuntu 9.04 on my Asus EEE 1000H without problems and my brother runs the same on his Dell Mini 9, also without problems.  Basically, bog standard Ubuntu will run happily on a netbook without problems.

---

