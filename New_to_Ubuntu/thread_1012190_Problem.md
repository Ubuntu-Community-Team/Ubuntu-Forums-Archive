---
title: "Problem"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Nemix on 2008-12-15
Having issues with a game called Wolfenstein: Enemy Territory, ive placed a similar thread before but i got different questions now.

-i was messing around with the game trying to fix a problem i had with it, now when i go onto it i get a black screen and my monitor saying "Out of Frequency" so then i tried using 
```
cd /usr/local/games
sudo rm -rf enemy-territory
```
and it got rid of the enemy-territory file, so i thought id just reinstall and my prob should have gone away...but it didnt still black screen. 
I did some research and found out that there is a config file attached to programs that you install and i should use this:
```
sudo apt-get remove --purge
```
but i dont know how to use that command properly comes up with 

sudo apt-get remove --purge enemy-territory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package enemy-territory

-lol this is the problem i was trying to fix when i messed up and got the first problem =P
When i had the game working, i started it up but i had some of the game hanging off the screen (bottom). Wolf:ET is very temperamental when it comes to full screen and windows... so when im in the game its set to full screen and abit of its hanging off and its not really full screen, its more like in a window (so i can still see the desktop but cant move my mouse to the desktop)
i was told to use
```
metacity --replace
```

which would turn off compiz, but i still got the same issue...bottom of the game is off the bottom of the screen. 

any help would be great, ive tried fixing it my self but only been using Linux for 3 days now and had to reinstall it few times cos i screwed up =P

Oh and how i got the first problem was while the game was starting up i moved the window which the game was in(while the game is starting i have about 3 sec where i can still move my cursor on the desktop) and when i released the mouse is jumped off the screen, i could only see a bit off it on the left side of my screen. Then i pressed ctrl Alt backspace, to restart and then when i went to the game again it went black like i said =D

feels like i never used a comp before now that im on Ubuntu so use to how Windows works.

-----------------------
this is more of a programming question:
i was learning C++ on windows and i know Linux uses different libraries and all. I was given this to get some of the files i need:
```
sudo apt-get install build-essential
```
which would give headers and libraries but how do i open gcc and g++, its not in the menus so i take it i need to use terminal to access them.



Again thanks for your time i know ive asked allot here and sorry for being so clueless :lolflag:

---

### Post by Nemix on 2008-12-15
any1 please??

---

### Post by markharding557 on 2008-12-15
try the win version on wine

---

