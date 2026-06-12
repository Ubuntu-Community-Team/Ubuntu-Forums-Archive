---
title: "Migrating from Mandriva to Kubuntu"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Captain_tux on 2008-12-06
Greetings all!

I have a laptop running Mandriva 2009 One (dual booting with Vi$ta) and I've been having issues with the wireless driver causing kernel panics. See [http://forum.mandriva.com/viewtopic.php?t=100256&start=50]("http://forum.mandriva.com/viewtopic.php?t=100256&start=50") if interested. Since KDE is a must (a new project at works requires me to learn KDE), I'm thinking of installing Kubuntu on top of Mandriva. I've used Kubuntu's LiveCD and everything seems to work well. I have a / partition, along with a separate swap and /home.

How do I install Kubuntu on top of Mandriva?

Are there any dangers of installing Kubuntu on top of Mandriva?

If I do install Kubuntu, will it overwrite Mandriva's **grub** or will it add to it? [And if it does add to it, I can easily edit **grub** and remove the Mandriva entries, yes?]

I'd really hate to leave Mandriva, but the kernel panics (and now being unable to connect at all!) is a show stopper and I need a system that works, not something I have to fight with.

Thanks in advance!

*And yes, I'm already an Ubuntu user... have it on my desktop ;)*

---

### Post by cmay on 2008-12-06
hi.
1 back up back up back up.
then you should be able to install kubuntu instead of the mandriva installation. the grub bootloader is reinstalled by kubuntu . i used to love mandriva also. i had it as my first distro. a couple of years ago. 

hope it helped.

---

### Post by louieb on 2008-12-06
You'll need to use the manual partition option. Just click the Mandrivia partitions  edit them to mount them as / (root) and /home. Check the format box. When the install is finished Mandrivea will be replaced by  kubuntu.

---

### Post by Paqman on 2008-12-06
Try out Kubuntu with the LiveCD first, just to make sure you won't get the same kernel panics on Ubuntu as well.

---

### Post by Captain_tux on 2008-12-06
Thanks everyone who's answered!

So basically, make sure I select **Manual** installation, keep my current partitions, and everything should be ok when it's finished installing?

---

### Post by zvacet on 2008-12-07
Yes,but back up your files from home partition if you want to save any of them.You are going to **format** / and /home witch means files on them will be deleted.

---

### Post by Paqman on 2008-12-07
You don't have to format /home if you don't want to. Just create a new user account with a new name and UID for Ubuntu. This would be useful if you had data in /home that you wanted to transfer to the new system, or if you wanted to reinstall Mandriva and restore your old settings at some later date.

---

