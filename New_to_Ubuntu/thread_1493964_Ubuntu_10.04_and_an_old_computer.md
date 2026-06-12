---
title: "Ubuntu 10.04 and an old computer"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by mjrich1976 on 2010-05-26
I'm essentially new to Linux. I would like to learn more about it, and I am eager to do so. If this post is in the wrong place,  I apologize.

This is my first post. I apologize for not contributing responses first, but as I stated, I am essentially new to Linux and Ubuntu.

I recently upgraded an old computer I have to 10.04. I've run into a number of issues that I am hoping the good folks in this forum can help me resolve (if the issues can be resolved).

The computer I upgraded is an HP Pavilion XE813 that has 196 MB of RAM, a 40GB hard drive, and a 733 Celeron.

Initially the issues I had (or I am currently having) are as follows:

1. The install took a decent amount of time (from a CD), but the updates (84 after the initial install) took over **24 hours**. I am not exaggerating in any way.

2. I can't really log into Gnome. Failsafe Gnome allows me to log in, but at times is very sluggish. Based on what I've read, the GNOME issue has something to do with applets, I think. When I try to log into Gnome, I only get the wallpaper, no tool bars or menu bars. I'm not entirely sure what KDE is, either, but I tried logging into that with no success. I also tried doing a reinstall of the applets from the Package Manager, and that did not seem to help any.

3. Something, at times, just hammers my processor. Occasionally, the light will appear solid, it's flashing so fast, other times it will just flash very rapidly. In both cases, I am not even at the machine. And if I were, I couldn't do anything.

I think this machine is only capable of holding 256 MB of RAM. If I understand right, Lucid Lynx requires 512MB to run properly. Please correct me if I am wrong.

This is driving me crazy. If anyone has any advice at all, I would be very grateful. I'd like to get this machine running faster, if it's at all possible. I mean, as fast as is practical for the setup that I have. I don't expect it to be as fast as most newer computers.

I would really like to increase my knowledge and usage of Linux, and getting this machine working properly would be a great step in the right direction.

Advice?

---

### Post by philinux on 2010-05-26
@mjrich1976, you don't have enough ram to run ubuntu. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You may be better with Lubuntu or damn small linux or puppy linux.

