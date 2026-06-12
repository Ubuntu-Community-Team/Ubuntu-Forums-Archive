---
title: "Newb cant locate hd in mnt folder? &amp; dosent understand how to use GmailFS"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by ZombieInTheSky on 2009-05-29
Hey guys I hope I can get some help with this stuff.

I am still learning as I have maybe a total of maybe 100 hours flying time with ubuntu LOL. 

So to first explain my situation I have two issues. 

The first one is about sharing media with my xbox. I was given a link to a post that has all the instructions on how to do this

([http://ubuntuforums.org/showthread.php?t=848144](http://ubuntuforums.org/showthread.php?t=848144))

but I am stuck at the configuration part, it wants to know the folder I am sharing my files from. The directory I wanted to share from is my Videos folder in my home user directory. So I used this as the path (/home/user/videos) but this is incorrect. I tried to find my HD in the mnt folder but Ubuntu must mount things differently that what I know of. Sorry for the long explanation on this one I bet someone can help me pretty fast on this very Newbish question and I thank you in advance.

Now for the second issue I am having. 

I would like to use GmailFS, I have used synaptic to install the GmailFS package and a FUSE package. (I don't even know if it is the correct package either) Currently all the information I have found on this subject is from this wiki here: 

([https://wiki.edubuntu.org/GmailFS](https://wiki.edubuntu.org/GmailFS))

Also the developers website which doesn't have much info at all.

Beyond that I don't know what to do I just found the wiki so I have not used it. 

To anyone that knows if it is correct, if at all possible could you either reply with what to do, or possibly edit the wiki for me and others as it is unfinished. Although it is for edubuntu it should be the same right? Also it only basically shows how to install the app. So it might at least help me select the correct packages to install but their is not much beyond that, just a little on setup is all.

I have had a VERY hard time finding information on GmailFS maybe that is because there is a better or easier free way to easily store data online. Preferably one with a large storage capacity like Gmail and its 7+ GB growing everyday. If so I am unaware !please! Educate me. 

Once I have these two things done I will have finally completely have untangled myself from the Micro$oft'$ web of death on my notebook thanks to ubuntu 9.04 the first Ubuntu Distro that Easily recolonizes all my hardware without me having to do it manually (which would required more knowledge on ubuntu an linux in general than I do) I have O'Reilly's Linux in a Nutshell but I haven't cracked open that thousand page book yet I believe its the second edition so its out of date anyway and I'm not exactly a book learner LOL (maybe thats why i am so dumb in general LOL).


In all I want to say sorry for the long post and I want to thank anyone that even reads this and I really hope someone can help me out on these. I know someone will you guys here never let me down. :D

---

### Post by doas777 on 2009-05-29
well I can;t help with most of it, but look for your hdd in /media rather than /mnt

---

### Post by drs305 on 2009-05-29
On the first point, did you literally use /home/*[COLOR="DarkRed"]user[/COLOR]*/videos or /home/*[COLOR="DarkRed"]your.real.username[/COLOR]*/videos ? Also remember ubuntu is case dependent ("videos" does not equal "Videos").

Also, you might look in /media instead of /mnt. You can see where things are currently mounted with the "mount" command. Open a terminal (System, Applications, Terminal or ALT-F2, tick "run in terminal") and type:
```

mount

```

---

### Post by ZombieInTheSky on 2009-05-30
no I used my real user name and i do know it is case sensitive that and the fact that spaces are required for cd commands were 2 of the first things I found out LOL.


```
So with "/home/my user name/Videos" (all case sensitive) and it should work? 
Or should I have it /media/hda01/home/my.user.name/Videos
```

I am currently on my work pc so I cannot find my HDD with the "mount" command but i will when i get home I bet it will have to be done that way with the directory starting with my hard drive? I am slowly but surely getting their with your help guys thanks!

Sorry for taking so long to reply but that you guys for the information.

---

### Post by drs305 on 2009-05-30
If Videos is a subfolder under your HOME, the address would normally be: 
/home/your_user_name/Videos

Some users mount $HOME on a partition separate from the main system partition, but it is still mounted and located at /home. Each individual user has a subfolders of /home, so your HOME folder would be /home/yourusername. Any folders you create under your $HOME would be located as /home/yourusername/newfolder.

/home/yourusername can also be designated as $HOME, so in this case "Videos" locatation would be $HOME/Videos.

As far as the "hda01" reference, ubuntu now designates all normal drives, sata or ide, as "sd"XX. There is no longer a distinction between hdXX and sdXX. And it uses simple numerics, 1,2,3 etc with no 0 necessary as a place holder (sda1, sda13, etc).

---

### Post by ZombieInTheSky on 2009-05-30
Thank you for the clarification, I must have done something else wrong or like i was told above, I may have not have it in the correct case! I wish i could fix it now but i will have to wait until later.

Also I will try the $HOME as its much easier thank you for clearing up some things and getting me up to date.

Thank you all
I believe I at least my file sharing issue is taken care of so THANK YOU!

---

