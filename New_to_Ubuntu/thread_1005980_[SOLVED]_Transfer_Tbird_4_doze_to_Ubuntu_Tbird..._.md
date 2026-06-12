---
title: "[SOLVED] Transfer Tbird 4 doze to Ubuntu Tbird... can it be done?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Chris Watts on 2008-12-08
Just pulled XP off my laptop to try Ubuntu, having not been in touch with linux since Slackware and Redhat in the late nineties. I really need to access my received emails but don't want to dual boot windows/Ubuntu. 
Has anyone had any luck with transferring their Thunderbird email messages to Thunderbird under Ubuntu? There only seems to be import support for communicator 4. I have looked for mail storage in the filesystem with the hope of replacing the empty files with my tbird4windows ones but no luck with that so far.

---

### Post by anim on 2008-12-08
I don't use thunderbird too much anymore but I believe there is a way to backup all your emails on the XP machine, then import those backed up emails on the linux machine.

[http://email.about.com/od/mozillathunderbirdtips/qt/et_backup_prof.htm](http://email.about.com/od/mozillathunderbirdtips/qt/et_backup_prof.htm)

basically shows you how it goes.

---

### Post by Moop on 2008-12-08
It's not hard to transfer your Thunderbird settings from windows to Ubuntu. Locate your Thunderbird profile folder in windows, usually located in [I]C:\Documents and Settings\[User Name]\Application Data\Thunderbird\Profiles\

[/I]Copy the folder. After you install Thunderbird in Ubuntu navigate to the profile in your home directory *~/.thunderbird/xxxxxxxx.default/  *You will need to enable viewing of hidden files to see it. Use the view tab or ctrl-h. The folder you are looking for is .mozilla-thunderbird. Make sure Thunderbird is not running and delete the profile folder and replace it with the one you copied from windows. 

Start thunderbird and all your emails and settings will be there.

---

### Post by Chris Watts on 2008-12-09
Thanks Moop for that info - very easy really. I have decided to remove Thunderbird tho cos it wont send my mail - keeps telling me incorrect password so I tried with Evolution Mail and had no problems. Tbird seems to have a few oddities in Linux that it never had in windoze.
I also like the calender etc in Evolution so will go that way. Thankyou very much for your help.

---

