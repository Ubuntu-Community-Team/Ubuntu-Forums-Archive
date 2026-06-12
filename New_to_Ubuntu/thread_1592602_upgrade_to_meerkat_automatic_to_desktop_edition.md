---
title: "upgrade to meerkat automatic to desktop edition"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by mikhaell on 2010-10-10
Hi, i have a netbook and when upgraded, it automatically upgraded to the desktop edition. ANy way I can switch to unity?

---

### Post by zaivala on 2010-10-10
I don't even know WHAT mine upgraded to -- I have a blank, black screen.  I can get to Terminal, but don't have a clue what to run to get back to my desktop.  (Also was running UNE 10.04)

---

### Post by andrewthomas on 2010-10-10
I think the package name is ubuntu-netbook
 
 
do a 
 
```
 
aptitude search netbook 

``` for the package name

---

### Post by zaivala on 2010-10-10
I typed 'unity' in my Terminal, and was told "unity is not installed; type sudo apt-get unity"

I did that... 

Ya know, Canonical put an extra space in their address, /_maverick ... I'm getting "Something wicked happened resolving 'us.archive.ubuntu.com:http' -5 no address associated with hostname."

The hostname being asked for is 

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main unity ...

See the extra space?  Well, whether that's the problem or whatever is, it's still trying and failing to connect to get the file(s).

Moss

---

### Post by zaivala on 2010-10-10
andrewthomas:

I did a Search as stated (aptitude search ubuntu-netbook)

It gave me a list of packages, such as ubuntu-netbook.

I tried sudo apt-get install ubuntu-netbook.

Guess what?

"Something wicked happened... "

---

### Post by andrewthomas on 2010-10-10
> **zaivala said:**
> andrewthomas:
 
I did a Search as stated (aptitude search ubuntu-netbook)
 
It gave me a list of packages, such as ubuntu-netbook.
 
I tried sudo apt-get install ubuntu-netbook.
 
Guess what?
 
"Something wicked happened... "
 what?

---

### Post by zaivala on 2010-10-10
See my previous post for the complete discussion of what wicked happened.

---

### Post by zaivala on 2010-10-10
OK, for giggles I tried sudo apt-get install ubuntu-netbook again.  This time it worked (they must have fixed it, I tried several times before).

