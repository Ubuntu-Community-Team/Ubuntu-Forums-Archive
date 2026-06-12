---
title: "Ubuntu wont boot please help"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by ran1wil on 2010-01-25
ok i have ubuntu 9.10 on the second hd and vist on the first all was fine untill the other day now ubuntu wont boot at all and dont know why and this is not the first time last time i just wipped the hd and reinstalled but i dont want to keep doing that can someone please help me i am new and i want to learn also i hope im posting this in the right place. oh yea it is on my laptop its an hp dv9000 if that helps i am also using the live cd now

thanks in advance

---

### Post by audiomick on 2010-01-25
first thing to do is go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
follow the instructions and post the output here. If I can't help, I am sure someone else will be able to.

---

### Post by ran1wil on 2010-01-25
Am i doing somthing wrong??? from terminal in the live cd this is what i got from the first two comands:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script*.sh
bash: /home/ubuntu/Downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo bash ~/Downloads/boot_info_script*.sh
bash: /home/ubuntu/Downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by audiomick on 2010-01-25
It looks like you haven't downloaded the script first.
That is right at the start.
> Special thanks to meiefra for authoring the script and making it available.

How to get it - Download it from here. Boot Info Script - SourceForge.net

or you didn't see this
> Update Karmic users - the default download directory is now ~/Downloads
Code:

sudo bash ~/Downloads/boot_info_script*.sh

---

### Post by ran1wil on 2010-01-25
A little more info for you on my problems:
My Boot Process is like this for any linux boot option:

Very long wait
a blinking courser  _ 
follower by an uncomlete filesys check that stops at about 9%
the drops to a maintenance shell and here i have no idea what to do
somewhere in between this i was able to see the following errors

DRdy Err
Media Error
Unc Err

Any Ideas

---

### Post by ran1wil on 2010-01-25
yea sorry but i was able to download it but had no idea how to install or use it

---

### Post by audiomick on 2010-01-25
I hate to say it, but you might have a problem with the HD.

Have another try with the boot info script, and see what that says.

If that looks ok, I think I can tell you how to check the drive.

---

### Post by ran1wil on 2010-01-25
yea this has been the same message each time
haw can i check the hd

---

### Post by ran1wil on 2010-01-25
Ok nevermind i fixed it with gparted 

thanks anyway

---

