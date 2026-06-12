---
title: "Removing old Kernels..."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by jrenaldy on 2010-01-12
Does anyone know the easiest way to remove old kernels?  After a few Ubuntu updates, I now have two old kernels (w/ safe modes) that seem to be screwing up my OS boot order.  Any suggestions?

---

### Post by drs305 on 2010-01-12
Take a look near the bottom of the guide I wrote on Startup-Manager. You don't need to use Startup-Manager or even Grub legacy. The section is universally applicable. Click on the "SUM" link in my signature line.

Hint: Remove "linux-image-<your old kernels> via synaptic.

---

### Post by tom.swartz07 on 2010-01-12
> **jrenaldy said:**
> Does anyone know the easiest way to remove old kernels?  After a few Ubuntu updates, I now have two old kernels (w/ safe modes) that seem to be screwing up my OS boot order.  Any suggestions?

Easy Peasy.
Mark down what the old kernels are- usually end with 13, 14, 15. The newest one is 16 i believe.

Open synaptic (system>admin>synaptic) and search for linux-image

Remove all but the most recent 2. If you are 100% certain that the newest kernel works on your system, you could remove all up to the latest. if you arent sure, leave the most recent two)

and apply changes.

Thats it!

---

### Post by jrenaldy on 2010-01-12
Thank you so much!

---

### Post by aquascrotum on 2010-01-13
Install Ubuntu Tweak - it allows you to clean up old kernels and is the easiest method I've found as well as being an all round useful tool.

---

### Post by audiomick on 2010-01-13
hey scrote,
can you give us a link to Ubuntu Tweak. Save me searching, I'm a lazy bugger...;)

---

### Post by drs305 on 2010-01-13
audiomick

Hah! I took a look at Ubuntu-Tweak and was impressed enough to return to this thread to add that I have included the instructions for Ubuntu Tweak on my StartUp-Manager "Remove Kernel" instructions.

Although they are in some ways "competing" apps, using Ubuntu Tweak is so easy I wanted to include it in the section on removing kernels. Additionally, it is independent of the version of Grub the user is using, and it only lists the kernels not in use.

You can return to the Startup-Manager link I previously referenced for the complete instructions on how to install and run Ubuntu-Tweak, or you can go to its site, download and run it yourself - it's not hard.  ;-)

Here is the link:
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by audiomick on 2010-01-13
@ drs305
Thank you! Setting bookmarks as we speak...;)

---

