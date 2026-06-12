---
title: "lynx beta2 upgrade broke browser flash. HELP!"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by Vintage.Ritz on 2010-04-21
Two days ago, I jumped the gun and upgraded from KK to LL 10.04 beta2.  The installation seems to have gone fine EXCEPT for Firefox.  It appears that my flash is gone or messed up.  At minimum, photos, headers, etc. don't display and some text formatting is messed up.  For example, I had a very difficult time logging into these forums because the "Search" bar overlaps the "User Name" bar, making it impossible enter my login.  I was able to work around and login through Launchpad in order to post here.

Before I  installed LL, I was already running Firefox 3.6.3 from Ubuntuzilla, and it was working fine.  Since the upgrade, I've downloaded Flash from Adobe using the Ubuntu Software Center, but that didn't help.  I've removed and reinstalled Firefox.  I know that I'm missing something, and it's probably a simple something that links flash to Firefox, but I'm not savvy enough (yet) to know what it is and/or how to put it back together.  I'm pretty sure this is a relatively simple fix, if someone will just walk me through it.

I'm running a 32-bit system, and will try to provide any other system information you might need.  I'd REALLY like to have my regular internet back.

Thanks in advance.
Andee

---

### Post by HarrisonNapper on 2010-04-21
Are these problems only in Flash apps? Make sure you're using flash from the Adobe website (they offer a deb) although I suppose the one in the medibuntu repos might work fine. If the text formatting issues are in pages in general, you need to do this:

```
sudo dpkg-reconfigure firefox
```

Or just do a reinstall from Synaptic, I guess.

---

### Post by Vintage.Ritz on 2010-04-21
How would I know if they are only in flash apps?  I can tall you that YouTube doesn't display ANYTHING useful.  A lot of boxes where video should be.  Flickr is similar.  I have a blog through blogger, and neither my header nor any of my photos are visible.  When I uploaded my avatar here at the Ubuntu forum, I have faith that it is visible.  However, I can't see it.

---

### Post by HarrisonNapper on 2010-04-21
Yeah, sounds like more than just flash to me. Apart from a full reinstall, it might be a good idea to go back to Karmic until Lynx is officially released. If you do want to stick with the beta, before you mess with this stuff, you might check on Launchpad and Bugtraq to see if these issues have been reported as a bug.

---

### Post by Vintage.Ritz on 2010-04-21
Perfectly willing to roll-back, since I feel like such a dweeb right now anyway.  Not a clue how to do so.  And I will hop over and check for bugs (I did, but I will again).  Methinks this seems like something important that should be reported.

---

### Post by HarrisonNapper on 2010-04-21
If it is truly a bug, it definitely needs to be reported. Given the number of us that use FF, though, it would've been reported already. Rolling back is pretty simple. Just backup your home drive, get a LiveCD or LiveUSB, and format/install. Be sure to use the same user name in the new installation or it will cause permissions problems that may be a pain to fix.

If you do want to stick with it, start by using the reconfigure command I showed you on Firefox and see what progress can be made there.

---

### Post by Vintage.Ritz on 2010-04-21
I ran the command you posted earlier.  I got:

Please restart all running instances of firefox, or you will experience  problems.


This sounds terribly noob, but what does THAT mean?  Well, I mostly think I know what that means, but I closed Firefox and then ran the command, so that doesn't make any sense.

---

### Post by Vintage.Ritz on 2010-04-21
Thought I would try downloading a different browser and see if there was a problem.  Tried Epiphany first and get this error message:

Unable to load page
Problem occurred while loading the URL file:///usr/share/ubuntu-artwork/home/index.html
Error stating file '/usr/share/ubuntu-artwork/home/index.html': No such file or directory


Downloaded Chromium.  It works fine, no display issues at all.

---

### Post by Vintage.Ritz on 2010-04-21
I've got to go run a few errands, but I'll be back in a couple of hours.  Maybe someone will have a miracle for me?

---

### Post by HarrisonNapper on 2010-04-21
Sorry, open a terminal and type "sudo killall firefox" then issue the aforementioned command, which is "sudo dpkg-reconfigure firefox".

As for Epiphany, that just means you don't have the home page. Change the home page and it will be fine.

I usually highly recommend NOT using pre-release distros unless you've been around the terminal awhile. With Ubuntu, it tends not to be as much of an issue as with other distros, but you can still run in to problems like this. You can, in fact, run in to these problems using a production release, but they're less common.

---

### Post by lovinglinux on 2010-04-21
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Vintage.Ritz on 2010-04-21
I'm back.

Ran the terminal commands.  Here is the result:
Okay, can't paste the results, so I'll type them.  If there is a typo, it's from my copying, not from the terminal commands:

andrea@andrea-laptop:~$ sudo killall firefox
firefox: no process found
andrea@andrea-laptop:~$sudo dpkg-reconfigure firefox
Please restart all running instances of firefox, or you will experience problems
.
andrea@andrea-laptop:~$


As for not installing pre-release distros, I know (insert head-hanging shamed face here).  My long-distance, computer-geek son, the one who originally got me to try Ubuntu read me the riot act too.  And frankly, I didn't want to tell him any more than I wanted to come on the boards and ask for help :oP .  Really, it's okay though.  I deserve the razzing.  Hey, I'm learning a lot.  Does that make it any better?

