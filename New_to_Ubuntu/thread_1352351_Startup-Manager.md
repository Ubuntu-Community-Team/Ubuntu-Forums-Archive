---
title: "Startup-Manager"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-12-11
Hi

On Jaunty I had Startup-Manager installed and it allowed me to choose the no. of kernels displayed at grub boot, whether I wanted memtest or recovery mode displayed at all etc.

However since installing Karmic most options relating to the OS selection screen seem to have disappeared, apart from the time the list of OS's is displayed.

Is there an alternative application to do the tasks I need?  I'm already up to a screenful of kernels etc when I'm booting up.

---

### Post by metalf8801 on 2009-12-11
It looks like you can still install StartUp-Manager usings synaptic Package manager 

System > Administration > synaptic Package manager  
then search for startupmanager with no spaces 

I hope this helps 
Dan

---

### Post by oldos2er on 2009-12-11
If you did a clean install of 9.10, you now have grub2 instead of grub legacy. Startupmanager has not yet been updated to work fully with grub2.

---

### Post by northern lights on 2009-12-11
> **aquascrotum said:**
> Is there an alternative application to do the tasks I need?  I'm already up to a screenful of kernels etc when I'm booting up.

You can manually edit the grub menu.

It resides in */boot/grub/menu.lst*

i.e. run```
gksu gedit /boot/grub/menu.lst
```

It is advisable to make a backup copy before editing files with system relevancy.```
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup
```

---

### Post by fbugnon on 2009-12-11
Hi,

I don't know of any application for this task.  But what you can do to clean up the Grub is edit the file /boot/grub/grub.cfg (that replaces /etc/grub/menu.lst) and add some comments (#) to the kernels to hide.

[[IMG]http://brainstorm.ubuntu.com/idea/22422/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22422/)

---

### Post by bacardiandwatermelon on 2009-12-11
You could always remove the old linux-image packages you don't want anymore...

---

### Post by durand on 2009-12-11
> **bacardiandwatermelon said:**
> You could always remove the old linux-image packages you don't want anymore...

If you go to System > Administration > Computer Janitor, you can do that and more there.

---

### Post by slumbergod on 2009-12-11
I have startup-manager installed via the repo in Xubuntu Karmic. Seems to be working for me though admittedly, its one of those things that when I have it set how I want it I don't touch it again.

---

### Post by wilee-nilee on 2009-12-11
Ubuntu tweak will clean your download cache, remove the old kernels, add PPA repos and keys and edit your apt/sources.list and change your desktop and other things get the PPA.
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by aquascrotum on 2009-12-12
Thanks for all the help folks.

The reduced functionality is indeed because of my clean install of Karmic & Grub2.

I've installed UbuntuTweak and removed redundant kernels, thanks for the heads up on that...am not too keen on resorting to text editing grub config files (am quite happy being a novice and have no desire to get into the back end of things).

If Startup-Manager is updated to include full grub2 configuration, will that come through Karmic updates or will it be held up until the next Ubuntu release a la Openoffice, firefox releases etc?  I still think it's a useful tool to have.

Oh and

> If you go to System > Administration > Computer Janitor, you can do that and more there.

Computer Janitor didnt flag up any old kernels for removal, despite me having everything there since about a week after Karmic was released.

---

### Post by wilee-nilee on 2009-12-12
Ubuntu Tweak is the lazy installers and maintainers tool It is always my first install. ;)

---

### Post by Kevbert on 2009-12-12
Startup-Manager is not working very well at the moment in Lucid. Grub2 has been updated to a full release (not sure about Karmic, it was still beta when I last tried it). Floppy support is a problem in Lucid (Ubuntu but not Kubuntu) and choosing the OS to boot is also failing.

---

### Post by aquascrotum on 2009-12-12
Edit - posted in wrong thread ](*,)

---

### Post by wilee-nilee on 2009-12-12
> **aquascrotum said:**
> If I install TB3 will it pick up my TB2 profiles, mail accounts etc or will I need to import / export them from TB2?

When I installed the PPA version it loaded everything, but that is my own experience.

---

