---
title: "Home Folder Disappeared or Hiding After an Update to 9.04"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by justinmiller87 on 2009-10-02
I performed an update and rebooted to have it take effect. Now when I log in I get the following:
'
```
User's $HOME/.dmrc file is being ignored. 
This prevents the default session and language from being saved. 
File should be owned by user and have 644 permissions. 
User's $HOME directory must be owned by user and not writable by other users.
```

It then logs in and brings up the default icky-brown Ubuntu desktop and none of my files are in my HOME folder.

From what I can tell, it just can't load my stuff, but I would love for it to do it again. What do I need to do to get it all back again?

Thanks.

---

### Post by JC Cheloven on 2009-10-02
Hi, try this:
- open a terminal and navigate to your user directory if you're not already in
- for future reference: run "ls -al", and post the output if the folowing doesn't work
- run this (one command at time):

```
sudo chown justin .dmrc
sudo chmod  644 .dmrc
```
(justin is to be replaced by your username)
Reboot and check if it is fixed.

oops: sorry for several editings, it's late in the night already :-O

---

### Post by tahitiwibble on 2009-10-02
I had a similar problem. This may help you [http://ubuntuforums.org/showthread.php?t=1081570](http://ubuntuforums.org/showthread.php?t=1081570)

I'm sorry not to be more helpful but I can never remember how I fixed things.

---

### Post by justinmiller87 on 2009-10-03
I did everything in these steps, and when I rebooted, I successfully stopped getting the error message, but had a huge fail at getting my old settings and stuff back. Could this have anything to do with having an encrypted home folder?

---

