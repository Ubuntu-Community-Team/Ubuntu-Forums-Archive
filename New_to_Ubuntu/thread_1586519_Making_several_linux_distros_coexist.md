---
title: "Making several linux distros coexist"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by mll on 2010-10-02
Hello there,

My question is not specifically a ubuntu one, but i don't know where else to ask, so here it is :

I want to try many different distros and therefore am trying to install them on a VirtualBox, all on different partitions of the same virtual hard drive.

Problem is, while ubuntu and linuxmint coexist gracefully with other distros (they don't erase them from grub's boot sequence), it's not the case for other (such as pclinuxos and mandriva).

Any advice to make a distro install not wipe other distros from the boot menu, or for some magical tool that could detect which distro is on which partition, and rebuild grub's boot menu ?

Thanks

---

### Post by NightwishFan on 2010-10-02
If one of the systems can detect other ones, perhaps install that one last so it controls grub. I am not sure how that will work though, so testing is required.

---

### Post by sikander3786 on 2010-10-02
> **mll said:**
> Hello there,

My question is not specifically a ubuntu one, but i don't know where else to ask, so here it is :

I want to try many different distros and therefore am trying to install them on a VirtualBox, all on different partitions of the same virtual hard drive.

Problem is, while ubuntu and linuxmint coexist gracefully with other distros (they don't erase them from grub's boot sequence), it's not the case for other (such as pclinuxos and mandriva).

Any advice to make a distro install not wipe other distros from the boot menu, or for some magical tool that could detect which distro is on which partition, and rebuild grub's boot menu ?

Thanks
Ubuntu and Grub2 reconginze all my OS without any problems until now. Install Ubuntu at last or, reinstall Grub2 if you install a new OS and it doesn't recongnize already installed distros.

You'll need to boot off an Ubuntu Live CD in the Virtualbox to do that.

---

### Post by HermanAB on 2010-10-02
Howdy, 

I think that you are doing something wrong and something right...

Yes, do use Virtualbox/VMWare Player.

No, don't install them all in the same VM!

Make a new VM for each distro.  You could run them all at the same time if you want, but keep them separate.

---

### Post by mll on 2010-10-02
Thanks guys for your advices.

> **sikander3786 said:**
> Ubuntu and Grub2 reconginze all my OS without any problems until now. Install Ubuntu at last or, reinstall Grub2 if you install a new OS and it doesn't recongnize already installed distros.

You'll need to boot off an Ubuntu Live CD in the Virtualbox to do that.

Well, that's what I had in mind, but it works only if I install no more than 1 "rogue" distro, because if there's a second "rogue" distro, it erases the first one's grub settings.

BTW, how do you "reinstall Grub 2" ?

> **HermanAB said:**
> Howdy, 

I think that you are doing something wrong and something right...

Yes, do use Virtualbox/VMWare Player.

No, don't install them all in the same VM!

Make a new VM for each distro.  You could run them all at the same time if you want, but keep them separate.

Wise advice, but I wanted to make it for the fun of it, and to prepare maybe a future situation when I'll install several distros on a single disk (without a VM, I mean).

---

