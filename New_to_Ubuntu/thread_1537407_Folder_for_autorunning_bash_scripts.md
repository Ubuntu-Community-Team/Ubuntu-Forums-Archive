---
title: "Folder for autorunning bash scripts"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by CaptainMark on 2010-07-23
Im sure i remember reading theres a folder that you plonk your nicely written bash scripts into have them automatically run at login but cant remember for the life of me where. Any one know?

---

### Post by matrixblue on 2010-07-23
Add the  following lines to your /etc/profile startup script

> for i in /etc/profile.d/*.sh ; do
    if [ -r "$i" ]; then
        . $i
    fi
done

Then create the directory /etc/profile.d/ and add your scripts to it. Bear in mind this will run the scripts at loging for ALL users so use with caution.

If you want just for one user then add the lines to ~/.bash_profile.

---

