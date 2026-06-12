---
title: "black screen/mo kernel ubuntu 9.10"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by daveinuk on 2010-03-08
hello people :) first time post, hoping you may be able to help  . . . .
had ubuntu on a dual install with xp for about 2 weeks, never used it before and i know nothing about command lines etc  . . .  got quite used to it then it just went off yesterday and won't boot. i get a black screen with GNU grub version 1.97 etc etc . . .  ends in 
sh:grub:>

googled loads and cant find an answer that makes sense to me, sorry totaly windows dependant but working on that lol  . . . . . 

cut a long story short i tried a command and got  - no loaded kernel 

so  . . . . do i go into add/remove in windows and uninstall and then reinstall cos i cant seem to find an answer (that i can understand anyway lol) but it seems this has happened because of an update the other night, i just don't know why, everything else has worked great up until then? 

thanks in advance, take it easy on the big command explanations please i am new 0)

---

### Post by MooPi on 2010-03-08
Will need some extra info to be able to help. Did you install using wubi in Windows or did you use the install CD ?

---

### Post by MichealH on 2010-03-09
- Neither way he can try pressing CTRL+ALT+F7 to get on the GUI?
- Has your disk been defected? Try it out but pressing "Check Disk for Defects" at the CD Menu.

---

### Post by daveinuk on 2010-03-09
hello thanks for getting back to me, was late last night when i posted hence the long delay replying  . . .   i installed it from cd, its alongside windows on a separate partition and it is in ext3 if i remember rightly. 

i cant seem to do anything from the 'grub' screen if thats the right name, except reboot and find some commands, really new to ubuntu so i dont know if you mean i put the cd in before booting up or while i'm in windows? i dont know if the disk has been detected (the ubuntu partition?) as i cant get past the black grub screen. 

thank you

---

### Post by daveinuk on 2010-03-09
sorry i see what you mean, booted from the disc and checked for errors, none came up, shouldn't do really its a pretty new machine (less than 18 months) i only got this problem after an update the other night. there doesn't seem to be an option to repair the install from the cd? just the usuall options for install/ try without - just the same options as when i installed it. 

i'd just reinstall it if this would have been windows  but i'd just got it how i liked it and set up a load of accounts and mail etc! also i don't know how i go with doing that anyway with installing it after windows, would it detect the install and just overwrite it? and then if i update again will i be back here with the same problem??

@moopi as far as i know i haven't got wubi? i checked add/remove in windows and i just see ubuntu in there thats all.

---

### Post by daveinuk on 2010-03-10
anyone got any advice regarding reinstalling ubuntu for me please? if there's not an easy fix then thats the way i'll have to go. 

do in uninstall from windows or boot from the disc and overwrite the partition and is there any likelyhood of the kernel error happening again?

---

### Post by halitech on 2010-03-10
before you go and reinstall, what video card do you have?

You say you checked Windows Add/Remove programs and you see Ubuntu listed? If I read that right then you used WUBI to install Ubuntu *Inside* windows and not in it's own partition.

---

### Post by daveinuk on 2010-03-10
thanks for the reply, it's an nvidia geforce9500gt, i did install it inside windows and it suggested a partition size of 17gb i think, what i meant was when i looked in add/remove i didn't see anything with the name wubi so i presumed i didnt have it but i'm not familiar enough with it yet to even know if my terminology is right!

---

### Post by halitech on 2010-03-10
I've never run an Nvidia card so I'll leave that part to someone with more knowledge :)

WUBI is the Ubuntu installer that allows you to install Ubuntu inside windows basically as a program instead of partitioning your hard drive. This allows Ubuntu to run in a "fake" filesystem but not without its issues. It's okay if you just want to try it out but personally I would do a true install if you plan on keeping it.

---

### Post by daveinuk on 2010-03-11
bump . . . . . 

been posting quite late (in the uk) so i'm posting from work in case anyone with a bit more knowledge of the **nvidia geforce9500gt** cards is on during the day that's had the same problem and might have any suggestions for me ;)

 thanks

---

### Post by clive littlewood on 2010-03-11
Hi

Put your Ubuntu live CD in the drive and boot from it (make sure your bios is set to boot from Optical drive)

A menu will appear giving you the option to try Ubuntu without altering your system.

Opt for this and you will get the OS running in ram.

