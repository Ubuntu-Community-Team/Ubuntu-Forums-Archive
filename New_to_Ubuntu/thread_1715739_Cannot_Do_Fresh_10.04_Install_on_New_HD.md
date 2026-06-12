---
title: "Cannot Do Fresh 10.04 Install on New HD"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by what-is-a-computer? on 2011-03-27
I've had problems with my computer booting.

So I have decided to get rid of that hard drive, put in a new one, create a live USB stick and start from scratch.

I've created the live USB stick.  I attach the new HD.  I turn on the computer.  I press F10 to select the "removable" device as the boot device.  An Ubuntu screen comes up.  I click on "English" and then "Install Ubuntu" and my computer screen just stays black with a blinking cursor.

What I am doing wrong, please?

And that is all I want on this computer is just Ubuntu, nothing else.

Also, I don't see the USB stick blinking.  It's like it's not reading it.

---

### Post by Hedgehog1 on 2011-03-27
Before beginning the install process, you need to establish a partition map on the 'empty' hard drive.

Using gparted from the: 'System >> Aministration >> Gparted Partition Editor' menu, under the 'Device' menu select 'partiton table' and create a new one for the drive.

***The Hedge***

:KS

---

### Post by what-is-a-computer? on 2011-03-27
there's nothing on this HD.   So how can I go to system and admistration?  The other hard drive has been completely disconnected from my computer.  I just have a new hard drive
only.

Maybe I'm not understanding.

---

### Post by Hedgehog1 on 2011-03-27
Sorry - I made too many assumptions... I do that...

Install the **NEW** HD in the computer, and attach the cables (with power off).

Next, please boot off the LiveCD/Live USB, select 'TRY', and then:

Using gparted from the: 'System >> Aministration >> Gparted Partition Editor' menu.

Inside gparted (**G**nome **PART**ion **ED**itor), under the 'Device' menu select 'partiton table' and create a new one for the drive.

You can then run the install.

***The Hedge***

:KS

---

### Post by what-is-a-computer? on 2011-03-27
okay.  I'll try that.  Thanks!

---

### Post by what-is-a-computer? on 2011-03-29
I get to the screen that says "Try Ubuntu" and I press "enter,"  it just sits there at a black screen with a blinking cursor.  It will go no further than that.

---

### Post by Hedgehog1 on 2011-03-29
You are hanging on the video card.

Were you using 10.10 on this system before?  Or 10.04?

When you press 'try' or 'install', press and hold the <SHIFT> key down.  When the grub menu comes up, press 'e' to edit, arrow down to the line that says 'quite splash' and and add 'quite splash **nomodeset**' next to those options.  Then press F10

***The Hedge***

:KS

P.S. the above option should do the trick.  Here are more options 'just in case'


[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)

---

