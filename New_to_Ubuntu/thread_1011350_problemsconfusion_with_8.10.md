---
title: "problems/confusion with 8.10"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by frankwakeman on 2008-12-14
After thinking about it for a while, I've installed Ubuntu today, using the method of installing from Windows (Vista).  Looking this up, this may for all I know be a new way as some experts didn't seem to know about it.  Anyway, it's gone 75% well, with even my mobile Broadband working, display fine and so on.  Ubuntu is on the E partition, where Vista is on C.  Vista is still working, so all appears fine.

I don't understand yet how to get a program I downloaded started up, except for the ones that seemed to get installed automatically, like Flashplayer.  I look in the downloaded, extracted folder and there is no setup.exe as with Windows.  One program is the thing needed to get encrypted dvds working, ending css - these programs have uncatchy names so I've forgotten.

I have three dvd playing programs installed, including VLC, but dvds won't play.  I put the dvd in and get it to use VLC or the standard Ubuntu player but I get an error message, and it will ask if I'm trying to play a dvd without having installed the ......css program.

While my sound is working, it is quieter than with Windows even with everything turned up.  Is this a driver matter too?  The laptop has Realtek HD audio.

I have some driver finding 'jockey' software which I also have no idea how to start, which will apparently look for all the latest drivers.  When I look at the System - Hardware drivers bit it looks for installed drivers and says there are no installed proprietary drivers.  Should it say that?

With these things sorted out I think I'd be okay.  Any help is much appreciated.

My laptop is a Toshiba Equiuum L40 series, pretty new - 2 gig ram, 1.6 mhz, Intel 965 graphics.

I also have a Compaq Deskpro 886 mhz, 512 meg ram, nVidia TNT2 - my last question is would it run Ubuntu well (dual booting with Windows 2000), even if I have to use the 'no effects' display mode, which is no real hardship.

I imagine my installation method is frowned upon, but it _is_ offered by the live cd, so I thought I'd do it, and the 'slight disk reading performance issue' doesn't seem noticeable.  The method I used wouldn't have anything to do with the above problems would it?

Thanks in advance.

---

### Post by frankwakeman on 2008-12-14
I nearly forgot.  Can I disable all the password stuff.  Only I use this machine and at home.

I've also found when I try to use the terminal it asks for my password after I've typed a command line in (e.g. sudo........ [to install a program]), but then it won't let me type my password - nothing is typed, the cursor doesn't move, though it's blinking.

---

### Post by karlr42 on 2008-12-14
You password is being entered, there's just no visual confirmation. It's so others can't see the lenghth of your password. 
For sound, enter alsamixer in a terminal, and see if all the bars are set to max.
For DVDs, it's because you're missing the correct codecs, to get them:
sudo apt-get install ubuntu-restricted-extras
Then try play again

---

### Post by kansasnoob on 2008-12-14
> **frankwakeman said:**
> After thinking about it for a while, I've installed Ubuntu today, using the method of installing from Windows (Vista).  Looking this up, this may for all I know be a new way as some experts didn't seem to know about it.  Anyway, it's gone 75% well, with even my mobile Broadband working, display fine and so on.  Ubuntu is on the E partition, where Vista is on C.  Vista is still working, so all appears fine.

I don't understand yet how to get a program I downloaded started up, except for the ones that seemed to get installed automatically, like Flashplayer.  I look in the downloaded, extracted folder and there is no setup.exe as with Windows.  One program is the thing needed to get encrypted dvds working, ending css - these programs have uncatchy names so I've forgotten.

I have three dvd playing programs installed, including VLC, but dvds won't play.  I put the dvd in and get it to use VLC or the standard Ubuntu player but I get an error message, and it will ask if I'm trying to play a dvd without having installed the ......css program.

While my sound is working, it is quieter than with Windows even with everything turned up.  Is this a driver matter too?  The laptop has Realtek HD audio.

I have some driver finding 'jockey' software which I also have no idea how to start, which will apparently look for all the latest drivers.  When I look at the System - Hardware drivers bit it looks for installed drivers and says there are no installed proprietary drivers.  Should it say that?

With these things sorted out I think I'd be okay.  Any help is much appreciated.

My laptop is a Toshiba Equiuum L40 series, pretty new - 2 gig ram, 1.6 mhz, Intel 965 graphics.

I also have a Compaq Deskpro 886 mhz, 512 meg ram, nVidia TNT2 - my last question is would it run Ubuntu well (dual booting with Windows 2000), even if I have to use the 'no effects' display mode, which is no real hardship.

I imagine my installation method is frowned upon, but it _is_ offered by the live cd, so I thought I'd do it, and the 'slight disk reading performance issue' doesn't seem noticeable.  The method I used wouldn't have anything to do with the above problems would it?

Thanks in advance.

Please, in the future break things down into separate posts. It's easier on my aging brain :p

For the weak sound issue look at my post #3 here:

[http://ubuntuforums.org/showthread.php?t=1011367](http://ubuntuforums.org/showthread.php?t=1011367)

regarding gnome-alsamixer (ignore the rest). I just can't see reposting the whole thing.

Regarding the DVD issue I second the motion to install ubuntu-restricted-extras, but also for encrypted DVD's look here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

The installation type you used is referred to as Wubi. Nothing really wrong with it. I don't particularly care for it but thye only real serious "downside" I'm aware of is that it's horribly susceptible to hard shutdowns or power outages. Susceptible meaning you're quite likely to have to reinstall Ubuntu after such an occurence.

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


[http://wubi.sourceforge.net/faq.php](http://wubi.sourceforge.net/faq.php)

Lots of good info here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Paqman on 2008-12-14
> **frankwakeman said:**
> 
I don't understand yet how to get a program I downloaded started up

Downloading apps from the websites is not the main way we install software on Linux. We have enormous libraries of ready-to-go software called repositories. Open Applications > Add/Remove and have a browse, try System > Admin > Synaptic if you want even more.

If you do have to download something, you want to get a .deb file. That will simply click to install, like a Windows .exe but without the 50 pointless questions Windows asks you. 

> 
I have some driver finding 'jockey' software which I also have no idea how to start, which will apparently look for all the latest drivers.  When I look at the System - Hardware drivers bit it looks for installed drivers and says there are no installed proprietary drivers.  Should it say that?


Hardware Drivers is Jockey.

There not being anything listed in Jockey/Hardware Drivers is good. That means all your hardware is supported out of the box, without any need for proprietary drivers.

> 
I also have a Compaq Deskpro 886 mhz, 512 meg ram, nVidia TNT2 - my last question is would it run Ubuntu well (dual booting with Windows 2000), even if I have to use the 'no effects' display mode, which is no real hardship.


It would probably run Xubuntu better than regular Ubuntu. It's designed to be slightly more lightweight.

> 
I imagine my installation method is frowned upon

Not at all, Wubi rocks! I recommend it whenever I can.

---

### Post by frankwakeman on 2008-12-15
Thanks you three, now I only have the sound problem unsolved (although I did have OpenOffice hang this morning and am still thinking of doing a proper installation).

So if you have any other ideas about the sound, I'm all ears -  cheers.*

Lee

*That seems like the worst sentence I've ever typed.

---

