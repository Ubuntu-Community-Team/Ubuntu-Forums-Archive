---
title: "Please, please, help me fix or get rid of ubuntu."
date: 2010-09-07
forum: New to Ubuntu
---

### Post by givemewindows on 2010-09-07
bought a laptop for my girlfriend (dell inspiron 910) unaware that it came with ubuntu. I hate it. 
 
Well, right now im stuck at a command prompt (similar to dos) that says
 
user@user-laptop:~$
 
Dunno why it randomly decided to get stuck there today, wasnt doing it yesterday. 
 
 
so thats a start.. once i can get back in ill have a few more questions. 
 
Please help me fix this so i can get this mess off of here.

---

### Post by givemewindows on 2010-09-07
if there is a way to login from here, or just wipe the HD and reinstall a different version thatll work too. 
 
i was also getting a "HD is being used outside perimeters" or something similar last night.
 
i just got the computer so wiping it wont bother me, as anything that is still on it isnt mine anyway.

---

### Post by LowSky on 2010-09-07
hi and welcome to the forums.

if it boots to the command prompt, which it shouldn't do unless somehing wrong, just login with the user name, then type

```
startx
```


if you are having other issues you can call Dell for possilby  quicker support.

---

### Post by clhsharky on 2010-09-07
givemewindows

Welcome to Ubuntu forum.

Try
```
startx
```

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)


Sharky

---

### Post by Calash on 2010-09-07
What is your end goal?

If you are looking to just get rid of Ubuntu and go to Windows then you will need a Windows CD.  If one did not come with the Laptop you will need to buy one.

If you would like to learn Ubuntu we can help there.  Without knowing the state the laptop came in your best bet would be to wipe everything and start fresh.  Go to the following link and download the iso image that best fits what you need.  

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Burn it onto a CD and boot the laptop from here just reinstall, using the entire hard drive and overwriting the current partitions.  This will get you the latest version.

If you want to try and fix what you have we may be able to help too.  Tell us the type of laptop you have.

---

### Post by givemewindows on 2010-09-07
> **Calash said:**
> What is your end goal?
 
If you are looking to just get rid of Ubuntu and go to Windows then you will need a Windows CD. If one did not come with the Laptop you will need to buy one.
 
If you would like to learn Ubuntu we can help there. Without knowing the state the laptop came in your best bet would be to wipe everything and start fresh. Go to the following link and download the iso image that best fits what you need. 
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
Burn it onto a CD and boot the laptop from here just reinstall, using the entire hard drive and overwriting the current partitions. This will get you the latest version.
 
If you want to try and fix what you have we may be able to help too. Tell us the type of laptop you have.
 startx brings up
"user not aughorized to run the x server, aborting"
 
attempts to upgrade via command prompts me that there is not enough data space to complete upgrade.
 
Id like to just wipe and start over if possible, i had planned on running a cracked XP or tinyxp as its a dell mini, (8gb) and doesnt have the space for a full windows OS.. but if i can just get this to work right for now that would be fine too. 
 
like i mentioned, the HD was having an error come up "hard drive is being used outside design parameters" so wiping may help that too.

---

### Post by migs73 on 2010-09-07
If your experience of Ubuntu is what you've got on this laptop, no wonder you hate it!
IMHO I would go for a clean install of Ubuntu  (download the ISO, burn it to disk and then check the MD5 check, all instructions are on the Ubuntu pages)and give it a try properly. If you're still not liking it, [SIZE="3"]then[/SIZE] spend £70 on Windows.

EDIT just saw your last post. If you burn the Ubuntu CD you can use it as a LiveCD (run the OS from the CD) and can use that to see what is on the hard drive as it sounds like it is bursting at the seams. There is also a utility on the Live CD called Gparted, this is a partition manager and will allow you to wipe the drive if you wish. Many instuctions on how to do this elsewhere.

---

### Post by givemewindows on 2010-09-07
.
 
 
Is there any way to delete it and reinstall from this stupid command prompt im stuck at? im in some sort of dos mode, and it will not allow me past it. How can i wipe it from where im at now and restart?

---

### Post by givemewindows on 2010-09-07
Btw, thanks for all the replies. ive been googling all night and this morning with no luck.

---

### Post by migs73 on 2010-09-07
For me the beauty of Ubuntu is the people on here.
If you download the ISO from Canonical and burn it as per the instuctions on the website, you can then use (quite legally since its free) it to install Ubuntu again. When prompted tell it to use ALL the hard drive for Ubuntu, that should get rid of any nasties. Although I am no fan of giving MS money, talk of 'borrowing' copies is likely to get you a slap on the wrist from the moderators.

---

### Post by givemewindows on 2010-09-07
Thanks. quote removed. So my best bet is to DL onto a disk, then plug that in? is that gonna work in this catatonic state that my computer seems to be stuck in?

---

### Post by LowSky on 2010-09-07
we cant help you with installing a "borrowed" copy of windows. if you want to erase your hard drive, a Windows CD can do that. sorry but we cant really help with that.

Like I said Call Dell if you need service, it could possibly be a defective computer if you having done anything to the installation and it isn't booting correctly.  

Without more info on what you might have installed or tried before the issue started we are only drawing at straws.

---

### Post by migs73 on 2010-09-07
Before you put the CD in, set the BIOS to boot from CD (usually is first boot device by default),put in the CD and reboot, this will then get you a fully working Ubuntu running (slower than normal) from the CD. 
You then get options, either to try Ubuntu without making any changes to the computer, or you can go ahead and install. If you choose to install, just follow the install wizard.
If you choose to try it out, and then want to install, there is an Icon on the desktop for installing from there.

---

### Post by pricetech on 2010-09-07
Contact Dell Support.  It sounds like you may have a defective machine.

Folks here are glad to help, but it sounds like you need to start by making sure the computer is functioning as it should from the manufacturer before doing a lot of other stuff to it.

---

### Post by silverglade00 on 2010-09-07
I have the same machine. It will run both Ubuntu and Windows just fine. It sounds like you bought yours used because it shouldn't be running out of room when it is new.

To wipe it and install Windows, just hook up a USB CD drive and run the Windows install CD. You also shouldn't announce on a public forum that you are planning to make an illegal copy of it. There is nothing to uninstall. You just install Windows to the hard drive and it will wipe out Ubuntu. You will need to press Fn+F2 when the Dell logo comes up and choose the CD drive to boot from. 

If you want to install Ubuntu, just download the ISO file from the website. Burn that to a CD. Pop it into a USB CD drive and do the same Fn+F2 to choose the CD. GO through the installer and it will let you install a fresh copy of Ubuntu.

---

### Post by givemewindows on 2010-09-07
> **migs73 said:**
> Before you put the CD in, set the BIOS to boot from CD (usually is first boot device by default),put in the CD and reboot, this will then get you a fully working Ubuntu running (slower than normal) from the CD. 
You then get options, either to try Ubuntu without making any changes to the computer, or you can go ahead and install. If you choose to install, just follow the install wizard.
If you choose to try it out, and then want to install, there is an Icon on the desktop for installing from there.
 ill be running off thumbdrive as this is a mini, with no cd slot.. and yet again, im stuck at a boot screen, im not actually in the actual program.

---

### Post by givemewindows on 2010-09-07
> **silverglade00 said:**
> I have the same machine. It will run both Ubuntu and Windows just fine. It sounds like you bought yours used because it shouldn't be running out of room when it is new.
 
To wipe it and install Windows, just hook up a USB CD drive and run the Windows install CD. You also shouldn't announce on a public forum that you are planning to make an illegal copy of it. There is nothing to uninstall. You just install Windows to the hard drive and it will wipe out Ubuntu. You will need to press Fn+F2 when the Dell logo comes up and choose the CD drive to boot from. 
 
If you want to install Ubuntu, just download the ISO file from the website. Burn that to a CD. Pop it into a USB CD drive and do the same Fn+F2 to choose the CD. GO through the installer and it will let you install a fresh copy of Ubuntu.
 This is what i needed. Thanks. ill give this a shot and report back. 
 
 
Did you experience any lag with windows? im hearing im going to need a stripped down version of xp in order to have any space whatsoever. Which all i need it to do is get online, type papers, and play solitaire.

---

### Post by givemewindows on 2010-09-07
im @ 60% of dling version 10.04.1.. wish me luck.

---

### Post by silverglade00 on 2010-09-07
> Did you experience any lag with windows? im hearing im going to need a stripped down version of xp in order to have any space whatsoever. Which all i need it to do is get online, type papers, and play solitaire.

It depends on how much drive space you have. I have the 64GB SSD and it has plenty of room left over after installing Windows XP, Windows 7 or Ubuntu. Ubuntu leaves the most room for me. If that is all you are using it for, any of the OSes will work. If you want to use Windows, Windows 7 pretty much has everything set up for you on install. It seems to run a little better than XP did in my experience. Ubuntu has everything installed and working except for wireless right after the install. You will need to plug it into a wired connection and run the Hardware Drivers application. This is not Ubuntu's fault, but a legal restriction that Broadcom has placed on their wireless drivers. 

