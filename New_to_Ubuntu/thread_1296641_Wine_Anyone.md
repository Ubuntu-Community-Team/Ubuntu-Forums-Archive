---
title: "Wine Anyone?"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Niko Johnson on 2009-10-20
So as i was doing my daily reading of the threads, i noticed a lot about using WINE. however every thread involving wine seemed to be an error or a dissapointment. now i dont really have any need for WINE but it looks like something that would be nice to have ( if it didnt have so much bugs in it) i was just wondering what all of you think. is wine worth the troubles.. do you use it without problems... are the problems easy to fix, do the have a good support team... should i use WINE or just reboot into winblows?

---

### Post by Bachstelze on 2009-10-20
WINE support is often not perfect, but it could be good enough for you. My advie is try it for yourself and see if you like it. I personally use WINE for µTorrent, Perfect Dark (japanese P2P, not the N64 game :p) and Photoshop 7, and it works pretty well (well enough for me, at least).

---

### Post by Niko Johnson on 2009-10-20
I Think im going to do that... i just wanted to get some second opinions, i heard one guy that was using wine and it froze up on him, He had to format all his partitions and reinstall linux... i dont want to end up like him!!!

---

### Post by Mike_IronFist on 2009-10-20
> **Niko Johnson said:**
> So as i was doing my daily reading of the threads, i noticed a lot about using WINE. however every thread involving wine seemed to be an error or a dissapointment. now i dont really have any need for WINE but it looks like something that would be nice to have ( if it didnt have so much bugs in it) i was just wondering what all of you think. is wine worth the troubles.. do you use it without problems... are the problems easy to fix, do the have a good support team... should i use WINE or just reboot into winblows?

It depends on what you're trying to do with Wine. Some programs work awesome under wine, others don't. Experiment yourself, and also refer to Wine's excellent App Database (AppDB for short) for more info:
[http://appdb.winehq.org/]("http://appdb.winehq.org/")

By the way, just in case you run into really picky folks, remember it's spelled with one capital letter and the rest lower case ("Wine") rather than all capitalized letters ("WINE"). This is because the makers of Wine don't want internet users to come across as "shouting" when discussing it.

---

### Post by Bachstelze on 2009-10-20
> **Niko Johnson said:**
> I Think im going to do that... i just wanted to get some second opinions, i heard one guy that was using wine and it froze up on him, He had to format all his partitions and reinstall linux... i dont want to end up like him!!!

That's pretty extreme, and I honestly don't think the problem was so serious that formatting was the only way out.

---

### Post by yeats on 2009-10-20
Wine is one of those things that is *awesome* when it works and sometimes just flat out doesn't work (or takes a great deal of shoehorning of programs to work).  I only use wine for occasional things... generally I'm satisfied with the native Linux apps.

---

### Post by Niko Johnson on 2009-10-20
You might be right, but i just saw way to many people have weird problems with it. it made it seem like Wine is a reinstall waiting to happen

---

### Post by Mike_IronFist on 2009-10-20
> **Niko Johnson said:**
> You might be right, but i just saw way to many people have weird problems with it. it made it seem like Wine is a reinstall waiting to happen

Remember, **this is a help forum**. This is where Ubuntu users go when things go wrong, **not** when things go right, although there are sections here for more positive discussion.

The way I think of it is, this is like a hospital - you can expect to see people with problems from moderate to severe around here.

Most of the time, things **do** go right, however. Trying new things in the Linux world is highly encouraged.

---

### Post by Niko Johnson on 2009-10-20
i just wanted to get an overall opinion with the Ubuntu forum community

---

### Post by 3rdalbum on 2009-10-20
It's useful to have sitting around; it can sometimes get you out of a tight spot. Wine can't completely mess up your system; you should only run it as your normal user account, and your normal user account can't do sufficient damage to your system to stop it from booting.

---

### Post by kostkon on 2009-10-20
*Spotify* runs perfectly under *Wine*, if you're interested.

---

### Post by Cope57 on 2009-10-20
Wine is good for those that do not want to use open source alternatives, and are devoted to proprietary software.  Or, there is some software that the individual already purchased, and cannot live without.

Wine, I tried it once to see if I could get a Windows application to work.  It did somewhat, but found an alternative for Microsoft Office, so Wine is no longer needed for me.

---

### Post by ikt on 2009-10-20
completely useless in my opinion, I've tried various programs with it including diablo 2 and they just didn't work.. I've found virtualbox is the answer to my multi-os needs.

---

### Post by UndefinedMind on 2009-10-20
I've had a few programs actually tell me that the program was not able to be ran under a virtual desktop. The programs that did work, worked perfectly.

[quote=chrissharp123]Wine is one of those things that is *awesome* when it works and sometimes just flat out doesn't work (or takes a great deal of shoehorning of programs to work). I only use wine for occasional things... generally I'm satisfied with the native Linux apps.[/quote]

---

### Post by nevets04 on 2009-10-20
I have never successfully ransomething in wine, maybe I'm just doing something wrong.

---

### Post by PhilGil on 2009-10-20
I have a couple of programs I use frequently that function very well in Wine.  One is Photoshop Elements 2 - there's one plug-in I really like that I can't get working in Gimp.  The other is a program called Pixort - it's a simple, lightweight and very fast photo comparison program that has no Linux equivalent.

---

### Post by flyerbrooks on 2009-10-20
I had limited success with Wine also. It either works for you or it doesn,t. Hence my need to keep a small xp partition for the games that i use. Also found it to be painfully slow.

---

### Post by bwang on 2009-10-20
For me, Wine often works beautifully and is also often complete garbage. .NET programs don't seem to like it very much.

---

### Post by JoshuaRL on 2009-10-21
> **Niko Johnson said:**
> You might be right, but i just saw way to many people have weird problems with it. it made it seem like Wine is a reinstall waiting to happen

Wine can't make things unbootable, I really can't see how that would happen.  At very most, you're merely a
```
sudo aptitude remove wine
rm -rf ~/.wine

```
away from no problem.  Even most viruses can't run properly on Wine.

But in the end, it is what it is.  You're trying to run a Windows application in a mostly reverse-engineered compatibility layer for Linux.

What I use it for works perfectly.  But that's circular reasoning, as I wouldn't use it for things it doesn't do well.  Check [the WineHQ Application Database for info](http://appdb.winehq.org/) and give it a go.

---

### Post by Niko Johnson on 2009-10-21
Cool thanks for all the replys guys... but i think i came to a conclusion and im just going to stick with my good old open source software. i dont really have any need for wine as long as the GPL is still around. ill just boot into winblows if i have to

---

### Post by NightwishFan on 2009-10-21
I prefer Wine over Windows. It is free of any Microsoft code. I can still run my proprietary applications on an open source kernel. I consider that sufficient.

---

### Post by John Bean on 2009-10-21
Invaluable for me, it allowed me to avoid booting XP just to run Photoshop CS2 which for my purposes can't be replaced by anything Open Source at this point in time. After a bit of trial and error I have it running just as well under Wine as it ever did under XP on the same hardware. It wasn't simple or straightforward to get to this point though.

Maybe one day Gimp will get around to supporting 16-bit images and adjustment layers but I'm not holding my breath. In the meantime Adobe already got my money back when I bought CS2 so it's nice to be able to continue using it alongside other excellent Open Source photographic tools I now use instead of their (often expensive) Windows counterparts I've used over the years.

---

### Post by Mark Phelps on 2009-10-21
My own experience with Wine is what others have already said -- it's success is very specific to the particular application you need to use. In my case, I tried several different MS Windows apps, ranging from huge (Office) to small (utilities) and in ALL cases, was unable to get a useful level of functionality.

In the end, did what others have done as well:
1) Retained dual-boot with MS Windows for those apps that I need and won't work under Wine
2) Learned to use native Linux apps for the rest.

