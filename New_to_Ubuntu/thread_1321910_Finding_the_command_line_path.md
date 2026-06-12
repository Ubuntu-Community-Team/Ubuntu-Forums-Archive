---
title: "Finding the command line path"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by david35580 on 2009-11-10
Can any one tell me how I can find the command line for an application to run.
I know I only have to put in 'Evince', say to make evince run in the properties box of applications (or the terminal), but suppose I need the entire command line for some reason:\usr\etc\etc. 
What is the Ubuntu/Linux equivalent to an .exe file?
Thanks,
David

---

### Post by CaptainMark on 2009-11-10
Linux doesnt really have the same thing as an .exe the closest thing would be a .deb , not 100% sure what your asking but to install evince you would just type ```
sudo apt-get install evince
``` into a terminal (applications>accessories>terminal) then the terminal looks in ubuntu's online repos and installs it for you, you dont see the install files, and to run it just type ```
evince
```

---

### Post by lykeion on 2009-11-10
I guess you mean the which command. 
Example:
>which evince
/usr/bin/evince

---

