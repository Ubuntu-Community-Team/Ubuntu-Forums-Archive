---
title: "Edubuntu Server LTSP, client can't access USB Drive"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by tamays on 2007-06-23
I have installed and configured the latest Edubuntu Server for a LTSP network. But when I log in as a client and insert a USB jump drive I get zilch, zero, nothing as in nothing at all, yet I hear it can be done. If so, what's the secret? :-k

Thanks for any Help.

---

### Post by npman on 2007-06-25
Make sure that your login is added to the FUSE group.

---

### Post by tamays on 2007-06-26
I did a quick search and could not find any information about the "Fuse Group", could you please be more specific? Where can I find documentation about this?

Thanks.

---

### Post by hboshoff on 2007-06-27
Each user is a member of one or more groups on the system.

Click System -> Administration -> Users and Groups for an applet that shows user settings and allows you to manage groups.

If you click on the button Manage Groups, another window opens, showing the groups already defined on the system. You may need to scroll down to find the fuse group. Select it, and click on Properties, which will open a third window. Check the box next to the user you want to add to this group, and close all three windows.

To activate the change, you need to log in again. If you want to make sure it worked, type in the terminal:
$ groups
which should list all the groups the current user belongs to. fuse should be there somewhere.

---

