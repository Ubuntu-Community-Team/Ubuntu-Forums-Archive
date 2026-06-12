---
title: "Very confused"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Lowelife101 on 2009-05-06
Recently my 5 year old part self built (my dad helped me :o) computer which is running windows has decided to fail miserably, it's been wiped so many times before i'm getting tired of the process of lightening fast, goes slow, spams error messages, spams blue screens and then refuses to do pretty much anything else. Before i get to the blue screen spam phase i settled on trying an alternative. My dad suggested we try mac, now i like mac's but i felt searching for emulators and learning a new system was time wasted if i'm still throwing money at a corperate machine that is as helpful as a condom machine in the vatican again. And then my friend suggested i do the which linux distribution is best for you test and ubuntu came up.
 
So i've been doing lots and lots of research about what i should do before migrating to ubuntu, for the most part i thought i had a good grasp of what i needed to do to get simplistic things running e.g. my printer, open office, firefox,thunderbird, teamspeak and world of warcraft through an emulator (hell i even found a world of warcraft addon updater that has a linux port, that pleased me no end ^^ ).
 
After putting all my important files on an external hard drive i made a list of all the other programmes that i use that i need to find a linux equivalent for OR find an emulator e.g. winamp. 
 
After nosing around a little i found Kubuntu which looked like (to me atleast) something a little more stylish, it's not a drop in replacement for windows but hell that's not what i wanted anyway, i just did'nt want soemthing that looked like it was hand typed in 1985 ^^
 
When i did the live cd test it loked amazing but given a few seconds i was pretty damn lost, most of the guides i'd read were for older versions so buttons etc were'nt where i expected.
 
In short i'm a little disappointed, i've always been a slow learner but now i feel like i've been throughly thrown in the deep end and have to shout for a windows life raft, i feel dirty :( . Things like command lines scare the **** out of me, i'm worried my computer is gunna start spewing blue electrical smoke like it did the last time i installed a fan in it :KS
 
Tl;Dr can anyone grab me some links of a guide for the current version of kubuntu, preferably showing how to install things like realplayer for linux, get wine to run world of warcraft, how to install teamspeak and a general "clicking this dohicky will do this" guide.

---

### Post by abn91c on 2009-05-06
everything you need is here [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by Nxion on 2009-05-06
Well I have always love this site. Lots of info. Pretty easy to nav in my opinion.
[URL="http://ubuntuguide.org/wiki/Ubuntu:Jaunty"]
http://ubuntuguide.org/wiki/Ubuntu:Jaunty[/URL]

I have a few more I can recommend once I find them, this is the only one that popped out in my mind :)

---

