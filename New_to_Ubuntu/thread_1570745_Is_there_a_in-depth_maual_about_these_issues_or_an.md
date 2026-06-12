---
title: "Is there a in-depth maual about these issues or an ubuntu 101"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by mslina on 2010-09-08
how to open software from the software center? Its not in the applications or programs...
when i download from the synaptic manager it keeps telling me to apply changes that i have marked after they have downloaded...and i still cant find those packages either... am i doing something wrong?  i also want to Burn my mp3s to a CD the mp3 files are on a jump drive but it burned the image and the options came up to turn them in 64 something compatible to windows...



any help is welcomed thanks):P

---

### Post by silverglade00 on 2010-09-08
> how to open software from the software center? Its not in the applications or programs...

Many of the programs available are command line only tools. You can run them from the command line in Terminal. ALso, the menus do not update right away sometimes. If you log out then back in, you might see some of the ones that you installed. When it wants you to apply updates, those are upgrades to the software you already have. You will not get any new menu items becuase they are already in there. 

I'm not sure how to help with your mp3s, but you might want to copy them to your desktop or something first before burning them. That way you will have an extra copy for backup in case something happens to your jump drive and the system will be able to read the files faster, which might help prevent errors while burning.

---

### Post by khelben1979 on 2010-09-08
I think you need to be more specific about what software don't show up in the Ubuntu menu.

However, to better understand how [Ubuntu SoftwareCenter]("https://wiki.ubuntu.com/SoftwareCenter") works, I think the link might be worth your time.

---

### Post by mslina on 2010-09-08
> **khelben1979 said:**
> I think you need to be more specific about what software don't show up in the Ubuntu menu.

However, to better understand how [Ubuntu SoftwareCenter]("https://wiki.ubuntu.com/SoftwareCenter") works, I think the link might be worth your time.

its a software i installed called mp3cd from the software center i want to run but i dont understand how and where to get it to run thanks for the link will check it out!

---

### Post by ajgreeny on 2010-09-08
mp3cd is a script to do the job, not an application in your expected sense, and as such it is run from the terminal.

Having installed it, run ```
man mp3cd
``` in the terminal and there will probably be a manual appear to tell you how to use it.

---

