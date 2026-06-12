---
title: "accessing windows shares"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by jazzfan1 on 2008-10-14
Please forgive my ignorance, I am just getting started with Ubuntu and I am trying to connect to my laptop which is in the same workgroup as my linux desktop. I get as far as the laptop icon but when I click on it I cannot see any of my windows shares. The only thing I have done, I edited the /etc/samba/smb.conf and changed the workgroup name to reflect my own workgroup, but apparently I am still missing something. Can anyone help??
Thanks in advance
jazzfan1

---

### Post by ghostborg on 2008-10-15
Hi, I cannot really help you but for someone who can it would be helpful to mention your operating systems, Ubuntu 8.xx, Windows Vista,XP SPx.
Vista might be a Share issue where you need to add Everyone, guest.
Don't forget to reboot both machines, sometimes that helps.

Another way to edit the workgroup value in Ubuntu,8.04,8.10:
If the configuration editor is not visible then do the following.
In Ubuntu you can right click on the Top menu on the word Applications and select Edit Menus. When the Menu Editor opens, click on System Tools and in right panel put a check in the box for Configuration Editor, Close. Run Applications==>System Tools==>Configuration Editor. With the arrow expand the label System. You should see smb. Click on smb and in the right panel you should see workgroup. If the workgroup value is the one you entered when you edited the file, you should be OK. Otherwise if it is blank right click on workgroup and edit key. Enter the name of your workgroup in the Value line. Close, reboot.

---

