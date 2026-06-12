---
title: "New choice when I dual boot?"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by Dave W. on 2009-06-19
Hello Folks,

I used update manager yesterday and now when I start up  my dual booting box, it has an extra ubuntu recovery mode in it.  Has anyone else noticed that also?  Or am I alone in this?


Bennachie showed me how to reset my default start with this, if any one is interested.  It works fine.  I had to set my default # to 6

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

Thanks,
Dave

---

### Post by pissedoffdude on 2009-06-19
> **Dave W. said:**
> Hello Folks,

I used update manager yesterday and now when I start up  my dual booting box, it has an extra ubuntu recovery mode in it.  Has anyone else noticed that also?  Or am I alone in this?


Bennachie showed me how to reset my default start with this, if any one is interested.  It works fine.  I had to set my default # to 6

[http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

Thanks,
Dave

That just means that the updater installed a new kernel.  Whenever a new kernel is installed, it's added to the grub menu and the old one stays just in case something goes wrong with the new one.  If it's bothersome, you can delete, or simply comment out the lines of the old kernel with a # by doing a :```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Dave W. on 2009-06-19
Thanks pissedoffdude!

I appreciate the info.

Dave

---

### Post by nhasian on 2009-06-19
i believe you can also easily remove it without editing any files by hand by going to System->Administration->Computer Janitor.

---

### Post by Dave W. on 2009-06-20
Thanks nhasian.

---

