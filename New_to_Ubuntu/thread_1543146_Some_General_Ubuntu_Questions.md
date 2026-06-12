---
title: "Some General Ubuntu Questions?"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by dbaybay on 2010-07-31
Hi there,

I'm really enjoying Ubuntu over Windows and trying out all the applications, but they don't seem to have that ""professional"" touch, like Windows/Mac apps do. So I'm having a very hard time getting around them. I have three questions as of now -

All my music is on my hard drive. I have one hard drive with Win7/Ubuntu10 dual booted and my music runs great in Windows 7, finds it no problem etc... but when I try to use Rythmbox and it will load all the songs, but it does EVERYTIME. Is there an Ubuntu app that I use to listen to my music with ease? All I want to do is have it read from my iTunes folder in Windows...

Second question is what are the best apps in your opinion? Things I should try out? I'm kinda lost right now trying to find the cream of the crop so to say, for music, movies, torrent clients, etc...

Finally, for some reason when I turn on my computer and get to the GRUB menu. It keeps adding more Ubuntu links. Like before it just said Ubuntu, Ubuntu Recovery, Windows 7 - now there are 3-4 Ubuntu and Ubuntu Recovery links and the just keep growing! Any thoughts?

Thanks so much for help in advance :D

---

### Post by dbaybay on 2010-07-31
Bump!!

---

### Post by Elmer Fudd on 2010-07-31
RE the increasing number of Grub entries.
Every time update adds a new kernel update, Grub will add it to the list.

There are a number of ways to remove old versions or just the entries from Grub.

-command line
-synaptic package manager
-Ubuntu Tweak is probably the easiest for noobs.
(install from synaptic ubuntu-tweak
or the command line "sudo apt-get install ubuntu-tweak")
It will install in Applications/System Tools menu.
Start it and select Package Cleaner/ Clean Kernels
It will show a list of removable kernels.
Click unlock and put in your password.


Do keep the two most recent kernels that work.

---

### Post by phillw on 2010-07-31
Hi,

watching folders, which is what I guess you are asking RythmBox to do if it is looking at your iTunes Folder on windows means that it has to see if you've added / deleted / edited any songs since the last time it ran. If it did not do that each time, it would not know any alterations :-)

As for "which is best", that depends entirely on which you prefer. One of the hardest things for people from Windows environments to get used to is 
1) It's all free
2) There's so many choices

Use the USC (Ubuntu Software Center), go look at catagories, download them, try them. If you don't like them, tell it to get rid of them. Go and explore :D

The extra entries you are seeing in the start up screen are when the main part of the system is updated (called the Kernel). 

Make a note of your exisiting kernel
```
uname -r
``` You need to keep that one !! It is also advised to keep the most recent one behind it, e.g. If you are on 
2.6.32-24-generic then you would also keep 2.6.32-23-generic.

You can remove the old ones using Synaptic package manager [http://www.pendrivelinux.com/how-to-remove-old-kernel-images/](http://www.pendrivelinux.com/how-to-remove-old-kernel-images/) which is safer for a new comer, or you can do it from the Terminal. Either way, do **not** delete the one you are currently using !!!

Via the terminal:
Assuming, as above, you have 2.6.32-24 as your current version.
```

cd /boot
ls
```
This will list 6 types of files, the important part is the 2.6.32-24 part of the ones you want to keep and you also want to keep the ones with 2.6.32-23 as your most recent backup. 
Assuming that you also have 2.6.32-22, 2.6.32-21 (and may be 2.6.32-20) (Hopefully you can see how the numbering sequence works)
```

sudo rm *2.6.32-22*
sudo rm *2.6.32-21*

``` If you have the 2.6.32-20, then use the sudo rm to get rid of it as well.
Then issue```
sudo update-grub
``` That command will rebuild the screen that you see when you start your computer up, with the older kernels gone, it will not include them.

Regards,

Phill.

---

### Post by natex on 2010-07-31
>>Hi there,
Hi. Welcome.

>>All my music is on my hard drive. I have one hard drive with  Win7/Ubuntu10 dual >>booted and my music runs great in Windows 7, finds it  no problem etc... but when I >>try to use Rythmbox and it will load all  the songs, but it does EVERYTIME. Is there an >>Ubuntu app that I use to  listen to my music with ease? All I want to do is have it read >>from my  iTunes folder in Windows...

Rhythmbox doesn't load all songs at startup. It reads the directory you point it to. Isn't this what you want? (e.g. "read from my itunes folder"? If you'd like a more classical music player, try the (default) music player Totem. You can browse using your filemanager and double click on a media file.

>>Second question is what are the best apps in your opinion? Things I  should try out? >>I'm kinda lost right now trying to find the cream of the  crop so to say, for music, >>movies, torrent clients, etc...

The great thing about Free software is that you are welcome to try them all and decide which you like - no strings attached. Amarok, Rythmbox, and Banshee are great, so is MPD. But you need to be bit less general here. What do you want to do? Make music? Download free legal music? Play your Last.fm stations? Serve your music collection to your mobile phone? Same thing with movies. There are thousands of applications and each one has their strengths and weaknesses. Tell us what you want to do?

---

### Post by dbaybay on 2010-07-31
Basically since my music is on the same hard drive as Win7 and Ubuntu, I want it to be able to "remember" it after it's scanned the folder once, and then add new songs as I place them there. I'm afraid I'm going to have to have two music folders, one for Linux and one for Windows, and that would take up over 100 gb on my hard drive, when it should be only 50 GB. Idk its hard to explain, you know?

And the GRUB thing is totally out of my league. Hopefully they'll come out with something that does it for you, because all those methods just seem so confusing to me.

---

### Post by phillw on 2010-08-01
Hi, the problem is that Rythmbox (or any music player) has no idea of alterations you make to your music collection when in windows. That's why it scans the folder on startup. There is no need to duplicate you music folder.

If you follow [https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit) to install pastebinit then issue the commands ```
cd /boot
ls | pastebininit
``` Post the link you get back onto here and I'll be happy to write you a custom set of instructions.

I'll explain what is happening with each command so you can learn how it works.

Regards,

Phill.

---

