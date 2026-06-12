---
title: "correct graphics drivers"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by FinnMcCool on 2010-01-29
But I have one or two niggles having installed Ubuntu. (P.s. I'm running Karmic Koala)
 
I'm not the brightest guy, but I've got reasonable "techy" experience. But one thing I've noticed from the moment I've installed ubuntu is how difficult it can be to get everything right in this Microsoft orientated world.
 
I've had it a few days now and I've still not figured out how to install the correct graphics drivers to ensure I can get higher than 800x600. Hell even the Software manager didn't work to start with and I had to type some random code into Terminal to enable the software manager.
 
It took me a while to figure out how to get the wireless Netgear going in the first place. Although admittedly it did turn out to be fairly simple. Maybe I was lucky(?).
 
But thinking of the possibilities I want to get from my system - Foobar2000, Football Manager 2010, web browsing, CD burning, other decent spec games, image editing (although GIMP is already installed - score!) etc etc
 
While I really like the OS so far, and am glad to get away from Billy Gates for a while, I do feel that with every new program installed there could well be a right bit of hassle that I might not be prepared for. Hell, like this silly resolution problem it might not get resolved at all if it's too complex!
 
So my question to anyone still with me is: Is this the life of an ubuntu user? Is it accepted that all new programs are going to be Windows-orientated and therefore a fair likelihood that it will be a struggle to get installed?
 
Or am I fretting too much?
 
Cheers from a n00b

---

### Post by Cheezespread on 2010-01-29
Try System ->Administration ->HardWare Drivers if you still have issues. The system should recommend suitable drivers for the your graphics card.

From my experience , When i started off with UBuntu/Linux as a whole , I asked one question to myself " How did you start using Windows OS and the apps in there ?. You had to learn one way or another to start off. Just the same way. " Frustration is natural for anyone . So calm down . Give it some time .

---

### Post by FinnMcCool on 2010-01-29
Hi, cheers for the quick reply / help. I'll be sure to amend this thread once I get things working.
 
I am actually calm! If it all goes belly up I can easily go back to *ahem* windows. But just a bit of concern that is all.

---

### Post by lijcam on 2010-01-29
Hi FinnMcCool Fear not but there is a light at the end of the tunnel. Once you learn the differences in linux and windows. 
Package management in ubuntu was one of the first things I struggled with. Have a read of [URL="https://help.ubuntu.com/9.10/add-applications/C/installation-windows-ubuntu.html"]https://help.ubuntu.com/9.10/add-applications/C/installation-windows-ubuntu.html
[/URL] This will help explain the differences with Ubuntu and Windows software installation.

You might also find this interesting and helpful [URL="https://help.ubuntu.com/9.10/switching/index.html"]https://help.ubuntu.com/9.10/switching/index.html
[/URL] (Switching From Windows)

---

### Post by halitech on 2010-01-29
First off, Linux is not windows and is not meant to be a windows replacement.

True, some windows apps will run in Ubuntu through programs like WINE but not all of them. Checking the list you posted of apps, here is what I found:

foobar2000 - windows only - [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749) - possibly should run with WINE

Football Manager 2010 - windows/mac - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18088&iTestingId=45667](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18088&iTestingId=45667) - alot of work to get it to run and may not run all that well.

web browsing - firefox is native

cd burning - brasero, k3b, gnomebaker and more are available

games - most games are windows based. Honestly if you are into games, either dual boot or stay with windows. I don't mean that in a snide way but games are where MS is beating linux and sadly thats just the way it is. Most people on here that are gamers either dualboot or keep a machine just for gaming.

video card - what card do you have?

---

### Post by FinnMcCool on 2010-01-29
Thanks guys,
 
It is a Nvidia 6100 motherboard (graphics built in) and I have had a bit of problems setting up the drivers.
 
One thing Halitech
 
>  Linux is not windows and is not meant to be a windows replacement
 
That's perhaps where I'm going wrong. I've been reading a lot of introductory passages as others have posted and I was under the impression that Ubuntu (not Linux per se) **could** be a Windows replacement. What I'm looking for is an operating system that is less memory intensive, has decent support of programs new and old (not necessarily gaming only, although FM2010 will be a must) and is of course not Microsoft.
 
My original post was merely asking the question CAN Ubuntu be an adequate replacement, and provoking discussion for us noobs who are looking at the big switch. I am actually dual-booting at the moment but find Windows annoyingly sluggish and with all the annoying Windows type skullduggery and want to move away from that if at all possible.

---

### Post by stalkingwolf on 2010-01-29
it has been my experience over the years with Ubuntu that some issues get fixed, some dont, and some get fixed then broken again.  Wireless and graphics drivers are two that lead the pack.   I have a laptop that is currently relegated to the status of paper weight(not do to Ubuntu)  the graphics card in it is a morphidite.  In 8.04 I could fix it.  in the current releases I cant.  Nobody seems to know the command.  I have asked 3 times in 3 places.  In 8.04 it was "sudo displayconfig-gtk" , a couple adjustments and Bobs your uncle.  That command has not worked since 8.04.

