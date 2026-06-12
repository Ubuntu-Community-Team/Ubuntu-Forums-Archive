---
title: "Problem with GIMP tools"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by hatrack on 2009-04-25
Hi All !

I am experienced with image editing programs in general, having used both Adobe and Corel s/w for several years. However, about six months ago, I changed over my system to run Hardy. I am now shooting "Camera RAW" pictures and naturally, I would like to use GIMP, which integrates seamlessly with "UFRAW".   Unfortunately, some of the tools in GIMP are "broken" and just do not work, so I am forced to continue to use Windows to provide an environment for my graphic editing.  In particular, the "Clone" and the "Crop" tools do absolutely nothing ! 

I have searched on the Web but all sources of information that I have found assume that the tools in GIMP work !

I am running GIMP ver 2.4.x. I have been to the SorceForge site and find that the latest version is 2.6.x but ... when I try to get this using the recommended procedure (using 'apt-get install gimp' ) my system reports that I already have the latest version and refuses to download anything from Source Forge. I am afraid that I do not yet feel sufficiently confident to attempt compiling from source code so I'm looking for a binary package.

I have been struggling with this particular problem for over a month now and just cannot find any clues about solving it. Can anyone please offer any advice/comments/guidance ?

Many thanks in advance and best regards to all ...

---

### Post by WatchingThePain on 2009-04-25
Hi,

Might be best to uninstall then use the version from the repo's.
Hope this helps.

---

### Post by BslBryan on 2009-04-25
Also, GIMP, while having most every feature of Photoshop, still works differently with some things.  I was very frustrated with the crop feature, myself, until I figured out what I was doing wrong.  Try selecting Tools --> Selection Tools --> Rectangle select, select a bit of the image, and then Image --> Crop to Selection?

---

### Post by Tibuda on 2009-04-25
> **hatrack said:**
> I am running GIMP ver 2.4.x. I have been to the SorceForge site and find that the latest version is 2.6.x but ... when I try to get this using the recommended procedure (using 'apt-get install gimp' ) my system reports that I already have the latest version and refuses to download anything from Source Forge. I am afraid that I do not yet feel sufficiently confident to attempt compiling from source code so I'm looking for a binary package.
Your forum profile says you are using Ubuntu 8.04, right? I don't think Gimp 2.6 is in the repositories for that version. You can download a deb package for hardy in [http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

---

### Post by hatrack on 2009-04-26
My thanks to the three people who wrote wrote regarding my post. Rather than write three individual replies, I will do one blanket post, as follows --

To WatchinThePain -- I have tried your suggestion to de-install and then re-install several times over the past months but with no success.

To BslBrian -- I am afraid that your suggestion to get to "Crop" using Tools > Selection Tools > Rectangle Select does not work. As soon as I click on the image to begin the selection, the whole image area turns gray (as though it is outside the selection) and it is not possible to draw any cropping/selection rectangle at all. Also, it is not possible to exit from this condition and the only route to recovery is to close down the image window and start again.

When the Clone tool is selected, the icon initially has a small additional item consisting of a circle crossed by a diagonal line. However, upon doing Cttrl+Clk, the small target icon appears to indicate the selected source area but ... it is still not possible to then clone.

To Danielrmt -- I have been onto the site you kindly suggested and have satisfactorily down-loaded and installed GIMP Vers 2.6.x. Unfortunately, however, this does not fix my problems ... GIMP does not run correctly under Ubuntu Vers 8.04 ... which is crazy !

Since I was on to the site to get Vers 2.6.x, I also down-loaded the version of GIMP intended to run under Windows, since I also have a set-up running Windows 2000. According to the information on the site, Windows XP or Vista is required but I decided to try to use the existing environment, nevertheless.

GIMP works perfectly and both the Clone and Crop tools work exactly as they do in Photoshop (see comment on this point by BslBrian).

The only explanation that I can think of is that the tool set used under Ubuntu is corrupted. Does anyone know (a) Is this possible ? and (b) If so, how I can de-install and then re-install a "good" set ?

I repeat my thanks and best regards to all on this forum ...

---

