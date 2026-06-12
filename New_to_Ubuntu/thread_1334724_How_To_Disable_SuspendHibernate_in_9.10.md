---
title: "How To Disable Suspend/Hibernate in 9.10?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2009-11-22
I've gone to gconf-editor and unchecked Can Suspend/Hibernate in gnome-powermanager.  I still have the options in my "start" menu.  Is there something else I need to do?

I'm having a ton of problems in 9.10 that I didn't have in 9.04, BTW.  Frustrating, frustrating...

---

### Post by Jon Monreal on 2009-11-23
You could try this:

> I had problems with a couple of my old machines resuming from suspend/hibernate. I couldn't seem to fix that so I just disabled the functions by editing /etc/default/acpi-support and commenting out the lines for ACPI_SLEEP and ACPI_HIBERNATE per the instructions in the file. After restart there are no more menus for either function.

Source: [http://ubuntuforums.org/showthread.php?t=440225](http://ubuntuforums.org/showthread.php?t=440225)

---

### Post by sldavid on 2009-11-23
I set the power management option - put computer to sleep when inactive for - to never and this has worked well. My laptop has never suspened or gone into hibernation.

I'm using the options located at preferences > power managment,

---

