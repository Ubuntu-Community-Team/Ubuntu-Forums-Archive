---
title: "Need IE in linux."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by Sugi on 2009-02-13
I am trying to get Internet Explorer in ubuntu, but my results are failing me.  I have tried IE6 through wine, but it rans my computer at 100% cpu and makes my mouse choppy.  I have to restart my computer, because it lags too much.  I'm currently using PlayOnLinux and I have looked into Firefox plugin for IE, but the offical one isn't support for linux yet.  And the other way is to run IE through wine, but like I said before my computer can't handle that.

Does anyone have any tips for getting IE running in Ubuntu?

Spec:
Ubuntu 8.10
Intel Celeron 1.60GHz
437 MB ram

Thank you,
Sugi




**MY FIX:**
 - First remove wine from your computer.  This wasn't an issue for me, because PlayOnLinux installed wine and I didn't have anything else installed that needs wine.
$ sudo apt-get remove wine

Next Install the deb file
[http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb](http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb)

Now load up IEs4Linux and bam. No 100% CPU after closing IE

NOTE:  I installed IEs4Linux pre deb file installation. Even when I removed wine, IEs4Linux was installed after removing wine and installing the script.

More information here:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895")

---

### Post by Dr Small on 2009-02-13
How about ie4linux?
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by Sugi on 2009-02-13
I just tried it out now.  It's working a little better then IE6 on Playonlinux, but when I close it, my computer is still at 100% cpu.  Does anyone know how to fix this?

Sugi

---

### Post by Old *ix Geek on 2009-02-14
WHY do you "need" IE?

Sorry, but this is one of my biggest pet peeves, so I just have to say this: You're using Linux.  IE is a piece of crap--a bloated, insecure, piece of crap.  If a site insists that you use IE to access it, *IT* must be crap, too!  You, as a Linux user, should not be expected to use a Micro$oft product--for ANY reason.  And you need to speak up and complain, as this is the ONLY way that we'll ever see the end of "IE only" sites (which, frankly, I thought had disappeared a long time ago, as I NEVER come across them any more).

---

### Post by DigiTan on 2009-02-14
> **Old *ix Geek said:**
> WHY do you "need" IE?

Don't be a pusher.  Any serious web developer is going to go strictly off what their client or boss needs at the time being, or start getting to know the unemployment office.  If you don't like it, I suggest taking it up with his supervisor or whatever the case may be.

