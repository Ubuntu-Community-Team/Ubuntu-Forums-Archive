---
title: "Partition questions..."
date: 2009-10-26
forum: New to Ubuntu
---

### Post by mesmith on 2009-10-26
I have a system that currently has 3 partitons.  One contains my current xubuntu, another is swap, and the third is actually unallocated space, but equal in size the the main linux partiton.

Can I install another version of xubuntu to the unallocated space, and if I do, will the two linux versions be smart enough to share the single swap area?  And after the install of a second linux version, will dual booting be automatically set up?

---

### Post by alphaniner on 2009-10-26
> Can I install another version of xubuntu to the unallocated space

Yes.

> will the two linux versions be smart enough to share the single swap area

I think it depends on how you do the partitioning step.  But in general, multiple installs can share swap.  Keep in mind this can affect things like suspend or hibernate.

> And after the install of a second linux version, will dual booting be automatically set up?

With ?Ubuntu's installer, yes.  Not necessarily so with all Linux installers I think.

---

### Post by martrn on 2009-10-26
> **mesmith said:**
> I have a system that currently has 3 partitons.  One contains my current xubuntu, another is swap, and the third is actually unallocated space, but equal in size the the main linux partition. Can I install another version of xubuntu to the unallocated space, and if I do, will the two linux versions be smart enough to share the single swap area?  And after the install of a second linux version, will dual booting be automatically set up?

Yes all linux kernels will look for linux swap and use the linux swap for linux swap file space.  Usually this is ok unless you have some very strange hibernation sequence.  

You can install xubuntu to the unallocated space, if your BIOS recognises it.  Dual booting may be set up if the ubuntu installation routine recognises it and/or you select the correct drive to store you /boot kernel images to, and where grub part II is installed.  If it does, it will be ok, else it will boot, but you would manually need to update your grub or change it when you first boot your second linux version, so that it works.

What don't you put a different version on or else you just have to identical versions of the same OS.  What about [Lubuntu]("https://wiki.ubuntu.com/Lubuntu")?

---

### Post by running_rabbit07 on 2009-10-26
> **mesmith said:**
> I have a system that currently has 3 partitons.  One contains my current xubuntu, another is swap, and the third is actually unallocated space, but equal in size the the main linux partiton.

Can I install another version of xubuntu to the unallocated space, and if I do, will the two linux versions be smart enough to share the single swap area?  And after the install of a second linux version, will dual booting be automatically set up?

Usually, multiple Linux distros have no problem sharing the Swap drive.

As long as both installs are Ubuntu/Xubuntu/Kubuntu, they will usually show up correctly on the boot menu, if not it will be an easy fix. Just post a Q here.

---

