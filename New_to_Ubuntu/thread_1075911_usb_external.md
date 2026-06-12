---
title: "usb external"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-20
i use a usb external hd to back up my docs.
but i can't fully erase what's on it can i re format it like is done in m$ and wipe it out that way?????

---

### Post by jdrodrig on 2009-02-20
can you explain a bit more, what you mean by "i can't fully erase what's on it"...?

---

### Post by DarinB on 2009-02-20
when i open the external usb drive i see the files when i click select all and delete or move to trash it moves then when i go to the trash  it won't empty completely and the external drive shows about 25 gb of space when it should show about 27.9gb available when it is empty. therefore i am assuming that it is not allowing me to totally dump all the files.
in window$ when that stuff goes on i just refomat the drive and bingo fully empty again.

---

### Post by taurus on 2009-02-20
What filesystem is that external harddrive, ntfs?  Try emptying the trash bin with root privilege.

---

### Post by sandyd on 2009-02-20
format part is easy....

gparted :)

```

sudo apt-get install gparted
sudo gparted

```
delete and recreating the partition should solve the problem.
please check over everything before you click apply. changes are irreversible. 
just create the partition as a ntfs or fat32 disk

done.

---

### Post by DarinB on 2009-02-21
the external drive is ext3.
i set it up a long time ago kinda forgot about it.
when i unmounted it it asked if i wanted to empty the trash, I clicked yes but that doesn't mean it freed up space. i suppose i will check it next time i decide to back up my docs. i wish i had a better back up system. that was more automatic. i have tried the back up programs from synaptic a long time ago but they weren't very satisfactory.
**i am open to suggestions** i do ok with the usb hd but i don't do it very often so if i have a problem i will lose some stuff.
But it is not like windows that gets messed up every few months and needs full reinstall, this thing keeps on running like the energizer bunny.
But i should have some system in place all the same.

---

