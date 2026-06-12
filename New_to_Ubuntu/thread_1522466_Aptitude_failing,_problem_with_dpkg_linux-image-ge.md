---
title: "Aptitude failing, problem with dpkg linux-image-generic-pae"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by dekz on 2010-07-02
Hi guys,

New to ubuntu and I'm having some problems installing some things using apt-get/aptitude.
Its failing on what seems to the the depackaging of linux-image-generic-pae. Getting /etc/grub.d/10_linux: 123: /boot/vmlinuz-2.6.31-21-generic-pae: Permission denied

here is the pastie with some of the commands I tried and their output.

[http://pastie.org/private/0egqcofl6s28cdxpfiysjw](http://pastie.org/private/0egqcofl6s28cdxpfiysjw)

sed -n 123p /etc/grub.d/10_linux: rel_dirname=`make_system_path_relative_to_its_root $dirname`


Thanks for any help.

---

### Post by sikander3786 on 2010-07-02
Hi.

Are you logged in as root?

Seems like you are trying to install from local disk. And seems like you are getting dependency problems. Why don't you try installing from the repositories? It will automatically solve all the dependencies.

That is only what I could figure out from your paste. Wait for wiser heads if problem remains unsolved.

Regards.

---

### Post by dekz on 2010-07-02
> **sikander3786 said:**
> Hi.

Are you logged in as root?

Yes in the pasted example I'm root, I've also tried all other combinations.

---

### Post by warfacegod on 2010-07-02
Try doing it through Synaptic instead. Any special reason you need the -pae kernel instead of a 64 bit OS?

---

### Post by dekz on 2010-07-02
> **warfacegod said:**
> Try doing it through Synaptic instead. Any special reason you need the -pae kernel instead of a 64 bit OS?

It happens through synaptic also, I can't use any package manager as it still gives the error about the generic-pae. Attempted to upgrade using the in built manager and it failed due to the same problem also. Just a note: I didn't ask it to attempt to install and configure the -pae, it was automatic.

---

### Post by migs73 on 2010-07-02
FYI
If you have a 32 bit machine with 4GB+ memory the PAE kernel is automatically loaded (otherwise you can't use all the memory).

If you don't have that much memory maybe the normal kernel would be sufficient or, if your hardware supports it, try the 64 bit.

NB You'll need to download the 64bit iso for that.

---

