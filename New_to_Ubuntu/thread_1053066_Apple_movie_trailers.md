---
title: "Apple movie trailers"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2009-01-28
Hello all!
I have a question:can you watch movie trailers on apple.com?All I see is a black screen and a small white text with "no video".... :(

---

### Post by zika on 2009-01-28
> **Troll_the_Great said:**
> Hello all!
I have a question:can you watch movie trailers on apple.com?All I see is a black screen and a small white text with "no video".... :(
that's my main test site for any change in configuration. great movies ... ;)

---

### Post by philinux on 2009-01-28
> **Troll_the_Great said:**
> Hello all!
I have a question:can you watch movie trailers on apple.com?All I see is a black screen and a small white text with "no video".... :(

Watching the SD trailers no problem with the totem plugin. HD nothing happens. If I copy the link location into vlc it works for a while then freezes, same with mplayer, but totem has a better go at it.

---

### Post by Bablefish on 2009-01-28
I have been trying to get Quicktime vids to run on my computer for more than a year. I say your goal is impossible. I can get some quicktime mov files to play but not all. Look for anything that either uses flash or windows media, those work. Remember Apple hates Linux for some reason.

---

### Post by SunnyRabbiera on 2009-01-28
> **Bablefish said:**
> I have been trying to get Quicktime vids to run on my computer for more than a year. I say your goal is impossible. I can get some quicktime mov files to play but not all. Look for anything that either uses flash or windows media, those work. Remember Apple hates Linux for some reason.

Indeed, the only real way I have been able to get the vids to work is to install wine and then install firefox under wine and then try to install quicktime for windows...
But you may need an older version as the latest has issues with Wine.
@$%^& apple

---

### Post by Troll_the_Great on 2009-01-28
> **philinux said:**
> Watching the SD trailers no problem with the totem plugin. HD nothing happens. If I copy the link location into vlc it works for a while then freezes, same with mplayer, but totem has a better go at it.

How do you watch the movies with the totem plugin?

---

### Post by zika on 2009-01-28
> **Bablefish said:**
> Remember Apple hates Linux for some reason.
no it doesn't, at least applemovies. at this moment I'm driving my machine (8.10, 64bit, ATI HD3650, 64bit flash) without any video driver (a different story about how new kernel killed fglrx driver) and still I can watch these movies without a glitch.

---

### Post by Troll_the_Great on 2009-01-28
> **zika said:**
> no it doesn't, at least applemovies. at this moment I'm driving my machine (8.10, 64bit, ATI HD3650, 64bit flash) without any video driver (a different story about how new kernel killed fglrx driver) and still I can watch these movies without a glitch.

  Lucky you, I'm using Hardy with all the codecs installed (I think) and with the correct video drivers and all I see is a black screen (like I said).
  By the way, you could use EnvyNg to install your ATI drivers.Let me know if you need help with that.
Cheers!

---

### Post by SunnyRabbiera on 2009-01-28
> **Troll_the_Great said:**
> Lucky you, I'm using Hardy with all the codecs installed (I think) and with the correct video drivers and all I see is a black screen (like I said).
  By the way, you could use EnvyNg to install your ATI drivers.Let me know if you need help with that.
Cheers!

Thats why I just cheat and use wine in those occasions.

---

### Post by philinux on 2009-01-28
> **Troll_the_Great said:**
> How do you watch the movies with the totem plugin?

I just click one of the Standard Definition links. I've included my plugins page.

---

### Post by UbuntuNerd on 2009-01-28
I made this guide just for that purpose check it out let me know if it worked for you( some pc's are just not capable)
[http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem]("http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem")

---

### Post by zika on 2009-01-28
> **Troll_the_Great said:**
> By the way, you could use EnvyNg to install your ATI drivers.Let me know if you need help with that.
Cheers!

I'm fine now. thank You very much for Your offer, I'll keep it in my mind. for now I'll try to make myself not to meddle to much (which is difficult and against my nature) and not to try ATI driver ... but I am pretty sure that if I wanted it would work well. I've cleaned my system from any instance of fglrx and after scrolling through Xorg.0.log I've found that radeon is used but is not mentioned in xorg.conf. adding a single line *Driver "radeon" *could make that official but I like it this way, at least today ... ;)

did You make X11 default option for Your video? (System->Preferences->Multimedia_Systems_Selector->Video->X11(no xv))

---

### Post by SunnyRabbiera on 2009-01-28
> **shipshape said:**
> Its right that sometimes Apple does deny linux to access its movies. You may try PCLOS/Firefox with media player plugin. should work fine with it.

This is almost universal though on any distro with multimedia, only PCLOS has media codecs preinstalled, but they are easy enough to get with some knowhow.

---

### Post by Troll_the_Great on 2009-01-28
> **UbuntuNerd said:**
> I made this guide just for that purpose check it out let me know if it worked for you( some pc's are just not capable)
[http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem]("http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem")

I tried your guide and I can watch trailers on Yahoo but still the same problem on apple...Any other ideas?

---

### Post by Troll_the_Great on 2009-01-28
> **philinux said:**
> I just click one of the Standard Definition links. I've included my plugins page.

I don't know what do you mean when you say you "click one of the Standard Definition links".I have all the plugins in your page and more....

---

### Post by philinux on 2009-01-28
Have tried "right click" save link as or copy link location and paste it into vlc,mplayer or totem?

Post a pic of your installed FF plugins.

---

### Post by Troll_the_Great on 2009-01-28
> **philinux said:**
> Have tried "right click" save link as or copy link location and paste it into vlc,mplayer or totem?

Post a pic of your installed FF plugins.

Those are my installed plugins.

---

### Post by philinux on 2009-01-28
Looks like you got too many installed thats why you get black screen. Get rid of the vlc and mplayer plugins.

---

### Post by UbuntuNerd on 2009-01-28
I agree with philinux , get rid of the vlc and mplayer plugins then try it

---

### Post by Troll_the_Great on 2009-01-28
> **UbuntuNerd said:**
> I agree with philinux , get rid of the vlc and mplayer plugins then try it

I think we are getting somewhere.I disabled the 2 plugins and now I see just a black screen, without the writings =))
Other ideas?

---

### Post by philinux on 2009-01-28
Lets have another look then, post your plugins again. Tools>addons>plugins tab.

[edit] oh and restart FF.

---

### Post by UbuntuNerd on 2009-01-28
here what mine looks like, im also trying to get a screen shot of the apple website which plays fine, but when I take the picture is in half.

---

### Post by Troll_the_Great on 2009-01-28
> **philinux said:**
> Lets have another look then, post your plugins again. Tools>addons>plugins tab.

[edit] oh and restart FF.

Here you go!

---

### Post by UbuntuNerd on 2009-01-28
I bet all the plugins you have are interfering with each other try getting down to what mine looks like unless you need the other plugins for other reason and set totem as you default player and then try it, post back if it worked

---

### Post by Troll_the_Great on 2009-01-28
> **UbuntuNerd said:**
> I bet all the plugins you have are interfering with each other try getting down to what mine looks like unless you need the other plugins for other reason and set totem as you default player and then try it, post back if it worked

I did what you said, and still nothing...:(

---

### Post by UbuntuNerd on 2009-01-28
as weird as this may sound I have 3 different computers I try things on while trying to play apple trailers on all of them i found out that after adding other plugins and then removing them make the trailers from apple not play, maybe they left some other dependency or something behind, but after doing a fresh install on the same pc and adding just the plugins i have now everything work fine.
I just went to the apple website and finally got some screen shots:

---

### Post by Troll_the_Great on 2009-01-28
> **UbuntuNerd said:**
> as weird as this may sound I have 3 different computers I try things on while trying to play apple trailers on all of them i found out that after adding other plugins and then removing them make the trailers from apple not play, maybe they left some other dependency or something behind, but after doing a fresh install on the same pc and adding just the plugins i have now everything work fine.
I just went to the apple website and finally got some screen shots:

That is weird... So what can I do (except a fresh install)?

---

### Post by UbuntuNerd on 2009-01-28
the only thing I can think of is trying to clean up some of the things left behind by all the other plugins, but that can be a pain. try going to synaptic and see if you have any residual files and get rid of them also google around to see if there's is a way to clean or purge the specific codecs you unistall.

---

### Post by Troll_the_Great on 2009-01-29
> **UbuntuNerd said:**
> the only thing I can think of is trying to clean up some of the things left behind by all the other plugins, but that can be a pain. try going to synaptic and see if you have any residual files and get rid of them also google around to see if there's is a way to clean or purge the specific codecs you unistall.

How do I see the residual files?Any other ideas?And if this won't work, do you know a good movie trailer site (like apple)?

---

### Post by UbuntuNerd on 2009-01-29
I know some people like the apple website but I go to this site and is way better than apple, you can get info on movies before they ever come out:
[http://www.movieweb.com/]("http://www.movieweb.com/")

if you want to get rid off residual files and clean other things check out this guide:
[http://my.opera.com/ubuntunerd1/blog/2008/12/26/keeping-ubuntu-clean]("http://my.opera.com/ubuntunerd1/blog/2008/12/26/keeping-ubuntu-clean")

---

### Post by Troll_the_Great on 2009-01-29
You mean I can completely remove all the files I find in "Not Installed (Residual config)"?

I have allot of them...

---

### Post by UbuntuNerd on 2009-01-29
yes removed all of them, if you have install and uninstall lots of things and upgraded several times you will have things like dependencies and maybe other installer files left behind. this is a feature included in Synaptic Package Manager think of it as kind like "defragmenting" but is not also if you follow the guide I gave you,  you also have other things you can be cleaning that you don't need.

---

### Post by Troll_the_Great on 2009-01-29
I cleaned 180 packages!Allot of stuff I didn't need... What does "Installed (local or obsolete)" means?

---

### Post by UbuntuNerd on 2009-01-29
Packages that do not belong to any of your repositories will show up in
this section, for example this is what I have in mine and is because I downloaded "Opera" from their website instead of the Ubuntu repositories, I will leave them alone.

---

### Post by UbuntuNerd on 2009-01-29
did you install localepurge, after installing anything with apt-get install, localepurge will remove all translation files and translated man pages in other languages you cannot read.

also Install gtkorphan, you probably have a million "Orphaned package" you don't need.

---

### Post by Troll_the_Great on 2009-01-29
I installed GtkOrphan but I'm not sure how to use it.Can I delete all files in the "Orphaned packages" category? I have an option "Show all orphan packages, not only those in the libs section".What does it do? Can I switch it on?
And about configuring localpurge.My installation of Ubuntu is in English.Should I choose just "en" from the list?

---

### Post by pritamps on 2009-01-29
You should follow the instructions in this excellent guide. Follow it step by step for your version of Ubuntu only:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

It is slightly long, but it has answers to all your questions and many questions you and I haven't even asked yet ;-)

---

### Post by UbuntuNerd on 2009-01-29
the guide provided by pritamps is excellent you should check it out, but it could also be confusing just take your time.

---

### Post by Troll_the_Great on 2009-01-29
> **UbuntuNerd said:**
> the guide provided by pritamps is excellent you should check it out, but it could also be confusing just take your time.

Hmm....I will try, but I have some very important exams next week (I am getting my ATPL - Airline Pilot Transport License) so I don't have too much time now.Isn't there a quick answer to what I asked?
Also I find a package called "quicktime4linux" here [http://linux.softpedia.com/get/Programming/Libraries/Quicktime-for-Linux-257.shtml](http://linux.softpedia.com/get/Programming/Libraries/Quicktime-for-Linux-257.shtml) but I can't install it... :(
Would it help in my case?

---

### Post by UbuntuNerd on 2009-01-29
as far as I know all the Orphaned packages are no longer use by your computer but Im not 100 percent sure, but I do remove all of them all the time until is clean and my computer has never crash because of it. Sometimes you might have to deleted the same files a couple times, the none-Orphaned packages leave alone.

---

### Post by Troll_the_Great on 2009-01-29
> **UbuntuNerd said:**
> as far as I know all the Orphaned packages are no longer use by your computer but Im not 100 percent sure, but I do remove all of them all the time until is clean and my computer has never crash because of it. Sometimes you might have to deleted the same files a couple times, the none-Orphaned packages leave alone.

And do you checked the option "Show all orphan packages, not only those in the libs section"?

---

### Post by eddietours on 2009-01-29
can you click on apple trailer and then use new tab it always work for me sorry if this already posted

---

### Post by UbuntuNerd on 2009-01-29
only check the "show unistalled packages with orphan configuration files"

---

### Post by Troll_the_Great on 2009-01-30
Thanks guys (especially pritamps and UbuntuNerd), I manage to make my apple trailers work (though a little different than in the tutorial).By the way, what happened to the "thank" icon? I tried to give you a "thank you" but is gone....
I would require a little more help in configuring "localpurge".So, if someone can, please guide me step by step.

---

### Post by Troll_the_Great on 2009-01-31
OK, I will mark this thread as solved, and open a new one with questions concerning "localpurge" and "deborphan".
This guide [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) was excellent but I did something a little different:the guide instructed me to paste "QuickTime Plug-in 7.0 / 7:$" directly above "QuickTime Plug-in 6.0 / 7:$" but for me it didn't work so I erased "QuickTime Plug-in 6.0 / 7:$" and kept only "QuickTime Plug-in 7.0 / 7:$".I offered this explanation for those who might need it.
Thanks again to all who tried to help me!

---

### Post by Troll_the_Great on 2009-08-22
Hello again guys!

I have again troubles with apple trailers and I thought to post here, rather than opening a new thread.
Now the problem is that when I try to play a movie I get the message:
```
Failed to open /tmp/<html>
```
I attached a print screen for you to see what I mean.
Any ideas?

---

### Post by philinux on 2009-08-22
snap same here. vlc totem no play.

---

### Post by philinux on 2009-08-22
Error

Must have missed this thred.
[http://ubuntuforums.org/showthread.php?p=7820472](http://ubuntuforums.org/showthread.php?p=7820472)

---

### Post by mondalaci on 2009-10-24
Apple has made some countermeasures in the last months.  I've written a guide on how to make Apple trailers play on Linux:

[http://monda.hu/blog/2009/10/24/how-to-watch-apple-movie-trailers-on-linux-part-2/](http://monda.hu/blog/2009/10/24/how-to-watch-apple-movie-trailers-on-linux-part-2/)

---

### Post by samh785 on 2009-10-25
> **Troll_the_Great said:**
> Hello all!
I have a question:can you watch movie trailers on apple.com?All I see is a black screen and a small white text with "no video".... :(
The apple HD trailers didn't work for me with jaunty, but now that I'm using karmic they do for some reason. *shrug*

[[IMG]http://img194.imageshack.us/img194/9641/screenshotit.th.png[/IMG]]("http://img194.imageshack.us/i/screenshotit.png/")

---

### Post by zika on 2009-10-25
It is sort of a rollocoster, it works today and after several days when I come back it doesn't. It worked this week and it works today. It seems like a struggle.

---

