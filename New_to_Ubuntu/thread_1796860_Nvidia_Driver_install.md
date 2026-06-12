---
title: "Nvidia Driver install"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by littletime on 2011-07-04
OK.  I feel like a bit of an idiot.  I found and downloaded the drivers I need from nvidia.  I tried double clicking on them to install them and Ubuntu says it can open the file because it cant find the right decoder.  I strongly suspect there is a command line method of install required but I know so little about Ubunto I cant begin to figure out what it is.  Can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2011-07-04
to install the driver that way yuo have to to it from a tty hte installer run with sh
ex sudo sh ~/Downloads/*275.09.07.run but fisrt you will have to close the desktop sudo service gdm stop also yuo will need to disable the current drive using nomodeset at the boot line google for details you have the keywords you need
if you take this method you will have to reinstall the driver after every kernel update
you can install the driver from system->administration->hardware drivers easily
or [alt]+[f2] [FONT=Courier New]/usr/bin/jockey-gtk[/FONT]
depending on yuor version of ubuntu you may want to add the xswap ppa (google that) and run sudo apt-get install nvidia-current

---

### Post by littletime on 2011-07-04
OK.  The vast majority of that went straight over my head.  Can anyone recommend a good book for starting out???  I need to get the drivers installed, set up a swap file and reset the CPU fan speed.  The bios seems to think its a helicopter and needs more lift. 

The other thing I want to be able to do is install win 7 as a virtual machine.   Any book that can cover those things and get me some background on this would be great.  All I need is a good title.  I know there are a ton listed on the sticky, I was just wondering which would be the best to start out with.  And was hoping someone had a favorite or a suggestion.

I have a strong background in hardware and windows.  Did some programming when I was younger.  I pick things up quick, but don't know the terminology on this forum and thus am having a hard time understanding the vast majority of what is being said.  Hell I even had to look up what trolling meant (I saw it in another thread while waiting for someone to respond to mine).  I am trying but I am just too lost.

---

### Post by wildmanne39 on 2011-07-04
> **littletime said:**
> OK.  The vast majority of that went straight over my head.  Can anyone recommend a good book for starting out???  I need to get the drivers installed, set up a swap file and reset the CPU fan speed.  The bios seems to think its a helicopter and needs more lift. 

The other thing I want to be able to do is install win 7 as a virtual machine.   Any book that can cover those things and get me some background on this would be great.  All I need is a good title.  I know there are a ton listed on the sticky, I was just wondering which would be the best to start out with.  And was hoping someone had a favorite or a suggestion.

I have a strong background in hardware and windows.  Did some programming when I was younger.  I pick things up quick, but don't know the terminology on this forum and thus am having a hard time understanding the vast majority of what is being said.  Hell I even had to look up what trolling meant (I saw it in another thread while waiting for someone to respond to mine).  I am trying but I am just too lost.Hi, here are the instructions for installing your driver that I gave you on the other thread last night it should work and is the preferred method, if it does not let us know.
> To get the driver for your video card hit alt+f2 and in the window that opens type additional drivers and it will show you the icon click on it and install the one that is there for your card, you will need to be connected to the internet.


---

### Post by littletime on 2011-07-04
OK.  I am a little confused.  I was also told in the other thread that the open source driver would not work because there were dual cards linked via SLI and that the proprietary driver was likely the way to go.  I thought that meant I needed to find the proprietary driver.  Will try the way you have here first and see what happens.  Just was afraid things could get worse.  I at least have one screen working and don't want to lose that.

---

### Post by littletime on 2011-07-04
I tried typing additional drivers into that screen, this is what it gave me:

Could not open location 'file:///home/shy/additional%20drivers'
Error stating file '/home/shy/additional drivers': No such file or directory

---

### Post by rosencrantz on 2011-07-04
Well, there are two ways to install additional drivers on Ubuntu. 
1) the hard way. Download the drivers from the Nvidia homepage, open a terminal, navigate to your download directory and type
sh driver_filename (substitute appropriately). Follow terminal instructions from here.
2) the easy way, as suggested by wildmann: Ubuntu has a driver wizard that should find the appropriate proprietary drivers and do the install automatically. You should find it under Main Menu->System->Administration->Additional Drivers. I couldn't find it with the Alt+F2 runner either.

---

### Post by littletime on 2011-07-04
Cool.  Found it through the menu string.  For some reason the shortcut doesn't work.  I installed this for the first time last night, so I don't have a clue what the menu screens are yet.  Given time I will get it.  Installing it now.  Wish me luck.

---

### Post by littletime on 2011-07-04
That changed the layout of my screen.  Now have a sidebar and the menus I just learned changed, but still can't detect the other monitors.  I know in windows I need two copies of the driver installed (that's windows for you).  Trying the other version of the driver now to see if that works.

---

### Post by littletime on 2011-07-04
No luck.  Still only can get one monitor recognized.  Any ideas???

---

### Post by rosencrantz on 2011-07-04
Have you tried nvidia-xconfig from a terminal, as suggested here?
> **MantinoX said:**
> K i know what i did wrong had to spell config out. so it should be 
```
sudo nvidia-xconfig --sli=On
```

---

### Post by jramshu on 2011-07-04
Since you have the propriety drivers there should be a nvidia configuration program. I use 10.10 so I'm not sure exactly where to tell you to look for it in 11.04. In there it will have the additional monitor options and such.

---

### Post by gordintoronto on 2011-07-04
It might be useful if you mentioned what video card(s?) you have on your computer, and what monitor(s?).

---

### Post by jramshu on 2011-07-04
From the OP's first thread. Not sure on screens.
> The video cards are two Nvidia GeForce 9600GTs linked via SLI.

---

### Post by littletime on 2011-07-04
Screens two LG 21 inch and a Samsung 24 inch (with TV input if that matters).  I am cool with getting just two of them going directly under Ubuntu if I can make the 24 inch one of them.  I like watching netflix on it.  If I need all three I can go into windows.  May have to do most of my work in there anyway, because I think the two offices (Microsoft versus open source) tend to change formating when a file switches hands.

Will look for the nvida program.

When you type in a command and hit enter is something supposed to happen other than the command prompt pop up disappearing?

---

### Post by littletime on 2011-07-04
I found the nvidia x server settings program under installed programs and added the samsung on twin view.  When I hit accept changes the computer froze.  Been waiting to see if it's a temporary thing, but I get the vibe I am going to have kick the computer in the power button to get anything done.

---

### Post by jramshu on 2011-07-04
I found this thread that may help.

[http://ubuntuforums.org/showthread.php?t=1741962](http://ubuntuforums.org/showthread.php?t=1741962)

---

### Post by littletime on 2011-07-04
Go crash.  I tried save setting / configuration (not sure exact word), and restarted the computer.  It would not start up.  So I tried starting in recovery mode and reset graphics settings.  I had it create a new one since it would not let me restore from backup (likely because it does not exist).  It comes up with a fail on starting to load fallback graphics driver.  The last message line says stopping userspace bootsplash.

And then there was just a cursor......

Help????

---

### Post by littletime on 2011-07-04
I think there are a few things in that thread I could try.  Just need to get back in.  Going to try recovery mode again.  Ok I am in.  Now to see if I can reverse the crash and not crash it further.

Tried uninstalling nvidea program and reinstalling but the same programs don't show up.  Not sure what to do at this point.  Am thinking of starting fresh and trying the instructions on that other thread.  Any other suggestions??? 

I am going to head to the bookstore and pick up a reference on this.  If you think of anything in the next hour or so it probably won't be too late to try it. 

I figure I will keep trying and taking notes until I hit the right set of variables.  Then I might post it under a title that will make it easier for the next person to find.

---

### Post by maizuddin35 on 2011-07-04
you use Ubuntu 11.04, and I think you should try going to the 'Display' 
you just need to open the "Search" bar by hit the "windows"key on your keyboard and type display,, there you can see "monitors" try to check it out..im not really sure , if this is working or not, but I dual monitor with my laptop by doing that..

---

### Post by littletime on 2011-07-04
Any other way to open that search bar.  Windows key does nothing when I press it.  I am set to international keyboard FYI.  In case that matters.  I did a reinstall and am doing a little more research before trying my next shot at this.

Anyone know how to make it so I can rollback changes?  It would make this process easier.

---

### Post by maizuddin35 on 2011-07-04
I mean , by going to the upper left part . are using ubunt 11.04 with the side bar on the left?

when you click the "ubuntu" button on the upper left part , you will see "search" "media " etc...

---

### Post by littletime on 2011-07-04
Yeah... no side bar back yet.  It only came in after the nvidia install and went out with the last crash.  Been trying to figure out how to view the xorg file.  Want to see what it says before I start making changes again.

---

### Post by maizuddin35 on 2011-07-04
why wont you just install/download the nvidia card driver via the "additional driver"?

If you already download the nvidia driver via the website, does the installation end up successful?

---

### Post by maizuddin35 on 2011-07-04
check out this link...[http://askubuntu.com/questions/43895/how-do-i-install-the-nvidia-driver-for-a-geforce-9300m]("http://askubuntu.com/questions/43895/how-do-i-install-the-nvidia-driver-for-a-geforce-9300m")

and this

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html]("http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html")

try to look at the first link first.

---

### Post by littletime on 2011-07-04
Cool.  More ways to do this.  I still want to look at the xorg.conf file before altering it.  I also just need to figure out how to look at files if I am going to be able to follow half of these methods.  I don't know hardly any commands or what the ones I have used even mean.  That's what I am looking at now.  FYI I installed this for the first time last night.  I am as newbie to this as one can get.  The terminology is killing me.

---

### Post by maizuddin35 on 2011-07-04
I understand the way you are feeling right now,when my first time installing ubuntu on my computer. it just matter of time, you gonna learn this thing...

okey,if you want to see the xorg, 
i think this is the one..open your terminal...and type this...
```
 sudo gedit /etc/X11/xorg.conf
```

sudo , means run with root (sort of like that)
gedit, is one of the text editor in ubuntu.
/etc/X11/, is the address directory where the xorg.conf situated in.

---

### Post by littletime on 2011-07-04
Thanks.  I have been sitting here fighting back tears.  I got a book that is supposed to help but its missing the one thing I need the most.  Basic commands and what they mean.  I got it to run in terminal.... but it comes up blank.  Any ideas???  

If it helps at this point I have made no real changes.  Hell most of the commands I have typed have been seemingly ignored.  Nothing happens the run screen just disappears when I hit enter.

---

### Post by maizuddin35 on 2011-07-04
when you enter the command that I just told you too..

the terminal need to acquire your passowrd, when you type your password, you wont see a thing, but you just write like normal only.

or...
```
gksu gedit /etc/X11/xorg.conf
```

by the way...have you already update and upgrade your ubuntu system?

if you have not made the update and upgrade yet, I think you should..

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by littletime on 2011-07-05
I crashed it pretty hard a couple of hours ago and just did a reinstall.  I have literally not done anything to it (successfully anyway). 

Been on here and looking up stuff in the book and on google on my laptop.  Trying to get a better feel for what I am doing before proceeding.  I have tried a few commands that were supposed to help me enable  search bar, but noting ever happened.  I still have not even installed the nvidia drivers again.  I know last time after I crashed it I could not find the ones that worked to roll back to.... hence the reinstall.

---

### Post by maizuddin35 on 2011-07-05
if you just done installing it again,means that, you just need to do update and upgrade , just do the command sudo apt-get update && sudo apt-get upgrade. after all have been update and upgrade, reboot, and try to check out at the "Additional Drivers" to see if there is your driver list in there.

---

### Post by littletime on 2011-07-05
I installed the nvidia driver before I got your last response.  Now when I go to the command line it no longer has the tick box for run in terminal.  I entered the command but nothing happens.  I think it needs a password, and so far the only way I have gotten it to prompt for that was to run in terminal.  I got the sidebar back though.

OK.  forget it.  I found the terminal under applications and just typed it directly in there.  Its working on it right now.

---

### Post by maizuddin35 on 2011-07-05
when you put in the command with sudo , you need to enter the password .is it like this? this one is just an example,copied from my terminal.
```
utm@utm-hp-notebook:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for utm: 

```

and you just enter your password in, it will not show you this *** or your password in words..

if you had already your sidebar, does this means, that your driver is updated? and installed?now im confuse...XD

---

### Post by wildmanne39 on 2011-07-05
> **littletime said:**
> I installed the nvidia driver before I got your last response.  Now when I go to the command line it no longer has the tick box for run in terminal.  I entered the command but nothing happens.  I think it needs a password, and so far the only way I have gotten it to prompt for that was to run in terminal.  I got the sidebar back though.

OK.  forget it.  I found the terminal under applications and just typed it directly in there.  Its working on it right now.
Hi, sorry I have been out the last four hours, here is a guide to set up dual monitors.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
and you have to create the file xorg.conf in /etc/X11

---

### Post by maizuddin35 on 2011-07-05
when you put in the command with sudo , you need to enter the password .is it like this? this one is just an example,copied from my terminal.
```
utm@utm-hp-notebook:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for utm: 

```

and you just enter your password in, it will not show you this *** or your password in words..

if you had already your sidebar, does this means, that your driver is updated? and installed?now im confuse...XD

---

### Post by littletime on 2011-07-05
I was just hitting alt+F2 and running stuff from there.  I had not found the terminal at that point.  There was a check box that said run in terminal.  I tried it once and noticed that it seemed to work.  After I installed the nvidia driver that went away but the sidebar came up.  When I tried the alt F@ run command, it did not work.  So I found the terminal in applications and ran it that way.  It worked.  Now I need to go back and follow the rest of the path to get this working right. 

Its a bit tricky because its three screens on two cards linked via SLI.  I wish the computer was not so advanced right now but it was a figurative middle finger to my buddies who kept tricking me into showing up to build gaming computers for them by simply asking if I wanted to come over for lunch without telling me what was going on.

So I out built all of them when I got my tax money, and made it a point not to install a single game on it.  Its been great for data analysis.  Problem is windows doesn't like it.  Its got bugs in that system, so I figured I would try this.  My past experience with Mepis linux and reports I have gotten from those who use it made me think that once I got it right I could pretty much just leave it alone instead of having to do a reinstall every semester to clean it out and speed it back up.  Since I wont have as much of a break between semesters in medical school, I am going for it.  I intend to mirror the setup when I am done.  I also have been taking notes in case I ever have to do this again.

Yeah I installed the driver before the update.  It was in progress when I got your second message.

---

### Post by maizuddin35 on 2011-07-05
> I was just hitting alt+F2 and running stuff from there. I had not found the terminal at that point. There was a check box that said run in terminal. I tried it once and noticed that it seemed to work

you can Ctrl+Alt+T to run up the terminal , you know...

> Yeah I installed the driver before the update. It was in progress when I got your second message.


Okey, I get that..

as for three monitor on one graphic card driver is just the thing that I want to do later when I have the bucks to get a new graphic card and a monitor more. :) three monitor, is just something , wow, for me. 

It is good to know, that you putting up the spirit to learn ubuntu and configure it by yourself ;)

---

### Post by littletime on 2011-07-05
Thanks.  Its two video cards by the way.  Could not find a single card that would run three.  

Question for you.  I have to modify grub.  I am using pico to do it and it says to run grub-update when done to save the changes.  I tried doing it from the screen grub was in (pico I guess... opened from terminal and looked a lot like terminal), but that did not fly.  So I opened another instance of the terminal and ran it from there but when I type 

sudo pico /etc/default/grub

my changes don't show up.  How do I get them to save???  Forget it, figured it out.

---

### Post by littletime on 2011-07-05
Calling it a night for now.  I got the system to recognize both GPUs and they show up when I query the cards.  But when I tell it to turn on SLI it gives me the error
data incomplete in file "etc/X11/xorg.conf" device section default device must have a driver line.  I know I saw this in one of the threads, but will have to go back and find it.  I am getting close.... I can feel it.  Will post it from beginning to end when done.

---

### Post by maizuddin35 on 2011-07-05
> **littletime said:**
> Thanks.  Its two video cards by the way.  Could not find a single card that would run three.  

Question for you.  I have to modify grub.  I am using pico to do it and it says to run grub-update when done to save the changes.  I tried doing it from the screen grub was in (pico I guess... opened from terminal and looked a lot like terminal), but that did not fly.  So I opened another instance of the terminal and ran it from there but when I type 

sudo pico /etc/default/grub

my changes don't show up.  How do I get them to save???  Forget it, figured it out.

I suggest you to use nano or vim or gedit, much more easier. I think ,why there is no changes is because, maybe , you don't save the file .I'm not sure with pico, but I prefer vim, nano, or just the simple text editor that is gedit.

---

