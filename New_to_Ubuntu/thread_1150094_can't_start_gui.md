---
title: "can't start gui"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-05-05
i can't seem to start the gui after installing windows  7 rc please help me out the last thing i want to do right now is install jaunty again

---

### Post by tjwoosta on 2009-05-05
installing windows 7 should not have anything to do with ubuntu not working unless you somehow managed to write over some ubuntu files

could you provide more information?

what is the error you get?

how far do you get before the error comes up?

are you using grub as a boot loader or the windows boot loader?

---

### Post by Didius Falco on 2009-05-05
If you installed Windows 7 rc after Jaunty, Windows has a bad habit of acting like it's the only O/S around. It probably wiped your Grub out of the MBR.

Do you have a Live CD of Jaunty? If so, boot that, and download the little (57k) script in my signature to your desktop:

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named RESULTS.txt and put it on your desktop.

Open that file, select all and paste it in this thread, then put code tags (the # on the toolbar) around it.

It'll help to figure out the answer faster...

If it's what I suspect, the fix will be quick and easy.

Regards,

Didius

---