The thing I can't figure out is why is this affecting ONLY Firefox flash, and only for me?  I'm not finding a similar bug report anywhere.  Maybe I'm not searching correctly.

Hmmm...maybe the answer can be found in the Firefox optimization and flash links provided in the next post by LovingLinux.  I should probably go check those out.  That's what I'll be doing, and I'll check back here to see if there is some weird revelation garnered from my terminal quote above.

---

### Post by HarrisonNapper on 2010-04-21
The links provided would be the ones to go with.

And to clarify, I'm not razing you and saying not to do it. As you can see, it's a great learning experience and it's what creates helpful people on the forums to reply to questions :)

Don't want to make you feel inferior for not being a linux expert, just recommending the most stable path from personal experience.

Cheers.

---

### Post by Vintage.Ritz on 2010-04-21
I've read the links provided by LovingLinux, and worked through the flash recommendations.  I've removed other, possibly conflicting flash installs (there weren't any), removed the Adobe flash plugin (which I DID have), and added the nonfree plugin.

No change.

I didn't run the tweaks yet, since it doesn't seem to make sense to tweak something that isn't working at all.  Correct me if I'm wrong, please.

The next step, "Compiz, Xorg, and Graphics tweaks," tells me to "make sure you have the proprietary graphics card driver installed.   Go to “System >> Administration >> Hardware Drivers” and   enable the corresponding driver."

There is no proprietary driver.  The only driver listed is my Broadcom wireless driver.  Is this important?  Without the proprietary driver, I didn't go on with those tweaks either.

I'm kind of at a standstill right now.  I'm thinking I should try the "Troubleshooting Firefox" steps outlined in LovingLinux's document, beginning with backing up my profile and working my way through.  If anyone has other recommendations, feel free to let me know.

As to the razzing, I didn't think you were.  It's just one of those moments when you realize you're in WAY over your head and maybe aren't quite as competent (or lucky) as you thought.  I don't mind jumping in and making the mistakes.  Shoot, everyone around me thinks I'm some kind of forward-thinking genius because I don't run Windows.  Little do they realize just how little I really know......it just happens to be slightly more than they do.

---

### Post by Vintage.Ritz on 2010-04-21
HAH!!!!!

Found it!!!!!!

:)

It's a bad profile.  LovingLinux, I may be LovingYou!!!!  Clean profile looks PRE-FECT.  Now I just have to go read more and figure out what's wrong and how to fix it.

---

### Post by Vintage.Ritz on 2010-04-21
Okay, bad prefs.js file.  I replaced it with the clean file from the test profile as per LovingLinux's[ Firefox Optimization and Troubleshooting]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1").  I think I still have some tweaks and definitely have to re-enter ALL my preferences as well as re-install several add-ons that I removed before I ever came the the forum.

Thank you, thank you, thank you so much.  I knew the right information had to be out there.  It's just in knowing where to find it.

Hmmm....now, lemme see if I can find the info that tells me how to get this marked "Solved" . . . . .

---

### Post by lovinglinux on 2010-04-22
> **Vintage.Ritz said:**
> HAH!!!!!

Found it!!!!!!

:)

It's a bad profile.  LovingLinux, I may be LovingYou!!!!  Clean profile looks PRE-FECT.  Now I just have to go read more and figure out what's wrong and how to fix it.

> **Vintage.Ritz said:**
> Okay, bad prefs.js file.  I replaced it with the clean file from the test profile as per LovingLinux's[ Firefox Optimization and Troubleshooting]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1").  I think I still have some tweaks and definitely have to re-enter ALL my preferences as well as re-install several add-ons that I removed before I ever came the the forum.

Thank you, thank you, thank you so much.  I knew the right information had to be out there.  It's just in knowing where to find it.

Hmmm....now, lemme see if I can find the info that tells me how to get this marked "Solved" . . . . .

:) You are welcome.

---

### Post by D351 on 2010-05-02
I'm having pretty much the same problem, though I don't see how you got it running. I updated to Lucid today and now flash doesn't work. I've tried all of the specific advice tried on this thread and had the same problems in trying to get it to work. However, I can't figure out what I'm supposed to do to fix prefs.js. Any help would be greatly appreciated.

---

### Post by lovinglinux on 2010-05-02
> **D351 said:**
> I'm having pretty much the same problem, though I don't see how you got it running. I updated to Lucid today and now flash doesn't work. I've tried all of the specific advice tried on this thread and had the same problems in trying to get it to work. However, I can't figure out what I'm supposed to do to fix prefs.js. Any help would be greatly appreciated.


Type **about[noparse]:[/noparse]plugins** in the address bar and copy the information about flash, then post it here.

---

### Post by D351 on 2010-05-03
video/flv 	Flash video 	flv 	Yes

I think I'm starting to see part of the problem...

---

### Post by lovinglinux on 2010-05-03
> **D351 said:**
> video/flv 	Flash video 	flv 	Yes

I was actually asking about the files and versions.

---

### Post by D351 on 2010-05-04
Well, I'm not sure what you mean, but I uninstalled flashplugin-installer, and now everything's fine. :)

---

