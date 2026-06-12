---
title: "May have messed up partitions"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-02-05
When I reinstalled Ubuntu I think I may have accidently made an extra patition which I didn't need. I took a screenshot in GParted but can't find it :D The extended partition has nothing on it. Below is what I got doing fdisk -l There is no option on GParted to delete it. 



 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       15423    21486937+   5  Extended
/dev/sda3           15424       30401   120310785   83  Linux
/dev/sda5           12749       12991     1951866   82  Linux swap / Solaris
/dev/sda6           12992       15423    19535008+  83  Linux
kayte@SuperCow:~$

---

### Post by sailthesea on 2010-02-05
Looks like sda2 has 5 extended within it If you don't have anything working there just boot into LiveCD and wipe the lot, create a new one and reinstall The screenshot from GParted would be easier to sure of though!;)

Edit: Apart from sda1 JUST TO BE CLEAR!! Thats Windows Yes? You want to keep it?

---

### Post by ThePinkWitch on 2010-02-05
> **sailthesea said:**
> Looks like sda2 has 5 extended within it If you don't have anything working there just boot into LiveCD and wipe the lot, create a new one and reinstall The screenshot from GParted would be easier to sure of though!;)

Thanks for your reply.

Damn I was hoping not to have to reinstall again. That was my Fifth and it's taken two days to set everything up again :( The screenshot went to Root something and I don't know how to go there. It says I don't have permission.

---

### Post by ThePinkWitch on 2010-02-05
When I partition I'm not sure what is primary and what is the other one. And it says for the partitions beginning or end. Eg where does / go, Swap and Home. Are they primary? I just guessed and maybe I guessed wrong. The extended partition has nothing on it.

---

### Post by sailthesea on 2010-02-05
Thats easy enough
Open a terminal and enter 
sudo su
Then your password, it won't show on screen
You now have root power for 10 15 mins and can access all the files in your directory You may also be able to edit any unmounted partitions with Gparted and solve your problem Be CAREFUL what you do as a root user!! ;)

---

### Post by sailthesea on 2010-02-05
Best to back up a bit here!!
Do the sudo su thing and run Gparted to get a picture of your drive up and see whats what You seem seem to have a few empty partitions but lets get a clear idea Don't change anyting else yet!

---

### Post by ThePinkWitch on 2010-02-06
> **sailthesea said:**
> Thats easy enough
Open a terminal and enter 
sudo su
Then your password, it won't show on screen
You now have root power for 10 15 mins and can access all the files in your directory You may also be able to edit any unmounted partitions with Gparted and solve your problem Be CAREFUL what you do as a root user!! ;)

I may be able to access the files but I have no idea what to look for or where :D I went back with gparted and the only option for that partition is move or re-size. I'll try to get another screenshot and see where it went. I have another problem now as I installed wicd and removed Network manager and couldn't get wicd to work so I uninstalled it. I'm now using winxp because I have no internet. Thanks for your help :)

---

### Post by cwalker1960 on 2010-02-06
you can't delete an extended partition as long as there are partitions inside it   sda5 and sda6 are inside extended sda2 look at the start and end  #s from fdisk shot.. if you feel you have too many partitions you can delete sda6 and resize sda5 to include the whole extended area.

---

### Post by cwalker1960 on 2010-02-06
oh and you can't add or write anything to an extended partition ,, logical partitions go inside it. like sda5 and sda6 are now.

---

### Post by ThePinkWitch on 2010-02-06
Thankyou cwalker1960. I'm going to reinstall again because I have network issues. This is the last time. If I have any more hassles I'm slinking off back to XP. this will be the SIXTH time I've installed Ubuntu.

---

### Post by cwalker1960 on 2010-02-06
don't give up on Linux. i just spent 3 days trying to get grub-pc to do what i wanted it to. try puppy Linux on a cd you will be blown away by how fast everything is .. it's really the os that got me interested in Linux .. i just got through with a 4 os install and finally got grub to accept all 4 and load them. this form is a great source of information ,, but i think things could be a little more organized .. by the way puppy is so small you can run it from memory if you have around 512 mb  or it runs great from cd or usb thumb drive. I've been on xp for years and just needed a fresh start as system was taking forever to do anything. so during the re install i decided to see what all teh rave was about linux. also testing kubuntu right now  it's different but not too hard to get used to ,,i really beleive if the linux community ever expects to get a foothold in the pc arena someone is going to have to come up with a gui for grub ,, or some other loader ,, don't get me wrong ,,after delving into grub for the last 3 days I can appreciate it's complex simplicity ,, but it's way beyond the average windows users realm of patience.

---

### Post by cwalker1960 on 2010-02-06
by the way , i don't know about Linux yet ,, 3 days into it,, but i know plenty about hard drives and formatting. been into that since the late 80's .. lost a bunch of data on a bad drive and immediately understood the importance of backing up files ,, my first home built computer in the 80''s had 2 drives , today when i re install windows i keep the old drive in tact for several months just in case i find there was something i forgot to retrieve. most of time now i have 3 drives running. and always the last drive i used in a drawer just in case.

---

