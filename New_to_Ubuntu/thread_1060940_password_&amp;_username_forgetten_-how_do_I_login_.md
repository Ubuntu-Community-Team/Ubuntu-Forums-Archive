---
title: "password &amp; username forgetten -how do I login in?"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Overheat on 2009-02-05
My issue was solved thanks to tarus. Read post #3.

---

### Post by hyper_ch on 2009-02-05
boot into single user mode, go to the /home folder and see what names are there (there should be only one), that's the username... then set the password:

```

sudo passwd USERNAME

```

that will prompt you to set a new password

---

### Post by taurus on 2009-02-05
When you first boot up, you would see GRUB menu (if you don't see it, press Esc key to bring it up).  Then select recovery mode and boot from it.  Drop into root shell and look it up to see what your username is.

```
ls -la /home
```
Assuming your username is john, you can change the password with

```
passwd john
```
When done, reboot with 

```
shutdown -r now
```

p.s.  But if you are not able to reboot to the GRUB menu, then you need to ask either your teacher or somebody in the IT department to change your password.

---

### Post by Overheat on 2009-02-05
@taurus: what's the GRUB menu?

@hyper_ch: I don't know how to get to "single user mode"

---

### Post by taurus on 2009-02-05
Do you have physical access to the computer?  When you first turn it on, you would see a logo/message from the BIOS and then GRUB menu should appear.  If it doesn't, then you would see a word GRUB which means you have three seconds to press the Esc key to bring up the GRUB menu.  In there, you have an option for a normal boot, boot into recovery mode, or run a memtest (memory test).

---

