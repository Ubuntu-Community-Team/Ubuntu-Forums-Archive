---
title: "Copying files to restricted folder? (Ultimate noob question, I'm sure)"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by danielgrosvenor on 2010-06-06
I need to copy two files from my desktop into the /etc/acpi folder, but dragging and dropping (and copying and pasting) won't work because it says access is denied.

Presumably this means I need to open Terminal and give a sudo command, but could I please ask exactly what the command is to copy something from the Desktop to a specific folder?? :oops:  I'm still getting my head around paths and directories under Linux.

---

### Post by Hygaphunkik on 2010-06-06
Try typing

sudo nautilus

into terminal.

It should open up a file explorer that allows you to drag and drop all kinds of things to the most secret of places. Do be careful though, I once renamed some files using htis and completely banjacksed my machine.

---

### Post by Paqman on 2010-06-06
> **Hygaphunkik said:**
> 
sudo nautilus


For all GUI apps you should use gksu. Use sudo only on the command line. The correct command is:
```
gksu nautilus
```

---

### Post by wojox on 2010-06-06
There's also:

```
sudo cp <filename> /etc/acpi
```

---

### Post by danielgrosvenor on 2010-06-06
Thanks for introducing me to Nautilus!  This will be a lifesaver. :)

---

### Post by baddnady23 on 2010-06-06
> Thanks for introducing me to Nautilus! This will be a lifesaver.

I doubt that this is your first introduction to it, your just learning to use it as "root" now which gives you administrative privileges in it.  Nautilus is actually what you've probably been using all along to browse the files in Ubuntu.  Compare it to windows explorer... :P

---

