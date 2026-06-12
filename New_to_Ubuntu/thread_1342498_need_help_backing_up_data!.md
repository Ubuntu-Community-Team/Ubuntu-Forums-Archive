---
title: "need help backing up data!"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by axleman1011 on 2009-11-30
ok i had some trouble with vista and long story short it stoped working so i temporaraly installed ubuntu so that i could recover any data before i tryed to accualy install anything... (you know just in case anythng goes wrong...) basicly i need help with three things...
 
1) i can't figure out how to connect to the internet!
 
2) it won't let me insert a disk to back up my data! (i don't have any USB storage available at the moment)
 
3)i am missing th efiles that were on my desktop before windows failed... where can i find them?
 
if you can help with any of these problems please tell me... i need my laptop working by tomarow or i will get an F on my school assinment!!!
 
ps: i am not a total idiot, but i have never used ubuntu before...

---

### Post by SunnyRabbiera on 2009-11-30
well you have internet connection right now, on another computer?

Anyhow:
1: what kind of internet do you have?

2: do you know the brand of your CD/DVD burner?

3: well are you able to see your windows drive on Ubuntu?
Like a link on your desktop?
Usually ubuntu's pretty good with windows drives, so you will hopefully have access to your files.

---

### Post by axleman1011 on 2009-11-30
1) firefox ;) (right now i am on my old desktop...)
 
2) i just use what my laptop came with... (it says compact disk rewriting...:confused:)
 
3) i see a windows folder but no sine of the programs i had saved to my desktop...

---

### Post by SunnyRabbiera on 2009-11-30
Are you able to use firefox in Ubuntu, does it connect?
Have you ever used firefox before?
As for connection to the net is this a wired connection or wireless?
Is this a laptop or desktop?
As for windows, its good that your Ubuntu sees it. 
But as for your programs, depending on what you use there might or might not be a linux alternative to them.
What programs on windows do you use the most?
Just so you know the icons on your windows desktop are not the actual programs, they are called shortcuts.
Desktop shortcuts in windows are there for "ease of use" but in Ubuntu you really dont get desktop icons unless you set them yourself.
There is a reason for this, for most too many icons on the desktop makes the computer look cluttered.
Ubuntu and most other Linux distro's dont favor desktop icons and rely more on system menu's, but Ubuntu and linux is not alone in this. OSX also does not have a lot of icons set by default either.

Anyhow I ask these questions because I am trying to assess your situation

---

### Post by kristine12 on 2009-11-30
You can see the file on your desktop @

 "C:\Documents and Settings\_*USERNAME_*\Desktop" on windows.

You can also browse your files using Ubuntu with the same directory then back it up from there.

---

### Post by SunnyRabbiera on 2009-11-30
> **kristine12 said:**
> You can see the file on your desktop @

 "C:\Documents and Settings\_*USERNAME_*\Desktop" on windows.

You can also browse your files using Ubuntu with the same directory then back it up from there.

Just without the C:\ Directory, C:\ drives dont exist in Linux :D

---