Ubuntu installs on the computer in about 4.5 GB of space. Windows seems to take up about 12 for me after installing Office and anti-virus and all that. If you need some extra space, you can also look into [Dropbox]("http://www.dropbox.com/referrals/NTMzNjA2ODk"). They give you 2GB of online storage for free. It works with Windows, Mac, and Ubuntu and you can syncronize files from different computers.

---

### Post by Calash on 2010-09-07
> **pricetech said:**
> Contact Dell Support.  It sounds like you may have a defective machine.

Folks here are glad to help, but it sounds like you need to start by making sure the computer is functioning as it should from the manufacturer before doing a lot of other stuff to it.

This is a good point if this was purchased from Dell.  They should be giving you a working computer.

---

### Post by Rasa1111 on 2010-09-07
> all i need it to do is get online, type papers, and play solitaire

 If that's all you need, you certainly don't need windows. 

> im @ 60% of dling version 10.04.1.. wish me luck.

 sweet, good luck. 

 Ubuntu rocks man.

---

### Post by givemewindows on 2010-09-07
> **Rasa1111 said:**
> If that's all you need, you certainly don't need windows. 
 
 
 
sweet, good luck. 
 
Ubuntu rocks man.
 yeah, i dont need alot.. its just a new interface is a PITA to work around, and not being able to go to a delete/modify program screen like in windows is a bigger pain. 
 
its for my gf, and shes familiar with windows, and i know enough about it to set it up for what she needs, this linux OS has just thrown a wrench in all that. im gonna attempt to upgrade it and see what that does, if i can ever get off this dead screen.

---

### Post by Rasa1111 on 2010-09-07
> **givemewindows said:**
> yeah, i dont need alot.. its just a new interface is a PITA to work around, and not being able to go to a delete/modify program screen like in windows is a bigger pain. 
 
its for my gf, and shes familiar with windows, and i know enough about it to set it up for what she needs, this linux OS has just thrown a wrench in all that. im gonna attempt to upgrade it and see what that does, if i can ever get off this dead screen.

I understand. 
New stuff can be confusing,
and even more confusing when we didnt actually decide to make the change ourselves, and it is just kinda forced upon us. lol

 But I think, if you give it a chance, you'll really like it. 

Before I babble on...

 Since you and your girl are so used to windows,
 you may want to check into Kubuntu.  [http://www.kubuntu.org/](http://www.kubuntu.org/)

 It is Ubuntu, but setup more like a windows OS. 
People that have a difficult time getting used to the new desktop environment, often find that Kubuntu feels much more like 'home' to them, and easier to navigate. 


 This might not be of any consolation,
But if my parents (almost 60), their friends (same age bracket)
Can go from knowing only windows, to using only Ubuntu full time~
 I think you and your girl will be ok. ;)  lol

in Ubuntu, there is a 'screen' that, like windows, shows you all of your installed programs, and lets you simply delete that which you no longer want/need.

 The easiest way for a beginner, used to having a GUI , 
Would be through Ubuntu Software Center~

 You can simply open it (like an "add/remove programs" window) in windows,  Look at your list of everything installed, and then remove/or add programs/apps as you wish. 
All from within that one window. 

 All I ever knew was windows also.
 Until about 9 months ago. 
Then i just got tired of it, and decided I would learn Ubuntu/Linux, if it killed me!  lol
 I went ahead and removed windows completely, so I would have no choice but to learn Ubuntu. And that was a great decision! lol

 To my surprise though, I did not have to learn nearly as much as I always thought I would have to, to be able to use this OS.
And, it did not take me any time at all really to get used to the new layout.  I thought it would take a long time to get used to. 
But that was just old FUD. lol

 This is really, easier to use and maintain than windows ever was,
and I got pretty good at windows over the years, fixing it, breaking it, etc. :lol:
 I thought windows was 'easy"..
 but this, is super easy! 
[SIZE="1"][COLOR="Silver"](and a million times better)[/COLOR][/SIZE]  
lol :P

You'll see....
 I hope. lol :D

---

### Post by givemewindows on 2010-09-07
ill try that..
 
 
dl'ing kubuntu via utorrent as we speak.

---

### Post by givemewindows on 2010-09-07
ok, downloaded kubuntu, extracted files to usb, changed order of bios to usb first, now it searches and says no operating system found. 
 
however, when i plug it into my other laptop, it automatically recognizes it and asks to install kubuntu. 
 
jeez what have i done now?

---

### Post by Rasa1111 on 2010-09-07
> **givemewindows said:**
> ok, downloaded kubuntu, extracted files to usb, changed order of bios to usb first, now it searches and says no operating system found. 
 
however, when i plug it into my other laptop, it automatically recognizes it and asks to install kubuntu. 
 
jeez what have i done now?


 To be honest, I don't think *you* have done anything, 
from all that's been said so far, I think whoever you got the laptop from is the one at fault for these issues. 

I'm really not sure what the next step should be,
 But I did come across this thread~ 
