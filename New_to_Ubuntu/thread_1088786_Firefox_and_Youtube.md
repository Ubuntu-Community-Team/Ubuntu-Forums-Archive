---
title: "Firefox and Youtube"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by kerileigh on 2009-03-06
I have been having issues getting YouTube to work with Firefox. Iv installed and un-installed flash and java numerous times tried updated versions etc etc but nothing will work.

My screen shot shows what happens when i try to use YouTube in firefox.

I have just however installed Opera and this works fine with YouTube.

What are the issues with firefox?

---

### Post by linuxuser21 on 2009-03-06
It looks like it's to much for your computer to handle.  Flash is fine, if it wasn't Youtube gives you a message to install the latest Flash.

---

### Post by gandaran on 2009-03-06
right click that flash video window, does it say adobe flash player 10 or something else?

---

### Post by Malta paul on 2009-03-06
Try using 'DownloadHelper' down load it from the Mozilla Firefox sight
Have fun:D

---

### Post by jts0803odon on 2009-03-06
Is your system 64-bit? I haven't been able to fix Flash on Firefox either, but it seems to be an issue for many.

---

### Post by Rallg on 2009-03-06
If your Firefox is 3.0.7 (just released today), some users have reported various difficulties that they didn't see in 3.0.6.

---

### Post by Bearly Able on 2009-03-06
I had a very similar problem, which I finally solved by uninstalling the gnash mozilla plug-in.  It seems to have been a software conflict between that and Flash. I had help from folk in the forums; if you're interested, the thread is [here]("http://ubuntuforums.org/showthread.php?t=1085832").

---

### Post by kerileigh on 2009-03-06
Hello thanks for all the replys, according to package manager i have flash 10 installed :)

And i am using firefox 3.0.7

I have also been finding i can't use photobuckets uploaders this seems to be a problem for me in both firefox and opera (but reacts different in opera), maybe this is linked to my problems with YouTube also?

---

### Post by kerileigh on 2009-03-06
and i shall take a look as that thread :KS

---

### Post by randcoop on 2009-03-06
I have the same problem.  Every Youtube video results in a message the the video is no longer available.  Flash works perfectly on Youtube in Opera, but not Firefox.  And Flash works everywhere else in Firefox, just not Youtube.

I'm now using 3.0.7 Firefox, but had the same problem with 3.0.6  I did not have the problem in 3.0.5.  

It's weird, to say the least.

---

### Post by ClaytonOT on 2009-03-06
> **kerileigh said:**
> Hello thanks for all the replys, according to package manager i have flash 10 installed :)

And i am using firefox 3.0.7

I have also been finding i can't use photobuckets uploaders this seems to be a problem for me in both firefox and opera (but reacts different in opera), maybe this is linked to my problems with YouTube also?

I can't use my photobucket uploader from my main album screen, but if you go into the 'bulk uploader' which is the option right under the main single file uploader, you should be able to upload there. It might hang on initialization (you will need Java) but let it run for a few seconds. This method has worked for me aside from changing the resolution of the pictures. It seems no matter what option I pick from the list it'll always spit out a 640x???(dont remember the second dimension) picture.

I've ran into problems using flash on firefox in several occasions on my 64bit version at school, but on this laptop there hasn't been any issues.

---

### Post by kansasnoob on 2009-03-06
My thoughts:

Go to Synaptic and search "flash". Be certain that no "gnash" or "swfdec" is installed! But keep track of what you remove!

Next be sure you have "ubuntu-restricted-extras" installed - in fact - tick it for reinstallation! (Of course sub kubuntu or xubuntu if that's appropriate)

Then install the most recent "Flashblock", not the one from the repos! In Firefox just go to Tools > Add-ons > get add-ons and install the newest Flashblock (1.5.8+)!

Then restart Firefox. Still no joy?

Then I'd try the Mozilla build of Firefox using Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

I just like doing that anyway but it also "restores" the plug-in path so it might get you going!

Only my thoughts.

---

### Post by Gramps on 2009-03-06
I had that problem a while back and I think this fixed it

```
sudo apt-get install ubuntu-restricted-extras
```

You milage may very

---

### Post by kaligus on 2009-03-06
I just went through this thread from top to bottom and still cant get youtube to play.  I get

```
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 
```

and this is a new development today.

I also went through all of the other notes I have takne on getting youtube/flash to work previously with no luck.

Now running firefox 3.0.7 from the ubuntuzilla script on Intrepid 64 with no joy.

---

### Post by Ripose on 2009-03-07
You can try installing the 64 bit player manually.

**[How to Install Adobe Flash Player 64-bit on Ubuntu 8.10]("http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml")**

---

### Post by kaligus on 2009-03-20
I have given up and use Epiphany instead of FF anytime I want to see any flash now.

I have found several other sites that give a similar message about flash not being installed, while so far nothing has refused me service using epiphany.

This all makes my head hurt LOL a fork works fine but the original is borked... oh well.

---

### Post by kansasnoob on 2009-03-20
> **kaligus said:**
> I have given up and use Epiphany instead of FF anytime I want to see any flash now.

I have found several other sites that give a similar message about flash not being installed, while so far nothing has refused me service using epiphany.

This all makes my head hurt LOL a fork works fine but the original is borked... oh well.

If you're still using Gutsy you're in for a world of hurt!

Support for Gutsy ends very soon!

Also: Why drag up an old thread?

Please start a new thread.

---

### Post by leonardo_neo on 2009-03-20
I used to have the same problem. Yesterday a guy from the forum posted the solution for that, I tried, and it worked for me. You too can try that....

> 
Open a Terminal and put these in:

1 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
2 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
3 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

Hope this helps for the youtube issue......

Best of luck..... :D

---