You can then check that all your hardware works OK and if your happy then you have the option to install.

Ubuntu will give you the option to install alongside of windows as a dual boot.

Hope this helps

Clive

---

### Post by daveinuk on 2010-03-11
hello clive thanks for that. 

can i update or install  the missing kernel while i have the cd in?? as ubuntu is already installed will it automatically overwrite the ubuntu OS that's in there? obviously what i don't want to end up with is another 17gb taken up.

---

### Post by clive littlewood on 2010-03-11
Hi

Any changes you do whilst in "live CD" mode will not be retained.

This is only good to check that all your hardware, wifi etc. is recognized.

If you then decide to install and you get to the partition stage choose to partition manually, if you choose auto it will leave all the OS intact and as you say take up add space.

When you choose manual you can the choose the existing Ubuntu partion to use and you will just get a clean install alongside windows.

Hope this helps

Clive

PS. If you get to the partion stage and are not sure, if you you have access to another comp. then come back on here and people will help you out.   GOOD LUCK     :D

---

### Post by daveinuk on 2010-03-11
thanks again for the reply, the only thing i'm struggling to understand is that it all worked previously for 2/3 weeks before the update which was the last thing that happened before it stopped working, so it must have found my hardware to be compatible surely? 

i think i'll have to go with the manual partition and overwrite it, it wont boot as is and i do want to learn how to use this OS as against windows as i'd like to move away from windows eventualy - but i dont yet have a (spare) machine i can have it installed on as the main OS but i do intend to get a laptop soon and just use Ubuntu on that, i do appreciate it gets more complicated with a dual boot, i was just hoping my experiment with both would have gone a bit smoother so i could have formed a better comparison !

---

### Post by asharpham on 2010-03-11
I'm a newbie too but I was advised not to do any updates because I ended up with problems every time I did updates. So I NEVER update these days.

Alan.

---

### Post by daveinuk on 2010-03-11
i was under the impression that the OS automatically updated at least once every 6 months and updated all your installed software as well? 

is it just me being spoon fed on windows that makes me feel i'd be missing out on something important if i didn't update? and by important i mean potentially critical?

---

### Post by halitech on 2010-03-11
> **daveinuk said:**
> i was under the impression that the OS automatically updated at least once every 6 months and updated all your installed software as well? 

is it just me being spoon fed on windows that makes me feel i'd be missing out on something important if i didn't update? and by important i mean potentially critical?

They release new versions every 6 months but that doesn't mean your system will be updated every 6 months. Those releases are version upgrades. 

Updates come out whenever there is a security hole or bug that needs to be fixed. Personally, the security updates should be installed as they come out to prevent your system from being compromised. Bug updates should be done as well but they aren't as important.

---

### Post by daveinuk on 2010-03-11
thanks hali, i would personally prefer to keep everything updated myself, how often should i check for updates? i think i did it a couple of times while it was working . . . .  can you update too much?

---

### Post by halitech on 2010-03-11
when there are updates you should get an icon up by the clock saying there are updates. I think its some kind of star shape. Far as updating, you can manually check every day but it will only update when there are updates.

---

### Post by daveinuk on 2010-03-11
well i booted from the cd and it worked ok and ran through a series of tests that seemed to imply that it would be good to go, but stopped me on the nvidia when i did the sound test as i didnt get the test sound, even though when it was working the sound/graphics were good and i also had the advanced graphics applied (with the stretchy windows) 

i stopped installing at the point when it got to the drive as i could have guessed but wanted to check first  . . . .  
 i had the choices of: 

/dev/sda1 ntfs 30691 mb
/dev/sda5 ntfs 199888 mb (which i thought was my 17gb partition with ubuntu on? )

so i'm undecided what to do now  . . . .  i'm thinking of buying a cheap IBM ThinkPad T42 Laptop (1.7GHz 40GB 1GB onboard) and formatting windows and just having linux on that as i appreciate that its not the best idea to have 2 OS's on a machine really  . . . 
and i may well get it within the next week as i do like what i've seen of linux so far, but when it comes to laptops though, aren't there meant to be some versions that are more suited to them than others?  i think its kubuntu and debian i've read about that are meant to be 'the ones' to install on a laptop but there's so many i dont know if thats right or just opinions lol  . . . . .

---

