---
title: "new to ubuntu: problem and question"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by super1bat on 2011-05-03
Hi everyone

I'm new to ubuntu .
I just downloaded ubuntu 11.04 64bit because I have 4gb ram.

Question here: Which one is better 32bit or 64bit in ubuntu ?

I want to install ubuntu alongside my windows 7 sp1 64bit. So I burned ubuntu 11.04 64bit iso in dvd the size of the dvd is 4gb.
The problem when I install ubuntu on partition (14.5gb) it's all free space, I'm getting error:

no root file system is defined please correct this from the partitioning menu

I got 2 hard drive and 8 partition, every hard drive 4 partition.
first hard drive is 160gb.
second hard drive is 500gb.

I'm trying to install it on one of the partition from the first hard drive.

What is the problem ?

So I said I'll install ubuntu through the downloaded iso.
I'm getting 2 option

1-demo and full installaion
2-install inside windows

The first option is what I did so I didn't choose it.
So I installed ubuntu with the second option on the 14.5gb partition with the default install options.

Question here: Is it the same as the first option, I mean is everything installed or there is missing features or files or software or anything ?

After I installed ubuntu I updated it and the driver app that come with ubuntu downloaded everything ( I think :D ) including nvidia driver.

I gone to youtube it needs adobe flash to play the videos so I press on the adobe flash link, There is 32bit and 64bit I didn't know what to download, I mean I have win7 64bit and there is one for ie and the second one for other browser.
Anyway I tried the both 32bit and 64bit I download it, After that I extract the file I open it a window show up I didn't know what to do, So I search in the internet on how to install adobe flash.
on of the site says:
Go to mozilla folder and then plugin folder if you didn't find plugin folder create folder and rename it to plugin.

There is problem here too

I don't know where is mozilla folder so I used the search and I found more than one mozilla folder but one of it there is plugin folder so I said sure it is the folder that i 'm looking for.
The problem when I copy the adobe flash file and try to paste, the paste option is not activated, I tried to drag it a error shows up about permission denied. I change my account type from custom to administrator then i restart and still the same problem.
what I can do about how to install adobe flash and don't get error about permission denied ?

Question here: Whenever I do anything it ask for password, It's so annoying, How I can disable it ?

There is problem here too about games:

I tried to download one of the small games ( size about 4mb) from the software center, After I installed it I tried to play it but it was very very slow I don't know why, The driver app that come with ubuntu already installed nvidia driver and everything else ( I think again XD )


My system
nvidia gtx 275
4gb ram
intel core 2 quad Q9550

Thank you alot.
And sorry for my bad english :D

---

### Post by krishnandu.sarkar on 2011-05-03
> **super1bat said:**
> Hi everyone

I'm new to ubuntu .
I just downloaded ubuntu 11.04 64bit because I have 4gb ram.

Question here: Which one is better 32bit or 64bit in ubuntu ?


Choose what you like, Linux is not like Windows and Linux Distros comes with PAE kernels : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

In simple words, it allows you to utilize more than 4GB RAM even with 32bit versions.

Sweet deal right?? 

> 
I want to install ubuntu alongside my windows 7 sp1 64bit. So I burned ubuntu 11.04 64bit iso in dvd the size of the dvd is 4gb.
The problem when I install ubuntu on partition (14.5gb) it's all free space, I'm getting error:

no root file system is defined please correct this from the partitioning menu
Again, installation method is not like Windows.

Unlike Windows, Linux needs at least two partitions..
1. / (root)
2. Swap (Somewhat like virtual memory in Windows)

But recommendations are at least 3 partitions...
1. / (root)
2. /home (Somewhat like C:/My Documents in Windows)
3. Swap (Somewhat like virtual memory in Windows)

So Linux won't get installed in single partition like Windows.

> 
I got 2 hard drive and 8 partition, every hard drive 4 partition.
first hard drive is 160gb.
second hard drive is 500gb.

I'm trying to install it on one of the partition from the first hard drive.

