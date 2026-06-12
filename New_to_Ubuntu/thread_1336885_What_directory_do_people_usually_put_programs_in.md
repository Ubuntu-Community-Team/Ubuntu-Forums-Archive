---
title: "What directory do people usually put programs in?"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-11-24
Where do people usually store their programs in? Windows has the Program Files folder, but what is the equivalent in Ubuntu?

Second, is there an option on the 'mv' command to move a directory and all of it's contents? Or will mv move the whole lot?

---

### Post by -Zeus- on 2009-11-25
> **Cooter2543 said:**
> Where do people usually store their programs in? Windows has the Program Files folder, but what is the equivalent in Ubuntu?

Second, is there an option on the 'mv' command to move a directory and all of it's contents? Or will mv move the whole lot?

First off, welcome. :)

Question 1: different folders, but "you" don't really decide, the system takes care of that.  Often they will be in /bin, /usr/bin, etc.  If you're curious about a specific program, type the command "which programname" (eg, "which mv"), and it should say something like, "mv is /bin/mv"

2, mv will by default move directory contents

Have fun :)

---

### Post by Sealbhach on 2009-11-25
But when you install a program it often install library files as well, these go into usr/lib

.

---

### Post by slakkie on 2009-11-25
> **-Zeus- said:**
> First off, welcome. :)

Question 1: different folders, but "you" don't really decide, the system takes care of that.  Often they will be in /bin, /usr/bin, etc.  If you're curious about a specific program, type the command "which programname" (eg, "which mv"), and it should say something like, "mv is /bin/mv"


This is true for applications provided by .deb packages, but when you compile from source you can definitely decide where to install them:

./configure --prefix=/opt for example to install the application in /opt/.

---

### Post by Cooter2543 on 2009-11-25
OK, thanks guys.

---

### Post by -Zeus- on 2009-11-25
True - I was thinking on a new-user level.

---

### Post by louieb on 2009-11-25
For the most part Ubuntu follows the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")
The short of it
Programs essential to the system are located in /bin or /sbin.
Programs installed and integrated through the package manager are located /usr/bin or /usr/sbin

Anything else: Example - you get Firefox from the Mozilla site. It should install itself in /opt.

---

### Post by liquider on 2009-11-25
And any windows programs via wine installed to default path are found in
> ~/.wine/drive_c/Program Files/...

---

