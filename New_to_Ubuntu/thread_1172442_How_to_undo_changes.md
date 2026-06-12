---
title: "How to undo changes"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by natman on 2009-05-28
Hi,
I am thinking about using an intel gfx driver that is experimental, but i want the option to be able to roll back if something goes wrong. Is there a way to roll back changes? ( for sake of a better word like system restore in windows ).
Im looking at this site for the driver [[COLOR="Blue"]driver_page[/COLOR]]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by Didius Falco on 2009-05-28
Hi,

There are a couple of options on how to prepare for problems caused by this:

1. Know the command line commands you need to use to remove this driver and put the known working driver in place. This should include knowing how to completely remove the drivers and any dependencies and configuration info, and how to replace and configure the known good drivers.

I'd write the commands down, so you'd have a plan of action to refer to when you are looking at that big black screen.

2. Use one of the many backup and restore options available to you, so if there is a problem you can't get past, you can just restore your system.

3. If you have the free space, you could also install a second copy of Ubuntu and use that version strictly for testing the bleeding edge drivers. That way, you'd only install them into your default install after you were satisfied that they worked with your setup.

Regards,

Didius

---

### Post by natman on 2009-05-28
Yes, but what exactly are the commands for 1) ? and whats the name of a nice backup/restor tool?

---

### Post by Didius Falco on 2009-05-28
> **natman said:**
> Yes, but what exactly are the commands for 1) ? and whats the name of a nice backup/restor tool?

1. It would be something along the lines of ```
sudo apt-get remove --purge packagename
``` followed by ```
sudo apt-get install packagename
``` and then any configuration that you had to do. I don't use an Intel card, so you'd do better to search the forum for threads by people that do, particularly threads by others using the same experimental driver repos.

2. You can use Partimage, for one. If you have a CD/DVD burner then the link to Remastersys in my signature could be very handy. Remastersys can build a bootable, installable image of your entire system.

Of those two, I'd say that Remastersys is the easiest option. 

There are other options out there, and a quick google will turn up more than the two I've outlined.

Good luck!!

Regards,

Didius

---

