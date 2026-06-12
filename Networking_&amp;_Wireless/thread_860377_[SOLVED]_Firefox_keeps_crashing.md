---
title: "[SOLVED] Firefox keeps crashing"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by jose158 on 2008-07-15
I don't know if this is the right place to post this, but oh well...
Today I installed Google Earth via command: 

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin
```I don't know if that is what is causing the problem and if so, how do I uninstall it?

Anyways, after I install googleearth firefox kept crashing everytime i  went to a different website. Any ideas what is causing it?

---

### Post by jose158 on 2008-07-15
If googleearth is causing the problems, how would I go about uninstalling GoogleEarthLinux.bin and GoogleEarthLinux.bin.1?

---

### Post by StrawberryJam8 on 2008-07-15
There might be some incompatibility or file error right there. Try downloading an updated copy of Firefox and Google earth and make sure they are compatible this time. If it still doesnt work, might as well give up on having google earth for now.

---

### Post by jose158 on 2008-07-15
> **StrawberryJam8 said:**
> There might be some incompatibility or file error right there. Try downloading an updated copy of Firefox and Google earth and make sure they are compatible this time. If it still doesnt work, might as well give up on having google earth for now.
I really don't even need Google Earth... Is there a way to uninstall it?

---

### Post by dmizer on 2008-07-16
google earth uses java if i recall correctly.  install and use the non-free version of sun java:

[https://help.ubuntu.com/community/JavaInstallation?](https://help.ubuntu.com/community/JavaInstallation?)

if the above is not successful:
1) close all instances of firefox
2) open a terminal
3) type the following command into terminal:
```
firefox
```

when firefox crashes, you will see an error in terminal.  please post the error here.

---

### Post by jose158 on 2008-07-16
> **dmizer said:**
> google earth uses java if i recall correctly.  install and use the non-free version of sun java:

[https://help.ubuntu.com/community/JavaInstallation?](https://help.ubuntu.com/community/JavaInstallation?)

if the above is not successful:
1) close all instances of firefox
2) open a terminal
3) type the following command into terminal:
```
firefox
```

when firefox crashes, you will see an error in terminal.  please post the error here.
```
jose@jose-desktop:~$ firefox
FirebugService fbs.DBG_FBS_CREATION: false fbs.DBG_FBS_BP:false fbs.DBG_FBS_ERRORS:false fbs.DBG_FBS_STEP:false fbs.DBG_FBS_FUNCTION:false
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.google.com/ig?hl=en
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.google.com/ig?hl=en
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/about
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/about
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/search
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/search
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/get-lsi
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/get-lsi
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/how
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.tuxsoftware.com/home/how
debugger.onModuleDeactivate Attempt to deactive context that is not active http://www.ubuntu.com/
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success
jose@jose-desktop:~$ 

```

---

### Post by jose158 on 2008-07-17
installing java doesn't help:(

---

### Post by dmizer on 2008-07-17
the error you posted earlier is definitely related to java.

check the plugins directory: /usr/lib/mozilla/plugins to make sure that the libjavaplugin_oji.so is included.  also make sure that no other plugin files reference your old version of java.

browse to: about:plugins in firefox to make sure that it's using sun java.

---

### Post by jose158 on 2008-07-17
> **dmizer said:**
> the error you posted earlier is definitely related to java.

check the plugins directory: /usr/lib/mozilla/plugins to make sure that the libjavaplugin_oji.so is included.  also make sure that no other plugin files reference your old version of java.

browse to: about:plugins in firefox to make sure that it's using sun java.
libjavaplugin_oji.so is not in there. And since every time I tried to go to about:plugins in firefox cause it kept crashing I typed "firefox "about:plugins" and got:```
jose@jose-desktop:~$ firefox "about:plugins"
FirebugService fbs.DBG_FBS_CREATION: false fbs.DBG_FBS_BP:false fbs.DBG_FBS_ERRORS:false fbs.DBG_FBS_STEP:false fbs.DBG_FBS_FUNCTION:false
Obtaining the module object from Python failed.

Traceback (most recent call last):
cant import cStringIO
<type 'exceptions.ImportError'>: /usr/lib/python2.5/lib-dynload/time.so: undefined symbol: PyExc_ValueError
INTERNAL ERROR on Browser End: Could not get the plugin manager
System error?:: Success
jose@jose-desktop:~$ 

```Any solution?

---

### Post by dmizer on 2008-07-17
try making a new profile for firefox:

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by jose158 on 2008-07-17
> **dmizer said:**
> try making a new profile for firefox:

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)
Nope.... Still does it even when I made a new profile...:(

---

### Post by |{urse on 2008-07-17
Firefox has become ummm.. Special! it needs a helmet.

Try Opera, much more stable, faster and full featured.

---

### Post by jose158 on 2008-07-18
Well, I still think it has something to do with Google Earth, because the problem happened right after I installed it. Could be a coincidence, but I doubt it.

---

### Post by jose158 on 2008-07-19
Well, I uninstalled  Firefox and reinstalled it and now it works! Thanks anyways!:popcorn:

---

### Post by dmizer on 2008-07-21
> **jose158 said:**
> Well, I uninstalled  Firefox and reinstalled it and now it works! Thanks anyways!:popcorn:

something must have been severely hosed.  glad you got it working, i was completely stumped.

please mark this thread as solved (thread tools), so that others know there is a solution here.

---

### Post by Aditya_HUH on 2008-08-03
my firefox is crashing every time......also i wanna delete my old profile of firefox and create a new one....plz plz plz help me.

---

### Post by jose158 on 2008-08-03
> **Aditya_HUH said:**
> my firefox is crashing every time......also i wanna delete my old profile of firefox and create a new one....plz plz plz help me.
All I did was remove firefox and install opera and in a couple of days I installed firefox again and it worked great!

---

