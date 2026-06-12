---
title: "Fixing grub"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by sp-1070 on 2011-01-14
Howto install Windows next to Linux
If im correct this should work with Anny linux distro.

Secondly keep in mind that anybody makes mistakes i can be wrong or you might have done something wron if anny one post me a comment saying this and this in youre tut is wrong because this or that il edit it but it needs to be based on facts.
Now you got that continue

 I only tried this with Ubuntu and windows xp so the first thing you want to do is start partition magic,Make a partition for youre windows stuff or alternatively do this from the windows installation
First I’l guide you trough doing this when you don’t have a cd-rom drive such as netbooks(like my own)First thing you want to do for a windows xp system is get a xp cd (figures huh ? lol)You could also download it from somewhere but that’s on youre own (once again google is youre best friend)
Also download wintoflash (google it)
Follow the instructions just point to the xp files either on youre cd-rom or on the harddisk.
Then point to the usb a pop up shows saying the stick will be formatted click yes wait and done a bootable windwos installation usb.

For windows 7 this is way more easy peasy.
Grab a cd/iso download windows usb dvd tool and of you go.
Point to the iso/cd then the stick and done.

So now you did that restart the computer start from usb and do an install like you would normally do.Whammy grubs gone o gosh I hate this dude wrong howto I wanna  kill him…….Wait,Read and shut it =D                                                                                                                                                                                  Start into a linux live cd/usb again very easy for a cd burn the iso with nero or something that can burn images like power iso
Usb just go google unetbootin  follow the instructions (Or go to my profile and search my other threads theres a howto there)
There we are in the live mode open a terminal and do this:
Find /boot/grub/stage1
This prints the correct hd path like hd0,1 or anny thing else in the next commands REPLACE (HD0,0) FOR THAT OUTPUT.
Sudo grub
>root (hd0,0)
>setup (hd0)
>exit or quit

If in the evend of booting ubuntu works but not windows you open a terminal and go:
Sudo apt-get update grub and windows should be back if not youre screwed keep googling.
Thanks and bye bye

---

