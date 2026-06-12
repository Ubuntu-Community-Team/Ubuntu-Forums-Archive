---
title: "Lucent/Agere WinModem and Getting It to Work"
date: 2004-12-01
forum: Networking &amp; Wireless
---

### Post by Wig on 2004-12-01
Hey. Let me start off by saying that I'm completely frustrated with this. Now, for some background. 

I used to run Slackware 9.2 (or 9.1, forgot). It had the 2.4.22 kernel, and I was able to make my modem work with it. Cool, for me. One day I decided to up the kernel to 2.6.5 or something and quickly discovered that I had no clue how to make the modem work with it. Oh well, I thought, I'll just use 2.4.22.

Fast forward. My Ubuntu CDs arrive. Yay! They have the 2.6.8.1 kernel in them.

Nothign works. Yes, I have tried all the 2.6 modem drivers on this page: [http://www.physcip.uni-stuttgart.de/heby/ltmodem/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/)    I got the kernel headers so it would stop complaining, but it just enters the directory and says "no target for "and" make" or something like that. Not sure what that means.

I got as far as having the modules loaded up, some package.  .deb

I used "modprobe lt_serial" and no error. I did "lsmod" and YES, THE MODULES WERE LOADED!

wvdialconf time. It scans the /dev/modem and it doesnt' work. says no modem although that's where it was loaded (dev/modem is a sym link. ttyLT0 is the real one).  I go into network tools and it doesn't work. 

I cry inside.

If anyone has any idea what to do, get ahold of me. Use this thread, various other means are listed below.

AIM: nwig
PM Me: OF COURSE!
E-mail: [email]alawiggle@gmail.com[/email]

HELL, IF WE HAVE TO, I WILL CALL YOU AS TO NOT COST YOU LONG DISTANCE CHARGES. 

I just want this working.

---

### Post by az on 2004-12-01
DId you try this:
[http://ubuntuforums.org/showthread.php?t=6361](http://ubuntuforums.org/showthread.php?t=6361)
or this
[http://ubuntuforums.org/showthread.php?t=6319](http://ubuntuforums.org/showthread.php?t=6319)


Install this:
[http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb](http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb)


dpkg -i ltmodem*.deb

(This is compiled with the default warty kernel)

Let me know if it works.

Do this:
Open a terminal and do
sudo pppconfig
Enter the information as needed. Use the name provider for your default connection. COM1 is /dev/ttyLT0, COM2 is /dev/ttyS1, and so forth.
Add your user to the dip group using the advanced options.
Save and exit.
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated. You can then pon and poff without the sudo. Now, right click on the panel and add an applet called modem lights. It is already set up to use pon and poff. Make sure that it is using the correct lock file to see your modem or you will not see the lights.

---

### Post by Wig on 2004-12-01
[QUOTE=azz]DId you try this:
[http://ubuntuforums.org/showthread.php?t=6361](http://ubuntuforums.org/showthread.php?t=6361)
or this
[http://ubuntuforums.org/showthread.php?t=6319](http://ubuntuforums.org/showthread.php?t=6319)


Install this:
[http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb](http://www.vif.com/users/mzajac/ltmodem-2.6.8.1-3-386_8.31a9_i386.deb)


dpkg -i ltmodem*.deb

(This is compiled with the default warty kernel)

Let me know if it works.

Do this:
Open a terminal and do
sudo pppconfig
Enter the information as needed. Use the name provider for your default connection. COM1 is /dev/ttyLT0, COM2 is /dev/ttyS1, and so forth.
Add your user to the dip group using the advanced options.
Save and exit.
sudo pon
If you get nothing or if you run into trouble, open another terminal and do:
sudo tail -f /var/log/messages

This may give you an up-to-the-second idea of what is going on. Post the result in your question to the forum.
sudo poff hangs up.
You need to log out and back in for your user/group settings to be updated. You can then pon and poff without the sudo. Now, right click on the panel and add an applet called modem lights. It is already set up to use pon and poff. Make sure that it is using the correct lock file to see your modem or you will not see the lights.[/QUOTE]

I've done the installing of the *.deb package, and I tried wvdial, but I didn't try this sudo pon stuff. I'll try that today.

 Also, "Add your user to the dip group using the advanced options." how do I do that?

---

### Post by az on 2004-12-01
So your problem is not that your winmodem drivers do not compile, but that the post-configuration is not going right?

Insofar as the dip group -  Just run pppconfig and enter all the information.  Go into the advanced options and add you user name to the group.  If will be pretty obvious while you run pppconfig.  Save your changes.

Good luck!

Lemme know....

---

### Post by Wig on 2004-12-02
[QUOTE=azz]So your problem is not that your winmodem drivers do not compile, but that the post-configuration is not going right?

Insofar as the dip group -  Just run pppconfig and enter all the information.  Go into the advanced options and add you user name to the group.  If will be pretty obvious while you run pppconfig.  Save your changes.

Good luck!

Lemme know....[/QUOTE]

I included an attachement with everything I did. Please view and let me know what you think.

---

### Post by az on 2004-12-02
That file is a veritable mine of irrelevant information.

All that is relevant is that the module getls loaded.  Where did you get this package?  Did you compile it yourself?

Did you do pppconfig?  Pon will do nothing if pppconfig is not configured!

---

### Post by Wig on 2004-12-02
[QUOTE=azz]That file is a veritable mine of irrelevant information.

All that is relevant is that the module getls loaded.  Where did you get this package?  Did you compile it yourself?

Did you do pppconfig?  Pon will do nothing if pppconfig is not configured![/QUOTE]

I can't remember where I got the package from at the moment, but a9 doesn't work at all, whereas a8 does.

And yes, I did pppconfig. That's what you said to do, so I tried it.

---

### Post by az on 2004-12-02
And....

---

### Post by Wig on 2004-12-02
[QUOTE=azz]And....[/QUOTE]


It didn't work? The file has the log after I did pon in it. Or was that irrevalent, too?

---

### Post by az on 2004-12-03
Sorry for being rude.  It is difficult to help when you can't tell me where you got these drivers.  Did you make it youself or was it precompiled.  The checkout utility is buggy most of the output from it is usesless error messages!  

The module gets loaded.  Fine.

Were there any issues with pppconfig?  Did you try to change parameters?  Do you hear anything when you dial?  Did you try to install the drivers without making a debian package?

---

### Post by Wig on 2004-12-03
[QUOTE=azz]Sorry for being rude.  It is difficult to help when you can't tell me where you got these drivers.  Did you make it youself or was it precompiled.  The checkout utility is buggy most of the output from it is usesless error messages!  

The module gets loaded.  Fine.

Were there any issues with pppconfig?  Did you try to change parameters?  Do you hear anything when you dial?  Did you try to install the drivers without making a debian package?[/QUOTE]

Someone gave me the package on IRC. It came like that, so I'm assuming pre-compiled. 

pppconfig had no problems. I answered the information fine, and set the /dev/ or whatever to ttyLT0.

When I try to dial, I hear nothing. 

I used the source from this site: [http://www.physcip.uni-stuttgart.de/heby/ltmodem/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/)    the 2.6. resource page. I used the kernel headers for them, got the *.ko modules, copied them to /lib/modules/`uname -r`/ltmodem (after I created the folder ltmodem). After that I was pretty much stuck. 

Also, something to note, [http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)

I tried to use that package (might have been a8 or a9) and it had a ./build_deb thing in it. I tried to use it, but it said my kernel headers were wrong, being 2.6.8.1 when my kernel version was 2.6.8.1-3-386 ? 

Is there a way to fix that?

---

