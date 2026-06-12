---
title: "lost grub entry for ubuntu 9.04"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by niket_a on 2009-11-02
Hello all
I installed **ubuntu server 8.04** on my desktop which already had **windows vista** and **ubuntu desktop edition 9.04**

now after installing this server edition at boot time i get only 2 options 
1.   for windows vista
2.    newly installed ubuntu server edition 8.04

i cannot excess my ubuntu 9.04 since entry isn't there
   
   **please help me out since i have lot of imp data on my ubuntu desktop partition**

Yours faithfully
niket

---

### Post by LewRockwell on 2009-11-02
compare the /boot/grub/menu.lst file you find in your 9.04 partition and your 8.04 partition

editing will probably be required but is relatively simple

.

---

### Post by niket_a on 2009-11-02
hey thanks mate for a quick reply
so how should i do that
Kindly elaborate on that

your faithfully
niket

---

### Post by kansasnoob on 2009-11-02
I'd boot the live CD choosing "Try Ubuntu without changes to disc", then you need to know what OS is installed in what partition.

If you need help with that post the output of:

```
sudo fdisk -l
```

(BTW that's a lower case L)

And any knowledge you have regarding the partitions.

Anyway from terminal in the live desktop if you run:

```
sudo grub
```

Will drop you into a grub shell, then if you run:

```
find /boot/grub/stage1
```

You'll probably see two options like:

> **Example only!**
grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,4)


Whichever of the two is 9.04 is the one you want to use for the next commands:

**Example:**

```
root (hd0,2)
```

```
setup (hd0)
```

Where **hd0** is derived from (**hd0**,2). **Note: those are zeros!**

Then:

```
quit
```

Clear as mud? If unsure ask for more clarification and post the output of:

```
sudo fdisk -l
```

and also do the "sudo grub" and "find /boot/grub/stage1" and post the results of that command here also.

When you're done you should be able to boot Windows and 9.04 just like you did before installing 8.04 server.

You can then go to Places and mount the 8.04 server partition, navigate to Boot > Grub > menu.lst and copy the boot lines for 8.04.

Then open the terminal and run:

```
gksudo /boot/grub/menu.lst
```

and paste the 8.04 boot lines to the bottom of that menu.lst. Then be sure to click Save, then File > Quit.

Have I confused you yet?

This is a great Grub resource:

[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)

---

### Post by niket_a on 2009-11-02
hey thanks kansasnoob
i'll definately try out ur way
it seems the best way to fix
i will try out n come back
thanks once again for a detailed reply, i appreciate.

yours faithfully
niket

---

### Post by niket_a on 2009-11-02
hey kansasnoob, dude u did it!!!!!

man im soo grateful to u 
u r the best man on ubuntuforums
really i mean it
ur reply was soo simple n to the point  it worked like charm
thanks once again

also i want to ask something
where i can learn these commands  any book  u would suggest

thanks and regards
niket a

---

