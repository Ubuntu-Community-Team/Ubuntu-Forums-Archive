---
title: "booting problem"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by mikearzan on 2009-02-10
Hello everybody ,new in ubuntu,just installed ubuntu inside my windoes xp as an application.my desk top customization was gnome at the beginning and had no problem with it.last night ,i installed compiz package and then kubuntu and xubuntu and after taht tried to run some desktop effects ,wich window zooming was part of the effects .as soon as the zooming was enabled i saw the graphics started to give me problems.i decided to reboot ,thinking that will take care of the problem,but that was it . i could not boot into ubuntu anymore,the computer starts and then asks for username and then password and shows that, it will do it ,but it comes back to the username and password process over and over again and do not let me in.I did try options and evey different option wich was there ,but again the same exact problem,it deos not go pass the password and username process.I am looking for some way to get into the system(ubuntu) ,so at least i can go ahead and disable the desktop effects and uninstall compiz,but until i can not log in ,there is nothing that i can do.please ,if there is any way that i can bypass this process ,let me know,or tell me how can i go back to gnome desktop again without using username and the password.thank you all.mike

---

### Post by jbrown96 on 2009-02-11
When you get to the login screen, do the following
1) Press Crtl+Alt+F1 to get to a terminal login.
2) Login
3) ```
sudo /etc/init.d/gdm stop
```
4) ```
sudo dpkg-reconfigure xserver-Xorg
``` Accept all the defaults as long as you use a standard US keyboard.
5) ```
startx
```

It should be working now. Your graphics drivers have been disable, so you will need to re-enable them in System--->Administration--->Hardware Drivers. Compiz is disabled as well, so you can remove it or disable it.

---

### Post by mikearzan on 2009-02-11
Thank you very much for that great getaway.your step by step worked absolutely beautiful.
I am really glad that i am a part of this community now.

Thanks again.mike

---

