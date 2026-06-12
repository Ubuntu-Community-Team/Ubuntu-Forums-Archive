---
title: "I broke zsnes"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by jeremythuff on 2011-07-15
Hello folks,

I am fairly proficient with computers but absolutely new to Linux and Ubuntu.

I am running 11.4 and I used the sotfware center to install zsnes. I then started trying to find a good resolution. I came to one which sent my entire screen black. I have a cursor but I cannot seem to kill the program (is that alt-f2?) or alt-tab to another program. The only way I have found to get out is to put my computer to sleep, and then wake it up, at which point I can witch users and use the power options to restart.

I have tried to remove/re-install but every time i boot up zsnes it goes to that same inescapable black screen.

I read some instructions online for changing the resolution in zsnes manually by going into the zsnesl.cfg, but I cannot find that file on my computer.

Any suggestions?

---

### Post by jerome1232 on 2011-07-15
I would remove zsnes with the --purge option, it should clear out the config files.

Configuration files are normally in a hidden directory in your home folder, ie zsnes is probably at ~/.zsnes

The following should clear the config files and reinstall zsnes. Failing that I would open your home folder, press ctrl+h to view hidden files and search for a .zsnes folder and delete it.
```
sudo apt-get remove --purge zsnes
sudo apt-get install zsnes
```

---

### Post by jeremythuff on 2011-07-15
Thanks a ton!

I ended up having to delete the folder, but at least now I know how to find it too.

---

