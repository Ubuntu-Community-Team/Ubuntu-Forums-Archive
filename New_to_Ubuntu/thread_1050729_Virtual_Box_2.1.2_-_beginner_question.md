---
title: "Virtual Box 2.1.2 - beginner question"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Orographic on 2009-01-25
Hi all,

I've installed Virtual Box again after having problems in 2.1 with kernel panic upon shutdown.

This time I've installed VB 2.1.2 via the .deb file from the Virtual Box website. Have installed XP and guest additions and all seems well as present. I have IE6 and Safari installed for web design work.

My questions:

I've entered this line into terminal:

gksudo gedit /etc/apt/sources.list


then added this line to my sources list. 

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free

then I installed Virtual Box 2.1.2

Does that seem right?

What does adding that line to my sources list do? Is it for updates?

---

### Post by zvacet on 2009-01-26
There is nothing wrong with it,and you will probably geting updates like from any other repo.

---

### Post by GirionSoft on 2009-01-26
You are all set I have the same setup for vbox and received an update the other day.

---

### Post by Orographic on 2009-01-26
Thanks folk. I get something like this when I update Add/Remove.

'W:GPG error
[http://downloadvirtualbox.org](http://downloadvirtualbox.org) intrepid release:

The following signatures could not be varified because the public key is not available.'

Is that okay? Should I install the public key? how?

---

### Post by Orographic on 2009-01-27
I just added the public key link into my terminal from this page for intrepid. I think that is the right thing to do.


[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


Does this issue below need to be also addressed? And how?


'Note: Ubuntu users might want to install the dkms package (not available on Debian) to ensure that the VirtualBox host kernel modules (vboxdrv and vboxnetflt) are properly updated if the linux kernel version changes during the next apt-get upgrade.'

---

