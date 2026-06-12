---
title: "GRUB menu doesn't appear while booting"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Been Told on 2011-03-16
Hello everyone.
I have a computer with a 1TB HD, 300GB dedicated to Ubuntu x64 and the rest belonging to my Windows 7 x64.
I first installed Windows (a week ago), then Ubuntu 10.10 x64 (about 1.5 hours ago).

Every time I reboot or switch off and start the computer up again, I see no GRUB menu. The computer goes straight from the BIOS to loading Ubuntu.

I tried to find information on how to force the GRUB menu to appear, but I haven't been able to find anything.

Any hints anyone? Thanks in advance.

---

### Post by marshmallow1304 on 2011-03-16
Edit /etc/default/grub
```
gksudo gedit /etc/default/grub
```
Find GRUB_TIMEOUT and set it to
> GRUB_TIMEOUT="n"
where n is a time in seconds to display the menu before continuing with the default (I use 10).  Also make sure that that line is not commented (remove any leading #).

Then run
```
sudo update-grub
```

---

### Post by Been Told on 2011-03-16
Thanks marshmallow :)

I have found out that GRUB can't see my Windows installation and that is why the menu isn't being displayed.
I forced it by holding Shift while booting. And sure enough, GRUB came up and only showed Ubuntu, the memtest and so on. No Windows.

I have another harddisk and I have noticed that Ubuntu seems to have put its bootmgr on there. And since that harddisk has no partition with Windows installed on it, GRUB can't see it. At least that is what I assume.

Is there a way to tell GRUB, where Windows is so it can boot into it?

---

### Post by drs305 on 2011-03-16
Run "sudo update-grub" in a terminal and watch the results. If Grub2 finds Windows you will see it as the command is executed.

If you still have problems, please download and run the boot info script from the following link. Post the contents of RESULTS.txt.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Been Told on 2011-03-16
Thanks drs305!
Running "sudo update-grub" did the trick. Grub found Windows and at the next reboot I was able to select it. :)

Thanks for the quick and competent help guys :)

Edit:
I can't seem to be able to mark this thread solved. So I would be much obliged if a moderator could do this. :)

---

