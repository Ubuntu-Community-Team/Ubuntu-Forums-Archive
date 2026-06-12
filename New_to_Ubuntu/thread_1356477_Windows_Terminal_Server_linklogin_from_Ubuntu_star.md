---
title: "Windows Terminal Server link/login from Ubuntu startup/login screen ?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by chrisdee on 2009-12-16
Hi.

I'm trying to figure out how to connect to a windows terminal sever from a Ubuntu 9.10 startup/login screen, rather than using the tsclient (Terminal Server Client).

I'm running a small ubuntu 8.10/9.04 lab (8 machines) wich I would like to configure so that students could click on a link or have the option to login to a windows terminal server from the ubuntu startup/login screen.

Would greatly apreciate if someone could help point me in the right direction reguarding this.

---

### Post by callan79 on 2009-12-16
> **chrisdee said:**
> I'm trying to figure out how to connect to a windows terminal sever from a Ubuntu 9.10 startup/login screen, rather than using the tsclient (Terminal Server Client).


Hi chrisdee,

I don't have a solution to your question, I guess I just wanted to offer general advice that as far as I know, you're going to have to use tsclient software.

If you want to connect to a *WINDOWS* Terminal Server upon system login, you're going to have to use Windows, and set up a domain.

Now, you may know that tsclient is just a front-end for rdesktop. I'd suggest look at the man pages for rdesktop ('man rdesktop' in terminal), and work out what you need to start a connection directly to the terminal server.

Then create a launcher on the desktop with that command... then the students just click one icon, and they are straight in.

Or - put that command into Ubuntu Startup Programs ....

Cheers
Callan

---

### Post by chrisdee on 2009-12-16
Hi. Thank you for your answer.

The university where I work already have a domain and several windows terminal servers. What I need to do is find a way to customize login to terminalserver. For me it's easy to setup and use the Terminal Server Client program in Ubuntu. But I would like to give my "unexperienced" users the option to login to terminal server from the Ubuntu startup/login window.

I'v googled around for this but not found any examples or tutorials. But I'll have a look at the rdesktop man pages as you suggested as a start.

---

