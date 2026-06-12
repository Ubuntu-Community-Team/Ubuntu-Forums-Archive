---
title: "changing the grub boot order"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Johnecash on 2009-10-16
Hi Guys

Any idea how I can change the grub boot menu order? thanks

---

### Post by wojox on 2009-10-16
You may want to download Startupmanager from Synaptic.

---

### Post by Johnecash on 2009-10-19
I thought there was another way - kind of like editing the "boot.ini" file ?

---

### Post by oldfred on 2009-10-19
What is it your want to do? Messing up the menu.lst will cause the system to not boot.

At least make a copy so you have something to go back to:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst

Do not change anything in the automagic area except the ones with one # as they are settings used to rewrite the entire automagic area on every update to the kernel.

If you are not sure what you are doing using startupmanager is safer.

---

### Post by Johnecash on 2009-10-20
i am wanting to put Jaunty release #11 up top of the list
as my release #15 seems to freeze up on the internet some times

---

### Post by swoody on 2009-10-20
As mentioned, create a backup of your /boot/grub/menu.list file **first**

Then edit it with:
```
gksu gedit /boot/grub/menu.list
```

Then look for the entry:
```
Default   0
```

You will want to change this to another entry that you want to boot by default. The first entry in your menu.list will be 'defualt 0', the second entry will be 'defualt 1' and so on. Make the change you want, save the file, reboot and check it out. Let us know if this works or not for you :)

---

### Post by drs305 on 2009-10-20
You can use StartUp-Manager to change the default boot kernel. It's the safest way to do it although editing menu.lst will work as well. 

If you want to try SUM, which has a lot of Grub tweaks in a GUI application, click on the SUM link in my signature line to take you to a guide on it. The guide also gives hints on manual edits of menu.lst.

---

### Post by Johnecash on 2009-10-21
thanks guys - that worked well - for some reason I like Jaunty # 11 the best - its more stable on my computer

---

