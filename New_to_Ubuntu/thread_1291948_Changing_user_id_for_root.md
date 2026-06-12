---
title: "Changing user id for root"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Flatbed on 2009-10-15
Hi guys
I recently changed my user id from user to Root and now can't sign in to the ubantu system as it does not allow this.
How can I retrieve this so that I can sign in?
Please don't be too technical as I'm new to this and realise now that I did the wrong operation.

Hope you can help

Flatbed

---

### Post by sisco311 on 2009-10-15
Reboot the computer and select *Recovery Mode* from the grub menu.

You may have to press the Escape key during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select *Drop to root shell prompt* option from the *Recovery Mode* menu. 

Change your uid:
```
usermod -u 1000 username
```
replace 1000 with the user id and username with your login name.
type:
```
exit
```
and choose to resume a normal boot.

---

### Post by Flatbed on 2009-10-16
Hi Again
When I use recovery mode I cant get any menu even when I press the Escape button!

---

