---
title: "I am new to this OS."
date: 2010-08-06
forum: New to Ubuntu
---

### Post by Ironheadb3 on 2010-08-06
Hello all, 

I am new to this platform, and I need to know how to do a restore or repair in case I mess up my computer.  I know that this might have been posted before, and for that I am sorry.  I have been poking around on the net, and I have not found what I need.  My computer is a Samsung N210 netbook so I am running ubuntu 10.04 UNR with 250 gb hdd and 1 gb of ram.  We all know that this has a 1.66 ghz processor that is slow as heck.  I moved to this platform, because I was hating how fat and slow Windows was on this machine.  I also have been looking at ubuntu for about two years now.  I like the look and feel of the OS, and how user friendly it is once you learn where and how to find the tools that you need.  I have found that the help program that comes with this OS is put together much better than Windows and MAC.  I do have to say that I like how much you can make this OS feel like an extension of one's self.  I know that you can do most of the same stuff on other platforms, but this one gives more options when it comes to how you as the user wants.  

Thank you for you help, and thanks for taking the time to read this.

---

### Post by inameiname on 2010-08-06
I recommend Remastersys. Once it's installed, it's as easy as getting your computer to your liking and then clicking about two buttons, and an image will be made, which is actually a Custom Live CD image, so you can put it onto either a CD, a DVD, USB or SD Card (using startup disk creator). Simple, simple.

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

---

### Post by Zzl1xndd on 2010-08-06
I just make a back up of my home folder. The Config files for most everything are stored here. If I mess up the OS I just reinstall and install all my apps and dump the contents of my Home folder back in.

---

### Post by Ironheadb3 on 2010-08-06
Hello all, 

Thank you for the great advice I have bookmarked the link that inaminame had suggested.  The best way that I was able to come up with before talking to you guys.  I had a spare hdd that I was able to install the whole working OS.  I also put all the information that I have on the hdd that is in the computer, but I only wanted to use that setup in case there were no other options.  Thank you two for the good advice.

---

### Post by TimEnid on 2010-08-06
> **tweakedenigma said:**
> I just make a back up of my home folder. The Config files for most everything are stored here. If I mess up the OS I just reinstall and install all my apps and dump the contents of my Home folder back in.

 is this by default? are all the apps setting stored there as well?  and with remastsys, where is the back up file stored?

---

### Post by Zzl1xndd on 2010-08-06
> **TimEnid said:**
> is this by default? are all the apps setting stored there as well?  and with remastsys, where is the back up file stored?

If you go to you home folder and press "CTRL + H" it should show you all your hidden files. There is one for almost every application I have installed.

---

### Post by ubunterooster on 2010-08-06
> **Ironheadb3 said:**
> Hello all, 

I am new to this platform, and I need to know how to do a restore or repair in case I mess up my computer. 
Just clone the drive with clonezilla. [http://clonezilla.org/](http://clonezilla.org/)
Yep, clone the *entire* drive and you can restore it to be exactly as it was.

Yes, you will need this if you (like myself) tinker constantly

---

### Post by inameiname on 2010-08-06
The Remastersys ISO image that is made can be found in the '/remastersys' folder, as depending on what setting you use, it copies everything else.

---

### Post by waynefoutz on 2010-08-06
> **Ironheadb3 said:**
> Hello all, 

I am new to this platform, and I need to know how to do a restore or repair in case I mess up my computer.  I know that this might have been posted before, and for that I am sorry.  I have been poking around on the net, and I have not found what I need.  My computer is a Samsung N210 netbook so I am running ubuntu 10.04 UNR with 250 gb hdd and 1 gb of ram.  We all know that this has a 1.66 ghz processor that is slow as heck.  I moved to this platform, because I was hating how fat and slow Windows was on this machine.  I also have been looking at ubuntu for about two years now.  I like the look and feel of the OS, and how user friendly it is once you learn where and how to find the tools that you need.  I have found that the help program that comes with this OS is put together much better than Windows and MAC.  I do have to say that I like how much you can make this OS feel like an extension of one's self.  I know that you can do most of the same stuff on other platforms, but this one gives more options when it comes to how you as the user wants.  

Thank you for you help, and thanks for taking the time to read this.


Just get an external drive, or DVDs,  back up your Documents, Pictures, Music, Videos folders, and any programs in the home directory that can't be found in the repositories. (they are usually hidden, so you'll have to click "show hidden files" to see them.) The beauty of Ubuntu, or just about any other Linux distro, is that you can install and have everything working in about 15 minutes.

---

### Post by corrytonapple on 2010-08-06
See this:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Ironheadb3 on 2010-08-07
> **ubunterooster said:**
> Just clone the drive with clonezilla. [http://clonezilla.org/](http://clonezilla.org/)
Yep, clone the *entire* drive and you can restore it to be exactly as it was.

Yes, you will need this if you (like myself) tinker constantly


Yes I love to tinker to figure out how the OS works.  The truly funny part is I had to to a fresh install the first night, because I was messiong around with wine.  I managed to install MS office and all was working, but when I went to take it off the computer I did not get ride of all of MS office.  So instead of running a system with a half installed program I decided to restart fresh.  I had a spare hdd lying around, and did a fresh install of ubuntu on that one as well.  Then I copied all that was in my home folder so that way I could have a complete OS on that hdd as well.  Now I thought that when it comes to cloning you could only do that if the hdd that you are cloning to is larger than the one you are using.  Please correct me if my train of thought is wrong.  

I really want to say thank you to all that have replied to my post.  Ya'll have some great tips on keeping all the important data where it needs to be.  Once again thank you all for the help.

---

### Post by ubunterooster on 2010-08-07
> **Ironheadb3 said:**
>  Now I thought that when it comes to cloning you could only do that if the hdd that you are cloning to is larger than the one you are using.  Please correct me if my train of thought is wrong.  You are correct that the destination partition must be equal or larger than the source one.  
> I really want to say thank you to all that have replied to my post.  Ya'll have some great tips on keeping all the important data where it needs to be.  Once again thank you all for the help.
You are welcome :D

---

### Post by oldfred on 2010-08-07
I do not back up system folders as I would plan on reinstalling anyway. But I have a lot of programs so I export a list of installed apps that allows me to automatically reinstall. I save list in /home so my normal backup of /home includes that list. I also try to remember any system wide changes I make. They usually are in /etc, but rather than back up all of /etc I just make copies of those config files into another folder in /home. Then my /home has almost everything I need to recover. I also have /data separate from system partitions so I have several versions of Ubuntu installed in 20-25GB system partitions - previous, current & future and maybe another for experiment. I can easily link in my /data so all have my same bookmarks an data files.

 dpkg --get-selections > ubuntu-files

More info:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

---

