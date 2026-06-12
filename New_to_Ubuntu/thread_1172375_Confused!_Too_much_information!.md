---
title: "Confused! Too much information!"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by Fastio on 2009-05-28
Hello,

first of all, let me apologize, cause i'm sure this will be a noob question but i guess that's why this forum exists ;)

I've been reading info about Ubuntu all day, cause i want to install it on an old laptop but i'm a bit confused...

I have an old laptop with 256 ram, 10gb HD and 700 Mhz that is currently running Windows Xp SP3, taking ages to start and open any application! After much reading i decided to go for Xubuntu, cause i basically only use it for internet browsing and i want to be able to read today's newspaper before tomorrow, due to the time it takes to open a browser window :D

My problems are:

There are many versions of Xubuntu, common sense says "use the latest stable one" but i was wondering if i should use an older stable version cause my laptop is also ancient? Any recommendations?

Should i try it in the LiveCD version first, to see if it recognizes my wireless card and the usb hub?

If i get the green ligh in the LiveCD version, should i use the minimal CD image to avoid "extra weight" on the system or go for the full ISO? In any case, i can replace Windows completely, correct?

Thanks for the help, i really appreciate it!

---

### Post by halitech on 2009-05-28
for the specs you have, Xubuntu *should* work okay but it may not for you. I would suggest 8.04 due to it being LTS and therefore you won't *need* to update as often.

With only 256 meg of ram, the live cd *probably* won't run as it neds 384. 

If you are only using it for browsing the web, then I would go with a minimal install and add just what you want. Here is a good set of instructions for Debian with XFCE (runs even faster then Xubuntu on the same hardware)
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

---

### Post by ibutho on 2009-05-28
Try the latest version first because it seems like your system meets the minimum specs. If you decide to download the live cd, you can use it for installation which will save you the hassle of downloading another iso.

---

### Post by halitech on 2009-05-28
> **ibutho said:**
> Try the latest version first because it seems like your system meets the minimum specs. If you decide to download the live cd, you can use it for installation which will save you the hassle of downloading another iso.

the live cd requires 384 meg of ram to run and he only has 256 so if it runs he's lucky

---

### Post by philinux on 2009-05-28
xubuntu livecd needs this much ram.

