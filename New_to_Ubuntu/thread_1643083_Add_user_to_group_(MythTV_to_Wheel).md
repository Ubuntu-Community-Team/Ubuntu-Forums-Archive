---
title: "Add user to group (MythTV to Wheel)"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by SnoopFogg on 2010-12-11
I'm trying to set up ACPI wakeup on MythTV.  I have been successfully following these instructions:

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

But then I get to part that says "add mythtv and any other uses you wish to the "wheel" group. That can be done using the GNOME user GUI".

Can anyone tell me how to do this?  I go to system > administration > Users and Groups.  But I can't see a group called "wheel".  Should I create one?  And then how do I add myth to it?  

The object of the exercise as I understand it is to get the machine to showdown after a recording without requiring a password.

---

### Post by cariboo on 2010-12-11
Ubuntu doesn't use a wheel group, it's called admin group, To add your mythtv user to the admin group you can use the following command:

```
sudo gpasswd -a admin mythtv
```

---

### Post by SnoopFogg on 2010-12-12
Thanks for your reply.  I get an error message: 

gpasswd: user 'admin' does not exist

Under users and groups GUI I can see the group "admin".  Though the error message seems to be saying that user (rather than group) does not exist.  Any ideas?

---

