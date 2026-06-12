---
title: "I'm new to linux and could use some help"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by new_2_Intrepid on 2009-02-12
Hi everyone I'm new to Ubuntu Linux, and I have to say that I love it! I don't have to use MS crap and wait on them to fix things(When they "Feel Like It" You pay 100 and some odd dollars and their customer service is horrible. I'm going to be Ubuntu user for Life !!! 
But on to my questions : I have multiper users in my home and that play a lot of games and other various apps. I have a game on my account Guild wars and brother wants to play it also, but it is not available on is user account. Is there a way that I could make it available to him without having to install on his user screen??
Also I'm looking for Useful Links to sites that are Linux oriented like [www.phoronix.com](www.phoronix.com), and how-to-sites for new system administrator to an ubuntu system, and just plain helpful Linux sites ? 
I absolutely no intention of ever going to back to Microsoft. 
All help is appreciated.
Thankyou,
Dominic

---

### Post by ibizatunes on 2009-02-12
Wine Hq will allow you to played games but it hit or miss
[www.winehq.org](www.winehq.org)

---

### Post by new_2_Intrepid on 2009-02-12
Also what is Mplayer?? Is it used mainly for home-made videos? or can you watch dvd's in it. Because everytime I put a Dvd in it will not play and it says source error. I've installed the the medibuntu repository,

---

### Post by golusweet on 2009-02-12
This might help.

[http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine)

---

### Post by Therion on 2009-02-12
Open a Terminal and copy and paste the following:```
sudo apt-get install ubuntu-restricted-extras libdvdcss2
```
Enter your password when prompted for it.  The rest is pretty self-explanatory.

---

### Post by new_2_Intrepid on 2009-02-12
Also what is Mplayer?? Is it used mainly for home-made videos? or can you watch dvd's in it. Because everytime I put a Dvd in it will not play and it says source error. I've installed the the medibuntu repository,
Also is there some open software, or even sofrware that I could purchase to I can make back-up copys of my DvD's? preferably with LightScribe support?
Thanks for your time and patience,
Dominic

---

### Post by ibuclaw on 2009-02-12
> **new_2_Intrepid said:**
> Also what is Mplayer?? Is it used mainly for home-made videos? or can you watch dvd's in it. Because everytime I put a Dvd in it will not play and it says source error. I've installed the the medibuntu repository,
mplayer is an audio/video player.

I personally prefer VLC over mplayer.
```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc
```
If you paste that into a terminal, it will install along with the libraries required to watch DVDs.


[EDIT]
And you can get Lightscribe support from here:
[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)

Regards
Iain

---

### Post by ugm6hr on 2009-02-12
Try the Start here.. thread linked below for useful guidance.

For multimedia / DVD - see the Multimedia link below.

MPlayer will play whatever you ask of it, as long as you install the correct "codecs"

---

### Post by Therion on 2009-02-12
> **new_2_Intrepid said:**
> Also what is Mplayer??
[i]MPlayer is a movie player which runs on many systems (see the documentation). It plays most MPEG/VOB, AVI, Ogg/OGM, VIVO, ASF/WMA/WMV, QT/MOV/MP4, RealMedia, Matroska, NUT, NuppelVideo, FLI, YUV4MPEG, FILM, RoQ, PVA files, supported by many native, XAnim, and Win32 DLL codecs. You can watch VideoCD, SVCD, DVD, 3ivx, DivX 3/4/5, WMV and even H.264 movies.

Another great feature of MPlayer is the wide range of supported output drivers. It works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev, AAlib, DirectFB, but you can use GGI, SDL (and this way all their drivers), VESA (on every VESA compatible card, even without X11!) and some low level card-specific drivers (for Matrox, 3Dfx and ATI), too! Most of them support software or hardware scaling, so you can enjoy movies in fullscreen. MPlayer supports displaying through some hardware MPEG decoder boards, such as the Siemens DVB, DXR2 and DXR3/Hollywood+.[/i]

Source:  [http://www.mplayerhq.hu/design7/info.html](http://www.mplayerhq.hu/design7/info.html)

---

### Post by mttman on 2009-02-12
Hello,

Something you might consider doing is going to [www.linux.org/groups/](www.linux.org/groups/) and finding a local linux users group to join. Generally speaking people who Start Linux Users Groups know a fair amount about linux and can help you out when you have questions.

It also gives you the advantage to see other peoples systems, or talk to other people on a more personal basis about there systems to see what is possible with Linux.

Another suggestion is to get the Stumbleupon plugin for firefox, add linux/unix as an intrest and then "just hit the stumble button". You'll find a lot of good linux stuff this way too.

Hope this helps and i'm glad to hear you enjoy your linux.

<Mttman>

---

### Post by new_2_Intrepid on 2009-02-12
Actually the current version of wine 1.1.14 works flawlessly with all versions of Guild Wars, version 1.1.13 worked but you could'nt see the faces and some other things but the current release works great in fact in is now listed on the top 10 Platinum List.
What I was asking was is there a way that I could share guild wars on my brothers user account; I have it installed on my Administrator account but I do not want him to use my account. So is there a way that I could put it on his account without having to reinstall it on his account ?? Like some how move it to a shared folder or something? Because I am not familar with Linux File system. But I know with windows I could just set it as a default program .

---

### Post by gjoellee on 2009-02-12
> **new_2_Intrepid said:**
> Actually the current version of wine 1.1.14 works flawlessly with all versions of Guild Wars, version 1.1.13 worked but you could'nt see the faces and some other things but the current release works great in fact in is now listed on the top 10 Platinum List.
What I was asking was is there a way that I could share guild wars on my brothers user account; I have it installed on my Administrator account but I do not want him to use my account. So is there a way that I could put it on his account without having to reinstall it on his account ?? Like some how move it to a shared folder or something? Because I am not familiar with Linux File system. But I know with windows I could just set it as a default program .

NOTE: Please notice that WINE 1.1.14 is a development release. Usually the development versions of WINE are very stable and also the most used WINE versions. If the version of WINE you are currently using works, just use that version...

In the menu: System->Administration->Users and Groups you will be able to manage accounts. Just click on "unlock" and then select your brothers user and select preferences. You should now have a window open containing a lot of options.
You should now enable the option that fits you, that might solve your problem.

If that does not work, you must consider reinstalling Guild Wars on your brothers user or give him "sudo" (superuser/root/administrator) rights.

---

### Post by new_2_Intrepid on 2009-02-13
Its not wine that I have a problem with wine.
I want to know if there is a way to allow another user access to the same game without having to re-install it on his screen? ie.
I am the administrator, I installed Guild Wars on my account, my brother also plays the game too , but when I made him an account (b/c I do not want him to have super user powers) The Guild Wars game is not there. I have to install it again. And my question is there a way to put the game on his user screen without having to reinstal it? Maybe some folder I can move it to or something? When I am logged onto his account the Applications Menu shows that Wine is there, but not the game.

---

### Post by Bablefish on 2009-02-13
If your still having trouble playing DVDs? Try automatrix

---

### Post by howefield on 2009-02-13
> **Bablefish said:**
> If your still having trouble playing DVDs? Try automatrix

You have said this before but never explain what it is and why the poster should use it ?

---

### Post by jolx on 2009-02-13
> **Bablefish said:**
> If your still having trouble playing DVDs? Try automatrix

Automatix is no longer developed, anyway there's no need for it, so just don't bother.

> **new_2_Intrepid said:**
> Its not wine that I have a problem with wine.
I want to know if there is a way to allow another user access to the same game without having to re-install it on his screen? ie.
I am the administrator, I installed Guild Wars on my account, my brother also plays the game too , but when I made him an account (b/c I do not want him to have super user powers) The Guild Wars game is not there. I have to install it again. And my question is there a way to put the game on his user screen without having to reinstal it? Maybe some folder I can move it to or something? When I am logged onto his account the Applications Menu shows that Wine is there, but not the game.

i think WINE might still be 'installed' for him and it just needs to be set up from his account by running "winecfg". again i am not sure at all but because wine should be installed throughout /usr, making it available to any user, i think a 'C:' needs to be set up in each user's folder.

also you don't have 'superuser' powers just by using your account it just means that you have the ability to run "sudo" for a particular program, which would mean entering a password again

EDIT: i just realised what you mean. I think it would be too much messing around and it would be easier to just reinstall it in his account. unless you want to mess around, in which case make sure you back up any important files and google is your friend :)

---

### Post by oldos2er on 2009-02-13
> **Bablefish said:**
> If your still having trouble playing DVDs? Try automatrix

 Automatix is old, broken software. Its use isn't supported on the forums here.

---

### Post by new_2_Intrepid on 2009-02-13
I don't mind messing around b/c I want to learn how to use Linux (as I have no intention of ever going back to MS ever again !!!
But if I install multiple games through Wine, I have reinstall each game for each user account on my system.. I mean there has to be an easier way? 
Not to mention I need to Learn how to use Linux you know .. I'm willing to make a few mistakes in order to learn

---

