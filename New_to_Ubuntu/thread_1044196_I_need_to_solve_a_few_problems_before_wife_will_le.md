---
title: "I need to solve a few problems before wife will let me oust windows"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by jotremba on 2009-01-19
I installed Ubuntu on Friday and I must say it is pretty awsome - I just have a few issues that need I need to figure out how to get to work before the wife will let me oust windows.

  1) For some reason Ubuntu runs pretty slow on my 1.2 ghz celeron w/512mgs ram. I know its not much but there are folks on the forums that run it on less than that. I just have the standard package you get with the original download and I installed it over the internet.

  2) Virtualbox ose will not run WindowsXP I think this may have to do with my resource hog issues that I am having with the first problem but I don't know for sure.  But I am really going to need this program to work if I want to make the switch. (The main reason I need this to work is for my Sony MP3 player that basically only works with Sonicstage and for some dumb reason WINE will not work for the sonicstage installation - so an alternative for sonicstage that works with my mp3 player would be just as good.)

  3) My monitor always has sucked and even though I have the brightness just juiced on the monitor it still appears dark. I have installed ddccontrol and it didn't work for me. Its not unbearable - just annoying if there are any other ideas for that - it would be great.

    Well I guess thats about it I really like the os but these issues need to be fixed so I can justify giving the boot to windows without giving the boot to some of the stuff that I need windows for. I am thinking about doing a memory upgrade - but is Ubuntu really more of a resource hog than windows XP?????

---

### Post by rolnics on 2009-01-19
> **jotremba said:**
> 
  1) For some reason Ubuntu runs pretty slow on my 1.2 ghz celeron w/512mgs ram. 


You should be ok, but it might be worth looking at Xubuntu it's a bit lighter on the resources. Although if you go into Synaptic Prog Manager (System -> Admin -> Synaptic) there is an option that gives you a minimal install, but I can't remember how to get to it (@work, no linux machines here!)

> **jotremba said:**
> 
  2) The main reason I need this to work is for my Sony MP3 player that basically only works with Sonicstage and for some dumb reason WINE will not work for the sonicstage installation - so an alternative for sonicstage that works with my mp3 player would be just as good.)


We have a sony MP3 at home, I was having the same issue, but I did come across a solution that didn't need windows, but as mentioned already I'm at work, so for the life of me can't remember the program name. So that will solve that problem, by not needing to install windows and sonicstage.

As for you monitor issue I don't have any suggestions and your memory upgrade, well it might be worth it, but it depends on what you want to do with the machine.

---

### Post by yeats on 2009-01-19
> I installed Ubuntu on Friday and I must say it is pretty awsome - I just have a few issues that need I need to figure out how to get to work before the wife will let me oust windows.

Congratulations!  I had the same issue and my wife now has a dual-boot Ubuntu/Vista computer.  She, too, now prefers Linux, so there's hope!

> 
1) For some reason Ubuntu runs pretty slow on my 1.2 ghz celeron w/512mgs ram. I know its not much but there are folks on the forums that run it on less than that. I just have the standard package you get with the original download and I installed it over the internet.

It "runs" on that and less, but if you want to do a lot with it, you might consider xubuntu or another graphical environment that consumes less resources than regular ubuntu.  You can try xubuntu out by typing 

```
sudo apt-get install xubuntu-desktop
```

at the command line - but be aware that this will install ALL xubuntu programs and they will appear (by default) in your Ubuntu menus (you can edit them away).  I found this out the hard way when trying out KDE for the first time :-).  Also - it's easy to download, but more difficult to remove, but you could ask about that in a separate thread if needed.


> 2) Virtualbox ose will not run WindowsXP I think this may have to do with my resource hog issues that I am having with the first problem but I don't know for sure. But I am really going to need this program to work if I want to make the switch. 

