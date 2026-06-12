---
title: "Do I need to have an internet connection?"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by goofychick36 on 2009-12-10
HI, I have just installed Ubuntu Studio on my laptop.  It is an old laptop that I stopped using a few years ago because the moden stopped working and I wanted a new machine with more memory anyway.  It was lying around doing nothing and I need to use linux for my computing degree and cannot always hang around university after lectures to use their machines so I have taken a chance and overwritten Windows XP on this laptop and the installation has worked fine and its all very nice but I dont know what to do with it now.  I dont seem to have any of the software that they have at university although I have the studio version and not the version they have which I think is 9.10.  I have no software and I do not appear to be able to get any.  I keep being prompted to set-up a network connection which is not going to be possible on this laptop.  Have I wasted my time setting this up, can you only really use linux if you have the internet.  Right now what I really need in order to make any use of linux is to get office applications installed and some FTP software to convert my word processed and presentation documents so that I can open them.  Also it would be nice if I could store and play music but it wont play the mp3 tracks that I put on the machine.  I seems to open my photographs ok but thats all.

---

### Post by Bartender on 2009-12-10
Need more input.  You say that it's not possible to set up a network.  How come?  Does the laptop have no wireless card inside?  If not, what sort of port does it have on the outside?

I'm sure there are Linux-compatible PCMCIA wireless cards.

You do know that OpenOffice can save documents in a Word-compatible format, don't you?  Click "Save As" and browse thru the choices for Microsoft Office 97 or something like that.

For mp3 you need to get online first, then download restricted-extras.  Wait, I'm not sure about studio, but the standard Ubuntu install doesn't include some of the proprietary stuff.  I don't have the exact name right now.  Just google "Ubuntu restricted extras" for further info.

---

### Post by Raffles10 on 2009-12-10
I'm afraid you will need an internet connection to use Ubuntu for the things you want. Ubuntu doesn't include any proprietary software like mp3 codecs, these have to be downloaded separately from Ubuntu's repositories. Linux Mint is a Ubuntu based distribution that does include all the necessary codecs for music and video and would provide a better experience on a machine with no internet.

There are some distributions like Debian that have all their software available for download as iso files that can be burned to cd's or dvd's, you can then install everything or just use the cd's as a local repository, but to get all their software available locally you will need 31 cd's !

Because Linux systems use online repositories for their software installation an internet connection is really essential. Only so much can be made available on one 700mb cd.

---

### Post by goofychick36 on 2009-12-10
The laptop has an internal modem which stopped working several years ago and anyway I dont want to set the laptop up with internet access at the moment.  I want to know how do you get software if you dont have an internet connection.  Or don't you!  Because I get the impression that without the internet it's your tough luck!

---

### Post by cholericfun on 2009-12-10
not exactly sure how cause i never had the problem myself but just to nudge you to search a bit further you can download software packages on some other computer and then transfer them to the laptop. again- its not as easy as aptitude and such because of dependencies but i guess easy enough.

---

### Post by cholericfun on 2009-12-10
actually:

this is back from the stone age but have a look (didnt study the details now)

