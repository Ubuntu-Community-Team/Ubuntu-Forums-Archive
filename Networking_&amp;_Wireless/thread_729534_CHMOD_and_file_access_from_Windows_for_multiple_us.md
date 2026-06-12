---
title: "CHMOD and file access from Windows for multiple users"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by btwong on 2008-03-20
I have ubuntu server edition running on a computer, and i want to give access to users so they can add/edit/delete files/directories.

Everytime i make a new folder or file on the server, it becomes only read only to other users who want to access it. I have to CHMOD all the time to update the permissions.

Is there a way to make all files/folders that are created by users editable/deletable straight away, instead of doing a CHMOD all the time?

thanks

---

### Post by Eiríkr on 2008-03-20
One way of doing this is to use the [font=courier]setgid[/font] bit.  Have a look [here]("http://en.wikipedia.org/wiki/File_system_permissions#Additional_Permissions") for a decent explanation over on Wikipedia.  And have a look [post=4496702]here[/post] for instructions on how you can use the [font=courier]setgid[/font] bit via [font=courier]chmod[/font], together with group membership, to grant common access to specific users (group members).  Scroll down the post to the "Multi-user" section.  

Cheers,

Eiríkr

---

### Post by btwong on 2008-03-21
thanks heaps for that.

---

### Post by Eiríkr on 2008-03-21
Happy to help.  :)  And if that fixes your issue for this thread, please also remember to mark the thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :D

Cheers,

Eiríkr

---

