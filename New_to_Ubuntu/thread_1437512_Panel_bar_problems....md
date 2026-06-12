---
title: "Panel bar problems..."
date: 2010-03-24
forum: New to Ubuntu
---

### Post by Robby94LS on 2010-03-24
[SIZE=4]**Resolved** [/SIZE]


Hey guys! I am new to Linux. I installed Ubuntu via image CD and internet. It took me a while to get my broadband card connected (I used an Ethernet connection at work for installation) but was able to do so from what I found and downloaded on this forum. 

I was enjoying using it when I tried to edit some visual preferences. I set the panel or task bar to "auto hide" because I have a smaller monitor and it was cumbersome when web surfing. Now it seems to be gone for good. :( I searched here and came across some good articles but nothing I tried seemed to work. 

[http://ubuntuforums.org/showthread.php?t=1389891](http://ubuntuforums.org/showthread.php?t=1389891)

I tried what was in this thread which leads me to believe I have more of a problem. Alt + F2 is not doing anything. In addition to that when I ctrl + alt + del to shut down (all I can do without the bar) I get the equivalent to an illegal operation msg in Windows.  I also tried looking for the configurations folder but could not find it. All I can think of is to reload Ubuntu from scratch. #-o Any help or suggestions are much appreciated. Thanks.

---

### Post by ankspo71 on 2010-03-24
Hi,
Do you have access to the terminal?
One way to reset your default theme and theme preferences is to use the move command.
```
mv .gconf bkp.gconf
```That is equivalent renaming the folder for backup purposes.
Now all you need to do now is reboot. 
IF you can still browse your system you can also easily do this by renaming the hidden folder named .gconf in your home directory to bkp.gconf. You can use Ctrl+H to reveal hidden folders.
Hope this helps.

---

### Post by Robby94LS on 2010-03-24
Thank you so much! I actually figured it out! You and the thread I linked in mentioned commands but I Couldn't find my way to the terminal. I was able to access it by right clicking the desktop, clicking on "create launcher," putting the command in the command box, naming it and launching it from the desktop. (for future reference for searchers)

---

### Post by ankspo71 on 2010-03-24
I forgot to mention that the command I gave also resets some of the applications that have chosen to store some of their settings in that folder. I'm glad you got the problem fixed. ;)

---

