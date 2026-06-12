---
title: "Accessing Web-sites"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by expcman on 2009-05-29
I have a dual-boot set-up (WinXP & Ubuntu), one that worked fine until a month ago, when suddenly I found I could not up-date my Ubuntu files.  After working through lots of on-line help sites, I realized that I can access the Net, just not the web-sites I usually use [and which I get to through my WinXP OS without any problem at all, which means that neither my cable modem or router is creating any hard-ware or soft-ware problem, at least none of which I am aware] - in fact, my public library's web-site is the only one that I know I can get into on a regular basis, just like I expect ... which surely is puzzling; but when I try to access my other usual web-sites (using Firefox), the browser reports either that there is no connection or that there is a connection and that it is waiting for a down-load of data ... which never comes (???).

This problem was with Ubuntu 8.04 and after going into all sorts of files and changing things around (following various suggestions from this forum and elsewhere), I finally "got smart" (or thought I had) and re-installed Ubuntu 8.04 (a "clean" re-installation) ... but no joy, for the same thing happens ... or rather doesn't happen!  

So yesterday I got smart again :D (or thought I had) and after down-loading and burning a DVD (using WinXP) I did a "clean" install of Ubuntu 8.10 ... only to find the exact same situation. So having learned a bit (enough to get myself confused perhaps) I ask for ideas/suggestions/routines that might finally get me to fix this situation.

One last thing - when I installed the Ubuntu 8.10 yesterday, I did notice that it took a very, very long time, seeming to be hung up [at least nothing at all happened for at least twenty minutes ... ???]- the installation graph said that it was 82% done [oh, yes - this also was the situation after the installation reported only a minute more to go, only that may have been just for copying the files from the disk ... ???] and the little window showed "configuring apt" and "scanning the mirror ..." ... which may or may not "say something" (???) ... then it got to the next stage ("scanning the security update repository" where (again) nothing seemed to be happening ,this time for six minutes.  Which made me to wonder if it could not connect with some necessary web-sites (???).

I do look forward to instruction and clarification.

Thanks,

Frank

---

### Post by Miljet on 2009-05-29
This happened to me once before. I could access some web sites, but not others. After fighting with it for two days, I finally pulled the plug on my router, let it reset, and plugged it back in. And all my web sites were available again. Some temporary glitch in the router.

---

### Post by detroit/zero on 2009-05-29
You might want to check the DNS server settings in your network configuration for that particular connection.

You might also want to go have a look in /home/zero/.gconf/system/networking/wireless/networks

Every wireless network you've ever connected to will have a folder in that directory, regardless of whether you've got it in the list in nm-applet. To be on the safe side, go into that folder and delete all the networks you haven't connected to in a while.

If you don't have any fears about configuring or setting up a network connection, you could do well by first removing all your configured connections from the list inside nm-applet, and then going into that folder and removing all the remnant folders.

---

### Post by SunnyRabbiera on 2009-05-29
> **Miljet said:**
> This happened to me once before. I could access some web sites, but not others. After fighting with it for two days, I finally pulled the plug on my router, let it reset, and plugged it back in. And all my web sites were available again. Some temporary glitch in the router.

Indeed, some ISP's reset once or twice a month.
Comcast my ISP resets twice a month

---

### Post by expcman on 2009-05-29
Thanks for these comments about routers (and by implication cable modems) but as I have no problem at all when I use my computer booted up into WinXP (and the same router and modem) without any difficulties at all, it seems to me to be some soft-ware problem in/with Ubuntu - something I still do not know about.  Still, thanks for trying ... but futzing around with either the cable modem or router doesn't change anything ... and also by the way, my issue is not about obtaining and maintaining any wireless connection, formy lapt-top picks up on my router without any problem, but then the dual-boot there is Vista and Windows 7.  Heavy sigh!

---

### Post by expcman on 2009-06-06
Good news ... no, make that great news for I have found the answer ... or rather another person gave me the answer (re. question by "rennerocha" on "Networking & Wireless."  His computer's motherboard has the same NIC chip as mine (SiS 190 and was giving him the very same problem.  Happily, another guy knew the answer and told us how to change the value of the mtu and that "did the trick" - quick, simple, and easy.  Go take a look if your have the same problem - being able to ping all sorts of web-sites without being able to down-load any content ... except for a few!  It has been most frustrating but now that frustration is over.  So I just had to share this "good news"!

---

