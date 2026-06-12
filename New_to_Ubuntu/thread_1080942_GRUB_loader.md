---
title: "GRUB loader"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by cshotwell on 2009-02-25
This is probably posted somewhere, and I am an idiot for not seeing it.

Every time I update Ubuntu (kernel updates I think, but not sure), GRUB loader adds another Ubuntu and safe mode line.  I am up to 4 different sets of this, along with my vista partition and recovery partition.  

My question is how to clean up GRUB loader of all of these lines I do not use. It gets annoying that I now have to scroll to reach my vista partition, and I am completely unfamiliar with boot loaders of all kinds.

I would be happy to provide more clarification if it is needed on his issue, just ask.  Thank you very much, ubuntu support forums haven't failed me yet!

---

### Post by taurus on 2009-02-25
You can go into synaptic and remove the old kernels that you don't need anymore.  Then, install startupmanager to configure your GRUB--/boot/grub/menu.lst.

---

### Post by laidback on 2009-02-26
You might find this helpful:-

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

laidback

---

### Post by freak42 on 2009-02-26
you can edit your grub settings file (menu.lst) to adapt to your needs

first backup

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

then open an editor

```
sudo gedit /boot/grub/menu.lst
```

now there is this config area in the file:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

change the line 
```
# howmany=all
```

to
```
# howmany=1
```

save the file, close the editor
and then issue

```
sudo update-grub
```

hth

---

### Post by Saghaulor on 2009-02-26
Per a previous suggestion, unless you need the old kernel and header versions, remove them via synaptic. Consequently, this will remove a couple hundred megabytes of space and additionally it will remove them from your grub menu.

If they are not removed from your grub menu, manually edit the grub menu. (You don't need startupmanager, as it won't do what you're trying to do in the first place.)

To edit grub do the following.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
gksudo gedit /boot/grub/menu.lst
```

Then remove the entries that you no longer need. Save the file, exit, and when you reboot they should be removed.

---

### Post by cshotwell on 2009-02-27
Thank you very much to all of you! I look forward to being able to solve someone's simple problems someday!

---

