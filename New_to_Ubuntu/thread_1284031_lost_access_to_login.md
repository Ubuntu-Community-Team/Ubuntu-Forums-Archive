---
title: "lost access to login"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by kjvdveer on 2009-10-06
I installed Ubuntu 9 a week ago and did try to make backup of files with Simple Backup

The files could not be accessed as they belonged to Root, so I tried to change the access to them with sudo chmod.
I did manage to remove the file restrictions.

To my surprise I could now no more access my user map, after trying some more with chmod I gave up and wanted to restart.
This turned out to be impossible because no more access to $HOME/.dmrc

Could someone please help me to log in again. I do know how to get in into the terminal session, but what do I type there ???

---

### Post by nothingspecial on 2009-10-06
Try ```
chmod 644 /home/username/.dmrc
``` if you are in the root recovery shell. If you are in your own failsfe shell you will need sudo.

---

### Post by kjvdveer on 2009-10-06
Thanks so much for your suggestion.
I went into the Xterm safe mode session an typed: sudo chmod 644 /home/karel/.dmrc
an it seemed to work to my surprise I could still not access my usr map nor the home map.

Trying to startup again I got the following message:
      Your personal map has been set as: /home/karel  but does not seem to exist

in terminal changing directories cd /home  gave : access refused
                                               cd karel   gave does not exist

further suggestions very very welcome

thanks

---

### Post by kjvdveer on 2009-10-06
q

---

### Post by nothingspecial on 2009-10-06
What - exactly - did you do?

---

