---
title: "HELP: Dual boot windows and linux NOOB problem."
date: 2011-01-25
forum: New to Ubuntu
---

### Post by bennoculus on 2011-01-25
Okay, I followed this tutorial, but could not back up my grub menu.list file so I can dual boot.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6")

I CAN ONLY BOOT INTO WINDOWS, THIS IS A PROBLEM.

I am following this tutorial, and this is the current step I am on. It says to boot off a live CD, which I have done. It says to go into terminal and type,"sudo grub"

I enter this command and my terminal says "sudo: grub: command not found"

This is kind of a problem, as now I can't change the hard drive for linux as the boot drive and then edit the menu.list file to add windows, so I can boot from it as well. I really need a solution for this, as I have some important files on my Linux machine.

The tutorial also says you can do it in windows. It says to first make a backup of the menu.list file before you do this. It wouldn't bring up the file when I type the terminal command. It would bring up and empty text file.

Do I not have the menu.list file?

I tried using Linux extractors on the windows side to grab the file and none of them worked.

Please help me here, I've been googling around everywhere, searching these forums for an answer. Did I just destroy my linux side?

---

### Post by cariboo on 2011-01-25
It would help, if you told us what version of Ubuntu you are using, as the way to solve your problem is different in pre-10.04 versions, than it is with current versions

---

### Post by robgraves on 2011-01-25
i did it with existing windows installation first, following this websites directions:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by Quackers on 2011-01-25
From the live cd desktop please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

