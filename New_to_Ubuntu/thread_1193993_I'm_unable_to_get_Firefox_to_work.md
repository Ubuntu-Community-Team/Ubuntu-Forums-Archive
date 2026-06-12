---
title: "I'm unable to get Firefox to work"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by StuM on 2009-06-22
I seem to have made a bit of a noob error while attempting to install the latest Firefox 3.5 Release Candidate.  Now my standard 3.0 install is corrupt.  When I click on the launch icon in the menus I get 

> Error: Could not launch application Failed to execute child process "firefox" (No such file or directory)

I've tried reinstalling and then uninstalling (inc. complete) and reinstalling from Synaptic, but I'm still getting the same message.  

Typing firefox in the terminal window gives me: 

> The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found

I try doing that, but I get the error messages afterwards.

---

### Post by tarps87 on 2009-06-22
Try
```
sudo find / -name firefox*
```
(sudo so it can search in root read only folders)
or you can try typing firefox *now hit tab twice*

It is possible it is called something like firefox-3 or firefox3 and buy installing the rc it replace the link to firefox3 with on to the rc

---

### Post by StuM on 2009-06-22
Thanks for the help.  It looks like you were right, I've now managed to get Firefox to launch from the menus by changing the command from firefox %u to firefox-3.0 %u

---

### Post by tarps87 on 2009-06-22
If you want use the command firefox find where the firefox-3.0 command is stored
```
whereis firefox-3.0
```
and then symbolic link it
```
sudo ln -s /*pathToBinFolder*/firefox-3.0 /*pathToBinFolder*/firefox
```

It happened to me when I tried the 3.0 rc :)

---

