---
title: "GRUB question"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Grukmuck on 2009-02-11
im dual booting winxp and ubuntu 8.10 (still), and when i boot up my laptop, i get three options for ubuntu. 1 is Ubuntu 8.10, kernel 2.6.27-11-generic, 2 is Ubuntu 8.10, kernel 2.6.27-9-generic, and 3 is Ubuntu 8.10, kernel 2.6.27-7-generic. they all have the recovery options with them.

this is kind of annoying and i dont want to see the two that i dont boot into. i boot into Ubuntu 8.10, kernel 2.6.27-11-generic. the options went from 7 to 9 to 11 as i updated my system.

i went into file system/boot/grub and opened up menu.lst and i can see the three options at the bottom of the page. i wanna know if i delete those from that list if they will go away when i boot up, or if that will mess something up?

thanks in advanced

-gruk

---

### Post by Tek-E on 2009-02-11
I dont know about deleting them. But I do know that you can comment them out so that they dont show when you startup your computer.

---

### Post by sleepyjon on 2009-02-11
It is probably a better idea to just comment them out.

To do that just put a # in front of any line you don't want to show at boot.

---

### Post by dvlchd3 on 2009-02-11
```
sudo gedit /boot/grub/menu.lst
```
At the bottom you will see the entries.  You can either delete the entries or put '#' infront of the lines you don't use.  I recommend commenting out the lines, this way if you ever have to boot into the previous kernel (for whatever reason), you can just boot in to recovery mode, or use a live CD to uncomment out these lines.  Each option is seperated by a blank line.  Be sure to comment out each line within the block.

It would look something like this:

Before:
```

## ## End Default Options ##
title        Ubuntu 8.10, kernel ....
uuid         .................
kernel       /boot/vmlinuz-............
intrid       /boot/initrd.img.......
quiet

```
After
```

## ## End Default Options ##
#title        Ubuntu 8.10, kernel ....
#uuid         .................
#kernel       /boot/vmlinuz-............
#intrid       /boot/initrd.img.......
#quiet

```

---

### Post by jbrown96 on 2009-02-11
You can safely delete the older kernels. Just keep in mind that they are there for a reason. You will probably never need them, but they may come in handy if your kernel refuses to boot. I don't really find much need for the recovery versions, but it might be handy to leave at least one older kernel. You could change the order if you wanted to, and you could create blank lines by making lines that only contain > title

---

### Post by cjv8888 on 2009-02-11
or install startup manager,(in synaptic) then you can choose how many kernels you see on the grub screen, change the colour or put password on it etc.

---

### Post by Grukmuck on 2009-02-11
cool thanks alot

---

