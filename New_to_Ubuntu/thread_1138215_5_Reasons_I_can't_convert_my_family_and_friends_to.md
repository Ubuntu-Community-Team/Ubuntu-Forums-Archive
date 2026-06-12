---
title: "5 Reasons I can't convert my family and friends to Linux/Ubuntu"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by hobo14 on 2009-04-26
I recently made the permanent change on my main machine to Ubuntu only (have dabbled with dual boots a few times before, and still have an XP gaming box), and am so glad I did.  
Next I started trying to convert heathen non-believers from Windows, starting with my friends and family.

Unfortunately I failed because of the following 5 "characteristics" of Ubuntu that I(newb) can't change for them:

1.)  Automount is crap - external disks have to be manually mounted in terminal to be able to see files with Chinese characters in their names, and if a disk is first pulled out of a Windows box without being "safely removed" (which is what usually happens) Ubuntu automount won't mount it, it has to be manually mounted with the force option.

2.)  External disks have to be unmounted before data is written to them, and so they will automount next time. (I know, I know, don't tell me "Windows does too". In Windows you should, but it's rarely necessary, and most people don't.)

3.)  Installing new programs you find online can be hard - most Linux stuff seems to be source downloads that have to be compiled, and even deb packages don't install nicely enough for people who only know how to use windows: they need to be able to doubleclick the install package, then click next, ok, and see the new program magically appear in their menu and on their desktop. Always, no exceptions ever.

4.)  Eventually they are going to find themselves in a situation where they need to open a terminal window.  This is unacceptable to them; Ubuntu needs to be able to do at least as much through the GUI as Windows can. 

5.)  Other partitions on the internal hard drive mounted at boot belong to root and don't have friendly enough permissions to avoid using "sudo", so I like to change /etc/fstab to make the owner of the partition the main user of the machine, and to give him full control of that partition including execute permission.  Unfortunately text files on these partitions are marked executable, so doubleclicking them means they are run as scripts instead of being opened for editing.  I can change Nautilus to always view text files instead of running them (being asked  each time is not acceptable to the reluctant converts), but then they can't run script files....


I can work around these things, but my friends and family can't or won't. :(
Hopefully some of these can be corrected now by people who know more than I do, and the rest will be corrected in future versions of Ubuntu, so Linux can be brought to the clueless majority.

EDIT: probably not really the best place for this thread?  I'll put it in the cafe...

---

### Post by kwacka on 2009-04-26
Why would you want to convert them? 

If they don't convert themselves they're going to be resistant to change and stick obstacles.

I assume that whilst they're using Windows you're the one left to sort the crud out. Just tell them if they want to run Windows, **THEY** run it.

If they can't sort any problems out you say you're so busy that you can't manage until, say, Friday. If they can't wait there's plenty of computer stores that will do it for them.

I'm nearly there - "I don't know anything about Vista" and welcome the arrival of Windows 7 - I won't know anything about that either.

---

