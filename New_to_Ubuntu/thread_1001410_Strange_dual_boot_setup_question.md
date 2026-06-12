---
title: "Strange dual boot setup question"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by skatetokil on 2008-12-03
Did a search and I don't think this has been covered.  If so, point me in the right direction, and thanks in advance.

I have been running Ubuntu 8.1 happily on one of my main machine for a couple of weeks, and I definitely plan to stick with it as my primary OS.  I friend gave me a pile of parts and I ordered some new stuff, including a 400gb SATA hard drive which is home to the install. 

HOWEVER, I am increasingly doing work that requires windows, mostly GIS stuff.  

I have a decent but older XP Pro machine with an 80gb IDE drive, and I have been switching the monitor/kb/mouse back and forth when I need to use it.  

I no longer have an install disk so I need to keep that HD/install intact whatever I do, but the cable switching is getting to be annoying, not to mention having 2 towers on my desk. 

Basically, I want to know what will happen if I hook up the old drive in the new machine (yes the motherboard supports both inputs).  Will I get a prompt to select between the OSs?  Is there something else I need to do other than plug em up?

---

### Post by Miljet on 2008-12-03
You will need to install GRUB on whichever disk that you intend to boot off of. (Your post wasn't entirely too clear on that.) Anyway this is the best tutorial on GRUB that I have found.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by handydan918 on 2008-12-03
You will not be able to install a Windows drive in a different machine and expect it to work. I have been able to do this with Linux every time I've tried, but never Windows. 
However, I would consider dropping 30 bux or so on a [KVM]("http://www.iogear.com/solutions/kvm/")...

---

### Post by mapes12 on 2008-12-04
I have Ubuntu on one box and XP on another. They sit side by side but I only use one keyboard, mouse & monitor like this: [http://en.wikipedia.org/wiki/KVM_switch](http://en.wikipedia.org/wiki/KVM_switch)

KVM switches are fairly cheap. I got mine off ebay. You just press a button on the switch to toggle back and forth between the two boxes. Fast and easy.

Running XP and Ubu on the same base unit as a dual boot is too risky in my humble opinion. Been there and got the **T** shirt.

---

### Post by handydan918 on 2008-12-04
> **mapes12 said:**
> 
Running XP and Ubu on the same base unit as a dual boot is too risky in my humble opinion. Been there and got the **T** shirt.

Right. I've installed literally dozens of dual-boot setups over the last 6-8 years. Never lost data. Maybe you just need to read a good HOW-TO, or find a LUG to guide you through it. The only real issue is understanding partitioning.

---

### Post by billgoldberg on 2008-12-04
> **handydan918 said:**
> Right. I've installed literally dozens of dual-boot setups over the last 6-8 years. Never lost data. Maybe you just need to read a good HOW-TO, or find a LUG to guide you through it. The only real issue is understanding partitioning.

I'm glad you said it, so I don't have to.

--

To OP:

Why don't you just drop the new drive into the xp machine?

And use a switch like people suggested.

---

### Post by tarps87 on 2008-12-04
> **handydan918 said:**
> You will not be able to install a Windows drive in a different machine and expect it to work. I have been able to do this with Linux every time I've tried, but never Windows.

I have succeed with XP, I had to install the drivers as you would expect, but have only tried it once.
(I thought the drive was an old blank drive :))

If you want to duel boot you may be able to set the XP drive as a slave and add it to the boot list in Ubuntu. XP may have issues with this as it likes being a the start of the master hard drive, in which case you will have to install GRUB, this can be done from the Ubuntu cd, this may help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

An alternative is setting up remote desktop on the XP box and connecting to it from Ubuntu, one of the two pre installed remote desktop programs (on Ubuntu) will do this but I can not remember its name. You are looking for the one that supports RDP
To allow remote desktop connections in XP Control Panel -> System -> Remote (tab) and tick allow remote users to connect. (This does require your XP user to have a password)

---

### Post by mapes12 on 2008-12-04
> Maybe you just need to read a good HOW-TO

Keith Parkansky has written one of the best guides available: [http://www.aboutdebian.com/linux.htm](http://www.aboutdebian.com/linux.htm)

See the section "The Safe Way to Play"

---

### Post by theozzlives on 2008-12-04
I have a A/B switch to move the monitor/keyb/mouse that I bought at Radio Shack for about 10.00. Just the push of a button, that's it.

---

### Post by skatetokil on 2008-12-04
> **billgoldberg said:**
> I'm glad you said it, so I don't have to.

--

To OP:

Why don't you just drop the new drive into the xp machine?

And use a switch like people suggested.


Thanks for the advice so far.  The reason I don't do this is my Windows computer is the slower of the two, and the motherboard doesn't even support the SATA drive.  

Alright, so what's the realistic downside of plugging up the windows drive in the new machine and seeing what it does?  Is windows going to eat itself or is it just going to not run?  I assume that even if it doesn't run, the old drive would be visible to Ubuntu and I could at least transfer all my data to the new drive before trying a more dangerous approach.  

Also as I understood grub it just provides a clean gui for a function that already exists in the bios.  Am I getting it wrong and is it really essential?

---

### Post by mapes12 on 2008-12-04
handydan918 said > Right. I've installed literally dozens of dual-boot setups over the last 6-8 years. Never lost data. Maybe you just need to read a good HOW-TO, or find a LUG to guide you through it. The only real issue is understanding partitioning.and 9 mins ago a new post appears > ok, i wanted to try ubuntu before but i messed up and made a mistake and accidentally erased my whole hard drive when i wanted to dual boot and it didnt recognize anything, not even my wifi card so i re installed XP. now i want to try it again but everything i try it doesnt work. im going to try to be as specific as i can. first i downloaded the 8.10 and burned it and then installed it on to a partition i have called "backup" which is D: i used 10 gigs and set my name and password and then i restarted my computer and selected to boot ubuntu then it said while counting down "press esc to go to menu" i didnt and then ubuntu loaded and installed it, later i tried booting it again and it loaded and i entered my name and password and then it begins to load goes to a black screen with the loading icon frozen. i tried restarting over and over but it did the same thing. later i uninstalled it and then tried wubi, i did the same as before but it still didnt work. what am i doing wrong? if im missing any information just ask. thanks in advance.

OP will need to make his/her own decision about the risk they want to take.

---

### Post by handydan918 on 2008-12-04
> **skatetokil said:**
> Thanks for the advice so far.  The reason I don't do this is my Windows computer is the slower of the two, and the motherboard doesn't even support the SATA drive.  

Alright, so what's the realistic downside of plugging up the windows drive in the new machine and seeing what it does?  Is windows going to eat itself or is it just going to not run?  I assume that even if it doesn't run, the old drive would be visible to Ubuntu and I could at least transfer all my data to the new drive before trying a more dangerous approach.  
Nah, it won't self destruct. It just won't run. And you should certainly be able to mount it in Ubu and tranfer files off of it...> 
Also as I understood grub it just provides a clean gui for a function that already exists in the bios.  Am I getting it wrong and is it really essential?
Boy, if you can get the bios to do what GRUB does, tell me how! I have had as many as 12 different O/S's on a system, all on one hard drive, and GRUB never even hiccupped. You can easily set any given O/S as default, load virtually any O/S you can name, (not just Linux and Windoesn't).

:)

