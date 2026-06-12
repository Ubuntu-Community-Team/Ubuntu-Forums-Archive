---
title: "What ubuntu version to use"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by s195404 on 2010-07-14
Dear Ubuntu users,

I want to have a computer that my colleagues and I can all share to run some CPU- and memory-intensive calculations. In "days of old", I used to telnet into a remote supercomputer and then run an x-term and my X applications (via X-Win32 or Cygwin-X), all from my local PC.

I'm not sure what the modern way is to do all these things. I want a single workstation with lots of RAM and CPUs, but I don't know what the technology is for connecting to a Ubuntu machine. Is it VNC or what? Also, what version of Ubuntu should be installed on the workstation - desktop or server?

Is there anything else I need to know to have the setup that I'm after? Thanks in advance for your advice.

Regards,

Andrew

---

### Post by 3rdalbum on 2010-07-15
> **s195404 said:**
> Dear Ubuntu users,

I want to have a computer that my colleagues and I can all share to run some CPU- and memory-intensive calculations. In "days of old", I used to telnet into a remote supercomputer and then run an x-term and my X applications (via X-Win32 or Cygwin-X), all from my local PC.

I'm not sure what the modern way is to do all these things. I want a single workstation with lots of RAM and CPUs, but I don't know what the technology is for connecting to a Ubuntu machine. Is it VNC or what? Also, what version of Ubuntu should be installed on the workstation - desktop or server?

Is there anything else I need to know to have the setup that I'm after? Thanks in advance for your advice.

Regards,

Andrew

VNC is used to access the currently-running desktop of the computer. It doesn't sound like this is what you're after.

You can SSH into the Ubuntu computer and run X programs, as long as you use the -XC parameter in SSH. It's virtually the same thing as what you describe with telnet. The X programs will be running on the server/workstation, but their windows will appear on your computer.

If you want to run a GUI on this workstation, then use Ubuntu Desktop. The only difference between Desktop and Server is that Server does not have a GUI.

From what you describe, with multiple users, you could run Ubuntu Desktop or Ubuntu Server (your choice, would you prefer a GUI for administering the machine?), set up SSH on the server/workstation, add user accounts for everyone so they can log in, and bob's your uncle. Multiple people can use the Ubuntu computer at the same time for running all sorts of programs, with all their X GUIs being forwarded to each user's local computer.

---

