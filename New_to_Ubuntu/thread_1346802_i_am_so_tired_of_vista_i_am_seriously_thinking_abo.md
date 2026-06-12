---
title: "i am so tired of vista i am seriously thinking about putting linux on"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by deck60 on 2009-12-05
while ubuntu is downloading i think i will ask some questions about it 
 
1- can i run dual boot vista and ubuntu 
2- what downfalls problems will i expect with ubuntu
3- will my email work 
4- will my programs work 
5- printers hp 1312 and xerox 8200b 
6 i had ubuntu loaded on a old laptop that kept freezing up the startup and just loading it up not using it kept that working fine 
 
so right now i have a little over a hour of downloading left so lets see what kind of great minds are out there

---

### Post by ed-koala on 2009-12-05
1. Yes.
2. Very few if you are careful to do your homework first.
3. Which email?
4. Which programs?
5. HP printers are pretty good usually, not sure about xerox. You'll need to check compatibility (see doing homework)
6. Laptops seem to act a bit flaky for some reason. Just an observation from reading these forums, not from any experience.

Homework

Burn your CD at low speed.
Run from the CD awhile and check out how things work, save yourself some possible headaches later.
Research your hardware and software. See what is known to work (hardware) and what alternatives exist (software).  Also check into Wine (google WineHQ and check compatibility if you just don't want to give up that windows app)

This will help make your experience smoother.

---

### Post by aysiu on 2009-12-05
> **deck60 said:**
> 
1- can i run dual boot vista and ubuntu Yes. But do not mess with repartitioning and replacing the Windows boot loader.

If you run a dual-boot, start with Wubi:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Wubi allows you to install a dual-boot without messing with partitions, and if you later decide you don't want the dual-boot any more, you can uninstall Ubuntu as you would any normal Windows programs.

> 2- what downfalls problems will i expect with ubuntu Some hardware may not be compatible. Some Windows-only software will not work. There is a learning curve to move away from what you're familiar with.
> 3- will my email work If it's Hotmail or some Microsoft Exchange email and you intend to use an email client, then, no not at all or not perfectly. Otherwise, yes. > 4- will my programs work If your programs have Linux ports or equivalents, yes. Otherwise, probably not. > 5- printers hp 1312 and xerox 8200b HP, probably. Xerox, I don't know.

Best thing to do is just boot up the CD. The default loads up a functional "live" session that doesn't affect your hard drive, but you'll see very quickly if any hardware issues come up (no sound, no wireless, no printer, etc.).

---

### Post by ethanmadden on 2009-12-05
1- Yes you can dual boot. I am booting vista and karmic right now, actually.

2- The only problems I have really seen are with gaming, but as long as you don't do too much of that you are fine.

3- That depends on what you mean. Any web-based e-mail clients will work exactly the same. If you use a PoP program like outlook or thunderbird then you can use "evolution". Actually, you can probably still use thunderbird...

4- Again, that depends. Some programs you can run under WINE, and others have alternatives in Ubuntu. You will be able to do pretty much the same things you could before, except for gaming which I mentioned earlier.

5- Your printers should work. I have yet to try to use a printer that didn't work immediately under ubuntu.

I'm not really sure I understand your 6th question... Are you asking if it will still freeze up?

---

### Post by ethanmadden on 2009-12-05
1- Yes you can dual boot. I am booting vista and karmic right now, actually.

2- The only problems I have really seen are with gaming, but as long as you don't do too much of that you are fine.

3- That depends on what you mean. Any web-based e-mail clients will work exactly the same. If you use a PoP program like outlook or thunderbird then you can use "evolution". Actually, you can probably still use thunderbird...

4- Again, that depends. Some programs you can run under WINE, and others have alternatives in Ubuntu. You will be able to do pretty much the same things you could before, except for gaming which I mentioned earlier.

5- Your printers should work. I have yet to try to use a printer that didn't work immediately under ubuntu.

I'm not really sure I understand your 6th question... Are you asking if it will still freeze up?

---

### Post by VastOne on 2009-12-05
> **deck60 said:**
> while ubuntu is downloading i think i will ask some questions about it 
 
1- can i run dual boot vista and ubuntu 
2- what downfalls problems will i expect with ubuntu
3- will my email work 
4- will my programs work 
5- printers hp 1312 and xerox 8200b 
6 i had ubuntu loaded on a old laptop that kept freezing up the startup and just loading it up not using it kept that working fine 
 
so right now i have a little over a hour of downloading left so lets see what kind of great minds are out there

1 - Yes but you may encounter problems with initial setup - take this hour to read about installing a dual boot system

2 - Learning curve will be the biggest - Use this forum and search for help before asking for help...Meaning the wheel most likely has already been invented.

3 - You email should work - It depends on what it is. If it is online it will. If not then Evolution or any of the other mail packages will work.

4 - If not, then there will be an alternative or Wine.  Again use this forum to search for the app to work or replace.

5 - Those printers should work, if not there are solution with CUPS. Again use this forum to search

6 - Not sure what the question is here

Good luck, don't give up, we will help you all we can

---

### Post by VastOne on 2009-12-05
4 very similar responses....all within 5 minutes of each other...


Impressive

---

### Post by RJ12 on 2009-12-05
> **deck60 said:**
> while ubuntu is downloading i think i will ask some questions about it 
 
1- can i run dual boot vista and ubuntu 
2- what downfalls problems will i expect with ubuntu
3- will my email work 
4- will my programs work 
5- printers hp 1312 and xerox 8200b 
6 i had ubuntu loaded on a old laptop that kept freezing up the startup and just loading it up not using it kept that working fine 
 
so right now i have a little over a hour of downloading left so lets see what kind of great minds are out there
Hi, Welcome to the community
1.Yes you can dual boot vista and Ubuntu

2.I have not had any problems so far, but the biggest problem people have are hardware problems but if you try the LiveCD you can test all of your hardware it will be like its installed on your computer **but its not** when you turn off the computer it will clear

3.Yes, if you use webmail you should be fine. If you use hotmail in a email client like outlook then we might have to do some tinkering (I personnaly use Gmail which works great)

4.Windows programs do not run on Ubuntu Natively (Some programs can be ran in WINE a compatability layer for Ubuntu) but most Windows programs have alternatives

5.Someone else might have to tell you about the printers (HP has some drivers for Linux I think called HPLIP)

6.Ubuntu has gotten way better and if you have any probelms we should be able to sort it out for you :)

