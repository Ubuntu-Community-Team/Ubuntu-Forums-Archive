---
title: "Firefox - Ubuntu 9.10 - Streaming Vido fix is?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by Rolls_Canardly on 2009-10-16
Total Noob here, trying to divorce myself from Windows.. LOVE the beta of Ubuntu 9.10 with Firefox 3.5.  I have lots to learn, MUCH to look forward to.  But for right now (please, old pros, I know you've heard this before but..)

How do I get this link to play in Firefox:
[http://mackinaclive.com/](http://mackinaclive.com/)

I've installed (so I thought) shockwave flash, java, totem etc (and probably made a mess of things) and even grabbed a Firefox plugin / add-on or two.  Kinda the Noobie Spray-and-Pray method.

GOTTA be a short cut to getting that link to play video in Firefox.. thanks for any simple answers for now..

---

### Post by the.phantom on 2009-10-16
if it makes you feel better
i can't play on that site !

and i can work flash on my 8.10 32 bit

might be a microsoft thing? i have a few sites that require I.E. or windows to work

did you go to applications/add/remove  and install "ubuntu restricted extra's ?

can you work video at youtube?

---

### Post by mike555 on 2009-10-16
That site doesn't work for me ... it might be using "SilverLight" , which is only Microsoft.

---

### Post by Rolls_Canardly on 2009-10-16
> **the.phantom said:**
> if it makes you feel better
i can't play on that site !

and i can work flash on my 8.10 32 bit

might be a microsoft thing? i have a few sites that require I.E. or windows to work

did you go to applications/add/remove  and install "ubuntu restricted extra's ?

can you work video at youtube?

Youtube is running just fine.. and that Mackinac site runs on Windows IE, as well as FIrefox under WIndows without my having had to install Silverlight (at least not to my knowlege, Silverlight may have installed automatically, not sure) ... Also, I've not installed ubuntu restricfed extras.. will try that now.

Thanks for your ideas!

---

### Post by sandyd on 2009-10-16
> **Rolls_Canardly said:**
> Youtube is running just fine.. and that Mackinac site runs on Windows IE, as well as FIrefox under WIndows without my having had to install Silverlight (at least not to my knowlege, Silverlight may have installed automatically, not sure) ... Also, I've not installed ubuntu restricfed extras.. will try that now.

Thanks for your ideas!
EDIT:
i opened this in Firefox WINE.
Told me to install Windows Media Player 11
There is no WMP 11 for Ubuntu, so your outa luck.
might be able to hack it to play using totem though.
Im guessing that totem understands what is is (i can see the very regnoizable totem play/pause bar at the cottom of the black rectangle)
but is having some sort of problem playing it.
mmight also be able to hack it by installinf FIrefox in WINE, then installing WMP 10 and the WMP firefox plugin.

---

### Post by Rolls_Canardly on 2009-10-17
> **carlee said:**
> EDIT:
i opened this in Firefox WINE.
Told me to install Windows Media Player 11
There is no WMP 11 for Ubuntu, so your outa luck.
might be able to hack it to play using totem though.
Im guessing that totem understands what is is (i can see the very regnoizable totem play/pause bar at the cottom of the black rectangle)
but is having some sort of problem playing it.
mmight also be able to hack it by installinf FIrefox in WINE, then installing WMP 10 and the WMP firefox plugin.
Thanks for your input - I did install the Ubuntu unrestricted files, still no luck, as I'm sure you guessed, getting the mackinaclive.com site's video to play.  I'll looking Wine and Firefox - I'm assuming I install Wine for Ubuntu, then install the Windows version of Fire Fox?  (Obviously, I've only begun to use Ubuntu.. but it sure looks promising.. wow..)

---

### Post by serfcx on 2009-10-17
Not wishing to hijack but just stumbled on this thread and I am using Firefox 3.0.14 on Linux Mint Gloria, which is based on Ubuntu 9.04 and this link plays fine. Also plays well on Google chromium.

---

### Post by Andrews222 on 2009-10-17
Hi all,

I'm VERY new to Linux, but I have had Ubuntu 8.10 (I think) running on my desktop system and was unable to play streaming video from some sites.  There was a post I read in the forums that dealt with "all things video".  I executed a bunch of commands and then I was able to view Hulu and YouTube etc.

Fast forward to my recent installation of 64bit 9.04.  I installed the OS and everything went fine.  I can view YouTube vids but I can't view Hulu, I can't view the videos at MSNBC.com, can't view the vids at Yahoo.com.

Rather than go back to the old "Howto" i referred to earlier (which was based on an earlier 32bit version), I went to Adobe and downloaded the version 10 flash player for debian 8.04 (.deb file).  I installed that and it appears as an enabled plugin w/n Firefox.  Also listed as enabled is the version 9 plugin.

This made no difference.  The one hint I have is when trying to view a Yahoo video, I get a message inside the player window (image attached) that says things like server undefined, etc.  Any thoughts would be appreciated.

---

### Post by LuGRU on 2009-10-17
Hello,
I stumble upon this thread while optymizing my FF and at the begining I couldn't play that vid to. After awhile i figure out what was problem. So basicly vid on that site is a MMS stream, MP4S code find in Windows Media Player. To play it in FF I use mplayer plugin.
```
sudo apt-get install mozilla-mplayer
```But... before you will see a vid, You must first uninstall all other &quot;video player&quot; FF **plugins** (you can leave player itself, also going in ff tools->add-ons and disabling plugins didn't work in my case). In my case i did have VLC plugin and Totem. I dont know exactly how FF pick a proper player but Mplayer is at the bootom of that list (i instaled it lastly so maybe thats it?). After that vid plays like a charm. Side note here, mplayer will play most vid formats due to support of w32codecs.

To test if You mplayer will play that vid type
```
mplayer mms://74.208.123.60:5119/MainStreet
```I hope this helps.. and sorry for my lang, I'm to tired to check spellings [5am here ^^'].
Best regards

---

### Post by Nesaskewatch on 2009-10-17
Try here.

[https://answers.edge.launchpad.net/ubuntu/+question/34257](https://answers.edge.launchpad.net/ubuntu/+question/34257)

---

### Post by Andrews222 on 2009-10-18
Hey All,

I posted earlier about Flash not working for me on 9.04 (64bit).
I followed the instructions in this post:
[http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)
And, voila!  Every video I've attempted to view has worked like a charm.

But now I have Shirotok web browser (apparently firefox 3.5 64bit beta) AND the firefox 3.0.14 64bit BOTH on my system.  The older version still appears on my task bar.  Not a problem since they BOTH work now after simply installing 3.5.

I wouldn't mind having just one or the other but I'm inclined not to do ANYTHING that might screw things up. 

Any thoughts are appreciated.

---

### Post by king vash on 2009-11-01
above post solved my problem

---

