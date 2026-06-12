---
title: "accidentally edited visudo file: %sudo ALL=DAVID. Help!"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by davidstri on 2009-04-28
I changed the part of the visudo file "%sudo ALL=(All) ALL" to "%sudo ALL=DAVID", because my user name is david and I didn't want any other users on my computer looking at my personal stuff. The terminal gave me the error "Warning: undeclared Cmnd_Alias `DAVID' referenced near line 32" after I had saved and closed it with C-KX. Now when I try to enter visudo with sudo visudo, the terminal says, "Sorry, user david is not allowed to execute '/usr/sbin/visudo' as root on david-desktop."
I can't do anything!
Please Help!

---

### Post by Tibuda on 2009-04-28
Try to edit the file in the GRUB recovery mode or with a live CD.

---

### Post by _Purple_ on 2009-04-28
You can go to recovery mode and edit the sudoers file. Check the following link (last part) to see how to open the /etc/sudoers file in recovery mode
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)


To give permission to only your username to perform sudo, add this line at the end of Sudoers list

```
your_username ALL=(root) ALL
```

For example

```
DAVID ALL=(root) ALL
```

For more details on Sudoers, you can check this thread

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by unutbu on 2009-04-28
Reboot. At the GRUB menu, select "Recovery Mode". At the next menu, select "Drop to root shell".

At the root shell prompt, type

```

sudo nano /etc/sudoers
```
Fix the sudoers file. 
Save and exit.
Type
```

init 2
```
To get to a gdm login prompt.

---

### Post by ibuclaw on 2009-04-28
> **davidstri said:**
> I changed the part of the visudo file "%sudo ALL=(All) ALL" to "%sudo ALL=DAVID", because my user name is david and I didn't want any other users on my computer looking at my personal stuff. The terminal gave me the error "Warning: undeclared Cmnd_Alias `DAVID' referenced near line 32" after I had saved and closed it with C-KX. Now when I try to enter visudo with sudo visudo, the terminal says, "Sorry, user david is not allowed to execute '/usr/sbin/visudo' as root on david-desktop."
I can't do anything!
Please Help!

I would like to also note that until recently, the group "sudo" was the exempt group in the program, meaning that users of the "sudo" group didn't require a password to carry out administrative tasks. This is no longer the case as sudo is no longer compiled --with-exempt=sudo.

I will also note that by default, you are not part of the "sudo" group, so use the "admin" group in the future.


What _Purple_ has posted is correct.
The sudoers line goes as follows:
```
USER HOST = ( RUNAS ): CMD
```
You can optionally use your username **and** hostname in the configuration:
ie:
```
david **ubuntu**=(root) ALL
```
your hostname is located in the following file:
```
cat /etc/hostname
```

Regards
Iain

---

### Post by davidstri on 2009-04-28
Yess! It worked perfectly.  
Thank you all for your help.

---

