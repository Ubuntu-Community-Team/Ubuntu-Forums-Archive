---
title: "Changing my 'name'. And deleting a GRUB entry"
date: 2011-04-08
forum: New to Ubuntu
---

### Post by whonut on 2011-04-08
Hi, 

I just installed ubuntu on my laptop, and there are a few 'loose ends' I need help tying up.

Firstly, on my About Me page it says I'm 'Person A' (not really, don't want to put names up) but Person A is my Dad, and the user account name of my vista installation. How can I change that? Just to make it clear, it's not my username, it's what Ubuntu's displaying as my name at the top of the About Me page.

Secondly, When I boot through GRUB, I for some reason have 2 ubuntu boot options as well as my vista install, but the 2nd one is useless and I want to get rid of it, how would I do that?

Thanks

---

### Post by Dutch70 on 2011-04-08
Probably easiest to install Ubuntu Tweak to get rid of your older grub menu entries. It is a good idea to keep 2 entries though, in case you have a problem with one of them. 

If you don't want to install Ubuntu Tweak, go to synaptic package manager and search for "image-2" it will bring up all your kernels. Tick the one you want to remove, mark it for removal and click apply. Be sure you don't remove the wrong one!

---

### Post by Frogs Hair on 2011-04-08
You can change your name from Administration > Users and Groups and for removing old kernel entries I use the package cleaner from Ubuntu Tweak . Some users like to keep two kernel entries as an extra boot option just in case. There are other methods to remove old kernel entries and a forum search will provide other options. [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by whonut on 2011-04-08
thanks for the replies

I can't seem to find out how to clear the GRUB entry. Just to say, the entry isn't actually working, when I go to boot into it it asks me to insert boot media etc. I don't know how it got there but there is no OS there it's completely blank

---

### Post by Frogs Hair on 2011-04-08
What does the Grub entry say exactly ?

---

### Post by whonut on 2011-04-08
it just says 'ubuntu', as does my working ubuntu install's entry. Or do you mean what happens whwn I select it?

---

### Post by PPN13 on 2011-04-08
If the operating system is not there.
Run this on a terminal **sudo update-grub**
It will search your PC for installed operating systems and remake the grub boot menu (removing entries for non existent OS in the process).

---

### Post by whonut on 2011-04-08
thanks for the replies, problem solved

---

