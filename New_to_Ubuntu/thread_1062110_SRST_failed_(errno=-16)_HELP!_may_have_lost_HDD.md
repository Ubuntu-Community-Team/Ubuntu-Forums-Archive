---
title: "SRST failed (errno=-16) HELP! may have lost HDD"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by bjnueva8623 on 2009-02-06
I was trying to install Ubuntu but kept getting the "SRST failed (errno=-16)" message. I tried switching the IDE setting to RAID, but it didn't work. I can't even log in to WinXP. I think I lost everything. 

My system specs:

Pentium 4 
2.80 GHz 
1 GB of RAM
300 GB HDD
NVIDIA 6600 series

---

### Post by bjnueva8623 on 2009-02-06
Bump.

---

### Post by bjnueva8623 on 2009-02-06
I may have posted this in the wrong forum, but I am not able to post in the Installation & Upgrades forum for some reason. 

Can anyone help? This is a huge step backwards. I was really looking forward to using Ubuntu and now I've lost both my HDD as well as my WinXP OS. Hope someone can help.

---

### Post by furnace on 2009-02-15
Same error here. I got back in to Vista by booting from the Vista CD, getting into the recovery console from the "repair my computer" menu, and running "bootrec /fixmbr".

It will be similar for XP but you'll have to Google for the exact command. Lost of results for [Windows XP Fix MBR]("http://www.google.co.uk/search?hl=en&q=Windows+XP+Fix+MBR&btnG=Google+Search&meta=").

---

### Post by Azazel on 2009-02-25
This happened to me because i connected my IDE cable backwards. I did it on purpose to see what would happen, do you think you might have done that on accident? Also, when the command line came up (i think it was called initrams or something like that) i just typed exit and it continued with normal boot. As for your windows, I don't know what to do about that.

hope this helps!


Edit:

You might also want to check out this thread [http://ubuntuforums.org/showthread.php?t=1068463&highlight=srst+failed]("http://ubuntuforums.org/showthread.php?t=1068463&highlight=srst+failed")

---

