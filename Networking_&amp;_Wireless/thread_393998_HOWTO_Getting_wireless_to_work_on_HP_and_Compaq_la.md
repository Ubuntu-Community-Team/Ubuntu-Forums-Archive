---
title: "HOWTO: Getting wireless to work on HP and Compaq laptops"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by elizleisndahizle on 2007-03-26
First thing you need to do is go to [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and get the latest stable version of ndiswrapper.  All versions after 1.30 should work.

Open a terminal and run:
sudo apt-get remove ndiswrapper
sudo apt-get install build-essential

You should have everything you need.

Extract ndiswrapper and cd into the directory its in.
type the following commands into your terminal:
./configure
make
sudo make install

After that install your windows drivers and you will have working wireless.

A really easy solution that it took me 6 months to figure out.

Good luck!

---

### Post by puqing on 2007-03-26
Just for your reference. I have a Compaq Presario  v3000 laptop and installed Fiesty. I am using "ndiswrapper-common" and "ndiswrapper-utils-1.9" packages from the repository and they work well. As I remember, I used "ndiswrapper-common" and "ndiswrapper-utils-1.8" packages on Edgy and the wireless also worked. So, it might be unnecessary to compile the  ndiswrapper from source.

---

### Post by elizleisndahizle on 2007-03-27
They don't work at all on the DV9000z.

---

### Post by frank_costanza on 2007-03-30
How do you install the windows driver? Is there a GUI interface to do it?

I followed a different set of instructions where I had to do a cab extract to get the .inf and .sys files (I think those are the right extensions) from the Compaq Broadcom driver executable.

I can't remember the rest of the steps in the guide offhand. But the result is that when I log in now, the desktop never appears. The Ubuntu brown background is displayed and after some seconds, a medium-size blank gray box appears in the upper left corner....and then nothing.

I don't know how to rollback all of the changes I did by following the guide (there were some scripts that may have done things I don't know about).

Anyway, when I get around to it, I'll reinstall Feisty and try your steps.

But if you could expand on how to actually install the Windows driver, I'd appreciate it.

The only things stopping me from moving to Ubuntu full-time are wireless and APCI support!  Hopefully I can get them worked out.

---

