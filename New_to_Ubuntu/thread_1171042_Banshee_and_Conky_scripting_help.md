---
title: "Banshee and Conky scripting help"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Ryuki_NdranC on 2009-05-26
**_Disclamer_**

    I'm looking for help here, i'm not claiming that i created this scripts, they were downloaded from this same forum from other users who made them, or that i know any python/bash/conky programing, i'm just a guy (who is starting into collage studying computation), and happens to know a tiny little bit of general knowledge regarding this subjects and tried to modify some scripts to make them work to his needs.

**_The Problem_**

    I downloaded Mirav2 theme extra ".conkyrc" and i decided to make the "Now Playing" part of the conky work with banshee instead of mpd. After some reading i noticed that things like (if_running banshee-1) or even (dbus equivalent to it) don't prevent conky starting banshee unintentionally. I saw this guy idea about a wrapper to the dbus script itself but the program was intended to output a single line of info.

    To make a long story short i made individual wrappers for each queary, modified the (banshee.getPosition) and (banshee.getLength) parts to make them show a formated time (00:00), and downloaded another script that could output a current time bar. Now i know that maybe i could join the bar script and the main script into one but i haven't done it yet. The problem really is that everything worked just fine, i managed to make every single part of the Mirav2 conky script (status, artist, title, album, current time, length and bar) with banshee put my resources sky rocket to almost 50% - 60% while running banshee, and 30% - 50% while banshee is off. I have an Intel Core 2 Duo 2.4GHz and running the MPD version of that conky i get 3% with no music and 5% with music and sonata (even with compiz). I think i get an idea of what is causing that much bloat on the pc, all those scripts and python running each second querying dbus.

**_The Question_**

    Is this the final point? Is there a way reduce the resource hog part and still work? Like i said, i learned the basics of python yesterday while trying to modify the script, so i probably created some unnecessary lines of code here and there (not that they were many).

    I would be really appreciated if someone with better experience (and knowledge) could take a look into what i have, and make some suggestions.

**_The Scripts_**

    All scripts look in ~/Desktop for the things they need (like the wrappers), so i made a tar and i recommend to extract it all in the ~/Desktop, unless you want to change the path in each script.

    The wrappers are all named "bs_query" (like bs_artist bs_bar bs_album)

    The two main supporting scripts are the "bs_conky" (for everything but the bar) and "bs_conky2" for the bar alone.

    conkyrc_mpd is the modified .conkyrc

**_[Download]("http://www.mediafire.com/?xgijozbjl1t")_**

---