[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20alternative%20(Xubuntu](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20alternative%20(Xubuntu))

---

### Post by Screwdriver0815 on 2009-05-28
according to this [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

you are fine with the system requirements. So you also could use the normal Live CD. 

regarding the question if you should use the newest version:

the newer the version the better the chance that all your Hardware is supported. But if you have an Intel graphics card, you could get into trouble with Jaunty jackalope (the newest version). Because there is a bug in the driver for these cards.

Trying with the Live CD is a good idea but if the hardware doesn't work in the Live CD it doesn't mean that it doesn't work at all. because Ubuntu and all its different tasts (like Xubuntu) have a feature which installs proprietary drivers if you want. This feature doesn't work in the Live CD session.

You can replace Windows completely in any case - yes. But you also could set up a dual boot. But with a 10 Gb HDD it doesn't make much sense.

---

### Post by cb951303 on 2009-05-28
In my experience xubuntu will be at least as slow as a full gnome desktop on that system. I had a few ancient laptops (and I must say they were better than yours :)), tried xubuntu (8.04 if I remember correctly) and it was not bearable.

IMHO xubuntu is a very bloated and slow XFCE distro.

You can start with a minimal ubuntu installation and build your XFCE system. That would be fast (in theory). I can't recommend it if you're a beginner though.

---

### Post by ibutho on 2009-05-28
> **halitech said:**
> the live cd requires 384 meg of ram to run and he only has 256 so if it runs he's lucky

Thanks for the correction. I thought it was 256MB of RAM.

---

### Post by capnthommo on 2009-05-28
> There are many versions of Xubuntu, common sense says "use the latest stable one" but i was wondering if i should use an older stable version cause my laptop is also ancient? Any recommendations?

Should i try it in the LiveCD version first, to see if it recognizes my wireless card and the usb hub?

If i get the green ligh in the LiveCD version, should i use the minimal CD image to avoid "extra weight" on the system or go for the full ISO? In any case, i can replace Windows completely, correct?

Hi fastio
welcome to the forums
first, i would recommend running from the live cd first.  as you say, that will let you know if your machine will be compatible.  remember though, that it will run noticeably slower from cd than when it is installed to hard drive.
what you do is insert the cd, shut down, restart and select boot from cd if you need to (there should be instructions on how to do this when you switch on - probably F12 or F2 maybe) then when it gets into x/ubuntu choose the option to try without making any changes to your system.

i would recommend using a reasonably up to date version because if you go too far back the distro may be running out of support.  perhaps 8.04 LTS (long term support) would be good?

and yes, if you choose to you can entirely remove windows.  i did after about 3 weeks and have never looked back.  these are a great supportive bunch of people for if you have any problems.

dont forget though - ubuntu is not windows and there are differences - but it's worth getting used to 'cos it's brilliant.
don't forget, there are people here happy to help if you get into difficulty
good luck and again, welcome

EDIT:  sorry, seems i was beaten to the draw - i will duck out now and leave it to the clearly smarter cookies above

nigel

---

### Post by Screwdriver0815 on 2009-05-28
> the live cd requires 384 meg of ram to run and he only has 256 so if it runs he's lucky

> **ibutho said:**
> Thanks for the correction. I thought it was 256MB of RAM.

Xubuntu Live cd needs 192 Mb RAM

---

### Post by Fastio on 2009-05-28
> **cb951303 said:**
> You can start with a minimal ubuntu installation and build your XFCE system. That would be fast (in theory). I can't recommend it if you're a beginner though.

Hmmm, i'm a bit more confused now :D Thank you all for replying so quickly though!

I guess i'll rephrase the question:

What would you recommend for a beginner to install in that computer, knowing that is basically to browse the internet and see youtube or the occasional video?

I appreciate all the input, even though i might not understand it very well, helps me learn hehehe So thank you!

---

### Post by Coreigh on 2009-05-28
With the specs on that laptop you can very likely go ahead and use the standard Ubuntu desktop. I would definitely use 8.04 and make sure to set visual effects to NONE in the appearance menu. I have found that what slows down a computer are the flashy graphics effects and features. I have also had performance problems with web browsers. I have trued several different browsers and turned off Flash Java and javascript but the browser still can be slow even when the file browser (nautilus) and other programs are fast. So you may find that Xubuntu vs. Ubuntu may offer no performance difference.

---

### Post by Fastio on 2009-05-28
Ok, so everyone more or less agrees that i should try this first:

[]("http://releases.ubuntu.com/hardy/")[http://ftp.dei.uc.pt/pub/linux/xubuntu/releases/8.04.1/release/](http://ftp.dei.uc.pt/pub/linux/xubuntu/releases/8.04.1/release/) and check if it works ok with all my hardware?

Trying to determine my steps here :)

Edit: Ups, had the Ubuntu link, changed it to xubuntu.

---

### Post by NHArticleTen on 2009-05-28
try something like Puppy Linux, not all *nix are created equal

---

### Post by decoherence on 2009-05-28
> **Fastio said:**
> Hmmm, i'm a bit more confused now

LOL, welcome to the forum! Everyone has their own opinion on what an optimal system is.

I'd say 'just take the plunge with a version of Xubuntu.' If it's slow, try switching to [LXDE]("http://wiki.lxde.org/en/Ubuntu") or even [fluxbox]("https://help.ubuntu.com/community/Fluxbox"). A hint with the uber-minimalist fluxbox... just right click on the desktop. It's all there.

---

### Post by cb951303 on 2009-05-28
> **decoherence said:**
> LOL, welcome to the forum! Everyone has their own opinion on what an optimal system is.


anything with XFCE in it is not my optimal system :) I just wanted to point out the fact that I tried Xubuntu on better systems than OP's laptop and it was unbearably slow

---

### Post by Fastio on 2009-05-28
What about that Puppy Linux? Been reading about it, seems good and fast! Opinions? Is it as noob friendly as it seems?

P.S. - I forgot to ask, my mom sometimes uses it to talk in MSN, she'll still be able to do it but by some other software, right?

---