---

### Post by handydan918 on 2008-12-04
> **mapes12 said:**
> handydan918 said and yet just 9 mins ago a new post appears 

OP will need to make his/her own decision about the risk they want to take.

Can you spell PEBKAC?
Any one can screw anything up. Nothing is foolproof, because fools are so ingenious.


):P

:p

---

### Post by skatetokil on 2008-12-04
Grub does sound neato, but I'm not running off a partition, I'd just be selecting which hard drive to boot from.

---

### Post by lincoln32 on 2008-12-04
If I read you post right, the only problem is that windows is registerd to the old computer and ms tracks by prossor id so if you move the hard drive to new computer you will have to contact ms on first boot and fill out a form at ms and tell them old pc was m/b failure or simular and they will give you a code to reacivate windows to the new pc id. one computer per windows operating system. I have scrapped old computers and built new and did this to have a genuine windows system. and use a dual boot from there. best of both worlds. although kvm would allow both computers to operate at the same time with out rebooting
to change system. grub can work with two drives but would have to shut off and reboot to change systems

---

### Post by skatetokil on 2008-12-04
How does one go about contacting ms?  Will it prompt me or do I have to go through their customer service people.  The windows install I'm running came from a university from which I have since graduated, so hopefully that won't cause me a problem.

---

### Post by tarps87 on 2008-12-05
If you need to it will prompt on first boot, I don't think I had to with XP but it may have been a 'altered' version. With vista I couldn't do a clean install on a lager hard drive in the same machine (This was also a university version but I was still at the university so they gave me a second licence key, this was two years ago and still haven't got a solution from ms).
Looking at your post you are using xp so it should prompt.

@mapes12 that is down to careless partitioning, in this set-up the partitioning is already done and the black screen is a graphics problem.
I am using a duel boot on five system for about two years, three with xp, one with vista and one with arch and haven't lost any data so far

> **skatetokil said:**
> Grub does sound neato, but I'm not running off a partition, I'd just be selecting which hard drive to boot from.

Grub is already on the Ubuntu drive and is used to boot it, ms have there own bootloader but this won't detect other os's.
If you are want to select which drive to use in the bios, this should be possible by disabling the other drive or changing the boot order(Not all bios allow you to set which drive to boot from). (I this is what you mean?)
If you can get the xp drive to work in the other machine it would be worth setting the Ubuntu drive as the boot/master drive and updating the GRUB as it will be more efficient.

---

### Post by lincoln32 on 2008-12-05
It will give you a screen that says contact MS with a install number and a phone number. Call that number and follow directions it is a computer and it will tell you to speak the install number and gives you a new install number then type in and you back to genuine windows. you paid for legal copy
so this there way of moving it. I have a xp pro 
I got when it first came out and have moved it thru three computer upgrades
and several reloads--reloads go thu since it is registered to that pc

---

### Post by psusi on 2008-12-05
> **skatetokil said:**
> 
Also as I understood grub it just provides a clean gui for a function that already exists in the bios.  Am I getting it wrong and is it really essential?

The bios only knows how to read the first sector of the disk into memory and execute it.  It is a pretty dumb beast.  Grub stage 1 goes in that sector and loads stage 2, which is smart enough to understand the filesystem and find and interpret /boot/grub/menu.lst, which tells it what options to put on the menu and how to implement them.

---

### Post by skatetokil on 2008-12-19
Ok, so I plugged in the old windows hd and it mounted right up and gave me access to my files no problem.  At the very least I now have all my data on the ubuntu box.  

However, it didn't even let me try to run windows.  I guess my next step is to go fishing in the bios and change up my boot sequence so that it prompts me at startup.  Going to read more about grub cause it sounds like there is a better way.

  
Thanks for the help so far, no exploded hard drives :guitar:

---

### Post by caljohnsmith on 2008-12-19
> **skatetokil said:**
> Ok, so I plugged in the old windows hd and it mounted right up and gave me access to my files no problem.  At the very least I now have all my data on the ubuntu box.  

However, it didn't even let me try to run windows.  I guess my next step is to go fishing in the bios and change up my boot sequence so that it prompts me at startup.  Going to read more about grub cause it sounds like there is a better way.

  
Thanks for the help so far, no exploded hard drives :guitar:
If you want some help booting Windows from your Grub menu, how about opening a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what it might take to boot Windows from your Grub menu. :)

---