and someone who had the same > no operating system found. problem, [http://ubuntuforums.org/showthread.php?t=1317008](http://ubuntuforums.org/showthread.php?t=1317008)

You might want to check out unetbootin~ [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

 But if the USB drive works on your laptop, and not on this new one..
Im not sure what unetbootin will be able to do for it. 

 Sorry man, like I said, Im pretty much a n00b myself.
So not really sure where to go from here,
but there are others here who Im sure will be able to get you going. 

 Good luck bro. <3

hmm, maybe I will see if i can get bcbc in here, he seems to be pro with this stuff... lol

---

### Post by givemewindows on 2010-09-07
jesus i dont see how anyone could willingly want to use this garbage. Two days and im still stuck at 
 
[EMAIL="user@user-laptop"]user@user-laptop[/EMAIL].

---

### Post by nothingspecial on 2010-09-07
What have you done?

You`ve had a bad first time experience with {K}ubuntu.

Phone Dell.

---

### Post by givemewindows on 2010-09-07
Thanks for the links man, ill give that a shot. Im gonna need a few shots if it keeps going this way.

---

### Post by givemewindows on 2010-09-07
> **nothingspecial said:**
> What have you done?
 
You`ve had a bad first time experience with {K}ubuntu.
 
Phone Dell.
 its just really frustrating that theres no clear answer. ive gotta search through ten thousand codes, and .iso files, and hotkeys and all this nonsense, and its still stuck in a catatonic state.

---

### Post by Rasa1111 on 2010-09-07
> jesus i dont see how anyone could willingly want to use this garbage. Two days and im still stuck at 

user@user-laptop.

if everyone had these issues, I dont think anyone *would* want to use it.
 But most people dont have these problems.

 Garbage? hardly, man. 

People constantly have issues with windows, 
is that garbage to? 

 well, imho, for the most part, I think so.. lol
 but that doesnt actually make it garbage. 

 Im guessing youve never actually done a brand new fresh install of windows eh?

> Thanks for the links man, ill give that a shot. Im gonna need a few shots if it keeps going this way

 No problem.

 I really do understand it can be frustrating as hell, 
But in my experience,  it is usually something messed up with the computer itself, not the OS.

 and if it loaded right up on your laptop, just not your gf's,
shouldnt that be a clue that it actually does what it should...
on a working computer?

---

### Post by bowens44 on 2010-09-07
> **givemewindows said:**
> its just really frustrating that theres no clear answer. ive gotta search through ten thousand codes, and .iso files, and hotkeys and all this nonsense, and its still stuck in a catatonic state.

The fact that you can boot from the USB drive with another computer confirms that the problem is your laptop , not the operating system.

As others have said, if you bought this from Dell, contact Dell.

---

### Post by givemewindows on 2010-09-07
bought it off craigslist. if i had bought it from dell i wouldnt have gotten linux to start with. 
 
 
the warranty is out, so getting someone on the phone at dell is nearly impossible. im on hold right now. 
 
i just want this stupid thing to boot up. worked fine last night, today it hasnt seen anything outside this stupid boot screen.

---

### Post by tahitiwibble on 2010-09-07
> **migs73 said:**
> For me the beauty of Ubuntu is the people on here.

I do so agree with you :)

---

### Post by givemewindows on 2010-09-07
dell says LOL WUT 
 
i explain 5 more times
 
then they basically said "sorry about your luck.. wanna buy a new one?"
 
 
back to square one :facepalm:

---

### Post by halitech on 2010-09-07
first thing I do when selling a system is give the buyer any and all usernames and passwords I've set up on a machine. Contact the seller and see if they can give you that info although if its saying user@user:~$ then you are logged in already. 

as far as the message about the hard drive being used, apparently there was a bug (undocumented feature?) in an earlier version but no fix yet.

[http://ubuntuforums.org/showthread.php?t=1318284](http://ubuntuforums.org/showthread.php?t=1318284)

try typing this in at the command prompt
```
start service gdm
```
let us know what happens.

---

### Post by givemewindows on 2010-09-07
> **halitech said:**
> first thing I do when selling a system is give the buyer any and all usernames and passwords I've set up on a machine. Contact the seller and see if they can give you that info although if its saying user@user:~$ then you are logged in already. 
 
as far as the message about the hard drive being used, apparently there was a bug (undocumented feature?) in an earlier version but no fix yet.
 
[http://ubuntuforums.org/showthread.php?t=1318284](http://ubuntuforums.org/showthread.php?t=1318284)
 
try typing this in at the command prompt
```
start service gdm
```
let us know what happens.
 start: unknown job: service

---

### Post by givemewindows on 2010-09-07
if youre curious, this is what im looking at. 
 
 
[IMG]http://i165.photobucket.com/albums/u59/cnote05300/Mobile%20Uploads/IMG00036-20100907-1437.jpg[/IMG]

---

### Post by halitech on 2010-09-07
opps, wrong syntax, try this

```
service gdm start
```

---

### Post by givemewindows on 2010-09-07
> **halitech said:**
> opps, wrong syntax, try this
 
```
service gdm start
```
 start: rejected send message, 1 matchd rules; type "method_call", sender=":1;23" blah blah blah blah

---

### Post by wojox on 2010-09-07
Try

```
sudo /etc/init.d/gdm start
```

---

### Post by givemewindows on 2010-09-07
Heres a cool new message
 
Fatal server error:
server is already active for display 0
if this server is no longer running remove /tmp/.xo-lock and start again.
 
please consult the x.org foundation support
at [http://wiki.x.org](http://wiki.x.org) for help. ddxsigGiveUp:closing log

---

### Post by givemewindows on 2010-09-07
> **wojox said:**
> Try
 
```
sudo /etc/init.d/gdm start
```
 Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start
 
since the script you are attempting to invoke has been converted to an upstart job you may also use the start(8) utility, e.g. start gdm

---

### Post by wojox on 2010-09-07
Try and remove the lock

```
sudo rm /tmp/.xo-lock
```

---

### Post by givemewindows on 2010-09-07
> **wojox said:**
> Try and remove the lock
 
```
sudo rm /tmp/.xo-lock
```
 cannot remove tmp is a directory
cannot remove .xo-lock no such file or directory

---

### Post by wojox on 2010-09-07
> **givemewindows said:**
> Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm start
 
since the script you are attempting to invoke has been converted to an upstart job you may also use the start(8) utility, e.g. start gdm

I thought you tried that already. Thought you may have had an older version.

---

### Post by wojox on 2010-09-07
What's

```
ls /tmp/
```

---

### Post by givemewindows on 2010-09-07
> **wojox said:**
> What's
 
```
ls /tmp/
```
 ssh-bgevbJ1371

---

### Post by givemewindows on 2010-09-07
well i did apt-get update and apt-get upgrade and its going nuts doing something. results to follow.

---

### Post by wojox on 2010-09-07
> **givemewindows said:**
> well i did apt-get update and apt-get upgrade and its going nuts doing something. results to follow.

Sure updating and upgrading usually tend to help. Do you know which version your using?

---

### Post by givemewindows on 2010-09-07
it was an older version.. 9 something. well its still going crazy, showing 42 minutes left but keeps fluctuating, not really sure what its doing, im thinking that it might be possessed by satan.
 
lol i have no clue how i got it started, i was just looking at a cheat sheet of hotkeys and went to town seeing if any of them would do anything. well i found one that did. not sure whats gonna happen, but well see.

---

### Post by wojox on 2010-09-07
> **givemewindows said:**
> it was an older version.. 9 something. well its still going crazy, showing 42 minutes left but keeps fluctuating, not really sure what its doing, im thinking that it might be possessed by satan.
 
lol i have no clue how i got it started, i was just looking at a cheat sheet of hotkeys and went to town seeing if any of them would do anything. well i found one that did. not sure whats gonna happen, but well see.

Lol, it's just downloading and installing upgraded packages from the repositories. Let it do it's thing.

---

### Post by Rasa1111 on 2010-09-07
yeah smells like progress! lol :)

---

### Post by givemewindows on 2010-09-07
Nothing. two hours of updates and im still stuck on the same F$&%*#$ screen.
 
 
can i click my heels three times and end up in vista?

---

### Post by Rasa1111 on 2010-09-07
> **givemewindows said:**
> 
 
 
can i click my heels three times and end up in vista?

lol, from one nightmare to another eh? :P

---

### Post by wojox on 2010-09-07
> **Rasa1111 said:**
> lol, from one nightmare to another eh? :P

:lolflag:


I thought you where downloading (K)Ubuntu 10.04 and installing that.

---

### Post by Arla on 2010-09-07
> **wojox said:**
> :lolflag:


I thought you where downloading (K)Ubuntu 10.04 and installing that.

Problem is it sounds like he has a "bad" usb drive, and what I mean by that is he has a USB drive that his dell computer can't boot from, I know I have three USB drives, and some computers can boot from some, others can boot from others, I've got one so far that I've had good luck with MOST computers booting from.

Any chance of getting use of/having a USB CD drive? Really I would HIGHLY recommend a fresh install based on the discussion so far.

---

### Post by givemewindows on 2010-09-07
> **Rasa1111 said:**
> lol, from one nightmare to another eh? :P
Keep in mind, im typing this on my dell with vista, thats never given me an ounce of trouble, no matter how much music+videos+games ive downloaded.. Even with limewire *GASP*
 
my uber cool linux computer is currently a F%[EMAIL="F%#@$"]#@$[/EMAIL] paperweight and noone seems to know why. 
> **wojox said:**
> :lolflag:
 
 
I thought you where downloading (K)Ubuntu 10.04 and installing that.
 Well i would, if this thing would do anything besides sit at a screen that says [EMAIL="user@user-laptop:~$"]user@user-laptop:~$[/EMAIL]
 
i managed to do some sort of update+upgrade to ubuntu, but surprise surprise, its still bricked. For seemingly no reason at all.

---

### Post by givemewindows on 2010-09-07
> **Arla said:**
> Problem is it sounds like he has a "bad" usb drive, and what I mean by that is he has a USB drive that his dell computer can't boot from, I know I have three USB drives, and some computers can boot from some, others can boot from others, I've got one so far that I've had good luck with MOST computers booting from.
 
Any chance of getting use of/having a USB drive? Really I would HIGHLY recommend a fresh install based on the discussion so far.
 This is correct. 
 
My dell with vista would only recognize the drive with kubuntu on it in one slot. the others it didnt know it existed. 
 
Now ive tried to boot it from all three of the ones on the mini, to no avail.. ill try again. What did you mean by usb drive?

---

### Post by Arla on 2010-09-07
> **givemewindows said:**
> Now ive tried to boot it from all three of the ones on the mini, to no avail.. ill try again. What did you mean by usb drive?

I mean't USB CD drive, just missed the critical word, CD!

Unfortunately it also sounds like you got a HOSED install of linux from someone else, it could (honestly) be that the person on Craigslist was selling it because they had bricked it (or all but) and wanted to dump it quickly.

---

### Post by givemewindows on 2010-09-07
> **Arla said:**
> I mean't USB CD drive, just missed the critical word, CD!
 
Unfortunately it also sounds like you got a HOSED install of linux from someone else, it could (honestly) be that the person on Craigslist was selling it because they had bricked it (or all but) and wanted to dump it quickly.
 i do have a usb cd drive at home. think that would work? change the bios to boot from cd? 
 
 
 
 
why would it take all that time to load and replace and update stuff, just to come back to the same screen?

---

### Post by Arla on 2010-09-07
Let me put it another way, to get Windows on this PC is "simple" you need a windows disc (oh and a license), and you need a CD/DVD drive to boot from.

You can/could use (K)Ubuntu in a similar fashion, and the default install of ubuntu should be a lot better than whatever you currently have, but if you want to go with Windows (a perfectly acceptable option) you need, in essence the same stuff, a CD/DVD drive to install it from, and a boot CD/DVD with the OS of choice on it.

---

### Post by Arla on 2010-09-07
> **givemewindows said:**
> i do have a usb cd drive at home. think that would work? change the bios to boot from cd? 
 
 
 
 
why would it take all that time to load and replace and update stuff, just to come back to the same screen?

The problem is, it depends entirely how the person you got it from set it up, YES it is possible that eventually through numerous posts people on this forum could figure out what's wrong and fix it to get you to a nice GUI screen, the problem is that could take a long time because we don't have access to your machine and don't know what's on it (I'm somewhat new to Ubuntu, so it's possible someone's going to tell me I'm being thick here but, that's my opinion at least) if you did a brand new, fresh install of (K)Ubuntu at least we'd know what point you're starting from.

---

### Post by Hobgoblin on 2010-09-07
> **givemewindows said:**
> cannot remove tmp is a directory
cannot remove .xo-lock no such file or directory

You put a space between /tmp/ and .xo-lock

It's
sudo rm /tmp/.xo-lock

not
sudo rm /tmp/ .xo-lock


If you want Windows then you are going to need a USB CD drive or the help of a **Windows** forum to get it installed from a USB flash drive.  You may as well get a USB CD drive and have a go at a fresh unstall of Ubuntu, you never know, you might find that it it's acually OK when it does work.

---

### Post by givemewindows on 2010-09-07
> **Hobgoblin said:**
> You put a space between /tmp/ and .xo-lock
 
It's
sudo rm /tmp/.xo-lock
 
not
sudo rm /tmp/ .xo-lock
 
 
If you want Windows then you are going to need a USB CD drive or the help of a **Windows** forum to get it installed from a USB flash drive. You may as well get a USB CD drive and have a go at a fresh unstall of Ubuntu, you never know, you might find that it it's acually OK when it does work.
 took the space out, gave me the same answer.
 
 
at this point, i really dont care what it runs anymore, i just want it to run something. 
 
somehow i got it to [EMAIL="root@user-laptop:/home/user"]root@user-laptop:/home/user[/EMAIL]# for now, and start x still doesnt work. it tells me to try x wiki or something like that.

---

### Post by Arla on 2010-09-07
Probably to look at the x-wiki, because it's having some issue starting x (believe me, I had that issue recently and it was a bit of a pain, but my fault for trying beta software).

Again, my highest recommendation would be burn Ubuntu (or Kubuntu or whatever flavour you like) to a CD, boot from a USB CD drive, install from that (using entire disk) and see where it goes (assuming that the machine has nothing on it you want to save, which it sounds like it doesn't).

Assuming you decide that Linux isn't for you (it IS a learning curve from windows, since it doesn't do things the same way windows does) then you can do the same procedure, only boot with a windows CD instead of a Ubuntu CD (assuming you have a valid license and all that jazz).

---

### Post by givemewindows on 2010-09-07
can it be a cd OR a dvd i burn to? ive got plenty of cd's, but id rather save the cash from having to buy a spindle of dvds for just one. 
 
im still not 100% that i can run tinyxp or even a stripped down regular xp without using up all the HD.. as its a mini and only 8gb. w2000 would be a good fit, but its outdated by most standards today. 
 
Ill probably try kubuntu just to see if i can do anything other than this one screen, then go from there. if i get it back doing something i may just leave it the hell alone for now.

---

### Post by jtarin on 2010-09-07
I'm surprised that no one has given you the [link]("https://help.ubuntu.com/community/Installation") to the installation documentation. This gives you more options than you can use. Find one that seems suitable for your environment. You will need the .iso.  I would recommend [this one]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick") if you have a USB stick. You can also do a network install.

---

### Post by Arla on 2010-09-07
> **givemewindows said:**
> can it be a cd OR a dvd i burn to? ive got plenty of cd's, but id rather save the cash from having to buy a spindle of dvds for just one. 

Ubuntu (as standard) only requires a CD, I'd go for either the Ubuntu Desktop or Ubuntu netBook install, personally I think Ubuntu is better supported than Kubuntu, but that's just my opinion (you seem to like Kubuntu for some reason) lots of folks here know it so should be plenty of assistance if you have issues.

Do NOT go for ubuntu minimal! This will get you only to a command-prompt, and while great for people who know lots about Linux and what they are doing, would I think kill you (it near enough killed me!)

---

### Post by halitech on 2010-09-07
I'm wondering if it even has a GUI installed since startx and start gdm didn't work. try installing a lightweight desktop like Xubuntu-desktop on it

```
sudo aptitude install xubuntu-desktop
```

if you want to check your free space, run this
```
du  -s --si
```

---

### Post by Rational1 on 2010-09-07
Dell has their own version of Ubuntu, and in my experience it is very poor. I would burn a cd, or use a USB key, my preferred method, and install fresh.

Maybe give Easy Peasy a try?
Easy Peasy is optimized for netbooks, and can be switched to run in normal GUI mode easily.

---

### Post by anewguy on 2010-09-07
Personally, just to get you going, I would go with the download of the kubuntu ISO and burn it to CD.  Prior to booting with it, I would, however, post the output of the following (you can enter this right at that prompt you are getting):

lspci <press enter>

The idea here is to find out what type of video the PC is using to see if we also need to get you a driver for it.

Also, when startx fails, you can look at the log to see the error message:

ls /var/log <press enter>

look for something like Xorg0.log or some such thing, then:

cat /var/log/<the filename you determined> | more <press enter>

You'll be able to scroll through the log - look towards the end to see where it is failing and post that back here.

Dave

---

### Post by beew on 2010-09-07
OP said he just bought the PC, shouldn't that come with some kind of warranty? He should have contacted Dell before he did anything, now he has probably voided it.

---

### Post by Rasa1111 on 2010-09-07
> **beew said:**
> OP said he just bought the PC, shouldn't that come with some kind of warranty? He should have contacted Dell before he did anything, now he has probably voided it.

 No.
 He *said* he got it from craigslist. 
Someone borked a laptop and sold it to him.
 or so it seems.

 but if OP has access to CD drives and whatnot, 
I don't know why this has gone on for 8 pages,. 

If i really wanted to get a machine going, Id use everything I possibly had that might work. 
Now it's just "uber" (as OP would say)
.. Lame. lol

---

### Post by Baldrick_NZ on 2010-09-08
Lots of info here, and if you haven't thrown your PC out the window yet, maybe this might help...

When you burnt your Kubuntu CD, did you burn it as an iso (image)? Merely burning it as a file won't help.

Second, (assuming you burnt it as an image) insert the CD into the drive, then restart the PC. When the bios screen comes up, press whichever key that alludes to 'boot order' (or such). Choose CD (usually by scrolling to it) and press enter.

It should now load kubuntu from the CD. At some point, it'll ask you to choose whether you want to 'install' or 'try'. Go with the 'try' option. If kubuntu loads, then you've just proved the problem isn't with the operating system, but with the PC because you have effectively by-passed what's on the hard drive. You could then install kubuntu by clicking 'install kubuntu' from the desktop. 

If the installation fails, this would indicate problems on or with the hard drive itself.

See how that goes..

---

### Post by anewguy on 2010-09-08
> **Rasa1111 said:**
> No.

....but if OP has access to CD drives and whatnot, 
I don't know why this has gone on for 8 pages,. 

If i really wanted to get a machine going, Id use everything I possibly had that might work. 
Now it's just "uber" (as OP would say)
.. Lame. lol

Couldn't agree more - I think there has been more than enough info posted to get the OP going.  Ooopppsss - I may have just added another page!

Dave ;)

---

### Post by undecim on 2010-09-08
> **givemewindows said:**
> ok, downloaded kubuntu, extracted files to usb, changed order of bios to usb first, now it searches and says no operating system found. 
 
however, when i plug it into my other laptop, it automatically recognizes it and asks to install kubuntu. 

jeez what have i done now?

How did you extract the files to the USB drive? Unless you used something like Unetbootin to extract the files, the drive won't have a bootloader, and therefore cannot be booted.

I take it when you plugged it into your other laptop, the laptop was already running? You need a bootloader to boot a disk, but not to read files from it, and the ubuntu iso comes with a Wubi installer. Windows reads the files from it and recognizes the Wubi installer, which is different from booting the CD to install it.

If you haven't already, you should use Unetbootin to install to that thumb drive, not just extract the files to it. Once you do that, you should be able to boot from the thumb drive to reinstall.

---

### Post by sikander3786 on 2010-09-08
Here is the link if you couldn't find it yet.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And this one will also help during installation.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by strugglingbadly on 2010-09-08
Apologies in advance if the following advice seems far too simplistic. It is not meant to insult your intelligence - rather it is more an indicator of my own level of competence and lack of knowledge - take note of my name

I only 'converted' a week ago, and this is what I did....(I assume you have access to a working PC c/w r/w disk)

downloaded the desktop 386 version of Ubuntu 10.04 from the ubuntu site 

download the disk utility InfraRecorder from infrarecorder.org - as recommended on the ubuntu site

use the write image option to create the disk - you need a 700Mb disk as the .so file is about 694Mb

after this point I found that I could not boot on this disk as my PC started straight on C: drive with windows and ignored the disk. I had to get into the boot up routine and edit the startup priority for the removable disk to be selected first. Can't help you much with the specifics here as I have no familiarity with your machine. I do know that you need to be careful or you will certainly make things worse. Take note of all settings before attempting any changes.

After that, everything was completely straightforward - just follow the instructions.

Hope this beginners / kindergarten guide helps. Good luck.

ps   my record for a laptop is 27 meters onto concrete......into a headwind......but I do not recommend this course of action

---

### Post by Calash on 2010-09-08
> **givemewindows said:**
> took the space out, gave me the same answer.
 
 
at this point, i really dont care what it runs anymore, i just want it to run something. 
 
somehow i got it to [EMAIL="root@user-laptop:/home/user"]root@user-laptop:/home/user[/EMAIL]# for now, and start x still doesnt work. it tells me to try x wiki or something like that.

We need to know what you want.  Part of the problem right now is that you are getting advice for several different solutions.  What you need to do is pick your ideal solution and go for that.

Lets start with the very basic.

Windows or Ubuntu?

If Windows, get yourself install media and boot from the CD.  It is really as simple as that.  Ubuntu will not stop you from installing windows.

If you want Ubuntu we can work on that too.  For starters stay at the root prompt for now, that is the best place to fix the issue.

From there give us the output of the following command

```

grep 1000 /etc/passwd
grep 1000 /etc/group

```

They are search commands.  The first is searching for user 1000, the default first user you create in Ubuntu.  Make sure the name that comes up is what you are login in as.

The second command searches for members of your group.  One of the lines should be your username and some other groups separated by ':'.  The line that starts with your username is the important one to us.

The reason I ask for this info is based on your previous post

> 
startx brings up
"user not aughorized to run the x server, aborting"


Your login user needs to be a member of the x group to use the GUI.  In the root prompt this is easy to fix but first we need to make sure everything is in order.

Only do this if you want to fix your Ubuntu.  If you want Windows, you know what to do ;)

---

### Post by jshepherd on 2010-09-08
If you do get it working and want windows, don't use Tiny XP it is EXTREMELY LIMITED. The reason it it's called Tiny XP is because loads of functions and features have been disabled or removed from the OS. 8GB is more than enough for a full XP install but I'd still go with Ubuntu as it runs much smoother on solid state drives.

---

### Post by givemewindows on 2010-09-08
back again guys. The reason i hadnt tried the cd method yet, is that i was trying to do this yesterday at work, and my drive was at home. i brought it with me today and im dling kubuntu right now. 
 
Yes, i bought the comp off CL, i knew it had linux on it when i bought it, i didnt know how much id hate it. 
 
im using kubuntu bc it seems the interface is windows-esque.
 
hopefully ill be up and going today.
 
Lost a friend today so i really havent been in the mood to mess with it until now.

---

### Post by beew on 2010-09-08
> im using kubuntu bc it seems the interface is windows-esque.

Exactly the reason I don't like KDE. :)

I am sorry for your loss.

---

### Post by givemewindows on 2010-09-08
> **beew said:**
> Exactly the reason I don't like KDE. :)
 
I am sorry for your loss.
 lol, trying to reach a happy medium
 
 
and thanks, my "friend" was my pet bengal cat. Found out he had leukemia this morning. :(

---

### Post by givemewindows on 2010-09-08
well im posting this from the dell mini. i got a new OS loaded and shes running just fine. 

i went with linux mint and i really like it thus far. menus are a bit clutterd at first but its getting better.

---

### Post by Arla on 2010-09-08
> **givemewindows said:**
> well im posting this from the dell mini. i got a new OS loaded and shes running just fine. 

i went with linux mint and i really like it thus far. menus are a bit clutterd at first but its getting better.

HUZZAH! I'd call that a result.

I guess there is something of windows (at least to me) if it's too borked to do much, REINSTALL!

---

### Post by Rasa1111 on 2010-09-08
good to hear shes up n running. :)
Saddened to hear of your friend,
that can be just as hard as losing a human. :(
Love n Blessings. <3

---

### Post by walt.smith1960 on 2010-09-08
> **Arla said:**
> HUZZAH! I'd call that a result.

I guess there is something of windows (at least to me) if it's too borked to do much, REINSTALL!

True.  But it takes an hour to get a reinstall of Ubuntu usable.  It takes a day to get Windows usable.  And there's no activation crap or hunt down drivers crap (at least for me) or install the OS *then* install the malware protection and utilities to be able to actually *use* it then install an office program and a *good* graphics program and printer utilities etc. etc. ad nauseum.  And if you can't find serial #'s and keys you're SOL.  I'm lovin' Linux.

---

### Post by anewguy on 2010-09-08
I'm sorry to hear of your loss.  I have a big old male kitty that has been my best friend for years.  I shudder at losing him, but he's also somewhere around 10 years old, so I don't know how long he may be with me.  I really feel your pain.

As far as your PC,  good job getting it up and running!  As a side note, if you do at some point decide to install Windows instead, be aware that all of the XP installs I have done have never asked if I wanted to wipe the disk - it just used free space.  So if you have Linux installed and want to install Windows instead, I would recommend running one of the LiveCDs and running gparted to delete the Linux partitions.  You will need to issue a swapoff before you can delete the swap partition.

Again, great job!  I just wanted to provide the extra info in case you need it at some point in the future.

I also want to add what everyone seems to say in cases like this - be patient with Linux.  It is a different animal, but you'll also find that such things as getting on the net, using email, using a word processor, etc., all have a very familiar feel - it just seems different at first.

Dave ;)

---

### Post by gbestrada on 2010-09-08
if you are stuck in the terminal type :ctrl +alt+f5  it will take you to the ubuntu screen.
;)

---

### Post by givemewindows on 2010-09-09
> **walt.smith1960 said:**
>  And there's no activation crap or hunt down drivers crap (at least for me) .
 spoke too soon. Evidently linux decided it would be best to ignore that most people who use netbooks need wireless internet drivers. 
 
any recommendations?

---

### Post by YfoMp5QBh2 on 2010-09-09
Why dont you just remove the hard drive, put it into a different computer (preferably a Windows one) format it, then put it back in the laptop and re-install Windows using the Windows CD?
 
Possibly the easiest way to do it without using the command line.

---

### Post by nothingspecial on 2010-09-09
He hasn`t got a windows cd, it came with linux.

Ok wireless drivers, lets see if Mint is recognising your card.

Open a terminal how ever you do that in mint, should be in the menu somewhere

copy and paste ```
sudo lshw -C network
```

into it, and copy and paste the gobbldygook it spits out back here

---

### Post by givemewindows on 2010-09-09
requested gobbldygook 

 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d0:fb:c5
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:23:08:3d:aa:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by nothingspecial on 2010-09-09
Get a wired internet connection,

open the terminal again and type

```
sudo apt-get update && sudo apt-get install b43-fwcutter
```

Then restart

---

### Post by givemewindows on 2010-09-09
ok did that, it worked for a sec, then stopped. trying again.

---

### Post by nothingspecial on 2010-09-09
What worked?

Your wireless or installing the broadcom firmware

---

### Post by givemewindows on 2010-09-09
it installed something, booted back up, recognized wireless connections for a second, then it just decided to stop.

---

### Post by givemewindows on 2010-09-09
redid that process. it said nothing was updated, still wont connect

i really really hate linux. this is ridiculous.

---

### Post by nothingspecial on 2010-09-09
You may need to blacklist a conflicting module

type ```
lsmod
``` and post the gobbledygook

---

### Post by givemewindows on 2010-09-09
gobbldygook

Module                  Size  Used by
usbhid                 36110  0 
hid                    67032  1 usbhid
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
b43                   157218  0 
mac80211              204922  1 b43
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
compal_laptop           2034  0 
dcdbas                  5422  0 
serio_raw               3978  0 
jmb38x_ms               7311  0 
sdhci_pci               5470  0 
cfg80211              126485  2 b43,mac80211
soundcore               6620  1 snd
sdhci                  15462  1 sdhci_pci
memstick                8237  1 jmb38x_ms
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
led_class               2864  2 b43,sdhci
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  282354  3 
drm_kms_helper         29297  1 i915
r8169                  33884  0 
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
ssb                    37336  1 b43
mii                     4381  1 r8169
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video

---

### Post by nothingspecial on 2010-09-09
Uncle google has thrown this solution up........

......don`t know if it will work.....

one line at a time

```
wget http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz
tar -xvf b43-all-fw.tar_.gz
rm -r b43-all-fw.tar_.gz
sudo cp -r b43* /lib/firmware/
```restart

---

### Post by givemewindows on 2010-09-09
now it doesnt acknowledge them at all.

---

### Post by 23dornot23d on 2010-09-09
Did you reboot it ?

( and what version of Mint are you using 8 or 9 ? )

If you have Mint 8 ..... download the latest one Mint 9 .....

**I ask because your apt-update worked near the beginning of this thread ..... if you had Ubuntu 10.04 on originally ..... **

**Mint 9 is its equivalent **...... so it should pick up the drivers on installation .....
sounds like you are 90% the way to having this sorted too .........

It takes 30 mins to do a clean install once you have the disk ..... get the latest version of Mint if you have not already got it.
and try again ......

---

### Post by givemewindows on 2010-09-09
yep :(

---

### Post by nothingspecial on 2010-09-09
I`ve got to go

This is what I found

[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

If you want to undo what I have said,to get to where you were before I butted in, one line at a time

[SIZE=4][COLOR=Red]please copy and paste this next bit, if you try to type it and get it wrong you will hose the entire installation[/COLOR][/SIZE]

Which I imagine you wouldn`t mind doing anyway :D

```
sudo rm -r /lib/firmware/b43
sudo rm -r /lib/firmware/b43legacy
sudo apt-get remove b43-fwcutter
``` 

At least we got a few seconds..........

---

### Post by 23dornot23d on 2010-09-09
I noticed he had the apt-get work from the prompt - well back in the thread .... so unless he was hard wired then ..... the wifi was working ok ...... just a guess so asked for confirmation ..... and if it worked then that proves that there is nothing wrong with the wifi ...... on the original system .... be it 9.04 9.10 or 10.04.
[Here's some links that may be useful]("http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+forums+b43-all&ie=utf-8&oe=utf-8")
a re-install usually takes 30 mins ..... if you get the version that detects the wireless your problems are solved. (MINT 9 possibly) 
But need to know which version so we can get the equivalent working ..... carry on .... did not mean to butt in but thought the info might be useful ...... to you ......):P

---

### Post by givemewindows on 2010-09-09
> **nothingspecial said:**
> I`ve got to go

This is what I found

[http://www.omattos.com/node/6](http://www.omattos.com/node/6)

If you want to undo what I have said,to get to where you were before I butted in, one line at a time

[SIZE=4][COLOR=Red]please copy and paste this next bit, if you try to type it and get it wrong you will hose the entire installation[/COLOR][/SIZE]

Which I imagine you wouldn`t mind doing anyway :D

```
sudo rm -r /lib/firmware/b43
sudo rm -r /lib/firmware/b43legacy
sudo apt-get remove b43-fwcutter
```At least we got a few seconds..........
ive been copying and pasting.. ill try this.
> **23dornot23d said:**
> I noticed he had the apt-get work from the prompt - well back in the thread .... so unless he was hard wired then ..... the wifi was working ok ...... just a guess so asked for confirmation ..... and if it worked then that proves that there is nothing wrong with the wifi ...... on the original system .... be it 9.04 9.10 or 10.04.

But need to know which version so we can get the equivalent working ..... carry on .... did not mean to butt in but thought the info might be useful ...... to you ......):P
im at work.. ive got it plugged up to the ethernet here. trying to set up wifi bc its my gfs computer and she only has wireless at home, school, and work.

---

### Post by 23dornot23d on 2010-09-09
Which version of Mint  ?

Do 

**uname -a** 

in a console and post the output .... it will give us an idea.

We can check you are up to date too with the system / drivers etc

do these commands to get everything uptodate as possible too if you still have a wired connection
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade

I run a [number of Linux systems]("https://sites.google.com/site/23dornot23d/home/matrix---what-works-on-what-system") on my laptop .... and these were the ones that picked up ok for me from install 
you can usually find some versions of LINUX that will pick up everything first time ,,, although if you want to carry
on and troubleshoot the Wifi ..... there are things that can be learned along the way ,,, 
I usually just pick the quickest method to fix things nowadays though.
If burning a new CD and installing it can solve everything in one go - now you have experience at doing it 
is the best time to do another one ...... whats to loose ...... they are all free and you may get to like one of them.


Ok best of luck with whatever you do ....

---

### Post by givemewindows on 2010-09-09
laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

i just want my wifi to work so i can be done messing with this thing.

---

### Post by nick_goodfate on 2010-09-09
> **givemewindows said:**
> 
i really really hate linux. this is ridiculous.


> **givemewindows said:**
> 
unaware that it came with ubuntu. I hate it.


> **givemewindows said:**
> 
jesus i dont see how anyone could willingly want to use this garbage.


> **givemewindows said:**
> 
if i had bought it from dell i wouldnt have gotten linux to start with.


> **givemewindows said:**
> 
im typing this on my dell with vista, thats never given me an ounce of trouble, no matter how much music+videos+games ive downloaded..


> **givemewindows said:**
> 
my uber cool linux computer is currently a F%#@$ paperweight and noone seems to know why.


#-o
I really admire all those people here that trying to help you! They are some of the reasons i love ubuntu...

My recommendation: Go for windows... Windows are awesome !!!!!\\:D/

---

### Post by givemewindows on 2010-09-09
> **nick_goodfate said:**
> #-o
I really admire all those people here that trying to help you! They are some of the reasons i love ubuntu...
 
My recommendation: Go for windows... Windows are awesome !!!!!\\:D/
 The people helping have been great. Linux has been rubbish.

---

### Post by Fableflame on 2010-09-09
> **givemewindows said:**
> The people helping have been great. Linux has been rubbish.

Linux isn't so bad.
The problem is you clearly got a broken computer, or a computer with a broken OS because you bought from Craigslist. If you had downloaded Ubuntu and put it on a computer that was functioning correctly, you could've installed a fresh install of Ubuntu (or any other Linux OS for that matter) with a proper GUI that didn't leave you stuck at the command prompt on boot.

Don't take this as me being rude, but don't blame Linux because you bought a broken computer/OS off someone. Something like this should be expected to happen when buying from Craigslist. If you can't verify that it works as it should before you buy it, you shouldn't buy it.

---

### Post by jtarin on 2010-09-09
We tend to ridicule what is not understandable to us.It's human nature.

---

### Post by beew on 2010-09-09
> Something like this should be expected to happen when buying from  Craigslist. If you can't verify that it works as it should before you  buy it, you shouldn't buy it.

So maybe the OP can solve his problem by selling his PC on craiglist to someone else? That person will probably show up here and complaining that Linux sucks. :)

