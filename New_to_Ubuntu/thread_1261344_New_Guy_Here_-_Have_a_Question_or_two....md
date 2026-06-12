---
title: "New Guy Here - Have a Question or two..."
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Marlowe221 on 2009-09-08
Greetings all,
 
I have a confession to make: I am a Mac OSX lover. Unfortunately, my Macbook Pro was damaged when I moved not long ago and I have been told it's pretty much totaled (and out of warranty as well...). 
 
I am a small business owner and could not afford to replace the computer (my personal machine, not a business computer) with another Mac. So I had to buy a PC... :( (please be gentle). It has Vista-64 on it which makes me want to jump out a window (pun intended).
 
It's an AMD/ATI HP laptop and I've been doing some reading around the net after stumbling onto Ubuntu as an alternative to Windows (oh how I wish I could install OSX Leopard on my HP...). I know there are some issues with ATI cards but that there are easily installed drivers that will give at least partial functionality.
 
So, all that said, my question is this: I use my computer for word processing, surfing the interweb :), and World of Warcraft. Am I stuck with Vista til I can save up enough for a new Mac or will I be able to do what I would like to do with Ubuntu on my machine?
 
Thanks!
 
P.S. - Or would a different Linux distro work better for me??

---

### Post by misfitpierce on 2009-09-08
Let me ask you the first thing that we will need to know... The word processing and web browsing will actually work better on Ubuntu than windows but the world of warcraft we will need to know something... 

What graphics card is in your machine? Nvidia _____, ATI _____, or Intel ______?

---

### Post by Penguin Guy on 2009-09-08
> **Marlowe221 said:**
> 
So, all that said, my question is this: I use my computer for word processing, surfing the interweb :), and World of Warcraft. Am I stuck with Vista til I can save up enough for a new Mac or will I be able to do what I would like to do with Ubuntu on my machine?

Word Proccessing - [COLOR="Green"]Yes[/COLOR]
Internet - [COLOR="Green"]Yes[/COLOR]
World of Warcraft - [COLOR="Red"]Good luck[/COLOR]
ATi Graphics Cards - [COLOR="Orange"]Not usually (my 3850 works fine)[/COLOR]

Incase you didn't know already, it is very hard (but not impossible) to run Windows applications on Linux.

---

### Post by NoaHall on 2009-09-08
Ubuntu is the best for you. It comes with Firefox, and has a in-built Office package(openoffice.org). You can also customize it to be quite a lot like Mac OS X. You'll find Linux much more like OS X than Vista. If you have a ATI card, it could cause problems(poor support).

---

### Post by Bölvaður on 2009-09-08
> **Marlowe221 said:**
> 
P.S. - Or would a different Linux distro work better for me??

That could well be. Perhaps Linux Mint which bases on Ubuntu might be something for you or possibly Open Suse, but those distros do not have the ubuntuforums.org which really makes ubuntu ubuntu.

I normally don't recommend using software that was designed for windows, but if you must then click this link : [WoW on Linux]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922")

[QUOTE=wikipedia]Although there is no_ official _version for any other platform, support for World of Warcraft is present in Windows API implementations **Wine** and Cedega, allowing the game to be played under **Linux** and FreeBSD[/QUOTE]



In the unlikely event of you not having any video signal when booting off the live cd (when you are going to install), you might need to select *safe graphic mode* from the live cd boot menu or add *noacpi* to the boot code.

I dont know about your word processing but open office 3 should be enough, it is an overkill for my needs.

---

### Post by Darkwing-Duck on 2009-09-08
Having run WOW on Ubuntu before it works fairly well under Wine. ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421))
 
My brother used this and it works just great out of the box for the install and game run.

---

### Post by Marlowe221 on 2009-09-08
Geez - that's a lot of replies really fast!
 
