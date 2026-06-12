---
title: "How to get to &quot;know&quot; kubuntu - like you get to &quot;know&quot; linux?"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Istrebitel on 2010-06-07
Greetings!

I suppose maybe my question has no answer, but here it is:
How do you get to understand the Ubuntu (Kubuntu i am using now) in the way you do get to understand linux? You see, linux always attracted me with its simplicity. Simplicity not in the GUI (windows-like simplicity, a fat ugly monster with a nice gui) but in the core. Absolute control over the system, absolute ease of access to any settings (everything is a file - i LOVE IT!) and absolute transparency of "whats going under the hood". 

I've read books in past and reading now and i'm getting to understand how linux works, why it does what and how to solve any problem that can arise. 

But for Kubuntu, this is not so. Kubuntu is hard to understand. 

Is there a book on Kubuntu like analog of this for linux? [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

Or some manual that will answer or teach to get answers on:

1) Why did they broke root account and changed sudo?
2) Why does sudo (something gui like) should not work?
3) Why does this application autoruns if its not in autostart?
4) Where does this application store its configs so i can tweak them manually?
5) Why is this not remembering my settings?
etc. I mean, regular questions related to the inner working of the system that could ease changing or tweaking or solving problems that forum cant help me with?

---

### Post by jarviser on 2010-06-07
Why not install Ubuntu 10.4 and look for a book like Ubuntu Unleashed (2010 edition) although it does include a section on KDE I believe.

---

### Post by arochester on 2010-06-07
Obviously jarviser doesn't like Kubuntu - which is officially issued by Canonical.

You would be very welcome to ask your questions on (the non Canonical) Kubuntu Forums - Help the New Guy - [http://kubuntuforums.net/forums/index.php?board=7.0](http://kubuntuforums.net/forums/index.php?board=7.0)

Also have a look at the UNOFFICIAL Kubuntu Guide - [http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid)

---

### Post by jarviser on 2010-06-07
> **arochester said:**
> Obviously jarviser doesn't like Kubuntu - which is officially issued by Canonical.


Not that I don't like it - just that for a beginner (this is Absolute beginner section)  it's probably better to go mainstream and Gnome (or even Mint) than KDE which is a bit spartan for a beginner.

---

### Post by Istrebitel on 2010-06-08
I understand. 

Guides and forums you suggested take the approach "you do this like this, you do this like this", problem-solution approach.

What i was asking is the approach "over linux kernel, this os includes the following" and then "this WORKS like this, this WORKS like this", explanatory guide that can help me understand the OS, not learn how to use it. I suppose you get the difference.

---

### Post by sourchier on 2010-06-08
There is a wiki guide here:

[http://kubuntuguide.org/Lucid]("http://kubuntuguide.org/Lucid")

There is also forum support here:

[http://www.kubuntuforums.net/forums/index.php]("http://www.kubuntuforums.net/forums/index.php")

Is that all that you are looking for?

---

### Post by Nick_Jinn on 2010-06-08
I dont see anything wrong with putting fine cloths on a nice body (GUI). The two together work great, though its nice to be functional either way....sometimes its nicer to wear shoes and more comfortable if you have a jacket, though nude is also nice :)
Metaphors.

Windows is a scam in my opinion. They create problems and sell you the solution. When you create an artificial need to make money, i call that a scam, rather than developers getting paid for honest work.....not that honest work isnt done for windows, but some of it is a scam. 


I think its nice to have a comfortable GUI that is intuitive for point and click begginers...the idea of 'You already know how to use it' is a good approach for developers to take....rather than 'you already know how to use it if you can hack any system or already have'.


But a good OS with capture your attention and lure you into WANTING to go deeper than that functional baseline....people spend years on Windows and never get beyond point and click. Its too comfortable and there is no incentive. I think a good balance would be if the very basics were so simple and pretty that anyone without practice would already know how to do it by looking at it (graphical), and yet the options to go deeper are right in front of you tempting you to go forward....and when you get there, its easier than you think, and before you know it you are customizing your desktop and setting preferences that you didnt even know existed and you actually understand what they are because its not at all cryptic. 

I think its possibly a hard balance to walk, but i think it can be done.

---

### Post by Istrebitel on 2010-06-08
2 Nick_Jinn
> Windows is a scam in my opinion. They create problems and sell you the solution. When you create an artificial need to make money, i call that a scam, rather than developers getting paid for honest work.....not that honest work isnt done for windows, but some of it is a scam. 
I 100% agree with you. I mostly take that further, i very often think of alot of current marketing as a scam. Although they dont create problems for you, they make you think you have a problem that has to be solved. They tell you like "did you know <something>? Now you know it, and you urgently need <another something>! We are here to save you, because we offer you this anotehr something at very good price!"
Example: Here in Russia a company producing cleaning chemistry for household called Domestos made a new product - "Domestos that kills flying microbes". And they advertise like "Did you know that even after you clean with ur regular cleaning compound, the flying microbes are out there, waiting to infect you with salmonella, gastritus and various bad stuff. Buy Domestos to protect your house from flying microbes". 
I start to think - where were those flying microbes before Domestos started making that new product? Did we all suffer from all those diseases in the past years? How come those microbes suddenly appear and threaten us right now? Did Domestos probably spread them beforehead?

And my point in my post was "how do i learn system's internals?"

Like, my experience in windows tells me that if something persists through reboot, i have to look in autorun, then in registry (current version-run) then run msconfig and check if its there, then check servies, then check if another program lauches it, then start looking for rootkits or driver-based viruses... I learned that a long way, part by part, fighting viruses or reading internets, talking to specialists or working. 

I dont want to spend 10 years to learn Ubuntu! Thats what i'm talking about. I'm looking for some guide that can teach you advanced using, internals of a system, probably a book or series of books or a number of books. Faster way than getting to it myself through trial and error and forum asking.

---

### Post by ankspo71 on 2010-06-08
> **Istrebitel said:**
> 
Or some manual that will answer or teach to get answers on:

1) Why did they broke root account and changed sudo?
2) Why does sudo (something gui like) should not work?
3) Why does this application autoruns if its not in autostart?
4) Where does this application store its configs so i can tweak them manually?
5) Why is this not remembering my settings?
etc. I mean, regular questions related to the inner working of the system that could ease changing or tweaking or solving problems that forum cant help me with?

