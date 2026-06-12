---
title: "Genius wizardpen tablet doesn't work!"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by merrymoll on 2009-08-08
Ullo there!  I've installed Ubuntu on my computer for the first time so I'm a complete newbie at all this.  My version is 9.04.  Everything is great and working fine, except my trusty Genius wizardpen tablet 4x3.  There's no response form it at all, apart from it's light when I touch pen to pad.  I have looked at other topics covering this, but as I said I'm a total noob at this and a lot of the solutions went totally over my head. :confused:  I followed instructions in Ubuntu documentation but no joy.  I have absolutely nil experience and not sure what to do next.

Would some kind, patient soul hold my hand and guide me through this? :P

---

### Post by Favux on 2009-08-08
Hi merrymoll,

Welcome to Ubuntu Forums!

DoctorMo just set up a ppa for the wizardpen drivers in Jaunty.  What you do is add them to your System>Administration>Software Sources.  You click on the Third-Party Software tab and click Add.  Try to follow the instructions on the launchpad site.  Then Update Manager will offer to install the driver for you.  He would like feed back on how it goes for you.

See:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

Hope this helps.

---

### Post by merrymoll on 2009-08-09
Thanks for this - followed the links and did as instructed, but came up with the error: "Some index files failed to download, they have been ignored, or old ones used instead".:(

I'll need to let DrMo know about this - but thanks to you anyway!

---

### Post by Favux on 2009-08-09
Hi merrymoll,

Sorry to hear that.  One place DoctorMo wanted bugs reported is:  [https://bugs.launchpad.net/wizardpen](https://bugs.launchpad.net/wizardpen)

I hope you get it working quickly.

Edit:  Actually, come to think of it:  Did it say it didn't install?  Have you rebooted?

---

### Post by merrymoll on 2009-08-09
Opps - have already emailed him via Launchpad.  I'll see if he replies, or if any updates are made.

I did reboot and nothing happened. *shrug*  Like I said, I'll see how things develop.

---

### Post by Favux on 2009-08-09
Hi merrymoll,

I asked because it didn't sound like they were "fatal" errors.  Check in Synaptic Package Manager to see if the driver installed.  Search for "wizardpen".  If it is there click on it to highlight it and then click on Package (top left) and then go to the Installed Files tab.  See if there is a file installed called something like 99-wizardpen.fdi and where it's located.  It could be the driver is there and you just need the .fdi to get it working.

---

### Post by merrymoll on 2009-08-09
Aha!  99-wizardpen.fdi isn't in the downloaded files.

---

### Post by Favux on 2009-08-09
Hi merrymoll,

OK, that may be the problem.  This link will show you how to install a .fdi:  [http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en](http://www.jpbouza.com.ar/ESP2/tutoriales/gnulinux/genius-tablet/id/en)  I used this one because his .fdi in Step 3 with the "info.product stylus" line is probably what you want.  But look at the earlier stuff and follow it.  He basically got the info. from here:  [http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html](http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html)  I think.

Good luck!

---

### Post by Favux on 2009-08-09
Hi merrymoll,

Oh, to create the file and to add the stuff in and later edit it use:
```
gksudo gedit /etc/hal/fdi/policy/99-x11-wizardpen.fdi
```
Or you could just call it "99-wizardpen.fdi" I suppose.  And after you install it you'll need to reboot.

---

### Post by merrymoll on 2009-08-09
Done - and still nothing! :(

---

### Post by Favux on 2009-08-09
Hi merrymoll,

Good work.  Don't give up yet.  Try rebooting a few times.

Of course it could be the driver installed but it needed some of the files it didn't get to be working.

But either way it sounds like you needed to add the .fdi anyway.  You could also try installing the deb for your cpu architecture, i386 or amd64.  If you look at the launchpad site where you got the ppa at the bottom under "Source" is "xserver-xorg-input-wizardpen" etc.  Click on the little triangle in front of it and you'll see the deb.s etc.  Download the right deb and double click on it and see if it installs without the error message.

---

### Post by merrymoll on 2009-08-09
Right, downloaded the i386 deb and rebooted 'till I'm blue in the face - and still no joy.  Perhaps I'd be better off getting an earlier version of Ubuntu - or will I still have the same problems?

Sorry about all this!

---

### Post by Favux on 2009-08-09
Hi merrymoll,

> Perhaps I'd be better off getting an earlier version of Ubuntu - or will I still have the same problems?
Good question.  I've seen other people struggle to get it to compile.  And when they succeed (the ones who do) they're not sure how or why it happened.

Probably the best thing is to wait for DoctorMo to contact you.  That way you could stay with what you've started and help iron out bugs.  I'm sure he'll want the exact error message(s) from the ppa install if you have them.  And the deb too if it gave any.  Or if it didn't he'll at least want to know that and the fact that you tried the deb.

There is another deb from someone else  (I think) and a couple other links on how to compile.  Maybe hold off looking at them until and unless DoctorMo doesn't get back to you?

Edit:  By the way did you check that the two drivers were in "/usr/lib/xorg/modules/input/wizardpen_drv" like they recommend you do?

---

### Post by merrymoll on 2009-08-09
Ah, meant to ask about this:

"By the way did you check that the two drivers were in "/usr/lib/xorg/modules/input/wizardpen_drv" like they recommend you do?"

I've tried to copy the drivers to this folder, but it says I don't have the authority - Is this authority something I have to ask the people at Ubuntu for or is it something I can do myself?

---

### Post by Favux on 2009-08-09
Hi merrymoll,

No it's telling you you don't have the right permissions because you're not root.  You've already used "gksudo" which you use when calling up a graphical program from the terminal like Text Editor (gedit).  Since the cp (copy) command isn't graphical you'd use "sudo", like:
```
sudo cp /path/where/file/is /path/where/you/want/file
```
Each one ending in the file name you are copying of course.

---

### Post by merrymoll on 2009-08-09
Now it's saying it can't find the file I wan to copy!  Sheesh!

Never mind - I think I'll just forget about it for now - I'll put windows back on as a second OS, as I know it works there and just use it for my arty stuff (and Ubuntu for everything else!), and keep an eye out for any new developments in the new distro to help install the tablet.

Thanks very much for all your help!  I am grateful - it's just I'm so new to this most of it looks like a foreign language to me! XD

---

### Post by Favux on 2009-08-09
Hi merrymoll,

Sure.  There's a learning curve but you're doing it right, just dive on in.  You'll quickly get it.  This free download of the Ubuntu Pocket Guide and Reference may help:  [http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)  Remember in linux the file paths are case specific (A and a are different) unlike Windows.

---

### Post by merrymoll on 2009-08-09
Cheers!  And thanks for the link to the pocket guide - that'll be handy!

All the best!

---

### Post by jeanClo on 2009-08-16
Hi Merrymoll

Look at this link:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
You can use the file xserver-xorg-input-wizardpen_0.7.1.orig.tar.gz from DoctorMo.

I just installed a G-Pen 4500 and it is working.
Ubuntu 9.04 64bits

---

### Post by merrymoll on 2010-03-08
Thanks to Favux (for your patience with this n00b. XD) and to JeanClo for the handy link.  I've *finally *got the blimmin' pen working - I'm now on Ubuntu 9.10, and I followed [this]("http://ubuntuforums.org/showthread.php?t=1337260") very handy guide - even though I can't see the difference between this and what Favux talked me through before.  But this time, it seemed to work. *shrug*  *No* idea why.:confused:

But hey!  My pen works on Ubuntu, and I can now finally ditch Windows completely and move over to Ubuntu.  And draw pictures. :D

Thanks again!

---

