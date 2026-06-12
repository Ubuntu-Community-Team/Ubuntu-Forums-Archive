---
title: "uninstall ubuntu, install windows"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by foxiemoxie on 2010-04-22
So I've been trying Ubuntu for the past 2 months and it really isn't for me. Unfortunately when my friend installed Ubuntu for me he didn't do it as a dual boot, so I need to completely reinstall windows. I'm a total n00b when it comes to working ubuntu. Can someone please help me?

---

### Post by muteXe on 2010-04-22
Just pop your windows disk in and install. It won't care what's on your drive.

---

### Post by P4man on 2010-04-22
Do make a backup of files you want to keep, browser bookmarks, perhaps emails and stuff. windows will gladly reformat the ubuntu partitions, but you will lose everything you did these last months, so think before you pull the plug.

---

### Post by foxiemoxie on 2010-04-22
Everything is backed up. I definitely need to go back to windows. I tried inserting the cd and nothing happens and I've tried to boot from the cd, but that isn't working either.

---

### Post by P4man on 2010-04-22
insert the cd, then reboot.
You may have to enter the bios to change the boot order so it boots from cd first, or press a key like F10 or F11 right after boot to get a bios boot menu.

---

### Post by Rex Bouwense on 2010-04-22
Sorry it didn't work out for you.  To boot from the Windows CD you need to insure that your CD is before your hard drive in the boot order in the BIOS.  You shouldn't have a problem after that.
Once again my two finger typing skills have caused my response to be OBE.

---

### Post by MooPi on 2010-04-22
Oh well you tried, maybe it was meant that you use Ubuntu :)

Okay bad joke...... Sounds like your computer needs to be set to boot from CD-rom. Find out what needs to be done to enter your bios. Usually its tapping delete or Function key(F11) to enter your bios. After you've entered your bios look for the boot menu or boot device priority, and set to CD-rom.

---

### Post by QIII on 2010-04-22
After backing up anything you want (as advised above), you may find that your Windows installation may puke when it sees ext partitions on the drive.  Hopefully not.  Hopefully it will allow you to reformat the drive as NTFS.

But Windows sometimes doesn't understand that there is a world outside of Windows.

If you encounter problems, get an Ubuntu LiveCD out.  While in a Live session, use gparted to change your drive to a single, large NTFS partition.

(Let us know if you need help here.  You will be able to access the internet while in the live session.)

Windows will think the world is well, and will happily install after that.

---

### Post by ScottinSoCal on 2010-04-22
I had to use the recovery disks on a notebook so I could send it in for a warranty repair, after I'd installed Ubuntu as the sole operating system. I ran into a glitch with grub not being removed and not working after Windows was installed, and had to use Partition Magic boot CD to repair the Master Boot Record. Just a heads-up, in case you run into the same thing. Fast and easy to do, but it did take that PM boot disk.

---

### Post by P4man on 2010-04-22
BTW, foxiemoxie, im sort of curious what it is that didnt work for you. Im especially curious since you never posted here during those 2 months you tried it, and you registered only after deciding it didnt work..? Why didnt you ask help when you actually encountered the problems and difficulties (which Im sure every new linux user encounters) ?

---

### Post by Rasa1111 on 2010-04-22
> **P4man said:**
> BTW, foxiemoxie, im sort of curious what it is that didnt work for you. Im especially curious since you never posted here during those 2 months you tried it, and you registered only after deciding it didnt work..? Why didnt you ask help when you actually encountered the problems and difficulties (which Im sure every new linux user encounters) ?

yea, seems kinda trollish. no?  :confused:
i saw something like this somewhere else and the person was just 'gettin kicks' , 
a window$ fanboy stirrin poo. . 
really.

---

### Post by novelty on 2010-04-22
It could be a troll but....

I kicked Ubuntu's tires last year and never posted a help.  I found out on my own, at that time, it just didn't work for me. Why? With the hardware I had, it was just too much of a learning curve.


 A couple months ago I picked it up again and between the changes in Ubuntu and having a little more time and inclination to learn it, I now have it on four machines.  Yes, even my main use machine.

So maybe a troll maybe not.

---

### Post by flyfishingphil on 2010-04-22
Note: He said a friend installed it. May not have been aware of this area. Also, when I first looked into Linux, in 2008, I stopped by one of the chats and all I saw was a bunch of geek talk that made no sense at all. Asked a couple of questions, regarding how it worked and what I needed to learn to use it, and never got an answer.

Maybe that's what happened here. Seeing a "foreign" language makes it hard to ask the questions.(Lots of questions are answered on the presumption that the asker knows exactly what a GRUB is, what it does and exactly how to use, they just need fine tuning.)

Just a thought.

---

### Post by Rasa1111 on 2010-04-25
true... 
 mybad...

awhile after i posted that,
i realized....

i also have a friend who i installed ubuntu for, (he is phil to, but he doesnt flyfish lol :p)
and i also help him with whatever little problems he runs/has run into  (not many*)..
and he has never posted on the forums for help. 

he's only contacted me or used google for help..

so , apologies for calling it 'trollish'..
 if indeed it was not intended to be.

good luck with your windows. 

..............................
..... but the breeze is far nicer when you get it through a door. :) lol

---

