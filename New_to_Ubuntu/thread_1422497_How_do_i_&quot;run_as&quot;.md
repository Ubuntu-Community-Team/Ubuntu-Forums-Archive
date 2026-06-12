---
title: "How do i &quot;run as&quot;?"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by TechDragon on 2010-03-05
I am trying to install the virtual box guest additions piece, when I click on install guest additions a cdrom appears on the desktop.  I go into the cdrom and can see the file I want to run, I double click it and it says I must be an admin, is there a way to add a "run as" feature to the context menu?

I know how to install these the long way by opening a terminal and sudo-ing to the file and then running it.  But having a "run as" option would be great, if it is possible how do i add this functionality?

Thanks

---

### Post by abarilla on 2010-03-05
There's no way currently, but there is a related brainstorm: [http://brainstorm.ubuntu.com/idea/3145/](http://brainstorm.ubuntu.com/idea/3145/)

FYI: gksu is the gui version of sudo.

---

### Post by J V on 2010-03-05
sudo = run as, gksudo is graphical version... just run gksudo...

I assume its ubuntu in the vbox?

Edit: Abrillia led me to [this]("apt:nautilus-gksu")

---

### Post by superbenny on 2010-03-05
Not sure about adding it to the context menu, but a simple way around it is this:
Alt+f2 (open a run dialogue box)
type "gksu "FILE_PATH_NAME"
hit enter
enter your password, and you're good to go.

I guess the best way to describe this is like UAC in Vista, but much less annoying. gksu allows you to run graphical apps as the superuser (su) using a gui password prompt.

---

### Post by mkvnmtr on 2010-03-05
On the host have you added yourself to the vbox group in users andgroups?. On my 9.04 hows when I run a Ubuntu guest a simple right click gives me the option to execute a .sh install file. On some other guests I have to be more inventive.
Maybe you  should tell us your host and guest.

---

### Post by juancarlospaco on 2010-03-05
lol, theres the Nautilus plug-in that allow that feature, nautilus-gksu 
:)

---

