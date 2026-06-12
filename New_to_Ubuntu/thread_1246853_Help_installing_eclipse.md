---
title: "Help installing eclipse"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by Faudyen on 2009-08-22
I can sudo apt-get install eclipse which installs 3.2...I need 3.5 and see now way in the program how to upgrade.  If someone knows how that would be awesome.

I can download eclipse-SDK-3.5-linux-gtk-x86_64.  I choose extract here and then cd to the eclipse folder
I try to confgure or make and neither work so I open to folder to find a windows executible file.

How do I run this in the terminal?  If I just type eclipse in terminal it still brings up 3.2 not 3.5.  I have to actually click on 3.5 to get it to run.

Should I uninstall 3.2 from the package manager before trying to run 3.5 in the terminal?

bah...Im frustrated lol

---

### Post by Copernicus1234 on 2009-08-22
Download and unpack as you have. Then go to the directory where you unpacked it and type ./eclipse. The "./" means "current directory" which means the system will not search for eclipse in the other paths and find your old eclipse.

When you want to make it so the command "eclipse" always starts your new version no matter where you stand in the directory tree (or if you start it by a menu command saying only "eclipse"), simple rename the eclipse directory in /usr/bin to something else, and move your new eclipse directory to /usr/bin instead.

---

### Post by Faudyen on 2009-08-22
That worked perfectly.  Thank you.  I would like to mark the thread as solved but for some reason cannot find where to do that

---

### Post by Copernicus1234 on 2009-08-22
Ive been here for many months and I havent figured it out either. Ive tried and failed. Must be in some non-intuitive place....I would have put it under Thread Tools if I had designed this forum. :)

---

### Post by Nepherte on 2009-08-22
Just rename the thread?

---

