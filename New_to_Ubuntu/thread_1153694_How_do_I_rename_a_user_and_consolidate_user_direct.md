---
title: "How do I rename a user and consolidate user directories?"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by jon.reeve on 2009-05-09
So I have a separate /home partition, with my home directory on it, /home/jon and so when I upgraded to Jaunty I did a fresh install, keeping my /home. But I created a new master user name by mistake /jonathan, and what I want to do is delete this user name, and get all my old settings back in /jon, but I don't want to overwrite any of my old config files in the process. 

So I want to add new user "jon," but keep all the files in /home/jon untouched. Or, rename user "jonathan" to "jon" and have the home directory remain untouched. Is there a way to change my username, but tell it not to create a new home directory? Or is there another way of accomplishing this? 

Sorry this is so confusing sounding. Any ideas?

---

### Post by Didius Falco on 2009-05-09
are you sure there isn't a jon folder still in your /home partition?

Type ```
ls /home
``` in a terminal and see what comes up.

---

### Post by Operan on 2009-05-09
Log out your acc, ogin other account with sudo mode and try this:

usermod -l jon jonathan
groupmod -n jon jonathan
usermod -d /home/jon jon
usermod -c &#8220;Your Name&#8221; jon

Good luck!

---

### Post by jon.reeve on 2009-05-09
Thanks, Operan, that worked almost perfectly. I now have most of my settings back, which is great. The only problem is that now Network Manager won't start up. When I try to run nm-applet in a terminal, I get this error: 

jon@fia:~$ nm-applet

** (nm-applet:16187): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service.
  Message: 'Connection ":1.286" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'

Do you know how I might go about correcting these permissions?

---