[http://lubuntu.net/news](http://lubuntu.net/news)

---

### Post by cpplinux on 2010-05-26
Have you tried Xubuntu?

[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

Quote:
**Minimum system requirements**

 You need 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run the Live CD or 192 MB RAM  to install. The Alternate Install CD only requires you to have 64 MB RAM  at install time.
 To install Xubuntu, you need 2.0 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with starting from 192 (or even just  128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by Chuck- on 2010-05-26
[FONT=Arial][SIZE=4]I did a little search and it looks like the guy above has the right idea.
[/SIZE][/FONT][FONT=Arial][SIZE=4]
Your  HP Pavilion XE813 can have to up to a maximum  of  256 MB Memory RAM, which is correct. You said its upgraded to 196MB of ram. You need to take out the 68MB upgrade ram and install a 128MB. [/SIZE][/FONT][FONT=Arial][SIZE=4]The system has  2 sockets to install memory  already with  128 MB (removable) standard memory. So, if you buy 128 more you should have 256.


$11.00 for 128Mb upgrade
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=350295152276&rvr_id=&crlp=1_263602_263622&UA=WVF%3F&GUID=d569d8c51280a0aad1e48fd4ffcf0aa6&itemid=350295152276&ff4=263602_263622]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=350295152276&rvr_id=&crlp=1_263602_263622&UA=WVF%3F&GUID=d569d8c51280a0aad1e48fd4ffcf0aa6&itemid=350295152276&ff4=263602_263622")
[/SIZE][/FONT]

---

### Post by mjrich1976 on 2010-05-26
Thanks everyone for the very quick replies!

I think I'm going to do as cpplinux suggests and try Xubuntu.

My question is: Can I still install all of the same apps I have now? I want to install it not only to play around with from a learning standpoint, but also to do some coding and other things. I want to be able to put Eclipse, a C++ IDE, Java, PERL, PHP, MySQL, Apache, etc. on this, as well as put some games and educational stuff on it for my son.

I'm assuming this is still possible.

And Xubuntu is a GUI, right?

---

### Post by cascade9 on 2010-05-26
1st off, no 256Mb is NOT the maximum RAM that machine can take. Its 512MB- 

> **Figure 1: HP Pavilion XE813 PC bundle **
Memory

**Component****Attributes**RAM (standard)     128 megabytes (MB) PC 100     Maximum     512 MB (2 x 256 MB DIMM)     [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph06284](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=bph06284)

> **mjrich1976 said:**
> I'm essentially new to Linux. I would like to learn more about it, and I am eager to do so. If this post is in the wrong place,  I apologize.

1. The install took a decent amount of time (from a CD), but the updates (84 after the initial install) took over **24 hours**. I am not exaggerating in any way.

2. I can't really log into Gnome. Failsafe Gnome allows me to log in, but at times is very sluggish. Based on what I've read, the GNOME issue has something to do with applets, I think. When I try to log into Gnome, I only get the wallpaper, no tool bars or menu bars. I'm not entirely sure what KDE is, either, but I tried logging into that with no success. I also tried doing a reinstall of the applets from the Package Manager, and that did not seem to help any.

3. Something, at times, just hammers my processor. Occasionally, the light will appear solid, it's flashing so fast, other times it will just flash very rapidly. In both cases, I am not even at the machine. And if I were, I couldn't do anything.

I think this machine is only capable of holding 256 MB of RAM. If I understand right, Lucid Lynx requires 512MB to run properly. Please correct me if I am wrong.

Advice?

1- Could quite possibly be connected to having not enough RAM. Or it could be just that you have a slow internet connection.

2- Again, quite possibly from not enough RAM. 

3- yes, that would be the CPU working its poor little butt off as it tries to swap things to and from the swap drive. 

> **cpplinux said:**
> 
**Minimum system requirements**

 You need 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run the Live CD or 192 MB RAM  to install. The Alternate Install CD only requires you to have 64 MB RAM  at install time.
 To install Xubuntu, you need 2.0 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with starting from 192 (or even just  128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.

Outdated requierments. See here- 

>  Minimum system requirements for Xubuntu would fall roughly between Ubuntu Server and Desktop: 
 
[LIST]
[*]256 MiB of system memory (RAM)
[*]2 GB of disk space
[*]Graphics card and monitor capable of 800x600 resolution
[/LIST]
 [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Xubuntu wont help much IMO. Lubuntu, or a minimal install with Xfce should run a lot better. Since you are a beginner, I would advise not to try the minimal install (though its not that hard, it could be fustrating). Id try Lubuntu. ;)

More RAM would be really good as well. Even if you do use Lubuntu ;)

---

### Post by cascade9 on 2010-05-26
> **mjrich1976 said:**
> Thanks everyone for the very quick replies!

I think I'm going to do as cpplinux suggests and try Xubuntu.

My question is: Can I still install all of the same apps I have now? I want to install it not only to play around with from a learning standpoint, but also to do some coding and other things. I want to be able to put Eclipse, a C++ IDE, Java, PERL, PHP, MySQL, Apache, etc. on this, as well as put some games and educational stuff on it for my son.

I'm assuming this is still possible.

And Xubuntu is a GUI, right?

I wouldnt waste your d/l with xubuntu. It might run a little better (not in my expereince it wont, but that might be just me) but not enough better to make that system run well. 

Yes, Xubuntu is a GUI- but so is Lubuntu. Also, yes, you can run virtually anything on Xubuntu/Lubuntu that runs on standard Ubuntu ;)

---

### Post by philinux on 2010-05-26
Topic very recently discussed.

[http://ubuntuforums.org/showthread.php?t=1484359](http://ubuntuforums.org/showthread.php?t=1484359)

---

### Post by mjrich1976 on 2010-05-26
I've been looking for 256MB sticks for this machine, but I can't find them anywhere! Should I just be able to get some generic PC100 RAM and shove it in?

I'm good downloading and installing whatever flavor of 10.04 Ubuntu that I need to, as long as I can learn from it, and download any of the apps I might want.

---

### Post by cascade9 on 2010-05-26
> **mjrich1976 said:**
> I've been looking for 256MB sticks for this machine, but I can't find them anywhere! Should I just be able to get some generic PC100 RAM and shove it in?

I'm good downloading and installing whatever flavor of 10.04 Ubuntu that I need to, as long as I can learn from it, and download any of the apps I might want.

What country are you in? I knwo that you can still get 256MB PC100 sticks from newegg- 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147+1052107967&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=147&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147+1052107967&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=147&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

BTW, I've got a computer with the same chipset as that. I've found that it can be a bit funny with RAM (like things that should work dont). If your in a major city, it might be easier to find a 2nd hand computer store, or a 'computer recycler' and take your machine in to test the RAM when you buy it. 

Also, PC133 should be fine, and I have this idea that a 512MB stick works. I dont have a 512MB SD RAM stick to test that though :|

---

### Post by mjrich1976 on 2010-05-26
> **cascade9 said:**
> What country are you in? I knwo that you can still get 256MB PC100 sticks from newegg- 

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147+1052107967&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=147&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010170147+1052107967&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=147&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

BTW, I've got a computer with the same chipset as that. I've found that it can be a bit funny with RAM (like things that should work dont). If your in a major city, it might be easier to find a 2nd hand computer store, or a 'computer recycler' and take your machine in to test the RAM when you buy it. 

Also, PC133 should be fine, and I have this idea that a 512MB stick works. I dont have a 512MB SD RAM stick to test that though :|

I'm in the U.S.

I never thought of Newegg. Thanks!

From what I can tell, I wouldn't be able to run "standard" Ubuntu 10.04, even if I did  go to the 512 MB of RAM, because I would need a minimum 1 GHz processor.

So it looks like Lubuntu for now, then Xubuntu.

By the way, is there a way to go from one flavor to another without having to reinstall a ton of apps every time?

Like if I want to go from Lubuntu to Xubuntu, but I don't want to lose any of the apps I have installed (like Eclipse MySQL, educational stuff for my son, etc.)?

And one other thing...how long will the initial install/update take?

---

### Post by cascade9 on 2010-05-26
No problem ;) 

'Standard' Ubuntu should run on 733, and with 512MB it might just be slow, not painful. Probably better of with Lubuntu though. 

You can always install other DEs (desktop enviroments) with ubuntu (and most linuxdistros for that matter). You can do it from synaptic, the command line or (I think, I dont have a *buntu running to check now) the software centre. 

EG, to install lubuntu, you can go to command line and type-

sudo apt-get install lubuntu-desktop

That will install lubuntu, and then when you start up next, you can choose lubuntu at the login screen. All the programs you installed with ubuntu/xubuntu, etc will be usable ;) 