---

### Post by TCHebb on 2010-09-09
Have you tried going to Menu>System>Hardware Drivers and installing the Broadcom driver there?

EDIT: Whoops, spoke too soon. I just saw that you're on Mint and not Ubuntu. You might want to try asking [there]("http://forums.linuxmint.com/") instead of here.[__]("http://forums.linuxmint.com/")[]("http://forums.linuxmint.com/")

---

### Post by givemewindows on 2010-09-09
> **Fableflame said:**
> Linux isn't so bad.
The problem is you clearly got a broken computer, or a computer with a broken OS because you bought from Craigslist. If you had downloaded Ubuntu and put it on a computer that was functioning correctly, you could've installed a fresh install of Ubuntu (or any other Linux OS for that matter) with a proper GUI that didn't leave you stuck at the command prompt on boot.
 
Don't take this as me being rude, but don't blame Linux because you bought a broken computer/OS off someone. Something like this should be expected to happen when buying from Craigslist. If you can't verify that it works as it should before you buy it, you shouldn't buy it.
 I have it functioning now, i fixed the OS, im running whatever the newest linux mint is, and alls well except that for some reason now it has no wireless drivers. Which why you would offer a netbook specific DL without including wifi drivers is beyond me, but whatever. 
 
So now i have a functioning OS, and no wifi. So no, im not real thrilled with linux at all. 
> **jtarin said:**
> We tend to ridicule what is not understandable to us.It's human nature.
 Yeah, I guess so. I just dont see how the so called "easiest OS to use" is the biggest computer headache ive ever had. And ive yet to really find one thing about linux (other than the people on this board trying to help me fix this thing) thats really groundbreaking or standout. I hate the fact that everything has to be done via a terminal. I feel like im in windows 3.1 again. I hate that you have to memorize ten thousand codes just to do simple processes. I really dont like that my VZW wireless card isnt recognized by it at all. 
 
