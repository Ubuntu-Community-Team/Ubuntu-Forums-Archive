---
title: "bash script question"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by mamamia88 on 2011-02-13
how do i write a bash script that opens a terminal and runs sudo -i, aptitude-update, and finaly update-manager?  write now my basic update script i wrote looks like this ```
#!/bin/bash
sudo aptitude update && sudo apt-get upgrade
sudo apt-get autoclean
```  but i like the idea of update manager better

---

### Post by oldfred on 2011-02-13
I do not think it is good to mix aptitude and apt-get. 

I also is not considered good practice to include sudo in a script. You run the script with sudo so all the commands can run.

From my new install script:

#this updates everything
apt-get update
apt-get upgrade
#would upgrade you to the latest kernel in the repositories
apt-get dist-upgrade
# make sure update manager is updated
# apt-get install update-manager-core

---

