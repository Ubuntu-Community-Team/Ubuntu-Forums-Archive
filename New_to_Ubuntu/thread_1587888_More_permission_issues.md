---
title: "More permission issues"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by Sgele™ on 2010-10-04
Hi,

Problem? I can't set VLC player as my default media player.
When i tick 'set as default' when right clicking a AVI file and have VLC play these files, i get the message that i do not have any permission to do this. 

I saw some other topics on this, and i tried sudo nautilus, as well as the other options, to no avail unfortunately 

Though i can only open my desktop with that, and not my home folder, so i can't access the downloads folder. I thought i'd be smart, and copy that file (AVI) onto my desktop folder --> sudo nautilus, but... no file to be found.

As i am really new to Ubuntu, this permissions thing is driving me bonkers.. 

Is there a way to get full permission access to my Ubuntu installation? If even these 'basic' settings ask for permissions, i wonder what happens when i want to start setting up networks etc.. :D

---

### Post by 3rdalbum on 2010-10-04
What concerns me is that you have been doing things in your home directory with 'sudo' which really should never be some because your home directory should be owned by you. You should also never launch Nautilus with sudo, only with gksudo.

Try changing the permissions of your home directory so that you are the owner of everything there, and the owner has read and write ability.

Don't use sudo unless you need to, and you should be fine.

---

### Post by Sgele™ on 2010-10-04
I already changed permissions on the home folder and all the folders and files in there.

For some reason it keeps giving the permission error. After trying all that i tried the nautilus thing. If it fails, so be it, i'll reinstall :) I'm not too worried about that. I just want full access over the files and folders. I have to get used to the fact that some of the simplest things like changing a default media player will be permitted by Ubuntu. Though i would like to be able to change it eventually ;)

---

### Post by nikefalcon on 2010-10-04
Looks like you may need to change permissions recursively; you could use [this]("http://www.ubuntupocketguide.com/index_main.html") for reference.(it may be slightly dated; nevertheless, the command line stuff remains the same)

Note: The Desktop folder that you see when you open nautilus as root(sudo or gksudo nautilus) belongs to the root user, not you. To access your home directory, go to the root of the filesystem(press the 'up' button in nautilus) and navigate to '/home' and then your home folder(it will ave your username on it).

---

### Post by emoguitarist06 on 2010-10-04
I know it's might be dumb to install a program for just changing your default player to VLC

However Ubuntu Tweak is awesome and I used that to make VLC my default... along the many other things it does for me :)

---

### Post by Sgele™ on 2010-10-05
> **nikefalcon said:**
> Looks like you may need to change permissions recursively; you could use [this]("http://www.ubuntupocketguide.com/index_main.html") for reference.(it may be slightly dated; nevertheless, the command line stuff remains the same)

Note: The Desktop folder that you see when you open nautilus as root(sudo or gksudo nautilus) belongs to the root user, not you. To access your home directory, go to the root of the filesystem(press the 'up' button in nautilus) and navigate to '/home' and then your home folder(it will ave your username on it).

I guess being able to write machine codes in five different languages has it's advantages. Your solution was spot on ;) Thanks man

---

