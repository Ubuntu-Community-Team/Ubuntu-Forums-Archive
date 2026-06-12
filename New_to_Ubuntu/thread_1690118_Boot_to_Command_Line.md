---
title: "Boot to Command Line"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by mn_voyageur on 2011-02-17
Is it possible to avoid the GUI?  Can I go straight to a command line and log in and run as if in a terminal screen?

Thanks,
MarkN

---

### Post by lightningfox on 2011-02-17
You can open a terminal in the GUI by going to Applications>Accessories and click Terminal.

---

### Post by mn_voyageur on 2011-02-17
I am aware of opening a terminal.

I am curious as to whether I can boot to the command line.  (The equivalent of Ctl+Alt+F2.)

MarkN

---

### Post by outskut on 2011-02-17
There are a couple ways you can do this.  The easiest might just be to start a shell session while actively running Linux by pressing Ctrl-Alt-F2, but remember the second sequence to escape from the session:  Ctrl-Alt-F7.

I think there's also a way to boot exclusively to the command prompt through the ubuntu recovery mode.  Besides selecting the recovery mode on boot up in the Grub bootloader I don't know another way.  For clarity, the grub bootloader is a menu that will prompt you which partition of your computer you want to boot from before starting up your OS.  To activate your bootloader, install grub by typing into a terminal window:
sudo grub-install /dev/hda

---

### Post by zhogan85 on 2011-02-17
This [post]("http://www.linuxquestions.org/questions/ubuntu-63/boot-into-console-command-line-instead-of-x-549292/") tells you how, but I think if you do it this way, you will always boot to CLI. The post shows you how to change back too though.

---

### Post by Paqman on 2011-02-17
Permanent: Uninstall xorg and gdm. Or install a CLI-only system using the server, alternate or minimal .ISOs
Temporary: Boot into Recovery Mode as outskut says.

---

### Post by Blackbird_13 on 2011-02-18
In order to boot to command line, I insert "text 3" at the end of the linux line in grub,cfg:

```
linux    /boot/vmlinuz-2.6.32-28- ...... ro text 3
```

---

### Post by oldos2er on 2011-02-18
In /etc/default/grub, change this line

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Run **sudo update-grub** when done. This is easily reversed too if you need to change back.

---

### Post by mn_voyageur on 2011-02-18
Thanks.  I am having problems with my GUI, so booting to CLI is preferred.

MarkN

---

### Post by kindlychung on 2013-04-24
> **Blackbird_13 said:**
> In order to boot to command line, I insert "text 3" at the end of the linux line in grub,cfg:

```
linux    /boot/vmlinuz-2.6.32-28- ...... ro text 3
```

what does 3 mean here? thanks!

---

### Post by sandyd on 2013-04-24
**Necromancing - Thread closed**
Please do not post in threads more than a year old as many things change between Ubuntu releases, and the fixes/solutions/issues described may not be prevalent to your version of Ubuntu.

Thanks!

---

