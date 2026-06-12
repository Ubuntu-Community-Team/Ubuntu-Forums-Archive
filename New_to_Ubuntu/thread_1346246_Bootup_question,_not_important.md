---
title: "Bootup question, not important"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by ah pook on 2009-12-04
How does one turn on the verbose mode during boot up? The old versions did it, and I kinda liked watching it run. Is there any way to turn it on in 9.10? The screen is nice, but..

Thanks in advance...

---

### Post by cartisdm on 2009-12-04
Try this:

- launch terminal
- type
```


nvram boot-args="-v"
```

- press return
- type reboot

to disable
- launch terminal
- type

```

nvram boot-args=
```

- press return
- type reboot

---

### Post by ah pook on 2009-12-04
nope, command not found..any other ideas?

---

### Post by akelsall on 2009-12-05
ah pook, try this....

sudo gedit /boot/grub/menu.lst

Look for a line similar to the one shown below, then delete the word
"quiet". Save the file. Next time you reboot, you'll see all the startup messages:

kernel   /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash 


You can also open a terminal window and enter the command "dmesg | more" to see the startup messages.

Andy

---

### Post by presence1960 on 2009-12-05
> **akelsall said:**
> ah pook, try this....

sudo gedit /boot/grub/menu.lst

Look for a line similar to the one shown below, then delete the word
"quiet". Save the file. Next time you reboot, you'll see all the startup messages:

kernel   /boot/vmlinuz-2.6.17-11-generic root=/dev/hde4 ro quiet splash 


You can also open a terminal window and enter the command "dmesg | more" to see the startup messages.

Andy
In most cases 9.10 will have GRUB 2 installed which does not use menu.lst

---

