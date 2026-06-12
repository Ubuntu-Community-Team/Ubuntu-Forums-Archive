---
title: "USB thumb drives not detected - no vboxusers group?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by heliozoan on 2009-12-02
Hi,

I'm guessing that there is an obvious solution to this one....

I'm running Ubuntu 9.10 within Sun VirtualBox 3.0.12 (PUEL version) and I cannot detect my USB drives. I've read about adding my user profile to the vboxusers group under System>Administration>Users and Groups however vboxusers does not appear under the 'Group Settings' list....what am I missing?


Thanks!

---

### Post by jbrown96 on 2009-12-02
Just do it from a terminal (apps-->accessories). ```
sudo usermod -aG vboxusers $USER
``` the changes won't take effect until you logout.

---

### Post by Locke_99GS on 2009-12-02
Also, if you haven't, be sure you are enabling the specific USB device you want to pass to the VM in the USB config area of the VM's settings.

---

### Post by heliozoan on 2009-12-02
OK, I tried that and got this return:

usermod: user 'vboxusers' does not exist

Any other suggestions?

Thanks!

---

### Post by heliozoan on 2009-12-02
I've tried this [configuring the specific USB device in the Vbox settings]...it worked briefly then wouldn't work again. Thanks.

---

### Post by jbrown96 on 2009-12-02
I would try to re-install Virtualbox. It should automatically configure vboxusers. I'm not sure why it didn't. Then you just need to add yourself to the group.

Reinstalling won't delete your virtual machines or settings.

---

### Post by heliozoan on 2009-12-02
Thanks. Reinstalling the latest Virtualbox did the trick. I can see my thumb drives again however there is still no vboxusers group. Within Virtualbox I added the two specific thumb drives, but then I also just added a couple of extra 'Empty USB filters', which were necessary to make my 16 Gb SanDisk Cruzer U3 smart drive visible on the Ubuntu desktop. Cheers!

---