Hope you enjoy it

P.S. When you dual boot you need to use Vista's tool to shrink your C:\ drive and Ubuntu will install in the free space thats left and automatically see vista and give you a choice when every time you turn on your computer and ask which one to load :)


Edit: Wow when I was typing this post I thought I was gonna be first but then they all popped up so sorry for the repeated answers, but +1 with the WUBI just be careful I have heard some people having problems with WUBI and Karmic

---

### Post by deck60 on 2009-12-05
#6 was just a past experience that i had I just installed it on a laptop dual boot with xp i was having problems with the laptop not wanting to start up  and i did mess abit with it then i went to windows to see if i cold get back in and it worked fine just putting it in was a great hep no i am looking at getting mre in to it with vista of which i hate but tese new laptops they dont come with anythng else 
 
most of the software programs are windows based that i use havent  called to find out the guy i normaly talk to is not in till 5-6

---

### Post by aysiu on 2009-12-05
> **deck60 said:**
> 
most of the software programs are windows based that i use havent  called to find out the guy i normaly talk to is not in till 5-6 These two sites may help you find native Linux alternatives:
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)
[http://www.osalt.com/](http://www.osalt.com/)

If not, you can see how well your Windows programs might run in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by halitech on 2009-12-05
> **deck60 said:**
> while ubuntu is downloading i think i will ask some questions about it 
 
1- can i run dual boot vista and ubuntu 
2- what downfalls problems will i expect with ubuntu
3- will my email work 
4- will my programs work 
5- printers hp 1312 and xerox 8200b 
6 i had ubuntu loaded on a old laptop that kept freezing up the startup and just loading it up not using it kept that working fine 
 
so right now i have a little over a hour of downloading left so lets see what kind of great minds are out there

answers have been pretty much right on but I'll answer #5, specifically about the Xerox8200. Yes it definitely will work but only if you download the correct files. When you search Xerox drivers, you'll end up with 3 options. DO NOT go for the first 2 options, use the third option (Linux CUPS Printing Package) Download the file, extract it then add your printer. When you get to where you can select the driver, select the option to provide the PPD file and browse to where you extracted the file. Locate the xrx8200b.ppd file and select it. Continue on from there. I know this works as I did it many times on Ubuntu, Debian, Fedora and others when I worked there.

direct link to the download page:
[http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8200&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=](http://www.support.xerox.com/go/getfile.asp?Xlang=en_US&XCntry=USA&objid=61334&EULA=0&prodID=8200&Family=Phaser&ripId=&langs=English%20(US)&plats=Linux&Xtype=download&uType=)

---

### Post by Anuovis on 2009-12-05
It all really depends on your specific needs. Only dual boot is certain, the rest will probably be OK but a few issues might arise now and then. You will surely have to look for software alternatives because there are few applications that run on both systems. 

Recall your first time using a PC if you can, probably a Windows system. Unless had some experience with Ubuntu, (I do not think this is the case) the feeling will be somewhat similar. It has a learning curve, do not give up easily if something is not perfect right from the start.

---

### Post by l-x-l on 2009-12-05
Use WUBI first. It's the most painless way to find out if you'd like Ubuntu.

---

### Post by The_Pirate_King on 2009-12-05
> **l-x-l said:**
> Use WUBI first. It's the most painless way to find out if you'd like Ubuntu.
But keep in mind that wubi is far more unstable than an actual installation and might crash frequently.  Also make SURE to uninstall WUBI before installing Windows 7, if you are going to install Windows 7.  I didn't uninstall WUBI first, and when I actually installed Ubuntu, the WUBI boot loader caused a conflict with the Windows 7 bootloader and made it so I couldn't access Windows 7 and had to do yet another clean install.

---

### Post by presence1960 on 2009-12-05
> **VastOne said:**
> 4 very similar responses....all within 5 minutes of each other...


Impressive

Like the House avatar!! Impressive.

---

### Post by newbieforever on 2009-12-06
> **deck60 said:**
> i am so tired of vista i am seriously thinking about putting linux on
that is one of the usual motivations
another good one, is learning something new: the more you know, the more you learn (kynda koan)
your reason anyway, could evolute to the next level: you are doing that for your freedom, freedom to act, freedom to think: free software is above all a matter of democracy
you brain will begin to work more smoothly, you'll start to see the big brain wash you got with marketed industrial software

> while ubuntu is downloading are you using bittorrent? there is no need to over load servers
remember to checksum the image
and burn it slowly: may be this is something mystique, anyway, you are not in a hurry, have a good cup of tea
maybe you want to try LinuxMint (a nice ubuntu derivative)

> 1- can i run dual boot vista and ubuntudefinitely yes; as it has been said, you can go wubi, or install grub
anyway: back up ALL your drive, including programs and the rest, even better, make an image of your harddrive
if something will go wrong (and sooner or later it will) you will discover that you had forgotten something, or you didn't know what you really needed
that said, I never had a problem with partition resizing, but this is just my experience; gparted alway do a good job, particularly if your drive has been judiciously house-kept and maintained

the best option, if you can afford it, is installing linux on an external usb disk, even a cheap one just to start; you could boot from usb

if you are not a techie, keep a copy of partition manager or similar at your hand, just in case, to restore your master boot record

> 2- what downfalls problems will i expect with ubuntuyou will feel discouraged, you will have to learn lot of new things, if not else because you will have so many new options you didn't imagine
remember that you will be with millions others, in that, that's the way things go
you should expect from a couple of months to a couple of years to feel comfortable in the new system, more or less the same time you needed to learn windows
this also depends on you target, and on your expectations
consider attending an installation party in a town besides you, you'll find nice people ready and happy to help you to get started the right way
 
> 3- will my email work 
 4- will my programs work 
 5- printers hp 1312 and xerox 8200bplease refer to guides, manuals, howtos, google and so on... you already heard of this...
expect to have quite a lot work to do
 
> 6 i had ubuntu loaded on a old laptop that kept freezing up the startup and just loading it up not using it kept that working finekeep in mind that linux in general is not as light as you might expect, particularly kde, and above all gnome
you could consider some light interface, like xfce (ver very nice, considering its speed), or lxde (amazingly fast)
  
> so lets see what kind of great minds are out therethe wiser you are, the greater wiseness you'll find

---

### Post by bwsmith7 on 2009-12-06
I felt the same way, and about 4 days ago I installed Ubuntu on my laptop.  I am now dual booting Windows 7 and Ubuntu, which means when I turn my computer on I can choose which one to run.  You could do the same thing with Vista.

I don't know much about computers, so I needed a little help from friends getting everything installed. It took a few hours, but since then I haven't had any problems starting up my computer and using Windows or Ubuntu.  Ubuntu is super fast and there is lots of great stuff you can do with it - I definitely prefer it over Windows 7, and am glad I made the switch.  That said, there are some drawbacks:

1. A learning curve.  Some things in Ubuntu are confusing at first, if you've never used it.  However after a few days of playing around (and lots of searching on this forum!) you should get the hang of it. 

2. You won't be able to use some programs that you use in Windows.  BUT Ubuntu has programs Windows doesn't, so it's kind of a trade.  Personally I miss Digsby a lot, but Pidgin is an okay replacement I guess.  I find that most programs run MUCH faster in Ubuntu, even compared to Windows 7.

3. Some hardware problems. I can connect to my network printer fine, and  the speed is much better than in Windows - internet speed seems better too (at least when using BitTorrent).   MY BIGGEST COMPLAINT: Ubuntu flips my webcam upside down, which makes is pretty much unusable in Gmail Video Chat or Skype. As I live overseas and often video chat with fam and friends, this is a huge problem.  Also, my laptop (Lenovo Y510) has surround sound, but it takes constant tweaking to get the speakers and mic to work properly.  

Ubuntu definitely has some areas to improve, but all in all I prefer it over Windows, and will keep it as my main OS for now.  Try dual booting or just try Ubuntu out using a cd, I'm sure you'll like it :)  

(Also, keep in mind that the ugly, ugly colors/theme can be easily changed - Ubuntu is capable of having the best-looking interface, in my opinion. See this video for an example of some of the cool visual effects: [http://www.youtube.com/watch?v=cK0eA6IfZOo](http://www.youtube.com/watch?v=cK0eA6IfZOo))

---

### Post by VastOne on 2009-12-06
> **presence1960 said:**
> Like the House avatar!! Impressive.

Thank you kind one!

---

### Post by The_Pirate_King on 2009-12-06
> **bwsmith7 said:**
> I felt the same way, and about 4 days ago I installed Ubuntu on my laptop.  I am now dual booting Windows 7 and Ubuntu, which means when I turn my computer on I can choose which one to run.  You could do the same thing with Vista.

I don't know much about computers, so I needed a little help from friends getting everything installed. It took a few hours, but since then I haven't had any problems starting up my computer and using Windows or Ubuntu.  Ubuntu is super fast and there is lots of great stuff you can do with it - I definitely prefer it over Windows 7, and am glad I made the switch.  That said, there are some drawbacks:

1. A learning curve.  Some things in Ubuntu are confusing at first, if you've never used it.  However after a few days of playing around (and lots of searching on this forum!) you should get the hang of it. 

2. You won't be able to use some programs that you use in Windows.  BUT Ubuntu has programs Windows doesn't, so it's kind of a trade.  Personally I miss Digsby a lot, but Pidgin is an okay replacement I guess.  I find that most programs run MUCH faster in Ubuntu, even compared to Windows 7.

3. Some hardware problems. I can connect to my network printer fine, and  the speed is much better than in Windows - internet speed seems better too (at least when using BitTorrent).   MY BIGGEST COMPLAINT: Ubuntu flips my webcam upside down, which makes is pretty much unusable in Gmail Video Chat or Skype. As I live overseas and often video chat with fam and friends, this is a huge problem.  Also, my laptop (Lenovo Y510) has surround sound, but it takes constant tweaking to get the speakers and mic to work properly.  

Ubuntu definitely has some areas to improve, but all in all I prefer it over Windows, and will keep it as my main OS for now.  Try dual booting or just try Ubuntu out using a cd, I'm sure you'll like it :)  

(Also, keep in mind that the ugly, ugly colors/theme can be easily changed - Ubuntu is capable of having the best-looking interface, in my opinion. See this video for an example of some of the cool visual effects: [http://www.youtube.com/watch?v=cK0eA6IfZOo](http://www.youtube.com/watch?v=cK0eA6IfZOo))
1.  This is true.  I have found that google and my hacker friend are my best resources when it comes to Ubuntu.  And these forums seem pretty nice... 
2. Digsby will soon be available for Linux-derivatives, so you won't have to miss it for long.  I have always loved pidgin, it was one of the first open source programs I installed and the first multi-protocol IM client.  I have never used Digsby though... is it nice? 
3. Try looking for some different webcam programs.  There is a chance there's one out there that will flip your video right-side-up again.  Unless by "overseas" you mean in the southern hemisphere... then it's upside down because you are! [just kidding]

One of the things I have noticed with Ubuntu is that firefox basically never crashes in it.  Firefox crashes a ton in windows, at least for me, so this is a really great improvement.

---

### Post by 3rdalbum on 2009-12-06
A lot of posters have suggested using a "Wubi" install. This is where you use a Windows program to install Ubuntu (the program is on the CD).

I disagree; there are technical issues with using Wubi. Firstly, you are limited to 30 gigabytes of space for Ubuntu. Secondly, Ubuntu will run slower on a Wubi install. Thirdly, you can't remove or reinstall Windows without also removing Ubuntu.

Fourthly, and most importantly, if Windows fails to start or fails to shut down, this also locks you out of your Ubuntu until you start up and shut down Windows again (it's a technical problem with the way Wubi works). Of course, if your Windows is utterly hosed and unfixable, you've also just lost your Ubuntu.

I recommend backing up your data, booting up your computer from the Ubuntu CD, and installing Ubuntu that way. It repartitions your drive (it asks you how much space you want for Ubuntu) so Ubuntu becomes independent from Windows.

---

### Post by ctdahle on 2009-12-06
I've been very happy switching over to Ubuntu. I was initially worried about "will my programs work" but I realized that the way programs work under Windows was a large part of my frustration. There are open source programs that do everything I was previously doing with proprietary software.

I have a houseful, and a classroom full of computers and the cost of keeping them upgraded and running consistently on windows was starting to kill me.

Setting up to dual boot with Windows was easy just following the prompts from the install routine...however, you have to have sufficient free space on your hard drive to begin with.

Open office handles all of my legacy word documents and excel spreadsheets and I find both programs easy to use and more intuitive than the comparable MS products. I routinely create Open Office documents at home and email them to work where I have no problem sharing them with colleagues.

I have had a few small annoyances, one with sound, that the folks here helped me solve, and one with internet connectivity that the people here are helping me with right now.

I'm now adding Ubuntu partitions to every computer in the house...except for my wife's because hers is owned by her office and they won't allow it.

At school, I am resurrecting old computers donated by businesses and parents and am finding that I can run remarkably outdated machines on Ubuntu or Edubuntu. The oldest is a 12 year old celeron machine, originally shipped with win-98.

Ubuntu had no problem communicating with the cheap D-Link printserver that runs my ancient HP LJ IIP  (which could NOT print from Windows 7). Ubuntu also had no problem finding my new printer, an HP Office Jet 6500 which I bought because W-7 apps couldn't run the LJ-IIP

Now that I am using Ubuntu, I have had almost no reason to boot into Windows since, and I now have enough confidence in Linux, and my own ability to figure it out that I am ordering a couple of "bare bones" kits so that I can build new, fast machines for my two kids.

---

### Post by ronnielsen1 on 2010-04-04
> If it's Hotmail or some Microsoft Exchange email and you intend to use an email client, then, no not at all or not perfectly. Otherwise, yes.

I've used Hotmail for years (Before MS bought it) in the classic style. I haven't had much trouble

---

