---
title: "An Improvement in Graphics 11.04 Classic Mode"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by OldBoy44 on 2011-07-15
This thread refers to previous thread marked as solved -
[http://ubuntuforums.org/showthread.php?t=1797730](http://ubuntuforums.org/showthread.php?t=1797730)

By inserting 20 as variable within Link quoted in #7 I was trying to gain some consistency in graphics improvement -
This is the link I am referring to -
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

I now find that all six Users correctly log on to a higher graphics mode however after six or seven seconds, the Top Panel reverts to a lower quality (no effects) type mode. The graphics on the desktops stays on higher graphics mode.

It appears that I may have "broken" something - :(
Graphics Radeon HD5770 HDMI Proprietary Driver.

Does anyone have any suggestions ? Perhaps a command that reverts setting to original which may then allow me to start again. If you are still around wildmanne39 I apologize for being a pain in the neck. 

- :(

---

### Post by wildmanne39 on 2011-07-15
Hi, if it looks like windows 95 theme look at this link.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by OldBoy44 on 2011-07-15
Yes, I think that is the Link I was referring to.

You've already pointed me in the right direction wildmanne39, I can't expect much more from you, you've already helped a lot!

---

### Post by wildmanne39 on 2011-07-15
> **aussiebean said:**
> Yes, I think that is the Link I was referring to.

You've already pointed me in the right direction wildmanne39, I can't expect much more from you, you've already helped a lot!Hi, I just realized I gave you the same link I was thinking of another but I can not find it.

---

### Post by OldBoy44 on 2011-07-15
Both Top Panel and Desktop were working pretty well with a delay, but like a fool I tried to improve things - :(

---

### Post by OldBoy44 on 2011-07-16
Bump! with thanks - :)

---

### Post by OldBoy44 on 2011-07-17
A not too hopeful bump!  :)

---

### Post by wildmanne39 on 2011-07-17
> **aussiebean said:**
> A not too hopeful bump!  :)Hi, is it not possible to change the delay back to the setting that was working better? 

What is the exact problem now the same thing or did it create another issue?

---

### Post by OldBoy44 on 2011-07-17
Hi wildmanne39 -

I have tried numerous changes of settings (using numbers 5 to 30) but to no avail - I even resorted to doing a re-install.

What happens -
Top panel logs on O.K. with high graphics but after a short delay (now 6 to 7 seconds) it resorts to low graphics mode. Graphics on files on desktop and within files under places remain in a high graphics mode. I can only think that with all of my fiddling I have broken something - is that possible?  I just may have to put up with it as it is.

 :)

---

### Post by wildmanne39 on 2011-07-17
Hi, if you did a clean reinstall then it should have erased any problems you might have created by changing the settings, and I doubt anything you did caused any hardware issues.

If you did not reformat your partition and you just installed over the top of the existing ubuntu then it would have preserved your previous settings.

---

### Post by OldBoy44 on 2011-07-17
Hi wildmanne39,

I did not reformat - It really is strange - It appears to be a "time out" issue but I don't understand how it only affects a part of the screen.

Is what you are saying that a reformat could possibly fix problem ? I am prepared to do that if so - I do not have all that much data which I have saved to flashdrives - I would be prepared to reformat if that may resolve issue. There don't appear to be many others cropping up with this issue (Using the published fix)
 
In any case wildmanne39, I really appreciate your efforts and don't expect you to respond anymore expect perhaps for one last time - I will see my post drift down the board and drift slowly off into the sunset - :D

---

### Post by wildmanne39 on 2011-07-17
Hi, I am not sure that it will fix it but if you just reinstalled over the top of the old ubuntu then you did not get rid of the old configuration files it would have saved then and used them in the new install. 

If you do a clean install then you can start over and if the problem still exists I would do what the link I gave said and then do not change any part of what it says keep it as stated in the link. I hope it helps.

---

### Post by OldBoy44 on 2011-07-18
Well wildmanne39. here I am at the top of the board again - I apologize for that. I have now done a reformat and am in the process of downloading all my data - although I was set up for six users that was really for experimentation purposes. I haven't altered the file in question as yet - I guess I am dreading what the possible outcome will be - I will do it soon and post back if results are successful - 

I really appreciate all the help you have been wildmanne39 - I will add a further comment - I am amazed at the number of hours you put in on the forum - you deserve a medal!

Cheers,  :P

---

### Post by wildmanne39 on 2011-07-18
Hi, thank you and I hope for the best possible outcome. I am surprised that no one else has an idea of a way to help you.

