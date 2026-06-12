---
title: "System&gt;Administration&gt;Services from CLI"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by ScaredNoob on 2009-02-26
(Ubuntu 8.10)
Hi all.  In the quest for a faster boot time, I mistakenly disabled the graphical login manager (I thought autologin enabled meant I didn't need to start it) and now I need to reenable it.  I can login using my username/password and the startx command, but when I graphically mouse over to system>administration>services the "unlock" feature is greyed out and unclickable.  I'm thinking that starting system>administration>services from cli with sudo in front should let me reenable it, but I'm not sure how to get to that services.exe (I know its not really an exe).  for example is it in /etc/services or something?  If there's an easier way to reenable the graphical login manager, I'd love to hear it.  Thanks for the help penguin buddies.

-ps I'm sure a number of noobs like myself have made this mistake, and there should be some kind of prompt explaining the ramifications of disabling the graphical login manager, because literally right after you click to disable it, BOOM! you're in cli land with no terminal or anything.  From there I had to do a half-hard power down and then I remembered how to startx again, but a total noob would have no idea how to do this (and possibly have no way to access the internet to look up how to do this) and could be highly discouraged.  Just my two cents.

---

### Post by scrooge_74 on 2009-02-26
Try to reconfigure the login manager

from console 

sudo dpkg-reconfigure gdm

sudo reboot

---

### Post by dzark on 2009-02-26
Too slow!

---

### Post by ScaredNoob on 2009-02-26
unfortunately that didn't seem to work.  got this bit after it said changes will take effect after x session is restarted:

invoke-rc.d: initscript gdm, action "reload" failed.

reboot computer... same CLI username prompt.  Is it possible I should be using a different command instead of startx, for example is there such a thing as start-ubuntu or something like that?

---

### Post by scrooge_74 on 2009-02-28
try from the command line sudo startx see if  you can then fix what you messed in first place. You should be able to log as root

---