Same goes for xubuntu (xubuntu-desktop) kubuntu (kubuntu-desktop, kde-minimal) etc. BTW, whatever you do, dont try kubuntu (or even kubuntu-minimal) on that machine.

---

### Post by mjrich1976 on 2010-05-26
> **cascade9 said:**
> No problem ;) 

'Standard' Ubuntu should run on 733, and with 512MB it might just be slow, not painful. Probably better of with Lubuntu though. 

You can always install other DEs (desktop enviroments) with ubuntu (and most linuxdistros for that matter). You can do it from synaptic, the command line or (I think, I dont have a *buntu running to check now) the software centre. 

EG, to install lubuntu, you can go to command line and type-

sudo apt-get install lubuntu-desktop

That will install lubuntu, and then when you start up next, you can choose lubuntu at the login screen. All the programs you installed with ubuntu/xubuntu, etc will be usable ;) 

Same goes for xubuntu (xubuntu-desktop) kubuntu (kubuntu-desktop, kde-minimal) etc. BTW, whatever you do, dont try kubuntu (or even kubuntu-minimal) on that machine.

So Xubuntu should be OK with 512MB RAM and my 733 Celeron? It might just run a little slow?

---

### Post by gator2802 on 2010-05-26
> **cpplinux said:**
> Have you tried Xubuntu?
 
[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)
 
Quote:
**Minimum system requirements**
 
You need 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run the Live CD or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.
To install Xubuntu, you need 2.0 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
Once installed, Xubuntu can run with starting from 192 (or even just 128) MB RAM, but it is strongly recommended to have at least 256 MB RAM.
 
I ran Xubuntu on a Dell C600 and it ran very efficiently and smoothly.  One of the major changes between the two distros is that Ubuntu uses GNOME and Xubuntu uses the lighter XFCE desktop environment.  Best of luck.

---

### Post by cascade9 on 2010-05-26
> **mjrich1976 said:**
> So Xubuntu should be OK with 512MB RAM and my 733 Celeron? It might just run a little slow?

It should be OK (ish) even with 256MB. Still, its never going to be anywhere near as fast as lubuntu, even with 512MB. 

I would have less issues with xubuntu except that I have used Xfce and its been very light (minimal install buntu + Xfce, or Debian Xfce)...I just dont get why the developers have done what they have done to xubuntu.

---

### Post by Mark Phelps on 2010-05-26
I ran an older (8.04) Xubuntu on a PIII 600MHZ, 256MB RAM laptop.

