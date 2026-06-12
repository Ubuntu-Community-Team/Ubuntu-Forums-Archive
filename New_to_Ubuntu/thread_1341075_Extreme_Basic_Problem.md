---
title: "Extreme Basic Problem"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by OldGoat58 on 2009-11-29
Following the suggestions of just about everyone I burned a new CD of Ubuntu last night.  This time I chose the Ubuntu 9.10 i386 distribution instead of the AMD64 hoping that the 32 bit OS would function better.  I checked the disc for errors, I tested the memory, and am all set to install Ubuntu 9.10 i386 and REMOVE the Ubuntu 9.10 AMD64.  

I am not trying to get fancy and create an additional partition as suggested.  After reading how to create partitions I decided I was too basic for that function at this time.  I get to step 5 on the install where you enter user information.  I am using the same naming conventions that I used with the 64 bit installation, "mike", full name "Mike Hofer", computer name "mike-laptop", however this time I am getting an error message that states "User name must start with one lower case letter and can be followed by any combination of numbers or other lower case letters".

I have tried mike, mike01, m01ike, br549, ou812, hike, and there message remains the same as stated above.

HELP!
Still Frustrated in Fairless Hills PA
Mike

---

### Post by ubudog on 2009-11-29
This has happened to me before too.  All I had to do was go back one page and then go back to the information page.  Enter the username "mike" again and see what happens.

---

### Post by OldGoat58 on 2009-11-29
> **ubudog said:**
> This has happened to me before too.  All I had to do was go back one page and then go back to the information page.  Enter the username "mike" again and see what happens.


I have tried going back, exiting and restarting the install, everything but standing on my head.  Is it possible that since I am trying to install Ubuntu 9.10 32 bit over Ubuntu 9.10 64 bit that I'm going to need to use a completely different naming convention?

(banghead)

---

### Post by Bartender on 2009-11-29
Jeepers, it's been one thing after another hasn't it?  

I've never seen the problem you describe.  The only thing that comes to mind is turn it off and plug in a different keyboard.  A plain old PS/2 keyboard if you've got one laying around.

If the original keyboard is sending some wrong messages to the PC, that might explain some of the goofy problems you were having previously!

---

### Post by sandyd on 2009-11-29
turn the keyboard upside down, give it a few good whacks and try again.

---

### Post by jrrader on 2009-11-29
Hello again,  

If you are installing over the other operating system, the disk won't care what is on the drive.  It's going to format it anyway.  I can't be sure why you are getting this error, but I wouldn't waste much time on it.  I have had disks that check out fine, but don't work fine.  Hopefully you have a USB thumb drive (1GB is more than you need).  Download another ISO and then go to system> administration > USB start up disk creator.  You can do this from the Live CD.

Change your bios to boot from a usb drive when you restart and install from there.

What to download? I think you should listen to what quite a few people have said and go with [ubuntu 8.04]("http://www.ubuntu.com/getubuntu/downloadmirrors#bt") or [mint]("http://www.linuxmint.com/") (Mint 7).  Mint is still Ubuntu but it has been modified a little to be easier for people who are new to Linux to use.  You've got a lot of options out there, don't let one of them steal too much of your time.

---

### Post by OldGoat58 on 2009-11-29
Well, as the subject line suggests the issue is resolved.  I walked away, came back, started over, and it accepted "mike".  Couldn't change anything else on that page without the error repeating so I stayed with what worked.

I am new to Linux but I am not stupid.  I can normally figure my way out of just about everything so I would truly appreciate people not suggesting that I use a more "Windows Friendly" version of Ubuntu, or Wine, or whatever else is out there.

I chose Ubuntu/Linux after careful research and experimenting.  I have the "Help" window open at all times and try to solve my own problems.  I apologize if I have made anyone in this community feel as though I was trying to create trouble.  I can assure you that I would never purposely offend anyone.

Thank you for all of your assistance.  I will try very hard to not to abuse the forums again.

No Longer Frustrated in Fairless Hills, PA
Mike  =)

---

### Post by Desert Sailor on 2009-11-29
But just one comment here.  This is the beauty of Linux, Ubuntu and these forums.  If this had been a Mickysoft type problem, you would have spent hours trying to talk to someone in a far away place with whom you couldn't communicate, It's just so damn satisfying when you solve a problem now. I have been messing around with the new Grub2 and having a blast editing files and figuring out how things work.  It never would have been possible to me if the file had been a windows DLL.  You take it the way it's written, and if you don't like it, tough.

---

### Post by jrrader on 2009-11-29
I think you really misunderstood my, and many other people's, intentions here.  Mint is not "Linux Windows."  It is Ubuntu with restricted and non-free drivers preinstalled to make installation easier.  This does not mean anyone thinks you are stupid - If you mastered Tony Hawk's Pro Skater but had never been on a skateboard before, you would hardly expect to step on a real skateboard and skate like a pro.  The same is true when it comes to switching from Windows (which is a product you pay for and expect to work out of the box) to Linux (which is created and used by a community of people who just enjoy what they are doing).  This is also the reason Ubuntu has a message board rather than 1 on 1 customer service as you suggested - though you could get that if you asked someone (or paid canonical a lot of money for their services).  The bottom line is that everyone who responded to you was only looking to help you.

Except the wine thing - some people seem to just shout out wine whenever someone is having problems making the transition from Windows to Linux.  I don't think they have ever tried wine - it does not work with most Windows programs and is not a good solution to most problems.

Please don't take this as me being angry at you. I don't think you've offended anyone here.  Some posters come in swearing at everyone, angry because they can't get Ubuntu to work "like Windows," demanding help ASAP.  You were pretty tame compared to some of them.

---

### Post by Bartender on 2009-11-29
> **OldGoat58 said:**
> I would truly appreciate people not suggesting that I use a more "Windows Friendly" version of Ubuntu, or Wine, or whatever else is out there.

I'd suggest you read over your posts one last time before sending them.  

You come here asking for help, people give their opinions, you get tight-jawed.  Nobody is inferring that you're unintelligent by suggesting a distro that they found easier to use.  

If someone told you to RTFM that might be different.

---