I guess you guys see something i dont. Because honestly i havent found anything that i really like about it yet. The games on ubuntu were cooler. i guess i could say that.
 
Not trying to be rude, just honest. I dont see what all the commotion is over. Honestly, linux mint to me is just basically a wal mart version of windows anyway. 
 
i dont know. i just really want my wifi to work so i can be done with this thing. By the time i get all these codes to actually work the semester will be over.

---

### Post by scottuss on 2010-09-09
> **nick_goodfate said:**
> #-o
I really admire all those people here that trying to help you! They are some of the reasons i love ubuntu...

My recommendation: Go for windows... Windows are awesome !!!!!\\:D/

I totally agree. If I went to a Windows forum asking how to get rid of Windows so that I could install Linux I'd get told where to go. I appreciate that both communities have different attitudes, and whilst that's good, this guy hasn't exactly been the most deserving of the patience he has been shown.

All I can say is, this community is a testament to the Linux world.

---

### Post by nick_goodfate on 2010-09-09
> **givemewindows said:**
> I have it functioning now, i fixed the OS, im running whatever the newest linux mint is, and alls well except that for some reason now it has no wireless drivers. Which why you would offer a netbook specific DL without including wifi drivers is beyond me, but whatever. 
 
So now i have a functioning OS, and no wifi. So no, im not real thrilled with linux at all. 

 Yeah, I guess so. I just dont see how the so called "easiest OS to use" is the biggest computer headache ive ever had. And ive yet to really find one thing about linux (other than the people on this board trying to help me fix this thing) thats really groundbreaking or standout. I hate the fact that everything has to be done via a terminal. I feel like im in windows 3.1 again. I hate that you have to memorize ten thousand codes just to do simple processes. I really dont like that my VZW wireless card isnt recognized by it at all. 
 
