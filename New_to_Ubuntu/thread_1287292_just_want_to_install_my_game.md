---
title: "just want to install my game"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by theoak on 2009-10-10
ok so i know ive posted a lot but i still havent been able to install my game. ive tryed the step by step doesnt work for me dont know why but it just doesnt.

ok so ive installed wine. now i typed "wine /media/cdrom0/Installer.exe" into my terminal ive tried the sudo mount remount command doesnt do **** but show a few more files, i do have the installer.exe file showing no need to do that command i believe. now when i type 
"wine /media/cdrom0/Installer.exe" into the terminal i get 

theo@theo-laptop-ak:~$ wine /media/cdrom0/Installer.exe
wine: could not load L"D:\\Installer.exe": Module not found

ive tried several other commands all to do with wine and file location. ive tried "wine" and draging the installer.exe file into the terminal to get the proper location, and get the same outcome wine:could not load L"D\\Installer.exe":Module not found.

what do i do now... how do i get this game to run and install in wine. let me say again ive done wowwikki installation methods ive tried numerous other installation methods and yet no install what so ever. what am i doing wrong. maybe someone can give me a step by step on how to do this im trying to install WOW3.1.0 and the expansions. i would really like to keep ubuntu jaunty 9.04 but this is just making me sick of trying to install this game. please help me.

---

### Post by Jazzy_Jeff on 2009-10-10
You should be able to right click on the wow installer and click on Open with "Wine Windows Program Loader", that was all I had to do to make it work. If you have problems getting it to work off your cd, you can download the installer from wow's website. Just log into your account.

---

### Post by theoak on 2009-10-10
well when i do try to open the installer with wine program loader i get access denied. what do i do?

---

### Post by orky7 on 2009-10-10
copy or rip all the data from the CD and put it in a folder in linux and then click on the .exe file it will get install (i hope so) .... i have done it for AOE-3

---

### Post by theoak on 2009-10-10
yeah... i dont have the permission to do that. thats what i get when i try that.

---

### Post by orky7 on 2009-10-10
ok u can copy the content of the CD by sudo command into a folder ...or if u have windows copy the data from there or u can log in as super user with all privileges. how to do it see this thread:

[http://ubuntuforums.org/showthread.php?t=220396](http://ubuntuforums.org/showthread.php?t=220396)

---

### Post by theoak on 2009-10-11
ok so when i open through super dude or whatever i still cant download. either syas the installer data cannot be found ive tryied the sudo mount remount code, got the extra files tried again and temporary files cannot be created all in all still wont dl and as what im trying to do copying the files onto my actuall desktop...still cant do that through root. i have installed the game on root and can play from /root/desktop but from what everyone is telling me is that to never run it through there. what do i do.

---