It ran, it was just painfully show when compared to more typical, modern, desktop machines.

So, if you're OK with waiting a while every time you want to do something, it will work ...

---

### Post by cascade9 on 2010-05-26
> **Mark Phelps said:**
> I ran an older (8.04) Xubuntu on a PIII 600MHZ, 256MB RAM laptop.

It ran, it was just painfully show when compared to more typical, modern, desktop machines.

So, if you're OK with waiting a while every time you want to do something, it will work ...

Thats pretty much what I had, with slightly better specifications (P3-866, intel 810 video, and I used everything from 192MB to 384MB). While Xubuntu was (heh, heh) 'painfully' slow, minimal install Xfce, Debian Xfce and sidux Xfce were actually fairly snappy. 

Not as fast as a modern machine, I agree, but that huge delay between opening a program and it being useable was reduced a lot.

---

### Post by halitech on 2010-05-26
if you want to avoid some of the bloat they are adding lately to make things easier, try Debian with XFCE or LXDE. I have it installed on a P3 500 with 192meg of ram on a 40 gig drive and it runs nicely to me. No where near as nice as my Debian + XFCE on my AMD X2 5200+ with 2gig of ram but very usable.

[http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/](http://cdimage.debian.org/cdimage/squeeze_di_alpha1/i386/iso-cd/)

---

### Post by mjrich1976 on 2010-05-26
> **cascade9 said:**
> Thats pretty much what I had, with slightly better specifications (P3-866, intel 810 video, and I used everything from 192MB to 384MB). While Xubuntu was (heh, heh) 'painfully' slow, minimal install Xfce, Debian Xfce and sidux Xfce were actually fairly snappy. 

Not as fast as a modern machine, I agree, but that huge delay between opening a program and it being useable was reduced a lot.

So I think for now Lubuntu will be the way I will go.

Once I get my 512MB, I might try out Xubuntu.

But for now, I think I'm going to try Lubuntu.

Thanks again for all the help! I'm not going to change this thread to "solved" at this point, but I will after I see if everything works like it should.

---

### Post by cascade9 on 2010-05-26
Good luck ;)

---

### Post by mjrich1976 on 2010-05-26
> **cascade9 said:**
> Good luck ;)

Thanks!

It's still selecting/unpacking right now...I'm hoping it's almost done.

---

### Post by mjrich1976 on 2010-05-26
> **mjrich1976 said:**
> Thanks!

It's still selecting/unpacking right now...I'm hoping it's almost done.