### Post by irv on 2009-05-28
I know that this thread might make you more confused that when you started, but you do have many choices. Seeing you have an old laptop, you can't really hurt it by trying different things.
Last year I got a hold of a dozen old desktops that I fixed up and sent to Africa. I installed 8.10 on all of them. I found that some had trouble with the install, but it was because of low memory. What I did was just take memory from one and put it into the other until the install was done. After I had the OS installed on all of them they all ran OK, The ones with less memory just a little slower than the ones with more, but they all ran.
Over the years I have installed different Linux Distros on older machines and I found that what ever I used ran better then Windows because you can remove all the stuff you don't want, and if you run less services the PC will run much faster.
I guess if I had to give you some good advice, I would say run a cut down version of what ever you install and you will get the best performance. If you are going to run youtube videos you will need a plugin in firefox to play them. You will fine out how to do this once you get everything installed.
One more thing, this is a learning curve and if you are like many of us on this forum, you will enjoy doing things like this. And remember we are a group of Linux user learning from one another.
Welcome to the group.

---

### Post by Sealbhach on 2009-05-28
Consider using Crunch Bang Linux, it is Ubuntu based but uses Openbox as the window manager so uses a lot less RAM:

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)


.

---

### Post by decoherence on 2009-05-28
> **Fastio said:**
> What about that Puppy Linux? Been reading about it, seems good and fast! Opinions? Is it as noob friendly as it seems?

P.S. - I forgot to ask, my mom sometimes uses it to talk in MSN, she'll still be able to do it but by some other software, right?

I've used Puppy a few times, though not recently. As I recall it was blazingly fast and very easy to use. It also looked like it belonged in the '90s, but that's fine.

As I recall, it asked a series of questions about your hardware and setup before it let you use it. The questions were well written and, as long as you take the time to read them, easy to answer. Perhaps these days they do more auto-detection?

In any case, I didn't stick with Puppy because I'm addicted to Debian-style package management. But that's just me.

Like another poster said... if you have the time, try a few. They're free, after all!

---

### Post by decoherence on 2009-05-28
> **cb951303 said:**
> anything with XFCE in it is not my optimal system :) I just wanted to point out the fact that I tried Xubuntu on better systems than OP's laptop and it was unbearably slow

I hear ya! Is it just me or did XFCE used to be way faster? I remember it kicking butt on a 400MHz Celeron laptop back when I was running Debian, about four years ago. Now, Xubuntu seems pokey on my 700MHz PIII. Not sure if that's a "new xfce vs. old xcfe" thing or a "debian vs. ubuntu" thing (my debian/xfce setup was certainly more 'bare-bones' then the stock Xubuntu setup.) Hardly scientific, I know!

Anyway, I guess I gone off topic. Bad me!! We now return you to your regularly scheduled thread. :D

---

### Post by raymondh on 2009-05-28
try crunchbang .. which is ubuntu-based

---

### Post by oldos2er on 2009-05-28
There's a lot of Gnome in Xubuntu's xfce, which makes it heavier than it should be. I personally prefer Vector Linux standard's xfce, which is cleaner and faster than Xubuntu's.

---

### Post by timzak on 2009-05-28
I have a 650Mhz laptop with 384MB ram and it runs the regular Ubuntu Gnome desktop just fine.  I use 8.04 (Hardy Heron) and I went through Services and Autostarted Apps and disabled everything except the bare minimum.  I don't run Desktop Effects, and I keep a vanilla Gnome desktop theme with no wallpaper to minimize memory consumption.  OS memory footprint is around 90-100 MB on this particular machine, which is not much more than I could achieve with Xubuntu.  For me, it runs fine.  It's slow for playing Flash content, and you can't have more than two apps open at a time, but it works.  You might have a hard time installing Ubuntu with Gnome with only 256MB, but if you can, you'll appreciate the better features over Xubuntu, with little to no performance penalty.  Just keep your expectations in check.

You could try Crunchbang as others have mentioned.  It's got a steeper learning curve, though, due to Openbox Window Manager, which if you're a newb, might not be acceptable.  It is definitely a better choice, though if you want a good combination of performance and features.

---

### Post by aysiu on 2009-05-28
Older versions do not run faster than newer versions.

If you want speed, actually, Ubuntu 9.04 is faster than any other release of Ubuntu that I've seen (and I've been using Ubuntu since 5.04).