My graphics card is ATI Radeon 3200 (I believe, I'm at work at the moment)
 
Thanks for all the replies - I'll check out that WoW in Linux article.
 
Edit: Good to hear that the os will remind me of OSX.

---

### Post by NoaHall on 2009-09-08
I'm afraid that any attempt I've had at installing a Radeon 3200 on Linux has failed. However, this may be down to system conflicts, as the owner of the computer had installed a nvidia card without telling me. It's on the list of supported cards - but don't expect miracle performance out of it.

---

### Post by cariboo on 2009-09-08
I have an HP laptop with an ATI chipset in it, running Jaunty (9.04) it works quite well right of the box with open source drivers.

---

### Post by Marlowe221 on 2009-09-08
> **cariboo907 said:**
> I have an HP laptop with an ATI chipset in it, running Jaunty (9.04) it works quite well right of the box with open source drivers.
 
I don't suppose you play WoW do you? :)

---

### Post by terabyte1 on 2009-09-08
Marlowe221 I know how you feel about Vista. I had Vista Ultimate - the full version and it had more security holes than a colander. My quickie advice is to download a 64-bit copy of Jaunty Jackalope (9.04) to your desktop (its free)! and then burn iit to a cd. then load it via a cd-rom drive and start up your computer. No viruses. No problems (worth mentioning - if you do have pproblems this is what the forums are for or IRC can do the same thing - need more help get back in touch I'm usually on at night (UK) ok? Great! terabye1:guitar:

---

### Post by Vaeil on 2009-09-08
Surfing the web / Word Processing etc. works like a charm, wouldn't be that much of an OS if it couldn't do any of those, now would it?!

WoW is one of the applications that works best in Wine as far as I've had experience with (albeit, always with nVidia cards) - See this page [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine) [wowwiki] for a bunch of information if you hit any problems.

Good luck with your graphics card though!

---

### Post by SoftwareExplorer on 2009-09-08
> **Marlowe221 said:**
> 
Edit: Good to hear that the os will remind me of OSX.

If you do go with ubuntu, [have a look at this.]("http://sourceforge.net/projects/mac4lin/")

---

### Post by halitech on 2009-09-08
the ATI 3200 should be supported with either the ATI drivers or the ones provided by Ubuntu. Once installed, just check System - Admin - Hardware drivers and see if it is listed. If it is, simply enable it. If its not, go to [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English) and download the ATI catalyst drivers which should work.

---

### Post by Marlowe221 on 2009-09-09
So when I make the CD after downloading the file from the Ubuntu site, it will allow me to test everything out without totally erasing my current OS?? 
 
Do I have that right?

---

### Post by Windows Nerd on 2009-09-09
> **Marlowe221 said:**
> So when I make the CD after downloading the file from the Ubuntu site, it will allow me to test everything out without totally erasing my current OS?? 
 
Do I have that right?
That you do. After making the cd, insert the cd, reboot, it will boot from the CD, and you should be presented with a list of options. Press enter to select an option and the arrow keys to switch options. Select "Try Ubuntu without any change to your computer". You will then continue to boot from the CD and you will be sent straight to the desktop.

If ya like what ya see, and everything works, double click the install Icon on your desktop and away you go :).

Scott

---

### Post by sailthesea on 2009-09-09
> **Windows Nerd said:**
> That you do. After making the cd, insert the cd, reboot, it will boot from the CD, and you should be presented with a list of options. Press enter to select an option and the arrow keys to switch options. Select "Try Ubuntu without any change to your computer". You will then continue to boot from the CD and you will be sent straight to the desktop.

If ya like what ya see, and everything works, double click the install Icon on your desktop and away you go :).

Scott

 Or you could try a dual boot

---

### Post by terabyte1 on 2009-09-09
You can even look at the kernel of a Linux Distro (distrobution, type, etc). The nearest to that is the Registry in Windows - but because Microsoft patents and copyrights everything - your not allowed to examine the system - - good thing too, cos you'd be off like sugar off a shovel when you see the problems there! Linux is not copyrighted or patented, you can look at the kernel (like I said - which is the 'brain' of the operating system), even take it apart and re-compile it to your own liking and nowone will say "Boo!" to you. This is why there are so many versions of linux out there and flavours are whast makes the world go around... but I suggest you find out how linux works and how to build the system before going around tampering with it - its very easy to destroy the whole system with a couple of clicks, which is why Linux has some security features that you can switch on or off if you feel like it that is as feature-rich as a US government-backed security system such as Selinux (but that is why Ubuntu switch it off by default) it can really mess up your system if you forget the password because you can encrypt the system as well as protect it! More of that from someone else more qualified than I. Suffice to say, we would love you to join this forum and become one of the family - but like free-will, again, that's up to you! Best Wishes! terabyte!:guitar:

