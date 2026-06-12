---
title: "Dual Boot Menu"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by zipteye on 2010-11-23
Installed ubuntu 10.10 on my windows 7 HD using Free Space. (Shrunk the HD via windows disk manager)
Works fine, but I get several options when the computer boots. 
Ubuntu.
A couple mem check options.
Two Win 7 options (Im sure the second one is for the windows 7 backup partition)
Something about Windows Vista - doesnt make any sense as the computer came pre-loaded with Win 7 profesional.
 
I just want Windows 7 and ubuntu to show up.
And I want Windows 7 to be the default if I dont make a choice.
 
Do I need to gedit some file?

---

### Post by Jetso on 2010-11-23
Okay, I had the same questions... And I got it fixed... This WILL take a while, but it's fun and it teaches you alot! Okay to startoff. ```
gedit /boot/grub/grub.cfg
```
Make a copy of that file, then copy it. Then run ```
gksudo gedit /etc/grub.d/40_custom
``` And paste it on there. That is the first step, post when your done :P

---

### Post by Jetso on 2010-11-23
Well, anyway... After that, go into the 40_custom and take out all the one's you don't want, and change the names. Go into terminal and type ```
sudo chmod +x /etc/grub.d/40_custom
sudo update-grub. 
```
Reboot and you renamed entry's should be there. If they aren't post what you have in 40_custom. If they are working, then ```
sudo chmod -x /etc/grub.d/10_linux
```
When ever there is a signifigant update, run the same thing with a + in front of x

---

### Post by garvinrick4 on 2010-11-23
Do not worry about the Vista that is just how Linux reads that Windows partition
of Recovery in Windows 7. Nothing you can do about it, it is a Windows thing.
Read this if you want to: You can make changes in this file below:  Here is a link:  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
```
gksudo gedit /etc/default/grub
```can uncomment what you want (# is a comment) you are in root so focus. Save changes.
then run in terminal:
```
sudo update-grub
```# If you want to change the default OS in GUI install. will be in System/Admin/startup manager
```
sudo apt-get install startupmanager
```[URL="https://help.ubuntu.com/community/Grub2"]
[/URL]

---

### Post by zipteye on 2010-11-24
[SIZE=3]Did it all with just: sudo gedit /boot/grub/grub.cfg[/SIZE]

[SIZE=3]I changed the timeout from 10 to 5.[/SIZE]
[SIZE=3]Cut the Windows 7 menuentry and pasted it above the ubuntu menuentry.[/SIZE]
[SIZE=3]Used # to comment out all the other lines for the other menu entries.[/SIZE]
[SIZE=3][/SIZE] 


[SIZE=3][FONT=Batang]**if [ "${recordfail}" = 1 ]; then**[/FONT][/SIZE]
[SIZE=3][FONT=Batang]**set timeout=-1**[/FONT][/SIZE]
[SIZE=3][FONT=Batang]**else**[/FONT][/SIZE]
[SIZE=3][FONT=Batang]**set timeout=5**[/FONT][/SIZE]
**[SIZE=3][FONT=Batang]fi[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]### END /etc/grub.d/00_header ###[/FONT][/SIZE]**
 
**[SIZE=3][FONT=Batang]### BEGIN /etc/grub.d/05_debian_theme ###[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]set menu_color_normal=white/black[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]set menu_color_highlight=black/light-gray[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]### END /etc/grub.d/05_debian_theme ###[/FONT][/SIZE]**
 
**[SIZE=3][FONT=Batang]### BEGIN /etc/grub.d/10_linux ###[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]menuentry "Windows 7 (loader) (on /dev/sda1)" {[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]insmod part_msdos[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]insmod ntfs[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]set root='(hd0,msdos1)'[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]search --no-floppy --fs-uuid --set 4c56569a5656851c[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]chainloader +1[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]}[/FONT][/SIZE]**
 
**[SIZE=3][FONT=Batang]menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]recordfail[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]insmod part_msdos[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]insmod ext2[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]set root='(hd0,msdos3)'[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]search --no-floppy --fs-uuid --set dcb20e93-b137-4a47-b750-3c8179b02c37[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dcb20e93-b137-4a47-b750-3c8179b02c37 ro quiet splash[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]initrd /boot/initrd.img-2.6.35-22-generic[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]}[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]#menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class #ubuntu --class gnu-linux --class gnu --class os {[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# recordfail[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# insmod part_msdos[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# insmod ext2[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# set root='(hd0,msdos3)'[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# search --no-floppy --fs-uuid --set dcb20e93-b137-4a47-#b750-3c8179b02c37[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# echo 'Loading Linux 2.6.35-22-generic ...'[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# linux /boot/vmlinuz-2.6.35-22-generic root=UUID=dcb20e93-b137-4a47-#b750-3c8179b02c37 ro single[/FONT][/SIZE]**
**[SIZE=3][FONT=Batang]# echo 'Loading initial ramdisk ...'[/FONT][/SIZE]**
**[FONT=Batang][SIZE=3][/SIZE][/FONT]** 
**[FONT=Batang][SIZE=3]etc, etc...[/SIZE][/FONT]**

---

### Post by zipteye on 2010-11-24
[SIZE=4]Now...[/SIZE]
[SIZE=4]If I could only get this damned Belkin Wireless USB drive to work.[/SIZE]
[SIZE=4]Dont know how to use ndismanager, or whatever it is called...[/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]Have the Belkin Windows Drivers CD, but that does me no good.[/SIZE]
[SIZE=4]Can't plug into the ethernet as it stands right now, cuz the router is clear in the back room.[/SIZE]
[SIZE=4]So, internet with Win 7, but no worky with ubuntu.[/SIZE]

---

### Post by garvinrick4 on 2010-11-24
```
gedit /boot/grub/grub.cfg
```
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub


##actually do not no the reprocussions from editing this file that you did but it leads off with this above:

---

### Post by zipteye on 2010-11-24
[SIZE=3]There are no reprocussions. I just commented out the sections that I didnt want.[/SIZE]
[SIZE=3]I think that warning is there to keep people from tinkering with multiple lines and screwing things up.[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]At least I haven't encountered any reprocussions yet. I've rebooted , and cold rebooted several times to make sure.[/SIZE]

---

### Post by garvinrick4 on 2010-11-24
I am just wondering when grub updates will os-prober go out and find the other menu
entries and return you to state before editing it. Everytime that you update-grub or system
updates grub during upgrade it makes a new config file and looks in /etc/default/grub,
 so is that just a tempory fix because it was not done in /etc/default/grub seems very, very, very likely to happen.
Matter of fact look at your /etc/default/grub and you will see what it will return to when a new grub-mkconfig by
the update-grub command.

---

### Post by zipteye on 2010-11-24
> **garvinrick4 said:**
> I am just wondering when grub updates will os-prober go out and find the other menu
entries and return you to state before editing it. Everytime the you update-grub or system
updates grub during upgrade it makes a new config file and looks in /etc/default/grub,
so is that just a tempory fix because it was not done in /etc/default/grub seems very, very likely to happen.
 
[SIZE=3]Ah, I see.[/SIZE]
[SIZE=3]How often does Grub have to be updated? Or does it ned to be at all?[/SIZE]
 
[SIZE=3]Can i set it to ask me if it wants to update? [/SIZE]
[SIZE=3]And if I say 'no'?[/SIZE]

---

### Post by zipteye on 2010-11-24
[SIZE=2]Yep.[/SIZE]
[SIZE=2]I did update-grub and it set the boot menu back to what it was to begin with.[/SIZE]

---

### Post by Quackers on 2010-11-24
Yes it will do. That's why it says don't edit it :-)
All the details you want are in this guide by drs305

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Have fun :-)

---

### Post by Jetso on 2010-11-24
Or you could just do what I wrote. drs305 actually helped me do it.

---

### Post by zipteye on 2010-11-24
> **Jetso said:**
> Okay, I had the same questions... And I got it fixed... This WILL take a while, but it's fun and it teaches you alot! Okay to startoff. ```
gedit /boot/grub/grub.cfg
```
Make a copy of that file, then copy it. Then run ```
gksudo gedit /etc/grub.d/40_custom
``` And paste it on there. That is the first step, post when your done :P
 
Yeah, but i dont understand what you meant by "Make a copy of that file, then copy it."

---

### Post by Jetso on 2010-11-24
Oh, sorry. I meant to copy the contents, then paste them in 40_custom. Sorry!

---

