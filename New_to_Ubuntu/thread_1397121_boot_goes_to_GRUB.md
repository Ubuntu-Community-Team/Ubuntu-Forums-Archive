---
title: "boot goes to GRUB"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by thulefoth on 2010-02-02
Hi - I'm new at Linux, used the 'install under Windows' (Wubi?) option on the Ubuntu download page last week, and overnight got a nice new Ubuntu system (plus some added in the morning).  Everything went well, and I was soon fully connected, exploring & studying - using Linux!  Over the next few days I installed many programs, using the Software Center, and Synaptic.  Then I read in a recent article about Karmic Koala 9.10 that start-up options can be adjusted, using "Startup Manager", under Panel > Administrator (or System?).  But when I looked under my Panel, I could not find it.  Checking in Synaptic, sure enough there it was, and I installed it.  Now when I checked my Panel, it was there.  At some point, probably while taking a quick 'familiarization' glance at Startup Manager, something was displayed that caused me a little concern.  'GRUB' was mentioned (which I knew to be part of the boot-process) ... maybe there was some 'action' that occurred, that seemed out-of-place.  In any event, after working with Ubuntu for awhile, I rebooted the system ... and the boot failed.  After being presented with the choice to start Windows or start Ubuntu, the Ubuntu choice now places me at the GRUB prompt.    Uh-oh, I thought - sure enough, I shouldn't have installed that Startup Manager program ... maybe it was for a Partition install, not a Wubi, or maybe during my install configurations were set, which I've now corrupted.  Something...  By studying & reading, I have gotten as far as using the "linux" and "initrd" statements in GRUB to load what seem like the appropriate files in the /boot/ directory.  GRUB responds with the expected info & reports.  Then, I issue the "boot" statement...  A great deal of text is printed to the screen, after the boot command, but eventually the action halts, printing to the screen:   "Waiting for root file system..."  After a time, the system lists several "common problems", things to check, then concludes:  "ALERT! does not exist.  Dropping to shell!"  The BusyBox intro-lines then appear, followed by the prompt:  (initramfs)  My efforts to find a way forward from this point have not been fruitful.  Since this Ubuntu install is 'just' a 'loop-file' under Windows, it can be deleted, and I can start over.  But exploring this issue has been a good eye-opener, and I would like to continue trying to 'save' the install (to later convert it to a proper Partition) if that is a reasonably practical thing to do.  Are there details, or alternative general approaches to the problem that I can use to resolve this situation?  Thank you!  "Ted"

---

### Post by Atzu on 2010-02-02
GRUB is what let you choose if you want to boot Windows or Ubuntu ... That's when you install ubuntu... when you install wubi you still use MBR the windows bootloader... so i guess that when GRUB actually doesn't exist how can u modify it? :p if you were using a Ubuntu install then i'd suggest you to use a live cd to reinstall GRUB... but dunno what to do with a wubi install. 

Also... Less text would be helpful in your post... Sorry but reading all that was a bit tiring ... maybe because i dont see any spaces between paragraphs... or maybe because your whole post is one big paragraph :p Good luck with ure problem.

I had problems with wubi the first time i tried it, and messed everything up... finished installing ubuntu on a partition. Again, Good luck

---

### Post by thulefoth on 2010-02-02
Well, maybe there shouldn't be a GRUB under a WUBI ... but there sure is now!  Maybe that's what my problem is - that installing Startup Manager put GRUB on a system where it shouldn't be?  Mmm ...  :)

---

### Post by warfacegod on 2010-02-02
I don't see how installing Startup Manager would install GRUB. It's settings (as far as I know) are strictly after the OS begins the bootup process.

---

### Post by thulefoth on 2010-02-02
Yeah, it doesn't seem to me that Startup Manager should be in charge of installing GRUB; it seems more like just for *managing* the various choices & options ...

---

### Post by Atzu on 2010-02-02
Question... when you select Ubuntu on windows bootloader... what exactly happens? 

btw i believe you have to clean shut-down windows to be able to boot wubi and what i think if i understand is that the windows bootloader doesn't find wubi install for some reason...

---

### Post by thulefoth on 2010-02-02
When I select Ubuntu on the Windows bootloader, the screen goes black for a second, and comes back up with the GRUB header & intro, and the prompt, sh:grub>.   It isn't necessary to do a full shutdown to bring up the OS-choice: I use Restart fairly often from Ubuntu, and it does a normal restart.  Same from Windows ... tho I've been using it a lot less lately!  [-(

---

### Post by bcbc on 2010-02-02
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by warfacegod on 2010-02-02
This might be worth checking out. meirfra's script helped an awful lot of fragged Wubi installs at the beginning of January.

---

### Post by thulefoth on 2010-02-02
bcbc - hi!  I look out at the sun washing over Victory every morning.  Well, some mornings.  Ok ... I thought I saw it once!  :---)
 
Spot-on link - Thanks!  Sounds like maybe Startup Manager "updated" GRUB.
 
I'll go perform the fix now ...

---

### Post by thulefoth on 2010-02-02
Greetings from Ubuntu!      :D
 
The fix worked.   
 
I have been rapidly removing stuff from Windows as I find replacement functionality on Ubuntu ... have been 'controlling' myself somewhat, not to get 'over-excited' and hurry the transition too much.  BUT, this experience shows that there is risk in the Wubi set-up that justifies moving quickly.
 
Over the next couple nights, I will download and burn a couple live/install CDs (and backup personal files!), as 'insurance' for the conversion of Wubi to a true partition OS - which I see is also not without risk - soon.  

Thank you very much, all!   "Ted"

---

