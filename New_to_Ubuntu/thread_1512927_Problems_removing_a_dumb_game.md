---
title: "Problems removing a dumb game"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by rklpro on 2010-06-18
So I've been obsessed with playing poker on my phone and decided to download poker2d for my netbook.  I couldn't configure the network easily so I just decided to uninstall it.  Now, I can't uninstall it, reinstall it, fix broken packages or even run update manager or package manager anymore.

I've tried sudo apt-get remove, sudo apt-get --purge remove and maybe a couple other options.

Thanks in advance.

---

### Post by jtarin on 2010-06-18
> **rklpro said:**
> So I've been obsessed with playing poker on my phone and decided to download poker2d for my netbook.  I couldn't configure the network easily so I just decided to uninstall it.  Now, I can't uninstall it, reinstall it, fix broken packages or even run update manager or package manager anymore.

I've tried sudo apt-get remove, sudo apt-get --purge remove and maybe a couple other options.

Thanks in advance.What method did you use to install it? As a last resort you can run "sudo ubdatedb" from the terminal and when it finishes running issue the command "sudo locate <filename>" . This will show you just about all instances of the file(s).Then remove them .

---

### Post by rklpro on 2010-06-18
I installed using the Software Center and tried to remove it through that and the terminal.  

When I located the files, there's a ton of them.  I wouldn't normally care but everytime I open the Software Center, Package Manager and Update Center, it tries to configure and/or reinstall the dumb network.

---

### Post by jtarin on 2010-06-18
> **rklpro said:**
> I installed using the Software Center and tried to remove it through that and the terminal.  

When I located the files, there's a ton of them.  I wouldn't normally care but everytime I open the Software Center, Package Manager and Update Center, it tries to configure and/or reinstall the dumb network.

Whay's the name of the game? What network?
 If you look at the files there will not be as many as you think because most of them are in their own directories. You can find commandline information for "rm" (delete) from the terminal by typing "man rm" and  [[COLOR="Blue"]here[/COLOR]]("http://www.ee.surrey.ac.uk/Teaching/Unix/unix2.html")

---

