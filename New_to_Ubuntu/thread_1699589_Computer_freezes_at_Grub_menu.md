---
title: "Computer freezes at Grub menu"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by what-is-a-computer? on 2011-03-03
Can anyone please tell me how to get my computer from "unfreezing" at the grub menu at the words "starting up?"  It will not go beyond that.

Another strange thing is that even when the computer is off, the keyboard "Num Lock" is still lit.  I tried another keyboard and it's the same thing.  Once I unplug the computer, then that light goes off.  But it stays lit once I try to start the computer again and stays lit even if I turn the computer off.

I tried booting in the recovery mode.  At the very end it says:

7.417107 pci 000:00:01:1: PME# disabled.

Does that help?

Thank you!

---

### Post by what-is-a-computer? on 2011-03-08
No brilliant men to resolve this issue?    My computer freezes at the words  "starting up" and no one can resolve it?  

Oh, well.  That means this computer has been reduced to a door stop.  

I think I'll pull out my old Xandros laptop...........that still works.

---

### Post by Dutch70 on 2011-03-08
> **what-is-a-computer? said:**
> No brilliant men to resolve this issue?    My computer freezes at the words  "starting up" and no one can resolve it?  

Oh, well.  That means this computer has been reduced to a door stop.  

I think I'll pull out my old Xandros laptop...........that still works.

I'm certainly no expert, but you'd probably get more offers for help if you gave a little info. Such as, some computer specs maybe, how bout which version of Ubuntu, or is it even Ubuntu that you're using?. Anything that you've done, has it ever worked, when did you install it?

---

### Post by what-is-a-computer? on 2011-03-08
Thank you so much for responding, Dutch.

Ubuntu, Jaunty (Please don't ask me to upgrade yet.  I will soon.) is what I'm using.

Worked perfectly and has with no problem.    My mouse froze last week.    So I turned off the computer with the power button.    It's like it will not turn off now.  It freezes at the words "starting up."  Oh, and it no longer goes forward on its own as it used to.  It stops at F2, BIOS and F10, boot order.  

So I put in an Acronis boot disk, booted from the CDROM  and tried a different kernel in the grub menu.  I was finally able to see my desktop.  

That was last Friday.    I got no responses or help on the forum all day Friday, nor over the weekend.   So I gave up.  

This morning I exited out of my desktop and shut down the computer to try to just redo the whole computer with a passport drive image that I have, using Acronis.  And now I cannot get into my desktop at all with any of the kernels through the grub menu.  

Also, when I plug in my passport drive and use my Acronis CD,  once I click on "recovery within acronis, my screen goes black and I can see nothing.

My keyboard number lock stays lit even though my computer is off.  I have to hold the "power" button in a long time and the computer finally turns off,  but but the keyboard number lock stays lit as well as the passport drive.  The blue power button goes off but not the other stuff.  I have to pull the power cord in order for my keyboard/passport drive to go off.

If I boot with the Acronis CD and select "hard drive," it gets as far as "starting up" and then just freezes there.   I don't know what to do.  I should have left it running this morning and then someone maybe could have told me what to type in a terminal but unfortunately that's gone.  I cannot get back to that screen.

Any help would be appreciated.  Thank you so much for at least responding.  I don't know what other questions to answer.  I'm such a novice at all of this.

---

### Post by what-is-a-computer? on 2011-03-08
Correction:  When I said it stopped at F2-BIOS and F10, boot, it just hesitates and then loads grub and that's where it freezes, where it says "starting up."

Another thing:  I just went in and tried it again.  If I unplug the computer from the power cord, everything goes black and the computer if off.  If I plug the power cord back in, instead of having to turn on the power button, it comes on on its own and the computer tries to start up again.

Also, I just tried to boot from a live CD and it starts and then just completely like "powers down"  and stops.

And as info, this is basically a brand new computer.  I just had it in a box as a backup but it worked perfectly.  I took it out of the box  and used it all last week with no issue until the mouse froze and fell on the floor and it zapped everything.

Surely it's just something minor.

---

### Post by what-is-a-computer? on 2011-03-08
Does this help?  Oh, my gosh.  I just plugged in the power cord, and of course the computer came on on its own without me pushing the power button,  and I came in here and wrote the last reply to this thread, went back in the other room, and I'm at my desktop on the computer.  The live CD is in the CDROM drive.  So....

Now that I'm in my desktop, is there anything I can type in a terminal to check something that I need to check to make sure it boots properly?  Anything in grub (whatever that is), etc.?  Anything like "reinstall grub" or "remount" grub.  I don't know what any of it is.  I just know I see it on the screen when I'm booting.  

Pleeeeeeeeeeeeeeeeeeeeeeeeeeeeeease.  

Then I could just put the image back on this computer with my passport drive.  I'm just scared to turn it off, but I would have to in order to boot the CDROM with the acronis CD...which wasn't working earlier.  Does any of that make sense?

---

### Post by JKyleOKC on 2011-03-08
Many recent (within the last 5 years or so) machines have some "always-on" features that are not controlled by the power switch, but can be turned off only by unplugging the power cord. The network cards on this machine have that strange property. Its purpose is to allow the power switch to be operated remotely from another machine, even though the vast majority of home systems never make use of this capability. Your keyboard light staying on may be something similar, but I've never encountered such a situation myself in more than 40 years of dealing with computers from micros to mainframes.

As for determining what's going on with your machine, go to this thread: [http://ubuntuforums.org/showthread.php?t=1702290](http://ubuntuforums.org/showthread.php?t=1702290) and read post #5. Do what it says there and post the result. That will show us a pretty complete picture of what is in your machine and will help greatly in figuring out what you need to do to fix it!

Stopping the machine by turning off the power frequently results in severe damage to the file system and should be avoided whenever possible -- but sometimes it's the only alternative. If that is what has happened to you it will probably be necessary to reinstall everything, losing all your data. However that's a worst-case scenario, and let's hope that you have better alternatives. The "results.txt" file should show us, and the fact that you got it up and running again bodes well for the final outcome.

EDIT: The automatic turn-on is a feature controlled by a BIOS setting, that you can turn off by going into BIOS at boot time. It's quite helpful in some cases, but annoying in others. Let's get the boot process cleaned up and we can then walk you through turning off automatic power-up if you want to do so.

---

### Post by what-is-a-computer? on 2011-03-08
Jim, bad news.

I lost my graphics on my machine.  Everything went squiggly on the screen.  So I had to turn the computer off.

Now I cannot get my desktop back.

Give me a few minutes here.  I don't know how I got them back the first time.  I just walked away and left the computer.

Also, does this help?  When I boot the live CD, the first thing that comes up is "language."  There is a countdown to the left of the word "English."  Once that counts down to zero, I can reach up and press the power button once and the computer goes off along with the keyboard.

If I click on that and then try to "boot from the first hard drive," it sticks at "starting up" again.  Then when I try to turn off the computer, I have to hold the power button in a long time, not just push it.  At that point, I have to unplug the machine to restart it.

This is a real mess.  However, if I can just get my desktop back and do the command you suggested that may help.

One moment, please.  And thanks a million!

---

### Post by Dutch70 on 2011-03-09
That's all out of my league :)

Sounds like it may be overheating. Stick it in the freezer man...lol j/k, but I've done that. :-\" To recover pics & docs. 
 Make sure it has plenty of air flow from the vents.

I just want to add...
If you don't have any external media to save your most important files to, in case of a reinstall. Use dropbox. 
[[COLOR="Blue"]https://www.dropbox.com/referrals/NTE2MTIwMzg5[/COLOR]]("https://www.dropbox.com/referrals/NTE2MTIwMzg5")

To avoid doing a hard reboot in the future, hold down the <Alt & Sys Rq> keys, while pressing the following keys with a slight pause between each one. R-E-I-S-U-B and your pc should reboot. You may have to let off the >alt & sys rq< buttons before letting off the "B" depending on your keyboard.

---

### Post by what-is-a-computer? on 2011-03-09
Tried until late to get this to work.  It won't.

What is the best course, to put in a new hard drive?

I don't know what else to do.

---

### Post by what-is-a-computer? on 2011-03-09
Jim, I've probably damaged the file system because I turned it off/on so many times, as you alluded to in your previous messages.  Rats!

---

### Post by what-is-a-computer? on 2011-03-09
Is it possible that this is a hardware issue, the CDROM?

---

### Post by JKyleOKC on 2011-03-09
It might be an overheating problem. I had one machine that would garble its video display when it got too hot, and would automatically reboot itself. Try pulling the power cord and letting it sit for an hour or so, then boot again. If it then comes up okay, it's most likely a heat problem. The internal fans do collect a lot of dust, and if you have pets in the house also get clogged up with bits of fur that they shed. I routinely use a portable vacuum on all the air vents to suck out what it can and this helps.

If you do get a usable boot with the Live CD, choose the "Try without installing" option to have a chance at downloading and running the script. This won't make much if any use of the hard disk so any damage there will have minimal impact on getting the results to us.

---

### Post by what-is-a-computer? on 2011-03-09
Jim, I opened up the case by unscrewing the back.  I have never seen so many wires and stuff in my life.

Anyway, there was a bit of dust on those fans but not much.  I wiped it off.
I left it unplugged all night but when I plugged it back in, the blue power light came on on its own.  

What I should have done was put in the acronis disk and clicked on "turn off the computer."  That's the only way I can turn off the blue power button quickly is with that command or when I try to boot with the live CD by letting the number counter to the right of "English" count down to zero.  Then I can turn off my power by literally pushing the button.  So I'll go in and try that and THEN unplug the back and let it sit for an hour or so.  Otherwise, the computer doesn't seem to really be off.

I'm going to try putting the live CD disk in again -- I tried late last night and it would not boot -- and press "enter" on the first selection which is "try but do not install."  I did that last night and it just hung at "starting up."  The screen was frozen there.

Thanks.  TTYS.

Oh, and BTW, last night when I would try to boot, I would hear the CDROM running and then it would just shut down and then nothing.

---

### Post by owiknowi on 2011-03-09
just another thought on how it all came to be:
has the power cable also a ground connection? i've had a lot of problems myself with not properly grounded pc's.

btw. you've chosen a proper nickname: what is a computer?
answer: a catch22... ;)

---

### Post by what-is-a-computer? on 2011-03-09
Very funny, Oki.  :D

Yes, that's why I chose the name.  I know zip about computers, only my software.  That's why I have these issues.  When one little thing goes wrong, I'm toast.

Speaking of toast, I've done something.  I took out my hard drive and put in another that was a "spare" that my ex-teacher told me to keep on hand.  I've never done that in my life.  I just unscrewed all the screws and finally figured it out.  I turned on my computer and could see nothing.  So I took it out and put the old one back. 

I've turned on the computer and now it does not recognize my monitor, keyboard nor the mouse.   What's up with that?  I know that monitor works because I've hooked it up to other computers.  Oh, and when I turned it back on, I could hear this loud, constant beeping.  So I took out the CMOS battery which I learned about for the very first time yesterday that I was told to replace because my BIOS would not save any changes.  Once I took out that battery, it has quit beeping.  Of course, it's not recognizing any of my peripherals.

As far as the outlet being grounded, I just have it plugged into a big extension cord that is plugged into the wall.  I assumed any house outlet is properly grounded.

I'll take any suggestions and do what anyone says.  Just please don't tell me something is fried....like the mother board.  I'm not up to it.

---

### Post by owiknowi on 2011-03-10
alas, not every power outlet has a ground connection (here in holland that is).
don't know about the rest of the world or galaxy. you can see if it has by the number of pins/connectors the cable has (three means it has, two it doesn't).

just one thingy: make sure when you take a tour in the insides of your pc you are grounded too.
no, i'm not joking or mocking you: statical electricity ruins many pc (especially memory and motherboards).

and indeed the cmos battery needs to be replaced every now and then (my guess is every 4 years?)

and hopefully a bit for your comfort: computers aren't build to last and computer specialists don't exist in real life...

---

### Post by what-is-a-computer? on 2011-03-10
thank you, oki. 

Yes, it has three prongs.  So it's grounded.  All of my outlets here in the US have three prongs.  

I've probably ruined it.  Today, when I get time, I'm going to put in a different set of memory chips and see if that's the issue.  I turned it on this morning......nothing:  no monitor, no mouse, no keyboard.

I read up on it yesterday and it says to re-seat the memory chips.  I finally found that "memory chip" item behind my hard disk/CDROM.  It was hard to find.  It has those plastic clips at the top and bottom.    So I removed it and put it back in yesterday and still not working.   Hope I haven't ruined the mo.b.  Now that I know where it is/what it is, I'm going to another another one of those.  

Oh, and last night, I wiggled the power cord that I know is perfect because I tested it on another computer.  And it made my computer go on without pushing the power button.    So those three prongs on the computer where I plug in the power cord, there may be an issue there.

We'll see what happens.  Thank you for helping me.
Have a wonderful day in Holland.

---

### Post by what-is-a-computer? on 2011-03-10
I mean "Owi"

---

### Post by owiknowi on 2011-03-10
hope all goes well!

oki or owi: just differs one letter but whole different meaning according to john steinbeck ;)

---

### Post by runeh76 on 2011-03-10
Try to install Ubuntu with LiveCD to ur second Hard-disk. I think ur HD have problems! U can also use GSmarttool to check ur HD.