I guess you guys see something i dont. Because honestly i havent found anything that i really like about it yet. The games on ubuntu were cooler. i guess i could say that.
 
Not trying to be rude, just honest. I dont see what all the commotion is over. Honestly, linux mint to me is just basically a wal mart version of windows anyway. 
 
i dont know. i just really want my wifi to work so i can be done with this thing. By the time i get all these codes to actually work the semester will be over.

You have used linux for... one day? When you first saw windows what was your reaction? Anyway, you started this thread by saying you hate linux, at your very first post. If you have decided you hate linux just format your f%$@#%#$^$%&^$%&ng hard drive and install the rubbish you want! I really can't see the point of this thread...

---

### Post by 23dornot23d on 2010-09-09
So the first part should be like this ,,,,,,, I am now running in **Mint 9** the same as you are .....


keith@keith-laptop ~ $ uname -a
Linux keith-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
keith@keith-laptop ~ $ sudo modprobe -l |grep b43
[sudo] password for keith: 
kernel/drivers/net/wireless/b43/b43.ko
kernel/drivers/net/wireless/b43legacy/b43legacy.ko
keith@keith-laptop ~ $

---

### Post by nothingspecial on 2010-09-09
Right, I`ve fed and bathed my smaller kid and taken the older one to football and returned. I`m going to bed in a minute.

