---
title: "unlock default keyring"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-07-01
We are getting this message popping up at the library and it is very irritating and patrons don't know how to unlock."unlock default keyring". I googled and found instructions but they don't work on maverick the interface for passwords and encryption keys has changed. Can someone give directions for Maverick?I have the public set to automatically login.

---

### Post by beew on 2011-07-01
> **cmcanulty said:**
> We are getting this message popping up at the library and it is very irritating and patrons don't know how to unlock."unlock default keyring". I googled and found instructions but they don't work on maverick the interface for passwords and encryption keys has changed. Can someone give directions for Maverick?I have the public set to automatically login.

Just go to your home folder, click view > show hidden files and find the folder .gnome2 and open it to find the gnome-keyring folder and delete it.

Then when it starts again you just put in nothing for the keyring password and it will ask if you are sure that you want unsafe storage, click ok and it wouldn't bother you again.

---

### Post by cmcanulty on 2011-07-01
OK thanks I have 8 laptops at the library to fix this on.Just to be clear there is a keyrings folder in the .gnome2 folder. I don't see a gnome-keyring folder.Do I delete the whole keyrings folder or just one of the files?

---

### Post by el_koraco on 2011-07-01
Go to System - Preferences - Passwords and Encryption Keys, check out which of the keys are listed. Right click, Edit, enter your sudo password, and leave the two other fields blank.

---

### Post by beacon on 2011-07-03
This is a repeat of a query on another thread, but it still hasn't been solved.

 > Go to System - Preferences - Passwords and Encryption Keys, check out which of the keys are listed. Right click, Edit, enter your sudo password, and leave the two other fields blank.

When I try to follow those instructions I am told 'could not launch passwords and encryptions. Failed to execute child process'

Solutions seem to hinge on getting into this program, but I can't seem to find a way.

---

### Post by beew on 2011-07-03
> **cmcanulty said:**
> OK thanks I have 8 laptops at the library to fix this on.Just to be clear there is a keyrings folder in the .gnome2 folder. I don't see a gnome-keyring folder.Do I delete the whole keyrings folder or just one of the files?

Yes, delete the whole keyrings folder. See all these things will regenerate so you don't have to be afraid of deleting the wrong thing, the point is if you delete it  you will be able to start afresh, at that point you can choose no keyring password (put in blank--nothing when prompted  to create a new password )

---

