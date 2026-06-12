---
title: "computer turned off during win update,...help please"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by apdturbo on 2010-02-21
Hello all, i'm a newb to ubuntu. here is my issue.
 
My father-in-laws dell netbook with ubuntu and win xp was recently shut off during a windows update(i know this is bad and windows is corrupt at this point), ubuntu seems to load fine then windows begins to load i hit the "Fn" key and "F8" to enter safe mode but the computer loads into windows and the mouse is dead. it will not load into safe mode!!! doesn't even show the XP screen just shows white screen for a few seconds and mouse works then loads desktop and freezes....... how can i save this sweet little netbook????? im "ok" with computers but know nothing about ubuntu... any help would be great!!!!!!

---

### Post by J V on 2010-02-21
> how can i save this sweet little netbook> ubuntu seems to load fineBy definition "saving" a computer entails removing windows, so you don't have to do anything :)

If you want to get windows working you will have to take it to someone to get the data recovered and then wipe it and re-install (and if it doesn't have built in recovery that means buying a new copy of windows)

---

### Post by JiuJitsu500 on 2010-02-21
Well, you can wipe the whole thing out and start fresh with ubuntu :)

Use a live USB to back everything up... then re-do the computer fresh with Ubuntu.

But, I think you just confused me, a lot. When ubuntu loads it's fine but when windows loads it's bad? Windows loads completely seperately from linux... the same machine can't boot two OS's at the same time.... are you saying when you boot ubuntu it's okay, but when you restart and boot windows it's bad?

*edit - you totally got there before i did... I lose...

---

### Post by spiky001 on 2010-02-21
Is it not pssible to acess the data from ubuntu side by going to paces then windows file system save it the sort out windows, i thought netbooks had a recovery partion on them correct me if i,m wrong

---

### Post by JiuJitsu500 on 2010-02-21
> **spiky001 said:**
> Is it not pssible to acess the data from ubuntu side by going to paces then windows file system save it the sort out windows, i thought netbooks had a recovery partion on them correct me if i,m wrong

I'm not sure exactly what you just said, but yes you can see anything on any hard drive put in the computer from any OS, it just won't be able to open it if the format or extension or OS isn't supported, obviously. I've used Mac and Windows to look at ubuntu files just to see if I could, and ubuntu to look at windows (virus scanning too) and Mac files.

It sounded like you wanted to say you can't look at ubuntu stuff from windows, which is wrong. If thats not what you said though I just made a pointless post :)