[http://www.addictivetips.com/ubuntu-linux-tips/using-gsmartcontrol-in-ubuntu-linux/]("http://www.addictivetips.com/ubuntu-linux-tips/using-gsmartcontrol-in-ubuntu-linux/")

If its not in the LiveCD, install it from recovery mode:
```
sudo apt-get install gsmartcontrol
```

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> thank you, oki. 

Yes, it has three prongs.  So it's grounded.  All of my outlets here in the US have three prongs.  

I've probably ruined it.  Today, when I get time, I'm going to put in a different set of memory chips and see if that's the issue.  I turned it on this morning......nothing:  no monitor, no mouse, no keyboard.

I read up on it yesterday and it says to re-seat the memory chips.  I finally found that "memory chip" item behind my hard disk/CDROM.  It was hard to find.  It has those plastic clips at the top and bottom.    So I removed it and put it back in yesterday and still not working.   Hope I haven't ruined the mo.b.  Now that I know where it is/what it is, I'm going to another another one of those.  

Oh, and last night, I wiggled the power cord that I know is perfect because I tested it on another computer.  And it made my computer go on without pushing the power button.    So those three prongs on the computer where I plug in the power cord, there may be an issue there.

We'll see what happens.  Thank you for helping me.
Have a wonderful day in Holland.

I started to tell you last night to lose the extension cord, getting the proper amount of power to  your system is extremely important, or you will do serious damage. If you wiggle the power cord and it affects your pc at all, then you've got a short somewhere. Make absolutely sure you're getting a good connection before you take another step to fix anything. 

Also, are you unplugging the pc, then hitting the power button to release any stored electricity before you touch anything inside? If not, that's very dangerous. Also, are you touching the power supply or something metal inside of it to discharge any static ele. you have in your body before touching anything else? If not, you can definitely fry your mobo. 

I'm curious how you know your keyboard & mouse aren't working if your monitor isn't working. What is your monitor doing? Is it a yellow light on the front, or do you get the red,white,blue thing moving across the screen? I know I've thrown a lot at you there, but answer as best you can, and I'll help with what I can.

---

### Post by what-is-a-computer? on 2011-03-10
Woo-hooooooooooooo!

Just re-seated those memory chips.  I added another. So now I have two.    I didn't realize you have to push so hard.  Those clips finally clicked and locked into place.   So now, believe it or not, the monitor/keyboard/mouse are working.

I had to reset the BIOS.  So I've done that.  

I cannot believe that I could so this.  I'm a complete and total novice and I opened up this machine and changed the RAM.  I'm not bragging.  I'm shocked actually.  I watched a video -----  three times, of course -- on how to change the RAM.  So helpful.  

Anyway, I just tried to tried to boot with a Live Ubuntu CD and clicked on the first one as Jim Kyle  suggested.  It says  "Install without changing your system" or whatever it says.  I got an error message that said "problems with CD or system (I don't remember)" and then "reboot."  So I rebooted.  My computer is stuck, as before, at "starting up."

But at least my monitor/mouse/keyboard are working.  That's progress.

Also as suggested by Dutch, I'm going to lose the extension cord.  I'll see if any of that helps.  And, no, I hadn't touched the metal inside my computer to ground myself.  I didn't know I was supposed to.  I do now.  Yikes!

thank you!

---

### Post by what-is-a-computer? on 2011-03-10
PS  Dutch, the reason I knew that the monitor/keyboard/mouse were not working, when I turned on my computer, there were no lights on the keyboard and the blue light did not come on on the monitor.  I just made an assumption on the mouse because of the other two.

At least that's fixed now.

Now on to the other issue of the short.

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> Woo-hooooooooooooo!

Just re-seated those memory chips.  I added another. So now I have two.    I didn't realize you have to push so hard.  Those clips finally clicked and locked into place.   So now, believe it or not, the monitor/keyboard/mouse are working.

I had to reset the BIOS.  So I've done that.  

I cannot believe that I could so this.  I'm a complete and total novice and I opened up this machine and changed the RAM.  I'm not bragging.  I'm shocked actually.  I watched a video -----  three times, of course -- on how to change the RAM.  So helpful.  

Anyway, I just tried to tried to boot with a Live Ubuntu CD and clicked on the first one as Jim Kyle  suggested.  It says  "Install without changing your system" or whatever it says.  I got an error message that said "problems with CD or system (I don't remember)" and then "reboot."  So I rebooted.  My computer is stuck, as before, at "starting up."

But at least my monitor/mouse/keyboard are working.  That's progress.

Also as suggested by Dutch, I'm going to lose the extension cord.  I'll see if any of that helps.  And, no, I hadn't touched the metal inside my computer to ground myself.  I didn't know I was supposed to.  I do now.  Yikes!

thank you!

Nice work! You keep this up, you're gonna have to change your user name. :P

Just to make sure you've got it straight, you press the power button **after** you unplug it to discharge any built up electricity in the machine. Your fan may spin when you hit it, even though it's unplugged. 

You touch metal inside the pc, preferably the power supply, to discharge any static electricity that's in your body. You know how you rub your feet on the carpet & you can shock someone. That's more than enough energy to fry your mobo. It won't hurt you though. AFAIK

Is there another computer you can try your live cd on? Can you use a usb stick/flash drive? 
You may need to go with Xubuntu btw. if your pc can't handle Ubuntu.

---

### Post by what-is-a-computer? on 2011-03-10
Okay.  I turned off the machine with the power button.....even though the "num lock" is still lit.

I changed my BIOS to have it boot to the CDROM.  I have the live CD in there.
I clicked on "English" and selected "check the CD" because my neighbor said maybe there's something wrong with your boot disk.

This is the error message:  I/O error.  Error reading boot CD"  And then there's a square that says "reboot."

So????????????????

Is it the boot CD?  What's I/O?  The only thing I have heard of is an I/OPCI  serial card.  I don't know what it does but I have one I believe on this computer.  Does that have anything to do with booting a computer?

---

### Post by what-is-a-computer? on 2011-03-10
Okay.

I just tried again to select "Try Ubuntu without changing your system"

I get the same message as when I selected "check disk for defects."

Here's the error message:  
  I/O error.  Error reading boot CD"  And then there's a square that says "reboot."
If I reboot it goes back to the same window.  Because I change my setting in BIOS to boot to the CDROM, it, of course, goes back to that.

If I select my hard drive as the first boot-up option in BIOS but click on F10, the boot menu, and select CDROM so that it boots from the CDROM, get the error message in there about rebooting and click on "reboot," it then goes to the hard drive and freezes at "starting up" just as before.

Any suggestions?

---

### Post by runeh76 on 2011-03-10
Make with Clonezilla *.IMG from ur HD Ubuntu installation and "put" it to ur second HD.
[http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/")


Edit: Link above to server, here it is:
[http://clonezilla.org/]("http://clonezilla.org/")

---

### Post by what-is-a-computer? on 2011-03-10
I will here shortly!  Thanks!


Should I change to the new second hard drive first and try that or do this?  You said that in your previous message and I just have not had a chance to try that.

---

### Post by runeh76 on 2011-03-10
Try GSmartcontrol to check ur HD condition, u dont lose nothing and u learn something  ;)

---

### Post by what-is-a-computer? on 2011-03-10
i have obviously misunderstood you, now that I think about it.  At first I thought you meant to put in the second NEW hard drive that I purchased.  I think you mean to have both computers connected to the internet, click on the link and then....

To do what you say, I would have to have the non-functioning computer  plugged into the internet.  I only have one connection on the back of this modem from my cable company for my internet connection.  So this working computer that I'm using is plugged into the internet.  Don't you need other devices for hooking up two?  I don't have it.  A splitter?  I don't know.

Did I neglect to tell you that I also have wire/setup-computer-equipment issues?  :D
Once it's set up, I absolutely don't touch it.  Otherwise, things happen.

I'll call a computer store and ask them what I need.  I know on telephones you have a splitter.

---

### Post by JKyleOKC on 2011-03-10
It's possible that when you replaced the hard drive, you disturbed the connector on the CD drive and that could be causing the errors. It's also possible that it's a jumper problem if your drives are the PATA type rather than SATA. Newer machines mostly use SATA, which has two rather small connectors, one for power and the other for data. The older PATA drives have larger connectors: the data one has 40 pins arranged in two rows and the power one has four larger pins in a single row, exactly like many of the other power connectors to the motherboard and maybe the fans.

If your drives are the PATA variety, they will have a third small connector at the rear of the drive, which usually has a little black jumper plugged into it to short two of the pins together. The sets the drive to be a master, slave, or cable-select. Most PCs avoided use of cable-select, sticking with either master or slave. The motherboard will have two 40-pin connectors, each with a cable on it that has two plugs at its other end. This allows a total of four drives, one master and one slave on each of two channels. Usually the HD is set to be master on one channel and the CD is set as master on the other; these settings are made in the BIOS setup. If the drive's jumper doesn't match the BIOS setting, it won't respond at all. This might be a cause of your CD error. Unfortunately the jumper settings vary from one manufacturer to the next, although they are usually explained on the drive's label.

If the drives are SATA, none of that applies; the addressing is handled by other means.

---

### Post by runeh76 on 2011-03-10
GSmartcontrol is in LiveCD 10.10 
Download and burn and put it to ur broken PC and boot from CD.
Then u can see if ur CD-drive is also broken or not!  lol!

---

### Post by what-is-a-computer? on 2011-03-10
I just did another test before I go to the store.   I just put in the brand new hard disk and i'm getting all the same errors.  Error reading boot CD.

Doesn't that pretty much rule out that it's a hard disk issue?  Neither of them works, the old or the new.  

Oh, and another test:  I boot from the Live CD and select "boot from first hard drive."

This is what it says:  "Booting from local disk..." and it's frozen there, just like on the old one it's frozen at "starting up."

Are you sure it's now a power issue; that it's not getting enough power to boot?

And you hear the CDROM drive like shut down.

---

### Post by runeh76 on 2011-03-10
> **what-is-a-computer? said:**
> I just did another test before I go to the store.   **I just put in the brand new hard disk and i'm getting all the same errors.  _Error reading boot CD_.**

Doesn't that pretty much rule out that it's a hard disk issue?  Neither of them works, the old or the new.  

Oh, and another test:  I boot from the Live CD and select "boot from first hard drive."

This is what it says:  "Booting from local disk..." and it's frozen there, just like on the old one it's frozen at "starting up."

Are you sure it's now a power issue; that it's not getting enough power to boot?

And you hear the CDROM drive like shut down.

Did u change BIOS-settings to boot from HD?

---

### Post by what-is-a-computer? on 2011-03-10
Jim, it's SATA, I believe.  I think I saw that word in BIOS plus there are two connectors, and I had already checked both of those.  They are connected.  So it's not that.

Runeh76 - Thank you (she says, rolling her eyes sheepishly)  It probably all broke at once on its own and, I'm sure, not by anything I did.  :)

---

### Post by what-is-a-computer? on 2011-03-10
Yes, I had changed the BIOS back to the 1st device booting as the HD.

---

### Post by what-is-a-computer? on 2011-03-10
The CD ROM roars for about 30 seconds and then powers off.  The green light is not on on the CD ROM.  Does that help?

---

### Post by runeh76 on 2011-03-10
sry, i dont understand so well..did u triple check ur BIOS, that u are booting from Hard-Disk?

---

### Post by what-is-a-computer? on 2011-03-10
I just turned off the machine with the power cord first and then plugged it back in.
The machine came on.  Now it says "Verifying DMI Pool Data Boot from CD (Even though I have it set for booting at HD)

Then it says NVIDIA Boot Agent 249.0542 Copyright, blah, blah, blah
and then PXE-E61: Media test failure, check cable PXE-MOF:  Exiting NVIDIA Boot Agent.
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

---

### Post by runeh76 on 2011-03-10
Okey now its booting from HD, but ur HD doesnt have Operating System. Now install it there! lol!

---

### Post by what-is-a-computer? on 2011-03-10
yes.  It's supposed to be booting from the HD.  I have that checked in the BIOS.
One second.

Okay.  I just checked it.  Even though it says to boot from the HD as the first device, it goes to the CMROM automatically.

I do have the option to press F10 also and do it that way and select HD.  But it's set properly in the BIOS as the HD.

Hmmmm.

---

### Post by runeh76 on 2011-03-10
When u change ur BIOS-settings, u MUST SAVE when ur done!

---

### Post by what-is-a-computer? on 2011-03-10
when it says put in system disk and click "enter" I do that.  Then I see the Ubuntu splash screen with:
Try Ubuntu without any change to your computer
Install ubuntu
check disc for defects
test memory
boot from first hard disk

If I click on the first one, my machine is frozen.  Then it says the error about the I/O and "reboot."

If I click on the second one, "install Ubuntu" exact same thing.  My machine is frozen for awhile and then it gives the I/O error I described previously.  "i/o Error.  Error reading boot CD.  Reboot.

Am I missing something?  What am I doing wrong?

---

### Post by what-is-a-computer? on 2011-03-10
I always press F10 and then save.  I'll try it again.  Maybe I'm not doing that correctly.
One moment!

---

### Post by runeh76 on 2011-03-10
> **what-is-a-computer? said:**
> when it says put in system disk and click "enter" I do that.  Then I see the Ubuntu splash screen with:
Try Ubuntu without any change to your computer
Install ubuntu
check disc for defects
test memory
boot from first hard disk

If I click on the first one, my machine is frozen.  Then it says the error about the I/O and "reboot."

If I click on the second one, "install Ubuntu" exact same thing.  My machine is frozen for awhile and then it gives the I/O error I described previously.  "i/o Error.  Error reading boot CD.  Reboot.

Am I missing something?  What am I doing wrong?

2choices:
-Ur LiveCD is broken
-Ur CD-Drive is broken

---

### Post by what-is-a-computer? on 2011-03-10
I just quadruple (or what's five times) checked it in BIOS, and it's correct as HD 1st device.  When I exit out of that, it boots to the CDROM auto.,  not the HD.  Will it boot to HD if there's no operating system on it?  I know that's a ridiculous question but I honestly don't know.  When it said, previously, "local disk" meaning the new OS-less HD, it was trying to boot with the new HD but froze there.  So....

---

### Post by what-is-a-computer? on 2011-03-10
Okay.  I'll go get a new CD ROM box (whatever you call those.)  thanks!

---

### Post by runeh76 on 2011-03-10
Now, download and burn new LiveCD 10.10 and try that!

---

### Post by what-is-a-computer? on 2011-03-10
I think before I trek to the store (and spend money), Ill put this LiveCD that I downloaded from the internet (I probably goofed that as well) into this working computer and see if the same thing happens.

If it does, it's the CD.  If it doesn't, it's the CDROM.

---

### Post by runeh76 on 2011-03-10
If it works, change that CD-Drive to ur broken PC and try Livecd option--> Try ubuntu

by the way..what Ubuntu version ur Livecd is?

---

### Post by what-is-a-computer? on 2011-03-10
Exciting discovery:  This LiveCD works perfectly in this machine.  It's the CDROM, a hardware problem.

I wonder if it's the cables that attach to the CDROM.

I cannot stand the thought of unplugging all those connections -- monitor/mouse/keyboard, foot pedal, ETH cable and on and on and unscrewing all those screws on the back of the computer and taking out my functioning CDROM and putting it in this computer.  What if it fries it?

Can I think about it?  It may be prudent to go get a new one and ask them if it does not fix the issue, if I can bring it back.  Of course, on the other hand, the thought of going to the store at the moment............ugh!

At least I know it's not the Live CD....which means I did something properly...finally.

---

### Post by what-is-a-computer? on 2011-03-10
PS  All this technology for one day...........I'm exhausted and it's not even noon!:)

---

### Post by what-is-a-computer? on 2011-03-10
PS  9.04 is the version (as I said previously, please don't ask me to change.  I will go to 10.04 as soon as I possibly can, the long-term-support version.)

---

### Post by what-is-a-computer? on 2011-03-10
PS  Except if the issue is the CDROM but I'm booting from my hard drive (which was the begining issue when I had my old HD in), what would the CDROM have to do with booting from the hard Drive?  Doesn't sound right.

Of course, if it's the CDROM AND the hard drive, I can put in a new CDROM that functions, leave in the new hard drive and just use my passport drive image and copy it to this computer.

---

### Post by runeh76 on 2011-03-10
I just asked, becouse GSmartcontrol is available LiveCD 9.10>  :o
Yeah u are learning, and u see computer-dreams now  :)
U could download allready that 10.04 and when u have new hardwares..u know

---

### Post by what-is-a-computer? on 2011-03-10
Problem:  I had to buy an external CD/DVD Drive.  I live in a small town and they don't sell the kind that fit inside the computer.

Anyway, I have attached it, gone into BIOS and defined it as the 4th boot device, "removable," put the live CD in, tried to boot by pushing F10 and it says no removable device is recognized.  It's plugged into the computer.

Any thoughts, anyone?

---

### Post by what-is-a-computer? on 2011-03-10
PS  Also, when I plug in the external device, the little blue light comes on, you can hear it working.  Then it shuts down pretty quickly.

Are you sure this isn't a power issue?  The power cord works perfectly in another computer.  Could it be the power source thing on the back of the computer?

---

### Post by Dutch70 on 2011-03-10
Sorry I've been away & haven't kept up with everything you're doing. Although I did briefly read over it & I have a couple questions.

1. Do you have a usb stick, aka flash/thumb drive???

2. Does your computer have usb ports???

---

### Post by what-is-a-computer? on 2011-03-10
Hi, Dutch.  Welcome back.

Yes, I have a flashdrive and my computer has USB ports and the thing in BIOS says USB controler (one "r") is enabled.

---

### Post by what-is-a-computer? on 2011-03-10
PS  And I just put it in one of the ports and it blinks, so it's reading it, and then the light on it (it has a light) goes steady instead of blinking.

what are you going to recommend; that I download the live CD with my flashdrive?

---

### Post by what-is-a-computer? on 2011-03-10
Uh, I hate to admit this, but I wonder if I downloaded the wrong version.  64-bit?  I probably should have done the other one.  Is that the issue?

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> PS  And I just put it in one of the ports and it blinks, so it's reading it, and then the light on it (it has a light) goes steady instead of blinking.

what are you going to recommend; that I download the live CD with my flashdrive?

OMG, download the .iso  and create a bootable live usb. Much, much better than using a cd/dvd. 
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

Also, if you have a 64 bit processor that should be fine, if not, then you need to get the 32 bit iso.
Download Ubuntu from here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Edit:
Or you can use the universal usb installer from the ubuntu page, I've never used it myself.

*You will have to format your usb stick to FAT32, but it's very simple. There should be howto's on the links I sent you, or google for a video howto.*

Mind if I ask why you are stuck on Jaunty? Up to you, I'm just curious.

---

### Post by what-is-a-computer? on 2011-03-10
Okay.  I'll try it.

No problem.  I'm stuck on Jaunty because I'm not quite ready to upgrade......out of sheer fear.  I just know it won't work properly.  But one of these days.

I'll try this USB thing.

One second.

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> Okay.  I'll try it.

No problem.  I'm stuck on Jaunty because I'm not quite ready to upgrade......out of sheer fear.  I just know it won't work properly.  But one of these days.

I'll try this USB thing.
One second.

I used 8.04 Hardy for about 2yrs. when I 1st started with Ubuntu. I didn't upgrade to 10.04 until about 3mths ago. I kept it a couple weeks & went on up to 10.10. Now I have... well, just have a look at my 2nd hdd, the first one has Ubuntu Maverick & Vista.

---

### Post by what-is-a-computer? on 2011-03-10
That's a gorgeous desktop, Dutch, and with all that stuff, those petitions or whatever.  Looks so complicated.  Now you know why I don't change easily.  And I began with Xandros on my laptop and Edgy (which I still have on a computer), then Feisty and then on and then to Jaunty.  So.....it's hard for me to move on.  I only have one hard drive with all Ubuntu and that's it.  It's just too complicated to understand.

As for my USB stick, it failed.  Since I already have the ISO on my desktop, I went to System, Admin., Startup USB creator, clicked on the ISO, went to my home folder and then on to my desktop.  It tried to get me to do it from root but I had nothing there to click on for the "other" part.  The ISO is not listed at root.

Does that make sense?

It got clear to the end and failed.

---

### Post by what-is-a-computer? on 2011-03-10
i clicked on file system, went to my home folder, to my desktop, clicked on the file, went through the installation, and it failed.

And I right-clicked the properties  on the ISO, went to permissions and it's read/write under my name and the others are read only.  Does that have anything to do with the failure?

And it says to check some log for more info on the failure but I see no log.

I tried to look at the other instructions and they were more complicated.  These were the instructions under the 10.04 and 10.10.

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> That's a gorgeous desktop, Dutch, and with all that stuff, those petitions or whatever.  Looks so complicated.  Now you know why I don't change easily.  And I began with Xandros on my laptop and Edgy (which I still have on a computer), then Feisty and then on and then to Jaunty.  So.....it's hard for me to move on.  I only have one hard drive with all Ubuntu and that's it.  It's just too complicated to understand.

As for my USB stick, it failed.  Since I already have the ISO on my desktop, I went to System, Admin., Startup USB creator, clicked on the ISO, went to my home folder and then on to my desktop.  It tried to get me to do it from root but I had nothing there to click on for the "other" part.  The ISO is not listed at root.

Does that make sense?

It got clear to the end and failed.

Thank you, that's my Kubuntu desktop btw.

I didn't realize you had access to usb/disk creator. Is your usb formatted to FAT32?  I don't want to get off the beaten path here, but if you can create a live usb, that would be soooo much better imho. I also think it may solve the problem with your cd or cdrom.

---

### Post by what-is-a-computer? on 2011-03-10
I know nothing about formatted to FAT32.

I wouldn't know where to begin with that.  I just took it out of the container.  I didn't format it.  I did the thing at terminal with the -ln or something like that.

So.....

---

### Post by what-is-a-computer? on 2011-03-10
i would hate to format it and then not have it work on my computer.  All I did was make a link with it to my export file.    I left it as it was.

---

### Post by what-is-a-computer? on 2011-03-10
usb disk creator is already in Jaunty.

---

### Post by what-is-a-computer? on 2011-03-10
Is this what you do in a terminal?

Code:
 fdisk /dev/sda
mkfs -t vfat /dev/sda1

---

### Post by what-is-a-computer? on 2011-03-10
I have a brand new unopened USB 2GB.  I'll use that one if you'll verify the correct code.
thanks!

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> I have a brand new unopened USB 2GB.  I'll use that one if you'll verify the correct code.
thanks!

Not sure of the code, but you can use gparted.
[[COLOR="Blue"]http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html[/COLOR]]("http://www.ehow.com/how_4963426_format-usb-flash-drive-ubuntu.html")

You know you can also edit a post, so you don't end up with an overload of pages.

---

### Post by what-is-a-computer? on 2011-03-10
if my computer won't recognize an external CDROM, why would it recognize a USB drive?
I would think those would be the same situation.

---

### Post by what-is-a-computer? on 2011-03-10
edit a post?  Uh, no.  How do I edit a post?

---

### Post by Dutch70 on 2011-03-10
> **what-is-a-computer? said:**
> edit a post?  Uh, no.  How do I edit a post?

bottom right corner of your the post you want to edit. :)

---

### Post by what-is-a-computer? on 2011-03-11
Jim, I'm finally into my program.  I just left it on "starting up" for a very long time, just left my computer running.

The screen has finally come on.

I have done what you said:  
sudo bash ~/Desktop/boot_info_script*.sh

The error message is "No such file or directory.

---

### Post by what-is-a-computer? on 2011-03-11
> **JKyleOKC said:**
> Many recent (within the last 5 years or so) machines have some "always-on" features that are not controlled by the power switch, but can be turned off only by unplugging the power cord. The network cards on this machine have that strange property. Its purpose is to allow the power switch to be operated remotely from another machine, even though the vast majority of home systems never make use of this capability. Your keyboard light staying on may be something similar, but I've never encountered such a situation myself in more than 40 years of dealing with computers from micros to mainframes.

As for determining what's going on with your machine, go to this thread: [http://ubuntuforums.org/showthread.php?t=1702290](http://ubuntuforums.org/showthread.php?t=1702290) and read post #5. Do what it says there and post the result. That will show us a pretty complete picture of what is in your machine and will help greatly in figuring out what you need to do to fix it!

Stopping the machine by turning off the power frequently results in severe damage to the file system and should be avoided whenever possible -- but sometimes it's the only alternative. If that is what has happened to you it will probably be necessary to reinstall everything, losing all your data. However that's a worst-case scenario, and let's hope that you have better alternatives. The "results.txt" file should show us, and the fact that you got it up and running again bodes well for the final outcome.

EDIT: The automatic turn-on is a feature controlled by a BIOS setting, that you can turn off by going into BIOS at boot time. It's quite helpful in some cases, but annoying in others. Let's get the boot process cleaned up and we can then walk you through turning off automatic power-up if you want to do so.

Jim, I have done this after Dutch told me I needed to download the sourceforge or something like that.

Anyway, here are the results.  I hope this tells the story!
                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 32.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8fc9515e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   301,186,619   301,186,557  83 Linux
/dev/sda2         301,186,620   312,576,704    11,390,085  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2004 MB, 2004353024 bytes
16 heads, 32 sectors/track, 7646 cylinders, total 3914752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00043db3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,914,751     3,914,720   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        b803da66-c741-459e-b78c-311c48affcb2   ext3                                     
/dev/sda2                                               swap                                     
/dev/sdb1        F216-9F16                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sr0         /media/Ubuntu 9.04 i386  iso9660    (ro,nosuid,nodev,uhelper=hal,uid=1002,utf8)
/dev/sdb1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1002,utf8,umask=077,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

# title        Ubuntu 9.04, kernel 2.6.28-11-generic
# root        (hd0,0)
# kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
# initrd        /boot/initrd.img-2.6.28-11-generic
# quiet

# title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
# root        (hd0,0)
# kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
# initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, kernel 2.6.24-21-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 9.04, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 9.04, kernel 2.6.22-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-15-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.22-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-15-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.22-15-generic

title        Ubuntu 9.04, kernel 2.6.20-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.20-16-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.20-16-generic

title        Ubuntu 9.04, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=b803da66-c741-459e-b78c-311c48affcb2 ro  single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b803da66-c741-459e-b78c-311c48affcb2 / ext3 defaults,errors=remount-ro,relatime 0 1
# Entry for /dev/sda5 :
UUID=4396a8a9-5e84-46db-82f8-01815b59d4d8 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

=================== sda1: Location of files loaded by Grub: ===================


  95.5GB: boot/grub/menu.lst
   1.0GB: boot/grub/stage2
   1.0GB: boot/initrd.img-2.6.20-15-generic
   1.0GB: boot/initrd.img-2.6.20-15-generic.bak
   1.0GB: boot/initrd.img-2.6.20-16-generic
   1.0GB: boot/initrd.img-2.6.20-16-generic.bak
   1.1GB: boot/initrd.img-2.6.22-15-generic
   1.1GB: boot/initrd.img-2.6.22-15-generic.bak
   1.0GB: boot/initrd.img-2.6.24-21-generic
   1.1GB: boot/initrd.img-2.6.24-21-generic.bak
   1.0GB: boot/initrd.img-2.6.27-11-generic
   1.0GB: boot/initrd.img-2.6.27-7-generic
   6.7GB: boot/initrd.img-2.6.28-11-generic
   1.0GB: boot/vmlinuz-2.6.20-15-generic
   1.0GB: boot/vmlinuz-2.6.20-16-generic
   1.0GB: boot/vmlinuz-2.6.22-15-generic
   1.0GB: boot/vmlinuz-2.6.24-21-generic
   1.0GB: boot/vmlinuz-2.6.27-11-generic
   1.0GB: boot/vmlinuz-2.6.27-7-generic
   1.0GB: boot/vmlinuz-2.6.28-11-generic
   6.7GB: initrd.img
   1.0GB: initrd.img.old
   1.0GB: vmlinuz
   1.0GB: vmlinuz.old
```

---

### Post by what-is-a-computer? on 2011-03-11
And the questions I have are:

A.  Why is there so much stuff?  Is that because I kept trying to boot it, using different kernels?

B.  And why is it dated February 15th?  That's not when it became frozen.  It froze on March 3rd while I was attempting to copy audio files from a digital recorder.

C.  If I turn my computer off now, will it boot up properly or now that you have "the story" does something need to be configured properly?

Any help would be appreciated.  I'm not going to turn the computer off for fear that it will not start again.  

I cannot thank everyone enough for your help.  I'm so glad to be able to see my screen.

---

### Post by what-is-a-computer? on 2011-03-11
good morning!

So that we can make quick work of this and I can quit taking up people's time, I will make the following suggestion:  This non-booting computer is an image of the computer I'm working on now.  So if someone can tell me what to type in a terminal to find the boot settings on this computer, I can look at them and go to a terminal and set the non-booting computer up the exact same way.  I don't know if it's a grub menu setting or what but when you get a moment, please let me know.  Then everything is solved and back to normal.

Thank you!

---

### Post by Hakunka-Matata on 2011-03-11
Quote from Forum Member **what-is-a-computer?** post # 80

> And the questions I have are:

A. Why is there so much stuff? Is that because I kept trying to boot it, using different kernels?

B. And why is it dated February 15th? That's not when it became frozen. It froze on March 3rd while I was attempting to copy audio files from a digital recorder.

C. If I turn my computer off now, will it boot up properly or now that you have "the story" does something need to be configured properly?

Any help would be appreciated. I'm not going to turn the computer off for fear that it will not start again.

I cannot thank everyone enough for your help. I'm so glad to be able to see my screen.

[LIST]
[*]A:  Because there is that much information involved in booting a computer, it's all important.
[*]B:  That's the date the script file was created.
[*]C:  ¿Quien Sabe? It should boot the same way it always has.  The boot_info_script file only collects and outputs collected information, it [COLOR="Red"]changes no settings, none,[/COLOR] in your computer.  It reveals information necessary to resolve the problem. 
[/LIST]

---

### Post by what-is-a-computer? on 2011-03-12
[FONT=monospace]After googling further, I just typed in the following command onto my properly booting computer:

[/FONT]sudo nano /boot/grub/menu.lst

I got the following:
```

 GNU nano 2.0.9           File: /boot/grub/menu.lst                            

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
                               [ Read 215 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

I did the same on the computer that does not boot properly.  

The result:  The screen is blank and instead of "Read 215 lines" at the bottom, it says "New File," but the screen is completely blank.

Could someone please tell me if I can merely copy what's in the functioning computer to the slow non-booting computer so that it boots properly and quickly?

Thanks!

---

### Post by Hakunka-Matata on 2011-03-12
> **what-is-a-computer? said:**
> [FONT=monospace]After googling further, I just typed in the following command onto my properly booting computer:

[/FONT]sudo nano /boot/grub/menu.lst

I got the following:
```

 GNU nano 2.0.9           File: /boot/grub/menu.lst                            

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3
                               [ Read 215 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```

I did the same on the computer that does not boot properly.  

The result:  The screen is blank and instead of "Read 215 lines" at the bottom, it says "New File," but the screen is completely blank.

**Could someone please tell me if I can merely copy what's in the functioning computer to the slow non-booting computer so that it boots properly and quickly?**

Thanks!
[B]
Question: Could someone please tell me if I can merely copy what's in the functioning computer to the slow non-booting computer so that it boots properly and quickly?[/B]

**Answer:** No, you cannot fix your other computer this way.  The file /boot/grub/menu.lst is unique to the system it is located on.  It references specific details about which HDD contains the Operating System, and other particulars of that system.  It's one of several files Grub uses during the boot process.
When Grub is installed to a HDD, usually to the MBR, it examines the system, and generates these files, storing them for reference, and reading them each time the machine boots up.

**Quote: I did the same on the computer that does not boot properly.**

**Comment:**  The command line "sudo nano /boot/grub/menu.lst" tells nano to open the file named /boot/grub/menu.lst, if the file does not exist, it creates the file.  That's why it said "New File" instead of "Read 215 lines".  Either the file does not exist on that system, or the command was issued from a directory from which nano (the text editor) could not find it.

---

### Post by what-is-a-computer? on 2011-03-12
Thank you for responding.

Except these computers are the exact  same system.  I took a passport drive and copied the first computer to that passport drive,  in other words, making an image of the first computer, using an acronis CD; and then I took my Acronis CD and in recovery mode on the Acronis CD put the exact same image of the old computer onto the backup computer.  So they are literally the same computer.   

That's how my ex-teacher taught me:  Always have a backup of your system in the event something happens to the first.  He calls it a "footprint."  Then if something happens to your main computer, you pull that one out of the closet and you never have down time.  You can fix the other one, time permitting.  So the second computer is literally identical to the first computer.  The hard drives are the same.  He said to always keep that passport drive and update it, making an image of your main computer every month or so, so that it's current. Then if something happens, you've only lost a month's worth of work at the very worst.  He also uses something called "Dropbox."  So he always has those files for every computer and never loses them.

I must be in the wrong directory or something, but I wouldn't know how to begin to check different directories.    I just clicked on "Accessories", opened my terminal and typed in that command because I know nothing about computers and I found that command in one of the  Linux forums where someone was having difficulty with their computer booting.  So I tried it.

The file has to exist because it existed before my system  froze and I dropped my mouse.  My system booted absolutely perfectly, immediately and within a second or two.  So.....but now it doesn't.

And I would re-do the image and start over  (even though it takes hours to put it on a computer -- but it's worth it) which is what I tried in  the first instance, except when I put the acronis CD in, it won't view the CD properly because it's not booting properly and I cannot get into Acronis recovery mode in order to recover the backup data.

Unfortunately I think I have a new doorstop.

And BTW, I opened this functioning computer the same way, just opening a terminal and typing that command that I saw in a forum.    So if it worked on this one and I got all of that information, I would assume the "image" computer should function the same way but the screen is blank.  So.....

Oh, well.  I think it's a lost cause.  It's all just too complicated and no on can figure it out and there are just too many variables.  And as a "non-computer" person, I don't explain things well and I don't have the foundation or the knowledge that I need to fix a computer.  I only can run my software.

Anyway, thank you for trying.

---

### Post by JKyleOKC on 2011-03-12
> **what-is-a-computer? said:**
> I must be in the wrong directory or something, but I wouldn't know how to begin to check different directories.    I just clicked on "Accessories", opened my terminal and typed in that command because I know nothing about computers and I found that command in one of the  Linux forums where someone was having difficulty with their computer booting.  So I tried it.

...

Oh, well.  I think it's a lost cause.  It's all just too complicated and no on can figure it out and there are just too many variables.  And as a "non-computer" person, I don't explain things well and I don't have the foundation or the knowledge that I need to fix a computer.  I only can run my software.

Anyway, thank you for trying.There are still a few things we can try in order to determine what is wrong, if you want to avoid the doorstop condition.

On the non-working machine, get to a terminal window and type in "ls /boot" without the quotes, then Enter. You should see a list of words that are rather cryptic, and one of them should be "grub" without quotes. If it's there, then type "ls /boot/grub" and hit Enter; you should get another list, again with most of them cryptic, but "menu.lst" should be among them. Based on what happened when you tried to edit it, it may not be, however. Even if it is, it might be empty or damaged, so the next step if it's there is to type "cat /boot/grub/menu.lst" and see if it produces any output. If it does, it will more than fill the screen but what's still visible should match what you see when using that exact same command on the working machine.

Agreed, it IS complicated and tedious, but what we're trying to find out here is just which part of your non-working system has been damaged, so that we can tell you how to fix it. Sometimes this means making lots of tests that don't lead anywhere, before getting to the one that shows results.

Since you cloned the non-working system from the working one using Acronis, the earlier info about grub files not being portable from one system to another probably does not apply in this case although it is, in general, true. I'm not sure whether any of the supposedly unique information is generated from things like drive serial numbers, though, and that MIGHT be the root of your problem. Did the non-working machine ever boot properly? If it did, that would mean that the copy process worked okay and something happened later. If not, then it might just be the copying that failed... And this question is probably one of those that won't lead anywhere -- but it might!

The Acronis CD should boot on its own, independently of anything else on the machine; its failure to do so points toward possible failure of the CD drive. The external one should handle that, but there could be a configuration problem there. Let's leave that area alone until you do the other tests I've described, and if they don't get anywhere then we can look at configurations...

---

### Post by what-is-a-computer? on 2011-03-12
Jim, where have you been?  Glad you're back.  :D

Okay.  The new clone has worked perfectly with no problem at all.......except sometimes the screen graphics go out but that's for another day.

I had it in a box with the image on it.  Worked perfectly.  I took it out because I wanted to put it in another locale.  Did so and it booted perfectly and has been booting perfectly.  I put some different files in my software program and it worked absolutely perfectly.

So I'm copying my audio digital files at the end of the day on March 3, and my computer froze, my mouse.  I couldn't click on anything.  The mouse did fall to the floor.  Then I turned off the computer with my power button, turned it back on and it was frozen, after it says something about entering grub stage, at "starting up."

It should say "Starting Up."  Literally in a second or two it should say  "Loading please wait..." and then ":*Reading Files Needed to Boot."  But it sticks on "Starting Up."  I left it Thursday just sitting there and it finally opened up to my program.  So whatever makes a computer go from "Starting Up" to "Loading please wait," that's what is broken.

As far as my acronis disk, yes, it boots but only to the screen where you can click on "clean disk" and whatever the other selection is, "recover data" or "backup" or something.  I don't remember what it says.  The moment I click on that, my screen is black and doesn't go anywhere, like it's stuck there as well.  It is not seeing what's on my computer.  It that called a partition?  I don't know.

May I make a suggestion?  I was just reading on the forums and so I went to "file system" and there's something in there called "boot."  And I clicked on that and saw a file folder called "grub."

What if I copy that entire folder on this computer and delete the file on the cloned computer (but copy it to my flashdrive in the event I need it back; of course, I won't be able to get back on the computer) and then paste that copied grub folder onto the cloned computer?  Will that work?

The problem is I have to turn the computer off to see if it functions, and I'm afraid it won't come back on.

Also when I clicked on that grub folder, "menu.1st" was there and I compared that folder to the folder on this computer and they looked the same.  

Whatever causes a computer to go to "loading please wait," that's what is broken.

Any suggestions?

---

### Post by what-is-a-computer? on 2011-03-12
PS  In grub, etc., there's a menu.1st and a menu.1st~

There is no output when I typed in cat /boot/grub/menu.1st

It says"  No such file or directory." 

There is a space after "cat," right?

---

### Post by what-is-a-computer? on 2011-03-12
PS/PS  if next to "grub" it says vmcoreinfo-2.6.28-11-generic, I think I saw that folder in that grub folder under "file system."  What if I copy that folder from the working computer to the clone?  Will that solve it?

---

### Post by what-is-a-computer? on 2011-03-12
And another thing I need to tell you:  Why do I have F11 - Recovery Mode on this  computer at the startup screen and I don't have it on the cloned machine?  I only have the option of selecting F2 (BIOS) and F10 - grub boot menu.

 It was a difference on the machines and thought it may have something to do with it.

---

### Post by what-is-a-computer? on 2011-03-12
Jim, I just tried those three ls /boot  commands on this computer and it says the same thing when I put in cat /boot/grub/menu.1st    "No such file or directory."

So I'm getting the same response on both computers.

---

### Post by what-is-a-computer? on 2011-03-12
One other thought:  Could this be a software issue?

I always try to go back and retrace my steps.
what if I delete all the new files I created on March 3?  There are only a few of them in my specialized software.

The computer was working prior to creating those three files.  So why not delete them.
I mean, is it possible that something is still "on" or "connected" within my software and that is preventing my computer from booting properly?

It would require me to turn my computer off once I delete those few files.

Just a thought.

---

### Post by JKyleOKC on 2011-03-12
That doesn't sound at all likely. If those files had anything to do with the problem, the boot would have to get much further along than it is before they could become involved. Here's a quick, very over simplified, outline of what happens when you power up:

First, the power supply provides power to all the chips. The CPU chip automatically goes to a predefined memory address, which is actually in the BIOS chip rather than any memory chip, to begin operation. The code in the BIOS displays that very first screen, then searches through the defined sequence of boot devices looking for the first one that has a valid boot loader on it.

When it finds one, it displays the "Starting up" message and transfers control to that boot loader, in our case that's grub (**GR**and **U**nified **B**ootloader if you're curious where the name came from). The code for grub is too big to fit into the area of disk where the initial boot loader is stored, so the program is split into pieces and its second part is placed in your /boot area. When the first part is nearing its end, it displays the "Loading" message and transfers control to the second part.

That second part then displays the grub menu listing all the various choices, or may just skip the menu altogether and load up the main Ubuntu kernel code. When it does so, you get the Ubuntu splash screen and eventually, your desktop or the login screen. Until you get to your desktop, the added files can't be involved.

Since you never get to the "Loading" message, the problem appears to be somewhere in the first part of the grub code itself. That's what I'm going to have to research in some depth, to see what it may be looking for. 

I have a couple of errands to run so it may be several hours before I get back on line. Don't try any changes until I get back and show you how to save your files; you might want to get another flash drive or two while waiting, though. You'll need enough to hold everything that's in your /home directory, which could be several GB depending on what kind and how many files you have stored...

---

### Post by what-is-a-computer? on 2011-03-12
Okay.  Thank you.

And I "already" did something.  I'm sure I can get it back.  Don't worry.  I'll await hearing from you further.  No problem.

---

### Post by Hakunka-Matata on 2011-03-12
> **what-is-a-computer? said:**
> PS  In grub, etc., there's a menu.1st and a menu.1st~

There is no output when I typed in cat /boot/grub/menu.1st

It says"  No such file or directory." 

There is a space after "cat," right?

```
cat /boot/grub/menu.lst
``` that's a lower case L, not a numeral 1

Look @ your post # 79, you'll see the filename in 3rd? section

---

### Post by what-is-a-computer? on 2011-03-12
oh, I've been typing in "1," not small "L."

Thank you.  I'm going to try it.

---

### Post by what-is-a-computer? on 2011-03-12
I'm so sorry.  I read that as "1st" instead of "lst."  What does it stand for, "list?"  Tsk..tsk..tsk.

Anyway, I have done it and a whole bunch of stuff comes up.  It looks like what I provided before in my boot script.

Also, Jim, what I had already done before receiving your message was I already deleted those files and turned off my computer.

Was I able to get it back?  Yes.  By just letting it sit here at "starting up" and it finally appears.  You know how long it takes to reboot my computer:  A bit over eight minutes.

Maybe that information will help.

PS EDIT:

And before when I said my computer was not booting, I guess it is technically booting, but it takes over eight minutes instead of a couple of seconds.    I didn't dream it would go after eight minutes.   I made the erroneous assumption that it was "stuck" or "freezing" when it actuality it  is booting..........but after a very long time when comparing two seconds versus over eight minutes........which I just now discovered.  All this time, I assumed that having the Live CD in the CDROM was making it go forward.  I just booted from the HD and after over eight minutes, it goes into my program.    

And thank you so much, Hakunka,  for correcting my error.   Really appreciate it.

---

### Post by JKyleOKC on 2011-03-12
> **what-is-a-computer? said:**
> I just booted from the HD and after over eight minutes, it goes into my program.That is VERY good news and quite encouraging. It means that whatever is causing the delay eventually gives up, and that whatever it was looking for is not totally essential to making the system work! (Or, possibly, that after 8 minutes it actually DID find it, but that's less likely.)

I'm back from the errands and ready to give you the step by step instructions for saving your data, but first I need a bit more information. On the system that's not working right, open a terminal window and type "sudo fdisk -l >drives.txt" (and again, that's a lower-case L rather than a numeral 1). This should give you a list of the drives that the system has recognized, in a file "drives.txt" inside your home directory. Paste the content of that file into a reply here, inside the CODE tags, just as you did before with "results.txt" from the desktop. That will tell me the names and types of all your drives so that I can use the correct names in the steps...

More and more I'm beginning to believe that the CD drive may have gone sour, and the mouse falling to the floor been just a coincidence. One of my boxes here has a bum CD drive and it sometimes locks up for more than a minute, trying to access it, when booting. However it's never taken as long as 8 minutes so this may be another bad guess. I did find, with my drive, that removing any disk from the drive greatly reduced the lockup time -- that might be worth a try!

---

### Post by what-is-a-computer? on 2011-03-12
Hi, Jim.

Well, I have done as you directed.  It gives no list.  It just goes back to my original prompt.

---

### Post by what-is-a-computer? on 2011-03-12
and I'm so glad this is good news.  I could use some!

---

### Post by what-is-a-computer? on 2011-03-12
Jim, I did a search in my home directory on the non-working computer for "disks.txt."  (But I cannot do your command in a terminal.)

Here's the response:  

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fc9515e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+  82  Linux swap / Solaris
```What is strange is:  I did the same thing on this computer and nothing comes up.

---

### Post by JKyleOKC on 2011-03-12
> **what-is-a-computer? said:**
> Well, I have done as you directed.  It gives no list.  It just goes back to my original prompt.In the terminal, try "less drives.txt" and you should see the list. Returning to the original prompt is normal; the command sent all of the output to the file "drives.txt" which it created. Sorry I wasn't clear about that in the first place.

You've been doing so great with following the instructions that I sometimes forget that what we geeks take for granted is still a mysterious and only dimly charted world for you!

The "less" command I mentioned above will display files to you, a page at a time (but the drives.txt file should not take more than one page) and is quite handy for looking at text files from the command line. Unlike using an editor such as nano, it won't create the file if it doesn't already exist; it just gives an error message, which is more useful when troubleshooting.

---

### Post by Hakunka-Matata on 2011-03-12
> **what-is-a-computer? said:**
> Jim, I did a search in my home directory on the non-working computer for "[COLOR="Red"]disks.txt.[/COLOR]"

Here's the response:  

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fc9515e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+  82  Linux swap / Solaris
```

What is strange is:  I did the same thing on this computer and nothing comes up.

> open a terminal window and type "sudo fdisk -l >[COLOR="Red"]drives.txt[/COLOR]" (and again, that's a lower-case L rather than a numeral 1).

copying commands and then pasting them into the Terminal avoids typos;)

---

### Post by JKyleOKC on 2011-03-12
> **what-is-a-computer? said:**
> What is strange is:  I did the same thing on this computer and nothing comes up.Not strange at all; that file was created by the command I told you to run. If you run that same command on the working machine, you should then find the file -- and it ought to show very similar, but not necessarily identical, information.

Sorry to be a bit confusing in my previous message by calling the file "drives.txt" rather than "disks.txt" -- I should have looked back to see what I told you to call it instead of relying on my memory. My memory ain't what it used to be back when I was a kid of 75!

EDIT: I see we're posting past each other so I'll slow down for a while and let you catch up.

---

### Post by what-is-a-computer? on 2011-03-12
Jim, my screen has gone black.  I've lost the screen even though the computer is on.
Huh????????

I cannot see anything on my screen but the blue light is on.

I'll obviously have to reboot which I'm doing now.
Can this be a graphics issue?  I would not think the two are connected.

---

### Post by JKyleOKC on 2011-03-12
That might be the screensaver cutting in; even if you've set it to "none" there's a timeout that puts the video to sleep without powering down the monitor. One of my machines does this. If that's what it is, moving the mouse should bring back the screen in a few seconds. Otherwise, it may be a video problem of some sort, or could be a heat buildup inside the box. The video chips and the CPU both get pretty hot in operation and if anything impedes the airflow around them can shut off on their own when they get hot enough to risk being permanently damaged. In my systems, which run on the ragged edge of that point due to poor air circulation around them, the temperatures get above 60 degrees Celsius, which is well above the point that touching them would give you an instant and painful burn. Some systems have BIOS settings that can be set to control the automatic shutdown point; one of mine does but the others do not.

---

### Post by what-is-a-computer? on 2011-03-12
Jim, while I'm waiting for this slooowwwwwwwwww computer to boot,  theonly thing I did a minute ago while  I was waiting for a response from you is: When I went into  my home folder I couldn't see the little circles in the upper right-hand corner for minimizing and exiting and restoring.  They are the "emerald" circles.  

So I changed the horizontal config. on my computer but with my monitor controls so that I could see those in the upper right-hand corner.  They were cut off.    Why my screen dimensions changed from the last time I booted, I have no idea but I couldn't see those for some reason.    That's the only change I made and then I copied the disks.txt file to my USB flashdrive.

Hasn't it been eight minutes?  My computer is still not booting.  It's still at the "starting up" screen.  Oh, my gosh.  Hope it wasn't a short-lived victory.

I wonder if I should turn it off and try again.

---

### Post by what-is-a-computer? on 2011-03-12
It's up on top of any open desk.  There is nothing around it.  So it is getting complete circulation.

Should I restart it?

---

### Post by what-is-a-computer? on 2011-03-12
I'm rebooting my computer, Jim.

Be back shortly.....hopefully.

---

### Post by what-is-a-computer? on 2011-03-12
Well, those were short-lived victories, Jim.

My computer will not boot at all and is frozen at the "starting up" screen.  It's been 12 minutes now, not eight.  Gosh, what is this?  Now 13 minutes.  Rats, rats and triple rats!

Now what?  

Now we're at 15 minutes.  No booting.

---

### Post by what-is-a-computer? on 2011-03-12
You know what?  I think I also unchecked "activate screensaver when computer is idle."  Would that have affected it?

---

### Post by JKyleOKC on 2011-03-12
If that was unchecked, it ought not have fired -- but as I said there's another setting that might still be active.

If it's still not re-started, best cross your fingers and toes, power down, pull the cord, and let it cool off for at least half an hour, maybe more. If you can get it to power down by pressing CTRL, ALT, and DEL all at the same time, do it that way. This should force a controlled shutdown for the disks -- and may take you to the initial splash screen. If it does, power it down while that screen is still displayed; that will minimize the risk of file damage.

---

### Post by what-is-a-computer? on 2011-03-12
Nope, cannot shut the power down with CTR-ALT-DEL.  It doesn't respond. My keyboard doesn't respond at all.  

I'll turn it off for awhile.

TTYL.  Appreciate your help.

---

### Post by what-is-a-computer? on 2011-03-12
Hi, Jim.  I've turned off my computer with the acronis disk which there is an F4 option to "really" shut down the computer.  Otherwise, even when it's unplugged and I put the cord back in, it comes on on its own.  So was, I guess, never completely shut down.

I let it set and I'm back in.  What's that all about?  It's like the computer is still running or on and that's why it won't boot.

I have done your command sudo fdisk -l >less drives.txt

The files are not displayed.  Is there a space between the "-l" and the ">"?  
I did it both ways.  No files are displayed a page at a time.

---

### Post by Hakunka-Matata on 2011-03-12
```
[LIST]
[*]sudo fdisk -l > disks  [INDENT]produces the output of fdisk -l in a file named disks[/INDENT]
[*]sudo fdisk -l  [INDENT]displays disk information[/INDENT]
[*]sudo fdisk -l | less  [INDENT]disk information, but less verbose[/INDENT]
[/LIST]
```

try copying the commands, and pasting them into the Terminal

---

### Post by what-is-a-computer? on 2011-03-12
Uh, duh!

I typed "just" the "less disks.txt" and....the "stuff" is there but there's no way to save it.

I copied it but there's no "save."

And now with Hakuna's additional info, I have done so and I'm going to try to either copy the info or do a screenshot.  Thank you.  I did the one on "display"

---

### Post by Hakunka-Matata on 2011-03-12
if you want the output of the command to be written to a file and saved, then add a > filename behind the command.  Leave a space between end of command and > and a space between > and filename

sudo (space) fdisk (space) -l (space) > (space) filename.txt   or whatever

**FYI on slow computer boot up** try typing in the command```
dmesg | more
``` and see what you get.  It's a log of everything that happens from power on till finish of boot-up.

---

### Post by what-is-a-computer? on 2011-03-12
unfortunately my graphics just went out on my computer screen.    So I had to turn it off.  It now won't boot again.  

I'll let you know when I'm back into Ubuntu.............if I live through it.  This is very maddening/stressful.

The only way I can get it to boot is to put an acronis disk in, use F4 in acronis to turn off the computer.  I see the light go out and the fan stops.  So I know it's "really" off.  I turn it back on and let it boot on its own.......in about eight or nine minutes.  

When I have to turn it off to reboot it, it's like the computer is already running so it won't let it boot; that even though I turned it off with the power button, Ubuntu is still open and then the computer cannot reboot back into it.

I'm going to turn it off again for awhile.  (Sighing deeply)

---

### Post by Hakunka-Matata on 2011-03-12
What's up with that machine?  Is it old & tired, CMOS battery half dead?, I've seen PXE boot fail reports, that's a network boot, do you need that?  Would a "Load defaults Setup" in BIOS be worth a try?  Good Luck

---

### Post by what-is-a-computer? on 2011-03-12
It's not old and tired.  It's basically a brand new machine, hardly used.  Something is wrong with it.

The CMOS battery?  Brand new.  Put it in a few days ago.

If I can get back on and show you/Jim the fdisk settings, maybe that will tell the story.
We'll see here soon.

Thanks.

PS  And I tried to -- oh, here it comes.  It's coming up now.

---

### Post by what-is-a-computer? on 2011-03-12
here's the output for

"sudo fdisk -l"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fc9515e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+  82  Linux swap / Solaris

Disk /dev/sdb: 2004 MB, 2004353024 bytes
16 heads, 32 sectors/track, 7646 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000e6282

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7646     1957360    c  W95 FAT32 (LBA)
```I'm sending this one before something happens to my screen.

---

### Post by what-is-a-computer? on 2011-03-12
Here's the output for "less"

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fc9515e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18748   150593278+  83  Linux
/dev/sda2           18749       19457     5695042+  82  Linux swap / Solaris

Disk /dev/sdb: 2004 MB, 2004353024 bytes
16 heads, 32 sectors/track, 7646 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000e6282

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7646     1957360    c  W95 FAT32 (LBA)

```

---

### Post by what-is-a-computer? on 2011-03-12
when I just tried to close out of terminal, it said "There is still a process running in the terminal."

Is that important?  Just trying to troubleshoot here.

---

### Post by what-is-a-computer? on 2011-03-12
And the ```
dmesg | more 
``````
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4
.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.2
7-11.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fee0000 (usable)
[    0.000000]  BIOS-e820: 000000006fee0000 - 000000006fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fee3000 - 000000006fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fef0000 - 000000006ff00000 (reserved)
[    0.000000]  BIOS-e820: 0000000070000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it aroun
d.
[    0.000000] last_pfn = 0x6fee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37813000 - 37fef438
[    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)
```Now, does any of this help?

See below.  This was not a fraction of it!  The entire output is listed below.  Sorry.

---

### Post by what-is-a-computer? on 2011-03-12
Here's the entire thing.  And the ```
dmesg | more 
``````
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4
.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.2
7-11.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fee0000 (usable)
[    0.000000]  BIOS-e820: 000000006fee0000 - 000000006fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fee3000 - 000000006fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fef0000 - 000000006ff00000 (reserved)
[    0.000000]  BIOS-e820: 0000000070000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it aroun
d.
[    0.000000] last_pfn = 0x6fee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37813000 - 37fef438
[    0.000000] ACPI: RSDP 000F8080, 0014 (r0 ACRSYS)

[    0.000000] ACPI: RSDT 6FEE3000, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
  0)
[    0.000000] ACPI: FACP 6FEE3080, 0074 (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
  0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has 
zero address or length: 0000000000000000/1 [20080609]
[    0.000000] ACPI: DSDT 6FEE3100, 6E1B (r1 ACRSYS ACRPRDCT     1000 MSFT  3000
000)
[    0.000000] ACPI: FACS 6FEE0000, 0040
[    0.000000] ACPI: SSDT 6FEEA000, 00D3 (r1 PTLTD  POWERNOW        1  LTP      
  1)
[    0.000000] ACPI: HPET 6FEEA100, 0038 (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
 98)
[    0.000000] ACPI: SLIC 6FEEA140, 0176 (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
  0)
[    0.000000] ACPI: MCFG 6FEEA2C0, 003C (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
  0)
[    0.000000] ACPI: APIC 6FEE9F40, 0098 (r1 ACRSYS ACRPRDCT 42302E31 NVDA      
  0)
[    0.000000] 894MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 -
 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 -
 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 -
 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 -
 00005c29e0]
[    0.000000]   #4 [0037813000 - 0037fef438]          RAMDISK ==> [0037813000 -
 0037fef438]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 -
 00005c6000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 -
 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 -
 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 -
 0000018000]
[    0.000000] found SMP MP-table at [c00f3c50] 000f3c50
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0006fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006fee0
[    0.000000] On node 0 totalpages: 458351
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c100024
0
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 227074 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7000
0000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pag
es: 454321
[    0.000000] Kernel command line: root=UUID=b803da66-c741-459e-b78c-311c48affc
b2 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1607.267 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1802412k/1833856k available (2576k kernel code, 30084k re
served, 1164k data, 424k init, 916352k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03843ea   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor 
mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, N
odes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer fr
equency.. 3214.53 BogoMIPS (lpj=6429068)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.016426] SMP alternatives: switching to UP code
[    0.023083] ACPI: Core revision 20080609
[    0.025487] ACPI: Checking initramfs for custom DSDT
[    0.470173] ENABLING IO-APIC IRQs
[    0.484030] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.532244] CPU0: AMD Athlon(tm) Processor 2650e stepping 02
[    0.549520] Brought up 1 CPUs
[    0.550157] Total of 1 processors activated (3214.53 BogoMIPS).
[    0.556668] CPU0 attaching NULL sched-domain.
[    0.613942] net_namespace: 840 bytes
[    0.615641] Booting paravirtualized kernel on bare hardware
[    0.660669] Time:  3:54:04  Date: 03/09/11
[    0.669729] NET: Registered protocol family 16
[    0.765305] EISA bus registered
[    0.767217] ACPI: bus type pci registered
[    0.797307] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.798156] PCI: MCFG area at f0000000 reserved in E820
[    0.798581] PCI: Using MMCONFIG for extended config space
[    0.799218] PCI: Using configuration type 1 for base access
[    1.318158] ACPI: EC: Look up EC in DSDT
[    4.073949] ACPI: Interpreter enabled
[    4.074799] ACPI: (supports S0 S3 S4 S5)
[    4.079642] ACPI: Using IOAPIC for interrupt routing

