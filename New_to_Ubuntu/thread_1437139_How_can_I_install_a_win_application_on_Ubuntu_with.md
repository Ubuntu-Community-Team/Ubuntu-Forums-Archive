---
title: "How can I install a win application on Ubuntu with Wine?"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by bilbo.san on 2010-03-23
Hey everyone!!!

I have installed WINE on Ubuntu (just did), I have the .exe file on my desktop... what is next??, I have double clicked the file and nothing worked. Can you please help me??? What is the next step???

Thanks
e.

---

### Post by protiss on 2010-03-23
Try opening up a terminal and navigating to your desktop ("/home/administrator/Desktop" with your account name in lieu of administrator), then type "wine Installer.exe" (case sensitive) ...or whatever the .exe is called.

---

### Post by halitech on 2010-03-23
how about right click - open with wine ?

---

### Post by protiss on 2010-03-23
Yeah I guess if you don't like the command prompt :(

---

### Post by Calash on 2010-03-23
If it did nothing then there is likely  problem.  Issuing the command from the terminal will get better information as to what went wrong.

---

### Post by Sir Jasper on 2010-03-23
Hi,

Some programs do not work well in Wine and some do nothing at all when clicking the ¨exe¨.

I suggest you try Firefox 3.6.2 Portable version from PortableApps. Download it to your desktop from [http://portableapps.com/apps/internet/firefox_portable](http://portableapps.com/apps/internet/firefox_portable). then install it to your Desktop then try FirefoxPortable.exe


You can just delete the new files from your Desktop after any test since with the portable versions there is nothing to uninstall.

I have no idea what sort of Windows programs you want to work via Wine; however, as a general tip I have found that Windows portables tend to work well with Wine (either from Hard Drive or USB Stick).

My regards

---

### Post by sandyd on 2010-03-23
whats the app?

---

### Post by Sir Jasper on 2010-03-23
Hi carlee, our buddy,

This is way off topic, but could you please have a look at  [http://ubuntuforums.org/showthread.php?t=1408380](http://ubuntuforums.org/showthread.php?t=1408380)

My regards

---

### Post by linuxman94 on 2010-03-23
See if your app is compatible with wine.  Go to [http://appdb.winehq.org/]("http://appdb.winehq.org/") and search for it. Check the entry for it and look under Test Results.  Look for one that says 'Ubuntu 9.10' as the version and see what it is rated.

---

### Post by bilbo.san on 2010-03-23
Thanks everybody!
The application I would like to install is SILO, I followed the basic steps to run the .EXE file and nothing happens, some other .exe files do work but SILO didnt.

So, I read somewhere that I could just copy the folder from a windows machine that containing the SILO program and then put it on WINE and try to run it from there... does that make sense???

---

### Post by sandyd on 2010-03-23
> **bilbo.san said:**
> Thanks everybody!
The application I would like to install is SILO, I followed the basic steps to run the .EXE file and nothing happens, some other .exe files do work but SILO didnt.

So, I read somewhere that I could just copy the folder from a windows machine that containing the SILO program and then put it on WINE and try to run it from there... does that make sense???
hmm.
winehq's rating is very old, but it says it is garbage.

lets see...

ill run it in the latest dev version of WINE and see if I can get it working...

heh.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14082](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14082)

if you mean that program, add the wine dev repos, upgrade wine, and run.

Runs OOB

---

