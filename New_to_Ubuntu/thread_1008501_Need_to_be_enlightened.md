---
title: "Need to be enlightened"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by dain3 on 2008-12-11
Hey everyone.I am a first year Computer Science student. I am pretty much interested in learning everything about computers and how to be an efficient user. Someone recommended that I joined a Linux community for starters; and that Linux OS was better than Windows.My problem is that I pretty much grew up using only Windows and I am curious about what makes Linux better than Windows in the eyes of my peers at school and to what extent. I look forward to hearing from someone soon and being apart of and learning from this community.

---

### Post by halitech on 2008-12-11
what makes it better is personal for each person. For me, the fact that I don't have to worry about upgrading hardware to keep up with their requirements, not worrying about viruses and spyware, that it is rock stable and best of all, it is free (both to download and to do what I want with)

---

### Post by Duck2006 on 2008-12-11
Download the live CD and see how it works with your system.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Some reading that may help on your way.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by dain3 on 2008-12-11
Okay.I get the idea of not having to worry about upgrading hardware and the OS being free to download but what I don't get is why don't you have to worry about viruses or spyware and what do you mean by it being rock stable.

> **halitech said:**
> what makes it better is personal for each person. For me, the fact that I don't have to worry about upgrading hardware to keep up with their requirements, not worrying about viruses and spyware, that it is rock stable and best of all, it is free (both to download and to do what I want with)

---

### Post by halitech on 2008-12-11
> **dain3 said:**
> Okay.I get the idea of not having to worry about upgrading hardware and the OS being free to download but what I don't get is why don't you have to worry about viruses or spyware and what do you mean by it being rock stable.

I don't have to worry about viruses or spyware because there basically there isn't any (yes, I know it exists but reports in the wild are almost non-existant) and rock stable means I reboot about once a month because I want to, not because the system has locked up or started running like a snail up hill in winter.

---

### Post by dain3 on 2008-12-11
So is it that there is some sort of code in the OS that reduces level of threat? Just curious why it's like that.

---

### Post by halitech on 2008-12-11
its the way the entire OS is designed, worse a virus could do (if you got one) would be to delete your home folder as the security is designed to prevent access to anything you don't own.

---

### Post by dain3 on 2008-12-11
> **halitech said:**
> its the way the entire OS is designed, worse a virus could do (if you got one) would be to delete your home folder as the security is designed to prevent access to anything you don't own.

Thanks much.Gonna check it out right now.Let you know how it is for me

---