1) Sudo in Kubuntu is almost the same as sudo in Ubuntu, except we use kdesudo instead for graphical applications. The actual root account is disabled for security reasons. If the root account is enabled, and if I log into it, I could easily accidentally destroy my linux system, or I will accidentally allow malware and hackers to ruin it for me.

2) because if we open a graphical application with sudo and something changes within the graphical application, it will make those changes as root and cause permissions problems for that graphical application or user account. Using kdesudo (in kubuntu) and gksudo (in Ubuntu) prevents this from happening because it opens the application graphically as a normal user (using the user's settings) but allows that graphical application to make other changes to the system (but not changes to itself). There is more to it than that, look at this link: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

3) Look for a application called "Service Manager" somewhere in your system settings. I don't think KDE 4.4.3 has this application yet, but I'm using KDE 4.4.8 (aka kde 4.5 beta 1) and it is there and looks very useful. (see screenshot). It might be possible to get it installed in Kubuntu 10.04, but I don't know the package name. Many of these services are in are located in /etc/init and /etc/init.d . [https://help.ubuntu.com/community/InitScriptList](https://help.ubuntu.com/community/InitScriptList) and [https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto) (this is unexplored territory for me, but I think there are commands that need to be run to enable and disable init scripts). Search google for **ubuntu init** for more documentation. *_Correction: Kubuntu 10.04 does have the Service Manager by default. It is located in the advanced tab of the System Settings. I booted into my live cd to find out because I couldn't remember seeing it or not._*

4) Most user configurations are stored in a hidden folder the user's home folder. For KDE applications, look in /home/<user>/.kde/share/*** . You will find alot of things in there. Most system wide kde settings should be stored in /usr/share/kde4/***  Ubuntu and non kde applications stores the configurations in different folders.

5) I don't know. I used to have problems with Kubuntu not remembering my display size settings. Forgetfulness isn't only a problem with KDE though because  Ubuntu used to forget my volume settings at one time too. I think these are bugs that happen to a few of us once in a while.

Hope these help.

---

### Post by gdonwallace on 2010-06-08
Another good way to learn Linux and by default Ubuntu is find a users guide for Debian or for GNU/LINUX.  Debian is the foundation on which Ubuntu is built.  So anything you can learn about Debian should work with Ubuntu.

Just like Windows, it just takes time.  You have to mess around with it.  Reading the forums is a good place to start, as well as the sticky in the beginners thread "Beginners guide to Ubuntu".

If you can find them, there are several PDF's available specifically about Ubuntu.  I would recommend "The Ubuntu Desktop Study Guide", or "The Ubuntu Pocket Reference".  Also another good one is "Pocket Linux Guide"  There is also a guide to Karmic Koala, but that is a little hard to find sometimes.  The website [www.distrowatch.com](www.distrowatch.com) has links to download most of these.  For more advanced there is the "GNU/LINUX Advanced Admin" guide.  

It just takes time and little playing around with it to get the knowledge you want.

---

### Post by LowSky on 2010-06-08
> **Istrebitel said:**
> 
1) Why did they broke root account and changed sudo?
2) Why does sudo (something gui like) should not work?
3) Why does this application autoruns if its not in autostart?
4) Where does this application store its configs so i can tweak them manually?
5) Why is this not remembering my settings?


1) root isn't broken, it is disable by default. The consensus among most Linux users, Sudo is a much better idea when you use a GUI based version of a Linux based operating system. This way the user is less likely to corrupt a setting.
2) Sorry I don't understand the question
3) Depending on the Distrobution of Linux this file can be in other place, for Ubuntu, it is /etc/rc2.d 
4) Which application? KDE? What do you wish to tweak?
5)What is not remembering your settings?

---

### Post by Istrebitel on 2010-06-09
2LowSky, 
the point was i was looking for a way to learn how to answer my questions! Not that i seek particular answers. I see now that q1 and q2 had an answer but the point was, i wasnt looking for answers, but a way to answer them. Not the fish, but the fishing pole.