[    7.274582] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    7.310796] PCI: 0000:00:01.0 reg 18 io port: [1d00, 1dff]
[    7.317732] PCI: 0000:00:01.1 reg 10 io port: [fc00, fc3f]
[    7.319646] PCI: 0000:00:01.1 reg 20 io port: [1c00, 1c3f]
[    7.320881] PCI: 0000:00:01.1 reg 24 io port: [f400, f43f]
[    7.323435] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    7.324673] pci 0000:00:01.1: PME# disabled
[    7.336666] PCI: 0000:00:02.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    7.342793] pci 0000:00:02.0: supports D1
[    7.343218] pci 0000:00:02.0: supports D2
[    7.343643] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.344668] pci 0000:00:02.0: PME# disabled
[    7.349093] PCI: 0000:00:02.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    7.354367] pci 0000:00:02.1: supports D1
[    7.354793] pci 0000:00:02.1: supports D2
[    7.355219] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    7.356456] pci 0000:00:02.1: PME# disabled
[    7.367215] PCI: 0000:00:05.0 reg 10 32bit mmio: [fe024000, fe027fff]
[    7.372882] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    7.373734] pci 0000:00:05.0: PME# disabled
[    7.379432] PCI: 0000:00:06.0 reg 20 io port: [f000, f00f]
[    7.386369] PCI: 0000:00:07.0 reg 10 32bit mmio: [fe02d000, fe02dfff]
[    7.387220] PCI: 0000:00:07.0 reg 14 io port: [ec00, ec07]
[    7.391219] pci 0000:00:07.0: supports D1
[    7.391644] pci 0000:00:07.0: supports D2
[    7.392455] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.393307] pci 0000:00:07.0: PME# disabled
[    7.397521] PCI: 0000:00:08.0 reg 10 io port: [9f0, 9f7]
[    7.398373] PCI: 0000:00:08.0 reg 14 io port: [bf0, bf3]
[    7.399223] PCI: 0000:00:08.0 reg 18 io port: [970, 977]
[    7.400667] PCI: 0000:00:08.0 reg 1c io port: [b70, b73]
[    7.401306] PCI: 0000:00:08.0 reg 20 io port: [d800, d80f]
[    7.402367] PCI: 0000:00:08.0 reg 24 32bit mmio: [fe02c000, fe02cfff]
[    7.407857] PCI: 0000:00:08.1 reg 10 io port: [9e0, 9e7]
[    7.408879] PCI: 0000:00:08.1 reg 14 io port: [be0, be3]
[    7.409728] PCI: 0000:00:08.1 reg 18 io port: [960, 967]
[    7.410578] PCI: 0000:00:08.1 reg 1c io port: [b60, b63]
[    7.411427] PCI: 0000:00:08.1 reg 20 io port: [c400, c40f]
[    7.412880] PCI: 0000:00:08.1 reg 24 32bit mmio: [fe02b000, fe02bfff]
[    7.422155] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.422792] pci 0000:00:09.0: PME# disabled
[    7.429091] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.429728] pci 0000:00:0b.0: PME# disabled
[    7.435217] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    7.436669] pci 0000:00:0c.0: PME# disabled
[    7.439218] PCI: 0000:00:0d.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    7.440814] PCI: 0000:00:0d.0 reg 14 64bit mmio: [e0000000, efffffff]
[    7.442088] PCI: 0000:00:0d.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    7.443152] PCI: 0000:00:0d.0 reg 30 32bit mmio: [0, 1ffff]
[    7.468455] pci 0000:00:04.0: transparent bridge
[    7.469093] PCI: bridge 0000:00:04.0 io port: [b000, bfff]
[    7.469942] PCI: bridge 0000:00:04.0 32bit mmio: [fd800000, fd8fffff]
[    7.470580] PCI: bridge 0000:00:04.0 32bit mmio pref: [fdf00000, fdffffff]
[    7.477944] PCI: bridge 0000:00:09.0 io port: [a000, afff]
[    7.478582] PCI: bridge 0000:00:09.0 32bit mmio: [fde00000, fdefffff]
[    7.479432] PCI: bridge 0000:00:09.0 64bit mmio pref: [fdd00000, fddfffff]
[    7.485950] PCI: 0000:03:00.0 reg 10 64bit mmio: [fdcff000, fdcfffff]
[    7.491224] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    7.492457] pci 0000:03:00.0: PME# disabled
[    7.498159] PCI: bridge 0000:00:0b.0 io port: [9000, 9fff]
[    7.499009] PCI: bridge 0000:00:0b.0 32bit mmio: [fdc00000, fdcfffff]
[    7.499859] PCI: bridge 0000:00:0b.0 64bit mmio pref: [fdb00000, fdbfffff]
[    7.507431] PCI: bridge 0000:00:0c.0 io port: [8000, 8fff]
[    7.508456] PCI: bridge 0000:00:0c.0 32bit mmio: [fda00000, fdafffff]
[    7.509305] PCI: bridge 0000:00:0c.0 64bit mmio pref: [fd900000, fd9fffff]
[    7.511429] bus 00 -> node 0
[    7.513732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    7.623429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   22.795007] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   22.851429] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   22.907006] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   22.963005] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.019429] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.075857] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 *10 11 14 15)
[   23.131641] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.186792] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.243218] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   23.298795] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.355219] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 *7 9 10 11 14 15)
[   23.411432] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[   23.467433] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 *7 9 10 11 14 15)
[   23.524668] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.581306] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   23.637309] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   23.693093] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disa
bled.
[   23.749307] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[   23.805519] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[   23.881093] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   23.953947] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.027216] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   24.099852] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.172667] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   24.244880] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0
[   24.317093] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   24.389305] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   24.462582] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22) *0
[   24.535434] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   24.608457] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   24.681093] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22) *0, disabled.
[   24.753945] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22) *0
[   24.826371] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22) *0
[   24.899005] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   24.971430] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   25.045305] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   25.117732] ACPI: PCI Interrupt Link [APSI] (IRQs 23) *0
[   25.190156] ACPI: PCI Interrupt Link [APSJ] (IRQs 23) *0
[   25.244457] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.255218] pnp: PnP ACPI init
[   25.258156] ACPI: bus type pnp registered
[   27.024880] pnp: PnP ACPI: found 12 devices
[   27.025516] ACPI: ACPI bus type pnp unregistered
[   27.026154] PnPBIOS: Disabled by ACPI PNP
[   27.133943] PCI: Using ACPI for IRQ routing
[   27.169942] NET: Registered protocol family 8
[   27.170580] NET: Registered protocol family 20
[   27.181094] NetLabel: Initializing
[   27.181519] NetLabel:  domain hash size = 128
[   27.181944] NetLabel:  protocols = UNLABELED CIPSOv4
[   27.185943] NetLabel:  unlabeled traffic allowed by default
[   27.187222] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   27.189305] hpet0: 3 32-bit timers, 25000000 Hz
[   27.194160] Switched to high resolution mode on CPU 0
[   27.537883] tracer: 772 pages allocated for 65536 entries of 48 bytes
[   27.538311]    actual entries 65620
[   27.575096] AppArmor: AppArmor Filesystem Enabled
[   27.581698] ACPI: RTC can wake from S4
[   27.594463] system 00:01: ioport range 0x1000-0x107f has been reserved
[   27.595316] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   27.595954] system 00:01: ioport range 0x1400-0x147f has been reserved
[   27.598081] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   27.598720] system 00:01: ioport range 0x1800-0x187f has been reserved
[   27.599570] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   27.600209] system 00:01: ioport range 0x2000-0x207f has been reserved
[   27.602125] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   27.603827] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   27.605741] system 00:02: ioport range 0x295-0x314 has been reserved
[   27.609353] system 00:0a: iomem range 0xf0000000-0xf3ffffff could not be rese
rved
[   27.611261] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[   27.612111] system 00:0b: iomem range 0xfeff0000-0xfeff00ff could not be rese
rved
[   27.614026] system 00:0b: iomem range 0x6fee0000-0x6fefffff could not be rese
rved
[   27.614665] system 00:0b: iomem range 0xffff0000-0xffffffff could not be rese
rved
[   27.615516] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   27.617433] system 00:0b: iomem range 0x100000-0x6fedffff could not be reserv
ed
[   27.618286] system 00:0b: iomem range 0x70000000-0x7fffffff could not be rese
rved
[   27.619137] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be rese
rved
[   27.619988] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be rese
rved
[   27.621906] system 00:0b: iomem range 0xfefff000-0xfeffffff could not be rese
rved
[   27.622758] system 00:0b: iomem range 0xfff80000-0xfff80fff could not be rese
rved
[   27.623608] system 00:0b: iomem range 0xfff90000-0xfffbffff could not be rese
rved
[   27.625525] system 00:0b: iomem range 0xfffed000-0xfffeffff could not be rese
rved
[   27.894988] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[   27.895625] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[   27.897751] pci 0000:00:04.0:   MEM window: 0xfd800000-0xfd8fffff
[   27.898601] pci 0000:00:04.0:   PREFETCH window: 0x000000fdf00000-0x000000fdf
fffff
[   27.899662] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[   27.901365] pci 0000:00:09.0:   IO window: 0xa000-0xafff
[   27.902215] pci 0000:00:09.0:   MEM window: 0xfde00000-0xfdefffff
[   27.902852] pci 0000:00:09.0:   PREFETCH window: 0x000000fdd00000-0x000000fdd
fffff
[   27.903914] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[   27.905619] pci 0000:00:0b.0:   IO window: 0x9000-0x9fff
[   27.906468] pci 0000:00:0b.0:   MEM window: 0xfdc00000-0xfdcfffff
[   27.907105] pci 0000:00:0b.0:   PREFETCH window: 0x000000fdb00000-0x000000fdb
fffff
[   27.907955] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[   27.909867] pci 0000:00:0c.0:   IO window: 0x8000-0x8fff
[   27.910716] pci 0000:00:0c.0:   MEM window: 0xfda00000-0xfdafffff
[   27.911353] pci 0000:00:0c.0:   PREFETCH window: 0x000000fd900000-0x000000fd9
fffff
[   27.914544] pci 0000:00:04.0: setting latency timer to 64
[   27.915820] pci 0000:00:09.0: setting latency timer to 64
[   27.918159] pci 0000:00:0b.0: setting latency timer to 64
[   27.919222] pci 0000:00:0c.0: setting latency timer to 64
[   27.920071] bus: 00 index 0 io port: [0, ffff]
[   27.921774] bus: 00 index 1 mmio: [0, ffffffff]
[   27.922411] bus: 01 index 0 io port: [b000, bfff]
[   27.922836] bus: 01 index 1 mmio: [fd800000, fd8fffff]
[   27.923476] bus: 01 index 2 mmio: [fdf00000, fdffffff]
[   27.923903] bus: 01 index 3 io port: [0, ffff]
[   27.925605] bus: 01 index 4 mmio: [0, ffffffff]
[   27.926034] bus: 02 index 0 io port: [a000, afff]
[   27.926672] bus: 02 index 1 mmio: [fde00000, fdefffff]
[   27.927100] bus: 02 index 2 mmio: [fdd00000, fddfffff]
[   27.927737] bus: 02 index 3 mmio: [0, 0]
[   27.928163] bus: 03 index 0 io port: [9000, 9fff]
[   27.929868] bus: 03 index 1 mmio: [fdc00000, fdcfffff]
[   27.930507] bus: 03 index 2 mmio: [fdb00000, fdbfffff]
[   27.930934] bus: 03 index 3 mmio: [0, 0]
[   27.931359] bus: 04 index 0 io port: [8000, 8fff]
[   27.931997] bus: 04 index 1 mmio: [fda00000, fdafffff]
[   27.933702] bus: 04 index 2 mmio: [fd900000, fd9fffff]
[   27.934127] bus: 04 index 3 mmio: [0, 0]
[   27.937748] NET: Registered protocol family 2
[   27.979006] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.066369] TCP established hash table entries: 131072 (order: 8, 1048576 byt
es)
[   28.215400] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.291952] TCP: Hash tables configured (established 131072 bind 65536)
[   28.293653] TCP reno registered
[   28.329804] NET: Registered protocol family 1
[   28.365527] checking if image is initramfs... it is
[  221.163323] Freeing initrd memory: 8049k freed
[  221.477972] audit: initializing netlink socket (disabled)
[  221.482222] type=2000 audit(1299643064.480:1): initialized
[  223.098377] highmem bounce pool size: 64 pages
[  223.099863] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[  223.959858] VFS: Disk quotas dquot_6.5.1
[  223.990262] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  224.030432] msgmni has been set to 1748
[  224.071250] io scheduler noop registered
[  224.071675] io scheduler anticipatory registered
[  224.073379] io scheduler deadline registered
[  224.077627] io scheduler cfq registered (default)
[  224.084016] pci 0000:00:00.0: Enabling HT MSI Mapping
[  224.898491] pci 0000:00:02.0: OHCI: BIOS handoff failed (BIOS bug?) 00000784
[  224.899310] pci 0000:00:04.0: Enabling HT MSI Mapping
[  224.899329] pci 0000:00:05.0: Enabling HT MSI Mapping
[  224.899359] pci 0000:00:07.0: Enabling HT MSI Mapping
[  224.899376] pci 0000:00:08.0: Enabling HT MSI Mapping
[  224.899392] pci 0000:00:08.1: Enabling HT MSI Mapping
[  224.899410] pci 0000:00:09.0: Enabling HT MSI Mapping
[  224.899427] pci 0000:00:0b.0: Enabling HT MSI Mapping
[  224.899445] pci 0000:00:0c.0: Enabling HT MSI Mapping
[  224.899462] pci 0000:00:0d.0: Boot video device
[  224.899577] pcieport-driver 0000:00:09.0: setting latency timer to 64
[  224.899606] pcieport-driver 0000:00:09.0: found MSI capability
[  224.899630] pci_express 0000:00:09.0:pcie00: allocate port service
[  224.899674] pci_express 0000:00:09.0:pcie03: allocate port service
[  224.899752] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[  224.899779] pcieport-driver 0000:00:0b.0: found MSI capability
[  224.899799] pci_express 0000:00:0b.0:pcie00: allocate port service
[  224.899842] pci_express 0000:00:0b.0:pcie03: allocate port service
[  224.899916] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[  224.899942] pcieport-driver 0000:00:0c.0: found MSI capability
[  224.899962] pci_express 0000:00:0c.0:pcie00: allocate port service
[  224.900225] pci_express 0000:00:0c.0:pcie03: allocate port service
[  224.900522] isapnp: Scanning for PnP cards...
[  225.253233] isapnp: No Plug & Play device found
[  225.296407] hpet_resources: 0xfeff0000 is busy
[  225.296493] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[  225.298895] brd: module loaded
[  225.298974] input: Macintosh mouse button emulation as /devices/virtual/input
/input0
[  225.299100] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[  225.307222] serio: i8042 KBD port at 0x60,0x64 irq 1
[  225.307229] serio: i8042 AUX port at 0x60,0x64 irq 12
[  225.307782] mice: PS/2 mouse device common for all mice
[  225.308164] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[  225.308200] rtc0: alarms up to one year, y3k, hpet irqs
[  225.308329] EISA: Probing bus 0 at eisa.0
[  225.308336] Cannot allocate resource for EISA slot 1
[  225.308340] Cannot allocate resource for EISA slot 2
[  225.308356] Cannot allocate resource for EISA slot 8
[  225.308358] EISA: Detected 0 cards.
[  225.308362] cpuidle: using governor ladder
[  225.308365] cpuidle: using governor menu
[  225.308934] TCP cubic registered
[  225.308965] Using IPI No-Shortcut mode
[  225.309186] registered taskstats version 1
[  225.309348]   Magic number: 3:861:916
[  225.309434] tty ptywf: hash matches
[  225.309473] tty ptmx: hash matches
[  225.309542] rtc_cmos 00:05: setting system clock to 2011-03-09 03:58:04 UTC (
1299643084)
[  225.309546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[  225.309549] EDD information not available.
[  225.309859] Freeing unused kernel memory: 424k freed
[  225.309932] Write protecting the kernel text: 2580k
[  225.309977] Write protecting the kernel read-only data: 940k
[  225.334526] input: AT Translated Set 2 keyboard as /devices/platform/i8042/se
rio0/input/input1
[  225.572052] fuse init (API version 7.9)
[  225.685648] fan PNP0C0B:00: registered as cooling_device0
[  225.685656] ACPI: Fan [FAN] (on)
[  225.692684] processor ACPI0007:00: registered as cooling_device1
[  225.695513] ACPI: Expecting a [Reference] package element, found type 0
[  225.695806] thermal LNXTHERM:01: registered as thermal_zone0
[  225.696374] ACPI: Thermal Zone [THRM] (40 C)
[  225.904839] usbcore: registered new interface driver usbfs
[  225.904875] usbcore: registered new interface driver hub
[  225.904915] usbcore: registered new device driver usb
[  225.912815] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[  225.912829] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 22 (level, 
low) -> IRQ 22
[  225.912842] ehci_hcd 0000:00:02.1: setting latency timer to 64
[  225.912846] ehci_hcd 0000:00:02.1: EHCI Host Controller
[  225.912899] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus numbe
r 1
[  225.912930] ehci_hcd 0000:00:02.1: debug port 1
[  225.912935] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[  225.912952] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[  225.920231] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[  225.924505] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[  225.924678] usb usb1: configuration #1 chosen from 1 choice
[  225.924715] hub 1-0:1.0: USB hub found
[  225.924726] hub 1-0:1.0: 10 ports detected
[  225.936235] No dock devices found.
[  225.971613] SCSI subsystem initialized
[  226.008760] libata version 3.00 loaded.
[  226.132878] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[  226.132891] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, 
low) -> IRQ 21
[  226.132908] ohci_hcd 0000:00:02.0: setting latency timer to 64
[  226.132912] ohci_hcd 0000:00:02.0: OHCI Host Controller
[  226.132942] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus numbe
r 2
[  226.132968] ohci_hcd 0000:00:02.0: irq 21, io mem 0xfe02f000
[  226.190417] usb usb2: configuration #1 chosen from 1 choice
[  226.190458] hub 2-0:1.0: USB hub found
[  226.190471] hub 2-0:1.0: 10 ports detected
[  226.244103] usb 1-8: new high speed USB device using ehci_hcd and address 2
[  226.292315] pata_amd 0000:00:06.0: version 0.3.10
[  226.292372] pata_amd 0000:00:06.0: setting latency timer to 64
[  226.293793] scsi0 : pata_amd
[  226.293920] scsi1 : pata_amd
[  226.294995] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[  226.294998] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[  226.385999] usb 1-8: configuration #1 chosen from 1 choice
[  226.459033] ata2: port disabled. ignoring.
[  226.459070] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.6
1.
[  226.459630] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[  226.459642] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 20 (level,
 low) -> IRQ 20