What is the problem ?
Read above, answered it there 

> 
So I said I'll install ubuntu through the downloaded iso.
I'm getting 2 option

1-demo and full installaion
2-install inside windows

The first option is what I did so I didn't choose it.
So I installed ubuntu with the second option on the 14.5gb partition with the default install options.

Question here: Is it the same as the first option, I mean is everything installed or there is missing features or files or software or anything ?
1st one is normal installation method.
2nd one is actually Wubi, which helps first timers to try out Linux by installing it from Windows(Or specifically within Windows).

This has been added as most first timers didn't know the partitioning system that I said above like you. So this is generally for them.

But I personally strongly recommend to go for Normal Installation method. Because Wubi installation faces many problems later. And if the person starts liking Ubuntu and plans to use on long term basis, gets a headache because of Wubi.

BTW That's my personal view ok..??

Don't worry, you didn't perform anything wrong. So if you start liking Ubuntu and wants to use in long term later on, ask here, members will help you out. Not a big deal though :)

> 
After I installed ubuntu I updated it and the driver app that come with ubuntu downloaded everything ( I think :D ) including nvidia driver.

I gone to youtube it needs adobe flash to play the videos so I press on the adobe flash link, There is 32bit and 64bit I didn't know what to download, I mean I have win7 64bit and there is one for ie and the second one for other browser.
Anyway I tried the both 32bit and 64bit I download it, After that I extract the file I open it a window show up I didn't know what to do, So I search in the internet on how to install adobe flash.
on of the site says:
Go to mozilla folder and then plugin folder if you didn't find plugin folder create folder and rename it to plugin.

There is problem here too

I don't know where is mozilla folder so I used the search and I found more than one mozilla folder but one of it there is plugin folder so I said sure it is the folder that i 'm looking for.
The problem when I copy the adobe flash file and try to paste, the paste option is not activated, I tried to drag it a error shows up about permission denied. I change my account type from custom to administrator then i restart and still the same problem.
what I can do about how to install adobe flash and don't get error about permission denied ?

Question here: Whenever I do anything it ask for password, It's so annoying, How I can disable it ?
First things first...!!

As you are on 64bit version of Ubuntu, install 64bit version of Adobe Flash, directly from their site. It'll get installed automatically.

BTW here's an automation too like NVIDIA Drivers, hope you'll like it..!!

Just go to terminal and type sudo apt-get install ubuntu-restricted-extras. It'll ask for password, provide it, and flash player, JRE, Audio and Video Codecs everything that's needed in everyday life general use, will automatically gets installed. 

Awesome right?? 

Now lets answer your second query, Linux is not insecure like Windows, and it won't if you want it to be or force it to be :)

So for every administrative tasks Linux asks for root password, so you have to provide it.

There's a way to disable it, but I'm sorry I won't tell you that, because then you'll not understand the features of Linux and may do mistakes or harm your system. So go on with as it is. :)

So it asks for password because installing something is an administrative task.

**NOTE : Don't get confuse with / (root), which is a partition, main partition. And root is also a user, which is Admin.**


> 
There is problem here too about games:

I tried to download one of the small games ( size about 4mb) from the software center, After I installed it I tried to play it but it was very very slow I don't know why, The driver app that come with ubuntu already installed nvidia driver and everything else ( I think again XD )
I guess that's a driver issue, so check your driver version you are using from "Additional Drivers"

> 
My system
nvidia gtx 275
4gb ram
intel core 2 quad Q9550

Thank you alot.
And sorry for my bad english :DNot a problem.

Finally WELCOME TO THE LINUX AND UBUNTU CLUB :)

We hope you enjoy your stay here :D

---

### Post by super1bat on 2011-05-03
> **krishnandu.sarkar said:**
> Choose what you like, Linux is not like Windows and Linux Distros comes with PAE kernels : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

In simple words, it allows you to utilize more than 4GB RAM even with 32bit versions.

Sweet deal right??

