---
title: "Kernel Update Breaks Programs"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2009-04-17
Hi

Whenever there is a kernel update, VirtualBox and my broadband connection does not work.  I have to start up with kernel 2.6.27-9 instead of kernel 2.6.27-14.  Needles to say, I would like to start up with the latest kernel.

How do I make the kernel work with my existing programs or how do I make for example Virtualbox work with the latest kernel?

Any help will be appreciated.

Thanks

---

### Post by swoll1980 on 2009-04-17
If you didn't use the repos to install the programs, or drivers, an update could break them

---

### Post by mister_pink on 2009-04-17
To elaborate, these both require kernel modules which will need to be added for the new one. For packages installed with apt this is done automatically using dkms, for ones you installed manually you'll need to redo whatever it was you did to get your broadband to work in the first place.

For virtualbox, I seem to remember it gives you a command to run in the error message when you run it to fix it. I think it might be:

```

sudo /etc/init.d/vboxdrv setup

```
but I'm not 100% sure.

---

### Post by Astarroth on 2009-04-17
You are correct. I was running virtual box and after every kernel update I had to run the command. Not a big hassel since it gives you the solution in the error message.

---

### Post by sdennie on 2009-04-17
The above is correct.  You can also automate the building of the kernel modules.  This is what I use to auto-build the virtualbox modules on kernel re-install:

```

$ cat /etc/kernel/postinst.d/update-vbox 
#!/bin/bash

echo "Building VirtualBox driver for $1" >&2
cd /usr/share/virtualbox/src
make clean 2>&1 > /dev/null
make install KERN_DIR=/lib/modules/$1/build KERN_INCL=/lib/modules/$1/build MODULE_DIR=/lib/modules/$1/misc 2>&1 > /dev/null

depmod -a $1

```

---

