---
title: "Sound themes in Ubuntu"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by JordyD on 2009-01-18
I've been playing around with themes from [gnome-look.org]("http://gnome-look.org/") and I noticed several of them have their own sounds. So after downloading some, I fished around for a place to switch/install themes. I found that there was a "Sound" application under System >> Preferences, and it had a drop-down for switching sound themes, but no option to install new ones...

So I was wondering if anybody could tell me how I could install this sound theme, or if it's even possible (the drop-down seems to suggest that it is).

Thanks,
Jordy

---

### Post by swoody on 2009-01-19
I've Googled in the past quite a bit, and have come to the conclusion that it's not easy to swap to a custom sound profile. Although, I was able to switch to Ubuntu Studio sound theme from the drop-down box you had mentioned after I installed that package.

If you're trying to do something custom, I think you would have to do it the hard way, and save all the sound files you want to use to one folder, then double-click on the sound action in the menu at the bottom of that window and select 'Custom'. Then you can find where you saved your sound files, and select the file you want. I included a screenshot to show you what I mean.

Let me know if you have any problems using this method!

---

### Post by JordyD on 2009-01-19
Thanks for your help. There were no problems and that picture really helped.

---

### Post by swoody on 2009-01-19
*SOUNDS* good! (get it?:)) Glad I could help :D

---

### Post by the8thstar on 2009-01-19
How did you get the sound themes to play? They don't work on my system (but all the other sounds do)

---

### Post by swoody on 2009-01-19
Are all the options selected like in my screenshot above? If they are, try turning up your volume a little, and put an ear to a speaker. Can you hear *anything* from the sounds? The sound theme is extremely quiet on my laptop, so I disabled sounds on there to save system resources. If you can't hear anything, try uninstalling and reinstalling 'ubuntu-sounds' in your Package Manager and see if that helps at all.

Post back here what results you get :)

---

### Post by AZorin on 2009-05-05
Is it possible to cerate your own sound scheme and install it? I am making an operating system called Zorin OS based on ubuntu and I am making a sound scheme.

---

### Post by swoody on 2009-05-05
What you may want to try doing is to take your sounds, and name them with the exact same names as Ubuntu's sound files. Then just replace Ubuntu's sound files with your own. That way you can use the "Ubuntu theme" name, but just replace the sounds it makes.

---

### Post by Dirjel on 2009-05-09
> **swoody said:**
> Are all the options selected like in my screenshot above? If they are, try turning up your volume a little, and put an ear to a speaker. Can you hear *anything* from the sounds? The sound theme is extremely quiet on my laptop, so I disabled sounds on there to save system resources. If you can't hear anything, try uninstalling and reinstalling 'ubuntu-sounds' in your Package Manager and see if that helps at all.

Post back here what results you get :)

So.  That went poorly.

I tried to uninstall and reinstall the ubuntu-sounds package, because my sound theme was not working as I want it to.  When I removed that package, though, it wanted to take the ubuntu-desktop package with it.

No big deal, I thought.  I'll just reinstall it along with the ubuntu-sounds package.  HOWEVER, neither synaptic nor apt-get will retrieve the packages for me.  They ask me to "please insert the disc labeled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter."  That is not an option, as I do not possess such a disc.  I have the .iso files for both the desktop and alternate install CD's on my hard drive, and I tried mounting both of them, but apparently those are not the CD's the package manager is looking for.

So.  Nothing is overtly broken, but I think I would like very much to get the ubuntu-desktop package back on my system.  It sounds... important.

EDIT:  Nevermind, I got it fixed.  Used the handy dandy Ubuntu Package Search that came with Firefox, and was able to find the ubuntu-desktop package online.  Downloaded and installed the .deb manually, and life is great.  It even put the ubuntu-sounds package back by itself, and now my sounds are doing what I want!

---

### Post by swoody on 2009-05-09
> **Dirjel said:**
> neither synaptic nor apt-get will retrieve the packages for me.  They ask me to "please insert the disc labeled
 'Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)'
in the drive '/cdrom/' and press enter."

It sounds like you still have your Live CD as a repository. Try going to "System">"Administration">"Software Sources" it'll ask for your password, so enter it and hit enter to continue. Then on the new window that popped up look under "Installable from CDROM/DVD" and make sure the liveCD in there is unselected - the box by it is not marked. If it is, unmark it. Then be sure that all the choices above that are marked - Main, Universe, Restricted, and Multiverse. Click on the close button, and it should ask to to reload your repositories. Allow it to reload, and you should be set. Just for kicks and grins, you can try installing something through Synaptic to be sure that it works now, and doesn't want to use your disc to install new packages. You can try xchat, removing and reinstalling "ubuntu-sounds" again, or just any other package to test it out. It should download it from the internet by itself this time :)

> So.  Nothing is overtly broken, but I think I would like very much to get the ubuntu-desktop package back on my system.  It sounds... important.

Actually the "ubuntu-desktop" is a meta package. It doesn't contain/remove anything, but it just makes sure that all the rest of the packages you need are installed. So you can remove it without any ill side effects, but obviously I'd recommend having it installed :)