[  226.459648] forcedeth 0000:00:07.0: setting latency timer to 64
[  226.980669] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:
1d:72:a7:23:86
[  226.980675] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim ms
i desc-v3
[  226.980707] sata_nv 0000:00:08.0: version 3.5
[  226.981256] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[  226.981268] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, l
ow) -> IRQ 23
[  226.981319] sata_nv 0000:00:08.0: setting latency timer to 64
[  226.981382] scsi2 : sata_nv
[  226.981591] scsi3 : sata_nv
[  226.981817] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[  226.981821] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[  227.760037] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  227.768307] ata4.00: ATA-8: Hitachi HDP725016GLA380, GMBOA52A, max UDMA/133
[  227.768311] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[  227.784304] ata4.00: configured for UDMA/133
[  227.784412] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDP72501 GMBO PQ
: 0 ANSI: 5
[  227.785065] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[  227.785071] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 23 (level, l
ow) -> IRQ 23
[  227.785119] sata_nv 0000:00:08.1: setting latency timer to 64
[  227.785394] scsi4 : sata_nv
[  227.785565] scsi5 : sata_nv
[  227.785792] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[  227.785796] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[  228.252041] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  228.260133] ata5.00: ATAPI: HL-DT-ST DVDRAM GH15F, EG00, max UDMA/100
[  228.276139] ata5.00: configured for UDMA/100
[  228.591443] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH15F     EG00 PQ
: 0 ANSI: 5
[  228.613754] usbcore: registered new interface driver libusual
[  228.620570] Initializing USB Mass Storage driver...
[  228.621502] scsi6 : SCSI emulation for USB Mass Storage devices
[  228.621603] usbcore: registered new interface driver usb-storage
[  228.621608] USB Mass Storage support registered.
[  228.621714] usb-storage: device found at 2
[  228.621716] usb-storage: waiting for device to settle before scanning
[  228.632269] Driver 'sd' needs updating - please use bus_type methods
[  228.632382] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  228.632399] sd 3:0:0:0: [sda] Write Protect is off
[  228.632403] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  228.632429] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[  228.632498] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  228.632514] sd 3:0:0:0: [sda] Write Protect is off
[  228.632517] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  228.632543] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[  228.632548]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  228.647630]  sda1 sda2
[  228.674840] sd 3:0:0:0: [sda] Attached SCSI disk
[  228.681468] sd 3:0:0:0: Attached scsi generic sg0 type 0
[  228.681529] sr 4:0:0:0: Attached scsi generic sg1 type 5
[  228.685860] sr0: scsi3-mmc drive: 78x/78x writer dvd-ram cd/rw xa/form2 cdda 
tray
[  228.685866] Uniform CD-ROM driver Revision: 3.20
[  228.685983] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  233.620257] usb-storage: device scan complete
[  233.621258] scsi 6:0:0:0: Direct-Access              USB Flash Memory 5.00 PQ
: 0 ANSI: 0 CCS
[  233.623878] sd 6:0:0:0: [sdb] 3914752 512-byte hardware sectors (2004 MB)
[  233.624537] sd 6:0:0:0: [sdb] Write Protect is off
[  233.624542] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  233.624546] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  233.627613] sd 6:0:0:0: [sdb] 3914752 512-byte hardware sectors (2004 MB)
[  233.628110] sd 6:0:0:0: [sdb] Write Protect is off
[  233.628114] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  233.628117] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  233.628128]  sdb: sdb1
[  233.628999] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  233.629120] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  233.849956] EXT3-fs: INFO: recovery required on readonly filesystem.
[  233.849962] EXT3-fs: write access will be enabled during recovery.
[  235.546991] kjournald starting.  Commit interval 5 seconds
[  235.547008] EXT3-fs: sda1: orphan cleanup on readonly fs
[  235.566290] ext3_orphan_cleanup: deleting unreferenced inode 11288592
[  235.566332] EXT3-fs: sda1: 1 orphan inode deleted
[  235.566334] EXT3-fs: recovery complete.
[  235.595548] EXT3-fs: mounted filesystem with ordered data mode.
[  243.594977] udev: starting version 141
[  243.751808] udev: renamed network interface eth0 to eth6
[  244.888687] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/inpu
t/input2
[  244.888959] ACPI: Power Button (FF) [PWRF]
[  244.891491] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0
C:00/input/input3
[  244.894394] ACPI: Power Button (CM) [PWRB]
[  244.941835] ACPI: WMI: Mapper loaded
[  244.951711] input: PC Speaker as /devices/platform/pcspkr/input/input4
[  245.101965] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[  245.101989] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf400
[  245.125740] Linux agpgart interface v0.103
[  245.357494] nvidia: module license 'NVIDIA' taints kernel.
[  245.616943] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 22
[  245.616951] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 22 (level, lo
w) -> IRQ 22
[  245.616959] nvidia 0000:00:0d.0: setting latency timer to 64
[  245.618359] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 1
4:59:10 PST 2009
[  245.770395] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[  245.770403] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 21 (level,
 low) -> IRQ 21
