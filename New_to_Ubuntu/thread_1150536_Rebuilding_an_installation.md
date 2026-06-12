---
title: "Rebuilding an installation?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by madomac on 2009-05-06
Servus!

If I want to rebuild an existing Jaunty installation on the **same** machine, would these be the correct steps?


[LIST=1]
[*]Back up /etc
[*]Back up /home
[*]Create list of packages installed via 
dpkg --get-selections | awk '!/deinstall|purge|hold/ {print $1}' > packages.list
[*]Reinstall from scratch, update system
[*]Reinstall all packages via 
xargs -a "packages.list" sudo apt-get install
[*]Restore /etc
[*]Restore /home
[/LIST]
Reason for re-installing: I want to get rid off my Vista partition - as soon as the Jaunty freeze problem is fixed.

Thank you & regards,
Marc

---

### Post by tom56 on 2009-05-06
> **madomac said:**
> Servus!

If I want to rebuild an existing Jaunty installation on the **same** machine, would these be the correct steps?


[LIST=1]
[*]Back up /etc
[*]Back up /home
[*]Create list of packages installed via 
dpkg --get-selections | awk '!/deinstall|purge|hold/ {print $1}' > packages.list
[*]Reinstall from scratch, update system
[*]Reinstall all packages via 
xargs -a "packages.list" sudo apt-get install
[*]Restore /etc
[*]Restore /home
[/LIST]
Reason for re-installing: I want to get rid off my Vista partition - as soon as the Jaunty freeze problem is fixed.

Thank you & regards,
Marc

You don't need to reinstall. Just install gparted, remove the Vista partition and extend the Ubuntu one to fill the free space. As with any partioning, make sure you back up /home first just in case.

---

### Post by madomac on 2009-05-06
> **tom56 said:**
> You don't need to reinstall. Just install gparted, remove the Vista partition and extend the Ubuntu one to fill the free space. As with any partioning, make sure you back up /home first just in case.

Sounds like a plan! Will it modify the GRUB config as well? I think I will go down this route as soon as my freeze problem is solved.

Just out of curiosity - would my suggestion above have done what I expected?

Thank you!
Marc

---

### Post by KIAaze on 2009-05-06
> **madomac said:**
> 
Just out of curiosity - would my suggestion above have done what I expected?


Yes, I think it would have worked.
I'm not sure about the package backup/restore commands, because the ones I know are different:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by aparigraha on 2009-05-06
Backup and restore system:

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by tom56 on 2009-05-06
> **madomac said:**
> Sounds like a plan! Will it modify the GRUB config as well?

To be honest, I'm not sure. As long as you keep a LiveCD/USB handy then you can always boot in to that to fix it.

---

### Post by madomac on 2009-05-07
> **tom56 said:**
> To be honest, I'm not sure. As long as you keep a LiveCD/USB handy then you can always boot in to that to fix it.

This link would be helpful [<click!>]("http://fosswire.com/post/2009/5/restoring-overwritten-grub/")

---

### Post by Didius Falco on 2009-05-07
Resizing your partitions will change the UUID numbers, so be sure and check those in your fstab and menu.lst files after you are done.

The script in my sig can be used from the desktop of the Live CD - just download it from there to the desktop and run it with this command from a terminal shell:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

It'll put a file called RESULTS.txt on your desktop that will have all the info you need. Fix up your UUIDS and paths, restore Grub and you should be good to go.

---

