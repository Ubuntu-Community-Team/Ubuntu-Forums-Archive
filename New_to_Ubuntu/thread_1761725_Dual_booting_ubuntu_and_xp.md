---
title: "Dual booting ubuntu and xp?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by bobbrock on 2011-05-18
So i decided to dualboot my xp with ubuntu 11.04 after not been able to get my wireless to work
with my laptop ."At least for now" 
When i install ubuntu 11.04 side by side with my xp home edition it work fined all day yesterday 
i booted a couple times and everything seem to be working ok except one thing i notice tha my
 partition were i have my xp on pop in on my ubuntu desktop it reads "25GB file system".
Today when i first booted into my xp os i got this 
System32\drivers\ntfs.sys is missing something like tha.So i looked it up on the net
And decided to used my windows xp cd to recover those files.
But  my windows xp cd is now giving me this message
File setupdd.sys could not be loaded the error code is 7.
I looked tha up online and i read a few people took their ram out and reseted it and their problem 
went away .I have'nt try tha yet. I figured i post here first since this issue started after installing 
ubuntu 11.04 .The funny thing is tha ubuntu is working great .But not xp .

Thanks for ur help Guys.

---

### Post by wildmanne39 on 2011-05-18
> **bobbrock said:**
> So i decided to dualboot my xp with ubuntu 11.04 after not been able to get my wireless to work
with my laptop ."At least for now" 
When i install ubuntu 11.04 side by side with my xp home edition it work fined all day yesterday 
i booted a couple times and everything seem to be working ok except one thing i notice tha my
 partition were i have my xp on pop in on my ubuntu desktop it reads "25GB file system".
Today when i first booted into my xp os i got this 
System32\drivers\ntfs.sys is missing something like tha.So i looked it up on the net
And decided to used my windows xp cd to recover those files.
But  my windows xp cd is now giving me this message
File setupdd.sys could not be loaded the error code is 7.
I looked tha up online and i read a few people took their ram out and reseted it and their problem 
went away .I have'nt try tha yet. I figured i post here first since this issue started after installing 
ubuntu 11.04 .The funny thing is tha ubuntu is working great .But not xp .

Thanks for ur help Guys.
Hi, I am pretty sure it has nothing to do with ubuntu, if you were able to boot xp even once after the ubuntu install, if you were not then it could be. Please post if you could or not even once.

---

### Post by bobbrock on 2011-05-18
Yes i was able to boot windows xp just fined after installing ubuntu 11.04
but not today.

---

### Post by jtarin on 2011-05-18
Go to this [LINK]("http://ubuntuforums.org/showthread.php?t=1291280") and follow instructions to post a boot info script here.

---

### Post by bobbrock on 2011-05-19
I tried that but im getting this 
dell@dell-Optiplex-GX280:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for dell: 
bash: /home/dell/Desktop/boot_info_script*.sh: No such file or directory
dell@dell-Optiplex-GX280:~$

---

### Post by jtarin on 2011-05-19
That should tell you one of three things. You have no file in that location by that name, you are in the wrong location or you only think  you downloaded the file. If you have the file....check the path.To see the contents of any directory use the command "ls" without quotes. Open a terminal....type "ls".....do you see the Desktop directory? Then cd into it and then do "ls" again.Do you see your script? Then in the terminal type "./boot_info_script*.sh"......no quotes

---

### Post by bobbrock on 2011-05-20
I tried running boot info scrip060 but i couln't get it to work i check my downloads and is there i also move it to my desktop and tried from there  didn't work either i downloaded it again still kep getting the same message
dell@dell-Optiplex-GX280:~$ sudo bash ~/Downloads/boot_info_script*.sh
[sudo] password for dell: 
bash: /home/dell/Downloads/boot_info_script*.sh: No such file or directory
dell@dell-Optiplex-GX280:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/dell/Desktop/boot_info_script*.sh: No such file or directory
dell@dell-Optiplex-GX280:~$ 

This is what i got from "ls,cd,ls,./boot_info_script*.sh


dell@dell-Optiplex-GX280:~$ ls
Desktop    Downloads         Firefox_wallpaper.png  Pictures  Templates
Documents  examples.desktop  Music                  Public    Videos
dell@dell-Optiplex-GX280:~$ cd
dell@dell-Optiplex-GX280:~$ ls
Desktop    Downloads         Firefox_wallpaper.png  Pictures  Templates
Documents  examples.desktop  Music                  Public    Videos
dell@dell-Optiplex-GX280:~$ boot_info_script*.sh
boot_info_script*.sh: command not found
dell@dell-Optiplex-GX280:~$ ./boot_info_script*.sh
bash: ./boot_info_script*.sh: No such file or directory
dell@dell-Optiplex-GX280:~$

---

### Post by jtarin on 2011-05-20
First you download....then go to your download directory and un-zip the file.Right-click on the "boot_info_script.sh" file and choose properties>permissions (tab)>check box "Allow executing file as a program">close.
 Then open a terminal and "cd" (change directory) to the directory you downloaded the file to. _The terminal's default location when it opens is the users /home directory_. In your case it will be like this if your default download location is "Downloads" directory.
.
```
dell@dell-Optiplex-GX280:~$ ls
Desktop Downloads Firefox_wallpaper.png Pictures Templates
dell@dell-Optiplex-GX280:~$cd Downloads
dell@dell-Optiplex-GX280:~$ls
dell@dell-Optiplex-GX280:~$boot_info_script060  boot_info_script060.zip
dell@dell-Optiplex-GX280:~$cd boot_info_script060
dell@dell-Optiplex-GX280:~$ls
dell@dell-Optiplex-GX280:~$boot_info_script.sh CHANGELOG
dell@dell-Optiplex-GX280:~$sudo ./boot_info_script.sh
```

---

### Post by bobbrock on 2011-05-20
jtarin my windows xp just bootup a gain this is what i did .
I unplugged the motherboard and the hardrive then i took 
the four sticks of ram tha it haves and then i plugged everything back up and 
put two sticks af ram and  it booted up then i put the third stick and it booted
up just fined again so i went a head and put the fourth stick of ram back and
it booted up again and now im replying back.

---

### Post by jtarin on 2011-05-20
Great!!! mark this thread as solved.

---