### Post by benmoran on 2009-04-26
Try going to your home directory, and pressing Ctrl+h to show hidden files and directories. Look for a directory named .gimp-xxx (or similar). This is the configuration folder, and containes all the brushes and other configuration settings. I would try uninstalling Gimp, deleting this folder, then reinstalling the version from get-deb.net. 

I'm pretty sure the tool settings (and problems in your case) are NOT overwritten when you upgrade. Give my idea a shot, and let us know how it works out. 

-Ben

---

### Post by hatrack on 2009-04-26
> **benmoran said:**
> Try going to your home directory, and pressing Ctrl+h to show hidden files and directories. Look for a directory named .gimp-xxx (or similar). This is the configuration folder, and containes all the brushes and other configuration settings. I would try uninstalling Gimp, deleting this folder, then reinstalling the version from get-deb.net. 

I'm pretty sure the tool settings (and problems in your case) are NOT overwritten when you upgrade. Give my idea a shot, and let us know how it works out. 

-Ben
Many thanks Ben ... I'll try this later today and report this evening ... I've been up all night playing with this problem !

---

### Post by hatrack on 2009-04-26
Hi Ben !

I am very pleased to be able to report that the fix you suggested has completely cured the problems with GIMP. Not only do I now have the latest version of this running, I have also down-loaded and installed UFRAW and so I can now process my camera RAW files within a single integrated environment.

Since I have been struggling to get things working for some considerable time, it is fair to say that now "I am one very happy bunny" !

My thanks to all who replied to my post and (of course) to you in particular, as the one who proffered the fix.

Very best regards ...

---

### Post by Kellemora on 2009-04-26
Hi Ben

Just wanted to say thanks for the tip to HatRack there!

Were running Hardy on 6 machines and do a lot of graphics work using Gimp!

On one of the dual boot machines, after the Doze did a nosedive and needed to be reinstalled, although this shouldn't have anything at all to do with Ubuntu, in a round about way Nvidia got messed up and I think this in turn caused our tools to quit working in Gimp.

We have Nvidia working perfectly for Ubuntu now too, but for the Doze it can't remember it's settings.

After reading your take on fixing Gimp I gave it a try and now it's back to normal again!

So Thanks for your Solution!  It WERKED here too!

TTUL
Gary

---

### Post by hatrack on 2009-04-27
Hi Gary !

Reading your post has reminded me of a further idea that you might find useful in sorting out problems with dual-boot setups ...

When I began with Ubuntu about 6 months ago I, like you, created a dual-boot setup (Windows XP/Ubuntu Hardy). Someone told me then  that when doing this, Windows _must_ be installed first, giving it the whole of the hard drive. Only after this is done and tested OK can Ubuntu be installed. Apparently, Linux slaps Windows around until it "plays nicely". Ubuntu can (and does) correctly partition up the HD as required.  If you try to do it the other way around (or re-install Windows on a Linux machine) Windows gets awkward and messes up at least something.

I don't know enough yet to know whether or not this idea _is_ correct but ... during my experimental period, I did many re-installs, to sort out the crashes and general changed ideas that one has when setting up a completely new and strange Op Sys. Whenever it was necessary to change Windows, I re-installed _everything_ again from scratch and I have always had stability and correct operation of the various tools (except for my problem with GIMP which started this thread off ! ).

I know that it sounds a right pain to wipe out a perfectly good installation of Ubuntu, just to fix a Windows problem but, Ubuntu installs so easily that the extra effort is not really a very high price to have to pay. Just a thought ....

Best regards ....

---

### Post by Tibuda on 2009-04-27
Hatrack,

When you install Windows, it may keep the Ubutu partition, but it will mess GRUB. It is possible to recover it after you install Windows, without reinstalling Ubuntu. It is not a very user friendly task, but read this: [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by hatrack on 2009-04-27
Many thanks !

I did say in my post that I wasn't _sure_ that my procedure was mandatory ... just that it always worked. However ... I've gone over to Ubuntu 100% on this machine and networked another to it running just Win2k for my legacy stuff so, this problem wont arise again for me. But ... thanks anyway !

---

