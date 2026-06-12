---
title: "Compiling .bin module &amp; Help My Sanity"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-05-22
This is unfortunately a necessarily long post. I'm not a command line beginner, but as to compiling, I'm completely noob. Quotes from others in RED color.

I have an AMD Athlon II X4 620 CPU. That's a 4 core cpu. It requires a module (is that a driver?) named k10temp (or something like that *.ko) to let the panel lm-sensors know the CPU's temperature. Or at least one of them, which is enough for me.

I've waited since Karmic's release for this driver to be in-built in the kernel and it's not happened, so I'm taking the plunge and compiling. Or so I hope.

I've got the K10 'patch' from the author of lm-sensors (at his wiki). That directory is currently in my /home/mark (mark is my first name). I have read & read about compiling. Yet, I cannot come up-to-speed about this. Some of the info could be out of date. Using that info could blow up my production box. I refer to this:

[http://www.linuxforums.org/forum/installation/46122-how-install-bin-file.html](http://www.linuxforums.org/forum/installation/46122-how-install-bin-file.html)

The poster says: 

[COLOR="Red"]You can install it from CUI. Just open a terminal and type this:
Code:
chmod +x file.bin
./file.bin
The installation will then start.

Where the installed files goes depends on which .bin installer it is, however in many cases it will ask where to install.

If you want a system-wide install, do this before typing the above commands:
Code:
su -
password: <enter password>[/COLOR]

that post is from 2005 and isn't about Ubuntu. Or at least no distribution is mentioned.

Next: 

[http://luv.asn.au/overheads/compile.html](http://luv.asn.au/overheads/compile.html)

At least this post helps me know (although I'm guessing) that this type of .bin goes in /bin as it should load at power up

[COLOR="red"]/bin
programs required during startup[/COLOR]

This poster also talks about the necessary packages:

[COLOR="red"]Debian packages: gcc, cpp, binutils, libc-dev. C++ programs also require: g++, and libstdc++
[/COLOR]

Is the foregoing correct for a .bin, .ko, .c, .mod.c, .mod.o, symvers, and .order?

and from:

[http://www.howtoforge.com/kernel_compilation_ubuntu[/COLOR]"]How To Compile A Kernel - The Ubuntu Way]("[COLOR="red")

I read:

[COLOR="red"]I prefer to do all the steps here as the root user. So if you haven't already created a root login, you should do so now:
sudo passwd root
Afterwards, log in as root:
su
If you would like to work as a normal user instead of root, remember to put sudo in front of all the commands shown in this tutorial.
[/COLOR]

But my understanding of compiling is that Make does not take su OR sudo. So, if I follow this posters words what would happen to my temperature module? or driver? or what ever it is?

And I've never heard of this --dry-run before, so as this info is from a post talking about Dapper Drake, is this still applicable?

[COLOR="red"]4 Apply Patches To The Kernel Sources (Optional)
Sometimes you need drivers for hardware that isn't supported by the new kernel by default, or you need support for virtualization techniques or some other bleeding-edge technology that hasn't made it to the kernel yet. In all these cases you have to patch the kernel sources (provided there is a patch available...).

Now let's assume you have downloaded the needed patch (I call it patch.bz2 in this example) to /usr/src. This is how you apply it to your kernel sources (you must still be in the /usr/src/linux directory):

bzip2 -dc /usr/src/patch.bz2 | patch -p1 --dry-run
bzip2 -dc /usr/src/patch.bz2 | patch -p1

The first command is just a test, it does nothing to your sources. If it doesn't show errors, you can run the second command which actually applies the patch. Don't do it if the first command shows errors![/COLOR]

I would like to use the --dry-run very much!

Next, from a post about the k10 temperature module, I read:

[COLOR="Red"]sudo cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon[/COLOR]

[http://stochasticflux.com/blog/?p=13](http://stochasticflux.com/blog/?p=13)

Above reads: "$(uname -r)" 

My terminal says: uname -r is 

2.6.32-22-generic

so I put 2.6.32-22-generic where the uname -r is but do I keep the ( and ) or not?

---

### Post by -humanaut- on 2010-05-22
Have you thought about updating to Lucid I believe it has the proper "drivers" my k8temp works under lucid atleast.

---

### Post by Mark_in_Hollywood on 2010-05-22
> **-humanaut- said:**
> Have you thought about updating to Lucid I believe it has the proper "drivers" my k8temp works under lucid atleast.

Thanks for catching that.

THIS IS LUCID LYNX ver. 10.04.

and for a fact, (see the signature on my posts, below, too.) 

This is an AMD Athlon II X4 620 (Propus) CPU. It requires the K10Temp for LM-Sensors to give a reading.

---

