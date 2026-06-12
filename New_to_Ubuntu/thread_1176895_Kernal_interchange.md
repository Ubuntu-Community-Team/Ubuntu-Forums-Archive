---
title: "Kernal interchange"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by navaneethan on 2009-06-02
Hi all,

      Is it possible to install ubuntu kernal to fedora kernal??
What we have to change in module of kernal??

     I think we can install ubuntu kernal for debian?? How it is possible? Is it depends on package type or not?


     Similarly Is any possibilities available to install Free BSD kernal to ubuntu??

     If you ve any idea relating this kindly detail it to me

---

### Post by Didius Falco on 2009-06-02
Hi,

Start here:

[http://kernelnewbies.org/](http://kernelnewbies.org/)

There is a FAQ that you should pay particular attention to on that site, along with lots of documentation.

After you're done reading up, you can go here:

[http://www.kernel.org/](http://www.kernel.org/)

That's about all I can do to help - kernels are WAY above my pay grade!

Regards,

Didius

---

### Post by 3rdalbum on 2009-06-02
> **navaneethan said:**
> Similarly Is any possibilities available to install Free BSD kernal to ubuntu??

You'd need to modify the system so much (replace Upstart with Init again, recompile Xorg and possibly most of the GNU userspace) that it wouldn't really be worth it. Why would you want to do it? Debian has a version with kFreeBSD anyway, why not run that?

As for installing Fedora's kernel on Ubuntu, I really don't know. Try it. If you don't want to break your system, do it inside a virtual machine.

---

