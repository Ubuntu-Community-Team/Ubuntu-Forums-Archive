---
title: "Grub and kernel issues and question."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by navic101 on 2009-02-13
Hi,

I have Hardy which is all set up until recently when i decided to try to install virtualbox.

This changed my kernel to open vz and messed up my system something awful. I found by going into grub and selecting the 8.0.4.2 kernel 2.6.24-23 generic then it boots up and everything is back as it should be.

The question is

1. Is it safe to uninstall the VZ kernel from synaptic. I don't want to make my system unbootable.

2. Will this then default to my desired kernel or do i have to start altering the command line?

Or should i leave the VZ kernel and just alter something to get it to boot the generic.


Many thanks..

Peter

---

### Post by drs305 on 2009-02-13
I don't understand the "set the kernel to open vz" but you can safely uninstall kernels via synaptic. It won't allow you to uninstall the currently-used kernel. Additionally, when you uninstall a kernel via synaptic, it will automatically remove that kernel from menu.lst. That should restore the default to either whatever is listed first in your grub menu or what is set as the default.

You can also install startupmanager (sudo apt-get install startupmanager) or via synaptic and set the default OS or kernel from there. StartUp-Manager is accessed via System, Administration, StartUp-Manager. There is a link to the tutorial in my signature line.

---

### Post by eragon100 on 2009-02-13
To be safe, don't remove the kernel. You can easily set the other one as default.

Go to add/remove software, search for, and install "start up manager".
Then go to system -> administration -> startup manager, type in your password. In the window that appears select the kernel you want as default under "Default Operating System". Then click close in the right bottom corner, and from now on, that kernel will be set as default.

---

### Post by navic101 on 2009-02-13
Thanks thats done the trick!

Much appreicated

---

