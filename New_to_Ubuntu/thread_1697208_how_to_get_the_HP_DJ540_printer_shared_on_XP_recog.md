---
title: "how to get the HP DJ540 printer shared on XP recognised?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by mastablasta on 2011-02-28
Ubuntu recognises it nicely, but not Kubuntu. i am not sure what i would have to do to see the printer connected to XP. 

What if i installed Ubuntu application for printers? Would that help?

Attaching a picture where most things that i can set up in sharing are greyed out.

---

### Post by mastablasta on 2011-03-01
I received this advice on KDE forums:
> 
You may need to go into CUPS (not accessible through System Settings, your distro may have a configuration tool for it) and enable network sharing. Samba usually has network sharing for printers enabled by default.

 
What configuration tool does Kubuntu use?

---

### Post by mastablasta on 2011-03-02
Ok this officially sucks. I managed to solve this but it's really a stupid way of doing this. ofcourse everything is done in system settings->printers menu. you have to select the SAMBA printer, and here comes the good part - to find it you need to know exactly where it is. if you are like me you probably don't know how to find this information as well as how to get the printer name.
 
anyway my solution was to open an Ubuntu computer connected ot same network and then type the path shown there into KDE. but seriously this should be done way more easier. sometimes i wonder if anyone even tests this Kubuntu before they release it out to the public.
SAMBA didn't work out of the box because a package was missing (there was no info that package is missing) and now this (windows printer can't be easilly seen simply because you don't have any option to browse to it from menu).
 
KISS should be the main guidance when creating an OS GUI.
 
/rant off

---