NICE

> Again, installation method is not like Windows.

Unlike Windows, Linux needs at least two partitions..
1. / (root)
2. Swap (Somewhat like virtual memory in Windows)

But recommendations are at least 3 partitions...
1. / (root)
2. /home (Somewhat like C:/My Documents in Windows)
3. Swap (Somewhat like virtual memory in Windows)

So Linux won't get installed in single partition like Windows.

Read above, answered it there 

1st one is normal installation method.
2nd one is actually Wubi, which helps first timers to try out Linux by installing it from Windows(Or specifically within Windows).

This has been added as most first timers didn't know the partitioning system that I said above like you. So this is generally for them.

But I personally strongly recommend to go for Normal Installation method. Because Wubi installation faces many problems later. And if the person starts liking Ubuntu and plans to use on long term basis, gets a headache because of Wubi.

BTW That's my personal view ok..??

Don't worry, you didn't perform anything wrong. So if you start liking Ubuntu and wants to use in long term later on, ask here, members will help you out. Not a big deal though :)

I don't have any free space in any partition so I'll try to use the  installed ubuntu until I buy new hard drive :D so I can get used to it.

> First things first...!!

As you are on 64bit version of Ubuntu, install 64bit version of Adobe Flash, directly from their site. It'll get installed automatically.

BTW here's an automation too like NVIDIA Drivers, hope you'll like it..!!

Just go to terminal and type sudo apt-get install ubuntu-restricted-extras. It'll ask for password, provide it, and flash player, JRE, Audio and Video Codecs everything that's needed in everyday life general use, will automatically gets installed. 

Awesome right?? 

Now lets answer your second query, Linux is not insecure like Windows, and it won't if you want it to be or force it to be :)

So for every administrative tasks Linux asks for root password, so you have to provide it.

There's a way to disable it, but I'm sorry I won't tell you that, because then you'll not understand the features of Linux and may do mistakes or harm your system. So go on with as it is. :)

So it asks for password because installing something is an administrative task.

**NOTE : Don't get confuse with / (root), which is a partition, main partition. And root is also a user, which is Admin.**

I'll do that.

about password I can look for it in the internet LoL ( Just kidding ) I'll do as you said.
But it's really annoying, I even disabled UAC in win7 :D.


> I guess that's a driver issue, so check your driver version you are using from "Additional Drivers"

I'll check it.

> Not a problem.

Finally WELCOME TO THE LINUX AND UBUNTU CLUB :)

We hope you enjoy your stay here :D

Thank you so much :smile:
I'm sure I'll enjoy.

---

### Post by idoitprone on 2011-05-03
I will advise against PAE kernel, since there might be a performance hit when try to addressing more than 4 gb. Try and get 64 bit since you already have 4 gb of ram. Remember PAE is just a hack to get around hardware limitations.

btw UAC is just like linux permission. You will only need to enter your pass when you try to do system task

---

### Post by kaldor on 2011-05-03
Just so you know, on these forums people usually ask you to type commands. This is because it is MUCH easier on both parties than telling somehow what to do with mouseclicks. For all the software installed via commands, you can get it normally via Ubuntu Software Centre.

---

### Post by super1bat on 2011-05-03
> **idoitprone said:**
> I will advise against PAE kernel, since there might be a performance hit when try to addressing more than 4 gb. Try and get 64 bit since you already have 4 gb of ram. Remember PAE is just a hack to get around hardware limitations.

btw UAC is just like linux permission. You will only need to enter your pass when you try to do system task

OK.
But UAC is less annoying LoL
Thank you.

---

### Post by super1bat on 2011-05-03
> **kaldor said:**
> Just so you know, on these forums people usually ask you to type commands. This is because it is MUCH easier on both parties than telling somehow what to do with mouseclicks. For all the software installed via commands, you can get it normally via Ubuntu Software Centre.

OK.
Thank you for the info :)

---

