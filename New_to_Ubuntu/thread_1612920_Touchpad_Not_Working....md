---
title: "Touchpad Not Working..."
date: 2010-11-03
forum: New to Ubuntu
---

### Post by sdwrage on 2010-11-03
Hey all,

I moved my system from Windows 7 to Ubuntu and everything works perfectly it seems except the touchpad... this does not work at all. It is an electro-static multi-touch pad for the Sony Vaio VPCEB33FM/BJ Model. Any help would be much appreciated.

:popcorn:

---

### Post by sdwrage on 2010-11-15
Bump? :KS

---

### Post by sdwrage on 2010-11-22
Can anyone help me on this?

---

### Post by Oaty on 2010-11-23
Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

---

### Post by Timo0060 on 2010-11-23
I'm having a similar problem... sort of. I use my laptop and the touchpad on it works fine, but the cursor will randomly disappear and appear some where else on the screen. Does anyone know how to fix this problem? Thanks if you can.

---

### Post by sdwrage on 2010-11-24
> **Oaty said:**
> Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

Worked great! :D thank you! :)

---

### Post by ma_chro on 2010-11-25
Hi, I have a VPCEE33EL and the same problem too.
I'm an Ubuntu user from 2 years ago but I don't understand so much.

I have to open a terminal and write: edit /etc........   ?

Please guide me step by step.
Thank you very much.

Best regards.

Mario

---

### Post by nyvietvet on 2010-12-02
> **Oaty said:**
> Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.
Oaty, when I did as you suggest, I got:

bill@bill-VPCEE3WFX:~$ sudo update-grub
[sudo] password for bill: 
/etc/default/grub: 1: &#65279;#: not found

---

### Post by gbrun on 2011-01-23
Hello,
I did the procedure above and my touchpad still doesn't work.
I'm running ubuntu 10.10 and the laptop model is VPCEB33FM.
Thanks

---

### Post by Ordepjo on 2011-02-07
> **Oaty said:**
> Here’s the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=”i8042.nopnp”
2. Run: sudo update-grub
3. Reboot.

im new with ubuntu, really new, and i have this same problem. my question is: what exactly do i have to do? should i write  /etc/default/grub into the terminal? or is it something else? sorry again, help appreciated

---

### Post by plaseo on 2011-02-10
1. Open Terminal
2. Type in: sudo gedit /etc/default/grub
3. Enter your password
4. Add a line at the bottom that says: GRUB_CMDLINE_LINUX=”i8042.nopnp”
5. Save the file
6. Back in terminal type: sudo update-grub
7. Reboot

---

