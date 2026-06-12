---
title: "Dual boot issues"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by jwutwn on 2009-05-01
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Verdana][COLOR=#3c3b3b]Tried Ubuntu 8.10 on an old machine for about 2 months with so so experience as am a longtime windows user.[/COLOR]
[COLOR=#3c3b3b]Then came the 9.04 so I tried to dual boot with window 7 trial version. Problem is:
[/COLOR]
[COLOR=#3c3b3b]I had one 1gb disk with c drive installed Window7 and D drive for files. E drive is not formatted initially in windows 7. 
I then tried ubuntu by installing in E drive and assign D as swap drive. 
not realizing ubuntu not able to play some video formats so after boot into Window7 I just deleted the E drive(Ubuntu). That caused me not able to [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]reboot[/FONT][/FONT][/COLOR]]("http://ubuntuforums.org/#")[/COLOR][/FONT][/LEFT]
[/FONT][/COLOR][FONT=Times New Roman][LEFT][FONT=Verdana] back to Window 7, after some research I use MBRFIX on drive C, I now able to boot into Window7, but drive D is not visible. On disk management. this volume shows as (layout)Simple, (type) Basic, (under file system)empty, status shows healthy (primary partition). 
Do I have to reinstall 9.04 again to let windows7 see the D drive or is there any easy way? 
[/color]
[COLOR=#3c3b3b]I really wants to try 9.04 again but above scares me. Thank you for help.
BTW, I posted in Tom's harware for 2 days with no response I figured probably not the right forum to post my question.
[/COLOR]

[URL="http://ubuntuforums.org/forum/windows-7/answer-234-1.htm#formulaire"]
[/URL]
[/FONT][/LEFT]
[/FONT][/color]

---

### Post by overdrank on 2009-05-01
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by zeex on 2009-05-01
> **jwutwn said:**
> [COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Verdana][COLOR=#3c3b3b]Tried Ubuntu 8.10 on an old machine for about 2 months with so so experience as am a longtime windows user.[/COLOR]
[COLOR=#3c3b3b]Then came the 9.04 so I tried to dual boot with window 7 trial version. Problem is:
[/COLOR]
[COLOR=#3c3b3b]I had one 1gb disk with c drive installed Window7 and D drive for files. E drive is not formatted initially in windows 7. 
I then tried ubuntu by installing in E drive and assign D as swap drive. 
not realizing ubuntu not able to play some video formats so after boot into Window7 I just deleted the E drive(Ubuntu). That caused me not able to [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]reboot[/FONT][/FONT][/COLOR]]("http://ubuntuforums.org/#")[/COLOR][/FONT][/LEFT]
[/FONT][/COLOR][FONT=Times New Roman][LEFT][FONT=Verdana] back to Window 7, after some research I use MBRFIX on drive C, I now able to boot into Window7, but drive D is not visible. On disk management. this volume shows as (layout)Simple, (type) Basic, (under file system)empty, status shows healthy (primary partition). 
Do I have to reinstall 9.04 again to let windows7 see the D drive or is there any easy way? 
[/color]
[COLOR=#3c3b3b]I really wants to try 9.04 again but above scares me. Thank you for help.
BTW, I posted in Tom's harware for 2 days with no response I figured probably not the right forum to post my question.
[/COLOR]

[URL="http://ubuntuforums.org/forum/windows-7/answer-234-1.htm#formulaire"]
[/URL]
[/FONT][/LEFT]
[/FONT][/color]

Hi, 

I'm assuming you wanna go back to the way things were before Ubuntu 9.04 disaster :). The reason D: drive is not visible is because you assinged it as SWAP space and windows have no idea what swap space is :). I am gussing you can see and still use your E: drive. 

I'd advice you to use a Ubuntu live CD ( 8.04 or 8.10 , don't use the new 9.04). Boot with the live CD. There is a program called gParted. *(I'm assuming you know how to handle a partition tool because if you don't you could loose all other data, so be careful)*. Start the partition tool from System -> Administration -> Partition Editor . This 'll look something like this. 

[IMG]http://img471.imageshack.us/img471/1698/screenshotgpartedtj5.png[/IMG]

Now here you 'll see your D: drive as swap. Change it's property from swap to fat32 or ntfs. save changes and reboot to windows 7. It should show the device now you may need to format it. 

I hope this helps.

Good luck :)

---

### Post by jwutwn on 2009-05-01
> **zeex said:**
> Hi, 

I'm assuming you wanna go back to the way things were before Ubuntu 9.04 disaster :). The reason D: drive is not visible is because you assinged it as SWAP space and windows have no idea what swap space is :). I am gussing you can see and still use your E: drive. 

I'd advice you to use a Ubuntu live CD ( 8.04 or 8.10 , don't use the new 9.04). Boot with the live CD. There is a program called gParted. *(I'm assuming you know how to handle a partition tool because if you don't you could loose all other data, so be careful)*. Start the partition tool from System -> Administration -> Partition Editor . This 'll look something like this. 

[IMG]http://img471.imageshack.us/img471/1698/screenshotgpartedtj5.png[/IMG]

Now here you 'll see your D: drive as swap. Change it's property from swap to fat32 or ntfs. save changes and reboot to windows 7. It should show the device now you may need to format it. 

I hope this helps.

Good luck :)



Thank you for prompt and correct advise. Indeed I need D: drive back and need those data. "may need to format it" means data will be gone?
Am looking for ways that don't have to sacrifice to reformat as I know how to reclaim/reformat D:drive back.
Appreciate your further advise.

---

### Post by jwutwn on 2009-05-01
Hi,
Thank you for prompt and correct advise. Indeed I need D: drive back and need those data. "may need to format it" means data will be gone?
Am looking for ways that don't have to sacrifice to reformat as I know how to reclaim/reformat D:drive back.
Appreciate your further advise.

---

### Post by zeex on 2009-05-01
> **jwutwn said:**
> Hi,
Thank you for prompt and correct advise. Indeed I need D: drive back and need those data. "may need to format it" means data will be gone?
Am looking for ways that don't have to sacrifice to reformat as I know how to reclaim/reformat D:drive back.
Appreciate your further advise.

Hi, 

Let me get this straight. You want to get the data from D drive. Right ?? . I'm curious you didn't backup the data when you installed ubuntu. You changed windows filesystem (FAT32/NTFS) to SWAP and now you want the data back?.

See I want you to understand in some situations data recovery is possible like if you didn't format the dive when you installed ubuntu. Also you might need someone who knows the HOWTOs of data recovery. It's really complex geeky thing. If the files were not important don't worry about recovery and go ahead and if it was something important then i wish you luck. 

I don't think you completely understand the Linux installation process. Lot my friends 've done something like this and lost their data but mostly songs and movies. Please read more about Linux installation. I'm gonna make one myself.

Good luck :)

---

### Post by Niniel on 2009-05-01
> **jwutwn said:**
> Hi,
Thank you for prompt and correct advise. Indeed I need D: drive back and need those data. "may need to format it" means data will be gone?
Am looking for ways that don't have to sacrifice to reformat as I know how to reclaim/reformat D:drive back.
Appreciate your further advise.
If you assigned D: as the swap partition, then your data is essentially gone.
Swapping works different in Linux - you don't specify a page file that'll reside on a drive/partition, like in Windows, but instead, you create and assign an entire partition/drive to be used for nothing else but swapping. That partition/drive will be specially formatted for that purpose.
So you should have just used your e drive/partition for all of Ubuntu - OS and swap partition. The installer would have taken care of it for you. 

Regarding video, which formats were you trying to play? I can play pretty much everything, but I had to install some restricted codices. Was easy though - the player, Totem, prompted me, and I said yes, and that was pretty much it.

---

### Post by jwutwn on 2009-05-01
Than you, noted D drive data is gone!
Video RMVB format seemed stutter.

---

### Post by zeex on 2009-05-01
> **jwutwn said:**
> Than you, noted D drive data is gone!
Video RMVB format seemed stutter.

Hi, 

just a reminder. You never needed the D drive for ubuntu installation. See if you choose say E drive for ubuntu. 

1) Backup the data from E 
2) Start installation from live CD. 
3) _*In partition editor make a SWAP partition from E drive itself.*_
4) Install ubuntu.

This way in case you need to remove linux All you need to do is merge both swap and / and then format it.

Use VLC or Smplayer. I use both of 'em. works like charm and plays every format.

---

### Post by sadaruwan12 on 2009-05-01
If you're finding it's difficult to understand the installation process of Ubuntu refer this guide and try to do it as it mentioned there.

About your D: drive it's better if you forget about that drive 'cos all the is gone so let this be lesson and learn from it to backup data before doing anything to the system.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04")

---

