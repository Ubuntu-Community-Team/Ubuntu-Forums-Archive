---
title: "X11 shutdown"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by newport_j on 2009-12-10
When I want to shut down X11 or Xwindows (is there a difference?) I use the following command:

sudo /etc/init.d/gdm stop

and it shuts down the Xwindows. I am also told that CTRL-ALT- works. Is this true?

When I shut down X11 the screen becomes very crowded with big fonts and I have no room (or little room) for commands on the command line.

Is there a better way? 

Please understand that I like to use it remotely. The computer with widows that i am shutting down is not where I am sitting. I want to do cuda-gdb debugging.

Sometimes even after issuing

sudo /etc/init.d./gdm stop 

it is still very hard to get into the NVIDIA GPU subprogtam. Sometimes when I set a break there it ignores it and just runs the program.

What is the proper command to shut down X11 and what else must you do in order to get into a CUDA kernel?


Respectfully,

Newport_j

---

### Post by RedSingularity on 2009-12-11
Thats the command i have always used to stop an Xorg from running.  I dont believe there is a "better" way.

---