### Post by Nxion on 2009-05-06
> **abn91c said:**
> everything you need is here [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

That was another. How could I forget that one lol. 

Here is one more for ya:
[URL="http://ubuntuforums.org/showthread.php?t=801404"]
http://ubuntuforums.org/showthread.php?t=801404[/URL]

---

### Post by Penguin Guy on 2009-05-06
Some people prefer KDE, some people prefer GNOME. If you're not liking your Kubuntu experience; [try GNOME]("http://www.psychocats.net/ubuntu/puregnome").

KDE:
[[IMG]http://www.psychocats.net/ubuntu/images/kdegnomejaunty09.png[/IMG]]("http://www.psychocats.net/ubuntu/kdegnome")


GNOME:
[[IMG]http://www.psychocats.net/ubuntu/images/kdegnomejaunty10.png[/IMG]]("http://www.psychocats.net/ubuntu/kdegnome")

---

### Post by Bartender on 2009-05-06
> **Lowelife101 said:**
> spams error messages, spams blue screens and then refuses to do pretty much anything else....  

i'm worried my computer is gunna start spewing blue electrical smoke like it did the last time i installed a fan in it

Is anyone else thinking what I'm thinking?  I'm thinking that Linux is not gonna solve Lowe's problems...

---

### Post by mick8985 on 2009-05-06
> **Bartender said:**
> Is anyone else thinking what I'm thinking?  I'm thinking that Linux is not gonna solve Lowe's problems...

If you mean that his browsing habits are probably the source of his windows grief I beg to differ, on linux you can pretty much browse any old website you want it's very hard to slow a linux system down through browsing. 
If you mean with his BSODs I would agree perhaps he need to do a memtest, could be faulty ram.

---

### Post by presence1960 on 2009-05-06
There is no easy way out. Linux is not Windows, is not like Windows and therefore expect a learning curve which requires complete willingness to learn and work through problems that arise. **THERE IS NO PAID SUPPORT SO GET USED TO SEARCHING THESE FORUM THREADS AND HAVING GOOGLE AS A BEST FRIEND.**

Now if you've gotten past that you will have to learn some command line. A lot of us felt the same way you do about the command line. With some time reading and practicing you will get there with it.

If you are tired of Windows and are willing to invest your time & effort into learning Linux, well my friend I have to say you are already in the best spot you can possibly be- the Ubuntu Forums. Remember this always: reflect back when you started using Windows. You didn't just jump right in and know what you know today about Windows. It was a learning process which included setbacks along the way. It will be so with Linux. 

So how bad are you really tired of Windows is what I ask you? Pain is a great motivator. If you are really tired of Windows then you will be able to learn Linux from scratch just like you did with windows.

---

### Post by Mortus Pryde on 2009-05-06
FYI the reason command line is used so often in the forums is not that is has any more "Power" than what you may be told to point and click, it is simply a more direct way of doing things that remains largely the same regardless of which interface you chose (Gnome in Ubuntu, KDE in Kubuntu and Xfce? in Xubuntu.). For strictly software "sudo apt-get install <package>" is safe, this just a more direct way of saying "Go to your Synaptic Package Manager and search for <package>, when you find it mark it for install.". Synaptic and "apt-get" both retrieve the package and any missing components from what are called "Repositories". The ones that come with Ubuntu by default are "Safe", the applications in them are known to run well with Ubuntu. Another trusted one people may suggest is "Medibuntu" should you need aditional codecs or non-open source applications like Google Earth or Skype.

Drivers in my experiance require you to do some reading before you commit to installing them. Not all driver versions, especially graphics drivers are compatable with all hardware, so in this case just because it's in the repository does not mean it is safe for your hardware. For example you may have an ATI graphics card you want excelerated graphics for, the latest proprietary driver in the repositories do not support some of the older ATI cards and if you have one that is not supported and install it anyway it will cause issues you will only be able to fix through command line or reinstalling.

---

### Post by Lowelife101 on 2009-05-06
> **presence1960 said:**
> There is no easy way out. Linux is not Windows, is not like Windows and therefore expect a learning curve which requires complete willingness to learn and work through problems that arise. **THERE IS NO PAID SUPPORT SO GET USED TO SEARCHING THESE FORUM THREADS AND HAVING GOOGLE AS A BEST FRIEND.**
 
Now if you've gotten past that you will have to learn some command line. A lot of us felt the same way you do about the command line. With some time reading and practicing you will get there with it.
 
If you are tired of Windows and are willing to invest your time & effort into learning Linux, well my friend I have to say you are already in the best spot you can possibly be- the Ubuntu Forums. Remember this always: reflect back when you started using Windows. You didn't just jump right in and know what you know today about Windows. It was a learning process which included setbacks along the way. It will be so with Linux. 
 
So how bad are you really tired of Windows is what I ask you? Pain is a great motivator. If you are really tired of Windows then you will be able to learn Linux from scratch just like you did with windows.
 
 
Well it's both a mixture of both boredom and annoyance, pretty much every single computer has window's on it and i feel as if i'm not learning anything new or useful when i use it, i'm almost stagnating. Besides that i've not used a single windows machine that has'nt had some sort of bug or error or some sort of counter intuitive mechanism that makes 0 sense no matter how long you use it, i'm tired of booting up the very machine i'm running and getting 3 error messages that tell me somethings broken that i've never heard of and never affects the things i use anyway:confused:.
 
Anyhoo i'm going to keep trying my best to make reading all these guides nice people have given me worthwhile ^^
 
p.s my dad say's he want's to keep windows on the machine but he's gunna try a fresh install, i am not interested in messing around with that anymore, however i was wondering if it's possible to partition external hard drives and install ubuntu/kubuntu on the new partition, that way my dad keep's windows on the internal hard drive (which after reading some responses may well just be busted), get's 500gb of storage space in case the internal drive breaks and i get 500gb to put ubuntu/kubuntu on.
 
p.s.s sorry for my appaling english

---

### Post by presence1960 on 2009-05-06
> **Lowelife101 said:**
> Well it's both a mixture of both boredom and annoyance, pretty much every single computer has window's on it and i feel as if i'm not learning anything new or useful when i use it, i'm almost stagnating. Besides that i've not used a single windows machine that has'nt had some sort of bug or error or some sort of counter intuitive mechanism that makes 0 sense no matter how long you use it, i'm tired of booting up the very machine i'm running and getting 3 error messages that tell me somethings broken that i've never heard of and never affects the things i use anyway:confused:.
 
Anyhoo i'm going to keep trying my best to make reading all these guides nice people have given me worthwhile ^^
 
p.s my dad say's he want's to keep windows on the machine but he's gunna try a fresh install, i am not interested in messing around with that anymore, however i was wondering if it's possible to partition external hard drives and install ubuntu/kubuntu on the new partition, that way my dad keep's windows on the internal hard drive (which after reading some responses may well just be busted), get's 500gb of storage space in case the internal drive breaks and i get 500gb to put ubuntu/kubuntu on.
 
p.s.s sorry for my appaling english

you can install on external drive or you can partition the internal drive to dual boot also. I would stick with the internal drive (even if I had to buy a second one) just because of the difference in speed, unless you have an eSata drive & port..

Your English is not that bad, I can understand you!

---

### Post by Lowelife101 on 2009-05-06
I do try my best when typing to be clear but I have a reputation of writing like i talk, all garbled and flustered ^^. 
 
I'm going to build a new machine anyway but atm i'm putting up with old crashy (i renamed it from bluethunder after it got wiped for the 5th time) So i thought putting it on the external hard drive would make data transition from this machine to my new build when i get the cash easier.
 
Could you point me in the right direction to do that? :o

---

### Post by Niniel on 2009-05-06
To do what?
Get cash? Transfer data?

Nothing wrong with an external hd, in my opinion. It's faster than CD (with USB 2 of course), and the Live CD works pretty well already...
So go ahead and install it on the external drive.

---

### Post by Lowelife101 on 2009-05-06
sorry i ment when i get the cash to build a new system having all my linux stuff already on an external hard drive will make transition of data to the other machine easier.

---

### Post by ugriffin on 2009-05-06
Please, whatever you do, don't use an external HD. Dual boot. All you need to do is resize your current EXT3 linux partition, let some 20 gigabytes free for Vista or 10 for XP, and install. Fix the grub bootloader (there's a lot of places that teach you how. If you dual boot, you can even PM me and I'll teach you how to fix it), and then, from Kubuntu, do this:

K Menu>Computer>System Settings>Advanced Tab>GRUB Editor.

In there, it should probably show your Windows install. Simply set it to default, go to options, and check the "hide boot menu" option. Give it some 2 to 3 seconds.

Now, each time your dad turns on the computer, he'll be greeted by Windows as long as he doesn't press ESC. You can press ESC and boot into Kubuntu, if you want. Quite simple, and no hassles of the external HD.

---

### Post by Lowelife101 on 2009-05-06
thanks mate that's awesome :o.

---

### Post by Mortus Pryde on 2009-05-06
Oh! BTW! Jumping back to your origional post! Once you get set up and start looking for alternatives again, if you still need an alt for WinAmp take a look at Exaile you can find it in the repositories.

---

