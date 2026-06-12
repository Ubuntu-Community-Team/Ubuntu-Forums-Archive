---
title: "Cannot login to Ubuntu after changing the 'username'."
date: 2009-02-03
forum: New to Ubuntu
---

### Post by linuxpenguin1 on 2009-02-03
Hi People,

I am really confused with Ubuntu. I currently own Ubuntu 8.04.1 Desktop Edition on my Intel-based Mac computer. 
I was following some guides online in order to change my **Computer Name**. At first, I went to the **About me** preference pane but I didn't find any option to change my **Computer Name** or maybe even my **User name**. Then I found a tutorial that said to go to: **System > Administration > Network > General** and change it from there. I did and then I restarted my computer. The boot process went fine but then it asked for my **User name** and **Password**. I typed my 'new' User name and my previous password but it keeps on saying: **'Incorrect User Name or Password...'**. I tried other previous combinations but no luck there either... 
What should I do to resolve this cumbersome problem. I wanted to change my Computer Name or User Name not really sure about the difference and now I cannot login in to Ubuntu...

Thank you.

---

### Post by cyberdork33 on 2009-02-03
> **linuxpenguin1 said:**
> Hi People,

I am really confused with Ubuntu. I currently own Ubuntu 8.04.1 Desktop Edition on my Intel-based Mac computer. 
I was following some guides online in order to change my **Computer Name**. At first, I went to the **About me** preference pane but I didn't find any option to change my **Computer Name** or maybe even my **User name**. Then I found a tutorial that said to go to: **System > Administration > Network > General** and change it from there. I did and then I restarted my computer. The boot process went fine but then it asked for my **User name** and **Password**. I typed my 'new' User name and my previous password but it keeps on saying: **'Incorrect User Name or Password...'**. I tried other previous combinations but no luck there either... 
What should I do to resolve this cumbersome problem. I wanted to change my Computer Name or User Name not really sure about the difference and now I cannot login in to Ubuntu...

Thank you.
The "computer name" would be the name of your computer. This is how your computer will be named when seen over the network.

If no previous combo is working, then you very likely did change your username, and entered something incorrectly for the password or username. Boot Ubuntu into recovery mode (an option in the GRUB menu). When given the choice, drop to a root terminal. 

You can use the following to list the users for your system:
```
cat /etc/passwd | cut -d":" -f1
```
then use the 'passwd' command to change your user password to something you can remember. For example, my username is cyberdork33, so I would type:
```
passwd cyberdork33
```It will then prompt you to enter a new password for that user.

After you change the password, type 'exit' and you will be given the option to continue aa normal boot and your should be able to login with the new password.

---

### Post by bapoumba on 2009-02-03
Moved to ABT (thanks twice cyberdork ;)).

---

### Post by cyberdork33 on 2009-02-03
> **bapoumba said:**
> (thanks twice cyberdork ;)).
gee, I wish the thanks system worked still! :)

---

### Post by bapoumba on 2009-02-03
> **cyberdork33 said:**
> gee, I wish the thanks system worked still! :)
Yeah me too :)

---

