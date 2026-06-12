---
title: "Cant find Skype exe"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by Myket on 2010-04-11
Couldnt find out how to update skype because i wanted to screen share. so i uninstalled skype and downloaded the new version from there website. i downloaded a Deb file and everything is installed and good to go. but now i cant find the exe file to open the program. i dont know the terminal code to open the file because i dont know where the exe is located

---

### Post by davec64 on 2010-04-11
EXE files are Windows and you won't find one in Linux!

Sometimes the menu entry isn't added to the Applications menu immediately, occasionally after a reboot it will appear. If it does appear it's likely to be in Accessories (if memory serves me right!)

If you just want to run the programme, just try typing the follwing in a terminal:

```
skype
```

that should start the application.  :)

---

### Post by WinterRain on 2010-04-11
You can usually add apps to the menus by going to system>preferences>main menu

Usually, the "executable" file to launch an app is in /usr/bin

---

### Post by wilee-nilee on 2010-04-11
> **Myket said:**
> Couldnt find out how to update skype because i wanted to screen share. so i uninstalled skype and downloaded the new version from there website. i downloaded a Deb file and everything is installed and good to go. but now i cant find the exe file to open the program. i dont know the terminal code to open the file because i dont know where the exe is located

This is a little confusing, exe is a windows file system it will not run on Linux except in wine. But I think what you want is the launcher correct? I have never used skype but right click on the menu then edit menus and look if it is there but just may need to be ticked off then on to show.

You can build a launcher I would build one on the desktop first. Right click on the desktop then create launcher hit browse in the gui go to filesystem-usr-bin or sbin and see if skype is there if so click on it the hit open then name the launcher and see if it works.

---

### Post by kimda on 2010-04-11
Is there a launcher in Applications > Internet? On my notebook it installed a launcher (shortcut) there.

---

### Post by mörgæs on 2010-04-11
> **davec64 said:**
> Sometimes the menu entry isn't added to the Applications menu immediately, occasionally after a reboot it will appear. If it does appear it's likely to be in Accessories (if memory serves me right!)


In Ubuntu 8.10, it is in the 'internet' menu. Yes, a reboot is a good first try, if it does not show up.

---

### Post by davec64 on 2010-04-11
> **mörgæs said:**
> In Ubuntu 8.10, it is in the 'internet' menu. Yes, a reboot is a good first try, if it does not show up.

Thanks, my memory is going! It's a long time since I used Skype! :)

---

### Post by Myket on 2010-04-11
> **mörgæs said:**
> In Ubuntu 8.10, it is in the 'internet' menu. Yes, a reboot is a good first try, if it does not show up.

rebooted.. no luck still cant find skype. usr/bin and sbin dont have anything skype related in them.  i found a skype folder in my usr/share folder but no executable file types

---

### Post by wilee-nilee on 2010-04-11
So it might help to know which version of Ubuntu your using. The download from skype is intrepid, and may be no more updated then the one you removed.

---

### Post by jaco223 on 2010-04-11
Open the terminal and type

```
whereis skype
```
It should tell you where skype is. Navigate to that directory in the terminal and try

```
./skype
```
Hope this helps.

Jaco

---

### Post by 3rdalbum on 2010-04-11
Is Skype actually installed? Go into Synaptic and check (yes, it will appear in there if you installed it from a Deb).

---

### Post by trig on 2010-04-19
since i upgraded to 10.4, .exe are marked as not supported.
The file '/home/captain/Downloads/TryWoW.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.****

---

### Post by LowSky on 2010-04-19
> **trig said:**
> since i upgraded to 10.4, .exe are marked as not supported.
The file '/home/captain/Downloads/TryWoW.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.****

Trig you should have started  a new thread as your post isn't the same as the above question.

But to help you need to install WINE from synaptic or the software store

---

