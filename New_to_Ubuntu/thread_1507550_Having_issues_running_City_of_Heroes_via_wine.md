---
title: "Having issues running City of Heroes via wine"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by Medieval Matt on 2010-06-11
I've seemingly successfully installed City of Heroes in wine on Lucid Lynx.  But when I run it, it shuts down when switching from the updater to the client. So I decided to run via the terminal and it dropped off at this error.

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  159 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  173
  Current serial number in output stream:  173

```Any suggestions?

-Matt

---

### Post by Mark Phelps on 2010-06-11
If you're going to mess around with Wine, you need to familiarize yourself with the WineHQ application compatibilty site.

The link below is to their page for City of Heroes:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2141]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2141")

Click on the test results to see what the tester did.

---

### Post by Medieval Matt on 2010-06-11
I tried editing the .exe file to include -renderthread 0 and also running CoH through the command line  as well as reinstalling the game itself none of which worked and all of which were he top results on that website.  Does this error tell you anything useful or is it just garbage.

---

