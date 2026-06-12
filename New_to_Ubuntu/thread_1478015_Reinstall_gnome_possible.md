---
title: "Reinstall gnome possible?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-09
Hello,

My Ubuntu pc has trouble showing the applications menu. I already [started a thread]("http://ubuntuforums.org/showthread.php?t=1476703") about it, but there seems to be no solution.

I now thought of reinstalling gnome for which I found this command:
```
sudo aptitude reinstall ubuntu-desktop
```
Would this be a good idea, or would that mess up everything even more? Would it for example erase anything?

---

### Post by shae on 2010-05-09
I do not think that would be really useful.

You should try creating a new user account and see if you have problems with the menu in it.  You can do that in System>Administration>Users and Groups.  Once you create a new one, log out and log into the new account and see if you have a menu problem.  If you still do, I have no clue what the problem is.

If you do not have a menu problem, then you should remove the hidden files in your home folder of your normal account if you want to use that one or use the new account.

Shae

---

### Post by ddecator on 2010-05-10
Go to .config/menus/ and delete applications.menu and see if it works again (this will reset it).

---

### Post by Taras.M.K on 2010-05-10
I do not think it's an installation problem, rather your configs are messed. You may try to move some gnome related dirs in your home dir. You need to enable preview of hidden files for it (via menu or Ctrl-H).
There will be:
.gnome2
.gnome2_private
.gconf
.gconfd
But erasing them you'll lose different prefs and customizations of your desktop, so may try to move them and later to merge. Or customize your environment from scratch.

---

### Post by kramer65 on 2010-05-10
Thanks for all the tips. I tried to mess araund with it but finally decided to do a totally fresh installation. I don't know what the problem was, but my pc works like a charm again! :-)

Thanks for all the help!

---

