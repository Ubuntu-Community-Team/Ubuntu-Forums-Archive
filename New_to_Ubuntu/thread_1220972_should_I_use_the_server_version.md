---
title: "should I use the server version?"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by jdrodrig on 2009-07-23
Hi,

I am in the process of buying a desktop (to get hooked up with my tv) with the purpose of having that computer running some codes (fortran and matlab), hopefully 24x7. 

I am planning to (after I learn how) connect remotely from the office to interact with that box. We will potentially be two users accessing the computer simultaneously.

Should I install Ubuntu server version on that box? or would Ubuntu Desktop be enough? would I miss much if I stayed with the desktop version?

---

### Post by Kobalt on 2009-07-23
You woulnd't actually "miss" a thing, because all of the services included in the Server Edition can be installed on the Desktop Edition, and all the GUI of the Desktop Edition can be installed on the Server Edition.
What's more important for you is which services you need, and do you need a GUI or will the command line suffice to install and configure all this.

---

### Post by Mighty_Joe on 2009-07-23
> **Kobalt said:**
> You woulnd't actually "miss" a thing

What he said.  [This article]("http://www.bmighty.com/blog/main/archives/2008/10/ubuntu_server_o.html") is about 8.10, but it's still valid for 9.04.

---

### Post by jdrodrig on 2009-07-23
> **Mighty_Joe said:**
> What he said.  [This article]("http://www.bmighty.com/blog/main/archives/2008/10/ubuntu_server_o.html") is about 8.10, but it's still valid for 9.04.

Thanks. I am just a bit confused about no pre-emption in the server kernel. Should I be concerned when running multiple applications that exploit parallelism?

---

### Post by Mighty_Joe on 2009-07-23
That depends on what applications and what load you are running.  If you have a modern multicore CPU and a reasonable load, I'd say you won't miss preemption (I think it's voluntary in the desktop kernel anyway).  You can always try to get processes to [play nice]("http://en.wikipedia.org/wiki/Nice_(Unix)")
How about dual booting desktop and server and seeing if there's a difference under realistic working conditions?  With 2 users, I'll bet there will be no difference.

---

### Post by jerome1232 on 2009-07-23
I think mostly the question is do you plan on running an X server on this server. If you do want to run an X server do you need a full blown Desktop Environment like Gnome/KDE or will a lightweight Window Manager like fluxbox/icewm suffice.

You can always install the server kernel if you want it.

---

### Post by jdrodrig on 2009-07-23
> **jerome1232 said:**
> I think mostly the question is do you plan on running an X server on this server. If you do want to run an X server do you need a full blown Desktop Environment like Gnome/KDE or will a lightweight Window Manager like fluxbox/icewm suffice.

You can always install the server kernel if you want it.

Thanks to all....the idea of doing a trial run using two virtual machines sound very reasonable one desktop one virtual...

About DE, yes I would like one, I ocassional do the final touches to the code in Sun Studio IDE.

---