Wireless is another area.  I use two wireless adapters that have worked out of the box since 7.10.  in 8.10 they are shut off and no way to enable them.
in 9.10 they work, but something is fubar with the password set up.  it wont authenticate.  And it is 9.10.  I can connect from several other OSs.

In 9.04 my S3 unichrome card doesnt work, in 9.10 it works enough for my use. I can get the resolution I want but no 3d.

It would seem that the old arguement that linux developers are volunteers
is no longer valid,
[]("http://linux.slashdot.org/story/10/01/21/230201/75-of-Linux-Code-Now-Written-By-Paid-Developers?from=rss&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+Slashdot%2FslashdotLinux+(Slashdot%3A+Linux)&utm_content=Google+Feedfetcher")  according to this article 75% are now paid.  If this is the case then these on going problems need to be addressed.

The old adage would seem to apply here, "if it works, dont fix it."
and " if you cant do it right, dont do it at all."

Given that Ubuntu is being used to give older systems new life , attention
needs to be given to the continued support of older hardware.

The focus on bleeding edge could indeed fucus.

---

### Post by halitech on 2010-01-29
If you are expecting Ubuntu to be a drop in replacement then that is a conception that alot of people have. As far as allowing you to do everything you can do in windows, yes it is an operating system with its own programs and ways of doing things but its not the windows way of doing things so keeping a windows mindset will just frustrate you when you are trying to do things.

If you are not tied to windows specific software then yes, Ubuntu can be a replacement for windows, but, if you require windows software, then that software will run on windows and may or may not run on Ubuntu using WINE.

For me, I was able to ditch windows completely as I'm not a gamer and I have found replacements for the programs I did use in windows so I have no need for windows at all.

---

### Post by FinnMcCool on 2010-01-29
[FONT=Calibri][SIZE=3]@Stalkingwolf[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks for the info – that seems to be part of my worry. If things stop working it is a worry, and I’m not just talking specifically Windows stuff. I can appreciate FM2010 was made for Windows and hopefully WINE is going to help me out, but if it’s going to be a running battle with hardware and other software then perhaps it isn’t for me.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]@Halitech[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I don’t expect it to be a drop-in replacement, there will be teething troubles as like many I’ve used Windows for over a decade. I am not perceptively trying to keep a Windows mind-set but being the standard it’s only natural to compare, and given most software is written with Windows in mind, again comparisons and alternatives will be made. I am keeping an open mind here to see if the big switch in the long term will be best for me. If it isn’t I’m not fussed, but this beginners forum is for me the best place to voice ideas.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]What does Ubuntu offer *you* exactly over Windows?[/SIZE][/FONT]

---

### Post by realzippy on 2010-01-29
*"...dual-booting at the moment but find Windows annoyingly sluggish and with all the annoying Windows.."*

..well,that might increase after getting familiar with Ubuntu.You even might get to the point asking yourself how ever been able to stand that...
however dualboot is the only way to go when enjoying newest directx games,for nearly everything else there should be an alternative.
AND there is all that fancy stuff that there is not on windows...

---

### Post by zipperback on 2010-01-29
> **FinnMcCool said:**
>  
I've had it a few days now and I've still not figured out how to install the correct graphics drivers to ensure I can get higher than 800x600.

What kind of graphics card do you have?


> **FinnMcCool said:**
>  
 Hell even the Software manager didn't work to start with and I had to type some random code into Terminal to enable the software manager.


To install software, you can do it a number of ways, however two easy ways are through the software center and through synaptic.

Applications -> Ubuntu Software Center
System -> Administration -> Synaptic Package Manager

Both of these options should work just fine with a clean install.

> **FinnMcCool said:**
>  
It took me a while to figure out how to get the wireless Netgear going in the first place. Although admittedly it did turn out to be fairly simple. Maybe I was lucky(?).


Wireless network management has come a long way with Linux. It's pretty easy now to get it working correctly as long as the wifi chipset is one of the recognized ones.

> **FinnMcCool said:**
>   
But thinking of the possibilities I want to get from my system - Foobar2000, Football Manager 2010, web browsing, CD burning, other decent spec games, image editing (although GIMP is already installed - score!) etc etc


Firefox is installed by default for web browsing.
Other browsers are easily installed such as Google Chrome, Opera, and a few others too.

CD Burning should also be working just fine with a clean install as well. There are numerous additional cd/dvd burning applications which are available in the ubuntu repository servers.


> **FinnMcCool said:**
>  
While I really like the OS so far, and am glad to get away from Billy Gates for a while, I do feel that with every new program installed there could well be a right bit of hassle that I might not be prepared for. 

Package management with Ubuntu is pretty easy, just install your software through either the software center or through synaptic.


> **FinnMcCool said:**
>  
Hell, like this silly resolution problem it might not get resolved at all if it's too complex!

Try this.
System -> Administration -> Hardware drivers.

See if there is a video driver available. If there is one available, but it is inactive, then you can check the box next to it, and then install the video driver.

What kind of video card do you have?