For example,
4)
I want to be able to find where ANY application i just know the name of stores its configs.

Windows example: if i want to find where application stores its configs, i would look in:
a) registry under software/manufacturer/appname
b) application-rleated folders in my user folder, looking for app name
c) application folder
d) google "where does ***.exe stores its settings"
e) search registry for app name
f) change something in the application, then search for files that have changed recently on my pc
etc

I want to be able to do something like that in linux. Not rely solely on asking forums for someone who stumbled upon same task and found answer, but get the philosophy, get the tendency, get how it's done in linux, so i can solve problems myself.

What i am looking for is a guide that lets you study system's internals. Because otherwise you can only be a slave of manuals and forums. And you will "get" it only after years of working with the system, when similarities will become clear to you.

Thanks to gdonwallace for guide names i will check them out.

Thanks to ankspo71 for trying to answer. I almost got it with graphical sudo. 
If i sudo appname, then appname has root owner and can access files at root access level, right?
If i graphicsudo appname, then appname has my_user owner... but how does it then accesses files that my user has no access to?
Does it run a setuid process that then accesses files for it? If it does - what prevents appname without graphicsudo to run same setuid process? I dont understand the mechanism of root elevation in this case. 
> kdesudo kate
kate is not ran as root, but as my_user
now how does kate write to a file that is chmod 0700 and owned by root root?

---

### Post by ankspo71 on 2010-06-09
Hi Again,
I wasn't sure if I wrote my last reply in the best way possible so I'll try again. 
Gksudo and kdesudo will use the current user's application settings rather than use root's application settings, thus preventing sudo from writing root permissions to the user's application settings or other settings in the user's home folder (or write current user permissions in system directories). 95% of the time using a graphical application with sudo safe to do, but the other 5% of the time it could lock up the application (or an entire user account, it has been said) by applying root permissions to files and folders where the user's permissions are supposed belong (and vice versa). In other words... sudo doesn't know that a regular user is running the application, because it always assumes sudo 'equals root user', so we have to tell it "hey I'm a regular user, don't lock me out" by using gksudo or kdesudo. ;)
Hope that clears it up a bit more.

---

### Post by Istrebitel on 2010-06-09
I see, so if i understand that correctly, the program ran by sudo can make its config files owned by root (instead of my user) and subsequent launch will only be possible with sudo because without sudo it wont be able to access config file? 

Okay i've experimented with ps and i see that both sudo and gksudo are running program as root. Do you know it more specific how does it work that program is told to use user settings instead of root's? I mean how exactly does it happen.

---

### Post by QIII on 2010-06-09
Just as an aside...

When you are starting to get into the nitty gritty, you are inevitably  going to break something.  Count on it.  Sometimes you may want to break  something just to find out what happens and how to avoid or correct the  problem you just created.  ("Destructive testing" in engineering  parlance.)

 Nothing worse than an "Aw, crap!" with your daily-use machine.

It would not be unwise to dual boot and have one production version you  don't fool with and another you can break and fix at your leisure.   That, or drag an old POS clunker out of the garage and do your tinkering  on that machine.

---

### Post by ankspo71 on 2010-06-09
Hi,
I don't have any examples, but this Ubuntu documentation shows an example of how it prevents problems:
[https://help.ubuntu.com/community/RootSudo#Graphical%20sudo](https://help.ubuntu.com/community/RootSudo#Graphical%20sudo)
The above example is for Xauthority

An example of breakage is ICEauthority, as seen here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Here's a man page with a brief description on gksudo
[http://linux.die.net/man/1/gksudo](http://linux.die.net/man/1/gksudo)

I think I locked up my gvfs once (it couldn't be stat'ed if I remember right) after using nautilus as root (sudo). That was a long time ago though.

PS. Permission problems can end up being a very bad thing, and in some cases it might not be easily recoverable. It's best to stick to gksudo/kdesudo.

---

### Post by Istrebitel on 2010-06-10
I see. All that happens (As far as community page author knows) is that it moves files to emulate environment. Okay i see it. Thanks again :)

I understand about breakage. I record every successfull change to the system and i have home on separate partition. If i break this system i'll install from scratch and apply changes i did (i hope i wont destroy /home...) Also i followed advice and partitioned extra 10gb of space for experimental system, so i can install new linuxthere and tell it to be mount as root instead of my current root, therefore i can always roll back to the old one.

---

### Post by jarviser on 2010-06-10
> **Istrebitel said:**
> 

... (i hope i wont destroy /home...)....

Obviously back up the /home directory including hidden (.) files (Ctrl-H when viewing), 

but also select the manual partitioning option on install, and when you tell it to mount the partition to /home make sure the Format box is NOT checked and select the same filesystem (ext3 or 4 ) as currently in use.

For a VERY clean reinstall I delete all my hidden files and folders in /home just before reinstall. That's radical suggestion and many would say that loses the configurations, but sometimes that is what is messing with the settings.

When getting to know a new distro I usually re-install like this at least twice after playing around with settings. (3rd time's lucky)

---

