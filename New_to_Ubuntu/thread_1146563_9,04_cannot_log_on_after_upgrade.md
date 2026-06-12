---
title: "9,04 cannot log on after upgrade"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by koolkev on 2009-05-02
I tried the upgrade last night. Had a fight walked away and came back to a machine that boots to the logon screen(very nice graphic) and when I log in the accounts including admin I get a screen whith the tan color but no features/toolbars. 

I have a dell inspiron 530 I think I was at 8.10 and not having any particular problems. 

I can get falesafe.

when i did sudo shutdown now (to get out of falesafe)and password I got a blue screen with several options on a recovery menue. 

I choose dpkg. to repair broken packages. 

It took me to myphp??? I choose yes

At another nother step (I forget the promp) and I was at upgrade. Yay.

now tracker applet won't go away. I got 'there was an error while performing indexing index corrupted.'  "reindex all contents, cancel, or ok. Any option doesn't appear to start a process to recover just presents a new similer error. 

I shut down and powered back on 

after a few minutes tracker error came back

I used this thread to repair this(after reboot because no internet connection which reboot restored.)

[http://ubuntuforums.org/showthread.php?t=1135629&highlight=using+tracker](http://ubuntuforums.org/showthread.php?t=1135629&highlight=using+tracker)

then i did the sudo apt-get install tracker-utils (to restart tracking(I think(comments)))

So easy. So fun.

---