Right now we have someone who doesn`t really want linux, doesn`t understand linux, expects linux to behave like windows and is stuck with it.

His problem is he has a broadcom wireless card which are a pain in the *** for someone who doesn`t know what to do. Especially if it`s his girlfriends laptop and he`s supposed to be the one who knows about computers.

**%$**!!% my wife would be going mad

As far as I know the bc43-fwcutter package should fix it but apparently it doesn`t.

I think the guy is understandably pissed off. 

Let`s not slate him because his computer doesn`t work. Like I said I have to sleep. The problem is the broadcom wireless card.

---

### Post by beew on 2010-09-09
Does he say he has Mint installed that looks like a cheap Windows? I don't know about Mint but he probably has a KDE desktop. Well for some reasons I was never able to get KDE to work with wireless. I have installed or tried Ubuntu on several machines with different wireless cards (*including different models of broadcom cards*) and they all work nicely. But never KDE,  a guy at work tried to install kubuntu and couldn't get wireless either, so there may be a bug in the knetwork manager.

---

### Post by Chris1274 on 2010-09-09
> **TCHebb said:**
> Have you tried going to Menu>System>Hardware Drivers and installing the Broadcom driver there?

EDIT: Whoops, spoke too soon. I just saw that you're on Mint and not Ubuntu. You might want to try asking [there]("http://forums.linuxmint.com/") instead of here.

In this respect there's no difference between Mint and Ubuntu. I'm using Mint on a machine with a Broadcom wifi card and the procedure for installing the driver was the same.

---

### Post by 23dornot23d on 2010-09-09
If its a fresh install it will be Gnome not KDE ......

Apparently [this Link solved it]("http://wiki.debian.org/bcm43xx") for one of the MINT users ....... the original topic is here if you want to read through it all [LINK]("http://forum.linuxmint.com/viewtopic.php?f=141&t=54668&start=0")

---

### Post by Rasa1111 on 2010-09-09
> why you would offer a netbook specific DL without including wifi drivers is beyond me, but whatever. 
So now i have a functioning OS, and no wifi. So no, im not real thrilled with linux at all. 


dont know, never used mint. 

but if you had a computer in proper working order, 
and could have just installed Ubuntu on it~
Ive never seen ubuntu not be able to connect, to wireless or wired. 
Everything it needs, it has, and has always done exactly what it should.. "just work". 

. 
>  I hate the fact that everything has to be done via a terminal. I feel like im in windows 3.1 again. I hate that you have to memorize ten thousand codes just to do simple processes.

Lots of hate ,man,
not healthy. 

When I was uneducated, I also thought everything had to be done via terminal.
But now that i know better,
 I never have to use the terminal for anything if I dont want to. 

 and you dont have to remember any codes if you dont care to. 
and you can get along perfectly fine without remembering codes or using terminal constantly. 

 If your computer worked, and did what it should,
you wouldnt have had to use the terminal once if you didnt want to.

I operate my Ubuntu system just as I did my windows system. 
Point, click, drag, move, etc. 

I only use the terminal when I feel like it , for fun or to understand it better.,
and it is sometimes fun. 

you just cant have a head full of old FUD. 

Seriously,
if my ancient family members and their friends can use ubuntu no problem,
without ever even opening the terminal..
 well.. 

yeah...

 you just bought something from a shady person from a shady place that didnt work as it should have. 

 That's all. 
(and you love windows). lol

2 or 3 years ago I couldnt fathom myself being able to use Linux, 
it was always ; 
" man, id love to, but ill never be able to learn all that just to run an OS".  lol

but that to, was old FUD, and i just didnt know any better.

 It (Ubuntu) truly is easier to use and maintain than windows ever was. 

Linux mint..
never even cared to test it out... lol

---

### Post by 23dornot23d on 2010-09-09
There is one more thing ..... make sure that the wifi ..... is not switched off in the BIOS ...... 
some people switch this off to save battery life ..... it may well have been done by the previous owner.

---

### Post by givemewindows on 2010-09-09
its not that im closed to learning new things, its just that this setup isnt very noob friendly. Had this forum not been here i would have already shot the thing with a 12 gauge and bought another one. The only reason this thing is functional at all now, is because of what ive learned on here. 
 
Its all just really really frustrating. i just want it to work. 
 
 
Right now when you turn it on itll acknowledge there are wireless connections, then, before you can connect to them they disappear. If you go into drivers in control panel, then itll show two drivers, and at the top it says no proprietary drivers in use. the driver thats in use is a free one, and when you try and remove it it throws an error and if you try to activate the second one, it freezes the computer. 
 
 
and yet again, im not trying to be rude guys, this is just really really really frustrating. Ive been at this for two days and i just want the thing to work so i can give it away and never have to see it again. Ill go back to my other laptop and all will be fine in the world. All of you have been very helpful, and i truly appreciate that. Whats so frustrating is this software isnt very noob friendly when youre trying to set it up, and theres no clear answers out there. Googling is an afterthought, and the only things ive found that have done anything is advice from you guys.

---

### Post by 23dornot23d on 2010-09-09
Did you do the commands to update 

open a terminal and put these into it one at a time ..... it will ask you to enter your password first .... before executing the commands

sudo apt-get update                                                             [COLOR=Blue] 
This command just updates a list of new software available ......
[/COLOR] 
sudo apt-get install aptitude                                                   [COLOR=Blue]
This command loads a updater that checks for dependancies and errors ......[/COLOR]

sudo aptitude update                                                            
[COLOR=Blue] This command updates the list it uses[/COLOR]

sudo aptitude install b43-fwcutter wireless-tools                      
[COLOR=Blue] This command gets the software and drivers you need for your Wifi to work[/COLOR]

sudo aptitude safe-upgrade                                                   [COLOR=Blue] 
This command does a last check to make sure that everything is at its latest revisions available[/COLOR]


There may be a few more steps to come ..... but please do all the commands above in a terminal.

I just need to know your system is uptodate and using the latest available drivers.

This is all free software and once its working it runs better than any Windows System I have ever used ,,, so please stop slatting it
once you have it running - then you can try it out ..... and slate it all you like ......... 
I really do not need to know .... how bad it is ..... !!!

[B]I also need to know that you have followed the commands and if there is any output - that looks bad or fails post it ......

Post the output after doing this too in a terminal - if you would please cut and paste it ... its LSPCI .... but in lowercase

[/B]lspci -nn

*( the information will be useful to others should I have to leave - its now 1:44 am here. )
for example the lines we need will look something like this .......

07:00.0 Network controller [0280]: Atheros Communications Inc. [COLOR=Blue]AR928X Wireless Network Adapter[/COLOR] (PCI-Express) [168c:002a] (rev 01)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)

---

### Post by spillin_dylan on 2010-09-09
> its not that im closed to learning new things, its just that this setup isnt very noob friendly

It's not necessarily that the setup isn't noob-friendly, but it sounds like you were definitely dealt a bad hand with your netbook, too.  Please try to understand it's not always this difficult to install a Linux system, and there is a ton of hardware out there that "just works" with Linux.  

For some reason you got the bad luck of not only a broken OS to start with, now you have to fight a WiFi driver problem too.  

I wish you luck, and am glad you have the patience to learn some new things, even if it's really slow going....

---

### Post by 23dornot23d on 2010-09-09
In the olden days ..... 

I would try 3 or 4 different Distros ..... then try each one in turn until one suited my system.

Mandriva it is now - it used to be Mandrake 7.1 was my first came on 3.5" Floppy Disks ...
Caledra was another
SUSE has been around for long enough
Kanotix - the first to do what was a very easy install picking up most devices first time.


Now as I said earlier ..... it may be easier and quicker to download some and try them out . 

Here are the 3 that I would try with my knowledge of what might be best for you after reading all your comments about LINUX.

There is always a solution ....... never give in .

[Zorin]("http://zorin-os.webs.com/download.htm") .............. very much a look a like windows setup with familiar commands.
[Fedora 13]("http://fedoraproject.org/get-fedora") ........ just picked up everything first time install for me.
[Ubuntu 10.04]("http://www.ubuntu.com/desktop/get-ubuntu/download") .... what the majority are probably using now on here, and in one month from today the very latest and greatest 10.10 will be released

---

### Post by TCHebb on 2010-09-09
I'm surprised no one has mentioned this yet... You could check Dell's website for a Mini 910 CD image. That would have all the Dell drivers, and would "just work," as you put it.

EDIT: Wow, I'm having bad luck with all my posts in this thread. I forgot that you said the guy on Craigslist had put Linux on himself :P

---

### Post by DougieFresh4U on 2010-09-09
You could always check[ PinguyOS]("http://www.pinguyos.smffy.com/index.php/topic,2.0.html") as it should have all you need to get you up and running without having to go here and there. It will require a DVD as it's to big for cd.
I triple boot my machine with :
Windows XP
Ubuntu Maverick Meerkat 10.10
PinguyOS Lucid 10.04

---

### Post by 23dornot23d on 2010-09-09
As far as I know from what I read here he has spent some time on the phone with Dell.
Is this the Link you mean [Dell]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=181316") .......

 [Pinguyos broadcom]("http://www.google.com/search?client=ubuntu&channel=fs&q=pinguyos+broadcom&ie=utf-8&oe=utf-8") ...... does broadcom work ok with it ?

