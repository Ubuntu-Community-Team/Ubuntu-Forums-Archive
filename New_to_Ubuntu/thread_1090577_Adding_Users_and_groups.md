---
title: "Adding Users and groups"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by panorack on 2009-03-08
I cannot add a user or manage groups since upgrading to 8.10. The unlock box in the 'User Settings' dialogue box is greyed out as are all the other boxes. 

I've tried coming at it from a terminal via 'sudo bash' followed by 'users-admin' but even starting up in this way as root I get the same greyed out boxes.

Can anyone please tell me how to get round this.

Many thanks in anticipation,

---

### Post by bailbath on 2009-03-08
[http://ubuntuforums.org/showthread.php?t=1089443](http://ubuntuforums.org/showthread.php?t=1089443)

Sounds familiar to this thread read it through and see if it applies.
Ian

---

### Post by taurus on 2009-03-08
Do you belong to group admin?

Applications -> Accessories -> Terminal
```
id
```
Are you trying to add somebody to /etc/group?

---

### Post by panorack on 2009-03-08
> **bailbath said:**
> [http://ubuntuforums.org/showthread.php?t=1089443](http://ubuntuforums.org/showthread.php?t=1089443)

Sounds familiar to this thread read it through and see if it applies.
Ian

Read the thread but it does not apply. I am in the admin group and I regularly install all upgrades. I put in my password when prompted after clicking on 'Administration>Users and Groups' but the 'Unlock' box is greyed out. 

Coming at it from a terminal I typed 'sudo bash' followed by my password when prompted then 'users-admin' which brought up the 'Users Settings' dialogue box but the 'unlock' button was still greyed out.

I was able to add and modify users and groups when running 8.04. This has only happened since upgrading to 8.10

---

### Post by panorack on 2009-03-08
I have now managed to access the 'Users and Groups' as administrator. I tried opening 'Users and Groups' from a terminal but this time after typing 'sudo su' followed by my password when prompted. After opening 'Users and Groups' from this terminal I had access to all operations. 

I don't know why it worked after opening the terminal with 'sudo su' rather than 'sudo bash' as both seem to open a terminal with root privileges but at least I can now make the changes I need to make.

Thanks to all who offered help.

---