---

### Post by Dirjel on 2009-05-09
> **swoody said:**
> It sounds like you still have your Live CD as a repository.

Oh yeah.  Duh.

*facepalm*

I don't know why mounting the iso wasn't satisfactory, though.  It worked before, when I was working on Intrepid a while back.  Oh well.

I have it disabled now.  Thanks.

---

### Post by swoody on 2009-05-09
No problem! It's usually those simple things that we always tend to overlook :)

---

### Post by camalion357 on 2009-05-09
Cool, I'll try that to see how it works for me, an see if i can do it
            
                                                   Thanks for the tip

---

### Post by swoody on 2009-05-09
camalion357 - What issue are you having? If you can't get it worked out from the above, you may have better chances starting your own thread about it :)

---

### Post by Andrew_P on 2009-06-12
> **swoody said:**
> If you're trying to do something custom, I think you would have to do it the hard way, and save all the sound files you want to use to one folder, then double-click on the sound action in the menu at the bottom of that window and select 'Custom'. Then you can find where you saved your sound files, and select the file you want. I included a screenshot to show you what I mean.

It appears as if sound theme management in Gnome, well ... sucks.:(  Microsoft had this problem licked in Windows 95 -- that's 15 years ago, gang!

The Default sound theme doesn't have files for every system event or action.  For example, it has nothing for "New e-mail".  If I add a custom file and point to it in the Sound Preferences dialog box, *it kills all the other sounds in the Default Theme*.  In other words, if you manually add *one* custom file, you need to manually add *all* custom sound files, and Gnome still doesn't provide a way to save it by name as a theme.  Windows 95/98 etc. would recognize that one file had been changed or added in a pre-installed theme, would keep all the pre-existing sound files in the theme, and give the opportunity to save the new set of files as a custom theme.  Even if the user didn't choose to save the customized theme by name, it would still remember it from session to session.

:idea:That said, in the absence of a built-in, user-friendly way of creating and saving sound themes, what's needed is a complete, step-by-step howto document to allow users to create new themes and splice them into the system so that they appear in the drop-down menu along with the Default sound theme.  Given a good set of instructions, even a novice should be able to do it.

---

### Post by edwardtilbury on 2009-09-17
yes, sound themes would be awesome

---

### Post by dubski on 2009-09-17
How painfull.  I remember this was possible in 1998 with winblows.  Seems like a simple enough feature.  The sounds themes are available, but there is no easy way to change all your sounds as there is for visual themes.

---

### Post by nortexoid on 2009-11-28
It appears in Karmic that you can't even manually change sound events to custom ones besides the alert sound. Lame!

---

### Post by spsf on 2009-12-16
> **nortexoid said:**
> It appears in Karmic that you can't even manually change sound events to custom ones besides the alert sound. Lame!

Agreed...
It's a shame for gnome...

---

### Post by n2sins on 2009-12-20
i thought my sounds were broken as i dont get a preferences screen at all..  it had it in  jaunty.. whats the deal.. ? i cant specify mail sounds or opening or closing windows.. or anything i have like 5 themes.. 1 is a dog bark.. what the heck.i have a bad sense of humor but come on now.. i am attaching screenshot.. maybe mine is broken and i dont get it..if it is broken and someone could tell me why i have no preferences tab anymore i would be grateful.. but anyway.. if i cant get to choose my sounds.. open sources freedom of  choice is  getting windowized.. and no one should be victimized like that

---

### Post by n2sins on 2009-12-20
heres a screenshot

---

### Post by swoody on 2009-12-21
Yeah, it's too bad really, but Gnome has removed the ability to change most of your sound theme settings. It only gives you the option to select different sound themes in general, and to select your 'alert sound'.

---

### Post by Djlatino on 2009-12-27
> **swoody said:**
> Yeah, it's too bad really, but Gnome has removed the ability to change most of your sound theme settings. It only gives you the option to select different sound themes in general, and to select your 'alert sound'.
But all the sounds are in /usr/share/sounds!
whenver i try and overwrite it, it say permission denied
is there a way to get into the root user?
EDIT: i put in gksudo nautilus and it got me root access :) then i copyed and pasted the .wav files :D

---

### Post by JoshuaOrtega on 2011-08-25
> **swoody said:**
> I've Googled in the past quite a bit, and have come to the conclusion that it's not easy to swap to a custom sound profile. Although, I was able to switch to Ubuntu Studio sound theme from the drop-down box you had mentioned after I installed that package.

If you're trying to do something custom, I think you would have to do it the hard way, and save all the sound files you want to use to one folder, then double-click on the sound action in the menu at the bottom of that window and select 'Custom'. Then you can find where you saved your sound files, and select the file you want. I included a screenshot to show you what I mean.

Let me know if you have any problems using this method!
my sound preference does not look like this. I am using 11.04 Natty, and none of the customized sound themes work. only the default. I know it is petty complaint, but damned if I dont want to have my ubuntu to work completely. I got ubuntu because Microsoft can kiss it. UBUNTU RULES!!!!!!!!!!!

---

