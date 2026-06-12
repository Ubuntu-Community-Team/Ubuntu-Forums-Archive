---
title: "N For Novice"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by richie1913 on 2009-06-15
I have just ordered myself a copy of Ubuntu to use on my spare computer as I am sick to the back teeth of windows.I will be using It on my spare computer till I get used to It then I will be putting It onto my main computer,but I am a complete beginner In this area,I have used windows since I was In nappies,so I would like to ask a few basic questions,forgive me If they are way of mark.
1.I use usb dongles for my Internet connection will they still work
2.Will any of my programs still work,like Avira anti-virus or online armour.
3.Have you got any do not ever do this advice
Thanks Richard

---

### Post by SuperSonic4 on 2009-06-15
1. Depends on your hardware - test it out with a live CD to be more sure

2. Unlikely. It's considered that Ubuntu and Linux in general don't need protection from anti-malware software. Some simply won't work, some may requite tinkering, some will run under wine, some have linux versions (like firefox/skype) but in nearly all cases there is open source software that works :)

3. Do not run any commands you don't know - especially ```
sudo rm -rf /
```

---

### Post by richie1913 on 2009-06-15
Thanks,when the C.D. arrives I will try It out,I just know I am going to get stuck but I know where to come for help,I can't believe how many members there are on this forum.A great pool of knowledge just waiting for me to tap Into(and I will need to do that alot me thinks)

---

### Post by jperez on 2009-06-15
Welcome to the Ubuntu Linux community, one of the many Linux communities out there, but the only one to have cookies and pie in one sitting...or perhaps cake and tea.

2. A better explanation for that is because there are VERY few linux viruses out there and Windows viruses don't run in Linux systems, so there's no real need for protection at this point in time.  Still, as was already said, there are some that don't work at all, some that work in WINE (although that's a bit useless since they scan Windows folders and files, not Linux folders and files) and some that are made for Linux/OSS.

3. Do not try to follow guides to install/customize/etc. something for your system that are meant for advanced users as it may lead to a system crash, login failure, video corruption, sound failure and death due to head desk from said problems.

Other than that, if you want to customize the look and feel of your newly installed distro, head over to [www.gnome-look.org](www.gnome-look.org) for **Ubuntu**, [www.kde-look.org](www.kde-look.org) for **Kubuntu** and [www.xfce-look.org](www.xfce-look.org) for **Xubuntu**.  They have wallpapers, themes and add-ons that can help you get the look you might be looking for to really enjoy your system.

Use the "**Add/Remove..."** application to find software for your Ubuntu flavor.  If you want a more detailed approach or once you really like getting into the system a bit more, use "**Synaptic**" instead.

Follow guides here to help yourself find solutions to many problems.  If you find a bug that either has no solution or is still open, post it in the [Ubuntu Launchpad]("https://launchpad.net/ubuntu").

There many other things to do with Linux and searching the forums will help you do that.  If there's anything else I missed, others can contribute.  Anyway, great to see someone else trying it out for themselves!  Enjoy your stay!

Jesse~

---

### Post by richie1913 on 2009-06-15
Thanks for that,at the moment I am getting as much Info as I can so when I do Install,It wont be so daunting,I am looking forward to the challenge and of course learning something new.

---

### Post by QIII on 2009-06-15
Welcome to Linux and Ubuntu.

Just a tidbit to add to everyone's wonderful advice.

Many who make the switch from Windows encounter a little bit of "culture shock".  Don't be overwhelmed.  Expect your experience to be far removed from your previous experience from Windows.

You may find that your impression is that something just seems "odd" or "wrong".  

Don't think of it in those terms.  You are learning a new "language".  The vocabulary and syntax will be different.  But that is no more "wrong" than when you try to learn German if you are an English speaker.

German is different from English.  Linux is different from Windows.  But that's the fun!

---

### Post by guyminuslife on 2009-06-15
On number two, just a heads up if you're new---you don't install programs in Linux the same way that you do in Windows. It's much simpler, actually. Pretty much every program you'll need to use (unless you're running Windows apps in Wine) is in the repositories. You can search through this in Synaptic Package Manager, or a subset of it in Add/Remove Programs. Or, you can use the command line, like:

$ sudo apt-get install <some_program>

That blew my mind when I first switched. And knowing it beforehand would have saved me hours of, "Where are the prograaaaams?"

---

### Post by Abu_Dayya on 2009-06-15
Yes, repositories in linux are fantastic. you don't have to go to websites to download and install software. Almost all programs are in 'Repositories'. When you install ubuntu on your computer and figure out how to connect to the internet (its not hard at all by the way), you go to 'Software Sources' from the Systems -> Admin menu, choose the repositories you want, and let ubuntu reloads software header files and information. Then any peice of software can be downloaded and automatically installed through System -> Admin -> Synaptic menu.

There are other ways to install software in linux, but first use this approach untill you're comfortable enough to do the alternatives

---

### Post by lisati on 2009-06-15
Don't be put off when things seem confusing: some things will be the same or similar (e.g. the basics of "point-and-click").

While you're finding your way around and learning how to do things, you might find the following interesting: [https://help.ubuntu.com/9.04/switching/applications-equivalents.html](https://help.ubuntu.com/9.04/switching/applications-equivalents.html)

And don't be scared to ask questions: there's no such thing as a "dumb" question unless it remains unasked.

---

### Post by pous on 2009-06-15
> **QIII said:**
> Many who make the switch from Windows encounter a little bit of "culture shock".  Don't be overwhelmed.  Expect your experience to be far removed from your previous experience from Windows.

You may find that your impression is that something just seems "odd" or "wrong".  


i felt the same the instant i had ubuntu running(last week) something was wrong very worng.... they call it windows ;) ....

i'm a first time user of linux and all i can suggest is if you dont know how to approach some issue there is the search function also dont doubt asking, this is a great forum!

---

### Post by freeman2000 on 2009-06-15
Download and read the Free Beginners Guide.  Here's the link.  good luck.

 [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by H2SO_four on 2009-06-15
Definately read everything you can about it.  Don't run commands that you are unsure of.  you can erase your whole computer with only a handfull of commands.

---

### Post by Chemical Imbalance on 2009-06-15
For another guide, check my sig.

Don't worry about Windows security programs like Avira and Online Armour.  They won't run on Linux and are not meant to...because you don't need them.  Ubuntu has its own firewall built in with no ports open by default.  
There are very few viruses for Linux and they are only proof on concept and not worth worrying about at this time.

Repositories are stores of programs housed by Canonical and are officially supported and security checked.  No need to go browsing for apps from your browser except under certain circumstances.

Have fun!

---

### Post by richie1913 on 2009-06-16
Thank-you all for your wonderful advice,just finished work so I am going to sit back and read the beginners guide before the kids finish school.

---

### Post by 3rdalbum on 2009-06-16
My advice would be:

1. Take things at your pace. You don't absolutely need to get every one of your peripherals working in the first day. If there's something you don't understand, it's okay to wait a while and do a bit of reading so you do understand.

2. After you install Ubuntu, go to the Medibuntu website and add their repository (they have a "howto"). Then you can easily install DVD playback, Flash, Skype, Google Earth, restricted formats etc from the Synaptic Package Manager.

3. Don't get obsessed with Compiz effects - they're nice, but they're only the icing on the Linux cake. Be careful with what settings you change and what checkboxes you turn off with Compiz. It's possible to turn off the ability to move or resize windows in CompizConfig Settings Manager, so make sure you DON'T turn off those features!

4. If it's getting frustrating, ask for help. If it's still frustrating, sleep on it - go for a walk or something to clear your head, or literally call it a day and approach the problem again in the morning. While you are asleep, your brain does actually try and work on unresolved problems from the day; take advantage of this feature of your mind!

Linux isn't hard, but it's radically different to Windows.

---

### Post by richie1913 on 2009-07-01
Hello again everybody,you will all be pleased to hear that I received my Ubuntu 9.04 Disc today,I have yet to Install It as I have been playing around on it using the demo option,first Impressions are amazement.I was always told that windows good linux or ubuntu bad,linux Is slow and complicated etc etc...Well now that I have actually tried It for myself I am very pleasantly surprised,I really was not expecting menus and windows,(I always had a picture of a blank screen with just a flashing cursor blinking at you),so that part of Ubuntu I found pretty easy to use saying that,I now need help as I cant get my Internet to work.I use a usb dongle from 3 on payg also got a vodafone one but 3 is slightly better so use that the most,If I plug the dongle in nothing happens(the software and drivers are on the dongle for windows and mac osx10.4.11/10.5.2 If thats any help) so I have created the network connection manually but cant find any way of actually telling it to connect.So I was hoping If there was anyone out there that could help me out.Just for Information I am going offline now and wont be able to get back untill I finish work tomorrow afternoon so wont be able to reply to any help till then.Thankyou all very much and speak to you all again soon.
Richard
P.s. What would be the best way to reformat the hard drive before putting Ubuntu on,I was going to use D-Ban to totally wipe It,what do you think.

---

### Post by pous on 2009-07-09
about internet, i dont know if this might help, but in my laptop i had some issues with my wireless after getting ubuntu, internet only worked via ethernet untill i found i had to turn on the drivers in **system->administration->hardware drivers** hope you find it usefull... good luck

---

### Post by richie1913 on 2009-07-09
Hi pous,I eventually got everything working as It should and am very Impressed by Ubuntu,totally different from what I expected,very steep learning curve though.Thanks .

---

### Post by 3rdalbum on 2009-07-09
> **richie1913 said:**
> Hi pous,I eventually got everything working as It should and am very Impressed by Ubuntu,totally different from what I expected,very steep learning curve though.Thanks .

I'm glad you got everything working and that you like Ubuntu!

I'd have to disagree about it being a steep learning curve; on the whole Ubuntu is as easy as Windows, but it's so incredibly different. Total novices tend to pick up Ubuntu without much fuss, because they don't have a decade worth of assumptions about how their computer should behave.

But yeah, in particular I'm glad you took my advice about sticking with it :-)

---

### Post by Paddy Landau on 2009-07-09
> **richie1913 said:**
> 2.Will any of my programs still work,like Avira anti-virus or online armour.
On Windows, enable your firewall, antivirus and antimalware. Then [test your computer on GRC]("http://www.grc.com/") (click on the "Shields Up" icon; scroll down to "Hot Spots"; click on "ShieldsUP!"; follow the instructions).

Then, go to Ubuntu without any antivirus or antimalware, just with the default firewall, and test your computer again. I had a really pleasant surprise.

By the way, AFAIK, the only way to get a virus on Linux is to install it. The only way to install it is to have someone fool you into installing one. A little common sense and care should take care of that.

> **3rdalbum said:**
> 2. After you install Ubuntu, go to the Medibuntu website...
[Medibuntu instructions]("https://help.ubuntu.com/community/Medibuntu")

> **3rdalbum said:**
> Linux isn't hard, but it's radically different to Windows.
[Linux isn't Windows]("http://linux.oneandoneis2.org/LNW.htm")

> **richie1913 said:**
> What would be the best way to reformat the hard drive before putting Ubuntu on
The installation disk will take care of that for you. Just choose the option to use the entire drive. WARNING: That option will ERASE everything on the drive, so only do it if you're absolutely sure you have nothing you need on that drive.

---

### Post by 3rdalbum on 2009-07-09
> **Paddy Landau said:**
> Then, go to Ubuntu without any antivirus or antimalware, just with the default firewall

If you think that's cool, I'll probably blow your mind by telling you that the "default firewall" is not even turned on - it lets all packets through to anything that's listening. By default, nothing is listening.

---

