---
title: "Backup Options"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by leonhart83 on 2008-12-27
Hey Guys,

I am new to Ubuntu and new to the forums. I purchased the Official Ubuntu guide just recently and thought that I might have a play around over the holidays with this OS.

I have been using Sun xVM VirtualBox with a 10 gig partition to give it a go. After using it I am extremely impressed and I am thinking that I might eventually want to have it as my only OS. 

I was wondering whether or not there are any options for creating a disc with all of the settings and modifications I might make during my study etc that I can use to install the OS when I am happy I have it setup how I like on the Virtual Machine?

This way I won't have to download all the apps and resetup the system when I decide to partake in this process.

Thanks,

Micky.

---

### Post by billgoldberg on 2008-12-27
I would say use the clonezilla live cd to ghost your drive.

But I doubt it will work for virtualbox drives.

I'm intresting on how to do this, I'll be watching this thread.

---

### Post by scorp123 on 2008-12-27
> **leonhart83 said:**
>  I was wondering whether or not there are any options for creating a disc with all of the settings and modifications I might make during my study etc that I can use to install the OS when I am happy I have it setup how I like on the Virtual Machine?
Search these forums for **remastersys** ... It creates a bootable DVD out of your installed OS incl. all customisations you may have done.

The fact that you installed Ubuntu inside a VirtualBox VM should be irrelevant. From remastersys' point of view it's as if you are installing your customised Ubuntu on a "new PC" with slightly different hardware (the scenario when moving a virtual machine to a real PC is the same).

External link:

"Transforming your Installation Manually into a Live DVD/CD"
[http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html)

---

### Post by Joao Paz on 2008-12-27
Scorp123,

Great find, thanks :)

---

### Post by mapes12 on 2008-12-27
To keep personal settings, all your files, firefox bookmarks etc. just keep a backup of /home. To keep a backup of all your installed packages inc updates and any applications you have installed then burn an [aptonCD/DVD.]("http://aptoncd.sourceforge.net/")

---