[  245.770425] HDA Intel 0000:00:05.0: setting latency timer to 64
[  245.851520] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/seri
o1/input/input5
[  247.386587] lp: driver loaded but no devices found
[  247.456898] Floppy drive(s): fd0 is 1.44M
[  250.472022] floppy0: no floppy controllers found
[  250.875473] EXT3 FS on sda1, internal journal
[  251.547793] type=1505 audit(1299643110.734:2): operation="profile_load" name=
"/usr/share/gdm/guest-session/Xsession" name2="default" pid=4041
[  252.016938] type=1505 audit(1299643111.206:3): operation="profile_load" name=
"/sbin/dhclient-script" name2="default" pid=4045
[  252.017108] type=1505 audit(1299643111.206:4): operation="profile_load" name=
"/sbin/dhclient3" name2="default" pid=4045
[  252.017177] type=1505 audit(1299643111.206:5): operation="profile_load" name=
"/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=4045
[  252.017235] type=1505 audit(1299643111.206:6): operation="profile_load" name=
"/usr/lib/connman/scripts/dhclient-script" name2="default" pid=4045
[  252.229472] type=1505 audit(1299643111.418:7): operation="profile_load" name=
"/usr/lib/cups/backend/cups-pdf" name2="default" pid=4050
[  252.229711] type=1505 audit(1299643111.418:8): operation="profile_load" name=
"/usr/sbin/cupsd" name2="default" pid=4050
[  252.719870] type=1505 audit(1299643111.906:9): operation="profile_load" name=
"/usr/sbin/tcpdump" name2="default" pid=4054
[  253.746412] powernow-k8: Found 1 AMD Athlon(tm) Processor 2650e processors (1
 cpu cores) (version 2.20.00)
