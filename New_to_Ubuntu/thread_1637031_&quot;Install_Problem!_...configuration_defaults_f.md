---
title: "&quot;Install Problem! ...configuration defaults for GNOME Power Manager...&quot;"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by AnjanaSofia on 2010-12-03
Hi all,

As my first foray into the world of linux, I'm running ubuntu 10.10 on my netbook via a persistent live USB stick (8G, created with the tool from pendrivelinux). So far, so good. Except...

Today when I booted up, it got up to the screen with the ubuntu logo with the red dots under it, hung for a while, then the bottom 1/3 of the screen went black and I got a pop-up in the upper right corner:

"Intall problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."

After a few more seconds, docky (which is on auto-start) tries to run, and a second pop-up appears over that one:

"Docky requires compositing to work properly. Please enable compositing and restart docky."

Then a very pared-down docky dock loads at the bottom of the screen, although the top 2/3 of the screen still have the ubuntu start-up logo and the pop-ups from before. I can't see the cursor but if I move it around I can somewhat interact with docky. I can't get anything productive to happen, however.

OK, so after some googling, it appears that the likely cause of the problem is not enough free space on the drive. There's lots of seemingly good advice in threads like [this]("http://ubuntuforums.org/archive/index.php/t-980711.html") on what commands to type in to fix it, but the problem is I don't know how to get to a terminal where I can type anything in!!!

CTRL+ALT+F1 gives me a cursor in the lower left corner, after several lines of commands [which I a) don't understand and b)don't have the patience to painstakingly transcribe letter for letter unless it's absolutely necessary] ...but I can't type anything in. CTRL+ALT+F2 gives me a nice clean screen with a cursor in the upper left, but I still can't type anything in! Same with +F3, +F4, etc. (+F7 brings me back to my messed-up logo/pop-up/docky screen.)

Please help! I'm super new at this so it's likely I'm missing something totally obvious, but have pity and point it out to me!

Thanks!

---

### Post by AnjanaSofia on 2010-12-04
So I managed to get a command line by booting into single-user mode (though doing things as root makes me super nervous), and I've tried all the methods I could find ([here]("http://ubuntuforums.org/archive/index.php/t-980711.html") and [here]("http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/")) to fix this issue:

removed over 700MB of files (really thought this would help, but it didn't... if the problem is too little space, how much space do I need to free up?)

apt-get clean   

dpkg --configure -a

mkdir /var/lib/gconf/default

...None of the above seemed to have any affect, still getting the same "Install Problem!" message. So I tried:

apt-get --reinstall install ubuntu-desktop  

This didn't work, presumably because I have no internet connection, and I could not figure out how to get it working; webroot just tried and failed to connect to anything. (Advice on how to make that work? I only have access to wireless right now, nothing wired.)

When --reinstall didn't work, it suggested I try --fix-broken, which I did, but that just told me everything was up-to-date and A-OK; not helpful.

Banging my head against the desk is also not having much of an effect. :(

Can anyone HELP?????????? Pretty pretty please!!!

---