### Post by Duck2006 on 2008-12-11
Most viruses are set to work with *.exe's and *.com and *.dll files witch linux does not have.

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
[http://digg.com/linux_unix/How_many_Linux_viruses_are_there_](http://digg.com/linux_unix/How_many_Linux_viruses_are_there_)

---

### Post by halitech on 2008-12-11
> **Duck2006 said:**
> Most viruses are set to work with *.exe's and *.com and *.dll files witch linux does not have.

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
[http://digg.com/linux_unix/How_many_Linux_viruses_are_there_](http://digg.com/linux_unix/How_many_Linux_viruses_are_there_)

actually I ran into a person the other day that did have dll files on his system that we figured were used by a linux program, just can't think what it was at the moment.

---

### Post by cek on 2008-12-11
> **halitech said:**
> actually I ran into a person the other day that did have dll files on his system that we figured were used by a linux program, just can't think what it was at the moment.

Some applications use DLL's -- though they aren't native (ala Win32 DLLs).  F-Spot, for instance, uses DLLs, presumably for its interaction with the CLR (F-Spot is written in C#).

---

### Post by halitech on 2008-12-11
might have been f-spot but not sure. I just remember thinking it waws weird to see them on a linux system but I think maybe they did mention they programmed in C#

---

### Post by tjwoosta on 2008-12-11
> Hey everyone.I am a first year Computer Science student. I am pretty much interested in learning everything about computers and how to be an efficient user. Someone recommended that I joined a Linux community for starters; and that Linux OS was better than Windows.My problem is that I pretty much grew up using only Windows and I am curious about what makes Linux better than Windows in the eyes of my peers at school and to what extent. I look forward to hearing from someone soon and being apart of and learning from this community.

i would not say that one O.S is ever better then another because they all have their advantages and disadvantages

but in my experience tech savy users usually prefer to have complete control over their system


with linux you have absolute complete control over everything


if you wanted, you could choose any base system you want and piece together all of the components from the ground up (creating a completly custom system)

you can choose between desktop environments

then you can choose between window manaagers

then you can customize even further and choose what components you need with your system

for instance..

do you want an extreamly fast and minimalistic system that will run with 32mb ram or less

or do you want a top notch 3d accelerated desktop effects/ bling loving environment

or do you want anything in between

you can do it all with linux!!


not to mention its free!!

and open source!



if you really want to learn computers from the ground up, and learn some of the inner workings behind the blinds, linux is definatly the way to go

---

### Post by juanoleso on 2008-12-11
@dain3
Windows is what is called monolithic.  Every part of windows is built into the kernel: networking, file browsing, firewall, HAL, sound control.  With their servers, it is even more so where the http servers and the user account control are all built into the kernel.  If one piece of the puzzle fails, there is a chance that the whole system could fail.  That is why you have to restart windows every once in a while or when some service isn't working right you may have to restart the entire machine.  

With Linux, on the other hand the saying goes, everything that doesn't need to be in the kernel is not in the kernel.  It is what is called modular.  For instance, the default ubuntu networking program is network manager, but that can be switched out for WicD.  Or if sound is not working properly or can't get setting just right, switch from pulseaudio to ALSA.  In addition, when one piece isn't working that piece can be restarted without bringing down the entire box.

That is stability.

Some other things:
-Most everything is Open Source and so you could modify some part of a program to fit your needs. (and its free)
-Commandline still means something and sometimes it is a lot easier to use it than a GUI everything.
-As for viruses and malware: Linux is designed to be multi-user, multiple people can be logged into the computer at any one time through different consoles (impossible in windows desktop OS).  But they are "trapped" in their own home folders.  If they were to run a virus, it would only be able to destroy or damage files in their home folders (which contains "my documents" and then personal settings for different programs).  The OS and the programs themselves are unharmed unless the user has executed the program as root user which is the superuser.  With ubuntu and a lot of other Linux Distributions users have programs that download and install programs almost exclusively from a safe central respository.

I wrote this out mostly for my benefit, =-D , but it still applies.  It is a summary of this link...

[COLOR="Blue"][The Register - Security Report: Windows vs Linux]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/")[/COLOR]

---

### Post by cmay on 2008-12-11
to use open-source software is more of a lifestyle for many people. it gives a sence of belonging and being a part of creating something. you cant buy a product from a closed source company and then change it like you can with open-source. of course it takes more devotion and work if you want to use the software this way. its one of the things i noticed to be true for me. anyway. if you want to learn about computers then go find the book operative systems design and implementation by andrew s tannenbaum and read it. try the library first the book is not cheap. then try download the minix 3 operative system and play around with it. it comes with that book on a cd also. it will teach you many things about computers in generel. 
hope it helps .

---

### Post by oldos2er on 2008-12-11
You might want to read this essay: [http://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar](http://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar) about the differences between Win* and Linux.

---

### Post by markbuntu on 2008-12-11
The big thing about using linux is choices, more choices than you need really, but choices nonetheless for absolutely everything from the kernel to the textures of the little buttons on your application windows. The best thing is if you don't like something you can change it, right down to rewriting the source code.

Distro watch lists 312 different linux distributions.

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by dain3 on 2008-12-12
> **tjwoosta said:**
> i would not say that one O.S is ever better then another because they all have their advantages and disadvantages

but in my experience tech savy users usually prefer to have complete control over their system


with linux you have absolute complete control over everything


if you wanted, you could choose any base system you want and piece together all of the components from the ground up (creating a completly custom system)

you can choose between desktop environments

then you can choose between window manaagers

then you can customize even further and choose what components you need with your system

for instance..

do you want an extreamly fast and minimalistic system that will run with 32mb ram or less

or do you want a top notch 3d accelerated desktop effects/ bling loving environment

or do you want anything in between

you can do it all with linux!!


not to mention its free!!

and open source!



if you really want to learn computers from the ground up, and learn some of the inner workings behind the blinds, linux is definatly the way to go



Sounds fun and all but how do I actually get the effects I want.Remember I am totally clueless when it comes to the linux OS.

---

### Post by dain3 on 2008-12-12
So your saying that I can make a linux OS suit me in terms of looks and performance. But how. What do I do...how do I get it done?

---

### Post by Duck2006 on 2008-12-12
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by perspectoff on 2008-12-12
Read the Guides:

Ubuntu Guide ([http://ubuntuguide.org](http://ubuntuguide.org))

Kubuntu Guide ([http://kubuntuguide.org](http://kubuntuguide.org))

---

### Post by Paqman on 2008-12-12
> **dain3 said:**
> what makes Linux better than Windows

IMO the main thing that Linux does better than Windows is package management.

Say I don't like my media player and I want to try a new one:

**On Ubuntu:**
Open Add/Remove programs and look under the Sound & Video category (pretty logical so far). It will has a brief description of each one and shows how popular they are. I tick which ones I want and hit "apply". That's it. They''re all installed in one go. You can remove them the same way. It's easy, and everything is guaranteed 100% spyware and adware free. Plus, the system will automatically install updates for that program, and all other installed software. That's pretty smooth.

[B]
On Windows:[/B]
Ok Windows! Show me what media players are available for installation! Hmm, looks like you can't. Guess i'll have to trawl around the net and do my own research. I sure hope none of this includes spyware or adware, but since i'm downloading it from some random site, i'll never really know. Ok, let's run the installer. My god, why are you asking *me* where to install this? You're the OS, don't you *know* how to install it? And why have you installed it in my menu under the name of the manufacturer??? That makes no sense, I don't care who manufactured it!
Ok, so it's installed. How do I keep it up to date (especially security patches!) Well, it *might* have an "update" button buried in some menu somewhere, but every app is different, so you'll have to search through all the app's menus looking for one. Or maybe there isn't one, and it's installed a completely separate updater. Which will run all the time (Wtf? Why not just once a day?) slowing down the machine and joining all the other baffling icons in the system tray. Or maybe there's no updater at all, and i'll have to keep checking the manufacturer's website. Then i'll have to manually download the entire program and install it all over again. What a mess.

Basically, there's a lot of things about Windows that suck quite badly (and I say this as a Windows user) but because you've never used anything else, you haven't seen how much better things could be. It's well worth trying out Ubuntu. If nothing else it will give you some perspective about what's good and what's bad about Windows, so you can make a more informed choice about what OS you decide to use.

---