---

### Post by OldBoy44 on 2011-07-18
Hi again - No improvement at all in graphics with setting at 5 - Previously the improvement only came about with figure at about 15. One thing I didn't previously mention was the error message after issue of command - does this mean anything?

geoff@ABC:~$ gksudo gedit /etc/xdg/autostart/gnome-settings-daemon.desktop

(gedit:3117): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.MQDRYV': No such file or directory

(gedit:3117): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3117): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.0A6SYV': No such file or directory

(gedit:3117): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by wildmanne39 on 2011-07-18
Hi, I recently seen that message in a post and I will see if I can find it, I did a search but nothing came up so I will look through the last couple of days of my posts and see if I can find it.

---

### Post by OldBoy44 on 2011-07-18
Thanks wildmanne39 - no rush - I will keep on keeping on! :)

---

### Post by wildmanne39 on 2011-07-18
Hi, I just finished looking through all of my posts and I most not have posted to the thread that had that same error, and I can not find it with a search.

---

### Post by OldBoy44 on 2011-07-18
Hi wildmanne39,

I have done my own research and come up with this -
[http://ubuntuforums.org/showthread.php?t=1788133&highlight=file+directory+%28gedit%3A3117%29%3A+Gtk-WARNING+**%3A+Attempting+store+failed%3A+Failed+create+set+permissions](http://ubuntuforums.org/showthread.php?t=1788133&highlight=file+directory+%28gedit%3A3117%29%3A+Gtk-WARNING+**%3A+Attempting+store+failed%3A+Failed+create+set+permissions)
It appears relevant  - posts appear to suggest that there is nothing to worry about - One thing though - Should I issue command in #4 if I run fix again?

You will never guess what I have done - I have reinstalled yet again - I tried to issue commands for Flash 64bit but got messed up with errors when issuing commands to delete old versions - The download site was not particularly clear on how to go about it - I will leave alone until I come across clear directions.

I have been thinking that I may leave the fix alone as well - I am interested to see if graphics improves on its own as it did last time - it seems to take about a week for this to occur - why I don't know - This time I will see how long the improved graphics stay - maybe it is related to time logged on - What do you think the reason may be ?  

Anyway wildmanne39 as I have said before, I really appreciate your efforts in helping me. If you may answer my last two questions I will be on my way - :)

---

### Post by wildmanne39 on 2011-07-18
> **aussiebean said:**
> Hi wildmanne39,

I have done my own research and come up with this -
[http://ubuntuforums.org/showthread.php?t=1788133&highlight=file+directory+%28gedit%3A3117%29%3A+Gtk-WARNING+**%3A+Attempting+store+failed%3A+Failed+create+set+permissions](http://ubuntuforums.org/showthread.php?t=1788133&highlight=file+directory+%28gedit%3A3117%29%3A+Gtk-WARNING+**%3A+Attempting+store+failed%3A+Failed+create+set+permissions)
It appears relevant  - posts appear to suggest that there is nothing to worry about - One thing though - Should I issue command in #4 if I run fix again?

You will never guess what I have done - I have reinstalled yet again - I tried to issue commands for Flash 64bit but got messed up with errors when issuing commands to delete old versions - The download site was not particularly clear on how to go about it - I will leave alone until I come across clear directions.

I have been thinking that I may leave the fix alone as well - I am interested to see if graphics improves on its own as it did last time - it seems to take about a week for this to occur - why I don't know - This time I will see how long the improved graphics stay - maybe it is related to time logged on - What do you think the reason may be ?  

Anyway wildmanne39 as I have said before, I really appreciate your efforts in helping me. If you may answer my last two questions I will be on my way - :)
Hi, no I think you will be ok without running that command.

When you use root for running GUI programs make sure you use gksu or gksudo and not sudo because root my become the owner of that program if you do it that way and that is bad.

I believe it is a configuration issue,I do not think it has anything to do with how long you are logged in.

For your flash problem open firefox and click on tools,addons and install flashaid and follow the directions and it will install and fix any problems you have with flash it works great.

---

### Post by OldBoy44 on 2011-07-18
Hi wildemanne39 - My last post on the issue for now - 

With fresh install I decided to try the fix one more time using the suggested high variable number of 20. Unfortunately the same result - Top Panel on high graphics for about six seconds before reverting to low quality graphics. At least Desktop files and those under Places menu remain in high graphics mode. That will have to do me for now!

No need to reply - I will not mark as solved yet - All the best and many thanks - :)

---