And yes, most computers (I haven't seen a windows computer without) have a recovery partition on them... but recovery won't work if the OS is completely screwed, only re-installing it... and windows recovery is the suck anyway, never worked for me, still had the virus that led me to looking for the alternative that freed me and so many others... (looks to the sky, sees Saint Linus Torvalds and Tux) l... o.... freakin... l

---

### Post by apdturbo on 2010-02-21
like i said i'm new to ubuntu and don't fully understand it, this computer was just handed to me with this problem and so all i know thus far is some basic searching on this forum (which has helped explain some things).
 
when the computer boots it shows the ubuntu logo with a "loading status type bar thing" under it, after that is proceeds to a white screen then the desktop then freezes, i understand that ubuntu is a seperate OS from XP but why then does ubuntu even load at all if this is normally set to run the XP OS
 
also this being the first time i've ever even seen ubuntu i can say that when the desktop loads and freezes it doesn't look like win XP at all, even though a win update bubble does pop up amidst the freeze.
 
in searching this subject on this forum it seemed like everyone was able to get into safe mode and recover to a working win OS, with that not being the case here i'm not sure what i want to do.
 
i could wipe it cause theres nothing of importance
 
another question for you guru's while messing with the computer i got into a login screen for ubuntu, if i got my father in laws name and password could i still use this OS? i'm used to windows based stuff unfortunately....
 
theres no cd-rom drive on this netbook, normal ports network, usb and a memory card port, how would i reload windows into this machine? 
 
be honest..... am i in over my head?
 
and thanks for the help thus far guys!

---

### Post by spiky001 on 2010-02-21
It can be reloaded from a usb stick but can get to that later you would have to download the operating system, if that was the way you wanted to go, also there is the option of getting past the asswords to see what happens then will leave it to you to ponder over, but there is plenty of help on forums all can be fixed 1 way or another

---

### Post by nick_goodfate on 2010-02-21
> It sounded like you wanted to say you can't look at ubuntu stuff from windows, which is wrong.
how you can do this , because i knew that this was right ...

---

### Post by Paddy Landau on 2010-02-21
> **apdturbo said:**
> also this being the first time i've ever even seen ubuntu i can say that when the desktop loads and freezes it doesn't look like win XP at all, even though a win update bubble does pop up amidst the freeze.
Sorry to labour the point, but I'm quite confused here. Please be very specific as to what happens. Here is what I *think* you are saying; correct me if I'm wrong:

[LIST]
[*]You turn on the computer. The computer asks what operating system you want.
[*]If you choose Windows, it starts but then appears to freeze, with a Windows Update bubble on the screen.
[*]If you choose Ubuntu, then Ubuntu loads fine.
[/LIST]
  Also, if you could tell us what version of Ubuntu you installed (9.10? Jaunty? etc.). And how did you install: A proper native install with the Live CD (using a USB stick, I would presume)? Or did you install Wubi?

We need to understand exactly what's happening and how you got there, otherwise we're guessing and could give you totally wrong advice.

---

### Post by Paddy Landau on 2010-02-21
> **JiuJitsu500 said:**
> It sounded like you wanted to say you can't look at ubuntu stuff from windows, which is wrong.
To look at ext2, ext3 or ext4 partitions from Windows, you need an appropriate driver. I've found a good [Windows driver for ext2 and ext3]("http://www.ext2fsd.com/"), and one for [read-only ext4]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/"), but none for read-write ext4.

If you've found a read-write driver for ext4, please let us know.

---

### Post by apdturbo on 2010-02-21
ok wow i figured a bunch out, this machine isn't running windows at all, it is purely ubuntu and i don't know why he told me windows xp he knows far less about computers than i and i feel like i don't know much and since he shut if off in the middle of an update i should have known he had no clue about this netbook at all......
 
sorry to mislead to you guys
 
this computer is locking once it loads into _ubuntu_ because it was shutoff in the middle of an update......
 
sooooooooo
 
is there a restore function in ubuntu? like a safe mode?
 
sorry for the confusing statements to this point but hey i'm figuring this thing out.....

---

### Post by spiky001 on 2010-02-21
I think if I were you I would reload ubuntu. As you have a netbook you wil need to load it via usb memory stick

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Have a look here

---

### Post by wobin77 on 2010-02-21
Can you choose an older kernel (a whole lot of numbers) on boot?  
like this:
[img]http://tugulab.files.wordpress.com/2008/02/grub_prima.png[/img]

---

### Post by J V on 2010-02-21
Yes either boot a live cd and save the data or get into grub (what was legacies shortcut key again?) and choose recovery or an older kernel, chances are its a userland problem though...

booting into recovery and reinstalling all the packages should work too, but thats unknown territory for me :)

---

### Post by Paddy Landau on 2010-02-22
> **apdturbo said:**
> ... i don't know why he told me windows xp
Non-technical people have heard "Windows" so many times that they think "Windows" means "computer", just as many people think that Hoover means vacuum cleaner. It's likely that he won't have the foggiest idea of the difference between Windows, Linux, Mac or anything else -- just as when I drive a car, I have no idea about the difference between a carburettor and a spark plug. I just drive it.

> **apdturbo said:**
> sorry to mislead to you guys
np, at least we now know what's going on.
 
> **wobin77 said:**
> Can you choose an older kernel (a whole lot of numbers) on boot?  like this:
If you don't see that menu when turning on, then do this: When you turn on the computer, repeatedly press the Shift key until you get that menu. (Unless the Ubuntu version is before 9.10, in which case you'll have to press the Escape key.)

Are you sure that it has Ubuntu and not some other distribution of Linux?

---

