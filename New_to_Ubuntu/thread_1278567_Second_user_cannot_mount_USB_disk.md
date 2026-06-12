---
title: "Second user cannot mount USB disk"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by tonylewis on 2009-09-29
My USB external disk mounts fine, it pops up in the desktop and I can use it normally.  I have created a second user, but they cannot mount the disk or see it in their desktop.  The permissions for the user are default and include access external devices automatically.  I looked at the drive properties for the first user, and it says the Permissions cannot be determined.

I've searched and browsed the forums and the pocket guide and cannot work out what is going on.  I want both users to be able to use the drive and all files freely.

Any help will be appreciated
Thanks,
Tony

---

### Post by cariboo on 2009-09-29
You have to go into System-->Administration-->Users & Groups and give the user permission to access external drives by adding him/her to the correct group. I believe it is the plugdev group that needs to be added.

---

### Post by tonylewis on 2009-10-07
Thanks for the response.  I do not have a plugdev group, so I created one and allocated all accounts to it, but nothing changed.  I have quite a number of groups showing, a lot of them with no members.  Is there a reference source that will help me work out what each group does ?

Tony

---

### Post by etnlIcarus on 2009-10-07
```
gksu polkit-gnome-authorization
```

Goto HAL>Storage and add exceptions for specific users, or change the system-wide policy for certain devices.

---

