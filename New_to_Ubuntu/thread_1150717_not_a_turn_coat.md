---
title: "not a turn coat"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-06
i have heard so much about debian, 
does anyone know if i can get a live cd of it. to try it.
i hear it is the most stable and if they add something it really works.
what are peoples thoughts on this?
Is it better than Ubuntu?

---

### Post by LowSky on 2009-05-06
try it for yourself

[http://www.debian.org/CD/http-ftp/](http://www.debian.org/CD/http-ftp/)

---

### Post by halitech on 2009-05-06
Live CD - [http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

the folks at Debian don't use a time table to decide when to release something, they do it when it has been satisified in their mainds it is stable enough to be released (there is a testing and experimental version as well for the more daring).

As far as is it better then Ubuntu? You're asking on the ubuntu forums so of course you are going to get a fair number of answers saying Ubuntu is better. Same if you go to the debian forum, they will say Debian is better, hard to get an unbiased opinion on either site :)

Personally I've used both and it depends on what you want to do. If you want something that will basically install and be usable, go Ubuntu. If you don't mind doing a little work after the initial install, then go Debian. The benefit of Ubuntu is it includes a lot more of the non-free apps and binary blobs that Debian doesn't include (but allows you to install) but that also slows the system down some so Debian is slightly leaner and responds faster due to a lighter kernel.

My 2 cents, others may disagree

---

### Post by DarinB on 2009-05-06
i went to the down load site and it seems there are 5 dvd's to download and burn????
or all they all the same thing??????
the cd iso has about 30 cd's listed????

Index of /debian-cd/5.0.1/i386/iso-dvd

Icon  Name                               Last modified      Size  [DIR] Parent Directory                                        -   
[   ] MD5SUMS                            14-Apr-2009 20:10  369   
[   ] MD5SUMS.sign                       14-Apr-2009 20:16  189   
[   ] SHA1SUMS                           14-Apr-2009 20:10  417   
[   ] SHA1SUMS.sign                      14-Apr-2009 20:16  189   
[   ] debian-501-i386-DVD-1.iso          13-Apr-2009 02:45  4.4G  
[   ] debian-501-i386-DVD-2.iso          13-Apr-2009 02:47  4.4G  
[   ] debian-501-i386-DVD-3.iso          13-Apr-2009 02:50  4.4G  
[   ] debian-501-i386-DVD-4.iso          13-Apr-2009 02:54  4.4G  
[   ] debian-501-i386-DVD-5.iso          13-Apr-2009 02:55  1.2G  
[   ] debian-update-5.0.1-i386-DVD-1.iso 14-Apr-2009 02:20  1.5G

---

### Post by mick8985 on 2009-05-06
Depends which branch you are running, if you run stable packages will be very old (ie programs such as rhythmbox/totem/banshee will be without features you have had on ubuntu for years), if this is likely to annoy you don't run it.
If you run testing the packages won't be quite so old but still can be noticeably annoying at times, and when you want a newer package expect to have to compile because you don't have launchpad ppa's all over the place with nice prebuilt packages for debian, also you will find that projects which host debs tend to always host ubuntu debs and not as frequently host debian debs.
If you run unstable it will be like running ubuntu, but sometimes with newer, but less stable packages than ubuntu (especially near the end of the ubuntu release cycle, although people often change to ubuntu beta by this point).
In short unstable is like a constantly rolling beta, in testing the packages are still too old for my tastes, and stable is completely unusable as a desktop system unless you have a hard on for 2004 and refuse to move on.
But Debian is a great system, it's just hard to strike the balance of bleeding edge and stable packages that you can on ubuntu using the launchpad ppa infrastructure, and easily available debs from getdeb and other sources.

For me the other differences in an distro are largely irrelevant, all I care about is the availability of quality up to date packages.

---

### Post by halitech on 2009-05-06
> **DarinB said:**
> i went to the down load site and it seems there are 5 dvd's to download and burn????
or all they all the same thing??????
the cd iso has about 30 cd's listed????

Index of /debian-cd/5.0.1/i386/iso-dvd

Icon  Name                               Last modified      Size  [DIR] Parent Directory                                        -   
[   ] MD5SUMS                            14-Apr-2009 20:10  369   
[   ] MD5SUMS.sign                       14-Apr-2009 20:16  189   
[   ] SHA1SUMS                           14-Apr-2009 20:10  417   
[   ] SHA1SUMS.sign                      14-Apr-2009 20:16  189   
[   ] debian-501-i386-DVD-1.iso          13-Apr-2009 02:45  4.4G  
[   ] debian-501-i386-DVD-2.iso          13-Apr-2009 02:47  4.4G  
[   ] debian-501-i386-DVD-3.iso          13-Apr-2009 02:50  4.4G  
[   ] debian-501-i386-DVD-4.iso          13-Apr-2009 02:54  4.4G  
[   ] debian-501-i386-DVD-5.iso          13-Apr-2009 02:55  1.2G  
[   ] debian-update-5.0.1-i386-DVD-1.iso 14-Apr-2009 02:20  1.5G

those are the install dvds, the link I posted are to the actual live cds

> **mick8985 said:**
> Depends which branch you are running, if you run stable packages will be very old (ie programs such as rhythmbox/totem/banshee will be without features you have had on ubuntu for years), if this is likely to annoy you don't run it.
If you run testing the packages won't be quite so old but still can be noticeably annoying at times, and when you want a newer package expect to have to compile because you don't have launchpad ppa's all over the place with nice prebuilt packages for debian, also you will find that projects which host debs tend to always host ubuntu debs and not as frequently host debian debs.
If you run unstable it will be like running ubuntu, but sometimes with newer, but less stable packages than ubuntu (especially near the end of the ubuntu release cycle, although people often change to ubuntu beta by this point).
In short unstable is like a constantly rolling beta, in testing the packages are still too old for my tastes, and stable is completely unusable as a desktop system unless you have a hard on for 2004 and refuse to move on.
But Debian is a great system, it's just hard to strike the balance of bleeding edge and stable packages that you can on ubuntu using the launchpad ppa infrastructure, and easily available debs from getdeb and other sources.

I run Debian stable (Lenny) and I don't see the issue you are talking about. Unstable is the next stable release, Experimental (code named SID) is more like a rolling release. The previous stable (Etch - now stable-old) has old software but you can update to newer apps using the backports repos.

---

### Post by mick8985 on 2009-05-06
> **halitech said:**
> 
I run Debian stable (Lenny) and I don't see the issue you are talking about. Unstable is the next stable release, Experimental (code named SID) is more like a rolling release. The previous stable (Etch - now stable-old) has old software but you can update to newer apps using the backports repos.

Sorry it's been so long since I ran Debian I was wrong about the naming of the three different branches, but what I said still applies IMO if take into account my error in naming.
I just find it's easier to strike the balance I want with newer software on Ubuntu thanks to launchpad ppa's, debs provided from getdeb and debs directly from software developer/vendor website.
I am not trying to put the guy off Debian by any means, just offering my opinion. He is best off just to try it if he has the time and inclination to give it a go.

---

### Post by halitech on 2009-05-06
thats the beauty of linux, we are free to make the choice on what we want to run on our systems :) Personally I prefer Debian for my main system although I am about to try the new Xubuntu on my old laptop just to see how it works.I just find that I would rather have system that runs stable on my system instead of chancing crashes from running software that may not have been tested but I also don't need the latest software for anything I do.

---

### Post by DarinB on 2009-05-06
This very interesting stuff. 
the reason i ask is because one of the linux podcasts said that they will wait on ext 4 until debian uses it. Implying that Debian is much better. 
I have converted 5 wondiows users to Ubuntu. The thing these people really need is out of the box usability.
That is still a problem for all of them.
i.e. i still don't have a working microphone on skype because of pulse audio.
or can get my ipod to mount in gpodder for video ipods. Banshee has no genre catagory and crashes
i would love to see this Ubuntu take off, but it is hard to convert people when stuff don't work.

---

### Post by DarinB on 2009-05-06
**can't** get ipod to mount in gpodder

---

### Post by halitech on 2009-05-06
> **DarinB said:**
> This very interesting stuff. 
the reason i ask is because one of the linux podcasts said that they will wait on ext 4 until debian uses it. Implying that Debian is much better. 
I have converted 5 wondiows users to Ubuntu. The thing these people really need is out of the box usability.
That is still a problem for all of them.
i.e. i still don't have a working microphone on skype because of pulse audio.
or can get my ipod to mount in gpodder for video ipods. Banshee has no genre catagory and crashes
i would love to see this Ubuntu take off, but it is hard to convert people when stuff don't work.

Debian is one of the grandfathers of Linux (along with slack) and Debian will only use things that are stable. If this makes Debian "better" or not, thats an opinion question.

If you are looking for a distro for new users, then either Ubuntu or Linux Mint (built on Ubuntu) as they both include a lot more non-free items that should get things working. For sykpe, try using ALSA instead of pulse-audio. For the ipod, try gtkpod and see if that works.

---

### Post by NightwishFan on 2009-05-06
Debian is an excellent, well polished system. Some people who are not free software purists might not like it's policy on software. They also might not like that the "stable" version of Debian is just that: Stable. It uses older, very well tested software, such as KDE3.5.10 and GNOME 2.22. Ubuntu Jaunty uses KDE 4.2.2 and GNOME 2.26. This is not to say you cannot get proprietary software working or newer less supported software.

One thing you might like is using Debian Unstable, which is still fairly stable. It has more modern software, and if you keep updating at intervals, you can constantly get newer software. It is called a "rolling release".

Using Debian, you may notice it is much lighter than default Ubuntu. Please note that lighter is not essentially faster. If you have trouble with drivers and the like already you may want to test Debian before you install.

I would say try the live CD, and bask in the speed and polish. If you want another interesting alternative to Ubuntu try OpenSUSE or Fedora, or both. Fedora has interesting innovative features, and tries to be one step ahead of other distros. OpenSUSE is very integrated with a full featured control center, and has some features like menus that are made originally for the distribution itself.

---

### Post by DarinB on 2009-05-08
ok i did try it.Debian 5.0
not the fastest os in the world not as slow as windows.
very retro as far as the advancements of Juanty, even less advanced that hardy.
i have a machine with 4gb of ram core 2 duo it screams with jaunty not great with Debian.
i am as a whole not impressed i am sticking with Ubuntu, now i get to have the fun if getting this thing off my machine,,,, i did give it a real honest try, i thought open suze was better even on an old p4 with 768 of ram,,,,
so if i have offended the die hard Debians i am sorry. 
i think the ubuntu team does a great job and i applaud then, even if? not all upgrades and new versions since i started with Feisty have been smooth or the best i am
solidly on board.

---

### Post by bodhi.zazen on 2009-05-08
Debian is an awesome OS, and in fact Ubuntu is based on Debian. The Ubuntu and Debian developers interact and cooperate.

Ubuntu is an ancient African work for "Can't install Debian" :lolflag:

While no longer as true, if you are new to Linux Debian is a bit more difficult to "set up" for desktop users meaning much more is set up automatically on Ubuntu.

Debian users may feel Ubuntu is "bloated", new users may feel Ubuntu is easier.

Once you understand how ubuntu works, Debian is, with the exception of a few minor things, essentially the same as Ubuntu, IMO.

Let me qualify that a bit though - I no longer do a Desktop install of either Ubuntu or Debian, I do minimal installs and then add only what I want, which is generally a light weight XFCE. So really the process is almost the exactly the same for Debian and Ubuntu for the type of installs I do.

In general, if you are installing for a new user, I would think the average users would prefer Ubuntu. Once the user has some experience under his or her belt, IMO, there really is no difference.

---