[  253.746455] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x16
[  253.746458] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16
[  255.095056] /dev/vmmon[4574]: Module vmmon: registered with major=10 minor=16
5
[  255.095071] /dev/vmmon[4574]: Initial HV check: anyNotCapable=0 anyUnlocked=1
 anyEnabled=1 anyDisabled=0
[  255.095077] /dev/vmmon[4574]: HV check: anyNotCapable=0 anyUnlocked=1 anyEnab
led=1 anyDisabled=0
[  255.095081] /dev/vmmon[4574]: Module vmmon: initialized
[  255.126339] /dev/vmci[4585]: VMCI: Driver initialized.
[  255.127049] /dev/vmci[4585]: Module vmci: registered with major=10 minor=60
[  255.127054] /dev/vmci[4585]: Module vmci: initialized
[  255.249849] ppdev: user-space parallel port driver
[  256.468967] /dev/vmnet: open called by PID 5174 (vmnet-dhcpd)
[  256.468980] /dev/vmnet: hub 1 does not exist, allocating memory.
[  256.470148] /dev/vmnet: port on hub 1 successfully opened
[  256.508212] /dev/vmnet: open called by PID 5178 (vmnet-netifup)
[  256.508230] /dev/vmnet: port on hub 1 successfully opened
[  256.546548] /dev/vmnet: open called by PID 5184 (vmnet-dhcpd)
[  256.546561] /dev/vmnet: hub 8 does not exist, allocating memory.
[  256.546576] /dev/vmnet: port on hub 8 successfully opened
[  256.596553] /dev/vmnet: open called by PID 5186 (vmnet-natd)
[  256.596570] /dev/vmnet: port on hub 8 successfully opened
[  256.638674] /dev/vmnet: open called by PID 5190 (vmnet-netifup)
[  256.638697] /dev/vmnet: port on hub 8 successfully opened
[  259.137278] RPC: Registered udp transport module.
[  259.137285] RPC: Registered tcp transport module.
[  259.232176] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  259.456516] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery d
irectory
[  259.483492] NFSD: starting 90-second grace period
[  261.000039] Clocksource tsc unstable (delta = -249909998 ns)
[  262.455370] Bluetooth: Core ver 2.13
[  262.458563] NET: Registered protocol family 31
[  262.458574] Bluetooth: HCI device and connection manager initialized
[  262.458583] Bluetooth: HCI socket layer initialized
[  262.490679] Bluetooth: L2CAP ver 2.11
[  262.490690] Bluetooth: L2CAP socket layer initialized
[  262.514425] Bluetooth: SCO (Voice Link) ver 0.6
[  262.514435] Bluetooth: SCO socket layer initialized
[  262.544347] Bluetooth: RFCOMM socket layer initialized
[  262.544898] Bluetooth: RFCOMM TTY layer initialized
[  262.544907] Bluetooth: RFCOMM ver 1.10
[  262.548875] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  262.548887] Bluetooth: BNEP filters: protocol multicast
[  262.596208] Bridge firewalling registered
[  267.813414] /dev/vmnet: open called by PID 4657 (vmnet-bridge)
[  267.813426] /dev/vmnet: hub 0 does not exist, allocating memory.
[  267.813440] /dev/vmnet: port on hub 0 successfully opened
[  267.813459] bridge-eth6: up
[  267.814581] bridge-eth6: attached
[  270.389161] NET: Registered protocol family 10
[  270.393184] lo: Disabled Privacy Extensions
[  280.476031] vmnet8: no IPv6 routers present
[  280.808014] eth6: no IPv6 routers present
[  281.132015] vmnet1: no IPv6 routers present
[  534.084124] ISO 9660 Extensions: Microsoft Joliet Level 3
[  534.114952] ISOFS: changing to secondary root
[  547.909813] NET: Registered protocol family 17
[  554.092234] /dev/vmmon[6842]: HostIF_ReadUptime: detected settimeofday: fixed
 uptimeBase old 18445444430595266088 new 18445444084913518843 attempts 1
