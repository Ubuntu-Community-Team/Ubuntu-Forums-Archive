---
title: "Delete 'Data Crow' folder"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by mwimmersc on 2009-03-12
Weird Problem...

I installed the media cataloger 'Data Crow,' and the installation wizard created a folder of the same name under /usr/local. It turns out that the program needs full control of its sub folders and it won't run from there. I copied the entire folder into my 'Music' folder & it ran from there, which worked, but I expected more from the program and decided to delete it. 

Data Crow did initially install an uninstaller jar file, but it seems to me that it needs root privileges & I cannot get to it in the terminal, and I think this is because the folder 'Data Crow' is made of 2 words & the terminal won't let me in. I ran the uninstaller from nautilus, but nothing was uninstalled. Is there a way that I can either enter the 2-worded folder 'Data Crow' from the terminal to access the uninstaller, or to get root privileges from nautilus?

---

### Post by ptn107 on 2009-03-12
Press ALT+F2 and type **gksu nautilus** in the box, press 'Run'.  You'll have root privileges from there so be careful what you mess with.

---

### Post by mwimmersc on 2009-03-27
Thanks, it worked! How do I mark this thread as solved?

---

### Post by llamabr on 2009-03-27
Be sure to edit the original post to reflect that the issue has been [SOLVED]]

---

