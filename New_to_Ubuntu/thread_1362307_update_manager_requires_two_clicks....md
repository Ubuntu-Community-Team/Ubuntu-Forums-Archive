---
title: "update manager requires two clicks..."
date: 2009-12-23
forum: New to Ubuntu
---

### Post by kentechy on 2009-12-23
I have a, possibly dumb, question...

Why does one have to click on "update manager" twice, often, and enter the password to get updates?  Doesn't it make more sense for the first click to bring up the password window and get any updates the first time around?

:rolleyes:

---

### Post by lavinog on 2009-12-23
Can you be more descriptive?
What do you have to click on twice?

Also I think the update manager will be replaced in the next version of ubuntu...so it might not matter.

---

### Post by kentechy on 2009-12-23
I am running Karmic.  If you open the update manager it appears to search for updates but often finds none.  If you click on "Check" a second time it requests a password.  If you enter your password it often finds updates available.  Why does one have to click twice?

---

### Post by steveneddy on 2009-12-23
> **kentechy said:**
> I am running Karmic.  If you open the update manager it appears to search for updates but often finds none.  If you click on "Check" a second time it requests a password.  If you enter your password it often finds updates available.  Why does one have to click twice?

Security - it doesn't check for updates until you hit the "Check" button.

You need to input your password for security purposes, as opposed to Windows which will install anything, including virus', with no authorization required.

---

### Post by lavinog on 2009-12-23
> **kentechy said:**
> I am running Karmic.  If you open the update manager it appears to search for updates but often finds none.  If you click on "Check" a second time it requests a password.  If you enter your password it often finds updates available.  Why does one have to click twice?

The update manager scans the local cache data when it loads...it doesn't update the package info until you click on update.
There are ways to configure how it behaves.  Settings>updates>check for updates daily...etc.  This way you don't need to check.
Some users want the current behavior because they want to control when the repositories are updated.

---

### Post by kentechy on 2009-12-23
> **lavinog said:**
> The update manager scans the local cache data when it loads...it doesn't update the package info until you click on update.
There are ways to configure how it behaves.  Settings>updates>check for updates daily...etc.  This way you don't need to check.
Some users want the current behavior because they want to control when the repositories are updated.
That makes sense.  I guess the first click just opens the update manager, but the message at the top of the window always says that "your system is up to date" unless a major update has been detected.  Just seems a little buggy, nothing serious.  Thanks.

---

### Post by lavinog on 2009-12-23
Feel free to make sugestions on how to improve it on [brainstorm.ubuntu.com](brainstorm.ubuntu.com)

---