### Post by kristine12 on 2009-11-30
If you cannot access your Windows HDD on your Ubuntu. I know that there is a setting there where you can actually allow all the HDD to be fused (but the thing is I don't know where to find that setting).  After doing that, you can know see the HDD on the Places Menu @ the top panel.

---------------------------------------------------------------------------------------------------------

I think the setting can be found @
System -> Administration -> Authorization and Permission

Not sure about it. But try it. Another thing...
You must be a root to modify rights there.

---

### Post by axleman1011 on 2009-11-30
i have used firefox before, it cannot connect to server...
wireless, it worked when i had vista, and yes, i know my ip adress (127.0.0.1)
 
it is a laptop, (dell inspron 1525...)
 
in the windows file i see a few of the programs i had (system32, 7-zip, ijji, etc...) but i also see alot more files i don't rember... (Branding... Prefetch, OEM02Cfg.exe, twain.dll, etc...)
 
i can see the reason for not having so many desktop icons but i had alot of files saved to the desktop because vista couldn't find them when they were tucked away in their sub-sub-temp-folders...

---

### Post by SunnyRabbiera on 2009-11-30
> **kristine12 said:**
> If you cannot access your Windows HDD on your Ubuntu. I know that there is a setting there where you can actually allow all the HDD to be fused (but the thing is I don't know where to find that setting).  After doing that, you can know see the HDD on the Places Menu @ the top panel.

---------------------------------------------------------------------------------------------------------

I think the setting can be found @
System -> Administration -> Authorization and Permission

Not sure about it. But try it. Another thing...
You must be a root to modify rights there.

Well apparently he can see his windows drive so no worries about him not seeing it.

---

### Post by axleman1011 on 2009-11-30
but i am not sure i can get anything out of this windows drive... it is mostly alpha-numaric sequences .exe, .dll, .log, or .ini

---

### Post by axleman1011 on 2009-11-30
woops i am sorry, i feel like an idiot now... i have been looking at the wrong windows files... :oops:
 
ok i think i found the right file now... dang... "Unable to mount location"

---

### Post by Some Penguin on 2009-11-30
> **axleman1011 said:**
> i have used firefox before, it cannot connect to server...
wireless, it worked when i had vista, and yes, i know my ip adress (127.0.0.1)

*All* machines can refer to themselves by 127.0.0.1.  It's a dummy address.

 > **axleman1011 said:**
> 
it is a laptop, (dell inspron 1525...)
 
in the windows file i see a few of the programs i had (system32, 7-zip, ijji, etc...) but i also see alot more files i don't rember... (Branding... Prefetch, OEM02Cfg.exe, twain.dll, etc...)
 
i can see the reason for not having so many desktop icons but i had alot of files saved to the desktop because vista couldn't find them when they were tucked away in their sub-sub-temp-folders...

Sounds like you're wandering around the main Windows directory rather than your user's data directory.  You probably want the latter.    Judging by [http://en.wikipedia.org/wiki/Home_directory](http://en.wikipedia.org/wiki/Home_directory) you should be looking for a Users/ directory.

---

### Post by axleman1011 on 2009-11-30
ya i just realised that... also i don't wanna give out a real ip address where anyone in the world can access it...

---

### Post by SunnyRabbiera on 2009-11-30
Is the drive protected?
As for your wireless, hmm...
I will do some digging on your model.
Is it possible for you to hook your laptop up to a hardwired connection, like a LAN?
Depending on your wireless card there might be some workarounds you might have to do, and sometimes its not all that easy.
There are some wireless cards that are really hard to work with in Ubuntu, its not Ubuntu's fault though as most devices out there only have windows in mind.

Edit: argh you have a broadcom wireless card its no wonder you have no connection.
Actually you may want to use something like Linux Mint instead of ubuntu as it comes with some tools that cannot be installed by default in Ubuntu.

---

### Post by axleman1011 on 2009-11-30
ya i know what you mean... i don't have any cales to conect my computer because i got rid of those yeasr ago... i do have a little net-rear USB router thing but it is installed on a diffrent computer and the instlation disk wipes itself after you use it once... 
 
i don't think it a secure file, i had a password for my account but i don't see how that would matter... that is more of a user protection...

---

### Post by SunnyRabbiera on 2009-11-30
> **axleman1011 said:**
> ya i know what you mean... i don't have any cales to conect my computer because i got rid of those yeasr ago... i do have a little net-rear USB router thing but it is installed on a diffrent computer and the instlation disk wipes itself after you use it once... 
 
i don't think it a secure file, i had a password for my account but i don't see how that would matter... that is more of a user protection...

Still might matter though, anyhow do you have another computer nearby?
I still suggest you burn Linux Mint and use that as an alternate, for most it helps with the broadcom cards.
Lucky for you Linux mint is based on Ubuntu, so you can still come here for help with your issues.

---

### Post by axleman1011 on 2009-11-30
sigh... so i have to burn a whole new CD? is there any way to move my hard-drive on to a CD now?

---

### Post by SunnyRabbiera on 2009-11-30
> **axleman1011 said:**
> sigh... so i have to burn a whole new CD? is there any way to move my hard-drive on to a CD now?

Err no, unless you have some sort of super CD with ultra high capacity or something.
In the future maybe you should save up for a external drive.
I only suggest Mint as it might save you some headaches with setting up wireless.

---

### Post by almufadado on 2009-11-30
First download and burn ubuntu live cd

Get [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/) bootable and burn it

To backup your drive there are 2 ways:

If there is free space on the drive that has windows you can :

Boot hirenbootcd and choose boot from the cd 
(just press enter in all those cdrom options and see if it works)  
**choose Mini Windows Xp**

run "cmd"  
run "defrag c:"
and if you have another partition as drive d:  
run "defrag d:"

This to deframent you drive and be more secure when repartition you drive
If 


Reset and boot from ubuntu life cd 

choose live cd and check if you windows drives are in the Places menu

Check if you have at least 10GB for ubuntu 

If you upgrade to vista check both
c:\documents and settings\_user_\desktop
c:\documents and settings\_user_\my documents
c:\documents and settings\_user_\application data ->you will find firefox profile, game saves, graphics apps data, etc)
  
and 
c:\users\<user>\

---

### Post by axleman1011 on 2009-12-01
> **almufadado said:**
> First download and burn ubuntu live cd
 
Get [http://www.hirensbootcd.net/](http://www.hirensbootcd.net/) bootable and burn it
 
To backup your drive there are 2 ways:
 
If there is free space on the drive that has windows you can :
 
Boot hirenbootcd and choose boot from the cd 
(just press enter in all those cdrom options and see if it works) 
**choose Mini Windows Xp**
 
run "cmd" 
run "defrag c:"
and if you have another partition as drive d: 
run "defrag d:"
 
This to deframent you drive and be more secure when repartition you drive
If 
 
 
Reset and boot from ubuntu life cd 
 
choose live cd and check if you windows drives are in the Places menu
 
Check if you have at least 10GB for ubuntu 
 
If you upgrade to vista check both
c:\documents and settings\_user_\desktop
c:\documents and settings\_user_\my documents
c:\documents and settings\_user_\application data ->you will find firefox profile, game saves, graphics apps data, etc)
 
and 
c:\users\<user>\
 
 
you don't seem to understand... without the ubuntu disk in i can't access ANYTHING! (other than BIOS) and as cool as ubuntu is, i would rather have windows be my primary OS... 
 
also i only have 1 disk drive... i have 4 USB ports but i don't have a thumb drive big enough to contain my entiar hard-drive!
 
it is VISTA not XP
 
 
 
and i think i figured out the problem... can i access partitions with ubuntu?

---

### Post by axleman1011 on 2009-12-01
just wondering are we allowed to bump threads if the problem hasn't been solved yet?

---

