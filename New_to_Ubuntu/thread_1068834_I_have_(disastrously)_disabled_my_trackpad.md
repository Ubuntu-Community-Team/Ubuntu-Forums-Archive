---
title: "I have (disastrously) disabled my trackpad"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by ni2hao3 on 2009-02-13
Hi,

For some time, I have been trying various config edits to deal with the horribly bad performance of my hp Pavilion dv4000's trackpad in Ubuntu.  I have 8.10, but this has been a problem for three versions.

I recently read about changing ANOTHER file, and whatever file it was had some attributes for mice/trackpads, and it was supposed to be the solution.

Long story short, I edited it and it disabled the trackpad.  I can't remember the name of the file, and searching by recent edits has not been fruitful.  I've had to go out and buy a USB mouse!  Not convenient.

Little help?

Thanks,

NEAL

---

### Post by Mark Phelps on 2009-02-13
The file that you hacked was most probably /etc/X11/xorg.conf -- that configuration file the X-windows uses when it starts.  

Hopefully, you made a backup copy of that before you hacked it, otherwise, you will have to generate a new one, and spend a lot of time customizing it again.

---