So, before you install Wine, as mentioned early on in this thread, check out the CodeWeavers Application Compatibility database site for the applications you want to run.  If they're all rated Platinum or Gold, you're good go to;  if they're rated Garbage or no rating is found, you're most probably wasting your time with Wine.

---

### Post by Niko Johnson on 2009-10-21
alright sounds good. ill check it out

---

### Post by anewguy on 2009-10-21
Just my 2-cents worth:

I use Wine only for a couple of apps myself:  Family Tree Maker and MSWord from Office 2007.

As already mentioned many times, your success with Wine depends on the application, and searching the already mentioned lists can give you a good idea for a specific application.  Also, sometimes it might be necessary to install a newer version of Wine from Winehq than that delivered in Ubuntu.

I try to remember a couple of things - (1) it's free, (2) someone is trying to find ways to duplicate what Microsoft does with it's Windows internals without actually using anything from Microsoft, and that is a terribly huge task.  It will never be perfect, but they sure have done a good job so far!

As far as doing something with Wine that messes up your system so much you have to reinstall, using normal applications won't result in that.  If someone is messing around with lower-level Windows/DOS things in an application that uses Wine, well...they deserve what they get.  Don't let a fear of something like that happening scare you away from Wine unless of course you are one of those people.

Wine has it's place - particularly if you have an app written for Windows but don't have Windows or a Windows disk (like me).  There are other options as well - dual-booting with Windows, or for me it would be using a virtual machine to run Windows inside of Linux.  VirtualBox and VMWare are just a couple that come to mind - of course you still need a Windows disk so you can install Windows in the virtual machine.

Dave :)

---

### Post by arvevans on 2009-10-21
The nature of a support forum is that what you see is mostly from those who have problems, or think they might have problems.  It is relatively rare for someone to state on the forum that everything works fine for them.  This then leads to most forum lurkers getting a feeling that something might be bad or unreliable, when the real situation is that a great many people are using it, and this raises the number of problem reports, when the percentage of users having problems might be less than for other programs which you never hear about because nobody is using them.

Wine is great.  WINE IS GREAT!  I use it frequently with almost no problems.  Most problems I seem to encounter with wine is programs that also run poorly or slowly on Windows OS.  
_._

---

### Post by RedRat on 2009-10-21
I run several Windows programs under Wine, the most important for me is ThumbsPlus for cataloging and managing my picture files. In point of fact, ThumbsPlus runs faster under Wine than on my XP machine. Granted, you have to apply some tweaks but nothing impossible. I also use it for Newsrover and it works quite well. It also is a good way to run Winamp too.

---

### Post by durand on 2009-10-21
The vast majority of apps I've run with wine work perfectly. Wine cannot harm your system in any way that makes you need to reinstall. It could definitely affect your home folder and settings however, that only applies if you run a malicious program, and that would happen even if you didn't use wine. The only way you could actually screw up your ubuntu install would be by manually running the program with sudo or gksudo or as a root user.

---

### Post by Jazzy_Jeff on 2009-10-21
I use Wine to play World of Warcraft and it works flawlessly. I also use it for a couple of other programs and it works pretty good.

---