Ok...well, it finished, and I switched users (I didn't shut down), and it gave me an error about not being able to access FAM.

But I did a restart, and it does seem to be working faster.

I'll keep an eye on it, and if it's still working good in a couple of days, I'll change the status to "solved".

---

### Post by cascade9 on 2010-05-26
FAM = File Alteration Monitor. 

If the package is installed (I think it is by default), then I'd try a reboot.

---

### Post by lil0tik on 2010-05-26
Just to throw in my two-cents...

On older computers, I've had very good luck with the "light" version of Crunchbang Linux, which is a heavily stripped down (and unofficial) Ubuntu variant with Openbox instead of Gnome/KDE/XFCE.  I've installed it on a variety of computers running as little as 192Mb RAM and it runs well, and - unlike Puppy or DSL - you can still take advantage of Ubuntu's excellent support and repos.  Personally, I prefer Openbox to LXDE, which is the main reason I prefer this distro to Lubuntu.

I also like the fact that I don't have to worry about breaking metapackages when I uninstall stuff I don't like (which always seems to muck up my later updates using Xubuntu, etc, even though it should be fine theoretically).

Once you've become used to using Linux and become more confident in messing with stuff, Crunchbang also provides a nice "base distro" upon which to build your own custom, ultralight Ubuntu installs.

The downfalls:

[LIST]
[*]It's built on 9.04, not 10.04
[*]If you're in the US, all the defaults for time, date, currency, and so on are in British units (likewise, the "Trash" is called "Wastebin", which is kinda silly).
[*]Maintaining menus and stuff takes more attention when using Openbox, though a couple nice GUI tools are included so you don't need to go so far as manually editing all the config files.
[*]It includes non-free codecs & stuff by default (this can be an advantage or disadvantage depending upon how zealous you are about free software)[/LIST]

---

### Post by golanbatrac on 2010-05-26
Second the recommendation for Openbox.  I build from the command line system available on the Ubuntu alternate cd rather than from Crunchbang.  Works great with 128 Mb RAM.  Soars with an extra 256.

---

### Post by lil0tik on 2010-05-26
> **golanbatrac said:**
> Second the recommendation for Openbox.  I build from the command line system available on the Ubuntu alternate cd rather than from Crunchbang.  Works great with 128 Mb RAM.  Soars with an extra 256.

Actually, I usually build from the alternate disc and use StumpWM (128Mb is no problem there, I assure you), but that's a little much for Absolute Beginners :)  Finding an extremely light Ubuntu distro (barring the alternate install + whatever WM/DE you want) that worked out of the box took me a very long time and many reinstalls as a beginner, which is why I recommended Crunchbang.

But, yes, Openbox (or Fluxbox, too) offers a nice mix of minimal resource use, ease of use, and prettiness that should please anyone with an older computer.

---

### Post by mörgæs on 2010-05-26
Go for a minimal Ubuntu:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by mjrich1976 on 2010-06-18
I've decided to go ahead and close this since Lubuntu is working for me.

I just need to get more RAM for this machine, and it should work a little faster.

---

### Post by Kixtosh on 2010-06-25
I know this is solved, but I'm a little surprised that you are having so many issues. I am running Xubuntu 10.04 (Lucid Lynx) on my laptop, which seems to have similar specifications, and is absolutely limited to 256MB of RAM. It's not perfect (browsing can be a little slow, and I don't dare to try OpenOffice), but here are some benchmarks:

- Boot time is 65-75 seconds, from pushing start to full desktop. 
- Active internet connection, after the full desktop displays, is about 10-15 seconds extra.
- Opening FireFox takes 10-12 seconds (slow, but not totally painful).

Currently with browser open and 9 tabs active on forum threads:

- 60% of RAM is in use (usually closer to 40 or 50%).
- 2.4% of swap is in use.

I haven't had to modify anything, or add any proprietary drives, even for my PC Card Wireless, but I don't think standby works properly (it's possibly a Toshiba thing).

I also tried regular Ubuntu 9.10 before and compared that to Xubuntu 9.10. The main difference was startup times, that were 20-30 seconds faster with Xubuntu. Also, sound worked better under Xubuntu with one of my old laptops.

I've also tried Puppy Linux. It's a great little OS, but installing it correctly to a hard drive can be a nuisance. It's not necessary on some machines to bother installing (you just use the CD when you want it) but this ultra light laptop does not have a built in CD drive, so the HDD install was the only option I wanted to try. Surprisingly, perhaps, Puppy took longer than Xubuntu to start up, but once loaded, all applications open with a few seconds.

I may try Peppermint too, or LXDE with Xubuntu, before I finally decide what I want to do, but for just regular browsing and document editing, I could easily live with either Xubuntu or Lucid Puppy.

Best of luck!

---

### Post by Kixtosh on 2010-06-25
):P The results for LXDE are in:
 
It was a very simple install (I just used the ubuntu software center from the drop down menu to add LXDE with my existing install of Xubuntu 10.04).
 
I switched over to LXDE by logging out from my Xubuntu session, and restarting a new session after selecting LXDE from the pop-up menu from the bottom of the log in screen (that should be the default location, since I haven't modified anything since installing Xubuntu). I did have to enable the _Network Manager_ from the _Preferences_ menu. It's under _Desktop Session Settings_. That got wireless to turn on again.
 
- Start up times have decreased by about 10-15 seconds.
- The browser may open a little faster, by a couple of seconds or so.
- RAM usage is now down to 30% just after starting up.
- RAM usage is still under 50% (114MiB) with eight FireFox tabs open.
- Swap is between 0% and 0.3% so far.
- I prefer the less cluttered look compared to regular Xubuntu.
 
So, there is a significant performance boost, but it's still not as fast as Puppy to open big applications like a browser. Chromium seems to be able to open consistently in under ten seconds (never fewer than eight), so that may be what I end up using, since that is at least two seconds better than FireFox or SeaMonkey. I'll see how it does when navigating from screen to screen over time.
 
None of this may seem ideal, perhaps, but for an old machine that could only be used with W2K (or sold on eBay for $100 or less), this makes it very suitable for a very mobile, very light, reliable secondary laptop.
 
***Edit!** It turns out that Chromium only takes eight seconds to start up the _first_ time during a session. On each subsequent start, it only takes two seconds to open, which is a huge boost compared to FireFox or SeaMonkey. There are fewer and fewer reasons to consider Puppy when compared to Xubuntu with LXDE!*

---