[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by goofychick36 on 2009-12-10
Thank you.  I suspected that I had made a mistake installing linux, but I was'nt using the laptop anymore anyway so it does not matter that I removed Windows XP.  I will put back in the cupboard where I got it from.

---

### Post by mikewhatever on 2009-12-10
First, it seems like a dumb move to install Ubuntu studio for office applications. OO is included by default in Ubuntu proper, so that you should have gone with that. As for installing apps off line, it is possible, but you will need a connected computer somewhere.
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by madmax.santana on 2009-12-10
> *Originally posted by: [cholericfun]("http://ubuntuforums.org/member.php?u=678842")*
you can download software packages on some other computer and then transfer them to the laptop

I guess I have your answer, at lease somewhat. There is a free source program (still under development) which lets you download all Ubuntu softwares and updates packages on Linux or Windows, with dependencies of course and then you can transfer them to your laptop and install them via debian package manager. Have a look at it. It's called Keryx
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by cholericfun on 2009-12-10
> Thank you. I suspected that I had made a mistake installing linux, but I was'nt using the laptop anymore anyway so it does not matter that I removed Windows XP. I will put back in the cupboard where I got it from.

your choice,
@mikewhatever:didnt know that ubuntu studio didnt include OpenOffice - kinda makes sense though.

now whether you do a fresh install or use the LiveCD or just download OO to a usb or whatever... 

without internet your computer cant get software *easily*, still working though?

good luck

---

### Post by Raffles10 on 2009-12-10
> **goofychick36 said:**
> Thank you.  I suspected that I had made a mistake installing linux, but I was'nt using the laptop anymore anyway so it does not matter that I removed Windows XP.  I will put back in the cupboard where I got it from.

There's no pleasing some chicks..... :roll:

---

### Post by goofychick36 on 2009-12-10
> **madmax.santana said:**
> I guess I have your answer, at lease somewhat. There is a free source program (still under development) which lets you download all Ubuntu softwares and updates packages on Linux or Windows, with dependencies of course and then you can transfer them to your laptop and install them via debian package manager. Have a look at it. It's called Keryx
[http://keryxproject.org/](http://keryxproject.org/)
That's spooky.  I have just come across Keryx myself and am looking into that now.  Thank you.

---

### Post by Raffles10 on 2009-12-10
That's another thing.......they're always changing their minds. :o

---

### Post by beetleman64 on 2009-12-10
You don't NEED an internet connection, but USB wireless cards are so cheap now that you really should get one. Ask someone a bit more knowledgeable than myself about compatibility, but you can get one for £20 from PC World.

---

### Post by cholericfun on 2009-12-10
> **beetleman64 said:**
> You don't NEED an internet connection, but USB wireless cards are so cheap now that you really should get one. Ask someone a bit more knowledgeable than myself about compatibility, but you can get one for £20 from PC World.

+1

even super-magic-can-do-everything-including-breakfast-OS is going to be feeling a bit wanting without www

---

### Post by Bartender on 2009-12-10
Keryx is not ready for prime time.  I've spent hours on two separate occasions and finally got it to work, but a rank newb woulda given up.

After all the setting up. Keryx failed.  Synaptic said a package was broken, and refused to do anything until it could go online and talk with the Ubuntu repository servers.

Is this laptop so old that it doesn't have an Ethernet port?

---

### Post by goofychick36 on 2009-12-11
> **Bartender said:**
> Keryx is not ready for prime time.  I've spent hours on two separate occasions and finally got it to work, but a rank newb woulda given up.

After all the setting up. Keryx failed.  Synaptic said a package was broken, and refused to do anything until it could go online and talk with the Ubuntu repository servers.

Is this laptop so old that it doesn't have an Ethernet port?
Yes I have a broken package, libdns50, my only option appears to be to remove the package.  I cannot use the Add/Remove Application program since using Keryx.  Not that I could use it before since I have no internet connection but at least before it used to get the list of software but now it will not even do that.  
So you don't think that I will ever be able to get software via Keryx, because i'm a bit screwed otherwise.  
The laptop is about 6 years old, the internal modem stopped working about 3 years ago and I replaced the laptop about 2 years ago and it has just been lying around since then.  I thought I would try Linux on it because I occassionaly have to use it at university and would like to understand it better.  I cannot use mobile broadband on this laptop because I live in a village and connectivity is dreadful.  On my other laptop which is a windows machine I have wireless so I take the laptop to hotspots to use the internet.  I cannot do this with the old laptop that is now running linux because the battery no longer charges so I am reliant on mains power.  I suppose I could take the laptop to a friends house to use but even then I would have to get a new mobile broadband account and even then there is no guarentee that I will be able to set up the internet connection, linux is not exactly user friendly - nothing is ever explained your expected to just know.
I think I am flogging a dead horse here and should just leave it.  How stupid is it to make the whole thing reliant on an internet connection.  Using  a computer does not revolve around the internet, I dont have the internet at home but i'm on my computer for hours every day and would be lost without it.  I'm just glad I still have my Windows laptop.

---

### Post by mutex023 on 2009-12-11
Try APTonCD. What you need to do is install whatever software you need in your college machine having the net connection, Create a CD with those downloaded packages using APTonCD, then use this CD to install the same packages onto your home laptop, Use the 'Add CDROM' option in the synaptic package manager : Settings>Repositories>Other software>Add CDROM.

---

### Post by joes7 on 2009-12-11
Definitely, pal :)! You need it for the things you've described.

---

### Post by Bartender on 2009-12-12
goofychick -
I read thru your last post and would say you've got two choices.

As you mentioned, abandon ship.  That old lappy's got too many problems.

Or, spend money.  Buy a new battery for the old laptop, and find a wi-fi card that would work with it so that you could go online wherever you can find broadband.

I have a bad feeling that buying a new battery and wi-fi card for that old clunker would be a waste.  Especially when you can get a functional netbook running Atom for about $400 or an entry-level laptop for not much more.

I'm guessing the original idea with the old clunker was gaining a functional laptop for free.  Sounds to me like that's not gonna happen.  I know I'd be tempted to start throwing money at the old rig, but that might not be very cost-effective.

---

### Post by goofychick36 on 2009-12-12
**problem now solved.  Thank you to those that were of help/tried to help.**

---

### Post by goofychick36 on 2009-12-12
> **goofychick36 said:**
> hi, i have just installed ubuntu studio on my laptop.  It is an old laptop that i stopped using a few years ago because the moden stopped working and i wanted a new machine with more memory anyway.  It was lying around doing nothing and i need to use linux for my computing degree and cannot always hang around university after lectures to use their machines so i have taken a chance and overwritten windows xp on this laptop and the installation has worked fine and its all very nice but i dont know what to do with it now.  I dont seem to have any of the software that they have at university although i have the studio version and not the version they have which i think is 9.10.  I have no software and i do not appear to be able to get any.  I keep being prompted to set-up a network connection which is not going to be possible on this laptop.  Have i wasted my time setting this up, can you only really use linux if you have the internet.  Right now what i really need in order to make any use of linux is to get office applications installed and some ftp software to convert my word processed and presentation documents so that i can open them.  Also it would be nice if i could store and play music but it wont play the mp3 tracks that i put on the machine.  I seems to open my photographs ok but thats all.
**problem now solved.  Thank you to those that were of help\tried to help.**

---

