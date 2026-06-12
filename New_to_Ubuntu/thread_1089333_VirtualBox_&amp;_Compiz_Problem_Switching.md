---
title: "VirtualBox &amp; Compiz Problem Switching"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-07
In this video
[http://www.youtube.com/watch?v=A7gKb65HuV0](http://www.youtube.com/watch?v=A7gKb65HuV0)

He can switch between Vista, XP and Ubuntu. Vista & XP are fullscreen on other workspaces.

I've done this, but when I switch to another workspace with Vista/XP on fullscreen, then try to use my shortcuts to change back to other workspaces (or enable 3d cube) they dont work because the keyboard becomes in use by Vista/XP.

My question is how did he set it up so he can switch between them like that with fullscreen?

---

### Post by beno1990 on 2009-03-07
Install the guest additions on all guest operating systems.

Then under "Machine" on the VM's window, choose "Seamless mode" or "Fullscreen mode".

You need to have installed the guest drivers on the guest OS to get the most out of the display abilities of VirtualBox.

---

### Post by Gp. on 2009-03-07
Yes, I have done this...but that's not relevant to what I mean...

When I have it fullscreen on another workspace, when I switch to that one, it takes control of my keyboard for Vista, so therefor if I try to switch back to another workspace using my shortcuts, it's not going to work because the commands are being sent to Vista, not ubuntu. If that makes sense?

---

### Post by beno1990 on 2009-03-07
Go to the main VirtualBox window, File -> Preferences -> Input, and then untick auto capture keyboard.

Is that what you meant?

---

### Post by albandy on 2009-03-07
also you can always push "right control key" and then ctrl+alt+left arrow key

---

### Post by Gp. on 2009-03-07
Auto Capture Off fixed it.

Cheers guys!

---

