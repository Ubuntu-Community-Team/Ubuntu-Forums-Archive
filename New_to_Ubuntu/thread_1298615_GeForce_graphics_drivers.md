---
title: "GeForce graphics drivers"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Vi3GameHkr on 2009-10-23
Hi,

I am very (like super extremely... well you get the point) new to Ubuntu and linux.. and anything non-windows for that matter.  After finally figuring out how to open Terminal (long hours of googling... No one writes tutorials on how to open the start menu in Windows right?) I was able to follow a tutorial to download the drivers for my graphics card from NVIDIA, the tutorial is located here: [http://forums.nvidia.com/index.php?showtopic=99513&pid=604009&st=0&](http://forums.nvidia.com/index.php?showtopic=99513&pid=604009&st=0&)

For your information, I'm using the 8.04 edition, I don't know if I need to upgrade to 9.04 or anything, I don't even understand any of the differences :/
I'm also using a GeForce 9800 GT graphics card.  I am really annoyed that I can't use anything besides 800X600 for my resolution and it cuts off half my screen.

Anyone that is able to help me in any way (like at least telling me how to do something besides open terminal at this point) will be my hero for the next 2 hours!


Now, I don't think I should create two threads at once so I'll just ask this question in here:  What's the difference between game programming on Windows and Ubuntu?  What makes it better on Ubuntu?  You don't have to explain the difference between DirectX and OpenGL, I'm just thinking OpenGL either way.

---

### Post by jbrown96 on 2009-10-23
8.04 is a long-term release, so it's supported for a longer period of time. That's ok for some people, but I really recommend running the current version. 9.04 is current, but 9.10 comes out in a week and is pretty much finished. The naming system is pretty obvious once you understand it. The first number is the year and second is the month (8.04: April 2008, 9.04: April 2009, 9.10: October 2009). There are two releases per year (april and october). 
I would recommend installing 9.10. I don't really trust upgrades, so I'd say do a clean install. Everything will work a lot better, and you won't have to go through all the pain of installing the Nvidia drivers (they are really complicated, especially for a newbie). 
Once you get 9.10 installed, here are a few things to do to get your system running well.
1) Enable the restricted repositories. Go to System->Admin-->Synaptic. Find the menu item for repositories (under settings?). You will want to enable all the repositories (universe, multiverse, etc.). It will warn you about updating your repositories, so click the reload button, then exit.
2) Install your Nvidia drivers. System-->admin-->hardware drivers. Use the 185 version. Then reboot. If you need to change some display settings like resolution use the nvidia utility. Bring up the application launcher Alt+F2 then ```
nvidia-settings
``` If you want to make a persistent change then put gksu before nvidia-settings. After you have made the changes, choose save configuration to xorg.conf. 
3) Install all the multimedia codecs. Open a terminal (apps-->accessories-->terminal) ```
sudo apt-get install ubuntu-restricted-extras vlc
```
4) If you are using the 64-bit version, replace the 32-bit flash that was just installed for the better 64-bit version. ```
sudo apt-get remove flashplugin-nonfree
``` Download the 64-bit version. [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") It will save to your desktop. Right click and extract the archive. "Cut" the libflashplayer.so file that is extracted. Places-->Home then Ctrl+H to show hidden files. Go into .mozilla and create a folder called plugins and past libflashplayer.so in it. 

That should get you setup nicely. 

About your second question: game programming is certainly not better on Ubuntu. Direct3D is a really good piece of technology, and openGL couldn't really replace it. That's not to say that opengl doesn't have its uses; it's just not that good for games (but there are a few that use it). If you are just comparing opengl performance on windows and ubuntu, then there really won't be much difference. I read an interview from an Nvidia developer about Linux support yesterday. Nvidia's driver will implement all the opengl pathways on your system, and the developer was saying they share 90+% of their code between windows and linux, so it's the same opengl code gets executed exactly the same; there won't be much difference.

---

### Post by Vermind on 2009-10-23
If you look at different devices on the market,
Direct3D is really a minority platform. Only Microsoft's platforms use it. The Xbox series and Windows PCs use Direct3D. Everything else uses OpenGL. Your phone uses OpenGL. Playstation 1-3 use OpenGL. Linux / Mac use OpenGL.
On the other hand, OpenGL has seen little change lately. OpenGL 3.2 only brought slight changes. It is a low level platform, meaning you usually need to work more to get the same level of effects with OpenGL vs Direct3D. I think Direct3D provides more easy ways to do fancy things. However, there are no differences in graphics quality; skilled developers can produce the same level of graphics with either API. 
See here for more:
[http://ubuntuforums.org/showthread.php?t=380216](http://ubuntuforums.org/showthread.php?t=380216)

---

### Post by jmszr on 2009-10-23
Vi3GameHkr,

Welcome aboard!

        I would suggest this sticky by ugm6hr: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . The links to Psychocats Ubuntu Guide:  [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)  and Free Ubuntu Pocket Guide by Keir Thomas:  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  are of particular note but the entire sticky is full of a lot of good information.

Also: [http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)  (Newbie 101) and: 

[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners) 

Media howto: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

To add the Ubuntu search engine to Firefox: [http://www.ubuntu-search.org/](http://www.ubuntu-search.org/)  

For any further Nvidia driver installation you may want to install EnvyNG: [http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html) . It is available in the Synaptic Package Manager - System > Administration > Synaptic Package Manager > Search:envyng and when it comes up select envy-gtk (envyng-core will install also)and install. It makes driver installation a lot easier.

---

### Post by Vi3GameHkr on 2009-10-23
jbrown96, 
Thanks for your opinions, I probably will get 9.10 as soon as it's out and see how it is.

I couldn't find anything under the Hardware Drivers window, it's completely blank and all of those repositories were already enabled.  When I went into the NVIDIA settings, I got a message which said: "You do  not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  So I did sudo nvidia-xconfig then rebooted and I still get that message.  (I had already installed the NVIDIA driver with the tutorial I mentioned in my first post, which is why I was able to access the NVIDIA settings I think)

Vermind, Thanks

jmszr, I'll make sure I check those out.  I had already seen the pocket guide and was planning to check that out, but for the moment I'm very annoyed at having to use 800X600 on a 16:9 20.5" monitor.


I do have another question at this point:  Where will I get by using Ubuntu?  I wanted to try it mainly because I heard I would do a little bit better with game programming and obviously that doesn't seem to be working out.  I don't really have the time to get used to a whole new operating system right now, I'd rather use the free time I've got to continue teaching myself C++ and also devote some extra time to school.  So, what can Ubuntu do for me that will make it worth my extra time?

---

### Post by jmszr on 2009-10-23
Vi3GameHkr,

Believe me , I know your aggravation - I recently got an Acer 21.5" 16:9 and getting the resolution was a PITA. This thread may be of help: [http://ubuntuforums.org/showthread.php?t=771810](http://ubuntuforums.org/showthread.php?t=771810) and this: [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) or this: [http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

The 9.10 rc is out now: [http://cdimage.ubuntu.com/releases/9.10/rc/](http://cdimage.ubuntu.com/releases/9.10/rc/) and it does automatically detect my monitor and resolution. 

Your last question is hard to answer. For me, it gave me freedom.

---

### Post by Vi3GameHkr on 2009-10-23
jmszr, 
Now I have something that is getting me somewhere!  Also in ugm6hr's sticky, I found a couple of useful threads down at the bottom that I didn't notice before which are helping me.  For reference, I'm looking at [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) right now.

When and if I get something working I'll be sure to let everyone know what got it to work.  Thanks a lot everyone!  I guess this was after all a matter of searching, if only I understood exactly what I was searching for
[[COLOR=#D40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=103883")

---

### Post by jmszr on 2009-10-23
Vi3GameHkr,
 
Good, I'm glad you're getting somewhere!

I just noticed this thread going on now over in General Help: [http://ubuntuforums.org/showthread.php?t=1298827](http://ubuntuforums.org/showthread.php?t=1298827) .
You may want to check it out.

---

### Post by oldfred on 2009-10-23
I have done upgrades since 6.10 (I think) and never done a clean install until I decided to test 9.04 64 bit since my system was 64 bit capable.
With my updates I had issues just about every upgrade and almost all were related to video. My last upgrade to 9.04 32 bitrequired a lot of work and I found on nvidia site that you had to remove all the old nvida files to get the new ones to work. In removing nvidia I managed to remove the entire desktop and had to reinstall that from the command line.

Long story short the clean install of the 9.04 64 bit worked immediately. I also installed 9.10 alpha and while there were various issues the video just worked. If you can wait until 9.10 is official I would recommend a clean install. If you have room save your old partition. Either way backup /home and any other data you think is important.

---

### Post by Vi3GameHkr on 2009-10-23
Wait where do you get 64-bit?  I didn't know such thing existed but I've noticed a lot of things have a 32-bit or 64-bit option (like certain downloads and tutorials) so I thought they were referring to another distro.  A friend gave me a  CD a long time ago and I found where to order those CDs, every once in a while I order a CD, install it and then find a problem I can't figure out how to fix and just give up until I get another recommendation to use Ubuntu.

Well all the more reason to get 9.10 I guess!

---

### Post by jmszr on 2009-10-23
Vi3GameHkr,

Ubuntu doesn't ship 64-bit anymore - you need to download (I advise using a torrent) it and burn the .iso image to a CD. 9.04: [http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/) and 9.10 rc: [http://cdimage.ubuntu.com/releases/9.10/rc/](http://cdimage.ubuntu.com/releases/9.10/rc/) . These are helpful: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) .

When (if) you run into a problem someone on these forums has probably already run into it and can help you through it - just ask.

---

### Post by Vi3GameHkr on 2009-10-23
On other forums, it is typical to get flamed for asking a question that could have easily been answered by using the almighty search function and asking the also almighty Google, and I will always be sure to use these first before also asking other people to spend their time answering my questions.

Anyways, I read in the pocket guide by Keir Thomas that 64-bit causes compatibility issues and other things that just make it not worth using unless you have at least 4GB of RAM (I currently have only 3GB)  Is anyone able to confirm this and/or explain why?  I have a 9.04 CD, and I ran into some partitioning issues (I had only partitioned 4GB space for Ubuntu and that went extremely quickly.  My partition utility BootIt NG doesn't support linux file systems so I didn't know how to repartition and give some more space to Ubuntu) so I decided I now have enough reasons to install 9.04 that I'm just going to do it now.  I'll make sure I download 9.10 in 6 days.

Anyways, I set a little goal for myself this afternoon:  If I can successfully watch Iron Man with my surround sound I'll have done a good days worth of work here.

So I do like asking questions, and I have more:  How is gaming on Ubuntu?  I've heard of emulating games via a windows emulator (I think it was called Wine) but is this anything compared to running them directly via Windows?  Again, I'm reading more and more stuff, I found a Beginners guide to switching from Windows to Ubuntu and I'm currently checking that out.


[B][EDIT]
[/B]So I finished installing 9.04 and I am now using 1600X900 resolution no problem!!!  It's time to prepare this baby to watch some movies now!

PROBLEM SOLVED - Solution: Install the latest Ubuntu version with all the updates, it supports all the latest hardware.

---

### Post by jmszr on 2009-10-23
Vi3GameHkr,

It is always good to try to answer one's own questions - but sometimes one doesn't even know what the right question is. I do recommend that you add the Ubuntu Google search engine to Firefox: [http://www.ubuntu-search.org/](http://www.ubuntu-search.org/) , the Forums search function can be a little tricky and straight up Google can deliver a lot of extraneous results.

I run 8.04 64-bit (2GB RAM initially - 4GB now) and there don't seem to be any compatibility issues any longer. However, if you are not planning on increasing your RAM then there is not much point in using 64-bit.

You can run the GParted partition manager off the Live CD: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition) .

I'm not a gamer but this may be of help: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

Good Luck with Iron Man!

---

### Post by Vi3GameHkr on 2009-10-23
I guess it's time to start venturing outside of the Absolute Beginner Talk!  You just keep on helping a ton!

Thanks a lot!!  I guess I've got some tutorials to get started in!  Ubuntu has got some real potential for me I can definitely see, after reading some of the stuff I've been reading this morning.  I just have to start using it!

---

