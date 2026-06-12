---
title: "access files in ubuntu"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by MelDJ on 2009-10-15
hi there, i installed ubuntu inside windows with wubi. is there a way to see the files in ubuntu through windows? 
i can boot into ubuntu, so i want to get my files from ubuntu and format it. 
anyone has a way?

i CANT BOOT into Ubuntu

---

### Post by hellblazer on 2009-10-15
Yes [there is]("http://www.fs-driver.org/")!

I've used it for a couple of years without any issues

---

### Post by MelDJ on 2009-10-15
i installed it with wubi. so i dont think there is an ext partition. thanks for the link anyway

---

### Post by halitech on 2009-10-15
WUBI uses a loopback file to create a filesystem inside a file so its not a real partition so I don't think you will be able to access it from Windows. Why can't you boot into Ubuntu? maybe we can help fix it so you can boot again.

---

### Post by MelDJ on 2009-10-15
here's the thread of why i cant boot into ubuntu: [http://ubuntuforums.org/showthread.php?t=1291906](http://ubuntuforums.org/showthread.php?t=1291906)

thanks

---

### Post by halitech on 2009-10-15
I'll admit I've never used wubi so I'm not sure how to help with that. Maybe give it some time and see if someone can help. Also, might want to try posting in the wubi section for assistance.

---

### Post by MelDJ on 2009-10-15
thanks. will do it

---

### Post by yalgret on 2009-10-15
[SIZE="7"][B][U][COLOR="Red"][CENTER][FONT="Impact"]STOP!
[/FONT][/CENTER][/COLOR][/U][/B][/SIZE]
I am quite new to ubuntu but I know a terribly easy way to view your files:

   >Open the file browser (just click on documents)
   >Go to the root folder (keep pressing up one level untill it stops)
   >You will see a few folders, look for one named "host"
   >Click on it and you have you "C:" drive (you will have to navigate to get to your documents)

Good luck
:guitar:

---

### Post by MelDJ on 2009-10-15
thanks for taking the trouble for posting. but i want to view my UBUNTU FILES through WINDOWS. the way you showed was to see windows files through ubuntu.

---

### Post by halitech on 2009-10-15
Just out of curiousity, what do you see for files if you go to c:\program files\ubuntu (guessing on the location but should be in the program files folder)

---

### Post by MelDJ on 2009-10-15
> **halitech said:**
> Just out of curiousity, what do you see for files if you go to c:\program files\ubuntu (guessing on the location but should be in the program files folder)

its in C: ubuntu.
i have:
Folders:
disks
docs
install
winboot
text files:
curl_log
metadl_log
apps:
ubuntu
uninstall ubuntu

using the program given by the earlier poster, i could mount the ubuntu partition. but all the files were weird files

---

### Post by halitech on 2009-10-15
can you go into any of the folders (specifically the disks folder) and see anything?

---

### Post by MelDJ on 2009-10-15
> **halitech said:**
> can you go into any of the folders (specifically the disks folder) and see anything?

in disks there are the folders shared and boot. shared is empty. boot has grub and vmlinuz files

---

### Post by halitech on 2009-10-15
you say there is a file called ubuntu that is an application, what happens if yo try to run it?

---

### Post by MelDJ on 2009-10-15
> **halitech said:**
> you say there is a file called ubuntu that is an application, what happens if yo try to run it?

my mistake!
its actually an icon:neutral:

---

### Post by halitech on 2009-10-15
ahh dang, was hoping it would run in a terminal window

well, hopefully someone will have an idea for you later on one of the threads

---

