---
title: "Exporting path to config file? Not exporting every time."
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Canime on 2011-03-03
Hi, I have installed Ubuntu 10.10! So far so good, I like the layout. I have installed a program from its binaries and in order to run it it requires the terminal command,

./run.sh

in order to run it from anywhere, they suggest to set the path variable, in fact to export the path variable so I can run it from any directory. But when I close the session, and re-open terminal, I have to export the path in the same way. Any way to make it stick, such as a file that contains all of the path variables? Where is it and what is it called?

---

### Post by Perfect Storm on 2011-03-03
Why not making a launcher for?, in the applications tab?

Right click on the Applications tab ---> Edit menu

Now choose a category you want the launcher in, then click **new Item**.


In the command box:
sh -c "cd /into/the/folder && ./binary"

---

### Post by Canime on 2011-03-03
That's a great solution! Thanks a lot, i'll use that instead!

---

### Post by Perfect Storm on 2011-03-03
My pleasure ^_^

Have marked the thread solved.

---

