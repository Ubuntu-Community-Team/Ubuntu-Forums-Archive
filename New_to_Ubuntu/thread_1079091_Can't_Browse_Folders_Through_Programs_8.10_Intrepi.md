---
title: "Can't Browse Folders Through Programs 8.10 Intrepid"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by thesoftwarejunkie on 2009-02-24
Here is the problem. I am trying to use programs like Songbird and programs that ask me to open a file. I select "open" and the file browser comes up, but I cannot click on anything. The scroll isn't doing anything, and I cannot select other directories or folders.

If I just browse places, desktop, use nautilus, no problem what so ever. Just when I try to access files through a program. The only program that didn't seem to do it was mplayer. The browser for that program is identical to Nautilus and allows me to browse with no problem.

I am the admin, the only account on the computer.

Specs:
Compaq Presario CQ60-215DX
AMD Athlon X2 Dual-Core
250GB HD
2GB RAM
8x DVD-DL Drive
nVidia GeForce 8200M
Atheros Wifi

Everything else runs great. I have the nVidia driver 177 running, compiz fusion working, emerald working. I can switch between compiz and metacity with no problems and ease. I can turn Emerald on and off. None of this changes the browsing scenario. Wifi works, Graphics works, DVD works. Everything else is fine just that.

I am new too Ubuntu and can do some things because I have prior computer knowledge, and have updated 8.10 and added programs and updates.

---

### Post by Xiong Chiamiov on 2009-02-27
Depending on what toolkit was used to create the app, different file-browsing dialogs are used.  It sounds like you're having a problem with one of them.  Sorry I can't offer any more than that.

---

### Post by arm-c on 2009-02-28
When did this start?  What did you install just before you had the problem?

On a second note, go to System, Administration, Unlock it, add a user, log out and back in under the new user account, and see if the problem persists.

Given the way packages are resolved in debian based distro's, unless you installed an application that doesn't declare dependancies correctly, it should work fine and install all required files.

Let me know what your result is with a new profile.  You can always delete it later on.

Regards!

---

