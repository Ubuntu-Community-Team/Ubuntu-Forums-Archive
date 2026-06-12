---
title: "After upgrade, greeted with &quot;error: the symbol 'grub_puts_' not found&quot;"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-12
I am starting this thread to simply ask what might have caused this problem in the first place.  What I am wanting to hear back from others is theories about what I might have done wrong.

Here's the setup I have on this machine.

Partitions:

1 NTFS partition with XP
1 ext4 partition for /
1 ext4 partition for /home
1 swap

Because I have it setup like this I am able to quickly do a clean install without losing everything in my /home folder, and I've gone ahead and done that to get around the "error: the symbol 'grub_puts_' not found" problem I just encountered.

Since I essentially replaced my / partition and preserved my /home partition, I'm up and running now with all my desktop preferences and such, but have to reinstall software that used to be on the machine all over again.

So why did I get met with this error message, I am wondering?

Throughout the upgrade I would occasionally get met with the messages about "What should we do with this configuration file that has been customized, sir?".  Every single dialog box I got asking such a question would be answered with a "Install developers new configuration".  From memory, these types of questions popped up for Samba configuration and something to do with automatic upgrades, but never did I get an error message asking me to do anything custom with my grub configuration.  Not one alert or info box about grub having issues, so I am caught off guard when I restart and am surprised with this grub rescue> prompt.

Now comes a tough question:  Did I do something wrong?  I mean, I don't know if it's fair for me to rejoice over the fact that I knew of a sloppy work-around for a problem that I honestly don't think I'm responsible for causing...

And another tough question:  What would have been the correct way to repair the system had I not gone ahead and just decided to reinstall the / partition?  If I were a novice user who had just installed Ubuntu earlier this year and was slammed with this confusing situation after an innocent upgrade, I might jump to the conclusion that Ubuntu is "still not ready" for mainstream use, and it really saddens me to have to say that because I bend over backwards promoting the OS to people who have never tried it before.  It's so embarrassing for me to be enthusiastic about Ubuntu and then get flanked with something like this on one of my own machines.

So far for me upgrading to 10.10 has been [0 for 2]("http://ubuntuforums.org/showthread.php?t=1593193"). :(

---

### Post by Quackers on 2010-10-12
Have a look here old bean :-)
[http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752)

---