Then when it booted it said that I was missing a driver for Unity (which driver, it didn't say, and what to do about it was also ambiguous)... and then loaded Gnome Desktop.

Don't get me wrong, I like Gnome Desktop.  But this computer really does not have the resources to run it (1 GHz Athlon, 0.5 Gb RAM maxed out).  So I'd like my Netbook back... without losing my settings... and don't remember how to do a rollback, and can't find that information here.  Maybe I'll have to do a new install with the 10.04 disk, but I'd like to give someone the time to tell me what my peabrain needs to know to avoid that.

Moss

Update: After checking for updates/upgrades, and downloading everything I could on Unity through Synaptic, I still am running Gnome desktop and still do not know why.  It is running better than it did under 10.04, which is a blessing.

---

### Post by zaivala on 2010-10-23
I have yet to get Unity to load and run.  There is something missing, and even in Synaptic I can't get it.

This machine worked well in Lucid with UNE... in Maverick with GNOME, the processor, with nothing loaded except the desktop and Firefox, is almost constantly running at 100%.  The RAM is fine (even though it's only 512 Mb) and the swapfile doesn't seem to be writing anything, but the processor is running and running, and the computer is, of course, getting hot.

I've tried Xubuntu in Lucid, and XFCE just didn't hang on... I was reloading the desktop, usually from Terminal, and not even getting all the features then.  I have not tried Lubuntu, I don't know the interface at all and it's not "official" yet.

The laptop itself is "not upgradable" (according to Sony) or "everything is upgradable on this machine" (according to owners of the device).  I can, in theory, move from the 1.0 GHz Athlon 4 to a 1.2 GHz similar chip.  Some people say I may need to update the BIOS.  But would that be sufficient to give me the processor power I apparently need?  

To be honest, I thought about starting a new thread, but there was one already... with about 12 responses, and written back when people were using Hardy and Jaunty.  Anyone want to put in their two cents?

---

### Post by cariboo on 2010-10-23
With low resources like what your system has, I don't think Unity will ever run properly. See [this]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements") page for hardware requirements.

---

### Post by zaivala on 2010-10-23
> **cariboo907 said:**
> With low resources like what your system has, I don't think Unity will ever run properly. See [this]("https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements") page for hardware requirements.

Could be the problem.  But the page you referred me to was for UNE 10.04... which ran on this computer pretty well.  Maybe I should go back to 9.10 UNR?

As I said, Xubuntu 10.04 ran on this machine, as it should, but I kept losing the desktop and brining it back was not consistently successful.  Maybe I should try Lubuntu ... ?

GNOME under 10.10 also should not run on this computer, but I'm not having problems with resources, only processor.

---

### Post by zaivala on 2010-10-23
I just added LXDE to my computer... and ran it... and it didn't connect my modem.  It told me that I had to activate the modem driver.  OK, no problem... except it wanted to go to the website to activate the driver.  Can you say "Catch-22", boys and girls?  I knew you could.

---

### Post by Terry Maker on 2010-10-27
As a newbie, I have been running an old "Millennium" Era Clevo 5100s, 30Gb HDD, 750Mhz Processor, 512Mb RAM, 32Mb Video Memory, with Linksys wireless connection to Broadband, first on *"Karmic Koala"*, and then on *"Lucid Lynx"*, and all was fine. It's my Ubuntu 'test bed'.

As there has always been a 'problem' with both of these, and the screen size of the 5100s, (*on the best settings, they are slightly too large, but acceptable, it just means a lot of drag and drop!)*, I read that *"Maverick Meerkat-netbook"*, was there to overcome the 'problem'. So I went for the 'upgrade'.

The 'upgrade' turned out to be the desktop version, and nowhere could I find a way to install the Netbook version. What the Hey! it worked fine, with the 'old problem. 

After two days it crashed irretrievably, and I had to reload *"Karmic Koala"*, and then *"Lucid Lynx"*, *(I only have a boot disc for [I]"Karmic"*!)[/I], and I am now back up and running with *"Lucid"*, and just as before. 

Another drawback is that the age of the laptop precludes booting from USB, and only boots from CD, or FDD, and all of the 'Live' CD's available were the "Have Windows, try this" type", and I did not want to put XP back on the 5100S only to take it off again.

Then I found the system requirements page! 

No way was *"Meerkat"* ever going to run on the 5100S, 

Sooooo! 

Does anyone know how I can get the *"Lucid Lynx"* desktop to fit a 12" LCD screen?

Terry M

---

### Post by zaivala on 2010-10-27
Either Karmic Ubuntu Netbook Remix or Lucid Ubuntu Netbook Edition should run on that computer -- although you are stretching it, as UNE claims to need 1 Gb of RAM.  I run it fine on my 2001 Sony Vaio, with only 512 Mb.  If you need something lighter, you can try Xubuntu or Lubuntu (the latter is not official yet)... my problems with Xubuntu was that the XFCE desktop kept losing its taskbar... I could usually get it back through a simple Terminal command, but it was frustrating, so I went back to UNE.

In my case, the upgrade to Meerkat left me with GNOME Desktop, which ran fine, in fact much better than Karmic UNR.  But I'd rather run GNOME on my desktop.

---

### Post by Terry Maker on 2010-10-27
Here is where I show my ignorance! 

I had never heard of the, *"Karmic Ubuntu Netbook Remix or Lucid Ubuntu Netbook Edition"*, that's what I like about Ubuntu, there is something new to learn every day, if you want to! 

I will have to run a search for either/both of these in a 'live' CD format, or .iso format.

For 20 years I was a DOS man, then a Windows man, *(95, 98, Millennium/2000, and XP)*, this is like the old days for me when Dos was "King"! But, with better(?) equipment, you couldn't even lift some of the 1976 vintage stuff I worked on!

Terry

---

### Post by zaivala on 2010-10-27
UNR was unofficial under Intrepid, official under Karmic, and included on the official disk for Jaunty; for Lucid they changed it a bit to UNE (Edition instead of Remix).  For Meerkat, they threw it out the window for Unity, which does not run on older machines like yours and mine.

It's very much a replacement for the gOS and Xandros ... I have found that it works much better than those distros, but it is not quite as frugal on power.

---

### Post by Terry Maker on 2010-10-28
After a day of switching Op. systems, the guru's may be right. 

I loaded Lynx netbook version and it worked as far as the screen sizing, but SSSLLLOOOOOOWWWWWWW! like walking through molasses! Just not enough resources!

So I went back to Lynx via Koala, and this time she screen sizing has come up right(?) So not a total failure there, but why?

Anyway it now works with the 10.4 L.T.S version, the only one that is too big out of all the programs is Evolution, but acceptable.

Thanks for the advice and the experience, too bad it didn't work out. I'm reasonably sure that I would have switched back anyway, since I couldn't find any kind of desktop, and the programs that I wanted to install. Then I came to the conclusion that netbook was just that, a book for using the net!

Thanks again 

Terry

---

### Post by zaivala on 2010-10-28
Well, you still have Xubuntu and Lubuntu (not yet official) to try out.  I've had stability problems with XFCE (Xubuntu) on my machine, but that doesn't mean they will be repeated on yours... and I tried the latest version of Lubuntu, to find that it didn't have a driver for my modem -- and wanted to download one from the Internet to fix it.  Ya know, if you don't have a modem working, you can't download something to fix it.  But again, that doesn't mean your machine would have the same problem.

---

### Post by Terry Maker on 2010-10-28
Now that the screen sizing 'error' seems to have been corrected, I think that I'll stay with 'Lynx' until the next hardware upgrade. Whenever that will be?

I don't know how long this poor old laptop can last though, I've had it for 7 years, after rescuing it from a waste bin!

I think that my next thing to do will be to get a 'Live' CD of 10.4 L.T.S., since "Lynx via Koala", is a bit of a pain, and takes the time of two installs!

Fun whilst it lasted though, till the next one.

Regards
Terry

---

### Post by zaivala on 2010-10-28
LOL I know what you mean.  I had to give back the Eee PC I was using, and bought this 2001 Sony Vaio.  Right now it's running Lucid Lynx UNE.  It's great for the big screen, but it is very heavy...  Sony claims it is not upgradable, but other Sony users say every single component on it is very upgradable -- although to go from the 1 GHz Athlon 4 to the 1.2 GHz model may also require a BIOS upgrade.  But I can't get past the 512 Mb RAM limit, so it looks like a new machine or at least a new motherboard.

---

### Post by Terry Maker on 2010-11-02
Sorry for the delay in replying, I've had a 3 day broadband 'outage', just to add to the fun. 

The *"Lucid Lynx"* desktop version is still a "Happy little Bunny", so I'm going to stick with it until the current laptop 'dies'

A friend of mine has just got himself an "Acer" laptop at a ridiculously low price from one of the big well known outlets in the UK! *(The one that has 'PC' in its name*)

1.8Ghz processor, 1Gb memory, 160Gb HDD DVD read/write, all as standard, for less than £300GBP! I think that's as close as I can say without avertising!

Sometimes, I wonder if it is worth 'recycling' old equipment, as more and more of it becomes economically unrepairable.

It's the kind of world we live in, *"just throw it away, and get another one"!*



Terry M

---

### Post by zaivala on 2010-11-02
You will know in your heart that you, like I, have slowed the system.  It cannot be stopped.  My old 2001 Sony Vaio laptop will have to be replaced some day.  I hope to get a 3-4-year-old one to replace it.  I will not stoke the New Is Best fires.

---

### Post by Terry Maker on 2010-11-08
Re your last, and spurred by the knowledge that "all things are possible" even in some limited form, I tried "Meerkat" again!

Only this time a totally "Clean" install, even down to removing the partition on the HDD, and, it worked! I booted up from the 'live' CD I had made, and after the 'details' bit I walked away and left the laptop, to get on with it.

I came back after an hour or so, to find a 'reboot' message, did so, and it all works! It actually took longer to re-install the programs I wanted, and set up the personal aspects than the 'install'.

Results and observations: Yes, it is slower than "Lynx", on this machine, but still not as slow as it was on the 'overlaid' upgrade version, and it seems to speed up as you use it more, almost as though the system is 'learning and adapting'.

Display: The desktop fits, and all associated with it, with one exception! The 'Evolution Mail' windows are still too large, which is a problem for the writers of 'Evolution', rather than Ubuntu!

Moral: If you want to install "Maverick Meerkat" on an old machine, then you are probably better off doing a totally clean install, and remove all traces of what was there before!

One Further piece of advice from this exercise: Run The post install system for another hour or so, doing anything, play a game, anything, and reboot several times, just to get the system to settle down! Then set up as you want it. 

It worked for me!

Regards

Terry M

---

### Post by zaivala on 2010-11-08
Good to know, Terry.  I ran clean boots (from disks in Ubuntu magazines) for Jaunty, Karmic, and Lucid, the latter of which is what I am currently using on my old Sony.

---