### Post by super1bat on 2011-05-03
Can I divide the 14.5gb partition to 2 or 3 new partition ? So I can install ubuntu in it ?
I'll not download alot of thing :D.

What is the best way to do it and do I use disk management from win7 or do I use another software ?.

Thank you.

Edit: And what size I'll make for every partition ?

---

### Post by krishnandu.sarkar on 2011-05-04
So you want to allocate 14GB for Ubuntu right??

Well, create a partition 10GB or 12GB for / (root), and assign remaining 2GB / 4GB respectively to swap.

See, in any of the way you should not disable the asking for root password.

See Linux is very much concerned about security and this is a basic security feature.

Let me make you a little story so that you can understand the things behind this annoying thing(according to your words).

In windows, I'm sure you have lowered down your UAC Settings, so what happens, when you try to install any software it doesn't asks for your permission anymore, which saves you from one click, but brings you lot of trouble, like when some gains unauthorized access to your PC without your knowledge and tries to install some virus, malware, spyware etc. in that case too you are not being notified and alas....you made mistake.

So as you lowered down your UAC settings, it doesn't notify you any unauthorized access to your resources, be it memory, be it processing power etc.

Hope you got the fault you made...by trying to get away from just one click you called trouble twice to it.

So in Linux, if you have the root password, you can do anything, yes anything and everything to your system. Say mistakenly you typed a wrong command and press enter and then it came to your mind that it'll delete everything in your system, typing that root password will make you remind that and you'll end up clicking cancel or cancelling it in the terminal.

And yes, generally use terminal, you'll learn the Linux way too, and peoples can help you easily too.

Enjoy Ubuntu :D

---

### Post by mastablasta on 2011-05-04
> **super1bat said:**
> Can I divide the 14.5gb partition to 2 or 3 new partition ? So I can install ubuntu in it ?
I'll not download alot of thing :D.

 
why do people complicate in their advice to new users is beyond me... afterall this is Ubuntu.
 
I am guessing from your first post that the "empty" partition you decided to use for Ubuntu is actually formated in one of the Microsoft file systems (NTFS, FAT32...). If you delete it it will be free disk space where you can install Ubuntu. Now ubuntu has an automatic partitioning option and as a beginner you can go with that. it will partition your 14.5GB partition automaticly so you won't have to worry abotu root, swap and all that being cretaed. it will all be done for you.
 
> 
What is the best way to do it and do I use disk management from win7 or do I use another software ?.

 
In disk management delete the partition and it woll show as free disk space or unused disk space or something like that. 
 
as for administration password you only need to use it when installing new programmes. i am not usre if you understand why it is there. let's say a virus/trojan/malware is installed on your computer. if it wan't to run and do harm to your system it first needs your permission. you give it by typing in your suser password. sytsem basically checks that it was YOU that launched important commands that can change the system itself. It does this by asking for password. also as i know password has a timeout period.
 
I am not sure how easy is this in gnome but if you used Kubuntu (KDE) then you can easilly disable user login as well as type in one password per session.
 
one thing is sure that once you install and configure the system the way you like it, you won't be using that password so much anymore. expcet maybe for system updates.
 
 
as for your game - it might have been slow because:
- you were running it in Wubi (which uses virutalisation and extra system resources)
- it is a more graphic intense game and you were running it with all desktop effects (Compiz) switched on - often this can cause lag in games. disabling the desktop effects can help.
- 3rd option was already mentioned - drivers for your card - they might not be ready for 11.04 and it's kernel yet. perhaps you could give the older LTS (long term support) 10.04 version a try.

---

### Post by Rachel_Eliason on 2011-05-04
> **super1bat said:**
>  
Question here: Whenever I do anything it ask for password, It's so annoying, How I can disable it ?
 

 
Entering your password all the time isn't half as annoying as all the viruses and malware you get in Windows, and requiring a password for all administrative functions is one of the main reasons you don't get as much of that stuff. 
 
And Welcome to Ubuntu, it's a fun little world:):):)

---