### Post by what-is-a-computer? on 2011-03-29
actually I was using Jaunty.  (I know.  It's "old.")  At least I'm trying to upgrade to 10.04.:D.

I'll try this.

And thank you so much for these suggestions!

---

### Post by what-is-a-computer? on 2011-03-29
it says "Loading /casper/vmlinuz.........................................................................
Loading /casper/intrd.lz...........................................................................ready.

And the curosor is up at the top, just blinking.

Now what?

Oh, and I did have Jaunty but then I tried to do two upgrades with upgrade manager.  But now the HD is completely wiped.  So there's nothing on my HD.

_______________________

Okay.  I have tried again and instead of using <shift>, there was something that said do F6 and then ESC.  I have done that.  I typed in nomodeset-- and it is booting but is hanging right now at PME disabled.  So it's stuck there.
Now what?

---

### Post by collisionystm on 2011-03-29
Is your usb drive light flashing? 

If it is a desktop use a usb port on the back of the computer. Generally on older machines the ports in the front are usb 1.0 and are very slow causing huge delays.

---

### Post by collisionystm on 2011-03-29
and did you make the usb with another ubuntu or with pendrivelinux

---

### Post by jtarin on 2011-03-29
How much physical memory do you have at present?

---

### Post by what-is-a-computer? on 2011-03-30
Okay.  I just started again and put the USB on the back of the computer.  It only blinks when I put it in and the system is turning on.   It blinks about three or four times and then goes off.

Yes, I made the live USB from this computer that I'm working on.  I made it with USB Disk Startup Creator.

As for my memory, I have two memory sticks.  So I think it's 2GB.  I just put a new one in right out of the package because someone suggested it could be the memory.

I did a memory test and it tested with no errors.

I think that addresses all the questions.

Now, what?  It boots as far as a bunch of zeros and "PME# disabled."  It's stuck there.

---

### Post by what-is-a-computer? on 2011-03-30
PS  And just now when I had to restart it, it didn't hold the "nomodeset --" command.  I had to put that in again.  It said requiet splash or something like that........again.  Maybe that's normal to have to put that command in again.

---

### Post by collisionystm on 2011-03-30
It might be a bad .iso file. Are you making sure to check the box to FORMAT the usb when you run the usb installer from ubuntu?

---

### Post by what-is-a-computer? on 2011-03-30
One time last week, before I erased my hard drive, it went to the "Try Ubuntu" desktop.  So wouldn't that prove that it's all right?

I followed these directions.  

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

And prior to doing that, I previously reformatted my USB to FAT32 if that's what you mean.
Sorry.  I'm not computer savvy.

---

### Post by collisionystm on 2011-03-30
Well even if there was no hard drive in your computer it would still prompt you with try ubuntu

its just a menu on the usb itself that was installed by the ubuntu usb installer

so.... it doesnt really prove that its alright.... lol. and you erased your hard drive? So you have no way of making another boot up right.....

---

### Post by what-is-a-computer? on 2011-03-30
What's wrong with making another one with the computer I'm talking to you on?  lol.

Should I?

I've done it twice, you know.  It wouldn't do it the first time.  So I did it again and voila, it made the live USB.

I can certainly try it again.

---

### Post by collisionystm on 2011-03-30
well this might be a silly question, but have you thought about making a cd?

AND before you make another, see if your usb boots on the computer you are on.... dont erase anything just hit try ubuntu and see if it works

---

### Post by Supergoo on 2011-03-30
Just wondering , has anything else changed on the computer, did you put in more, memory? Also check all your connections in the computer as you might have bumped something loose. 



Supergoo

---

### Post by what-is-a-computer? on 2011-03-30
too late.  I already erased it.

But the answer is:  Yes, it worked on another computer.  I forgot to tell you that.  Gosh, I should have tried it again on this computer.  Duh!  Anyway, I'm making another one right now.

And as far as memory, yes, I added more memory.  I have checked all the connections.  I re-seated both memory sticks and re-seated all the other cables.

I also put in a new CMOS battery.

---

### Post by cye05 on 2011-03-30
this might be a dumb suggestion but is your computer 32 bit or 64 bit. i know it will hang on the load screen if you put a 64 bit cd into a 32 bit machine again sorry if this dumb point to make.

---

### Post by what-is-a-computer? on 2011-03-30
it's not a dumb question.  I think it's 64.  How do I find out for certain?

that's what I downloaded was 64.  


And I just reformatted the USB to FAT32.  Then I redid the USB live disk creator and created a new live USB.

Then I put it into this computer.

Works perfectly.  And this computer is very close to the other computer.  So it must be 64.

Oh, how I would love to see that purple screen on that other computer.
And just so you know, I did see that screen on that computer a few days ago after I left the computer sit for awhile.  And it moved back and forth on those red dots and then stopped on one of them and it quit moving from dot to dot.  So it got stuck on that splash screen.

---

### Post by cye05 on 2011-03-30
well besides physically checking the specs on your chip you could just make a bootable usb with a 32 bit Ubuntu iso. regardless if the computer is 64 or 32 bit the 32 bit .iso should work. my 2 cents lol

---

### Post by jtarin on 2011-03-30
> **cye05 said:**
> well besides physically checking the specs on your chip you could just make a bootable usb with a 32 bit Ubuntu iso. regardless if the computer is 64 or 32 bit the 32 bit .iso should work. my 2 cents lol
Unless you can give us the specifications of your computer and know without a doubt that it is 64 bit, then I agree with the suggestion above. I know it's a hassle to download and redo your USB but it will eliminate that part of the equation with some assurance. Your downloads should be checksummed to insure you got a correct download. Your USB should be formatted correctly before transferring the .iso.
Failing this it is possible it's your USB stick itself. I've seen them work on some computers but not all some times.....then I have seen them work on a dual-boot computer with one OS and not the other.

As to your memory...I think its adequate for installation.

---

### Post by Paddy Landau on 2011-03-30
+1 to trying a 32-bit version. I have two computers that are virtually identical (same manufacturer, similar model number, same case, etc.) but one is 32-bit and the other 64-bit.

---

### Post by what-is-a-computer? on 2011-03-30
It's 64 bit.  I just called the manufacturer.

I have AMD Athlon 2650e Processor
NVIDIA GeForce 6150SE Graphics
DVD+-RW Super Multi-Format Dual Layer Optical Drive
160GB Hard Drive
1 (now 2) GB DDR2 Memory
14-in-1- Digital Media Reader.

So there you have it.

Last night I completely reformatted my USB to FAT32.  
And I redid the 64-bit ISO.

And this is not a dual-boot computer.  Only Linux.  

So all of that is functioning properly.

PS  Is it normal for the CD/DVD drive to rev up and then just stop?

---

### Post by what-is-a-computer? on 2011-03-30
just made a 32-bit ISO.

Only will boot as far as the "PME# disabled" and then the blinking cursor.

Is there anything else I can try?

---

### Post by what-is-a-computer? on 2011-03-31
Have tried the 32-bit ISO with a CD.  Can boot as far as the purple "Ubuntu" screen.  It cycles through those red dots on the splash screen for a bit and then stops on the second red dot and it frozen there.

---

### Post by Paddy Landau on 2011-03-31
This sounds more and more like a hardware issue.

I'm no expert in hardware, but maybe it will make a difference if you use the [alternative (non-GUI) installer]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate"). If possible, connect your computer to the Internet (using Ethernet) before you boot, because the installer downloads drivers as required and that can make a big difference.

---

### Post by what-is-a-computer? on 2011-03-31
thank you.  I'll try it.

---

### Post by what-is-a-computer? on 2011-03-31
Paddy, I cannot get this to download properly.

I have the iso torrent on my desktop.    When I click on it, it says something about peer-to peer.  Am I clicking on the right thing?

---

### Post by Paddy Landau on 2011-03-31
Did you want the torrent or the normal download?

If you intended the torrent:

[LIST]
[*]A torrent (peer-to-peer) is a fancy way of storing bits of the file all over the world -- extremely reliable, can at times be a bit slow.
[*]You need a suitable torrent program. I believe you use Windows; you can use [Deluge]("http://deluge-torrent.org/"), which also works on Mac and Linux.
[*]Start Deluge (or whatever torrent program you choose) and give it the torrent file you downloaded. Deluge will download the file for you.
[/LIST]
If you intended the normal download:

[LIST]
[*]Return to the [Alternative Downloads web page]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate").
[*]Scroll down to "Alternate Installer Details".
[*]In the first sentence, there is a link, "[location near you]("http://www.ubuntu.com/start-download")". Select it.
[*]It will automatically take you to a server near you. Find the Ubuntu 10.10 Maverick link, then the Alternate Install CD, then select either 32-bit or 64-bit as you prefer.
[/LIST]

---

### Post by what-is-a-computer? on 2011-04-06
Just received the dreaded call.

The computer tech believes it's my mother board.  Rats, rats and triple rats!

Thank you, all.

---

### Post by Hedgehog1 on 2011-04-06
Will it be more reasonable to replace the PC rather than a motherboard swap?

I hate hardware problems...


***The Hedge***

:KS

---

### Post by what-is-a-computer? on 2011-04-06
Yes,  $250 for a new board/$84 to put it in.

And you know what?  That was basically a brand new computer.  I had it stored in a box as a backup for probably a year and a half.  It had only been used for about a week.  So it was a brand new computer basically.

Very disheartening.  I've having difficulty accepting it.

But you're right, Hedge.  It's cheaper to get a new computer.  Thank you for your suggestions previously.  I love this forum.  It's extremely helpful for novices.

---

### Post by Paddy Landau on 2011-04-07
Sorry to hear about your problems. It's a pity that warranties run from the time you purchase, not from the date you start using the device!

Good luck with your new computer.

---

### Post by what-is-a-computer? on 2011-04-12
thank you so much, Paddy.

---

### Post by Hedgehog1 on 2011-04-12
Sooo...  Did you get a new PC??? (Hedgehogs LOVE hardware....) :D


***The Hedge***

:KS

---

### Post by what-is-a-computer? on 2011-04-12
No.  This one is going in for a new motherboard.  I found a better deal.  So we'll see if they can fix it.

---

### Post by Hedgehog1 on 2011-04-13
OK - thanks for the update.  Hope they can fis it, too (actually, a motherboard swap is usually successful) :D



***The 'Hardware Lovin' Hedge***

:KS

---

### Post by what-is-a-computer? on 2011-04-13
thanks, Hedge.  I cannot wait to announce that I have a machine up and running on 10.04LTS.

---