### Post by Tatty on 2008-12-15
With regard to compiling software, gcc and g++ are command line applications.  You compile by passing them arguments on the command line.  Have a read of this: [http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html](http://pages.cs.wisc.edu/~beechung/ref/gcc-intro.html)

There are several graphical development environments available in the repos, which can make organising and compiling your projects easier.  However I am only an amateur at such things, so I cannot really compare them or reccommend one for you.

How did you install this game?  If you followed some instructions then providing a link to them will help figure out where you are at.

apt-get --purge will only work if you installed via synaptic, or installed via a .deb and had the package added to synaptic.

There may be a hidden folder for the game in /home which may have a configuration file in it.  Have a look, if you see something that looks like a configuration file then try deleting it and see if it regenerates it.

---

### Post by Nemix on 2008-12-15
thank you for your replies:KS

the link for the guide which i used is here: [http://gaming.gwos.org/doku.php/guides:32bit:et_wolfenstein#enemy_territory_wolfenstein]("http://gaming.gwos.org/doku.php/guides:32bit:et_wolfenstein#enemy_territory_wolfenstein")

ill have a read that link.

---

### Post by Tatty on 2008-12-15
Sounds like others are struggling to uninstall the game too:
[http://www.linuxforums.org/forum/suse-linux-help/52589-uninstalling-wolfenstein.html](http://www.linuxforums.org/forum/suse-linux-help/52589-uninstalling-wolfenstein.html)

It sounds like you deleted the right directory, so it sounds more likely that there is a hidden directory in /home which has the config files. ctrl+h in nautilus will show hidden files and folders.

---

### Post by Nemix on 2008-12-15
whats nautilus?? 
i still dont know alot of things =P

---

### Post by Tatty on 2008-12-15
> **Nemix said:**
> whats nautilus?? 
i still dont know alot of things =P

Sorry, Nautilus is the name of the default file browser in ubuntu.

---

### Post by Nemix on 2008-12-15
oh i see now i can see all these file like .<name>
and a file named .etwolf

i went and deleted a file which hold player infomation within the game and that set the game back to default settings. It seems that resolutions is an issue some resolutions will work and some wont. Just wondering if there is a way to tell Ubuntu to open the game in a certain resolution? It seems Ubuntu makes the game too narrow.  

some questions nothing to do with my general problems just trying to figure out how it all works.
may i ask what is the function of these files (thses .<name> files i can see now)?? i mean why are they there?

Also what are these files in /usr/local/bin they have the same name as the two .exe or x86 for linux files, went into properties and it says "Link to shell script (application/x-shellscript)" what is the purpose of these files?

---

### Post by Tatty on 2008-12-15
> **Nemix said:**
> oh i see now i can see all these file like .<name>
and a file named .etwolf

i went and deleted a file which hold player infomation within the game and that set the game back to default settings. It seems that resolutions is an issue some resolutions will work and some wont. Just wondering if there is a way to tell Ubuntu to open the game in a certain resolution? It seems Ubuntu makes the game too narrow.
I would have thought those settings should be made in the game itself?

> **Nemix said:**
> some questions nothing to do with my general problems just trying to figure out how it all works.
may i ask what is the function of these files (thses .<name> files i can see now)?? i mean why are they there?
any file beginning with a "." is hidden.  This is just for convienience really, it has no real bearing on how the system treats them, they are just not shown in nautilus.

Most of those files will be configuration files for various applications.  They are stored in your /home folder for two reasons, Firstly it means each user can have their own separate settings.  Secondly if those settings were stored outside of your home folder then each application would need to be given superuser privilages each time you changed some settings.

> **Nemix said:**
> Also what are these files in /usr/local/bin they have the same name as the two .exe or x86 for linux files, went into properties and it says "Link to shell script (application/x-shellscript)" what is the purpose of these files?

Unix based filesystems are structured with a rather different philosophy than windows filesystems.  Rather than each application simply having its own directory which houses all its files, different types of files are stored in different parts of the system. 

/usr/local/bin is where the system expects to find the main executable files for non-essential applications, so it sounds like they have simply put a link in there to the executable in the directory the game is stored in.

Have a read of these links, the first is a bit lengthy but is worth it for the understanding of how your system is working:

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Nemix on 2008-12-15
dude i have to say You are awesome =D :KS:KS:KS

Yeah the game does have settings to change the resolutions but the resolutions dont get set right like if i set it to the same as my monitor it takes up like half of the screen and other resolutions will make some bits of the game off the screen.

---

### Post by Nemix on 2008-12-16
any ideas?
:confused::confused:

---

### Post by Tatty on 2008-12-16
Im afraid this now goes beyond my ubuntu knowledge.   :(

I dont play many games on my ubuntu machines so I dont have much experience in this field.

The only similar thing I have heard of has been caused by running compiz whilst trying to play games, but you say you have tried that.

---

### Post by Nemix on 2008-12-16
> **Tatty said:**
> Im afraid this now goes beyond my ubuntu knowledge.   :(

I dont play many games on my ubuntu machines so I dont have much experience in this field.

The only similar thing I have heard of has been caused by running compiz whilst trying to play games, but you say you have tried that.

ok thanks man you've been a great help :KS
im going to see if maybe wine will get it to work with a MS version

---

### Post by Tatty on 2008-12-16
I take it you get the correct screen resolution on the desktop?

Do you have the proprietry drivers installed for your card (if available)?

---

### Post by Nemix on 2008-12-16
yeah the res on my desktop is fine, im going to try and configure some of the file within the game, my video drivers are up to date.

quick question how would i check if my sound driver is working? i know that ubuntu knows about my sound card just some things i cant hear sound on.

---