---

### Post by Marlowe221 on 2009-09-09
Well I'm definitely going to do the Live CD thing and play around with it for a while - get a feel for it, etc. It seems there are varying results on ATI video card performance so it will be interesting to see what happens there...
 
Personally, I have no desire to see the kernel. I wouldn't even know what I was looking at. I have no fear of settings panels, terminals, config files, file structure, and etc when it comes to Windows or Mac operating systems. I've explored them and educated myself about them over the years. But acutal code? I know nothing about it and can die happy in that condition!

---

### Post by SoftwareExplorer on 2009-09-11
> **Marlowe221 said:**
> Personally, I have no desire to see the kernel. I wouldn't even know what I was looking at. I have no fear of settings panels, terminals, config files, file structure, and etc when it comes to Windows or Mac operating systems. I've explored them and educated myself about them over the years. But acutal code? I know nothing about it and can die happy in that condition!
That's fine--not everyone who uses ubuntu needs to be a developer. After all, I would say ubuntu's goal is to make a version of GNU/Linux that the average joe can use, without having to know about how it works underneath.

---

### Post by LewRockwell on 2009-09-11
> **Marlowe221 said:**
> ...
my Macbook Pro was damaged when I moved not long ago and I have been told it's pretty much totaled

...

what was damaged?

.

---

### Post by Marlowe221 on 2009-09-11
Not sure exactly. It would boot up fine before the move, and would get hung up after it.
 
I tried reseting PRAM, booting from the CD, etc. None of that was any help.
 
The dudes at the Apple Store couldn't get it going either.

---

### Post by oldfred on 2009-09-11
You said you reset ram, did you check every connection?  A move can cause things to get loose. I would check every connection and give everyone a push to make sure it is fully connected.

---

### Post by Marlowe221 on 2009-09-11
It's a laptop, there's not much that can get loose that I know of....

---

### Post by LewRockwell on 2009-09-11
> **Marlowe221 said:**
> Not sure exactly. It would boot up fine before the move, and would get hung up after it.
 
I tried reseting PRAM, booting from the CD, etc. None of that was any help.
 
The dudes at the Apple Store couldn't get it going either.

did the Apple Store Techs pop the top on it?

there was a batch of motherboards that had a problem with the connection area where the board that controls the brightness and keyboard illumination plugs in

we have personally removed this board and the offending loose connector(normally firmly and properly soldered to the motherboard) and that particular unit is still in operation(without auto-dimming and no more illuminated keyboard of course)

not that we're suggesting you go outside of your comfort level of course(and this is only one of several possible problems)

.

---

### Post by Marlowe221 on 2009-09-11
To be honest I'm not sure if they did or not. I do not personally have the skill or knowledge required to attempt such invasive surgery myself but I do have a buddy who may. I'll have to check with him...

---

### Post by LewRockwell on 2009-09-11
> **Marlowe221 said:**
> To be honest I'm not sure if they did or not. I do not personally have the skill or knowledge required to attempt such invasive surgery myself but I do have a buddy who may. I'll have to check with him...

If you look around the web you should be able to find a disassembly guide for your machine

as an example, this is the sort of guide that might assist you and your friend:

[http://www.xlr8yourmac.com/systems/PB_G4_15_AL_takeapart/AL_PB_G4_take-apart.html](http://www.xlr8yourmac.com/systems/PB_G4_15_AL_takeapart/AL_PB_G4_take-apart.html)

naturally you should try to find the EXACT guide for your machine

naturally you should exhaust all other reasonable alternatives BEFORE cracking open the machine

however, that being said, there is a true sense of accomplishment when you are able to fix a perplexing deficiency...and, with the unit out of warranty and inoperative, you really don't have much to lose

(although depending on the unit you have, you might still be better off selling it, as is, to someone familiar with that depth of repairs...as opposed to digging into it and causing further, and/or subsequent damage where none existed previously)

note: a new motherboard for your unit might easily cost $400.00 to $600.00 or more, depending on which and where...you price them

.

---