Virtualbox (OSE or otherwise) will almost certainly need more RAM than you have :-(.  It allocates RAM to each virtual machine based on what you specify, but you have to have it available to begin with (which is almost certainly why it wasn't working on XP).

> (The main reason I need this to work is for my Sony MP3 player that basically only works with Sonicstage and for some dumb reason WINE will not work for the sonicstage installation - so an alternative for sonicstage that works with my mp3 player would be just as good.)


Try all the major Linux music programs - Rhythmbox, VLC, Amarok - and find one you like.  I'd be very surprised if you don't find that one (if not all) work with your player.

I don't have any specific monitor suggestions - I bought a new one for about $200 that I love.  But if you're not in that position . . . .

You might consider upping your RAM - try [newegg.com]("http://www.newegg.com/").

Good luck!

---

### Post by Sealbhach on 2009-01-19
You defintely need at least 1Gb of RAM to run virtualisation. 

You need RAM to run the guest OS but you also need RAM to run the host OS.

You could dual boot Windows and Ubuntu, there's no shame in that.:)


.

---

### Post by yeats on 2009-01-19
> 
You could dual boot Windows and Ubuntu, there's no shame in that

I couldn't agree more. :-)

---

### Post by jotremba on 2009-01-19
> **rolnics said:**
> 

We have a sony MP3 at home, I was having the same issue, but I did come across a solution that didn't need windows, but as mentioned already I'm at work, so for the life of me can't remember the program name. So that will solve that problem, by not needing to install windows and sonicstage.

That is awsome - if you could let me know what that program is I would really appreciate it man.

Thanks

---

### Post by albinootje on 2009-01-19
> **jotremba said:**
>  1) For some reason Ubuntu runs pretty slow on my 1.2 ghz celeron w/512mgs ram.

Ubuntu is kind of sluggish on older machines compared to e.g. Xubuntu or Crunchbang Linux.
[http://www.xubuntu.org/](http://www.xubuntu.org/)
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Speeding up OpenOffice :
[http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php](http://lifehacker.com/software/optimization/speed-up-openoffice-270775.php)

This can help :
[http://theitreport.com/entries/linux/ubuntu-performance-tip---preload](http://theitreport.com/entries/linux/ubuntu-performance-tip---preload)

See also here :
[http://ubuntuforums.org/showthread.php?t=1011944](http://ubuntuforums.org/showthread.php?t=1011944)

---

### Post by rolnics on 2009-01-19
What model MP3 player do you have? I've done some searching and I'm sure *[this is what I used]("http://www.lynchconsulting.com.au/blog/index.cfm/2006/9/26/Sony-NWE005F-working-in-Linux--HOWTO")* for my MP3, but it depends on the model I think.

---

### Post by stefangr1 on 2009-01-19
> **jotremba said:**
> 
  1) For some reason Ubuntu runs pretty slow on my 1.2 ghz celeron w/512mgs ram. I know its not much but there are folks on the forums that run it on less than that. I just have the standard package you get with the original download and I installed it over the internet.

Did you specify enough swap? You can check this by running the command "free". I also run the full Ubuntu on old systems PIII-1000Mhz (slow but usable) and PIV-1600Mhz (very sufficient) both with 256MB ram, but I know of some people that experienced very low performance and later on appeared to have no swap.

I don't know about others, but in my experience Xubuntu doesn't make such a big difference over Ubuntu if you have sufficient RAM. As your system meets the requirements, I wouldn't worry about installing Xubuntu.

> 
  2) Virtualbox ose will not run WindowsXP I think this may have to do with my resource hog issues that I am having with the first problem but I don't know for sure.  But I am really going to need this program to work if I want to make the switch. (The main reason I need this to work is for my Sony MP3 player that basically only works with Sonicstage and for some dumb reason WINE will not work for the sonicstage installation - so an alternative for sonicstage that works with my mp3 player would be just as good.)


This is strange. It is agreed with the other posters that your system is not good for running vm's, but that doesn't mean it can't work. I suppose with 256mb for the os, and 256mb for the vm it should be possible (though you should expect performance issues). If it just doesn't work something else went wrong.

> 
  3) My monitor always has sucked and even though I have the brightness just juiced on the monitor it still appears dark. I have installed ddccontrol and it didn't work for me. Its not unbearable - just annoying if there are any other ideas for that - it would be great.


Correct me if I'm wrong, but I think that on regular desktop pc's Ubuntu does not effect the brightness of the monitor. 
The default theme of Ubuntu uses a lot of dark colors, maybe you can take a custom theme and background?

---

### Post by yeats on 2009-01-19
> This is strange. It is agreed with the other posters that your system is not good for running vm's, but that doesn't mean it can't work. I suppose with 256mb for the os, and 256mb for the vm it should be possible (though you should expect performance issues). If it just doesn't work something else went wrong.

I wouldn't do this if my system was already at a crawl . . . but maybe that's just me :-)

---

### Post by stefangr1 on 2009-01-19
> **chrissharp123 said:**
> I wouldn't do this if my system was already at a crawl . . . but maybe that's just me :-)

Dual booting is by far the better option here, and I don't think it's recommended to install vm's on a system with only 512mb.

However, back when I started running vmware I didn't have a fast dual core yet, and only 1GB RAM, so I always dedicated 256mb ram for a vm with windows xp. That runned pretty well. Especially when you aren't multitasking (e.g. not doing anything else on the host besides running the virtual machine) windows should run only a little slower than on native hardware (because of the regular penalty for running a VM), but it definitely shouldn't cause any trouble. Windows xp is slow anyway on such a system, even when it's running native. The advantage of a vm is that you can install it without SP1-3 and virusscanners etc. since you can use the internet from the host.

There are also other applications that need a lot of ram (photo editing with gimp), but that doesn't really mean that it just doesn't work on older hardware.

---

### Post by Big_astur on 2009-01-19
For the Sony player i use "jsymphonic" for my father's player:

[http://ubuntuforums.org/showthread.php?t=716477&highlight=jsymphonic](http://ubuntuforums.org/showthread.php?t=716477&highlight=jsymphonic)

And the last post in that topic is from the author who just created a new topic to talk about his application here:
[http://ubuntuforums.org/showthread.php?p=6446800#post6446800](http://ubuntuforums.org/showthread.php?p=6446800#post6446800)

---

