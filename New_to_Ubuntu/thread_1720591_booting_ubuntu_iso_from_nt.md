---
title: "booting ubuntu iso from nt?"
date: 2011-04-03
forum: New to Ubuntu
---

### Post by operaytor on 2011-04-03
How do I boot an ubuntu iso without burning it onto media? 
I need to boot from Win2k, i.e. not from grub.

---

### Post by Dutch70 on 2011-04-03
With Wubi.
[[COLOR="Red"]https://help.ubuntu.com/community/Wubi[/COLOR]]("https://help.ubuntu.com/community/Wubi")

Notice in that link where it says...
> Download Wubi from the Ubuntu Windows Installer Download page, this will download the latest LTS version. **You can download other versions from the Ubuntu pages on releases.ubuntu.com, e.g. 10.10, look for wubi.exe** at the bottom of the page. Wubi is also included on Ubuntu Desktop and Kubuntu CDs. 

You should be able to download the wubi.exe and run it from within windows.

---

### Post by bodhi.zazen on 2011-04-03
If all you want is to boot the iso (Live CD) and not install, then use unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You would then plug in the usb and reboot, set your bios to boot from usb.

If you want to try Ubuntu without rebooting then look at Virtualbox.

If you want to install ubuntu, and use the windows boot loader, then use wubi as suggested above.

---

### Post by operaytor on 2011-04-03
What I need is a way to "jump" into the LIVE CD 
menu without burning the iso onto CD. So ideally
I would add a line in boot.ini to jump into the livecd
screen from the Windows boot screen. Is it possible?
If not, I don't mind using a boot CD, that will be able
to jump into the LiveCD menu. The boot cd will be
very minimal, probably just an initrd system, that
will somehow mount the iso and start it?

---

### Post by bodhi.zazen on 2011-04-03
You would need to ask on a Windows forums, but I do not think the windows boot loader will boot an iso.

What are you trying to achieve ?

---

### Post by operaytor on 2011-04-03
They do it in Slax, you just boot a minimum cd which 
just has lilo on it, then you can start your slax iso
without burning it.

---

### Post by bodhi.zazen on 2011-04-03
I guess I am not understanding what you are wanting to do.

Boot and iso with the windows boot loader ?

You can boot some iso directly with some boot loaders, grub 2 will do it as well.

But the iso needs to be customized to do this, and the ubuntu iso is not so customized.

Not knowing what you want exactly it is hard to advise a resolution.

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

Note: If you read the fine print you will see that the grml iso has been modified (as has the slax iso) to allow booting the iso from the hard drive. Wolvix used to do this as well.

I have no idea what you have against grub 2 either =)

---

### Post by bodhi.zazen on 2011-04-03
Booting an iso is not the problem, the iso much be modified to boot that way. I do not know the customizations that make that possible.

"Demand" for this technology (booting and iso) has been low because most people are booting a usb.

If you do not like the Ubuntu menu, you would need to customize the iso.

---

### Post by operaytor on 2011-04-03
I explain in more detail,

I just downloaded the ubuntu iso onto my w2k desktop.

I just though it would be cool if I could "start" this iso
so that I could be straight away with the menu that 
we get when we put an ubuntu cd in the tray and boot
it. I think the first menu item is to try the cd without
install (i.e. live cd), the second item is to install (I do
not want to install anything, I don't want to touch my 
harddisk _at_all_ , then you have some other entries
like ram test etc. So this is the menu I was talking about.

Then I thought, because of your response, that was 
probably not possible, or not logical, so I remembered
how they done it on Slax. In slax, you have two directories,
one is called Boot, the other Slax. The Boot directory is 
what is resposible for the first screen where you choose
what you want to start off. The Slax directory is where
the real system is stored. If you delete the Slax directory,
all you can do is boot into this first screen,
and after this nothing will work. Now comes the Slax trick,
if you still have your slax iso on your harddrive, it does
not matter that you deleted the Slax directory, because you
can add to the boot command line

from=/slax-6.1.2.iso

and voila, slax will know to boot from it - This is what I need for
ubuntu as well.

---

### Post by bodhi.zazen on 2011-04-03
For that you would need to build a custom ubuntu iso.

I do not know the modifications you would need to make to do that, you could look at the grml iso as it is probably closer to the ubuntu iso then a slax iso.

[http://grml.org/](http://grml.org/)

---

