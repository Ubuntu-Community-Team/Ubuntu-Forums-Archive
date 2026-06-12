---
title: "java stopped working after upgrading to natty"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by hackeye on 2011-05-05
I'm facing the exact same problem as [http://ubuntuforums.org/showthread.php?t=1616700&highlight=java](http://ubuntuforums.org/showthread.php?t=1616700&highlight=java) after upgrading from maverick to natty. Only, i tried the stuff mentioned on that thread but it didn't fix it for me.

The popups from the java applet which i used to run all the time on maverick just hang and don't respond to mouse/keyboard inputs.

I'm using openjdk:

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  openjdk-6-jre             6b22-1.10.1-0ubuntu1      OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless    6b22-1.10.1-0ubuntu1      OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib         6b22-1.10.1-0ubuntu1      OpenJDK Java runtime (architecture independent libraries)

```

My OS is 32 bit.

I've changed my desktop session from unity to ubuntu classic since it was causing problems with my dual monitor setup, but it hasn't helped the java problem.

Any help would be greatly appreciated.

---

### Post by hackeye on 2011-05-17
Hello,

Does anyone have any ideas about how to fix this?

---

### Post by manishraj2011 on 2011-05-17
> **hackeye said:**
> Hello,

Does anyone have any ideas about how to fix this?
Try typing
about:  plugins ( without spaces )

in the url bar of firefox. Does it list anything related to open-JDK???

---

### Post by hackeye on 2011-05-18
Hi manishraj2011,

Thanks for your reply.

> **manishraj2011 said:**
> Try typing
about:  plugins ( without spaces )

in the url bar of firefox. Does it list anything related to open-JDK???

No. It doesn't. But i don't know if its necessary. It always used to be external (i.e. java would open up separately and i'd never view it within the browser, always a diff. window). It was like downloading any normal file which the browser doesn't understand - i'd have to tell the browser to open it with java. So i doubt a browser plugin was ever there in the first place.

---

