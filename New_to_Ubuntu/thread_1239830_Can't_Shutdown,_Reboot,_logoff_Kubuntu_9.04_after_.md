---
title: "Can't Shutdown, Reboot, logoff Kubuntu 9.04 after KDE 4.3 update"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by viveksj on 2009-08-13
Hello All

I am having trouble with Shutdown/Reboot or logoff Kubuntu 9.04 after updating to KDE 4.3. If i select any one of these options from menu i get absolutely no response from the system. But i can change user from kickoff menu.

One more thing Shutdown and reboot commands work fine from Terminal.

Anybody knows the reason or solution to this problem please reply

Thanks
VJ

---

### Post by sturmflut on 2009-08-16
I am having the same problem on a machine running Kubuntu 9.04 with KDE 4.3 packages and a machine running Kubuntu 9.10 Beta 4.

It is possible to go to the Logout/Shutdown dialog once (via the K-Menu or by right-clicking on the desktop and selecting "Leave.."), but after that nothing happens and the dialog won't appear again.

"Logout" is now only possible by restarting kdm, Restart/Shutdown only by using 'shutdown' in a konsole.

I don't know if it helps but I noticed that the session also can't be shutdown using qdbus:

```
sturmflut@ion $ qdbus org.kde.ksmserver /KSMSServer org.kde.KSMServerInterface.canShutdown
true
sturmflut@ion $ qdbus org.kde.ksmserver /KSMSServer org.kde.KSMServerInterface.logout 0 0 0

sturmflut@ion $
```

...and nothing happens after this.

---

### Post by sturmflut on 2009-08-16
Okay, apparently the problem has been found and a work-around is available:

[http://osdir.com/ml/kde-bugs-dist/2009-08/msg02999.html](http://osdir.com/ml/kde-bugs-dist/2009-08/msg02999.html)

You need to explicitely turn off the "logout" sound, even if sound notifications are already globally off.

Personally I am in favor of removing most of the sound notifications because I always deactivate them completely and this is not the first major issue connected to them.

---

### Post by homebaze on 2009-08-18
Hi, I tried the workaround as well, but it still doesn't do it for me.
If I want to shutdown or reboot, I have to use the terminal.
The odd thing is though, at an another account (without compositing and k-win effects), it can be shutdown via the GUI or the shutdown button on the laptop.
Can anyone help me? What further information would you need?

---

### Post by raditzman on 2010-03-25
I did the workaround and now I can logoff and shutdown :)

---

