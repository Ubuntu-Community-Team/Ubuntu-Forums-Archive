---
title: "Strange problem while logging in"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by naiquevin on 2010-07-05
Hi, 

I updated to ubuntu 10.04 and it is giving me a strange problem. When the computer is idle for a while, the screen gets locked. When i enter my password and try to unlock, it shows me incorrect password although the password is correct. The work around i have found for this is to select switch user on the unlock dialog, then on the switch user screen select the same user which is shown logged in and enter the password there. Now it takes the password. 

I have use one more computer running on ubuntu 10.04 and there absolutely no  such problem there. 

Any one else facing this problem ? How do i fix it ? 

Thanks

---

### Post by Jakiejake on 2010-07-05
> **naiquevin said:**
> Hi, 

I updated to ubuntu 10.04 and it is giving me a strange problem. When the computer is idle for a while, the screen gets locked. When i enter my password and try to unlock, it shows me incorrect password although the password is correct. The work around i have found for this is to select switch user on the unlock dialog, then on the switch user screen select the same user which is shown logged in and enter the password there. Now it takes the password. 

I have use one more computer running on ubuntu 10.04 and there absolutely no  such problem there. 

Any one else facing this problem ? How do i fix it ? 

Thanks

Would a reinstall be possible?
May be change your Password and try that.

---

### Post by naiquevin on 2010-07-05
Changing password seems to be a good idea for now. Reinstall would be the last resort. Lots of things already installed and running. 

Thanks

---

### Post by Jakiejake on 2010-07-05
> **naiquevin said:**
> Changing password seems to be a good idea for now. Reinstall would be the last resort. Lots of things already installed and running. 

Thanks

Cool Good Luck! :D

---

### Post by naiquevin on 2010-07-05
Tried changing the password but no luck with that. Still behaves the same way as before. Any other way i can fix it besides reinstalling ? 

Thanks

---

### Post by philinux on 2010-07-05
> **naiquevin said:**
> Tried changing the password but no luck with that. Still behaves the same way as before. Any other way i can fix it besides reinstalling ? 

Thanks

Change the screensaver prefs so it doesn't lock the screen for now.

Or you could delete this folder /home/YOURUSERNAME/.gnome2/keyrings

It could be a keyring problem.

---

### Post by naiquevin on 2010-07-05
> **philinux said:**
> Change the screensaver prefs so it doesn't lock the screen for now.

Or you could delete this folder /home/YOURUSERNAME/.gnome2/keyrings

It could be a keyring problem.

HI,

tried removing that folder .. still not working. 
I guess, will have to change the screensaver settings and live with the problem for now

---