```

It's no wonder it takes eight to nine minutes.  I'm surprised it didn't take 20 minutes.

---

### Post by what-is-a-computer? on 2011-03-12
should I remove that last part with the names, by editing same?

---

### Post by Hakunka-Matata on 2011-03-12
you could pipe the output of dmesg to a file, you know how now.  and then look thru the file for clues about where it might get hung up, I don't know what 99% of the output code means, I just look for something that makes sense. have you changed acpi settings, tried different ones, in BIOS?

Turn off floppy controller, turn off 'quick boot', try to get as much information displayed as possible during boot so you can maybe see something that's not going right.

Have you tried setting your BIOS to "default settings"?  to get back to a starting point.  also, you could install lm-sensors which displays component temperatures if you're suspicious of those.  Is your CPU fan running, is a cable stopping if from turning when you put the cover back on the box, ????  

Install device-manager if you haven't and look there to see if any devices are messed up.  Install all this stuff through synaptic package manager, right?

I forgot what you're trying to accomplish at this point, hehe

I'm done for today, good luck

---

### Post by what-is-a-computer? on 2011-03-12
Let me remind you of the goal here, Hakunka.  

We....don't....want.........it.................to................take..............
nine..........minutes............to..............boot............my.............computer!!!!  And........
we.............don't..................want..................to...........have ............to.........put.........
an...............acronis................disk................in..............in........order............to......boot
................this "heap of junk."

That is sooooo funny!:D  You're funny!

I tried to change the default in BIOS.  It won't let me.
I've changed several things in BIOS but nothing of import.  Only things like a password, one time I disabled the USB controler and then reenabled it.  It's set for 90 degrees or something with regard to overheating.  There is no "quickboot" as an option.

And, no, the fan is running perfectly and nothing is blocking it or hitting it.  

Thanks for your help.

You know what?  After this, I'm done forever.:D

Does anyone want to buy a computer?  I'll sell it to you cheaply!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Asking price:  $300.  That's verrrrrrrrrrrrrrrry cheap.

---

### Post by JKyleOKC on 2011-03-13
Actually, we ARE making progress, just in very small increments. It's not yet time to abandon ship.

Your dmesg listing tells me quite a bit although much of what it reports looks strange to me. The numbers at the left side of each line, inside brackets, are a tally of seconds and millionths of seconds since starting to boot. Here's the first long delay:```
[   28.365527] checking if image is initramfs... it is
[  221.163323] Freeing initrd memory: 8049k freed