Sugi, just curious, how recent is your ie4linux?  There's a bug in some versions where closing the window doesn't actually close the program.  You may have to manually kill the process.  ([http://ubuntuforums.org/showthread.php?t=835302](http://ubuntuforums.org/showthread.php?t=835302))

---

### Post by presence1960 on 2009-02-14
I am not sure by your post if you just want IE or need IE for certain websites because they will only allow you to view with IE. If the latter is the case you can install a firefox extension called User Agent Switcher. This allows you to choose between IE, netscape and opera. It "tricks" the website into believing you are using those browsers. I agree with Old *ix Geek but I wouldn't be so forceful about it. What he said about IE is true. I never used IE when I ran Windows. Why don't you try some alternative browsers in linux alongside your IE and then give it a fair trial? Firefox and swiftfox ( a lighter version of firefox) will blow IE away.

---

### Post by hyper_ch on 2009-02-14
if you truly need IE you might even want to look at virtualization. Installing a virtual windows will give you a native IE. A vanilly XP will be booted up quite quickly....

---

### Post by stalkingwolf on 2009-02-14
crossoverlinux is also an option.

Yes there are still some sites that are IE only. I use crucial.com for checking RAM compatibility and its scan tool only works in IE.  Where I worked, until recently their IP;s site only worked with Safari and IE.

---

### Post by Sugi on 2009-02-14
Actually, I needed IE for my girlfriend's laptop.  She needs it to view, edit and complete applications for jobs and such.  She's trying to get a second job :p

I, myself is a opera convert and have been for... well I don't know how long to tell you the truth.  But Even back in the window's day I was using Opera.  

Old *ix Geek, I am a little insulted to tell you the truth.  Don't be so quick to judge.  I have already pointed out my reasons for not using IE above ^  You should try to apply for Best Buy.  You are not able to get past it, and Best Buy do not allow you to use a different OS then Windows.  But presence1960's idea "User Agent Switcher" might be the trick to sneak pass best buy's application rules.  Maybe.


hyper_ch, my girlfriend's laptop couldn't handle virtualization of XP, but I am aware of virtualization and currently using it for my artist needs :D

stalkingwolf, thanks for the advice.

I already did get IE working in Linux.  I found a script to fix the 100% CPU issue with IE, but flash is still kinda choppy for her.  I think it may be her hardware.


MY FIX:
 - First remove wine from your computer.  This wasn't an issue for me, because PlayOnLinux installed wine and I didn't have anything else installed that needs wine.
$ sudo apt-get remove wine

Next Install the deb file
[http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb](http://www.tolaris.com/apt/pool/main/w/wine/wine_1.0.0-2eitri1_i386.deb)

Now load up IEs4Linux and bam. No 100% CPU after closing IE

NOTE:  I installed IEs4Linux pre deb file installation. Even when I removed wine, IEs4Linux was installed after removing wine and installing the script.

More information here:
[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/205895")

Enjoy boys and girls,
Sugi


PS:  Sorry for the late reply, I was playing video games and lost track of time.

Playing videos games IN Ubuntu! :p (Old *ix Geek)

---

### Post by ieee488 on 2009-02-14
> **Sugi said:**
> Old *ix Geek, I am a little insulted to tell you the truth.  Don't be so quick to judge.  I have already pointed out my reasons for not using IE above ^  


Don't be too quick to do play the victim here. Had you explained **fully** your reasons in your initial question, which in you did **not** do, then we wouldn't have this situation. People cannot read you mind; only what you write.

---

### Post by Dr Small on 2009-02-14
> **ieee488 said:**
> Don't be too quick to do play the victim here. Had you explained **fully** your reasons in your initial question, which in you did **not** do, then we wouldn't have this situation. People cannot read you mind; only what you write.
As good honest CoC abiding citizens, we should not be jumping the gun with such conclusions to begin with.

---

### Post by Sugi on 2009-02-14
I do agree with Dr Small, but I understand where you are coming from, ieee488.  But at the end of the day, does it really matter if it was my girlfriend's computer or mine own computer?  No, I just had a question and I needed it answered.  Please remember, linxu is here to offer us chooses.  No matter which one I may want, IE or Firefox or Opera or even Chrome. (just to name a few :p)

I hope my thread will help at least one person struggling with IE in linux.

Good luck,
Sugi

---

### Post by Old *ix Geek on 2009-02-14
You did NOT fully explain your reasons in your original, **unedited** post.

I stand by my statements regarding IE, particularly the part about COMPLAINING to companies/sites that require its use.  Simply pointing out to them that it's the LEAST secure browser around, to say nothing of slow and featureless, should be sufficient!

Really, how can we, as Linux users, ever expect to be taken seriously if we DON'T complain to IE-only places?  I feel that it's our duty.

I realize [now] that I overlooked the possibility that web developers may need to check their code in IE, so for that I do apologize.  Everything else, though, I stand by.

---

### Post by ieee488 on 2009-02-14
> **Dr Small said:**
> As good honest CoC abiding citizens, we should not be jumping the gun with such conclusions to begin with.

To my mind, the OP was also guilty of "jumping the gun" for throwing a mini-tantrum about "being insulted". Is that the kind of game we want to play here?

There is more than enough "jumping the gun" to go around.

Just stick to the facts and all the facts and everything will work out better.

---

### Post by Captain Legless on 2009-02-20
Thanks for the information in this thread.
As a disabled computer user I use an online shopping facility.

Unfortunately the webmasters for the site seem not to make it Firefox friendly under Linux or Windoz. Had it not been for the information given in this thread - sparked by a user with who obviously had a similar problem to mine, I, ( a new Linux user), would have had to resort to booting in Windoz to use IE and access the site, as it is I can continue to use Linux and simulate using IE.

I think the mini tantrum throw by "Old *ix Geek" was completly unwarranted and I for one am pleased that the original poster started the thread, as I said, it stopped me from going back into Windoz!!

---

### Post by Sugi on 2009-02-20
Your welcome.  I'm glad I could prove some helpful information for you.

Sugi

---

### Post by Volt9000 on 2009-04-06
I'm resurrecting an old thread, but felt like I had to throw my (¢)(¢) in.

First of all, I'm a very happy recent Linux convert. Even when I was in Windows I used either Firefox or Chrome, never IE-- unless I HAD to.

And yes, unfortunately there are sites out there that DO REQUIRE IE, because they WILL NOT work on other browsers.

One such site is the CRA's website, the Canadian Revenue Agency, which is an official Canadian Government Website. Pretty damn stupid, I think, for a government website to claim that you MUST use Internet Explorer. Trying with any other browser will just give you the error that you can't continue unless you're using IE.

Granted I didn't try changing the user-agent. There's a good chance the site would have worked perfectly fine. However I think it's incredibly poor design to design a website that will work ONLY in a specific browser or a specific platform. That's just developer laziness.

Of course it could be due to the fact that a particular feature of the website only works because of a hack applicable only to IE-- again, developer laziness.

I understand that most of the business world uses IE anyways, but that's no excuse. A well-designed site should work in any browser on any platform.

As an aside, if I ever really need IE I just open VirtualBox which has Windows XP installed and run IE from there. A bit overkill, yes, but I do use it for other things as well. And besides, IE works perfectly in there. ;)

---

### Post by SeanBlader on 2009-04-07
I'm a web developer, and I look forward to the day that official support for Windows XP Service Pack 2 ends so that maybe I can convince my bosses to stop supporting IE6 for our web applications. Until then I post browser statistics outside my cubicle and I reluctantly make the effort to get the sites to look the same in 3 different versions of Bill's browser (which easily doubles the workload). Currently I have IE6 and 7 on two different office XP systems, but I may be needing to ditch IE6 so I can get Office 2007 on one. In which case I'd want to reluctantly run IE6 on my personal laptop under Jaunty so I can check my work during development.

As part of my hatred for IE6 and to a lesser degree IE7, I've worked out a plan to infiltrate the company who shall not be named, locate and blackmail some software update manager and force an update to go out that would repair the virus that is Internet Explorer automatically by replacing it with Mozilla or Webkit.

But in lieu of that, thanks for Sugi for posting how it worked for him, I might be looking into this.

---

### Post by karinchen on 2009-04-28
Hi everyone,

Has anyone found another way than virtualization in order to use IE > 7 from Ubuntu (8.10) ?
I have to test my web sites in both Firefox and IE, so I definitely need IE, though Firefox is my favorite.
Nevertheless, the Javascript debugger provided in IE8 is a nice feature as well.

Thank you,
k

---

### Post by LowSky on 2009-04-28
You could always install the Windows version of Firefox using Wine, I've use that to get around a few web annoyances that "require" Windows/Mac.

---

### Post by scheuri on 2009-04-28
> **hyper_ch said:**
> if you truly need IE you might even want to look at virtualization. Installing a virtual windows will give you a native IE. A vanilly XP will be booted up quite quickly....

I second that very very very much.
No matter what you do, but IE installed on linux (with whatever tool) will not react and behave the same as an installation of IE on Windows.

However, your specs are not very good for virtualisation.

---

### Post by karinchen on 2009-04-29
So I guess I'll stay with vm-ware. Thx everyone!

---

