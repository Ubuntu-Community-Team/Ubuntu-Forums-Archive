---
title: "amarok has no sound in ubuntu 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by medya on 2009-10-31
i just installed amarok, when I hit play  I hear nothing.

sound works in vlc or movie player... just not works in Amarok

---

### Post by nns2006 on 2009-10-31
Have you tried rebooting the system? It worked for me.

---

### Post by medya on 2009-10-31
I just found it , amarok plays wav music but not mp3 ! 
strange .
I guess there is a bug in luanchpad .
is there any work-arround?

---

### Post by medya on 2009-10-31
rebooting didnt help me :(
has anyone installed amarok on a fresh ubuntu 9.10 ? does it work for anyone ?

---

### Post by arrgghh on 2009-10-31
hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

---

### Post by rakesh_roshan on 2009-11-03
hey thanks it worked

---

### Post by MelDJ on 2009-11-03
> **medya said:**
> rebooting didnt help me :(
has anyone installed amarok on a fresh ubuntu 9.10 ? does it work for anyone ?

tried removing and reinstalling amarok?

---

### Post by surja on 2009-11-04
This solution worked perfectly :D Thanks for the tip.:KS

---

### Post by proaditya on 2009-11-04
Yup. After installing the package , it works.

Thanks

---

### Post by travnewmatic on 2009-11-06
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

yeah buddy, worked for me

---

### Post by caitifty on 2009-11-06
Alas, didn't work for me, even after installing the kubuntu-restricted-extras package also mentioned in the link originally posted.  

The weird thing is, when I go to Settings -> Configure Amarok -> Playback -> Configure sound settings, it shows my sound card and plays a nice little tune when I click the 'test' button.  So the sound itself is working fine..  Just no Amarok.

---

### Post by LarryJ2 on 2009-11-07
Score another for 
sudo apt-get install libxine1-ffmpeg

Thanks!

---

### Post by dizee on 2009-11-09
Thanks for the tip, installing libxine1-ffmpeg also worked for me.

---

### Post by Milind on 2009-11-10
Thanks, friend. Same problem, solved!:D
The strange thing is Amarok used to work perfectly for me in Jaunty. Installed 9.10, installed Amarok, and - deathly silence. I was starting to tear my hair out in frustration.

---

### Post by mahiyar on 2009-11-12
Thanks bro, Amarok is my favorite player, I was terrified when it did not play. Installing libxine did the trick.

---

### Post by CrunchBuntu on 2009-11-14
sudo apt-get install libxine1-ffmpeg

Did the job here too. Thanks.

---

### Post by oviorus on 2009-11-21
> **caitifty said:**
> Alas, didn't work for me, even after installing the kubuntu-restricted-extras package also mentioned in the link originally posted.  

The weird thing is, when I go to Settings -> Configure Amarok -> Playback -> Configure sound settings, it shows my sound card and plays a nice little tune when I click the 'test' button.  So the sound itself is working fine..  Just no Amarok.

It didn't work for me either, I already had those packages installed, and I can't hear the test tune in configure sound settings. Also, when I launch Amarok it tries to open something called "KDE Wallet service" but freezes until I rigth click->close that window... 

I have been using amarok for some time, but just upgraded to 9.10 and it stopped working

Edit:
Never mind, the updrade didn't cause amarok to stop working, it caused all my sound system to stop working.

---

### Post by mahiyar on 2009-11-22
Ovirus -- Maybe in the upgrade process some dependency has broken down, try uninstalling amarok and then reinstall afresh.

---

### Post by ssarkarhyd on 2009-11-24
Works great. The workaround did work. :popcorn:

---

### Post by JBAlaska on 2009-11-25
```
sudo apt-get install libxine1-ffmpeg
``` Just worked for me also.

WTF? why isn't this installed with Amarok?

---

### Post by toupeiro on 2009-11-25
> **ssarkarhyd said:**
> Works great. The workaround did work. :popcorn:

Quick update on this.  I believe the libxine1 suite of libraries from the getdeb PPA are broken, I had to completely remove my libxine stuff, disable the getdeb ppa, then I got the karmic releases again and everythings good.

Another testament to the ubuntu PPA's and user beware for non-ubuntu PPA's...

---

### Post by statokinetics on 2009-11-27
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

+1, worked for me, odd that the synaptic package for amarok doesn't pull it in on the install

---

### Post by jeffltw on 2009-12-04
Yeap worked for me too.

---

### Post by rod40cool on 2009-12-30
Ah, would you believe the old libxine1-ffmpeg trick worked for me too...

---

### Post by Runlevel on 2010-01-08
Hi,

when I try [COLOR=SeaGreen]sudo apt-get install libxinel-ffmpeg[/COLOR] 

I get this error-message:

[COLOR=Red]E: Konnte Lock /var/lib/dpkg/lock nicht bekommen - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]
[COLOR=Black]
what can I do? I have Ubuntu Karmic.
[/COLOR]

---

### Post by kentpend on 2010-01-08
That sounds like you already have a package manager working.  Do you have update manager, gdebi, or synaptic running?  If so close them and try again.

---

### Post by ariasjose on 2010-01-12
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

Worked for me... TY Bro!

---

### Post by dewapur on 2010-01-14
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```did the trick

hth :)

it works for me too

---

### Post by riminicat on 2010-01-18
Hey it worked for me too.  Thanks you!:D

---

### Post by jlb.think on 2010-01-24
> **Runlevel said:**
> Hi,

when I try [COLOR=SeaGreen]sudo apt-get install libxinel-ffmpeg[/COLOR] 

I get this error-message:

[COLOR=Red]E: Konnte Lock /var/lib/dpkg/lock nicht bekommen - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR]
[COLOR=Black]
what can I do? I have Ubuntu Karmic.
[/COLOR]


You probably have your update manager set to download updates automatically in the background.  Open your update manager and change it to only notify you of updates and not automatically download them.

---

### Post by hughes532001 on 2010-01-29
Thanks For the solution.  I installed amarok in gnome desktop and the addition of the codec using 
sudo apt-get install libxine1-ffmpeg 

worked great for me.

Regards

Trevor

---

### Post by 1991sudarshan on 2010-01-29
the amarok is taking hell a lot of time to open in both ubuntu and Kubuntu any suggestions?

---

### Post by b9k9kiwi on 2010-01-31
Well, I've followed this thread with interest ever since Amarok packed a sulk on my Karmic box (fresh install).

I've installed/unistalled/reinstalled Amarok innumerable times following advice from other threads as well as this thread (deleting folders and configs and installing various libraries in the process) and finally it appears to be working - got sound (5.1 surround), tracks select without the programme choosing an entirely different track at random (not that it then played anyway), the bizarre and unwanted KDE Wallet dialogue is gone and (so far) it hasn't crashed to disappear and lie dead in the background.

I'm not in love with Amarok - I consider it merely to be the best of a pretty poor bunch - but I was determined not to be beaten by this glitch.

Thanks to everyone who contributed.

---

### Post by shan420 on 2010-02-14
Worked for me as well, thank You,.. I still wonder why Amarok doesn't have it's old live music Database, they shortened it out completely .... for e.g. Channels like 90's 80's, Dance, Dance floor are all missing


> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

---

### Post by shaneonabike on 2010-02-15
Hey guys,

I had the same problem where the sound wasn't be output even during the test. I ended up having to install:

phonon-backend-xine 

Read that on another post and it worked for me... :)

---

### Post by mihamtalamac on 2010-02-20
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)
great tip :)  works with me

---

### Post by gerben1 on 2010-03-09
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

Thanks, this made it work.

If you install Amarok in Ubuntu 9.10 via the Synaptic Package Manager, it apparently cannot play any mp3's nor can you add them to the playlist. Unless you have libxine1-ffmpeg installed.

I had to search around for quite a while before I found this thread...
Here follow some terms, so people searching for this issue might find it sooner:
Amarok how to add to playlist
Amarok cannot add to playlist
Amarok can't add to playlist
Amarok cannot play mp3
Amarok can't play mp3

---

### Post by Annigma on 2010-04-15
> **gerben1 said:**
> Thanks, this made it work.

Worked for me too. Thanks "arrgghh" :-D

> **gerben1 said:**
> 
If you install Amarok in Ubuntu 9.10 via the Synaptic Package Manager, it apparently cannot play any mp3's nor can you add them to the playlist. Unless you have libxine1-ffmpeg installed.

I had to search around for quite a while before I found this thread...
Here follow some terms, so people searching for this issue might find it sooner:
Amarok how to add to playlist
Amarok cannot add to playlist
Amarok can't add to playlist
Amarok cannot play mp3
Amarok can't play mp3

That's helpful gerben. 'Amarok help no sound' worked for me, but that can be one of the most frustrating things about searching for answers: how we describe our problem.

I was pleasantly surprised to find that I could just enter 
```
sudo apt-get install libxine1-ffmpeg
```
without even closing Amarok, and it worked! Impressive :cool:

I found the KDE Wallet thing rather annoying, but I've 'caved' and given it a password, so that it can do it's thing, so I guess I'll have to 'log in' when I use Amarok (I do like the last.fm scrobbler). No big deal I guess..

---

### Post by AmaDaden on 2010-04-25
Had the same issue. But installing libxine1-ffmpeg did NOT WORK for me. I needed to install phonon-backend-xine. 
```
sudo apt-get install phonon-backend-xine
```
It seems that the only phonon backend I had for Amarok was GStreamer and it was not working. In Amarok you can see what phonon backends you have by going to settings -> configure amarok -> playback -> configure -> backend

I'm having sound crashing issues now but I can at least get sound at all

---

### Post by Cyc. on 2010-05-03
Again for me needed to change the backend to xine, libxine1-ffmpeg did not work for me either.

The following worked for me:
```
sudo apt-get install phonon-backend-xine
```

---

### Post by jbeamz on 2010-07-14
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

:KS from me too! This worked. Thank!

---

### Post by seshomaru samma on 2010-08-14
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

This did the trick for me ,on Karmic

---

### Post by orthopod on 2010-08-26
loading the libxine-ffmpeg   file worked for me

---

### Post by pragya on 2010-10-08
Thanks buddy..that helped!!!

---

### Post by xpinguimx on 2010-10-31
> **arrgghh said:**
> hey, i had the the same issue. i couldn't replay mp3s. ogg vorbis, musepack, wav, etc.. all seem to be working fine. hence, must have been a codec issue.
found this: [http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/](http://digitizor.com/2009/10/10/how-to-play-mp3-files-add-mp3-support-amarok-ubuntu/)

```
sudo apt-get install libxine1-ffmpeg
```
did the trick

hth :)

Worked for me too =) and I use Linux Mint, an Ubuntu-based distro

---

