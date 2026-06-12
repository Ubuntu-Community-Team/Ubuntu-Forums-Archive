---
title: "what is gnu grub"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by Nod3225 on 2011-03-26
I have been trying for several weeks to install ubuntu 10.10 alongside windows xp.  I downloaded and made a live cd but no matter what I try it deletes windows.  I downloaded it again and made a second cd and it seemed to install ok but when I turn on the computer I still don't get an option to use windows.  it goes directly to a screen that says
GNU Grub version 1.98+20100804-5ubuntu3  and then below it it has the word grub>
What is this and how do I get to the desktop from it.

thanks for any help
Don

---

### Post by Quackers on 2011-03-26
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Faoesch on 2011-03-26
[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
To turn on the grub menu in the booting process you open the console and type:
```
sudo nano /etc/default/grub
```
and comment out the line "GRUB_HIDDEN_TIMEOUT=0"
press "ctrl + x" and save the file
to update the grub menu ```
sudo update-grub
```

---

