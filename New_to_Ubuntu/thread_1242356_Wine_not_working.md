---
title: "Wine not working"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by salmanbashir on 2009-08-17
Even with Wine I cant install many Windows based applications, for instance, I tried to install a Windows applications and it said, error!, no dll files found. What do I do?

---

### Post by Faud on 2009-08-17
You can import the .dll files into wine from the windows partition or you can google them and download them from online. There is actually a WINE section here on the forums that should have some really good info for you.

---

### Post by Mark Phelps on 2009-08-17
> **salmanbashir said:**
> Even with Wine I cant install many Windows based applications, for instance, I tried to install a Windows applications and it said, error!, no dll files found. What do I do?

First thing to need to do is check the CodeWeavers application compatibility database for the version of the application you're trying to install.  Lots of MS Windows apps do NOT run under Wine.

If your search returns no results, or it does and the rating is not at least Gold, you're wasting your time trying to install that particular app in Wine.

See the link below:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

### Post by 3rdalbum on 2009-08-17
> **salmanbashir said:**
> Even with Wine I cant install many Windows based applications

This is normal. It's remarkable that Wine works as well as it does, considering it is a reverse-engineered reimplementation of Windows libraries on Linux. But Wine does not work with many Windows applications, when you compare it to the number of Windows applications there are.

Your best bet is to find equivalent Linux programs.

---

### Post by harry2006 on 2009-08-17
first make sure you've all the basic dll files required for installing win apps[not all, btw] and then try installing your app keeping in mind "Not all apps are installable under wine" , and make sure you go through the winehq link already mentioned...thank you.

---

### Post by mrbiggbrain on 2009-08-17
play on linux, try it, love it. it installs wine apps for you, you just need the disk

---