There is still no reason why we cannot get the Wifi going here ..... its just how long it takes,
and it sounds like it would be a shotgun - or a new computer .... 
if the guy is rich maybe he will buy her a new one
with Windows 7 on it .........

I gave the quicker options in my opinion ..... as we could have to try different repositories for
updated drivers here ...... unless there is a quicker fix someone has not told us about yet.

Maybe someone with the same computer on here that has it running ok could give the answer to
why his from craigslist is not working ..... we still do not know for sure if its faulty or not !!!

Time will tell .... I have a feeling the Wifi is turned off in the BIOS ....

He needs to know how to check the BIOS ..... settings first ...... usually done by holding f10 down at boot
or some other key [del] maybe ..... it usually states it at the startup ....... which key to press.
Then go through the settings and just do a check ..... otherwise we may all be wasting our time.

I guess this is the fix he needs .... once he is sure that Wifi is activated and working .....
.. but think he has tried a similar approach already and it froze on him 

The same things needed in this  [LINK]("http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html") may be in synaptic for mint ..... 

I will have a look now ........ yep seems to be ok - maybe just a case of following the instructions in the link then .... no problem

Menu - Administration - Synaptic Package Manager

[IMG]http://i51.tinypic.com/sm6az6.jpg[/IMG]
[URL="http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html"]
[/URL]

---

### Post by DougieFresh4U on 2010-09-09
> **23dornot23d said:**
> As far as I know from what I read here he has spent some time on the phone with Dell.
Is this the Link you mean [Dell]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=181316") .......

 [Pinguyos broadcom]("http://www.google.com/search?client=ubuntu&channel=fs&q=pinguyos+broadcom&ie=utf-8&oe=utf-8") ...... does broadcom work ok with it ?

There is still no reason why we cannot get the Wifi going here ..... its just how long it takes,
and it sounds like it would be a shotgun - or a new computer .... 
if the guy is rich maybe he will buy her a new one
with Windows 7 on it .........

I gave the quicker options in my opinion ..... as we could have to try different repositories for
updated drivers here ...... unless there is a quicker fix someone has not told us about yet.

Maybe someone with the same computer on here that has it running ok could give the answer to
why his from craigslist is not working ..... we still do not know for sure if its faulty or not !!!

Time will tell .... I have a feeling the Wifi is turned off in the BIOS ....

He needs to know how to check the BIOS ..... settings first ...... usually done by holding f10 down at boot
or some other key [del] maybe ..... it usually states it at the startup ....... which key to press.
Then go through the settings and just do a check ..... otherwise we may all be wasting our time.

I guess this is the fix he needs .... once he is sure that Wifi is activated and working .....
.. but think he has tried a similar approach already and it froze on him 

The same things needed in this  [LINK]("http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html") may be in synaptic for mint ..... 

I will have a look now ........ yep seems to be ok - maybe just a case of following the instructions in the link then .... no problem

Menu - Administration - Synaptic Package Manager

[IMG]http://i51.tinypic.com/sm6az6.jpg[/IMG]
[URL="http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html"]
[/URL]

I think it's great that you have gone to great lengths to help the OP with this=D>
I sincerely hope that he/she hangs in there and gets it all situated.

---

### Post by 23dornot23d on 2010-09-09
Cheers and thanks ..... me too ..... 

I am sure they have just taken a break .... from what I gather ,,,
The person can only work on it from work ..... so it makes it awkward.

They will get it sorted they have not gone all this way to fail .... ;)

---

### Post by jtarin on 2010-09-10
Is it a forum rule when quoting someone to include their half-page pic plus their entire dialog in e-book format?:lolflag:

Just asking.:p

---

### Post by anewguy on 2010-09-10
23dornot23d - thanks for all your insight on this thread.  I don't know enough about what the OP has going (did someone strip down/modify/etc. the Linux that is installed?  Is there an /etc/xorg.conf file that perhaps needs to be deletec? etc., etc., etc.).

Your knowledge and helping this user is just another of those great reasons that this forum is great like it is!

Dave

---

### Post by 23dornot23d on 2010-09-10
Nice - at least in the future things should be easier ..... 

[Broadcom - announce open source drivers]("http://ubuntuforums.org/showthread.php?t=1571407")

---

### Post by perspectoff on 2010-09-10
> **givemewindows said:**
> bought a laptop for my girlfriend (dell inspiron 910) unaware that it came with ubuntu. I hate it. 
 
Well, right now im stuck at a command prompt (similar to dos) that says
 
user@user-laptop:~$
 
Dunno why it randomly decided to get stuck there today, wasnt doing it yesterday. 
 
 
so thats a start.. once i can get back in ill have a few more questions. 
 
Please help me fix this so i can get this mess off of here.


Cool. I'll take it. Mail it here!

---

### Post by anewguy on 2010-09-10
Ah gee, I was hoping I might get it!  ;) ;)

Dave ;)

BTW - like the post about Broadcom releasing open source drivers.

---

### Post by pinguy on 2010-09-10
> **23dornot23d said:**
> 
[Pinguyos broadcom]("http://www.google.com/search?client=ubuntu&channel=fs&q=pinguyos+broadcom&ie=utf-8&oe=utf-8") ...... does broadcom work ok with it ?

Some do but not all. [http://p2w.com.au/blog/pinguy-os-review/](http://p2w.com.au/blog/pinguy-os-review/)

---

### Post by 23dornot23d on 2010-09-10
Ok .... downloading PinguyOS now ...... ty ...... will have to make some space and add it to my other installs ..... cheers .... ;)

It looks good ..... I like it ..... conky pre-installed and docky too .... and its fast ..... looks like its based on mint too with the menu
(I only did one alteration upto now - replaced docky for [Cairo-dock as docky was not as responsive on my machine ]("http://i52.tinypic.com/x4nj1h.jpg").... I am also used to cairo-dock)
so no big deal .... they both do the same job ..... 

Very fast install too for 1.3gig .... dvd .... liking it - I will add another version tonight and upgrade the source files to [Maverick 10.10 ]("http://i55.tinypic.com/2m455yv.jpg").....
conky went - so replaced it with superkaramba ... transparancy and everything works well ....
(now docky is fast ..... so am leaving it in the [Maverick version]("http://i51.tinypic.com/1zl4xh3.jpg") - still in development though its - [10.10.2010 ]("http://i51.tinypic.com/2w5j5hh.jpg").... when the new version is released fully)


The wireless picked up as did everything else ...... just upgraded the graphics driver by picking add new driver ...... easy.

Maybe the OP should try it out too ..... ):P  nothing to lose ..... unless he sorted it ..... or reverted to Windows.

We all make choices 

Whatever he has chosen I hope it works well ,

---

### Post by nick_goodfate on 2010-10-05
I remember OP had uploaded a screen shot but i can't find it now ...
I think he might just was logging in a xterm session, is it possible to be that the problem ? :-k

---

### Post by givemewindows on 2010-10-14
well to those who wondered, i went back with xp. i tried 3 or 4 different flavors of linux, and they were all the most horrible worthless garbage ive ever used. i appreciate those that helped me answer some questions, but id rather eat broken glass than ever use this **** again.

---

### Post by nothingspecial on 2010-10-14
> **givemewindows said:**
> well to those who wondered, i went back with xp. i tried 3 or 4 different flavors of linux, and they were all the most horrible worthless garbage ive ever used. i appreciate those that helped me answer some questions, but id rather eat broken glass than ever use this **** again.


Happy windows, enjoy it :)

---

### Post by beew on 2010-10-14
> **givemewindows said:**
> well to those who wondered, i went back with xp. i tried 3 or 4 different flavors of linux, and they were all the most horrible worthless garbage ive ever used. i appreciate those that helped me answer some questions, but id rather eat broken glass than ever use this **** again.


I think it is just because you are rather incompetent.:) And with that suck *** attitude starting from your first post it is a true wonder that so many people were willing to help. Try go to a windows forum and tell them you try to get your Mac working bacause windows is garbage and see what happens.

---

### Post by jtarin on 2010-10-14
> **givemewindows said:**
> well to those who wondered, i went back with xp. i tried 3 or 4 different flavors of linux, and they were all the most horrible worthless garbage ive ever used. i appreciate those that helped me answer some questions, but id rather eat broken glass than ever use this **** again.
Impossible statement as you couldn't get the easiest distro to work for you.

---

### Post by RetchingRabbit on 2010-10-14
> **givemewindows said:**
> if youre curious, this is what im looking at. 
 
 
[IMG]http://i165.photobucket.com/albums/u59/cnote05300/Mobile%20Uploads/IMG00036-20100907-1437.jpg[/IMG]

That picture looks like the symptom of a full /home partition.

---

### Post by overdrank on 2010-10-14
> **givemewindows said:**
> well to those who wondered, i went back with xp. i tried 3 or 4 different flavors of linux, and they were all the most horrible worthless garbage ive ever used. i appreciate those that helped me answer some questions, but id rather eat broken glass than ever use this **** again.

Ok best of luck to you. If you decide you need help again please start a new thread.
Thread closed.

---

