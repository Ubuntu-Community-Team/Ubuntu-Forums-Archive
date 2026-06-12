---
title: "Dual Boot to share components"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by RichardCL on 2009-12-07
Dear Forum,

Is there a way for dual-boot Ubuntu to share components. I'm thinking of a webserver that I can boot into GUI Ubuntu for maintainance, programming etc. or boot into headless webserver for the rest of the time.

The problem is that I'd have to share the SQL and apache installations across the two ubuntu installations.

I really like the coloured editors for coding and to be able to view files with firefox and firebug for debugging online.

Otherwise, what about installing gnome as an option?


Thanks in advance



Richard

---

### Post by cariboo on 2009-12-11
You can install any gui you want, even the the complete ubuntu desktop. You can even install all the server components on a desktop system. You can also use X fowrding with ssh, and run a gui application remotely. Make sure you have the openssh-server running, then open a terminal and type:

```
ssh -X user@server
```

once logged in, just run any gui app you have installed on the server. You don't need to have X installed to do this.

---

### Post by jbrown96 on 2009-12-11
If you install Gnome (or run the Desktop edition), then you can stop/start Gnome with ```
start gdm
``` ```
stop gdm
``` you might have to sudo those, but try without first.

There's not really any good reason to forgo a GUI; there's no security implications if it's just sitting there, doing server stuff. It doesn't look like the small overhead of running a GUI will matter much either.

---

### Post by RichardCL on 2009-12-16
So I've moved over to a desktop install now, which is so much easier for the little tasks like sharing printers. It is also nice to have firefox for downloading the packages and software that I need for the webserver e.g. Joomla.

Now I'm stuck choosing between VNC and SSH as a remote login. Ideally, the GUI would run using my desktop's resources as far as possible since the server uses low power Atom hardware and the desktop uses Quad core.

I also want to run headless, which doesn't seem possible under VNC (I assume I need to login before running VNC). Does that mean I have to run SSH?

---

