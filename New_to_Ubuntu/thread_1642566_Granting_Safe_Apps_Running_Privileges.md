---
title: "Granting Safe Apps Running Privileges?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by fleamour on 2010-12-10
When booting Ubuntu 10.10 I have to manually type my password three times to grant Empathy, Ubuntu One Indicator Applet & my wireless internet connection, running privileges.

Is there a way round this?  As is tedious.

I cannot leave workstation hibernated as messes with keyboard initiation when dual booting 7.

---

### Post by bkapps on 2010-12-10
If I had to guess I'd say that there's a permissions error with that applet, your user needs to be added to the proper group in order to use it without authorization.  Is there another user set up on the computer or is it just you?

---

### Post by fleamour on 2010-12-10
It's just me.  Another issue is FatRat download manager auto starts regardless of there being no entry under System > Preferences > Startup Apps.  Also saved session is not ticked.

---

### Post by madjr on 2010-12-10
> **fleamour said:**
> It's just me.  Another issue is FatRat download manager auto starts regardless of there being no entry under System > Preferences > Startup Apps.  Also saved session is not ticked.

i use fatrat with flashgot in ff, never had that problem.

---

### Post by fleamour on 2010-12-10
I've had the same FatRat problem on Ubuntu 10.10 & earlier versions of Xubuntu.  

Also tried installing DocbarX & that did not work either.  A Case of MCS (Mysterious Computer Stuff) I guess...

---

### Post by fleamour on 2010-12-10
OK, DocbarX needs to be added to panel.  Solved.

On closer inspection it appears I am being asked for keyring access three times in a row, weird but very annoying.

---

### Post by madjr on 2010-12-10
are you in auto login?

might be good to disable it till you find a way.

this way you will only need to type things once.

and btw dockbar is cool :D

---

### Post by fleamour on 2010-12-10
OK, after deleting my keyring it would appear Gwibber, Empathy or Ubuntu One cloud service & wireless network key all store passwords.  This accounts for entering pass key three times.

I know Linux is secure, but this is just plain annoying!

---

### Post by fleamour on 2010-12-10
> **madjr said:**
> are you in auto login?

might be good to disable it till you find a way.

this way you will only need to type things once.

and btw dockbar is cool :D


Yes, auto login, where do I disable?

PS.  DockbarX gives some 7/OS X functionality.

---

### Post by fleamour on 2010-12-10
[http://www.liberiangeek.net/2010/10/disable-auto-login-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/disable-auto-login-ubuntu-10-0410-10-maverick-meerkat/)

---

### Post by fleamour on 2010-12-10
OK, after disabling auto login.  It'll ask for a keyring to unlock, there is an option under "Details" to unlock automatically upon login.

---

### Post by uRock on 2010-12-10
To fix the logging into wireless problem, right-click the network manager icon , then click edit connections. then click on the wireless tab, then click on your current profile for wireless. Once that window is open, tick the box at the bottom left that says, Available to all users. Once you click apply you should not be asked for the keyring password again.

---

### Post by madjr on 2010-12-11
> **uRock said:**
> To fix the logging into wireless problem, right-click the network manager icon , then click edit connections. then click on the wireless tab, then click on your current profile for wireless. Once that window is open, tick the box at the bottom left that says, Available to all users. Once you click apply you should not be asked for the keyring password again.

this is good, but would be nice if the text description mentioned the keyring and made it more obvious. I think this calls for a papercut

---

