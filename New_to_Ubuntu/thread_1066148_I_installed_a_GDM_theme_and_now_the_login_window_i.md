---
title: "I installed a GDM theme and now the login window is not showing, please help"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-02-10
Hi
Thank you for reading my post.
I installed a gdm theme and after I  restart my computer it come to the state that usually shows the login screen, but this time it shows nothing and instead the mouse stays in thinking mode. The system is not in hang mode because i can go to ALT+CTRL+F# and use the command line but no desktop :(

I tried fail safe recovery mode and it does not login either :(
please let me know how to revert to my previous gdm theme.

thanks

---

### Post by legolas_w on 2009-02-10
fixed.
If you have this problem here is the sequence to fix it

1- go to command line mode by pressing ALT+CTRL+F3
2- cd /usr/share/gdm/themes/
3- ls -al to see the list of theme names to find the faulty theme name (they are all separate folders, 1 folder for each theme)
4- mv faulty-theme-name faulty-theme-name2 to make sure that gnome will not find that faulty theme. you can use tab to simply complete the folder name after you typed a few characters.
5- reboot and you will see that gnome picked default gdm theme for you.


hope it helps

---

### Post by JK3mp on 2009-02-11
I have a similiar problem. I can't get my GDM theme settings to apply and when i try to apply them... *sometimes* i get an Xserver error... =(

---

