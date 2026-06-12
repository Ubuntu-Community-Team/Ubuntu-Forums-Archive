---
title: "Portioning problems"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-05
I partioned my (100GB) hard drive like this:
7 GB /  (for the OS)
92 GB /home (for data)
1 GB swap

However I'm not sure where the OS actually went. Another problem is the fact that if I install something using the terminal command "apt-get install" it automatically installs it in /usr and I don't even know where that is. I would like to install all my games/software in the /home and only the OS in /. How can I do this? (I'm ready to reinstall ubuntu and format everything on the computer if needed)

---

### Post by bioterror on 2010-11-05
So many questions, but you should read this. [http://www.tuxfiles.org/linuxhelp/linuxdir.html]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")

It explains it all better than I could.

---

### Post by Mark Phelps on 2010-11-05
You don't have the flexibility of installing app to whatever directory you want -- it doesn't work like that.  

Linux has a directory structure that places different kinds of files in different locations.  Installations have to follow that if they are to work.

Read the link provided for more details -- but basically, you can't do what you want to do.

---