Xubuntu uses a desktop environment (think: user interface) that's lighter than Ubuntu's Gnome desktop environment or Kubuntu's KDE desktop environment. You can go lighter still by using a window manager instead of a desktop environment. I'd recommend IceWM:
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

---

### Post by Zimmer on 2009-05-28
It might be a good idea to get the Alternate Install iso of whichever version you choose. The text based installer may play happier with your 256mb of RAM.

---

### Post by LEO_Servers on 2009-05-28
So the answer is probly yes but all most all your ram is going to be taken up all ready you may want to try a disto thats not as hardware intensive like dsL or puppy linux  :p

---

### Post by irv on 2009-05-28
Now that I am back home, I looked through all my burned CD's and DVD, and found I have installed the following:
DSL
Puppy Linux
Xubuntu many version
Kubuntu many version
Slackware
CrunchBangLinux
Arch Linux
gos
Ubuntu many version
At one time I use Red Hat, Mandrak, Suse, and about a half dozen more.

Like I said you can have fun trying all of them.
If you do a google search for small Linux OS's you will find many out there.
Two good sites to check out are:
[http://distrowatch.com/]("http://distrowatch.com/")

[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions")


As far as MSN Messenger goes, you can use Pidgin Internet Messenger.  It handles them all.

---

### Post by Fastio on 2009-05-28
Well, i tried the Live Cd of Xubuntu 8.04.1 (Hardy Heron) and things didn't go so well - very slow, mouse cursor very choppy, didn't recognize my wireless card and resolution was only half the screen.

I'm guessing it's slow because i'm reading it directly from the cd drive and i probably need drivers for a better resolution and wireless card.

Maybe i should try and install the latest Xubuntu version then? What's the worst that can happen? Explode my already dying ancient laptop? ehehe

I've been looking at Puppy manual and you can only install it in a partition? I don't really like partitions, i would rather have only one OS. 

Anyway, maybe Ubuntu latest version and if that doesn't work, one of those more light versions? Going to give another go at the Live CD, maybe i did something wrong!

Edit: I'm going to try Puppy first, curious about it!

---

### Post by irv on 2009-05-28
> **Fastio said:**
> Well, i tried the Live Cd of Xubuntu 8.04.1 (Hardy Heron) and things didn't go so well - very slow, mouse cursor very choppy, didn't recognize my wireless card and resolution was only half the screen.

I'm guessing it's slow because i'm reading it directly from the cd drive and i probably need drivers for a better resolution and wireless card.

Maybe i should try and install the latest Xubuntu version then? What's the worst that can happen? Explode my already dying ancient laptop? ehehe

I've been looking at Puppy manual and you can only install it in a partition? I don't really like partitions, i would rather have only one OS. 

Anyway, maybe Ubuntu latest version and if that doesn't work, one of those more light versions? Going to give another go at the Live CD, maybe i did something wrong!

Edit: I'm going to try Puppy first, curious about it!
Yes, it would be very slow running off the CD because if you laptop is old it would have a slow CD ROM.
The partitions is what happen when you prepare a hard drive for loading an OS. That's what all installs do.
Trying Puppy is a good idea.

---

### Post by mkvnmtr on 2009-05-28
I hate to suggest spending money but for 20 dollars American you can have enough ram to run Ubuntu with all the bells and whistles. It is easy to put in. Google will give you instructions for your unit.

---

### Post by irv on 2009-05-28
All of a sudden the light came on! I remember when I install gOS it was on an old machine and it booted very very fast, and was very small and looked great also.
I have a couple of old PC's in my store room and I think I will install it on them and give them away. It is a great way to get rid of old PC's without paying to do so. And it is also a good way to recycle them.

---

### Post by Fastio on 2009-05-28
> **irv said:**
> All of a sudden the light came on! I remember when I install gOS it was on an old machine and it booted very very fast, and was very small and looked great also.
I have a couple of old PC's in my store room and I think I will install it on them and give them away. It is a great way to get rid of old PC's without paying to do so. And it is also a good way to recycle them.

This one? [http://www.thinkgos.com/gos/index.html](http://www.thinkgos.com/gos/index.html)

Looks kind of heavy, no?

---

### Post by irv on 2009-05-28
> **Fastio said:**
> This one? [http://www.thinkgos.com/gos/index.html](http://www.thinkgos.com/gos/index.html)

Looks kind of heavy, no?

That's the one.
edit: No, as I remember it was a fast install and ran fast and booted fast.

---

### Post by Fastio on 2009-05-30
Ok, Puppy is the winner!

Runs very fast and i was able to detect my wireless card easily with the network wizard! I'm actually writing this in the laptop using it :)

Now that the OS is choosen, i would like to ask a few questions:

1 - Do i always have to create a partition to install it, even if i want to replace Windows? I can't understand this very well, sorry :( Read a bunch of tutorials but they all seem different! If someone could teach me or point me to a tutorial where i can learn how to install it properly, i would appreciate it! 
Edit: Found this one on the puppy forums, exactly what i want, i believe :)
[http://www.murga-linux.com/puppy/viewtopic.php?t=42876](http://www.murga-linux.com/puppy/viewtopic.php?t=42876)


2 - If i completely replace windows, will i have problems recognizing my wireless card or it worked so well cause Puppy has its own drivers?

3 - Is this seamonkey browser safe for stuff like online banking? I still have to researche about safety in Linux, though i always hear they're much safer than Windows but still, online banking is a thing i usually do on this laptop.

I think that this is it for now, really looking forward to install and fully explore it. Thanks!

---

### Post by irv on 2009-05-30
Maybe this link will help you:

[http://www.puppylinux.org/manuals/puppy-40/english/how-install-puppy/full-installation]("http://www.puppylinux.org/manuals/puppy-40/english/how-install-puppy/full-installation")

I use Linux for most of my everyday stuff. But I have to keep one machine around running Window because I need it for my online Banking and I use Quicken Bill Pay so I am still using Quicken. I can import my bank statements directly. Also Netflix does not support Linux so I can't watch movies without Windows.

---

### Post by Fastio on 2009-05-30
First, thank you all for your help, specially to Irv for the good advices and support!

So i have it up and running and its exactly what i wanted, much faster than with XP!

Now, my main concern is the browser! I was wondering, can i install something like Google Chrome or Firefox? I never heard about this Seamonkey before and i'm also having problems updating it to the latest version - i install it but then when i open it, it's always the 1.15 version!

Regarding online banking, it's all web based, just check account, do transfers, don't need an extra software, so i'm guessing Seamonkey would be fine? Anyway, if i can't install another browser, i must try and find out what i'm doing wrong for not being able to update this version of Seamonkey (1.15).

Puppy looks easy enough to use, apart from the single click to open stuff which might need time to get used to ehehe Also need to clear the desktop a bit more, cause there are too many icons and my parents also use this laptop and might confuse them a bit....more than they're already going to be when they see it's not Windows anymore ;)

---

### Post by irv on 2009-05-30
> **Fastio said:**
> First, thank you all for your help, specially to Irv for the good advices and support!

So i have it up and running and its exactly what i wanted, much faster than with XP!

Now, my main concern is the browser! I was wondering, can i install something like Google Chrome or Firefox? I never heard about this Seamonkey before and i'm also having problems updating it to the latest version - i install it but then when i open it, it's always the 1.15 version!

Regarding online banking, it's all web based, just check account, do transfers, don't need an extra software, so i'm guessing Seamonkey would be fine? Anyway, if i can't install another browser, i must try and find out what i'm doing wrong for not being able to update this version of Seamonkey (1.15).

Puppy looks easy enough to use, apart from the single click to open stuff which might need time to get used to ehehe Also need to clear the desktop a bit more, cause there are too many icons and my parents also use this laptop and might confuse them a bit....more than they're already going to be when they see it's not Windows anymore ;)

I would look into installing Firefox. It is well supported and easy to use.
As far as cleaning up the Desktop What I do is just make a folder on the desktop and put all my icons in there. That way all you have is one folder on the desktop and it is still very handy to get at when you need it.
Here is a screen shot of my desktop and you will see what I mean.
[ATTACH]115769[/ATTACH]

---

### Post by spcwingo on 2009-05-30
> **Fastio said:**
> Now, my main concern is the browser! I was wondering, can i install something like Google Chrome or Firefox? I never heard about this Seamonkey before

Seamonkey is made by Mozilla (the same people that make Firefox), so there's no need to install Firefox.  For the most part Firefox extensions and plugins will also work with Seamonkey.  You can read up on Seamonkey here:

[http://www.seamonkey-project.org/]("http://www.seamonkey-project.org/")

---

### Post by timzak on 2009-05-30
> **irv said:**
> I would look into installing Firefox. It is well supported and easy to use.
As far as cleaning up the Desktop What I do is just make a folder on the desktop and put all my icons in there. That way all you have is one folder on the desktop and it is still very handy to get at when you need it.
Here is a screen shot of my desktop and you will see what I mean.
[ATTACH]115769[/ATTACH]

Hey irv,

Can you tell me the name of that icon set you're using?  Looks great!

---

### Post by fluxlizard on 2009-05-30
skip anything ubuntu related- it will be too slow.
I have a laptop with very similar specs- an old ibm thinkpad a21m with 700mhz cpu 256 mb ram, 4mb video card, and I've tried all kinds of distros (and do so about once a year) to find the best to run on it.

PCLinuxOS gnome edition will make you very happy I think- it sure does me. My old laptop operates very nimbly with it and quick. It's not a stripped down OS (crunchbang), or a hacked OS that doesn't look and act like normal linux, limiting packages available and how you can operate it (puppy linux or dsl), or a limited desktop (xubuntu, zenwalk). You can try all those too and compare.

But PCLinuxOS gnome will run fine on your specs, and it's a fully functional and up to date gnome like ubuntu, uses synaptic package manager like ubuntu with thousands of packages and apps like ubuntu- though maybe not so many obscure ones as ubuntu, it still has all the big ones and unlike puppy still has hundreds and hundreds of more obscure ones.

It's easy to set up, it's easy to run, and for older hardware with 256mb ram it can't be beat. You can still enjoy a fast and fully functional and up to date firefox, open office, gimp, etc, etc, etc.

---

### Post by LEO_Servers on 2009-05-30
> **Fastio said:**
> 
 
I'm guessing it's slow because i'm reading it directly from the cd drive and i probably need drivers for a better resolution and wireless card.

 
Evrthing on the distro is loaded into ram no matter if it is a live disk or on the hard drive.

---

### Post by fluxlizard on 2009-05-30
> Evrthing on the distro is loaded into ram no matter if it is a live disk or on the hard drive. 

that's not really correct.
it will load as much as it can into ram and use the disk access for the rest. Especially if you do a true hard drive install... I'm pretty sure frugal install even puts your extra packages on disk and not in ram too, and on machines without a lot of ram running off the cd, it seems to access the disk when I click on apps.

Puppy is weird linux though- it doesn't work like normal linux. Everything is root, it uses ram strangely (normally if you have enough ram, everything runs out of ram to speed things up). Lots of the apps you might want are maintained by random users and not always kept up to date... It can be fun to play with though...

PCLinuxOS is normal linux, easy to use, kept up to date and will run on the OPs hardware.

---

### Post by LEO_Servers on 2009-05-31
ok not every application is loaded into the ram but all running apps and also the operating system. 

long story short 

"The boot loader loads both the kernel and the initramfs into memory and starts the kernel. The kernel then unpacks the initramfs and mount it as initial root filesystem, and then looks for the init program within the initial filesystem, and once it finds it, it executes it and hand the boot process over to it. This init scirpt is responsible for finding the real root filesystem and mounting it. It is also responsible for any special preparations required at boot time. "

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

you can get away with putting the kernel in ram and running in command line for great results but the  x-interface needs a little more memory to run properly

I believe windows xp 64 MB minimum supported requirement is easy enough to say just because you can doesn't mean you should.

all that i m saying is use the right distro for the right job

---

### Post by Fastio on 2009-05-31
Well, that PCLinuxOS looks good since it has firefox and open office and looks very light but i think i'm going to stay with Puppy for now. It's running great and i'm able to move around in it with ease. Maybe when i'm more experienced i'll try PCLinux but for now i think i'm going to do my learning experience in Puppy :D

My only concern was browser security but i've test seamonkey in a safety testing site and it's all good - anyway, i only use that laptop to check emails, bank account, read the newspaper and see some online videos from time to time. I was mostly worried cause of my dad, since he's not very experienced with computers but for browsing it's really simple and safe to use!

Thank you all for the help and suggestions!

---