```which indicates a delay of almost 200 seconds, more than 3 minutes, between completing a check of the initial boot image satisfactorily (the "it is"), and freeing its memory. During that time, the code in that image was presumably setting things up to proceed -- but usually the delay between these entries is less than a second.

The other long delay is here: ```
[  281.132015] vmnet1: no IPv6 routers present
[  534.084124] ISO 9660 Extensions: Microsoft Joliet Level 3

```This is over 250 seconds, or four minutes 10 seconds, when loading the code to read data from the CD. Those two long delays together account for about 7.5 of the 8 minutes you are experiencing.

Lots of shorter delays look suspicious, also. Once we get all of your important files out of your home directory onto a USB stick for safekeeping, the best bet will be to do a total wipe of the disk, and re-install from scratch. I don't think you have any actual hardware failure, but rather something is causing that box (and not the other one that's working) to overheat somewhere. That could trigger a thermal shutdown (the original freeze 10 days ago while you were working), and since such a shutdown didn't give time for all the data to be written back to the disks, it could result in damage to the system files.

Your fdisk listings gave me the names needed for the step by step procedures. The two "/dev/sda" lines are your hard disk, and the single "/dev/sdb" line is the flash drive. I assume that this flash drive is the one from which you can boot. If so, you need to plug in another, empty, one into a second USB socket, and run the fdisk command again to verify that it now shows a third line for "/dev/sdc" which will be the empty one. Let me know which is the empty one and I'll get going with the salvage procedure.

Sorry to be gone so long. I just got up; it's 9:45 AM here in Oklahoma and we just went to DST...

---

### Post by what-is-a-computer? on 2011-03-13
Good morning, Jim.  Glad you got to sleep in.

Before you do any salvaging, would it be prudent for me just to copy my grub folder from this working machine and copy it over to the other nonworking machine.

I have everything I need off of that computer.  But if I replace the grub folder, is it possible that that will solve the issue?

And also, on the VMNET1 delay, there is no VMNet1 in my VPN connections, my wired connections.  So Why would that even be on there?  Is there a way to delete it from the system?  I have another VMnet, not "1."

Also, Jim, if acronis will finally upload, I can go ahead and just redo the image from before.  It worked beautifully.  Something has gotten corrupted.

I forget to tell you previously something else that happened when it froze because I had forgotten until yesterday when I couldn't connect the broken computer to the internet (but can now.)

When it froze, I was not hooked up to the internet and that computer will never be.  But my computer showed that it was like connected wirelessly.  So emails  flashied up on the compute, I was copying digital files, the mouse dropped, everything was like happening at once.  So...thought that may shed some light on what has gone wrong.  This image works perfectly.  So I could redo it, save a ton of time.

If I disable the LAN connection within BIOS, doesn't that stop any wireless connection?

---

### Post by what-is-a-computer? on 2011-03-13
PS  As for "reading the data from the CD," isn't that because it's reading the acronis CD that's in there and that's why it's taking so long?

I cannot remember if once I turn the computer off, if I completely remove the CD from the drive, whether it will go ahead and boot or not.

Also, last question for awhile:

When I reconnected in my cables after changing to the new hard drive (which I'm back to the old one)  there was a PV3 cable and a PV4 cable.  One is for the hard drive; one is for the CDROM.  They both fit interchangeably.  If I got those mixed up -- which I don't think I did -- does that matter which of those cables goes on which device?

---

### Post by JKyleOKC on 2011-03-13
> **what-is-a-computer? said:**
> I have everything I need off of that computer.  But if I replace the grub folder, is it possible that that will solve the issue?If you really have **everything** from that machine that you need, then there's no need to salvage any data files. I've been under the impression that you had a number of files on it that were not on the other one, and that you wanted to preserve.

Just copying all the content of the /boot/grub folder over **might** work, but since there's no real way of telling just how badly the file system was damaged it equally well might not. Doing a full restore from the Acronis image would be much more trustworthy.

The VMNet drivers, so far as I know, are strictly for "virtual machine" use and you've not mentioned any use of VMWare packages. So their presence, and the wireless-like action you mention, are a bit of a mystery to me... If you have a wireless card in the machine, it could have automatically connected to a wireless access point in your neighborhood and been on line without your knowledge, but that would add a whole new dimension of possibilities!

At this point, if you have everything you want to keep copied off to safety and don't need anything that's on the machine, then I'd reformat the drive to erase everything that is there, and reload the Acronis image. That should bring things back to normal; if the problem still persists, then it would be time to take it to the tech folk for a complete diagnosis.

As for the plugs, I really don't know whether they are interchangeable. I believe that they are, but am not certain. Perhaps someone else will chime in with better information about them!

---

### Post by what-is-a-computer? on 2011-03-13
Yes, Jim, I have a virtual machine on this computer, but on my VNP connections, it's vm8, not 1.  

I already have everything I need off of this machine.

I'm going to try the acronis image and see if that works.

Thank you!  I'll let you know if it works!

---

### Post by JKyleOKC on 2011-03-13
> **what-is-a-computer? said:**
> Yes, Jim, I have a virtual machine on this computer, but on my VNP connections, it's vm8, not 1.The numbering can vary on the internal names such as VMNet1; it's not necessarily the same as that used on the VNP connection.

Virtualization makes use of "kernel modules" that are totally invisible to you as a user; I suspect that one or more of these got damaged by the unexpected shutdown, and that it's the cause of that final long delay. It might even have something to do with the first long delay also.

I had something somewhat similar happen to my email box here, a couple of weeks ago. The virtual machine that was running my email program went wacky and I could not access it. I was able to shut down the virtual machine, through the terminal, but then when I attempted to start it again it went into a loop: that is, it would get almost all the way through the first Windows XP screen, then flash a blue screen error, and start over. It kept this up until I forced the VM to power down at the start of a sequence.

It turned out that the virtual drive of that virtual machine had lost its last 2.5 GB, which included very critical data needed for the machine to finish booting. Nothing that I tried was able to salvage anything, so I lost six months worth of email messages (didn't have a more recent backup; I do now!) and had to totally re-install my email program on a new virtual machine.

If your damage affected the VM or any of its driver modules, that could be the reason for both delays -- and for all the other strange things! I look forward to your report...

---

### Post by what-is-a-computer? on 2011-03-13
Oh, Jim, I'm so sorry you lost the emails.  I HATE that.  

I could take my VM folder off of this machine and put it on the other one.  Wonder if that would work, if maybe that is the issue.   I could do that prior to transferring the grub folder.

Then if those fail, I'm going to redo the entire computer with the image.....if it will take my passport drive.  I already tried that once, at the beginning, but probably didn't wait long enough.  i didn't realize it was taking all this time to boot up.  So I'll retry that as a last resort.

TTYS.

PS  If I upgrade -- which I guess this is the time -- to 10.04, I can just do the upgrade to "KK" and then to "LL" through update manager?   I don't need to begin again, right, if I redo the image?  10.04 isn't where I can just upload only that version from scratch, is it?    I have to do it with upgrades, right?  I would hate to have to set this all up again, email, vm, etc, etc.

---

### Post by JKyleOKC on 2011-03-13
> **what-is-a-computer? said:**
> I could take my VM folder off of this machine and put it on the other one.  Wonder if that would work, if maybe that is the issue.   I could do that prior to transferring the grub folder.

...

PS  If I upgrade -- which I guess this is the time -- to 10.04, I can just do the upgrade to "KK" and then to "LL" through update manager?   I don't need to begin again, right, if I redo the image?  10.04 isn't where I can just upload only that version from scratch, is it?    I have to do it with upgrades, right?  I would hate to have to set this all up again, email, vm, etc, etc.It's always recommended to do a "clean install" from scratch, but that does require setting everything up again. My network got invaded (though my own carelessness, not any vulnerability in Linux) about a year ago so I had to reformat and reinstall from scratch; that's when I moved from 8.04 to 10.04. And it took me almost a week to get it all rebuilt, plus a couple of months of tweaking after that to get most of the kinks worked out. I still have to go through some hoops any time I reboot this box, since it has a semi-flaky network card in it that doesn't like to start properly every time.

Thus in your case, I would go through the two-step upgrade.

As for moving things between the two machines, as I said before since we have no real idea how widespread the damage to the non-working one actually was, there's no way of predicting whether a partial move can work. There are disk areas called "superblocks" and "inodes" that are absolutely essential to getting access to files, and if even one of those got damaged along the way, no amount of file copying can fix it. Restoring a complete disk image from Acronis, however, would include those areas along with everything else, so that's what I would try as the first thing now. Just give the Acronis CD plenty of time to boot.

Something just occurred to me: your /dev/sda2 partition on the hard drive is the swap area and many if not most Linux distributions will use the hard disk swap area if one exists rather than creating their own. If that partition's internal data got damaged, this could explain why everything is so slow to boot up -- and if that's what happened, once the Acronis restore completes the machine ought to be back to normal operation because the restore will re-create that partition along with the rest. Let's hope that this is the case...

---

### Post by what-is-a-computer? on 2011-03-13
Jim, if it took you, a brilliant computer expert, two months and a week to set your computer up.....................it would take me a year.  So when I upgrade, I'll go the two-upgrade route.  

I'll report back to you here shortly once I have this done.

---

### Post by what-is-a-computer? on 2011-03-15
Jim, not a good report.

All day yesterday I tried to boot my computer and it will not.  I couldn't get into my program.

So last night after work I came home, restarted it with the Acronis disk in, saw the screen, clicked on the home version and had my passport drive hooked into a USB port, it goes to a black screen and left it there all night.

This morning, nothing.  When I moved my mouse it said "Loading, please wait," which is what it said last night.  So nothing happened.

This is my question, though:  Are you certain this is not like a power issue, that three-prong outlet that's built into the computer?  Could that have gone bad and it's not getting enough power?

I'm sure this is a ridiculous question but:  If I put in a new hard drive as I did a few days ago  and it does the same thing, why would that indicate a VM issue when there's no VM even on that hard drive?  It's an empty hard drive.  I would think it would boot up immediately through the Live CD with the new HD in but it didn't.  So are you sure it's not hardware-related?

Or the CDROM?  And one time, when trying to get it to boot, I disabled the CDROM completely through BIOS and it still won't boot.  So if the CDROM is bad and you disable that, shouldn't the computer then just start easily without that if it's been dsiabled and it's a broken CDROM?

Just questions of which I certainly don't know the answer.

I hear something inside the computer move and then stop, like the CDROM is starting but can't get enough power and then it stops.  If the power supply inisde was bad or it had a short somewhere could that account for it?

---

### Post by JKyleOKC on 2011-03-15
> **what-is-a-computer? said:**
> This is my question, though:  Are you certain this is not like a power issue, that three-prong outlet that's built into the computer?  Could that have gone bad and it's not getting enough power?No, we can't be certain of anything when dealing with electrical gadgets; we just have to work with the highest probabilities. However, because of the way the power supply works to change mains power into clean direct current at various voltage levels, a shortage of mains power would almost certainly result in the electronics not working at all. That is, no lights, no display, no reaction to mouse or keyboard actions.

Reading this report it occurred to me that a memory failure might cause the problems you are seeing, since the boot-up code has to be loaded into RAM to work -- and the memory sticks are about the only thing that has remained constant through all of your attempts.

There's a memory testing program built into the Live CD disk; it's on the original menu, the one that starts out "Try without installing" and as I recall is the third or fourth line of that menu. The program is called "memtest86" and is definitely available from the grub menu if you can get that far on a LiveCD bootup. If you can get to it, select it and let it run for several hours or more. Overnight is best. It will give a running display of its actions, that won't have much meaning to you except for the tally of how many errors it finds. If that count ever gets above zero, or if the report stops changing, then the probability that you've found the problem is very very high, and it's time to take the machine to a repairman for replacement of the bad RAM stick.

Static electricity can destroy such a stick in a fraction of a second when you touch it, and you may not even feel the shock. Years ago, I lost one of my first PCs to exactly that. That's why I suggest taking it to the shop rather than replacing a stick yourself...

If that also fails, then I'm out of ideas! Good luck!

---

### Post by what-is-a-computer? on 2011-03-15
Jim, I put in a brand new memory stick a couple of days ago.  So now there's two of them, one being brand new out of the package.    So.....  

I already did "part" of that memory test.  You can see the result  on some of the output I posted previously.   I quit doing it because it took so long.  It got through a good portion of it but I assumed it wasn't doing any good.  So I stopped it midstream.

I'll do it again, letting it run its full course.

thanks again.

---

### Post by JKyleOKC on 2011-03-15
It will run forever if you let it. When it completes one pass, it starts another. On an overnight run it will finish quite a few such passes.

The reason for letting it run so long is that many memory problems are intermittent, possibly heat-related, so the first several passes may show no errors and then the problem begins to be detected. That's why the rule is "the longer, the better."

---

### Post by what-is-a-computer? on 2011-03-15
thanks for the info!

---

### Post by what-is-a-computer? on 2011-04-06
Just received the dreaded phone call:  The computer tech believes that it's my mother board.

Thank you, everyone.

---

