---
title: "Limiting OS system choices at login"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by Covalent Bond on 2010-10-02
Using a dual boot system (Ubuntu 10.04), and at log on, I am given 4 variants of Ubuntu to select from in addition to Windows.  I would like to limit the Ubuntu variants, but do not know the command.  In previous versions of Ubuntu, there was an option to do that under System, Administration.

CB

---

### Post by da burger on 2010-10-02
Hey, of the top of my head I can't remember how to limit the number displayed, but if you just want to get rid of them, you can uninstall the kernels that the lower menu items refer to. To do that use synaptic.
I'll go see if I can find the way to limit without removing :)
Angus

EDIT: [FOUND]("http://ubuntuforums.org/showthread.php?t=1287602")! You want number 2.

---

### Post by hhh on 2010-10-02
From here...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

To remove the recovery mode entries, remove the # sign in /etc/default/grub from the line GRUB_DISABLE_LINUX_RECOVERY="true".

To remove the memtest options, in a terminal run ```
sudo chmod -x /etc/grub.d/20_memtest86
``` and then ```
sudo update-grub
```.

As was stated, to remove old kernels, remove the appropriate linux-image and linux-header packages in Synaptic. It's recommended to leave one backup kernel.

---

### Post by sikander3786 on 2010-10-02
I think startup-manager can also serve the purpose.

```

sudo apt-get install startupmanager

```

Run it from under System > Administraion > Startup Manager.

---

### Post by uRock on 2010-10-02
Using startupmanager will distort the boot and shutdown screens to a point that you will not be able to see error messages should they happen.

---