> **FinnMcCool said:**
>   
So my question to anyone still with me is: Is this the life of an ubuntu user? Is it accepted that all new programs are going to be Windows-orientated and therefore a fair likelihood that it will be a struggle to get installed?

Installing software from the available packages is pretty easy with the package management tools. Once you get used to doing things a little differenly than with Windows, Ithink you'll find it is much easier than with a Windows computer.

> **FinnMcCool said:**
>   
Or am I fretting too much?

A little, but it is to be expected since you are moving away from a very familiar operating system and moving into Linux which you aren't all that familiar with. Learning how to manage your computer with Ubuntu is different from Windows. 

Be patient and don't be afraid to ask questions. Do a lot of reading, and check the ubuntu forums, it's a great resource of information.

I hope this helps you.
- zipperback
:popcorn:

---

### Post by cascade9 on 2010-01-29
> **halitech said:**
> foobar2000 - windows only - [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749) - possibly should run with WINE

I runs with WINE, pretty well. If your prepared to do some mucking around- 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1749)

[http://www.hydrogenaudio.org/forums/index.php?showtopic=54933](http://www.hydrogenaudio.org/forums/index.php?showtopic=54933)

I use it in WINE pretty often, sometimes I use a linux-native player (exaile mainly) but foobars still far and away my favourite audio player. I just wish there was a linux native player as configurable as foobar.

---

### Post by Mark Phelps on 2010-01-29
Regarding Ubuntu being a Windows replacement ...

When folks here point out that Linux is not Windows, what they're telling you is that while you can do many of the same things with Linux that you did with MS Windows, in some cases, you might have to do them a bit differently.  

What we're saying is that Linux is not a free clone of MS Windows.

Happiness in this community comes from finding Linux alternatives for doing what you want -- not from struggling with ways to reuse MS Windows apps.

So, if you're willing to change your ways a bit and learn how to do things the "Linux way", you'll be happy with the switch; if you're only interested in a free version of MS Windows, you'll be sadly disappointed.

---

### Post by zipperback on 2010-01-29
You should be able to get FM2010 running with Linux.
Check this page for more information.
[http://www.fmtux.net/](http://www.fmtux.net/)

I hope this helps you.

-zipperback
:popcorn:

---

### Post by FinnMcCool on 2010-01-29
Thanks zipperback and to everyone on this thread for taking the time to answer :P
 
> **Mark Phelps said:**
> Regarding Ubuntu being a Windows replacement ...
 
When folks here point out that Linux is not Windows, what they're telling you is that while you can do many of the same things with Linux that you did with MS Windows, in some cases, you might have to do them a bit differently. 
 
What we're saying is that Linux is not a free clone of MS Windows.
 
Happiness in this community comes from finding Linux alternatives for doing what you want -- not from struggling with ways to reuse MS Windows apps.
 
So, if you're willing to change your ways a bit and learn how to do things the "Linux way", you'll be happy with the switch; if you're only interested in a free version of MS Windows, you'll be sadly disappointed.
 
Cheers Mark, I didn't mean to come across like I wanted Windows but without paying for it! I do appreciate there are some things I guess I may not be able to do and therefore will need an alternative / workaround. 
 
But apart from the specifically Windows designed programs I am genuinely interested in getting the most out of Ubuntu while hopefully achieving the same things I have previously.. As a noob I suppose fairly obviously things have been a bit difficult to get used to, but every day I'm learning new things and hopefully I can use the helpful pointers from this thread to get my gfx and then FM2010 working. Thanks for the link zipper.
 
No doubt I'll report back after giving this some time and effort this weekend

---

### Post by halitech on 2010-01-29
> **FinnMcCool said:**
> 
[FONT=Calibri][SIZE=3]@Halitech[/SIZE][/FONT]

[FONT=Calibri][SIZE=3]What does Ubuntu offer *you* exactly over Windows?[/SIZE][/FONT]
Actually I'm running Debian now after running Ubuntu for over a year

For me, it offers me the freedom to do what I want with my system. It offers me a system that runs more stable, is virus free, doesn't require constant cleaning and maintaining and just does what I want.

Linux in general offers me the freedom to use the software and Operating System that I want to use, not what someone else tells me I have to run. I don't need to spend hundreds of dollars on upgrades for the software and hundreds of dollars upgrading hardware to run those updated systems. When I first changed over I kept the same old P4 1.8gig system running for 3 years longer before I upgraded and I upgraded the hardware because I had the money and wanted to upgrade, not because I had to.

It all depends on the mindset a person takes on how well they will adjust to going from windows to linux.

---

### Post by FinnMcCool on 2010-01-30
Just thought I'd pop in to say that I got the resolution thing sorted thanks to much of your advice. Not sure how to chance the thing to *solved*

I think part of the problem was I did rush a little installing it in the first place and hence had quite a small disk space to work with so all sorts of installations went wrong I believe. I done a complete reinstall on another HD (70gb of space to play with this time) and all is good. I have a decent resolution!

Now going to muck around with making sure everythings to my liking, and also going to have a quick go at WINE.

Thanks again

---

