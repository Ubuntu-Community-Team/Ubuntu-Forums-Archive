---
title: "CD needed for updating?!"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by stamatiou on 2010-11-28
Hey guys, I may switch to ubuntu (I have a laptop, I dont know if that matters)but a friend of mine has kubuntu and whenever he is making updates and such stuff he has to insert the live cd........
Is it really like this in ubuntu or I my friend  has done a mistake:KS:popcorn:?

---

### Post by andrewthomas on 2010-11-28
You would just need to uncheck the cd in software sources

---

### Post by Rex Bouwense on 2010-11-28
Ubuntu gets its updates from the Internet.  There is no need to reinsert the installation CD unless he has a persistent install on the CD.  I have heard of that but have no knowledge of the details.  Once you have the OS on your computer, you should not need the installation CD again (unless you break the system and have to re-install.);)

---

### Post by stamatiou on 2010-11-28
> **andrewthomas said:**
> You would just need to uncheck the cd in software sources
Are you a Kubuntu user?

---

### Post by Old_Grey_Wolf on 2010-11-28
Oops..double post.:oops:

---

### Post by Old_Grey_Wolf on 2010-11-28
> **stamatiou said:**
> Is it really like this in ubuntu or I my friend has done a mistake

> **andrewthomas said:**
> You would just need to uncheck the cd in software sources

Here is a little more information on how your friend can do this.

Open a terminal and type "gksudo synaptic" (without the quotes), and enter the user password. When the Synaptic Package Manager window opens, use the menus on that window to select "Settings > Repositories". Near the bottom of the window that is displayed there should be a box with something about installing from CD-ROM/DVD. There should be a check box for the CD. Remove the check from the box.

After doing this it will not ask for the CD anymore.

---

