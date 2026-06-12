---
title: "System Information"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-08-31
Hi

In Windoze I could get system information like what my graphics card was and hard drives etc 
Where do I get this information from in linux?
I want to find out what graphics card I have to see if it needs updating which then might stop the freezing system problem

Thanks

---

### Post by Liolikas on 2009-08-31
lspci shows all pci devices.
lspci | grep VGA
Shows only card VGA.

---

### Post by credobyte on 2009-08-31
The easiest way is to use hardinfo ( install from repositories ). If you want to do it manually, lshw/lspci/lsusb/lshal ( in terminal ), etc.!

---

### Post by wojox on 2009-08-31
I like:

```
sudo lshw
```

---

### Post by Kristofer Van Orton on 2009-08-31
Usually how I deal with this sort of thing is use google
for example if it were my computer i would search
**Acer Aspire x1200 specs**

obvisouly use your own make/model in the search and you should find a list of the hardware configuration in your system

---

### Post by Wim Sturkenboom on 2009-08-31
> **Kristofer Van Orton said:**
> Usually how I deal with this sort of thing is use google
for example if it were my computer i would search
**Acer Aspire x1200 specs**

obvisouly use your own make/model in the search and you should find a list of the hardware configuration in your system

Will really work well if you have a 'custom made' system that was given to you. ](*,)

---

### Post by nhasian on 2009-08-31
that might give you the general specs of the pc like hd size, but it wont give you the manufacturer of the HD for example, or the wifi adaptor, etc.

```
sudo lshw
```

you can specify which category you want like

```
sudo lshw -C display
```



> **Kristofer Van Orton said:**
> Usually how I deal with this sort of thing is use google
for example if it were my computer i would search
**Acer Aspire x1200 specs**

obvisouly use your own make/model in the search and you should find a list of the hardware configuration in your system

---

### Post by d_yat on 2009-08-31
> **Anybloodyid said:**
> Hi

In Windoze I could get system information like what my graphics card was and hard drives etc 
Where do I get this information from in linux?
I want to find out what graphics card I have to see if it needs updating which then might stop the freezing system problem

Thanks

For a solution that is like windows, try installing a program called "sysinfo" This gives you a nice menu entry under the "system menu".
which then loads a graphical window, with all the info you could ever need =)

(you should be able to find "sysinfo" in the add/removes programs list)

hope that helps =D

---

### Post by jmszr on 2009-08-31
Anybloodyid,

I've found this useful:```
sudo apt-get install gnome-device-manager
```

After installation you will find it under Applications > System Tools > Device Manager.

---

### Post by Anybloodyid on 2009-08-31
I'll say this about ubuntu, it sure has a lot of support.
Thanks to everyone

Here's what I ended up with

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=66 mingnt=8

---

### Post by 3rdalbum on 2009-08-31
> **Anybloodyid said:**
> I'll say this about ubuntu, it sure has a lot of support.
Thanks to everyone

Here's what I ended up with

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]

ATI doesn't support their Xpress 200M graphics chips anymore, so the driver that Jaunty ships with is *the* driver for it.

---

### Post by Anybloodyid on 2009-08-31
OK everybody thanks for all the advice and help

---

